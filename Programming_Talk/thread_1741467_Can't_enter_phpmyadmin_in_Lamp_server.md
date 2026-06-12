---
title: "Can't enter phpmyadmin in Lamp server"
date: 2011-04-28
forum: Programming Talk
---

### Post by kukker32 on 2011-04-28
Hey there i have this problem with i can't enter my database in lamp server..

all i know is when i type in [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) into the url bar in chromium, i got this error 

```

Oops! This link appears to be broken.

```

what i do to solve this ?? as i need to setup an ajax chat for a website i and i can't when i can't access my database in localhost :(

---

### Post by indytim on 2011-04-28
1.  How did you setup / install phpmyadmin?
2.  What is the ownership, group ownership and permissions on /var/www?

IndyTim / DataMan

---

### Post by kukker32 on 2011-04-28
> **indytim said:**
> 1.  How did you setup / install phpmyadmin?
2.  What is the ownership, group ownership and permissions on /var/www?

IndyTim / DataMan

i used this command, and it have worked for me before.. but now it simply wont work


sudo apt-get install apache2 apache2-doc mysql-server php5 libapache2-mod-php5 php5-mysql phpmyadmin


as for the ownership both the 'root' user and the general user i log in with have read/write permisiions

---

### Post by bashologist on 2011-04-28
I don't use phpmyadmin but I debug alot of my own apache stuff. What's the access and error log say? Did you try with your ip address too? if you have access rules you might've disabled access with the localhost word thing. Check logs with something like this.
```
clear; tail -n 0 -f /var/log/apache2/{error,access}.log | while read input; do echo "${input:0:200}"; done

```
Then with the command running goto the page in chromium and make it error, then ctrl+c in the terminal to stop the command.

Is it a cache problem with chromium? did you try firefox?

---

### Post by kukker32 on 2011-04-28
> **bashologist said:**
> I don't use phpmyadmin but I debug alot of my own apache stuff. What's the access and error log say? Did you try with your ip address too? if you have access rules you might've disabled access with the localhost word thing. Check logs with something like this.
```
clear; tail -n 0 -f /var/log/apache2/{error,access}.log | while read input; do echo "${input:0:200}"; done

```
Then with the command running goto the page in chromium and make it error, then ctrl+c in the terminal to stop the command.

Is it a cache problem with chromium? did you try firefox?

i don't really got what you want me to do?
you want me to write that code into a .php file and run it in localhost ? or ?

as for chrommium its not a cache problem.. i have tried in firefox and opera same result..

---

### Post by bashologist on 2011-04-28
> you want me to write that code into a .php file and run it in localhost ? or ?
No that's bash code you enter into your terminal... It basically will output the log files to your terminal so we can read them and find out what's wrong possibly. 

You enter the command to your terminal then goto your myphpadmin page and re-create the error then look for the output in the terminal.

Edit:
Same result with firefox? I've never seen this error in firefox before.
Oops! This link appears to be broken.

Just a basic 404 error maybe?

---

### Post by kukker32 on 2011-04-28
> **bashologist said:**
> No that's bash code you enter into your terminal... It basically will output the log files to your terminal so we can read them and find out what's wrong possibly. 

You enter the command to your terminal then goto your myphpadmin page and re-create the error then look for the output in the terminal.

Edit:
Same result with firefox? I've never seen this error in firefox before.
Oops! This link appears to be broken.

Just a basic 404 error maybe?

yea its was a 404..
but i asked a friend and told me it was a broken symlink or something. so i ran to command

```
sudo ln -s /usr/share/phpmyadmin /var/www
```
and it's working now :) thanks for your time to help me anyway ...

---

