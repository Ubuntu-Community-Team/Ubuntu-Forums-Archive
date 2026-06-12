---
title: "How to install pSX 1.13 on ubuntu"
date: 2008-09-24
forum: Outdated Tutorials &amp; Tips
---

### Post by rfrayer on 2008-09-24
get the dependancies 

```
sudo aptitude install libgtkglext1-dev
```

then do this 

mkdir -pv ~/.pSX/cards

touch ~/.pSX/cards/1.mcr && touch ~/.pSX/cards/2.mcr

```
cd $HOME

wget http://easyweb.easynet.co.uk/~david.s/saturn/images/Playstation_icon.gif

sudo mv Playstation_icon.gif /usr/share/pixmaps

wget http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2

tar xjvf pSX_linux_1_13.tar.bz2

sudo mv pSX /opt
```


I can't tell you where to get it but do a google search for index of scph1001.bin


```
sudo mv scph1001.bin /opt/pSX/bios

sudo gedit /usr/bin/pSX
```

Paist this code in it then save

```
#!/bin/bash

cd /opt/pSX
./pSX
```

```
sudo chmod 755 /usr/bin/pSX
```


Now to add it globally to your menues

```
sudo gedit /usr/share/applications/pSX.desktop
```

paist this code in and save

```
[Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Name=pSX Emulator
Comment=Play Playstation games on your PC!
Icon=/usr/share/pixmaps/Playstation_icon.gif
Exec=pSX
Terminal=false
StartupNotify=false
Categories=Game;Emulators;
```

should be all set!!

---

### Post by rfrayer on 2008-09-28
or even better yet skip all the above i rolled a deb package and it will get your dependancies etc. It says hardy but both dependancies are exactly the same in gutsy and hardy so it should go both ways


sorry removed my repository got to many hits

---

