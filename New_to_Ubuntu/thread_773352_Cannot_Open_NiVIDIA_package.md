---
title: "Cannot Open NiVIDIA package"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DarthOpto on 2008-04-28
I am trying to install the latest NVIDIA driver which is 169.12. 
I downloaded it from NVIDIA
Close the GUI with CTRL + ALT + F1
Login 
then 
sudo /etc/init.d/gdm stop

then I type the following as instructed from NVIDIA

sh NVIDIA-Linux-x86-169.12.pkg1.run

When I hit ENTER I get that sh cannot open the file

Any thoughts?

I have upgraded to hardy if that matters

---

### Post by nowshining on 2008-04-28
you need to use sudo

+

you need to cd to the location of the driver first or type the path

if it's on your Desktop

1st: sudo /etc/init.d/gdm stop

sudo sh /home/username/Desktop/NVIDIA-Linux-x86-169.12.pkg1.run

change username to your username.

while inputting your password rem. it won't show as you type as this is a security issue and just type it out as usual and press enter.

Follow the directions.

then issues,

sudo /etc/init.d/gdm start


alto you can use the TAB key for completion of paths & filenames.
ex: 

/home/now

TAB

/home/nowshining

/

De

TAB

/home/nowshining/Desktop

/

Nvidia

TAB

/home/nowshining/Desktop/NVIDIA-Linux-x86-169.12.pkg1.run

---

### Post by Anduu on 2008-04-28
Make sure the file is executable and try running it with sudo.

---

### Post by dearingj on 2008-04-28
First of all - you'd be surprised how often this is the problem - are you in the right directory? I believe Firefox by default puts downloaded files on the desktop, but when you log in you start in your home directory.

If you are in the right directory, have you tried running the command
```
chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```

[edit: looks like a few people beat me to the punch :) i wish ubuntuforums would let people delete duplicate posts like this]

---

### Post by DarthOpto on 2008-04-28
Thank you very much. 
I was able to get it installed and up and working. 
Another issue I seem to have is some files stuck in my recycle bin. How do I get rid of them. I have tried emptying my recycle bin repeatedly and the files still seem to be there.

---

### Post by nowshining on 2008-04-28
they may be root privelaged, and I heard that the .trash folder was moved in ubuntu in hardy heron, so you'll have to find that folder and it's location, change the permissions on the file and or files or find the location of the folder/trash folder and in the terminal

sudo chown -R username:username pathtofolder

change username and username to your username and pathtofolder to the path to the trash folder.

---

