---
title: "localhost pointing to old external ip"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by katxor on 2008-08-14
hmm, hi guys, 
I have an "lamp server" setup manily to be able to access my mp3s from inside and outside the home network. when i fiddled with this (4-5months ago) i remember that somewhere i had to go and set my external ip adress manually.
The problem now is, my router broke and since i dont have a static ip i got a new external one as soon as i plugged in my new router.

My problem now is that when i use "192.168.1.3" adress inside network or localhost/127.0.0.1 on the server computer it still is searching for my old ip adress... anyone know where i should look?

places ive been. 

/var/www/*.conf
/etc/host.conf
/etc/apache2/*.conf
/etc/apache2/sites-enabled/

and by *.conf i mean ive been look at each conf file to see if i can change anything.

oh, and when i set my router to "static ip" and type in my old adress everything works just fine. but not internet ofc since i can get that ip from my isp.

---

### Post by Too Late on 2008-08-14
How about this file: /etc/hosts

---

### Post by katxor on 2008-08-14
> **Too Late said:**
> How about this file: /etc/hosts

nope no ip adress there either, 

all i get is 127.0.0.1 pointing to localhost and 127.0.1.1 pointing to my user

---

### Post by katxor on 2008-08-14
fixed now, its was just some silly settings in wp

---

