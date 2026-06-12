---
title: "XAMPP does not work properly"
date: 2009-03-10
forum: Programming Talk
---

### Post by k3nny on 2009-03-10
Hello everyone,

it's my first post here. At the beginning sry for my english.

I have got a problem with XAMPP @Kubuntu 8.10. I installed it successfully but when I try to run [http://localhost](http://localhost) I get an information: "It works!". And this page is still active even if I turn XAMPP off.

The problem is: I am not able to get access to phpmyadmin and even XAMPP configuration site.

I don't know if it's important, but when I close XAMPP using
```
sudo /opt/lampp/lampp stop
```
and then
```
sudo /opt/lampp/lampp start
```
I get the information that there is one more web server daemon is already running.

What should I do to get access to my XAMPP config site, phpmyadmin etc?

I would appreciate any form of your help. Thanks a lot.

---

### Post by ddrichardson on 2009-03-13
Try entering the address for phpmyadmin without the http://

---

### Post by psamim on 2009-05-09
I have the same problem. When It shows "It works" it means that Apache is working instead of Xampp. How can I uninstall or disable it? How can I have a reinstallation?

---

### Post by Reiger on 2009-05-09
That message is just a test/auto-generated-for-verification-that-it-works HTML file called index.htm(l). Usually resides at /var/www/. To "disable" it: remove it.

---

### Post by keithweddell on 2009-05-09
It sounds like you have two instances of apache on your system: one installed by XAMPP and I assume that the other was loaded using synaptic or similar.  You need to remove one so that you can use the other without interference.

Keith

---

### Post by Alias1407 on 2009-05-09
Or perhaps the page is stored in the browsers cache!!

Press CTRL + F5 to bypass the cache.

---

