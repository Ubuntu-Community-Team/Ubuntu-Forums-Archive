---
title: "PHP Without Webhost"
date: 2011-12-04
forum: Programming Talk
---

### Post by Orcris on 2011-12-04
Is there any way to display PHP without a webhost? I'm trying to learn PHP, since I just learned HTML, and I don't want to need to get an actual host, since I would need to re-upload files every time I want to view them. I can't get any clear tutorials for Apache Server, so how do I view PHP pages I make on Kubuntu without a webhost?

---

### Post by Sworddragon on 2011-12-04
Without Apache or another http-server this is not possible. I recommend you installing Apache and PHP on your system so you don't need to upload your files somewhere else. If I remember correctly Apache and PHP are working out of the box. Just put your files into /var/www and call them in your web browser.

---

### Post by Orcris on 2011-12-04
I installed apache and PHP, but when I set the permissions of /var/www so that I could edit files in it and opened my index.php file, which was in it, Firefox asked me where to save it. it wouldn't let me view it.

Never mind. I got it working using [http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)__[URL="http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/"]
[/URL]

---

### Post by LANrover on 2011-12-05
> Just put your files into /var/www and call them in your web browser. 	

Just make sure you go to either "localhost" in your web browser or "127.0.0.1"

---

### Post by Majid7 on 2011-12-05
I recommend you to install XAMPP FOR LINUX.
here is the link :
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

