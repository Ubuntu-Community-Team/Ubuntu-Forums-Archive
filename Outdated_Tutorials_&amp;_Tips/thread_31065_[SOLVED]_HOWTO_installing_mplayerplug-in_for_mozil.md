---
title: "[SOLVED] HOWTO: installing mplayerplug-in for mozilla"
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-05-01
**EDITED**
Please refer to [http://ubuntuforums.org/showthread.php?t=44560](http://ubuntuforums.org/showthread.php?t=44560)
This is the most updated way to install mplayerplug-in

---

### Post by Seti on 2005-05-20
Alright I have mplayerplug-in working in Firefox, but I get no sound when watching movie trailers. I tried chmod 755 /dev/dsp, but still no sound. Any thoughts?

---

### Post by arnieboy on 2005-05-20
Have u copied all the windows codecs to /usr/lib/win32 ? The codecs are available from:
[http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/essential-20050412.tar.bz2)

---

### Post by f.prisson on 2005-05-22
Did you choose the correct output method (alsa,arts,esd)? Have a look at```
/etc/mplayerplug-in.conf
```

---

### Post by Seti on 2005-05-26
Thanks a lot for your help! It was those codecs that I needed.

---

### Post by Gouchi on 2005-05-28
Just to say that MPlayer Setup now support MPlayerplug-in installation  ;-) 

You can grab it in here :
[http://nyal.developpez.com/mplayer](http://nyal.developpez.com/mplayer)

P.S = New directory codec is /usr/local/lib/codecs, /usr/lib/win32 is to keep compability with others players.

---

### Post by jafanet on 2005-05-28
hmm, this didn't seem to work for me arnieboy, the MPlayer installation guide that you provided seemed to work fine however. 

I'm not sure where to start to check to see how far the plugin installation got, any ideas?

---

### Post by 1337sithlord on 2005-05-28
It asked for the cd when i tried it the old way lol thx

---

### Post by Gouchi on 2005-05-29
> I'm not sure where to start to check to see how far the plugin installation got, any ideas? 

type about:plugins  in the url and check if MPlayerplug-in is there.

---

### Post by arnieboy on 2005-05-29
[QUOTE=jafanet]hmm, this didn't seem to work for me arnieboy[/QUOTE]

if u dont find the mplayer plugin after typing "about:plugins" u should let me know what exactly went wrong in the installation (that is what error u got)
-arnieboy

---

### Post by cudaman73 on 2005-05-29
Well, I'm having problems getting the howto to work. I believe that my problems are unrelated though.

I get this -

```
m3r1k@m3r1kb0x:~/mplayer$ sudo alien mplayerplug-in-2.80-1.FC3.i386.rpm 
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 488.
Package build failed. Here's the log:
find: mplayerplug-in-2.80: No such file or directory
```

however, it did create the dir, look.

```
m3r1k@m3r1kb0x:~/mplayer$ ls
mplayerplug-in-2.80  mplayerplug-in-2.80-1.FC3.i386.rpm
```

Upon running it again, with the dir already created from the first run, i get the same error, plus 'cannot create file/directory: file exists', which makes sense, i suppose. Any ideas?

---

### Post by arnieboy on 2005-05-29
the first step would be to download the rpm again and try and build the .deb file. It seems like the downloaded file has a problem.
Do u have mplayer installed?

---

### Post by hardwarder on 2005-05-30
I'm having a problem with the plug-in. Firefox doesn't seem to detect it. Could it be a conflict with the CrossOver Office plug-ins?

---

### Post by arnieboy on 2005-05-30
firefox will detect the mplayerplug-in irrespective of whethere it has the crossover office plugins installed or not. The order in which the plugins are set up will decide the hierarchy of preference of an app for the same kind of file.
I will suggest u download and install the plugin again after making sure u have mplayer properly setup.

---

### Post by 1337sithlord on 2005-05-30
on second thought, now that i actually tried to play a file that way, it still doesnt work lol.  Thats becuase i dont have mplayer on my desktop and u said to only get the plugin if u have mplayer already.  Well how do u get that?  On ubuntuguide it has code to get both but it asks for a cd, so how do i get the mplayer so i can try getting the plugin this way?

---

### Post by arnieboy on 2005-05-30
in terminal do a :
sudo gedit /etc/apt/sources.list

when the sources.list file opens up **look for the first line ** which says:
**deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)] / hoary main restricted**
Change this line to :
**## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)] / hoary main restricted**

