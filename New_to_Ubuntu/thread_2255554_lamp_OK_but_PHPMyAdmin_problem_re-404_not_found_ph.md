---
title: "lamp OK but PHPMyAdmin problem re-404 not found /phpmyadmin"
date: 2014-12-05
forum: New to Ubuntu
---

### Post by gregory10 on 2014-12-05
Thanks for any help

Been working on this for many hours now since early berore first light and got to the point of needing help

Got instructed to do this from an WIKI page on this site: its the PHPMyAdmin workbench page below
[https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin_and_mysql-workbench](https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin_and_mysql-workbench)

gregory@gregory-Satellite-L500:~$ gksudo gedit /etc/apache2/apache2.conf
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu

Didn't work so tried this and got what is below
gregory@gregory-Satellite-L500:~$ sudo gedit /etc/apache2/apache2.conf
[sudo] password for gregory: 
sudo: gedit: command not found

Now I have done what was suggested but still no dice
Got this below as the result of the command:
gregory@gregory-Satellite-L500:~$ gksudo gedit /etc/apache2/apache2.conf

(gksudo:5249): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

so my next step was to try again and got a login popup on me and so logged in and 
gregory@gregory-Satellite-L500:~$ gksudo gedit /etc/apache2/apache2.conf
gregory@gregory-Satellite-L500:~$

Ye looked good but still no app to do any editing of the file and so tried again and 
then tried to put in the include through the terminal thinking that might be what is expected:
gregory@gregory-Satellite-L500:~$ gksudo gedit /etc/apache2/apache2.conf
gregory@gregory-Satellite-L500:~$ Include /etc/phpmyadmin/apache.conf
Include: command not found
gregory@gregory-Satellite-L500:~$ 

this file apache2.conf that need editing does not come up into any editor called gk or anything like that

I tried edting the file in Kate but got refused saying the file is read only so needed to do it through a terminal and tried the above as instructed.

If I type the url into firefox for local host: [http://localholt](http://localholt) ........ wahoo I get the "IT WORKS" message page in /html so LAMP is fine
but when I type into the firefow seach: [http://localhost/phpmyadmin](http://localhost/phpmyadmin) then I get the '404 Not Found' message
it seems to need a proper http address or something but just need to for some development work on an app and CMS I am building
I'm not going to publish a site on this instalment.

/etc/apache2/apache2.conf needs to be edited but have not got the nohow, can anybody help?
I have recently installed Kubuntu 14. 04 LTS

---

### Post by gregory10 on 2014-12-06
**It seems to be that this is not understood or is in the too hard category for most of us so to reiterate** 
I get the impression I need to make this question simpler...


OK just to summarize:
                                 It looks like all that needs to be done finalize the editing of that one file at the end of what is in that file
                              
                                 Include /etc/phpmyadmin/apache.conf

                                 and that one line needs to be put at the very end of: /etc/apache2/apache2.conf if it was done that would resolve this
                       
                                 So how is this done? How to open the file in an editing format and not read only?

---

### Post by Gone fishing on 2014-12-06
Is this on a server without a gui?

This will works open a terminal and run sudo nano /etc/phpmyadmin/apache.conf

Then when you have edited the file Ctrl x remembering to answer y

---

### Post by gregory10 on 2014-12-06
@Gone fishing

thanks nano is a great little editor
managed to make the change and edit that apache2.conf file
checked the file in another editor and the line was there at the end of the file where it was supposed to be

It's not working yet but am thinking it is because the Apache Server has to be closed before the change will take place.
Thanks for your help what you said worked. No its not a server without a gui just come to thinking that the terminal seems faster 
and more efficient in the long run. It's just a matter of getting used to it. It's a steep learning curve but worth it for sure.

---

### Post by gregory10 on 2014-12-06
Yes pleased to say this one is resolved

thanks again to 'Gone fishing'

sudo nano worked!

---

### Post by gregory10 on 2014-12-06
I need to tag this as resolved but don't know how???

anybody know how I show this as a resolved thread?

---

### Post by steeldriver on 2014-12-06
... from the drop-down 'Thread Tools' menu at the top of the thread

---

### Post by Gone fishing on 2014-12-06
Glad it worked

---

