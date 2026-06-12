---
title: "[SOLVED] Amarok issues"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by burnetbj on 2008-11-17
Hi folks

I am running Hardy with a pretty fresh install, installed Amarok like always but this time I seem to be missing something. I have enabled all the gstreaming I could possibly find the bad the ugly , fugly filthy i mean everything. I cant get .Mp3 to run. I have installed Ubuntu extras. I just now ran non-free codecs such as w32 all all the goods .....what the heck could i still be missing. 

Thanks

---

### Post by SuperSonic4 on 2008-11-17
Have you checked the xine engine? I know amarok uses the xine engine to run

---

### Post by burnetbj on 2008-11-17
Hi 

Thanks for the help 

I do have the xine engine selected as default and i do have the libxine and such installed

Is there a command i can run to help show what i got ?

---

### Post by gychang on 2008-11-17
I am interested in playing .flac files, can this be done in Amarok?  I have tried rhythmbox and it does but Amarok look more sophisticated.

gychang

---

### Post by burnetbj on 2008-11-17
I do have some Flac files and I am pretty sure I have played them fine in Amarok. I think I have some let me try on my desktop and I can let you know the out come

---

### Post by SuperSonic4 on 2008-11-17
flac are working on my box in amarok (kubuntu 8.04)

I have lame and liblame installed. It usually prompts you to install mp3 support in amarok =S

---

### Post by jenkinbr on 2008-11-17
install the libxine1-ffmpeg package.
```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by burnetbj on 2008-11-17
thanks for the help 

I can verify I do have that installed most current version it says

---

### Post by jenkinbr on 2008-11-17
and that did or did not fix it?

---

### Post by burnetbj on 2008-11-17
No sir 

Amarok wont play anything, dang thing I havent had this problem before. Think Im gonna reinstall Hardy but I need to understand what went wrong. At somepoint I would like to stop reinstalling every three weeks hahaha 

I have installed so many things I really havent got to sit back and enjoy myself heh. Seems to alway work after installing the restricted extras

---

### Post by burnetbj on 2008-11-17
Hmmmmm

I cant even direct it to play a standard CD  .wav

---

### Post by gychang on 2008-11-17
> **SuperSonic4 said:**
> flac are working on my box in amarok (kubuntu 8.04)

I have lame and liblame installed. It usually prompts you to install mp3 support in amarok =S

how do I go about installing lame and liblame?

gychang

---

### Post by jenkinbr on 2008-11-18
sudo apt-get install lame liblame0

This should do it in hardy (you said hardy, right?

for intrepid, do

sudo apt-get install lame libmp3lame0

---

### Post by gychang on 2008-11-18
> **jenkinbr said:**
> 
for intrepid, do

sudo apt-get install lame libmp3lame0

Great!, I will try it tonight.  I like to play my flac files in Amarok if possible.

gychang

---

### Post by gychang on 2008-11-18
> **jenkinbr said:**
> 

for intrepid, do

sudo apt-get install lame libmp3lame0

problem in the intrepid:

--
apa@ubuntu:~$ sudo apt-get install lame libmp3lame0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lame libmp3lame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 351kB of archives.
After this operation, 946kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse lame 3.98-0.0 [219kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse libmp3lame0 3.98-0.0 [132kB]
Fetched 351kB in 2s (129kB/s)       
dpkg: status database area is locked by another process
E: Sub-process /usr/bin/dpkg returned an error code (2)
--

what do I do now?

gychang

---

### Post by Kinetic Being on 2008-11-18
maybe try uninstalling amarok and reinstalling it. when i upgraded to 8.10 it broke amarok, I gave up, uninstalled it, and tried some other programs. I ended up trying to get amarok back working (I love those global shortcuts too much) and reinstalled. It fixed everything...

```
sudo apt-get remove --purge amarokapp
```
```
sudo apt-get install amarokapp
``` 

It might just be "amarok" and not "amarokapp" but I know thats what you have to use to kill it and I think uninstall it. If it doesn't work, replace "amarokapp" with "amarok". I am sorry, I can't recall exactly what it is, I've been smoking...but I don't think this could hurt your computer in any way.

---

### Post by jenkinbr on 2008-11-19
Your apt database seemes to be locked by another apt session.  Did you have synaptic, Add/remove, update-manager, or some other program interfering?

BTW, you have a line that reads ```
1 not fully installed or removed.
```
Try running ```
 sudo apt-get install -f
```
to fix whatever did not completely get installed before continuing.

---

### Post by burnetbj on 2008-11-22
OK 

I feel like killing my system right now. I have been messing with this problem off and on now for a few days, i got 7 PC's but this one was killing me. I still couldnt get anything to work for my Amarok playing Mp3's I hadnt had this issue before but I got it fixed now. To sum things up here what happened was I couldnt get my wireless to work with 8.10 so I reformatted and put 8.04 back on but Amarok wouldnt work so I was testing from a flash drive I had with a Box set of the Sex Pistols on. Well I kept getting error after error so I reinstalled 8.10 cause I can live without wireless but not Music

Well after the reinstall I was having the same issue with 8.10 and Amarok and I couldnt for the life of me figure out what I was missing. So after reinstalling 8.04 and 8.10 and countless codecs. The root cause is this for some crazy reason when my first system copied the Boxset over It made the folders and song listings but theres no data to the songs everything is listed but its only 380kb when it should be about 3Gb ......WTF!!! 

Anyhow it was me the entire time....Thanks for all the help people

---

### Post by go_beep_yourself on 2008-11-24
Try changing your icon set with kcontrol

---

