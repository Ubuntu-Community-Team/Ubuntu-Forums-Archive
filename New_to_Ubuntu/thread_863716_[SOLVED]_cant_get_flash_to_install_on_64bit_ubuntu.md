---
title: "[SOLVED] cant get flash to install on 64bit ubuntu"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by nachosDP on 2008-07-18
im fairly new to ubuntu and cant get flash to install, I had it installed and working except for the audio then i tried a line of code from a forum to fix it and then flash stoped working altogether and i cant get it back.
the line i ran was
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

---

### Post by SunnyRabbiera on 2008-07-18
flash on a 64 system is crap I must warn you, many have issues with it, blame adobe for not having 64bit support

---

### Post by nachosDP on 2008-07-18
i know it has been really really frustrating, im about to reinstall with 32bit so things will actually work right. Im alredy useing 32bit firefox.  i really dont want to have to do that though i spent so much time seting this thing up.  
And there is a vista64 disc staring me in the face!!!!(what a waste)

---

### Post by SunnyRabbiera on 2008-07-18
Yeh 64bit support is shoddy at best at this stage, not our fault though.

---

### Post by SuperSonic4 on 2008-07-18
[color=#007fff]The sticky in Multimedia and Video worked for me, giving me flash, it just wouldn't give me a working Java and that made me roll back to 32bit Kubuntu[/color]

---

### Post by nachosDP on 2008-07-18
I dont know what a sticky is. I dont understand though. it worked before. when i go to youtube and try to install missing plugins it says that adobe flash is not avalable and if i go to manual install from adobes website it says it installs but nothing happens (tar.gz file) i tried complete romoval and reintall from the package manager and still nothing.  its firefox32 it should still work

---

### Post by SunnyRabbiera on 2008-07-18
a sticky topic, one that is at the top at the top all the time

---

### Post by nachosDP on 2008-07-18
ahh ok.  i went to the topic compreshensive multimedia how to, and after the second line of code instructed it did this 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages               
99% [Connecting to packages.freecontrib.org (34.52.53.34)]                     
99% [Connecting to packages.freecontrib.org (34.52.53.34)]
99% [Connecting to packages.freecontrib.org (34.52.53.34)]

(i hit enter 2 times cause it seemed stuck) then

Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg    
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg    
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Fetched 23.5kB in 2min0s (195B/s)                         
Reading package lists... Done
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/Release.gpg)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

ok so i run sudo apt-get update and the same thing happens the connection times out and fails update 

also in the the thread; IMPORTANT: If you haven't already, you need to enable the Medibuntu repository. yeah thats just a dead end to a website that dosent work

im also having trouble with the updates the update manager tries to install seems to be a issue with the server possibly?

---

### Post by SuperSonic4 on 2008-07-18
[color=#007fff][Here]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java") is a guide for installing firefox 3 in 32bit. If you download the script [[link]]("http://home.comcast.net/~ubuntume/ff32_3in1_6293.tar.gz") and drag the extracted file to a terminal it will do it for you prompting you to install flash[/color]

---

### Post by RomeReactor on 2008-07-18
Hi. Did you re-install Ubuntu 32 bit, or are you still using 64 bit? If it's 64 bit, do you still have Firefox 64 bit installed? If you still have 64 bit Firefox, try this:
```
sudo aptitude purge mozilla-plugin-gnash && sudo aptitude install flashplugin-nonfree libflashsupport
```
And try 64 bit Firefox again. In many cases not having sound in Flash is due to not having libflashsupport installed. Also, the Gnash plugin interferes with Flash, so it's not a good idea to have both installed.

It's important to note that having mixed repositories is not a good idea; you seem to have Hardy and Dapper repositories in your sources.list.

As a comment, the level of usability and dependability in Ubuntu 64 bit in general, and Flash in 64 bit Firefox in particular, is an experience that varies from user case to user case. Not everyone has issues with it.

---

### Post by nachosDP on 2008-07-18
no im still running 64bit ubuntu amd yes i still have 64bit fire fox installed and i did a complete removal of gnash in the package manager. im at another computer and will try your code when i get back. thank you

---

### Post by nachosDP on 2008-07-20
that worked great for 64bit firefox except still no sound video is a good start though.
tomarow i am going to try useing my sound card insted of the m-audio usb sound hub midi interface 
thank you very much
if you have any tips on getting the sound working please let me know

---

### Post by RomeReactor on 2008-07-20
Before changing sound cards, go to 'System->Preferences->Sound' and change all the drop down menus in the 'Devices' tab to **PulseAudio Sound Server**. Also, open Firefox, start playing a YouTube video, then open a terminal and run:
```
alsamixer
```
and see if any channels are muted or with a very low volume; play with those and see if increasing the volume of a particular channel lets you hear the audio.

There are graphical interfaces for alsamixer so you don't have to use it from the terminal:
```
sudo aptitude install gnome-alsamixer
```
You can then find it in 'Applications->Sound & Video->GNOME ALSA Mixer'.

---

### Post by nachosDP on 2008-07-28
got video! got sound!  
thank you very very much
next project is to get guitar rig sessions I/O working

---

### Post by JG6_oddball on 2008-09-28
I have not had flash working since i upgraded to 8.04...but I got it working today :):):) here is what i did toget flash working in my 64bit Kubuntu
(i hope i have the order correct)
```
sudo apt-get remove -y --purge flashplugin-nonfree
```
```
sudo apt-get autoclean
```
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get install flashplugin-nonfree
```
```
cd /usr/lib/nspluginwrapper/x86_64/linux 
```
```
./npconfig -v -a -i
```

after that i have flash working :):)

I hope this helps somebody

S!

---

