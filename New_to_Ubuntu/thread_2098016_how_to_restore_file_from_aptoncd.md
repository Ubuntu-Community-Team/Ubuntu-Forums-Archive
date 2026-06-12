---
title: "how to restore file from aptoncd"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by arnav803 on 2012-12-25
hi.i have ubuntu 11.10. isntalled on my desktop as well as laptop .My problem is that i dont have internet connection on my desktop so i made a installation disc via aptoncd on my laptop and tried to restore files from it on my desktop it restored all files succesfully but i cannot find packages like vlc installed on my system please help.Thanks in advance.

---

### Post by 2F4U on 2012-12-25
As far as I understand, the default behaviour of AptOnCD is to select packages from the apt cache. Was VLC present in the apt cache on the laptop at the time you made the selection?

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-25
First things first.

How are you restoring your files?  If you don't have internet,then you couldn't install aptonCD on your other computer, and you wouldn't be able to simply hit the restore button.

So, 2 solutions (though they come with some questions embedded)

1 - Add the CD into software sources and install from there!

open software-center and change sources in the menu to include the CD you have in the CD drive (or USB or DVD or whatever) and reload, and install from there using your preferred method (synaptic, apt-get in terminal, or i suppose, searching for each program in the software-center)


2 - Are you making an exact copy of your system (all the same programs?) in the same format (VERY IMPORTANT) 32 bit or 64 bit
if so... you can manually copy everything... Open up nautilus with super user capabilities
```
gksu nautilus
``` navigate to your/var/cache/apt/archives and copy EVERYTHING to your DVD, CD, USB, (external HD, etc..).  
Then on the other computer open your terminal (Ctrl + Alt + T), navigate to your media 
```
cd /media/<whatever the cd shows up as>
```
then 
```
sudo dpkg -i *.deb
```


I would highly suggest not using the second solution unless you know exactly what you are doing and feel very confident that you understand the commands I have posted.

Cheers and Merry Christmas!

---

### Post by youWho on 2013-02-15
If you look at the comments in /etc/cron.daily/apt you would think that by default the apt cache is not automatically cleaned, but actually (if I'm understanding this correctly, and I think I am) because of the file /etc/apt/apt.conf.d/20archive files *are* in fact being deleted from the cache. Either when the cache reaches 500MB or when a package is older than 30 days. I think many people beliave that they have in their cache everything that they ever installed, but it's not necessarily so.

I've changed both "APT::Archives::MaxAge" and "APT::Archives::MaxSize" to "0" to disable that, and at the moment I have a cache that's about 2.4 GB.

---

