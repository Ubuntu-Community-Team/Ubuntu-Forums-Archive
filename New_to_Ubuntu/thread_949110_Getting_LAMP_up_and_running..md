---
title: "Getting LAMP up and running."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Symbit on 2008-10-15
Hello, I am having a few issues with getting Apache, PHP, and mySQL running together on Ubuntu (8.10 Beta). I installed apache, php, and mySQL via apt-get. As far as I can tell, they installed and are now running correctly. However, when I try to link from my 'index.html' to, lets say, /eyeOS/index.php, the server offers for me to download the eyeOS index.php as apposed to actually displaying it. How do I tie in PHP and Apache, and for that matter, Apache mySQL and PHP?

Thank you for taking the time to help me out and have a wonderful day!

-Symbit

---

### Post by eolson on 2008-10-15
I think if I was doing it,   I'd wait until the official release came out.   There are about 15 updates an hour comeing out right now.   Something works, the it doesn't, then it does .....

---

### Post by Symbit on 2008-10-15
Lets pretend that I am using 8.04. What would I have to do then?

---

### Post by louieb on 2008-10-15
In the future to insure the LAMP programs are correctly tied together. 

```
sudo tasksel install lamp-server
```

---

