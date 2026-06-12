---
title: "web server help."
date: 2011-12-31
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2011-12-31
hey guys. i want to set up a web server. but dont know how to go around doing that. can someone explain how? im running ubuntu 11.10 by the way.

---

### Post by lechien73 on 2011-12-31
If you want to set up a LAMP (Linux, Apache, MySQL, PHP) server - which is a common configuration - then open a terminal window and type:

```
sudo apt-get install php5 mysql apache2
```

When these are installed, you will be prompted for a root password for the MySQL user.

After the installation, open a web browser and type the address: [http://localhost](http://localhost)

You should get a "Success! It Works" banner. The files served by the apache webserver are located in the /var/www directory.

Before you open it up to the Internet, though, make sure you read about and patch any potential vulnerabilities.

Hope this helps...happy webserving :)

---

### Post by snowpine on 2011-12-31
Required reading: 

[https://help.ubuntu.com/11.10/serverguide/C/serverguide.pdf](https://help.ubuntu.com/11.10/serverguide/C/serverguide.pdf)

---

### Post by ilikelinuxitisthebest on 2011-12-31
thanks guys!!!! really helped.

---

### Post by d3v1150m471c on 2011-12-31
I have a much more simple webserver than apache2 on the link below. it's publically available if you have tor. Then if you think it sucks, you can complain to me and I can improve it.

---

### Post by lisati on 2011-12-31
> **d3v1150m471c said:**
> I have a much more simple webserver than apache2 on the link below. it's publically available if you have tor. Then if you think it sucks, you can complain to me and I can improve it.

Er, hello! This thread is in "Absolute beginner talk"...... :D

---

