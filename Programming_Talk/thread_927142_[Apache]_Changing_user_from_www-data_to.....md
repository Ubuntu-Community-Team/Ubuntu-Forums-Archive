---
title: "[Apache] Changing user from www-data to...."
date: 2008-09-22
forum: Programming Talk
---

### Post by Pyro.699 on 2008-09-22
Hello,

As some of you may have read in my other post, about running a java application with php ([URL](http://ubuntuforums.org/showthread.php?t=922399&goto=newpost)). In the disscussion we came to the conclusion that the reason the scripts were not working properly was that the user **www-data **was not running under the x display. What i would like to do is completly change over the user stats from **www-data** to **cody**. Now, before i get several people telling me the **LARGE** securety risks, i am well aware of the hole that this will open. This will be on a computer with absolutely no personal data on it at all, if someone hacks it, the most they could do is stop my downloads, or view my current background, so please dont inform me of that. Ive tried seatching all files for the text **www-data** but that took hours and only found 5 files, 1 of which were relivent. So there must be a loctaion to change the main user. Ive looked in these locations:

/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
/etc/apache2/envvars
/etc/php5/apache2/php.ini

Please tell me where it is that i need to go to change the user from **www-data** to **cody**

Thanks
~Cody Woolaver

---

### Post by pe7er on 2008-10-13
> **Pyro.699 said:**
> Please tell me where it is that i need to go to change the user from **www-data** to **cody**

It's located in /etc/apache2/envvars and you can change it with:
```
sudo gedit /etc/apache2/envvars
```

Change:
> export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data

to:
> #export APACHE_RUN_USER=www-data
export APACHE_RUN_USER=cody
#export APACHE_RUN_GROUP=www-data
export APACHE_RUN_GROUP=cody


---

### Post by mnml on 2009-12-07
it worked for me thanks.

---

### Post by Pyro.699 on 2009-12-07
Thanks for replying to a topic that is over a year old :P

---

### Post by minhnghivn on 2010-10-20
By the way, how can I set different RUN_USER for each vhost?

---

### Post by Jack Danish on 2012-09-28
I know it's an old post but thank you, exactly what I was looking for, works perfectly!

...dont forget about permissions.


Jack

---

