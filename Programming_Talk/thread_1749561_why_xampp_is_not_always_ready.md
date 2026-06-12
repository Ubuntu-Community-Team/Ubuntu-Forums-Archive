---
title: "why xampp is not always ready?"
date: 2011-05-04
forum: Programming Talk
---

### Post by bestron on 2011-05-04
Previously I've installed apache, PHP and MySQL separately on my machine, apache was always running and ready for my projects, every time I hit [http://localhost](http://localhost) I get the message that it works.
when I set up a new ubuntu installation, I installed XAMPP instead, installation was ok, started lampp successfully and went to localhost with the index of xampp,
the problem is when I restarted, I tried to open localhost but it gives the message that it can't connect to server, and I have to start lampp everytime I restart and this is really annoying.
Is that ordinary or I have to change settings somewhere?:confused:

---

### Post by deathadder on 2011-05-05
That's the expected behaviour, when you installed Apache/PHP/MySQL seperately the installer created entries within /etc/rc.* to start / stop the different services when you boot and shutdown.

On the other hand xampp is standalone app that starts Apache/PHP/MySQL when you run /opt/lampp/lampp start. You can set xampp to start automatically on boot ([instruction at apache friends]("http://www.apachefriends.org/en/faq-xampp-linux.html#fsl")).

---

### Post by slavik on 2011-05-05
don't use xampp. do it right.

---

### Post by deathadder on 2011-05-05
> **slavik said:**
> don't use xampp. do it right.
xampp is the right way to do it at times, I know when I've had to show off website I've been working on throwing xampp on my laptop is easier and cleaner than a full LAMPP install.

But if you're running xampp from startup or everyday it's probably easier to/better to go with a full LAMPP install which if I remember rightly is what's said on the xampp FAQ...

---

