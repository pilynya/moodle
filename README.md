# moodle
Гайд есть на moodle пятилистник <br/>
По ssh через клиента заходим на hq-srv <br/>

dnf install httpd -y<br/>
dnf install mariadb-server mariadb -y<br/>
install php php-common php-mysql php-gd php-intl php-curl php-xmlrpc php-ldap php-apc php-mbstring php-dom php-soap php-zip -y
systemctl enable --now httpd<br/>
systemctl enable --now mariadb<br/>
mariadb -u root<br/>
create database moodle;<br/>
create user moodle identified by 'P@ssw0rd';<br/>
grant all privileges on moodle.* to moodle;<br/>
flush privileges;<br/>
quit;<br/>
apt-get install wget<br/>
В браузере ищем подходящую нам версию moodle<br/>

![image](https://github.com/user-attachments/assets/426047b7-5c96-4b00-a072-f46198a334d3)

![image](https://github.com/user-attachments/assets/5e622236-830e-4b0c-87f3-120f22159cd7)

Заходим на загрузку tgz и копируем адрес ссылки<br/>

![image](https://github.com/user-attachments/assets/689e2645-87dd-4fd9-8808-e2444deed0fd)

Далее в консоль на HQ-SRV пишем wget и нажимаем shift+insert<br/>
Скачиваем tgz файл с moodle<br/>
tar -xf ( и файл который скачался табом)<br/>
Переносим moodle в каталог: mv moodle /var/www/html <br/>
Создаем: mkdir /var/www/moodledata <br/>
Раздаем права: chown -R apache:apache /var/www/html <br/>
Дописываем в файл /etc/php.ini max_input_vars = 5000 <br/>

![image](https://github.com/user-attachments/assets/0422372d-99e2-4144-80e9-e554fe10b78f)

В файле /etc/httpd/conf/httpd.conf меняем путь <br/>

![image](https://github.com/user-attachments/assets/bd54c317-9b97-49ab-ae68-738058680991)

Перезапуск службы httpd: systemctl restart httpd <br/>
Перезапуск службы php: systemctl restart php-fpm <br/>
C клиента HQ-CLI в браузере зайдите на страницу http://192.168.100.2/ и начните установку moodle в графическом режиме, заполнив параметры из предыдущих шагов<br/>

![image](https://github.com/user-attachments/assets/5cbf2df0-2c6c-4d66-9199-f535ff616221)

Далее создайте курс и в названии курса укажите номер рабочего места, через режим редактирования настройте личный кабинет (убрать все блоки и добавить блок обзор курсов)<br/>