save the file and exit.
Now when u install any app with apt-get it wont ask for the cd but will get all files directly from the internet.

Hope this helps.
-arnieboy

---

### Post by 1337sithlord on 2005-05-30
oo thx alot.  It doesnt ask for the cd when i install mplayer.  It also doesnt work, because it said all sorts of things about broken packages.  I wont worry about that tho cause i dont need any more media players.  I was gonna use mplayer so id be able to install the dvd ripper but i already got a good program like that for windows so  im good.  And that code helped with mozilla thunderbird too.  It previously asked for the cd but now it doesnt so i was able to install it perfectly :)

---

### Post by arnieboy on 2005-05-30
Nice to know that you found my tip useful. In case you ever feel like installing mplayer you can visit the following thread:
[http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061)

So long.

---

### Post by 1337sithlord on 2005-06-01
Ok, i read that and im in alot of trouble with hard drive space right now lol.  Im gonna reinstall ubuntu cause sudo apt-get remove can only take me so far.  Theres alot of stuff that i wont be able to delete.  For next time... what is the least amount of space than mplayer can take up?  Id like to install just the player and possibly the firefox plugin, with as few codecs and extras with it as possible.

---

### Post by arnieboy on 2005-06-01
I cant give u an exact figure simply because it depends on how many dependencies need to be installed and how many u already have installed. Ideally, from my experience, you would be well off if you keep a 10 GB partition for the ubuntu root partition. That way u will not run out of space so fast. U can store all movie and sound files on ur windows (FAT32) partition to save more space.

---

### Post by Seti on 2005-06-03
I had this working perfectly before but then reinstalled Hoary because I wanted it on a different partition. So, installation went perfectly, and now, I tried to install the mplayerplug-in again following the instructions exactly; installed mplayer first, then the plugin from the .deb made out of the rpm using alien. Now it doesn't work at all. I made sure I have the codecs in /usr/lib/win32, and made sure I copied the plugin to /home/me/.mozilla/plugins. Also verified that /etc/mplayer/mplayer.conf is correct. Nothing. And about:plugins shows me it isn't installed. 
 ](*,)

---

### Post by Seti on 2005-06-03
OK, seriously, now, I've tried everything I thought would work. I've come to the conclusion that watching these little movie trailers over at [http://www.apple.com/trailers/](http://www.apple.com/trailers/) isn't worth the amount of time I have put into trying to get mplayer to work.
I've followed a few of the various tutorials and howto's on this forum and nothing worked. I'm beginning to think that things have changed and maybe some of the instructions just don't apply anyore??
For instance, I even tried to install it from source, FOLLOWING THE INSTRUCTIONS, and I got as far as it telling me I needed gecko sdk something or other. 
I hate for this to sound like a rant, but I think the howto's need to be updated, and the info consolidated, cause there's a lot of us out there trying to do this and getting nowhere.

---

### Post by raz on 2005-06-12
Followed your guide on make'ing mplayer from source, worked great, thanks.

Now this one is troublesome..

No errors, but won't show under firefox's plugins.
```

$ sudo alien mplayerplug-in-2.80-1.FC3.i386.rpm
mplayerplug-in_2.80-2_i386.deb generated
$ sudo dpkg -i mplayerplug-in*.deb
(Reading database ... 72976 files and directories currently installed.)
Preparing to replace mplayerplug-in 2.80-2 (using mplayerplug-in_2.80-2_i386.deb ) ...
Unpacking replacement mplayerplug-in ...
Setting up mplayerplug-in (2.80-2) ...
```

Any ideas?

TIA,

-r

---

