---
title: "lamp server"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by milos2 on 2013-09-11
I wanted to install the lamp server and I found this tutorial[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) and I dont know how to do this step


 [COLOR=#000000][FONT=verdana]After that is installed our next task is to get PHP to work with MySQL. To do this we will need to open a file entitled [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]*php.ini*[/FONT][/COLOR][COLOR=#000000][FONT=verdana]. To open it type the following:[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]*gksudo gedit /etc/php5/apache2/php.ini*[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Now we are going to have to uncomment the following line by taking out the semicolon ([FONT=Courier New]*;*[/FONT]).[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Change this line:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*;extension=mysql.so*[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]To look like this:
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New][I]extension=mysql.so
I have some big text  inside that file, something like that [/I][/FONT][/COLOR] About php.ini   ;;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible for
; configuring many of the aspects of PHP's behavior.


; PHP attempts to find and load this configuration from a number of locations.
; The following is a summary of its search order:
; 1. SAPI module specific location.
; 2. The PHPRC environment variable. (As of PHP 5.2.0)
; 3. A number of predefined registry keys on Windows (As of PHP 5.2.0)
; 4. Current working directory (except CLI)
; 5. The web server's directory (for SAPI modules), or directory of PHP
; (otherwise in Windows)
; 6. The directory from the --with-config-file-path compile time option, or the
; Windows directory (C:\windows or C:\winnt)
; See the PHP docs for more specific information.
; [http://php.net/configuration.file](http://php.net/configuration.file) 
I dont have it 
[TABLE="width: 100%"]
[TR]
[TD="bgcolor: #f2f2ff"][FONT=arial][SIZE=2][COLOR=#222222]
;extension=[B]php_mssql.dll 
;extension=[B]php_mysql.dll 
;extension=[B]php_mysqli.dll 

I dont know what to chnge...


[/B][/B][/B][/COLOR][/SIZE][/FONT][/TD]
[/TR]
[/TABLE]
[COLOR=#000000][FONT=Courier New]*Help me*[/FONT][/COLOR]

---

### Post by leg on 2013-09-11
It seems that[ php_mysql.dll]("http://forums.mysql.com/read.php?52,37151,40841") is the one you want.

---

### Post by milos2 on 2013-09-11
you didnt read my question I dont have it [FONT=arial];extension=[/FONT][B]php_mssql.dll 
;extension=[B]php_mysql.dll 
;extension=[B]php_mysqli.dll  in my php.ini file
 I have some big text...
[/B][/B][/B]

---

### Post by Kevin_Arnold on 2013-09-11
.dll's are for windows, you'll want to change them to .so's... I'm guessing you got a config file originally configured for windows somehow.

If the line isn't there at all, just add it exactly how they have it in the guide instead of uncommenting it. It has the same effect.

---

### Post by milos2 on 2013-09-11
look
I  saw those dlls on some forum that it should look like that, forget that I posted that
 >  [FONT=arial];extension=[/FONT][B]php_mssql.dll 
;extension=[B]php_mysql.dll 
;extension=**php_mysqli.dll **[/B][/B]
My question is: When I open php.ini file with this command [COLOR=#000000][FONT=Courier New]*gksudo gedit /etc/php5/apache2/php.ini I dont have what to change(because in *[/FONT][/COLOR][http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) this tutorial it says 
[COLOR=#000000][FONT=verdana]Change this line:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*;extension=mysql.so*[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]To look like this:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New][I]extension=mysql.so

I dont have that 

I have something like that [http://postimg.org/image/xzod5m7ox/](http://postimg.org/image/xzod5m7ox/) and the text goes all the way down, I am beginner in this...[/I][/FONT][/COLOR]

---

### Post by leg on 2013-09-11
One of those lines will be the one you want. Find the line you are after and change it as stated.

---

### Post by Kevin_Arnold on 2013-09-11
> **milos2 said:**
> look
I  saw those dlls on some forum that it should look like that, forget that I posted that
 
My question is: When I open php.ini file with this command [COLOR=#000000][FONT=Courier New]*gksudo gedit /etc/php5/apache2/php.ini I dont have what to change(because in *[/FONT][/COLOR][http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) this tutorial it says 
[COLOR=#000000][FONT=verdana]Change this line:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*;extension=mysql.so*[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]To look like this:[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New][I]extension=mysql.so

I dont have that 

I have something like that [http://postimg.org/image/xzod5m7ox/](http://postimg.org/image/xzod5m7ox/) and the text goes all the way down, I am beginner in this...[/I][/FONT][/COLOR]

Right, in the tutorial they are only showing you the part that is important. The actual file is much larger, like what you linked. In the big file, you need to scroll down and find the line they have and remove the semi-colon.

---

### Post by SeijiSensei on 2013-09-11
You probably just need to install the **php5-mysql** package from the repositories.

---

### Post by milos2 on 2013-09-11
I messed something with lamp, I saw on this forum how to remove it, but now when I try to install it again it doesnt ask me to set up the password for my sql...what shall I do in order to ask me to set up the password...
Now I use this to install
```
sudo aptitude install apache2 mysql-server php5 php-pear php5-gd php5-mysql php5-imagick php5-curl curl phpmyadmin rsync cronolog libapache2-mod-php5 libapache2-mod-python
```

---

### Post by mörgæs on 2013-09-11
I have merged your two LAMP threads.

The best installation on Linux is 
```
sudo apt-get install lamp-server[COLOR=#444444][FONT=arial]^
[/FONT][/COLOR]
```
Remember the caret at the end of the command.

---

