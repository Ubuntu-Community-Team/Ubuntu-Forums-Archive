---
title: "apache2 tutorial"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-08-31
I need a tutorial on how to setup apache2. My friend made a website using it and I thought ide give it a try but ive only gotten as far as sudo apt-get install apache2 and then im at a lost.

---

### Post by mellowd on 2008-08-31
Stick your web files into /var/www

Now browse to localhost, or your local ip through your browser

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

---

### Post by jemate18 on 2008-08-31
> **SpenceMakesSense said:**
> I need a tutorial on how to setup apache2. My friend made a website using it and I thought ide give it a try but ive only gotten as far as sudo apt-get install apache2 and then im at a lost.

Install apache2 via repository
Steps:
1. Applications -> Accessories -> Terminal
2. Get root privileges
```
sudo su [password]
```
3. type
```
apt-get install apache2
```
4. type this to go to the configuration
```
cd /etc/apache2
```
5. to view the configuration type
```
less apache2.conf
```

The setting described are straightforward and will work out of the box.

Open browser and type 
```
http://localhost
```
or
```
http://127.0.0.1
```

If it says "It works!" You're good to go!

Your settings will differ for your setup. What exactly do you want apache2 to have? I mean, support for php, perl, and or python?

Hope this helps!

jemate18

---

### Post by cpetercarter on 2008-08-31
Have a look at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by SpenceMakesSense on 2008-09-01
> **jemate18 said:**
> Install apache2 via repository
Steps:
1. Applications -> Accessories -> Terminal
2. Get root privileges
```
sudo su [password]
```
3. type
```
apt-get install apache2
```
4. type this to go to the configuration
```
cd /etc/apache2
```
5. to view the configuration type
```
less apache2.conf
```

The setting described are straightforward and will work out of the box.

Open browser and type 
```
http://localhost
```
or
```
http://127.0.0.1
```

If it says "It works!" You're good to go!

Your settings will differ for your setup. What exactly do you want apache2 to have? I mean, support for php, perl, and or python?

Hope this helps!

jemate18

That worked getting it started but my friend managed to get as far as having his own internet link. Something like halloran.servegame.com. And for me whenver i edit the html file it doesnt change at all anyway

---

### Post by jemate18 on 2008-09-01
Does your friend bought a domain name?

What file are you editing?

What do you want to be configured for apache?

---

