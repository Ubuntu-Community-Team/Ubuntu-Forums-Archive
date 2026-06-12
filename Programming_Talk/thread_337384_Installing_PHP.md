---
title: "Installing PHP"
date: 2007-01-12
forum: Programming Talk
---

### Post by Enroth on 2007-01-12
Hi all,

I'm sure this question can be answered easily with either a short description or a link either will be appreciated.

I want to set up PHP, but i don't want to host sites, just be able to save a PHP document and view it as it would be displayed on my Unis server (were my site will be hosted). I have tried several methods to no success, and couldn't find another thread for this. 
I guess to do this I need to set  an Apache server, I have had past experience with this, but not in a while.

Thankyou for anyhelp
p.s. Sorry if this is in the wrong place, wasn't sure if it should be in faqs, or programing talk.

---

### Post by Grey on 2007-01-12
sudo apt-get install apache2 php4 libapache2-mod-php4

=)

---

### Post by Enroth on 2007-01-13
Thankyou for the quick reply, but having done that I get the same problem that I have had previously of it opening and displaying the code in the file rather than displaying page. Is this solved by saving the php files to a diffrent location, or the setting of a class path? Or a completely diffrent manner.

---

### Post by compwiz18 on 2007-01-13
save your files in /var/www and go to [http://localhost/name-of-file](http://localhost/name-of-file) to see it

---

### Post by Enroth on 2007-01-13
Wow must be my lucky day two get quick responses.
thankyou Grey and compwiz18
you have made my life a lot easier, and soon a lot more productive. :)

---

### Post by Grey on 2007-01-13
Glad it works for you.  Have fun.  :)

---

### Post by alcatraz678 on 2007-10-24
Apparently there was no /www in folder var. So I created one.
Then after that, I can't save anything in the folder.

---

### Post by LaRoza on 2007-10-25
> **alcatraz678 said:**
> Apparently there was no /www in folder var. So I created one.
Then after that, I can't save anything in the folder.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by #Reistlehr- on 2007-10-25
You should use php5, not 4.. :D

---