### Post by rfrayer on 2008-09-28
I also have a few other debs ive rolled here [http://ubuntu.global-web.us](http://ubuntu.global-web.us)

---

### Post by Meizulo on 2008-10-01
I followed your install and everything looks like it went well, but psx will not load???

HARDY amd64 user

I just found the error, but still need help

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

---

### Post by rorymullan on 2008-10-01
Thanks for the tutorial. Works perfect for me:D

---

### Post by Meizulo on 2008-10-01
Ok... so I reinstalled Ubuntu 8.04 LTS, but instead od using the amd64 version I am running the i386.

---

### Post by rfrayer on 2008-10-01
> **Meizulo said:**
> Ok... so I reinstalled Ubuntu 8.04 LTS, but instead od using the amd64 version I am running the i386.

did all go with that if its still saying that error try this 
sudo aptitude install libgtkglext1-dev if that dont work try sudo apt-get install libgtkglext1

---

### Post by binbash on 2008-10-02
> **rfrayer said:**
> or even better yet skip all the above i rolled a deb package and it will get your dependancies etc. It says hardy but both dependancies are exactly the same in gutsy and hardy so it should go both ways.


[http://ubuntu.global-web.us/hardy/binary/pSX-1.13-ubuntu-hardy2.deb](http://ubuntu.global-web.us/hardy/binary/pSX-1.13-ubuntu-hardy2.deb)

Deb works perfect here, thanks

---

### Post by rfrayer on 2008-10-06
> **binbash said:**
> Deb works perfect here, thanks


Not a problem... Anything i can do to give back to the comunity of the OS that has taught me so much

---

### Post by arapozo on 2008-10-07
Will this work on hardy 64 bits?

---

### Post by rfrayer on 2008-10-10
yes it will work on hardy 64 providing you have the extra repositorys backprorts or wherever the depenednicies are at when you go to install the deb

---

### Post by benhur99ph on 2008-11-19
hey! thanks for this! works great! I encountered a little issue with compiz but its nothing. I just turn compiz off when I play.

---

### Post by dkrus on 2008-11-20
Trying this in 8.10, I got it installed, I get the language thing when I click ok it doesnt work, I see the psx on the bottom for couple of seconds and it just disappears. Got it to work but cant click on the file menu to choose cd .

---

### Post by mocha on 2008-11-20
I was just curious, do you folks not use PulseAudio on your systems?  Because I found on my system that pSX is incompatible with PulseAudio so pulse needs to be killed before using pSX.

---

### Post by dashnak on 2008-11-29
Whenever I run pSX, it's slow as hell, as if it was rendering completely by SW. As far as I know, it makes use of openGL if it finds it. ePSXE works fine in Linux, as well as pSX in Windows. My card is an intel950. Compiz is disabled. Any ideas?

---

### Post by Zamfire on 2009-02-22
"
then do this 

mkdir -pv ~/.pSX/cards

touch ~/.pSX/cards/1.mcr && touch ~/.pSX/cards/2.mcr
"

im new to ubuntu, and maybe someone can spell this out to an idiot like me, but do i actually paste this into the terminal? both together? or one at a time?
because when i do paste them in there, together and otherwise, nothing happens. now for arguments sake i did try it, then continue on, but to no avail. i even got the "pSX Emulator" in the games tab on my menu, which is great, but when i click on it....nothing happens. im sure someone as dumb as me frustrates you all, but please, im new to ubuntu, and i would love some help. thanks!

---

### Post by mocha on 2009-02-22
> **Zamfire said:**
> "
then do this 

mkdir -pv ~/.pSX/cards

touch ~/.pSX/cards/1.mcr && touch ~/.pSX/cards/2.mcr
"

im new to ubuntu, and maybe someone can spell this out to an idiot like me, but do i actually paste this into the terminal? both together? or one at a time?
because when i do paste them in there, together and otherwise, nothing happens. now for arguments sake i did try it, then continue on, but to no avail. i even got the "pSX Emulator" in the games tab on my menu, which is great, but when i click on it....nothing happens. im sure someone as dumb as me frustrates you all, but please, im new to ubuntu, and i would love some help. thanks!

The first command is just saying to make a directory "/home/USERNAME/.pSX/cards".  The second command is saying to make files in the cards directory called 1.mcr and 2.mcr.  You can do all of this in the file manager GUI if you want.  If you run the emulator in a terminal you'll find out why it isn't running.  Just copy the launch command from the menu item, run it in a terminal window, and see what the error message is.

---

### Post by tritoch721 on 2009-09-17
i have also had trouble installing psx 1.13 on ubuntu 8.04 and finally found an easy way to fix this. All u have to do is download this file d3dx9_26.dll and copy it into your windows 32 folder in wine. afterwards just open the emulator normally and should work fine.

---

### Post by rfrayer on 2009-09-20
> **mocha said:**
> I was just curious, do you folks not use PulseAudio on your systems?  Because I found on my system that pSX is incompatible with PulseAudio so pulse needs to be killed before using pSX.


yes i use pulseaudio . what this script does is disables it plus keeps it from respawning wile the games plays

---

### Post by Saghaulor on 2009-09-29
I keep getting this message every time I try to load pSX.

```
stephenaghaulor@stephenaghaulor-desktop:~$ pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

```

But it's there, or at least I think it's there.

```
stephenaghaulor@stephenaghaulor-desktop:/usr/lib$ find libgtkglext-x11-1.0.so.0
libgtkglext-x11-1.0.so.0

```

```
stephenaghaulor@stephenaghaulor-desktop:~$ ls /usr/lib | grep libgtkglext-x11-1.0.so.0
libgtkglext-x11-1.0.so.0
libgtkglext-x11-1.0.so.0.0.0

```

Any ideas?

Btw, I'm using x86_64.

---

### Post by Vorsplummi on 2009-10-02
Great guide, thanks for that. 
But even so I have problem running pSX and I always have the same error note:
```
mikko@mikko-laptop:~$ pSX

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Virheellinen argumentti'
pad=0
/usr/bin/pSX: line 4: 10599 Muistialueen ylitys     ./pSX
```
Does anybody have a clue what's going on?

---

### Post by Saghaulor on 2009-10-09
> **Vorsplummi said:**
> Great guide, thanks for that. 
But even so I have problem running pSX and I always have the same error note:
```
mikko@mikko-laptop:~$ pSX

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:10599): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:10599): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Virheellinen argumentti'
pad=0
/usr/bin/pSX: line 4: 10599 Muistialueen ylitys     ./pSX
```
Does anybody have a clue what's going on?

Try searching the forums more.

I think you're problem is here.
[http://ubuntuforums.org/showpost.php?p=7723179&postcount=6]("http://ubuntuforums.org/showpost.php?p=7723179&postcount=6")

And your answer here.
[http://ubuntuforums.org/showpost.php?p=7723360&postcount=7]("http://ubuntuforums.org/showpost.php?p=7723360&postcount=7")

---

### Post by italomaia on 2009-10-31
I face the same problem as Saghaulor. 

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


All the time. And here it is: 

libgtkglext-x11-1.0.so: 
/usr/lib/libgtkglext-x11-1.0.so.0 
/usr/lib/libgtkglext-x11-1.0.so 
/usr/lib64/libgtkglext-x11-1.0.so.0 
/usr/lib64/libgtkglext-x11-1.0.so

---

### Post by mocha on 2009-11-01
> **italomaia said:**
> I face the same problem as Saghaulor. 

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


All the time. And here it is: 

libgtkglext-x11-1.0.so: 
/usr/lib/libgtkglext-x11-1.0.so.0 
/usr/lib/libgtkglext-x11-1.0.so 
/usr/lib64/libgtkglext-x11-1.0.so.0 
/usr/lib64/libgtkglext-x11-1.0.so


What happens if you run "sudo ldconfig" then try running pSX again?  Usually when there is a shared library problem you have to run ldconfig to update links.  If that still doesn't work perhaps you have an old lib installed or maybe in your case you have 32 and 64 bit libs installed and that causes a conflict somehow?  I only use 32 bit.

---

### Post by Saghaulor on 2009-11-01
> **mocha said:**
> What happens if you run "sudo ldconfig" then try running pSX again?  Usually when there is a shared library problem you have to run ldconfig to update links.  If that still doesn't work perhaps you have an old lib installed or maybe in your case you have 32 and 64 bit libs installed and that causes a conflict somehow?  I only use 32 bit.

I tried ```
sudo ldconfig
``` and then ```
pSX
``` and then received the same error.

---

### Post by rfrayer on 2010-02-06
its because you still have pulse running when you start it up

make sure you are added o the groups pulse and pulse-rt and pulse-access

then make sure you edit the file /etc/pulse/client.conf
 and change the autospan = yes to autospawn = no

if you are an oss user it just wont work pSX is closed sources and I am not a maintainer of the raw binary so i simply wouldnt know 


Howver im having a huge problem on karmic using an acer netbook with extreme choppyness

---

### Post by myromance123 on 2010-03-28
Hmm I got pSX from their site, then extracted it in my Documents folder.
After which I tried to run it from the terminal since double-clicking the runnable file showed no results.

I got this:
```
ismail@ismail-laptop:~/Documents/pSX$ ./pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory

```

So then, I took this part of your how to:
> get the dependancies

```
sudo aptitude install libgtkglext1-dev
```


and ran it once more, this time it brought me to the menu where it asked what language. I selected English and clicked 'OK', then I got this error message:
```
ismail@ismail-laptop:~/Documents/pSX$ ./pSX
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault (core dumped)

```

I have no idea what it means.
Also, I am using Ubuntu 10.04 beta 1 on a HP laptop (32-bit).
 Any ideas on how to fix that problem?
Thanks in advance.

EDIT: Even following your tutorial 100% wields the same results. Any ideas?

---

### Post by kacangitem on 2010-03-29
it isn't running on my ubuntu 9.10 and when i type in terminal pSX ,, appear this message

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
/usr/bin/pSX: line 4:  5279 Segmentation fault      ./pSX


what should i do?

---

### Post by myromance123 on 2010-03-29
@ KacangItem,
 Your problem is exactly the same as mine.

Although, I am using Ubuntu 10.04 Beta 1.
 Hopefully we get noticed soon.

I really want to play some old school playstation awesomeness on my systems :)

---

### Post by Arkanus on 2010-03-31
Just checked the threads you posted here and found a solution that works for me (10.04 beta), in [this thread]("http://ubuntuforums.org/showthread.php?t=1146830")Grishka posted a [simple solution]("http://ubuntuforums.org/showpost.php?p=7282494&postcount=8")

> 
1. kill pulseaudio (sudo killall pulseaudio)
2. run pSX as root (sudo ./pSX)
3. find the "sound" tab in the configuration and switch the "device" setting from "default" to your soundcard (plughw:0,0 in my case). apply. close pSX.
4 open /root/.pSX/psx.ini in a text editor (gksudo gedit /root/.pSX/psx.ini). find the "device" string under [Sound] section (I have "b7d317a4" there).
5. paste this string into the relevant section in ~/.pSX/psx.ini, in place of all zeroes. save. if you don't have this file in your user directory, run pSX and cancel just after choosing language, on the bios selection screen. pSX should save settings then.


in step 3 you have to select the analog output, otherwise there is no sound

---

### Post by 7G Operator on 2010-04-11
I think i've inadvertedly solved the choppyness issues here, but then again, maybe just mine, but i'll share what solved it for me. And if enough people agree then i guess its done and dusted. Firstly i tried the whole killing pulseaudio route (via editing respawn = no milarkee) Difference was negligible if any. Tried running as root, it said sound underrun blah de blah. Same skippy sound. Increasing latency = yeah not so great either. So then i got a bit more in depth in my researching looking into the soundcard e.t.c At this point i installed a real-time kernel (the one used by ubuntu studio) as i figured maybe it was to do with latency and soundcard settings which may be resolved using a real-time kernel. I think this might of increased quality slightly. I then went about editing the security/conf/limits file and adding a few parameters which involed setting cpu priority, and allocated memory for audio groups, which i then proceeded to add myself to. (Basic tweaks you need to do in order to get the RT kernel functioning nominally, and widely available guide on tinternet). I then having created a fairly cool audio workstation which i wanted to do anyways ;) Was messing about with pSX and realised it was now functioning perfectly without killing pulseaudio at all, but when in the smallest window available. No skipping sound or slowdown. Which is when it suddenly dawned upon me, after reading several articles and comments about how pSX faithfully recreates the playstation model rather than enhances it, queue quick research and.... what is playstations native and maximum resolution available? 480x600 (or 760 i think;). Changed the display settings temporarily to 480x600 and bobs your uncle and heathers your aunty, it all ran perfectly with no slowdown on fmv's or when playing. 

And thus my quest to try and get pSX working on my Samsung N130 NBR 9.10 came to a happy conclusion. Hopefully this might help some other people who've been getting truly narked by the choppy sound and thinking man if this worked properly it would be well cool. 

Just need to get me a playstation pad to usb convertor and i got myselfa  porta-playstation! ;)

Regards 

Dan - 7G Operator

---

### Post by 7G Operator on 2010-04-11
I just tried a couple more things, to ascertain exactly what it was that was causing my version of pSX to work properly. Firstly i tried my usual kernel for every day usage 31.-20. I then set the display to 480x600.....

*I tried first running pSX without disabling pulseaudio, full screen. FFVII. The video quality was o.k but the sound did skip very very slightly a number of times both during the intro FMV and for the first few bits of dialgoue box. (*No where near like the choppyness of running at a higher screen res though.) General Sound quality did seem slightly poorer than to be expected.

*I then tried the same but disabling pulse audio with the pulseaudio -k switch (after disabling autospawn a long time back;). Tihs warranted a perceived improvement in general sound quality, very very slight lapses in sound quality occured.

I then rebooted by comp (Which is For the purpose of diagnosing, and not boasting ;) *Samsung N130 netbook, 
UNR 9.10, 
1.6 GHZ atom, 
1GB RAM, 
some probably fairly crappy generic onboard intel sounddoolally ALC269 i think) 

