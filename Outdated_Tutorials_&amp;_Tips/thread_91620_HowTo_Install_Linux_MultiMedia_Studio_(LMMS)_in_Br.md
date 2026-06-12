---
title: "HowTo: Install Linux MultiMedia Studio (LMMS) in Breezy."
date: 2005-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by mcduck on 2005-11-17
LMMS is a free music studio software, in style of FL Studio. It's not very finished yet, but it sure is nice one to play with. And there aren't too many software studios available for Linux..

**Edit: LMMS can now be found from Backports, so you'll only need to use this howto if you don't want to enable Backports repository.**

Now, there are debian packages available, but they have some dependencies that cause problems with installing to Ubuntu, so it's not going to be as simple as just downloading and installing. Anyway, I managed to do get LMMS running without messing my Ubuntu (If installing some debian packages doesn't count), so if you wish to give it a try here are the steps needed:

********
1. Go to [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/) and download debian packages **lmms_0.0.9+0.1.0rc1-1_i386.deb** and **lmms-common_0.0.9+0.1.0rc1-1_all.deb** to your desktop.

********
2. Now, here comes the complicated part: LMMS needs package libqt3c102mt, but Ubuntu doesn't have a package with that name. Instead we have one called libqt3-mt which does do the job, we only have to edit the lmms package to change it's dependencies..

We'll make a new directory to work in: 
```
cd ~/Desktop
mkdir lmms
cd lmms
```

Then unpack the .deb to a new directory inside our current directory:
```
dpkg-deb -x ~/Desktop/lmms_0.0.9+0.1.0rc1-1_i386.deb lmms_0.0.9+0.1.0rc1-1_i386
dpkg-deb -e ~/Desktop/lmms_0.0.9+0.1.0rc1-1_i386.deb lmms_0.0.9+0.1.0rc1-1_i386/DEBIAN
```

Then we'll run 
```
gedit ~/Desktop/lmms/lmms_0.0.9+0.1.0rc1-1_i386/DEBIAN/control
```
and change 'libqt3c102-mt' to 'libqt3-mt' & save the file. Of course you can use whatever text editor you like to do this ;)

Next do 
```
dpkg-deb -b ./lmms_0.0.9+0.1.0rc1-1_i386
```
to create a new .deb package in ~/Desktop/lmms/

********
3. Then we'll install some dependencies:
```
sudo apt-get install libqt3-mt libsamplerate0 libsdl-sound1.2
```

These worked for me, but if you need any other packages please tell me and I'll add those here.

********
4. Finaly we are ready to install LMMS:
```
sudo dpkg -i ~/Desktop/lmms-common_0.0.9+0.1.0rc1-1_all.deb
sudo dpkg -i lmms_0.0.9+0.1.0rc1-1_i386.deb
```

********
5. run ```
lmms
``` to test that it works. If it doesn't, please don't blame me :)

********
6. If it does work, we'll add it to menu: 
```
sudo gedit /usr/share/applications/lmms.desktop
```
and copy following text there and save.
```
[Desktop Entry]
Name=LMMS
Comment=Linux MultiMedia Studio
Exec=lmms
Icon=/usr/share/lmms/icon.png
Terminal=false

Type=Application
Categories=Application;AudioVideo;
```

That's it. Now you are ready to write your hit song. While doing that you should save after any change as LMMS isn't very stable yet and you don't want to lose your masterpiece when LMMS crashes..

---

### Post by BLTicklemonster on 2005-11-18
Okay, now that that is settled, ummmm, GEE, THIS IS INCREDIBLE! THANKS FOR POSTING THIS!! WOO HOO!!!

Now what do I do with it? Is there an Idiot's guide to how to use it out there anywhere? I had cakewalk (can't find the cd anymore darnit) and never really did much with it, but was told that I could compose music on a sheet (I can read music) and cakewalk would use the sheet music to play what I composed. Is lmms anything like that?

---

### Post by johannes on 2005-11-19
I'm trying to get LMMS use the Jack Audio Connection kit instead of ALSA or OSS. According to the author of LMMS, that makes it NOT use 100% of the cpu resources at all times. (which is a kind of an annoying bug...)

I have gotten it to compile using the jack-dev package, and have set up Jack to run with realtime permissions (added the realtime-lsm module), but I can't get it to work. :mad: If I select the Jack as sound deamon in LMMS, I can connect it to audio out, but there is no sound and the program crashes after some minutes...

Has anybody gotten LMMS to work with Jack?

---

### Post by BLTicklemonster on 2005-11-19
Shoot buddy, I'd be pleased just to know what I'm doing in it. I have no idea what to do, lol. But I'm sure I will one day, so it's there for future use.

What did you do to get where you are right now? I'd like to try it, too.

---

### Post by mcduck on 2005-11-20
Thanks BLTicklemonster, I fixed those things you mentioned. :)

johannes: Please tell me If you get it working. Altough running at 100% CPU isn't such a problem for me, it would be nice if using Jack would fix that. Anyway, it would allow me to use some effects too, as LMMS doesn't yet have any. :rolleyes:

I think I'll have to try to get Jack working and then see if I have any success with LMMS and Jack.

---

### Post by BLTicklemonster on 2005-11-20
MCDUCK, no problem. Would you re-read my first post please? Apparently you know how to use the program, and I want to.

---

### Post by mcduck on 2005-11-21
It seems that there isn't any manuals for LMMS yet, but it has lots in common with FL Studio (alias FruityLoops), so maybe you could try some FL-Studio-101-tutorials to get you started..

LMMS doesn't read music sheets like Cakewalk does, it's more oriented towards electronic music. Instead you have a step sequencer for beats and percussions and a piano roll for everything else. But yes, you can compose music with LMMS and it can play it back or export as audio file.

---

### Post by theToolman on 2005-11-30
[QUOTE=mcduck]
... and change 'libqt3c102mt' to 'libqt3-mt' & save the file. [/QUOTE]

For the sticklers, I believe that 'libqt3c102mt' should be 'libqt3c102-mt'; at least with lmms_0.0.9+0.1.0rc1-1_i386,  lmms_0.0.9+0.1.0rc1-1_i386.deb

Otherwise, looks like ti is going :D

---

