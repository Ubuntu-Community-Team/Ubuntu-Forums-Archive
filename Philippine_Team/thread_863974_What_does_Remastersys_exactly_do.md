---
title: "What does Remastersys exactly do?"
date: 2008-07-19
forum: Philippine Team
---

### Post by adredz on 2008-07-19
does it include my custom settings in the iso as well? like the themes and the installed packages/apps? how about the graphics driver config and the custom settings that depend on it?

---

### Post by loell on 2008-07-19
> **adredz said:**
> does it include my custom settings 

If you wanted to, then Yes. :)

---

### Post by adredz on 2008-07-19
> **loell said:**
> If you wanted to, then Yes. :)

how? just made one by doing "sudo dist remastersys" but i don't know if my custom settings(you know the "blings") were included. well, i just have to try it for me to find out. kaya lng 1G eh, ala me dvd rom, hihiram pa ko sa friend ko haha. i didn't know this powerful tool was just around the corner, i could have saved time when my box messed up..

---

### Post by loell on 2008-07-19
my bad, you can't auto magically include it in remastersys , your custom settings for each programs must be backed up and must be copied to the newly installed system. 

backing your personal settings is in a way a no sweat task, you only have to copy you home folder and just copy it on to the new one.

going back to your original question what does remastersys do?  basically its just writes your installed system on to the ISO, excluding your personal settings.

---

### Post by MattBD on 2008-07-19
> **loell said:**
> basically its just writes your installed system on to the ISO, excluding your personal settings.

Not quite true, you can include these if you run it as:
```
sudo remastersys backup
```
rather than:
```
sudo remastersys dist
```
The dist option creates a distributable version that you can give to others, whereas backup includes all your files, Firefox bookmarks etc and user accounts. I have a heavily customised Ubuntu install with AWN and I used the backup option to create a live DVD based on this, and I have the exact same user account and desktop on this.

---

### Post by loell on 2008-07-19
/covers face in a paper bag. :oops:

---

### Post by adredz on 2008-07-19
> **MattBD said:**
> Not quite true, you can include these if you run it as:
```
sudo remastersys backup
```
rather than:
```
sudo remastersys dist
```
The dist option creates a distributable version that you can give to others, whereas backup includes all your files, Firefox bookmarks etc and user accounts. I have a heavily customised Ubuntu install with AWN and I used the backup option to create a live DVD based on this, and I have the exact same user account and desktop on this.

mmm, interesting. will your graphics card get configured automatically after installing the backup iso? because if it won't, my guess is that all those blings won't be in effect and maybe it could create issues like crashes since your backup iso is supposed to function with graphics card enabled, ryt?

---

### Post by adredz on 2008-07-19
> **loell said:**
> /covers face in a paper bag. :oops:

don't have to. i still appreciate your help..salamat bro :)

---

### Post by MattBD on 2008-07-19
> **adredz said:**
> mmm, interesting. will your graphics card get configured automatically after installing the backup iso? because if it won't, my guess is that all those blings won't be in effect and maybe it could create issues like crashes since your backup iso is supposed to function with graphics card enabled, ryt?

I think it would be configured automatically, but I don't know as all my computers use Intel integrated graphics cards which work out of the box in Ubuntu. Only way to find out is to try it,really.

---

### Post by adredz on 2008-07-19
> **MattBD said:**
> I think it would be configured automatically, but I don't know as all my computers use Intel integrated graphics cards which work out of the box in Ubuntu. Only way to find out is to try it,really.

thanks MattBD, it helps a lot :)

---

### Post by king leoric on 2008-07-19
I have used remastersys and yes you can include your personal setting. If you started remastersys in graphical mode, you can select either to back up you machine or you will make a copy of your machine and distribute it. 

I've used this when I installed ubuntu also on my desktop. (from my lappy). This will ease up my job for installing programs which I wanted or same programs on my lappy.

---

### Post by adredz on 2008-07-19
> **king leoric said:**
> I have used remastersys and yes you can include your personal setting. If you started remastersys in graphical mode, you can select either to back up you machine or you will make a copy of your machine and distribute it. 

I've used this when I installed ubuntu also on my desktop. (from my lappy). This will ease up my job for installing programs which I wanted or same programs on my lappy.

thanks! yes remastersys greatly saves us a lot time especially when our box gets broken. i should have known earlier about this. before i had to do the time and energy consuming fresh install again and again :)

---

### Post by MattBD on 2008-07-19
It's a good idea to have /home on a separate partition as well - this means that things like emails will be safe if your main partition goes belly-up. In case you don't know how to do that, I wrote a guide a while ago, which is at [http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html](http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html)

---

### Post by adredz on 2008-07-19
> **MattBD said:**
> It's a good idea to have /home on a separate partition as well - this means that things like emails will be safe if your main partition goes belly-up. In case you don't know how to do that, I wrote a guide a while ago, which is at [http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html](http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html)

thanks! your howto is great..

---

### Post by Recursion_1209 on 2008-08-23
Hi, I was trying to create a backup of my system using remastersys with dist option. However, when I tried to boot the DVD it was asking for my username and password.

I tried using "custom" as username but I do not know the password. In /etc/remastersys.conf I see this parameter LIVEUSER="custom".

What should be the default password?

---

### Post by ch1c0dj on 2008-08-23
> **Recursion_1209 said:**
> Hi, ...username and password.
Other thread with about this, Check mo ung #5 and #6 reply ni GILF na solve na nya, try mo kung applicable sa setup mo.
[http://ubuntuforums.org/showthread.php?t=688758](http://ubuntuforums.org/showthread.php?t=688758)

---

### Post by Recursion_1209 on 2008-08-24
thanks!

I'll try again later.

---