and selected the 2.6.31-9-rt Kernel from the grub booter. (This is a Real-Time kernel allowing for potentially low latency sound mitigation in recording/sound engineering scenarios, (it's the sorta shizz i like to mess with, being interested in the sound bizniss and all, although i've only just migrated to it having been a keen proponent of Cubase in the past, but deciding to try out some Linux stuff;) it is i believe one of the kernels used by ubuntu studio, although rather than install "ubuntu studio" i instead decided to just pick the tasty bits from it ;) and install only the audio apps i feel i might want to experiment with. Anyways i installed that kernel, and tweaked a bit. Now i think it was perhaps this tweaking which has in fact increased pSX's efficiency, although i have done a test with kernel tweaks on the R-T kernel, i have not actually just tweaked the kernel of the latest kernel edition. (If you get me;) Basically the kernel tweak is.....Well i'll find it but it involves adding a couple of simple parameters to your e.t.c/security/limits.conf file...
[FONT=monospace]
[/FONT]*(Unless you wish to engage/experiment with audio production/mastering stuff e.t.c, then skip down to "Real-Time Support".)

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) - For the source material.

sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
 sudo adduser <username> audio


You may want to research this part independantly as i was told about a "nice - 10" command, and came to the conclusion (which upon further research appeared somewhat 50/50 shared/debateable, that if you award memlock - unlimited, if there is a problem/bug in your program you are essentially awarding full memory rights to that program, which im thinking might possibly cause a crash. *shrugs So i instead assigned half my ram 512000. 
(*Although i'm sure i'll probably up that at a latter date if Cubase and general RAM neccessities for DAW programs are anything to go by ;) 

Anyways Basically upon reading that page it says nowhere about the specific kernel so im thinking the kernel tweaks may be all you need ;). 

