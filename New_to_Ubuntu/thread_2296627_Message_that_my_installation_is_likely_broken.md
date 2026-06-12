---
title: "Message that my installation is likely broken"
date: 2015-09-27
forum: New to Ubuntu
---

### Post by yash_pal2 on 2015-09-27
When updating Ubuntu 14.04 today, (27 Sep in India), the following message was part of updating:
```

(gtk-update-icon-cache-3.0:7966): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory
This likely means that your installation is broken.
Try running the command

gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache

to make things work again for the time being.
```



I ran:


```
yashpal@yashpal-Inspiron-M5010:~$ [COLOR=#800080]sudo   gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```


The response was:


```
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied

yashpal@yashpal-Inspiron-M5010:~$ 
```

I can run the system, access the net (Firefox), mail (thunderbird), writer, GIMP etc.

I do not have any computer games, no facebook or faceless book; no whats app, no PPAs; in short, only essential apps.

Will this message hamper my normal functioning and if so, how to fix it.

Could anyone enlighten me please. I will upgrade to 16.04 when it is released.

Also, it is a dual boot with Windows 7 and Windows 7 is corrupted and the key is not available and it just sits there.

---

### Post by QIII on 2015-09-27
Hello!

Please use the default color and font.

Also, please use code tags to enclose terminal commands and output:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by grahammechanical on 2015-09-27
Have you restarted the system yet. That is when you will find out if the system really is broken. I have been running the development version of Ubuntu for about three years and I have seen that message a few times and only once has the OS actually been broken. I fixed it by going to Advanced options for Ubuntu>recovery mode>Root and entering that code that has been given. We get out of recvoery mode by typing Exit and then selecting resume.

You can use the File Manager to see if loaders.cache exists on your system. It should be at /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/

If it is present there should not be any problems. I think.

Regards.

---

### Post by yash_pal2 on 2015-09-27
QIII, Noted for future. Actually, I do not use the forums much and have copied the instructions to refer to before posting in future.
Thanks.

---

### Post by yash_pal2 on 2015-09-27
It was restarted after update and again now. No difficulty was experienced. Should I ignore the message? 
I just do not fiddle with the OS as I do not have ability to fix it. Anyway, I have copied your reply for future reference and will do nothing if that is the safest course.
Thanks.

---

### Post by mc4man on 2015-09-27
Basically nothing to worry - 
[https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1282294](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1282294)
(- running that command isn't harmful, has to be from a root terminal (sudo -i), but can just be ignored also

---

### Post by yash_pal2 on 2015-09-27
Thanks.

---

### Post by Starfleet on 2015-10-15
Yash, or anyone else who has this issue...it's most likely the pixbuf loader is missing. It throws up exactly the same message you are getting. It's easy to fix by doing the following: first open a terminal by pressing Crt, Alt, & T. Next go to root by typing ```
sudo su
```. At the cursor type ```
apt-get install libgdk-pixbuf2.0-dev
```. Note you do not need to type 'sudo' first as you are already at root. This will install the missing loader. This totally cures the problem and is permanent.

IMPORTANT EDIT: I've just experienced a problem logging in after doing the above to my own computer. It may be that I've caused the problem by using the above commands. I'll post back when I've investigated further but do not follow these instructions for the time being.

---

