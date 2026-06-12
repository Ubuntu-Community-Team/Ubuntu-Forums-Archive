---
title: "Resetting the GWM"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by ben6 on 2013-08-10
[http://imgur.com/coUQxU4](http://imgur.com/coUQxU4)

As you can see from the picture above the right side of my window manager fades out to transparent and I hate it! Is there anyway I can fix it? I don't remember what settings I used to get it like that but I would be willing to lose all current unity settings and configs to fix it I already tried unity-tweak --reset-unity I deleted alot of gmone2,gmone, compiz files also any help would be greatly appreciated

---

### Post by Linux90s on 2013-08-10
have you tried deleting the .compiz and .config folders in /home/username ?

make a backup first though!!!

eg.

cd ~/
mkdir _old_settings
cp -fr .compiz _old_settings 
cp -fr .config _old_settings

log out of the gui

ctrl+alt+f1

login to the command line interface

cd ~/    <----this command changes to your home directory (safer as we are going to use "rm -fr")
rm -fr .compiz
rm -fr .config

reboot ... (they will be recreated by the system)

REMEMBER:- the .config folder contains settings for other applications, but since you backed them up, you can always
copy them back to /home/username one by one, but it's easier to troubleshoot without any of them there...

ccsm is the quick command for the compiz settings manager

gd luck

---

### Post by ben6 on 2013-08-10
Well looks like we can rule out that it is a user config setting since that didn't work. Thanks for trying.

---

### Post by Linux90s on 2013-08-10
Just on a side note - when i upgraded my distro from 12.10 to 13.04, i had issues with my Radeon HD audio and desktop cube, i spent alot of time resetting unity and trying various drivers, in the end, i did a clean install after backing up my home directory onto another and added only my documents, pictures etc. back, not the previous home directory in it's entirety (including hidden folders & settings) and it worked fine, the only thing i added later on was the proprietary amd drivers from their website.

I tried various fixes first as it's all a part of troubleshooting and learning more about the Ubuntu experience.

Maybe a clean install would be a good idea but to find the actual cause for future reference, make a backup of your config files so you can compare the differences and find the culprit.

gd luck

---

### Post by Linux90s on 2013-08-10
ps. i had a seperate partition for /home and /var ... clearing /var was key for my new install ... my issues were somewhere in there.

---

### Post by Linux90s on 2013-08-11
How to make Window Title Bar Transparent in Ubuntu 

[https://www.youtube.com/watch?v=xujflyr0ci8](https://www.youtube.com/watch?v=xujflyr0ci8)


Transparent Title Bar: Ubuntu 13.04 

[https://www.youtube.com/watch?v=-TI96I8Im5w](https://www.youtube.com/watch?v=-TI96I8Im5w)

---

