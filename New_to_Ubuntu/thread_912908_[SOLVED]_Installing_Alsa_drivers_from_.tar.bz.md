---
title: "[SOLVED] Installing Alsa drivers from .tar.bz"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by moltar3000 on 2008-09-07
Hello everyone,

I installed ubuntu 8.04 a week or so ago on my laptop and this is my first time ever using it.  I havent actually got round to doing anything productive with it yet as I've been plagued by unrecognized hardware and drivers from the very beginning.  This is my 6th day trying without success to install my REALTEK ALC662, SIS966 soundcard and I think I've now found the right set of instructions to install the hda-intel drivers that my computer requires at...
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

However, when i get to this step in the instructions (after downloading the latest alsa drivers from their site)......

    * Setup installation directories 

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2


....then the terminal gives me error messages or simply doesnt respond to the commands.

I managed to get my wireless card working without having to install from downloaded .tar.bz2 packages, however this seems unavoidable.  If somebody could talk me through this it would be greatly appreciated, as not having any sound at all is now quite frustrating

---

### Post by moltar3000 on 2008-09-07
bump, please help

---

### Post by eggdeng on 2008-09-07
You might try
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
& then proceed as before.
A better idea would be first to post the make and model of your laptop and the output of
```
aplay -l
```
It may not be necessary to reinstall ALSA.

---

### Post by moltar3000 on 2008-09-07
Hey thanks for replying, I had already done what you recommended a few days ago and yet the problem persists.

Ive been doing this for several days so I've followed LOTS of different sets of instructions to no avail.  The link I posted is quite comprehensive, and as its the only tutorial I haven't been able to complete, I think that by process of elimination it is the one that will lead me to success.  Unfortunately I couldn't be able to tell you what the other instructions Ive followed have accomplished because I am a noob and most of the time this all reads like gibberish to me.  The only thing I know is that they haven't turned my sound on.

All I am looking for is someone to talk me through installing the said .tar.bz2 packages in the terminal so I can continue through the linked tutorial.

> **eggdeng said:**
> 
```
aplay -l
```


**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Im not sure this is relevant to the process im trying to do, but here it is.

Just looking for a walkthrough of how to install these things
alsa-driver-1.0.17.tar.bz2
alsa-lib-1.0.17a.tar.bz2
alsa-utils-1.0.17.tar.bz2
which are located in the downloads folder in my home folder

---

### Post by eggdeng on 2008-09-07
I did a how-to for this just a short time ago, you can find it at 
[http://ubuntuforums.org/showthread.php?t=895284]("http://ubuntuforums.org/showthread.php?t=895284") posts #5 and #7.
Just bear in mind the following. When you download the source files, you  need to move them to the /usr/src/alsa folder which you created, if that is where you are going to do the install. So the first thing to do is to move there
```
cd /usr/src/alsa
``` and run
```
ls
``` to make sure you can see your source tar.bz2 files. If & when you get error messages, just prefix the command with sudo and try again.
To extract the files, you run
```
tar -xvzf source_file.tar.bz2
```
where source_file.tar.bz2 is the name of the source file as per the ls command above. In each case this will extract the source file to a directory of the same name but without the tar.gz extension. You then move to the first of these using the cd command and run
```
./configure (with any parameters specified in the how-to you were using)
```
```
./make
```
```
./make install
```
Then basically, just repeat for the other two folders.
So now will you tell me the make and model? 8-)

---

### Post by moltar3000 on 2008-09-07
Thanks very much for the help I was able to install all 3 of the packages.  I'm slowly picking up consciousness of what it is exactly that I am doing while I'm following instructions so things are going well.  I still haven't gotten sound yet but I'll keep plugging away.

Sorry, the last time I replied, I had forgot you asked me the make of my computer.  It's an ASUS F80S laptop.

---

### Post by Xiong Chiamiov on 2008-09-07
Of note are the (very) [Comprehensive Sound Problems Solution Guide]("http://ubuntuforums.org/showthread.php?t=205449") and [How to Install Anything in Ubuntu]("http://209.85.173.104/search?q=cache:IfbspYjsGWIJ:www.monkeyblog.org/ubuntu/installing.html+how+to+install+anything+in+ubuntu&hl=en&ct=clnk&cd=1&gl=us").

---

### Post by jweaver28 on 2008-11-02
Thanks, Eggdeng, even if I haven't figured out where the thanks button is;)

Thanks specially for your detailed explanations, I now have sound through my EVGA GeForce7150/NForce630i motherboard. I did have to download the newest Alsa package 1.0.18, which has NVidia's October-released hi-def audio drivers. Ubuntu/Synaptics thus far only has 1.0.17. I had several installation misadventures yesterday, including inadvertently uninstalling Gnome while uninstalling various audio packages, And I did need to uninstall Alsa's 1.0.17 package before installing the various parts of 1.0.18. Two slight quibbles, if a newbie is permitted: the alsa-drivers site had bad links to the newest package (I did file a bug report and managed to get them by FTP from Europe), and Intrepid insisted I use sudo for most commands and a hyphen before the flag in the tar command -vjk(?). Anyhow, I was so glad to see the redX muting my volume icon when I finished your suggested process despite two error messages on the modplug line!! (Intrepid dislikes something about an AC97 file and the Intel8x0 designations).

Also, for what it's worth, I needed to physically unplug my skype headset to plug in an audio cable between my sound port and TV (connected via an HDMI cable which also carries sound in Vista but not Linux).

My next project's getting NVidia's video drivers to work. But tonight I can relax with some tunes :)

---

