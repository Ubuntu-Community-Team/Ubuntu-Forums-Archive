---
title: "nautilus image resizer"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-02-24
This works great but the resized images come out owned by root (they all are from my home files) even in sudo nautilus I can,t copy or delete them. How can I change this behavior?

---

### Post by Frogs Hair on 2012-02-24
Strange , none of the information indicates indicates that the image resizer can change file permissions . If you are using 11.10 make it is compatible with Nautilus 3.2.1 .

---

### Post by Unooe on 2012-02-24
Had this problem a while ago. Didn't really find an answer back then.

So a solution would be appreciated. :)

__________________
Job YT&wiki:
[Uunisepät]("http://www.youtube.com/watch?v=fVIwv90wmQE") | [Uunisepät]("http://fi.wikipedia.org/wiki/Uunisep%C3%A4t")

---

### Post by ajgreeny on 2012-02-24
Can you copy a few images into a temporary test folder, then run the image resizer on them, and finally show us the output of **ls -l testfolder/** to see what that says about the file properties and permissions.

I assume you are not running the plugin after starting nautilus as root with "gksu nautlus"?  If you are that will answer the question, but I can not see why you would do that, so presume you are running nautilus and the plugin as your normal user.

---

### Post by aeronutt on 2012-02-24
Quick search, and I only see two nautilus image resizer's in my repositories:

nautilus-image-converter, and
nautilus-image-manipulator

nautilus-image-converter stopped working for me a few versions back.
nautilus-image-manipulator works great, you might want to try it.

---

### Post by HermanAB on 2012-02-24
gThumb is probably a better idea than Nautilus for that.

---

### Post by coffeecat on 2012-02-24
> **aeronutt said:**
> nautilus-image-converter stopped working for me a few versions back.
nautilus-image-manipulator works great, you might want to try it.

Point of information - nautilus-image-converter was for gnome2, that is Natty and before, and nautilus-image-manipulator is for gnome3 - 11.10 and later. I too am curious to know which of these the OP means by nautilus image resizer.

---

### Post by cmcanulty on 2012-02-24
According to synaptic I have both installed. I am running 11.10 with classic no effects. My nautilus version is 1.3.2.1. Now I tried it and the permissions didn't change, very weird. The other try was on my external hard drive but I still had me as the owner maybe the external drive caused it, thanks

---