Anyways loaded Real-time kernel (*tweaked;), set display 480x600, tried pSX with pulseaudio running, perhaps one extremely slight happening with the sound, when first box of dialogue appears.

Killed pulseaudio, and reloaded pSX and finally no problemos!!. Again FFVII was the benchmark game i used for testing. 

Hope this helps some dudes/dudettes =)

Dan - 7G Operator

---

### Post by {Gray-Fox} on 2010-08-19
Hello!
I am a newbie of linux. So please give me a help, to install pSX. Thanks!,
and sorry for my bad English.

So I followed the tutorial of **rfrayer** step by step, I copied the following into *Applications > Accessories > Terminal*:

```
sudo aptitude install libgtkglext1-dev
``````
mkdir -pv ~/.pSX/cards

touch ~/.pSX/cards/1.mcr && touch ~/.pSX/cards/2.mcr
``````
cd $HOME

wget http://easyweb.easynet.co.uk/~david.s/saturn/images/Playstation_icon.gif

sudo mv Playstation_icon.gif /usr/share/pixmaps

wget http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2

tar xjvf pSX_linux_1_13.tar.bz2

sudo mv pSX /opt
``````
sudo mv scph1001.bin /opt/pSX/bios

sudo gedit /usr/bin/pSX
```is opened gedit, and I pasted the following code and I saved with the name "[COLOR=DarkRed]pSX[/COLOR]":
this:
```
[COLOR=RoyalBlue]#!/bin/bash

cd /opt/pSX
./pSX[/COLOR]
```Then I returned to the terminal, and i pasted this:

