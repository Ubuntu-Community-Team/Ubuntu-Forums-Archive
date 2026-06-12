---
title: "Apache on Feisty  - Images &quot;Forbidden&quot;"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by AustinMarton on 2008-04-23
Hi there, I am running a basic webserver on Feisty. The directory which my pages are in is /var/www. I have had no problem in the past, but recently I copyed a new website to the server from a flashdrive and placed it in that directory. I can view the html pages fine over the internet, but none of the images will show. If I try to open the images directly I get 
```

Forbidden

You don't have permission to access /images/beboButton.png on this server.
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at abominableginnypig.mine.nu Port 80
```

I thought this would be basic file permissions, but I have other images in that folder with less permissions that show up! 

E.g. files that don't show up:```

> ls -l
total 32
-rwxr-xr-x 1 www users  5402 2008-04-20 00:48 beboButton.png
-rwxr-xr-x 1 www users  1488 2008-04-20 00:35 facebookButton.png
-rwxr-xr-x 1 www users  7604 2008-04-20 00:35 myspaceButton.png
-rwxr-xr-x 1 www users 10596 2008-04-20 01:12 youTubeButton.png
```
files that do show up:
```
> ls -l
total 1048
-rw-r--r-- 1 www users 230796 2007-06-23 22:26 agbannerBlur.png
-rw-r--r-- 1 www users 267611 2007-06-23 22:26 agbanner.png
-rw-r--r-- 1 www users  52949 2007-09-17 22:00 arcade_thumb.jpg
-rw-r--r-- 1 www users  67056 2007-06-23 23:34 GES.jpg
-rw-r--r-- 1 www users 154427 2007-06-23 23:43 ML.jpg
```

I'm sure this is something reallly basic and people ask this kind of stuff all the time, but I have been fiddling around for ages now and do not seem to be making any progress what so ever.

Cheers,
'stan.

---

### Post by spiderbatdad on 2008-04-23
Take a look at your html and make sure the path to the pictures is correct. Check the owner of the pictures.

---

### Post by AustinMarton on 2008-04-23
Thanks for your reply. I have checked the destinations to the pictures are correct, when I just try to open them in my browser I get two distinctly different errors, if I try to open "mysite/images/button.jpg" I get "FORBIDDEN" 
if I try to open "mysite/folderthatdoesntexist/button.jpg" I get "CANNOT BE FOUND".

How do I check the owner of the pictures? from the above terminal output it says "users" for both files that show up and those that don't?

---

### Post by spiderbatdad on 2008-04-23
I see now owner is the same. And you say the pictures you cannot access are in the same folder as the pictures you can access. Out of curiosity, has the server been restarted since adding the new pictures?

---

### Post by AustinMarton on 2008-05-02
Hi, Since I am not at the physical location of the server I haven't been able to restart it. But I just restarted Apache and am still recieveing the same "403 Forbidden". I am very very confused as my file permissions are correct!!

---

### Post by iSplicer on 2008-05-02
> **AustinMarton said:**
> Hi, Since I am not at the physical location of the server I haven't been able to restart it. But I just restarted Apache and am still recieveing the same "403 Forbidden". I am very very confused as my file permissions are correct!!

Dont you have SSH?

---

### Post by AustinMarton on 2008-05-02
Wow! Well just to inform anyone who stumbles across here, these are the few simple commands that cleared up forbidden issues:

```

> mv images Images
> mkdir images
> cp ./Images/* ./images/
> mv backgrounds Backgrounds
> mkdir backgrounds
> cp ./Backgrounds/* ./backgrounds/
> rm -r ./Backgrounds
> rm -r ./Images

```

I still have no clue WHY a new folder with exactly the same permissions works and the old one doesn't, but it works.

---

### Post by nowshining on 2008-05-03
next time try pressing F5 on your keyboard in the nautilus window, etc..

---