```
sudo chmod 755 /usr/bin/pSX
``````
sudo gedit /usr/share/applications/pSX.desktop
```I pasted the following code in gedit and I saved with the name "[COLOR=DarkRed]pSX.desktop[/COLOR]"

```
[COLOR=RoyalBlue][Desktop Entry]
Type=Application
Version=1.0
Encoding=UTF-8
Name=pSX Emulator
Comment=Play Playstation games on your PC!
Icon=/usr/share/pixmaps/Playstation_icon.gif
Exec=pSX
Terminal=false
StartupNotify=false
Categories=Game;Emulators;[/COLOR]
```I finished!
So I tried to start the emulator into [I]Applications > Games > pSX Emulator
[/I]The problem is that when I click on the icon (of *pSX Emulator*) does **not start**, nothing happens.

**Where is the problem or error?** help me! thanks.

*ps. very sorry for my bad English*

---

### Post by mocha on 2010-08-19
Just run pSX in a terminal and see what happens.

---

### Post by {Gray-Fox} on 2010-08-20
> **mocha said:**
> Just run pSX in a terminal and see what happens.

thanks!
I tried to run the psx in a terminal, but gave me anyway problems.
this:
[COLOR=DarkSlateGray][I]/ Usr / bin / pSX: line 3: cd: / opt / pSX: No such file or directory
[/I][/COLOR][COLOR=DarkSlateGray]*/ Usr / bin / pSX: line 4:. / PSX: No such file or directory*[/COLOR]


Now I tried to uninstall it, and rienstall it. following this guide:
[[COLOR=Blue]http://www.ubuntugames.org/us/emulator/38-psx-emulator[/COLOR]]("http://www.ubuntugames.org/us/emulator/38-psx-emulator")

but, gives me problems of "*sound: underrun*"

[COLOR=#000000]I opened a new thread to ask for explanations. here:
[/COLOR][http://wwww.ubuntuforums.org/showthread.php?p=9743285#post9743285](http://wwww.ubuntuforums.org/showthread.php?p=9743285#post9743285)

---

