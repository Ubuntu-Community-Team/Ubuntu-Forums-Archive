---
title: "HOWTO: Install ePSXe (a freeware Sony Playstation Emulator) with a simple installer!"
date: 2007-09-13
forum: Outdated Tutorials &amp; Tips
---

### Post by NightCrawler03X on 2007-09-13
* This installer should work for all GNU/Linux distributions *
* It should be noted that you should run this installer as user, not root, as it will download and install everything to a sub-directory of your /home/user directory *

For all you GNU/Linux users out there that want to use ePSXe, but can't set it up due to either laziness or incompetence, I have written an easy to use installer (a simple shell script) for you.

This installer will download and setup the following things:
 - ePSXe 1.52 
 - Pete's XGL2 video plug in for newer graphics cards.
 - Pete's Mesa video plug in for older graphics cards.
 - Pete's Software video plugin for those without 3D hardware acceleration
 - Pete's O.S.S SPU plug in.
 - AmmoHQ's Joypad plugin for those wanting to play with a joypad


Things that this installer will NOT download and set up
 - The PSX bios file(s). It is illegal to share it since it's Sony's intellectual property. You'll have to dump one from a PSX that you ACTUALLY OWN. You can just download one by searching for it on Google, but I/we won't help you here for the following reason:
1) I/we could get sued, since it's illegal to download the bios when you don't own one.
2) Because of reason #1, it would probably be against this boards rules.

[Click here to download the installer](http://www.freewebtown.com/franky06/installepsxe.tar.gz)
[Click here if the above link does not work](http://ubuntuforums.org/attachment.php?attachmentid=69998&d=1210752307)

When you have downloaded it, open your command prompt (konsole, rvxt, whatever program you use for terminal emualtion), cd to the folder it's in, so if it was in /home/hesho/installepsxe, you'd type "cd /home/hesho/installepsxe".
Then untar it (tar -xf installepsxe.tar.gz), then type "sh installepsxe" (without the quotes).

The installer will then download all the required files, extract them, and move everything to where it should be.

After that, you'll have everything you need to use ePSXe on your GNU/Linux system.
(the installer will tell you how to run it when you want to)
The only thing you WILL NOT have is the bios, you'll just have to do this yourself.
When wanting to run ePSXe, just type (without the quotes) "~/epsxe/epsxe" or "epsxe" at your command prompt.

It should ne noted that for running it by typing "epsxe", you will have to close your terminal emulator and open it again first. The reason for this, is that the installer will not make a shell script for actually running epsxe, but rather, make an alias by issuing the following:
cd ~
echo alias epsxe="'~/epsxe/epsxe'" >> .bashrc
Your terminal emulator will read ~/.bashrc when opened, and register any commands it finds, so since it hasn't registered the alias yet, you'll need to let it do so before being able to use said alias.

It should also be noted that you still won't be able to play right away. Even after you've got the bios(en), you'll still need to configure all of your plugin settings to get it running correctly on your system. I could also guide you through this myself, but there is a very good guide for it already, on NGemu Forums. [Click here](http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html) 

Things you'll need:
 - A PC that meets/exceeds ePSXe system requirements
 - An internet connection (this installer will download what you need, I'm not distributing the ePSXe binary + plug ins because my web host is a ****ty free one and thus would run out of bandwidth if I did so)
 - IMPORTANT! > 3D Video Acceleration (both plug ins that get downloaded use OpenGL extensions)
* The stuff mentioned below you probably already have *
 - wget
 - tar
 - gtk libraries
 - and OSS sound sound library
 - and other stuff that I can't remember off the top of my head
 - and obviously, a running+working graphical server such as Xorg or Xfree86, with a GUI such as Xfce, IceWM, KDE, JWM, etc.
Enjoy!

***Extra Note***
A lot of Gutsy (Ubuntu 7.10) users are complaining about ePSXe not loading.
This is because the ePSXe binary is upx-compressed, which is the cause of the problem.
So we simply decompress it to get the "real" binary.
Here's how:
```

sudo apt-get install upx-ucl-beta
upx -d ~/epsxe/epsxe

```
Assuming that you used my installer or your ePSXe executable is located in ~/epsxe, this should do the trick.

***Also***
You'll almost definitely have GTK libraries installed, but you probably don't have libgtk version 1.2 installed. ePSXe relies on this older version.
So do this:
```

sudo apt-get install libgtk1.2

```
Else it will report "error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory".
You could also create a symbolic link to a newer version of libgtk you have, to what would be the library for version 1.2, to trick ePSXe into thinking that you have the older version, but your mileage may vary. I don't personally recommend it.

***Bug Fixes:***
 - Fixed a bug where the installer deleted every .zip in home directory (thanks **crouchingturbo**)
 - Fixed a bug where the installer had the potential to move around any *.cfg or cfg* files in your home directory (again, thanks **crouchingturbo**)
To all people who used my old installer and found all your zip files deleted, I apologize.

***Additions:***
 - The script now download's Pete's (video) software plugin for those without 3D acceleration (14 May 2008)
 - The script now downloads AmmoHQ's Joypad plugin for those wanting to use a joypad (14 May 2008)

***Relevant Links:***
[ePSXe Homepage](http://epsxe.com)
[Game Emulation How-To Links (Courtesy "Felson")](http://ubuntuforums.org/showthread.php?t=612289&highlight=emulation+how-to)
[Install ePSXe playstation emulator (Courtesy "Felson")](http://ubuntuforums.org/showthread.php?t=612021&highlight=epsxe)
[Another How-To]("http://forums.ngemu.com/generic-epsxe-queries/93374-epsxe-configuration-guide-linux.html")

***Credit:***
The user "crouchingturbo" pointed out that my script deletes every *.zip in the person's home directory, and has the potential to move certain files around. These are all things that no ones wants. 

Since this has been brought to my attention, I have now fixed this bug. Everyone who downloaded the older script, delete it immediatly, and download it from this thread again.

But yes, thank you, **crouchingturbo**

---

### Post by TheIdiotThatIsMe on 2007-11-23
I tried downloading the installer, but alas no luck. Is the file still hosted?

---

### Post by Jose Catre-Vandis on 2007-11-24
> **TheIdiotThatIsMe said:**
> I tried downloading the installer, but alas no luck. Is the file still hosted?

It's still there, working here :)

---

### Post by F-3582 on 2007-11-26
You should definitely install SPU Eternal instead of PEOpS for various reasons I described [here]("http://ubuntuforums.org/showpost.php?p=3837030&postcount=13").

The link can be found there as well. In order to make it work, you need to do this:

```
sudo aptitude install libstdc++2.10-glibc2.2
```

A littlle configuration advice: The spuEternal.cfg should be look like this:

```
AudioDevice = 1
SoundBufferSize = 24
AudioOutMethod = 2
AsyncMode = 1
ShowRealtimeConfigWindow = 0
WaitForXABufferIsFree = 1
CacheVagDecode = 0
Finetune = 0
ReverbType = 4
RecOpt = 5
UpdateBeforeRegisterAccess = 1
SPUIRQWaitCPUAction = 0
SPUIRQForceInterruptFlag7 = 0
```

This sendss the Audio Output to SDL (which needs to be installed, of course) and uses the SPUAsync interface of ePSXe. By doing so and setting it to "Wait" mode it makes the frame limiter of your graphics plugin obsolete, but produces sound stuttering if the frame rate drops too low and the sound buffer is too small. Nevertheless, a sound buffer size of 18 to 24 or even slower should be possible on a conveniently fast machine. If you use PEOpS SoftX plugin, however (my preferred choice, by the way), it could become a little more complicated, since everything, scaling included is done by X and the CPU load increases a lot, of course. Play around with those settings and see for yourself.

---

### Post by gcrussell1 on 2007-11-28
Any chance you could attach the installer to the forum post? The freewebtown link is not working for me, which could be because it's a rubbish site or it might be blocked by the Chinese national firewall. Either way though, I'd like to try your installer, if only because it installs 1.52 - the more stable ePSXe version in my experience.

---

### Post by F-3582 on 2007-11-29
> **gcrussell1 said:**
> Any chance you could attach the installer to the forum post? The freewebtown link is not working for me, which could be because it's a rubbish site or it might be blocked by the Chinese national firewall. Either way though, I'd like to try your installer, if only because it installs 1.52 - the more stable ePSXe version in my experience.

There you go.

---

### Post by Elrian on 2007-11-30
Hello,

I have installed ePSXe using your installer and been trying to add a launcher for it in the gnome application menu without success...

Can someone tell me how to do it?

Thanks

---

### Post by gcrussell1 on 2007-11-30
> **Elrian said:**
> Hello,

I have installed ePSXe using your installer and been trying to add a launcher for it in the gnome application menu without success...

Can someone tell me how to do it?

Thanks

Right click on the menu bar and click "Edit Menus", then go to "Games" on the left side (or wherever else you want it), and hit "New Item" - then specify what it is in the small window that pops up (might pop up in the background for you, just select it). You can give a terminal command line or you can set the launcher by navigating to its icon, either way though, that should do it for you.

---

### Post by NightCrawler03X on 2007-11-30
Hey dudes, sorry about that freewebtown link. (Freewebtown is pretty lame).

I'll post it in an attachment here then:

---

### Post by Ashkc88 on 2007-12-06
Hi, I am a little bit familiar with Ubuntu, but I'm still unfamiliar enough to be considered a "noob."  I've been trying for ages to get this emulator to work.  I followed all of the guides I have found and none of them worked.  I am pretty sure it's a user error.

I just upgraded to Ubuntu 7.10 (Gutsy).  I'm using an Intel Mac Mini (Duo core, 512 MB of RAM), and I have every device for it working (bluetooth, wireless, etc.).  

I used the installer that was posted, I put the Bios in it's respective folder, and I used the...

"sudo apt-get install upx-ucl-beta
upx -d ~/epsxe/epsxe"

...code in the terminal and it still will not let me open the program.  

The answer is probably very obvious and I feel like an idiot for asking the question,  Does anyone know what I did wrong?

---

### Post by F-3582 on 2007-12-06
What does the terminal say when starting epsxe?

---

### Post by Ashkc88 on 2007-12-06
Never mind, like I said I'm an idiot.  User error, accidentally moved a wrong file. *doh*

Hello, my name is Ashkc88 and I'm new to Ubuntu.  How are you today?

---

### Post by NightCrawler03X on 2007-12-07
Hm, I was actually typing out some suggestions for your problem, but you replied saying that it's all fine now for you, before I had a chance to post, so I quickly edited.

Is ePSXe working for you now? 
(do games work on it for you I mean )

Oh, and I'm all fine and dandy thank you.
How are you?

---

### Post by rzrgenesys187 on 2007-12-18
SOOOOO Awesome.  I can finally move back to linux as my primary since i started another run through FFVII and PCSX would crash anytime i went through a battle :(  I can't believe all i had to do was decompress the file.  Thanks so much I forgot how much i can't stand vista, but i guess it makes me appreciate linux more.

---

### Post by skullhead on 2007-12-23
i get these messages well im doing the install 
=> `gpupetexgl208.tar.gz'
Resolving [www.pbernert.com](www.pbernert.com)... failed: Name or service not known.
tar: gpupetexgl208.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rm: cannot remove `gpupetexgl208.tar.gz': No such file or directory
mv: cannot stat `cfg*': No such file or directory
mv: cannot stat `*.cfg': No such file or directory
--13:49:26--  [http://www.pbernert.com/gpupetemesagl176.tar.gz](http://www.pbernert.com/gpupetemesagl176.tar.gz)
           => `gpupetemesagl176.tar.gz'
Resolving [www.pbernert.com](www.pbernert.com)... failed: Name or service not known.
tar: gpupetemesagl176.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rm: cannot remove `gpupetemesagl176.tar.gz': No such file or directory
mv: cannot stat `cfg*': No such file or directory
mv: cannot stat `*.cfg': No such file or directory
--13:49:46--  [http://www.pbernert.com/spupeopsoss109.tar.gz](http://www.pbernert.com/spupeopsoss109.tar.gz)
           => `spupeopsoss109.tar.gz'
Resolving [www.pbernert.com](www.pbernert.com)... failed: Name or service not known.
tar: spupeopsoss109.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rm: cannot remove `spupeopsoss109.tar.gz': No such file or directory
mv: cannot stat `cfg*': No such file or directory
mv: cannot stat `*.cfg': No such file or directory

im using ubuntu 7.10 32bit and also epsxe wont start up when i type epsxe in terminal

---

### Post by F-3582 on 2007-12-24
Is there some sort of proxy you are behind? I can access that site perfectly fine.

---

### Post by plap on 2007-12-25
I'm on gutsy 7.10 and I followed the guide step by step, including the upx step, but epsxe still doesn't open. When I double click it, the .epsxerc file is just created...

I have all the libs required and I've already seen that pSX runs images on my box, although not well, hence why i'm here ;)

---

### Post by F-3582 on 2007-12-26
Run ePSXe from terminal and watch what it writes. It might help you tracking down the problem.

---

### Post by NightCrawler03X on 2007-12-28
> I'm on gutsy 7.10 and I followed the guide step by step, including the upx step, but epsxe still doesn't open. When I double click it, the .epsxerc file is just created...

I have all the libs required and I've already seen that pSX runs images on my box, although not well, hence why i'm here 

You probably don't have the older version (1.2) of libgtk install:
```

sudo apt-get install libgtk1.2

```
And try to run epsxe then

PS:
Don't "double-click" the executable. You should run it from the command line.
My installer puts the epsxe executable in ~/epsxe, 
But it also makes an "epsxe" alias for running the executable.

At your command line, either
```

~/epsxe/epsxe

```
or
```

epsxe

```
and it should run.


> 
i get these messages well im doing the install
=> `gpupetexgl208.tar.gz'
Resolving [www.pbernert.com](www.pbernert.com)... failed: Name or service not known.
tar: gpupetexgl208.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rm: cannot remove `gpupetexgl208.tar.gz': No such file or directory
mv: cannot stat `cfg*': No such file or directory
mv: cannot stat `*.cfg': No such file or directory
--13:49:26-- [http://www.pbernert.com/gpupetemesagl176.tar.gz](http://www.pbernert.com/gpupetemesagl176.tar.gz)
=> `gpupetemesagl176.tar.gz'
Resolving [www.pbernert.com](www.pbernert.com)... failed: Name or service not known.
tar: gpupetemesagl176.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rm: cannot remove `gpupetemesagl176.tar.gz': No such file or directory
mv: cannot stat `cfg*': No such file or directory
mv: cannot stat `*.cfg': No such file or directory
--13:49:46-- [http://www.pbernert.com/spupeopsoss109.tar.gz](http://www.pbernert.com/spupeopsoss109.tar.gz)
=> `spupeopsoss109.tar.gz'
Resolving [www.pbernert.com](www.pbernert.com)... failed: Name or service not known.
tar: spupeopsoss109.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rm: cannot remove `spupeopsoss109.tar.gz': No such file or directory
mv: cannot stat `cfg*': No such file or directory
mv: cannot stat `*.cfg': No such file or directory

im using ubuntu 7.10 32bit and also epsxe wont start up when i type epsxe in terminal
that's a problem with your network. Are you sure you have internet access? Since your posting now, you probably do, but it was down for a little bit of time when you ran the installer. Try running it again, and tell me if it works.

Remember to install libgtk1.2 once you've installed epsxe with my installer
```

sudo apt-get install libgtk1.2

```
and if you're running Ubuntu 7.10 Gutsy (or more specifically, the 2.6.22-14 linux kernel), then decompressed the epsxe executable (it's compressed with upx, linux 2.6.22-14 has problems with that)
```

cd ~/epsxe/epsxe
upx -d epsxe

```
PS:
The epsxe executable is installed before the plugins. With shell scripts, if a command fails it goes onto the next command, unless you specify otherwise. Basically, you can run epsxe still but the plugins weren't downloaded because at the time when they were to be downloaded, your network went down; delete the epsxe folder in your /home/user directory then start over (note, make SURE you do "cd ~/epsxe" then "upx -d epsxe" because you will be back with the upx-compressed epsxe executable.

---

### Post by Elrian on 2008-02-21
> **gcrussell1 said:**
> Right click on the menu bar and click "Edit Menus", then go to "Games" on the left side (or wherever else you want it), and hit "New Item" - then specify what it is in the small window that pops up (might pop up in the background for you, just select it). You can give a terminal command line or you can set the launcher by navigating to its icon, either way though, that should do it for you.

Thanks but it still doesn work...

I can launch it by typing epsxe in the terminal but when i add epsxe or browse the file in the launcher it gives me an error...

---

### Post by breaking on 2008-02-23
Same problem here and solved with:

sudo aptitude install libstdc++2.10-glibc2.2 

:popcorn:

---

### Post by F-3582 on 2008-02-23
You'll have a hard time trying this in Hardy, for that package isn't in the repos anymore.

---

### Post by Elrian on 2008-02-27
I still cannot create a launcher...

---

### Post by F-3582 on 2008-02-27
I just tried it meself and it worked.

Just right-click the menu bar, "Edit Menus", then browse into the category of your choice, "Add Item", insert the name "ePSXe" into the "Name" field, insert "epsxe" (the command to launch it) into the "Command" field, add a meaningful description, if you like, add an icon, if you like, and you are set. That worked for me and probably for everyone else.

---

### Post by Elrian on 2008-02-28
I did that exactly and nothing happens...

Works if i type epsxe in the console but the launcher don't...

---

### Post by Frankly Francois on 2008-02-28
Thank you, the guide was very helpful! :guitar:

For some reason or other I kept getting an error message concerning "libstdc++.so.5", I did install all the library files the OP suggested. So that had me stumped, but I search around and used the following to resolve it:
```
sudo apt-get install libstdc++5
```

I probably did something wrong or tinkered with something I shouldn't have. I'm still quite new to Linux!

---

### Post by rf277 on 2008-03-11
i used your installer, worked great but it's doing this weird thing where when i go into configure none of the buttons are doing anything and there's no selections in my menues, just disabled, and when i click on configure nothing happens

---

### Post by F-3582 on 2008-03-11
Did you select any plugins?

---

### Post by demagnetized on 2008-03-13
Hi, 

I've gone through all the steps in the How-To including  installing libgtk1.2 but I am still getting the following error:

```
:~$ epsxe
/home/david/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

I tried entering the command again:
```

:~$ sudo apt-get install libgtk1.2
```

and I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I'm running Gutsy 64bit. I assume I'm doing something wrong but I have no idea what. Any help very gratefully received.

---

### Post by demagnetized on 2008-03-13
Oops, please ignore the above post. I got it working. :)

---

### Post by Sugz on 2008-03-24
I used this, it worked like a charm but i cannot go over
600 x 500 screen size or it will go quite slow.
This is strange as my friend can play R-type delta at a good speed on his relic of a laptop. 
How can i improve my speed at higher resolutions?

---

### Post by woahitsmatt on 2008-03-25
I'm still getting this error like demagnitized had been getting:

```
matt@ubuntu:~$ epsxe
/home/matt/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

I've already ran the command to the libgtk, but as the second post prior to mine said, it says none upgraded or installed........

I'm running Hardy x64. If someone could help me that'd be great.

---

### Post by ZeroXone on 2008-04-13
Hey i used the simple installer and i still can't get epsxe to start up when i type it into the terminal emulator. i'm pretty sure i installed it correctly, but i'm like an uber-noob so who knows? i'm using 7.10 gutsy and i read they are having problems with it so any help would be greatly appreciated.

---

### Post by NightCrawler03X on 2008-04-16
> **woahitsmatt said:**
> I'm still getting this error like demagnitized had been getting:

```
matt@ubuntu:~$ epsxe
/home/matt/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

I've already ran the command to the libgtk, but as the second post prior to mine said, it says none upgraded or installed........

I'm running Hardy x64. If someone could help me that'd be great.

ePSXe is for x86. you are trying to run it on x86-64. You need to install the 32bit libraries (in it is libgtk). I don't know how to help you because I've never used 64bit ubuntu. If you use my installer, then refer to Felson's guide on how to setup all required 32-bit libraries, you shouldn't have any problems.

1.2 is a very old libgtk version too, so newer versions of ubuntu might not have it. Try searching around the internet, opr this forum, for how to install "libgtk1.2" on Hardy Heron.
You could also create a symbolic link to a newer version of libgtk. But I don't recommend this, personally.



ZeroZone.
You type  "epsxe" but nothing comes up, no errors, but it doesn't run, I assume? I said in my first post that ePSXe is upx-compressed, and gutsy has problems with upx-compression..
Anyway, I basically said to do this in the command line:
```
sudo apt-get install upx-ucl-beta && upx -d ~/epsxe/epsxe
```
Do that, then try "epsxe" again at the command line. I think you'll find that it'll work after that.

---

### Post by NightCrawler03X on 2008-04-16
> **Sugz said:**
> I used this, it worked like a charm but i cannot go over
600 x 500 screen size or it will go quite slow.
This is strange as my friend can play R-type delta at a good speed on his relic of a laptop. 
How can i improve my speed at higher resolutions?
It's either crappy hardware you have, or crappy drivers. Since you said an older machine can run it faster than you, it's probably the drivers you have.

*Or*, it could be the plugin settings. Try different settings, and of course different plugins. It could be that you are using Pete's XGL/Mesa plugin but your GPU doesn't have very good opengl support. In which case, you might want to try the software plugin (it's called P.E.O.P.S I think). I didn't include the software plugin in the installer, but you can find it on pbernert.com
Just decompress the archive:
Put the .so file in the plugins folder
Put the cfg* file in the cfg folder
Put the *.cfg file in the cfg folder.
Then go to ePSXe, settings > plugins > (select) P.E.O.P.S software plugin > Configure
Then do whatever settings you like, press ok, then restart ePSXe and see what you get.

You should note that software plugins need more CPU power, since graphics are rendered on the CPU, not the GPU. All the GPU does in this case is draw the graphics to the screen. But try it, and see what you get.















PS:
To everyone:
I've read through this thread, and I see that people are having problems creating shortcuts to epsxe. This is because my installer does not create a shell script for running it (or set ~/epsxe/ as a PATH variable).
What it does instead, is create an *alias* for running ePSXe. It write "alias epsxe='~/epsxe/epsxe' to ~/.bashrc
This lets you type epsxe at the terminal, since the terminal registers anyu commands (i.e. aliases) in ~/.bashrc. If you want, you can make a shell script for running epsxe, and put it in /usr/bin, then sudo 755 the shell script. That should let you use shortcuts (of course, remove the alias if you do this).

I *could* include a shell script with the installer, and tell the installer to "sudo mv ./epsxe /usr/bin" 
("epsxe" being the script).
but this means that the user needs to type in their password when using the installer. I want the installer to be as easy to use as possible, hence I avoid doing anything that requires root privileges, or anything else that introduces awkwardness.

If you guys want to change the install script to do these things (or anything else you want for that matter), go right ahead, and post the modified script here, or anywhere else.
Believe me, it's not hard. The code in my installer isn't exactly complex. (Just a simple shell script really. Open it up in any text editor and off you go!)

EDIT:
Screw that. If you want a shortcut to epsxe, then when creating the shortcut, rather than typing "epsxe" as the command, type "~/epsxe/epsxe".
Shoulda thought of this earlier, but ohwell. Enjoy.

---

### Post by vdalmonte on 2008-04-20
It works, it works but when I try to pass it command line options it just opens up the interface, i.e.:
epsxe -nogui -loadiso [isopath/isoname]

makes the interface pop up on my laptop while on my desktop -loadiso loads and run the iso

[EDIT]
I had installed it using the guide @ [http://ubuntuforums.org/showthread.php?t=612021&highlight=epsxe+install](http://ubuntuforums.org/showthread.php?t=612021&highlight=epsxe+install)
but I had the same problem on my laptop so I tried yours
[/EDIT]

---

### Post by vdalmonte on 2008-04-20
I installed the upgrades of Hardy Henron or I did something else and now it works!

---

### Post by savethewabbit on 2008-05-06
hey, thanks for this thread :) i installed epsxe and it starts correctly when i launch it through terminal or through the menu. 
problem is, i can't get any game to work. i'm using hardy and i've tried all the apt-get codes in this thread, but i just get the "package is already the newest version" message for all of them. 
basically, i select an .iso file, or a cd drive, and when i select "ok" the program closes and that's it. am i doing anything wrong? i haven't changed anything plugin-wise, as if i select "video" or "audio" from the menu the program closes as well.

any help would be appreciated. thanks!

---

### Post by NightCrawler03X on 2008-05-06
I'm sorry, but I don't know  how to help. I haven't upgraded to Hardy yet.

But from the sound of things, it might be a seg fault. Tell me what your terminal shows when ePSXe closes.





Also, the video plugins use 3d hardware acceleration. It might be that ePSXe closes because you don't have acceleration enabled. But don't quote me on this, it's only a guess.

---

### Post by savethewabbit on 2008-05-06
thanks for replying so quickly!
it says
```

 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 0 1
 * Track 1: CD get track start failed (25)
 (DATA) - Start 0: (116,87,151)
CD(0,2,16) read ioctl failed (25)
CD(190,43,37) read ioctl failed (25)
CD(190,43,38) read ioctl failed (25)
 * NTSC cdrom detected.
plugins/libgpu.so: cannot open shared object file: No such file or directory

```

and i'm 90% sure that the cd is okay because there's other people who used the very same one and it works for them...

---

### Post by savethewabbit on 2008-05-07
okay, i managed to solve that first issue by renaming a plugin i downloaded "libgpu.so", (i can't enter the video config screen or epsxe crashes, so i couldn't just select that one instead...). 
now the problem lies just a couple lines below though:
```

 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpu.so] 
/usr/local/bin/epsxe: line 6:  7007 Segmentation fault      ./epsxe $*

``` 
i tried installing epsxe with yet another guide, and i got the same error (different file obviously, but still). any ideas? :\

---

### Post by wiebeest on 2008-05-09
Hello, I'm relatively new and quite a n00b to Linux, but having a blast with Ubuntu. 

Ditched Windows XP completely in exchange to Gutsy a while ago
and still gladly humming since I did. I find it very interesting adventure to learn about Linux through Ubuntu. The terminal commands remind me of the old DOS eara, so that doesn't scare me that much, although since it's 2008 I tend to prefere a GUI whenever possible.

Recently I made the switch from Gutsy to Hardy and by that time I thought I would be a good idea to join this Ubuntu forum, which I had allready been consulting for sollutions eversince I made the Ubuntu switch. 

For entertainment I've been succesfully playing Windows games through Wine under Gutsy.

And with the switch to Hardy, I wanted to try a PSX emulator.

Now, the new pSX works great for me, but I wanted to try the older ePSXe, because I joyfully had been using that in my Windows days and what I liked about that was the pluginsystem it uses and the fact you can graphically enhance the PSX experiance with that.

Tried the installer mentioned in this thread, works to the fact of starting ePSXe, but when I load an iso, I get the following error:

>  * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/wiebeest/epsxe/bios/SCPH1001.BIN].
 * Init ISO code ... ok
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Xlib:  extension "XFree86-VidModeExtension" missing on display ":2.0".Segmentatiefout
wiebeest@wiebeest-desktop:~$  

Now, for the record: I'm using the Dutch language, so the error "Segmentatiefout" stands for "Segmentation fault" in English. 

Does anyone around here know how to solve this unfortunate error and make ePSXe work? Many thanks beforehand!!

Wiebeest

---

### Post by camurgo on 2008-05-10
> **wiebeest said:**
> Hello, I'm relatively new and quite a n00b to Linux, but having a blast with Ubuntu. 

Ditched Windows XP completely in exchange to Gutsy a while ago
and still gladly humming since I did. I find it very interesting adventure to learn about Linux through Ubuntu. The terminal commands remind me of the old DOS eara, so that doesn't scare me that much, although since it's 2008 I tend to prefere a GUI whenever possible.

Recently I made the switch from Gutsy to Hardy and by that time I thought I would be a good idea to join this Ubuntu forum, which I had allready been consulting for sollutions eversince I made the Ubuntu switch. 

For entertainment I've been succesfully playing Windows games through Wine under Gutsy.

And with the switch to Hardy, I wanted to try a PSX emulator.

Now, the new pSX works great for me, but I wanted to try the older ePSXe, because I joyfully had been using that in my Windows days and what I liked about that was the pluginsystem it uses and the fact you can graphically enhance the PSX experiance with that.

Tried the installer mentioned in this thread, works to the fact of starting ePSXe, but when I load an iso, I get the following error:

 

Now, for the record: I'm using the Dutch language, so the error "Segmentatiefout" stands for "Segmentation fault" in English. 

Does anyone around here know how to solve this unfortunate error and make ePSXe work? Many thanks beforehand!!

Wiebeest



Man I don't know how to solve this problem in particular you've got.. But I  tell ya, epsxe has an endless number of errors on the linux version..  I struggled with some of them for  few days and ultimately just gave up and moved to PSX...

---

### Post by crouchingturbo on 2008-05-12
-
-
**Note that if you have any files ending in .zip in your home directory, THIS SCRIPT WILL DELETE THEM.**

Additionally, the script isn't very well written, and if one of the steps fails, it may cause more harm (moving around files matching *.cfg and cfg*).  Also it modifies your ~/.bashrc file.

Again, this is **not** a terribly safe script to run.

---

### Post by wiebeest on 2008-05-13
> **crouchingturbo said:**
> -
-
**Note that if you have any files ending in .zip in your home directory, THIS SCRIPT WILL DELETE THEM.**

Additionally, the script isn't very well written, and if one of the steps fails, it may cause more harm (moving around files matching *.cfg and cfg*).  Also it modifies your ~/.bashrc file.

Again, this is **not** a terribly safe script to run.

Hmm... Does this mean that if not succesfull up till now, better not go for ePSXe for now and stay with pSX? And does this mean maybe now the script has been moving files I don't want it to?

---

### Post by NightCrawler03X on 2008-05-13
> **savethewabbit said:**
> okay, i managed to solve that first issue by renaming a plugin i downloaded "libgpu.so", (i can't enter the video config screen or epsxe crashes, so i couldn't just select that one instead...). 
now the problem lies just a couple lines below though:
```

 * Force NTSC cdrom detected. 
 * Init gpu[0][libgpu.so] 
/usr/local/bin/epsxe: line 6:  7007 Segmentation fault      ./epsxe $*

``` 
i tried installing epsxe with yet another guide, and i got the same error (different file obviously, but still). any ideas? :\

There's a fault with the plugin causing that. Either that, or it's a dependancy on your system. I still don't know how to help, sorry.

> **wiebeest said:**
> Hello, I'm relatively new and quite a n00b to Linux, but having a blast with Ubuntu. 

Ditched Windows XP completely in exchange to Gutsy a while ago
and still gladly humming since I did. I find it very interesting adventure to learn about Linux through Ubuntu. The terminal commands remind me of the old DOS eara, so that doesn't scare me that much, although since it's 2008 I tend to prefere a GUI whenever possible.

Recently I made the switch from Gutsy to Hardy and by that time I thought I would be a good idea to join this Ubuntu forum, which I had allready been consulting for sollutions eversince I made the Ubuntu switch. 

For entertainment I've been succesfully playing Windows games through Wine under Gutsy.

And with the switch to Hardy, I wanted to try a PSX emulator.

Now, the new pSX works great for me, but I wanted to try the older ePSXe, because I joyfully had been using that in my Windows days and what I liked about that was the pluginsystem it uses and the fact you can graphically enhance the PSX experiance with that.

Tried the installer mentioned in this thread, works to the fact of starting ePSXe, but when I load an iso, I get the following error:

 

Now, for the record: I'm using the Dutch language, so the error "Segmentatiefout" stands for "Segmentation fault" in English. 

Does anyone around here know how to solve this unfortunate error and make ePSXe work? Many thanks beforehand!!

Wiebeest

Your videocard drivers aren't configured correctly.

> **crouchingturbo said:**
> -
-
**Note that if you have any files ending in .zip in your home directory, THIS SCRIPT WILL DELETE THEM.**

Additionally, the script isn't very well written, and if one of the steps fails, it may cause more harm (moving around files matching *.cfg and cfg*).  Also it modifies your ~/.bashrc file.

Again, this is **not** a terribly safe script to run.
Hmm, it seem that you are correct. I created a .zip in my ~, then ran the script, and the .zip was gone. I've fixed this bug now.

It moves *.cfg and cfg* files within your ~/epsxe directory. These files are the plugins that my script downloads, by the way. It moves those plugins to ~/epsxe/plugins/
But you are right, it moves any .cfg or cfg* file. This isn't my fault -- I've just realised that the terminal will be looking in ~, and so moving anything there

I've fixed all of the flaws you've mentioned. My installer is now safe to use.

All it does to ~/.bashrc is add the line
**alias epsxe="~/epsxe/epsxe"**
Which lets you type "epsxe" in the terminal, and be running epsxe.
at the bottom of the file. This part of the script is safe



**[size=20]Ok, so here is the old script: [/size]**

```

#!/bin/bash

# ePSXe install script written by Franky06
# This script will install ePSXe version 1.52, plugins, and biosen.
# The reason to which I have chosen version 1.52 is that
# though 1.6 has fixes for certain games, it breaks ALOT of games,
# and the fixes for 1.6 are only minor

# If you want to change this script in any way shape or form,
# go right ahead.
# In fact, I ENCOURAGE you to change this script, so it acts exactly
# how YOU want, since this is really just a simple script I wrote for myself,
# but released to the internet in the hope that it would be useful.

# Oh, and by the way, ENJOY! :D


# To make sure it installs to your home/user directory (recomended), we Compact-Disk to it
cd ~

# Downloading the archive containing the emulator
wget http://www.epsxe.com/files/epsxe152lin.zip 

# In ~, make an epsxe folder
mkdir epsxe 

# Move the .zip to the newly created epsxe folder
mv *.zip epsxe 

# Compact-Disk (lol) to the epsxe folder
cd epsxe 

# Unzip the zipped epsxe archive
unzip *.zip

# Remove the zip
rm *.zip 

# Compact-disk to the plugins folder
cd plugins 

# Download a video plugin for newer gpu's
wget http://www.pbernert.com/gpupetexgl208.tar.gz 

# Untar it
tar -xf gpupetexgl208.tar.gz 

# Remove it
rm gpupetexgl208.tar.gz 

# Move the plugins config's to the right folder
mv cfg* ../cfg 

# Move the other configs to the same place too
mv *.cfg ../cfg 


# Download and setup a video plugins for older cards
wget http://www.pbernert.com/gpupetemesagl176.tar.gz
tar -xf gpupetemesagl176.tar.gz
rm gpupetemesagl176.tar.gz
mv cfg* ../cfg
mv *.cfg ../cfg


# Downloading a sound plugin
wget http://www.pbernert.com/spupeopsoss109.tar.gz 

# Extract it!
tar -xf spupeopsoss109.tar.gz 

# KILL IT!
rm spupeopsoss109.tar.gz 

# Move the spu plugin configs to the right folder
mv cfg* ../cfg 

# Same as above
mv *.cfg ../cfg 

# CD to memcard folder and create two memcards
cd ../memcards
touch epsxe001.mcr epsxe000.mcr

# Create an alias to easily run epsxe
cd ~
echo alias epsxe="'~/epsxe/epsxe'" >> .bashrc

echo Installation complete. When wanting to run epsxe, just type "epsxe".
echo NOTE - THE PSX BIOSEN HAVE NOT BEEN DOWNLOADED, YOU'LL HAVE TO DUMP ONE
echo FROM A PSX THAT YOU ACTUALLY OWN!! You can search google and just download
echo it once you've found it, but I won't help you here because such activity is
echo illegal, and I don't want to get my *** sued, capiche?
echo Other than that, ePSXe is all setup, and all you hvae to do now is adjust the plugin
echo settings to your liking!
echo Enjoy.

```



**[size=20]And this here is the new script, where I've fixed everything: [/size]**
```

#!/bin/bash

# ePSXe install script written by Franky06
# This script will download all plugins, epsxe, 
# and put everything in the right place.

# It will not configure all the plugins or download
# the bioses, you have to do that yourself.


# To make sure it installs to your home/user directory (recomended), we Compact-Disk to it
cd ~

# Downloading the archive containing the emulator
wget http://www.epsxe.com/files/epsxe152lin.zip 

# In ~, make an epsxe folder
mkdir ~/epsxe 

# Move the .zip to the newly created epsxe folder
mv ~/epsxe152lin.zip ~/epsxe 

# Compact-Disk (lol) to the epsxe folder
cd ~/epsxe 

# Unzip the zipped epsxe archive
unzip ~/epsxe/*.zip

# Compact-disk to the plugins folder
cd ~/epsxe/plugins 

# Download a video plugin for newer gpu's
wget http://www.pbernert.com/gpupetexgl208.tar.gz 

# Untar it
tar -xf ~/epsxe/plugins/gpupetexgl208.tar.gz 

# Remove it
rm ~/epsxe/plugins/gpupetexgl208.tar.gz 

# Move the plugins config's to the right folder
mv ~/epsxe/plugins/cfg* ~/epsxe/plugins/../cfg 

# Move the other configs to the same place too
mv ~/epsxe/plugins/*.cfg ~/epsxe/plugins/../cfg 


# Download and setup a video plugins for older cards
wget http://www.pbernert.com/gpupetemesagl176.tar.gz
tar -xf /epsxe/plugins/gpupetemesagl176.tar.gz
rm ~/epsxe/plugins/gpupetemesagl176.tar.gz
mv ~/epsxe/plugins/cfg* ~/epsxe/plugins/../cfg
mv ~/epsxe/plugins/*.cfg ~/epsxe/plugins/../cfg


# Downloading a sound plugin
wget http://www.pbernert.com/spupeopsoss109.tar.gz 

# Extract it!
tar -xf ~/epsxe/plugins/spupeopsoss109.tar.gz 

# KILL IT!
rm ~/epsxe/plugins/spupeopsoss109.tar.gz 

# Move the spu plugin configs to the right folder
mv ~/epsxe/plugins/cfg* ~/epsxe/plugins/../cfg 

# Same as above
mv ~/epsxe/plugins/*.cfg ~/epsxe/plugins/../cfg 

# CD to memcard folder and create two memcards
cd ~/epsxe/plugins/../memcards
touch ~/epsxe/memcards/epsxe001.mcr ~/epsxe/memcards/epsxe000.mcr

# Create an alias to easily run epsxe
cd ~
echo alias epsxe="'~/epsxe/epsxe'" >> ~/.bashrc

echo Installation complete. When wanting to run epsxe, just type "epsxe".

```


As you can see, I specified exact folders. I still move every *.zip, *.cfg, cfg* and so on, but now I specify the exact folder they are in, so it no longer does anything you don't want it to.

It no longer deletes or moves any files.
**crouchingturbo**: As much as you were warning people off, telling them not to use my installer, I actually thank you. You've made me aware of the flaws in my installer, allowing me to fix them.

My installer is now 100% safe.

> **wiebeest said:**
> Hmm... Does this mean that if not succesfull up till now, better not go for ePSXe for now and stay with pSX? And does this mean maybe now the script has been moving files I don't want it to?
crouchingturbo was correct for pointing out teh dangers of using my script. I wasn't previously aware of the bugs in there, but thanks to him I became aware of them. I've fixed the installer, so it should be safe now.



crouchingturbo, you are on my main post, as a credited contributor.

Here's the new script then:

---

### Post by NightCrawler03X on 2008-05-13
Let me just re-emphasize:
 - My installer is now 100% safe.
 - Thank you for indirectly helping me **crouchingturbo**

To all people who used my old installer and found all your zip files deleted, I apologize.

---

### Post by wiebeest on 2008-05-13
> **NightCrawler03X said:**
> Let me just re-emphasize:
 - My installer is now 100% safe.

Good job!

On my original query you answered: > Your videocard drivers aren't configured correctly. But does anyone how I should configure them correctly? AKA: what is wrongly configured then, since stuff such as Compiz, or (games under) Wine work flawlessley...

[QUOTE=Wiebeest]Tried the installer mentioned in this thread, works to the fact of starting ePSXe, but when I load an iso, I get the following error:

Quote:* Running ePSXe emulator version 1.5.2.
* Memory handlers init.
* ePSXe: PSX BIOS loaded [/home/wiebeest/epsxe/bios/SCPH1001.BIN].
* Init ISO code ... ok
* NTSC cdrom detected.
* Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Xlib: extension "XFree86-VidModeExtension" missing on display ":2.0".Segmentatiefout
wiebeest@wiebeest-desktop:~$ 

Now, for the record: I'm using the Dutch language, so the error "Segmentatiefout" stands for "Segmentation fault" in English.[/QUOTE]

---

### Post by NightCrawler03X on 2008-05-13
Hmm. The plugin seems to be asking for Xfree86, but I assume that you are using Xorg as your graphical server right?

> AKA: what is wrongly configured then, since stuff such as Compiz, or (games under) Wine work flawlessley...
Those all work with the open source video drivers (you're using an ati/nvidia card I assume?). ePSXe plugins do not work with the open source drivers (except for Pete's software plugin which renders everything on the CPU, and only uses the graphics card to draw to the screen).

If you're using the open source drivers, switch to the proprietary ones since they are the only drivers that provide 3D acceleration, something that ePSXe needs. If you are using the open source drivers, do this and see if it helps, and if it doesn't, we will work from there.




To be honest, I'd actually just recommend the software plugin. It's so much better and has filters like scale2x and such. You can make games look much prettier than with the fullscreen anti-aliasing provided on the other gpu plugins.

And it doesn't need 3D hardware acceleration either.
It also has much less bugs. It's just better, easier, better.

I'll add it to the script later, but for now, you can get it using this:
```

cd ~/epsxe/plugins
wget http://www.pbernert.com/gpupeopssoftx117.tar.gz
tar -xf ~/epsxe/plugins/gpupeopssoftx117.tar.gz
rm ~/epsxe/plugins/*.tar.gz
mv ~/epsxe/plugins/cfg* ~/epsxe/plugins/../cfg
mv ~/epsxe/plugins/*.cfg ~/epsxe/plugins/../cfg

```

---

### Post by wiebeest on 2008-05-13
> **NightCrawler03X said:**
> Hmm. The plugin seems to be asking for Xfree86, but I assume that you are using Xorg as your graphical server right?

(snip)

If you're using the open source drivers, switch to the proprietary ones since they are the only drivers that provide 3D acceleration, something that ePSXe needs. If you are using the open source drivers, do this and see if it helps, and if it doesn't, we will work from there.

Ehhm... Yes, I have the standard Xorg as graphical server.
I have a nVidia Geforce 6600. Through synaptic I can see that I have the nVidia-glx-new enabled. And hardware drivers--> mentions that "third party proprietary drivers are bing used". Shouldn't that be okay?

---

### Post by NightCrawler03X on 2008-05-13
Yes, it should work correctly. I don't know anything about vnidia cards under linux (I have an ati card).

So, you're 3D acceleration works, but ePSXe won't run?
I have an idea, try:
```

glxinfo | grep render

```
on your terminal, and show me what it outputs

---

### Post by wiebeest on 2008-05-13
With the new installer I get a different error:

```
 * Running ePSXe emulator version 1.5.2.
 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/wiebeest/epsxe/bios/SCPH1001.BIN].
 * Init ISO code ... (+subchannel)ok
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteXGL2.so.2.0.8]
Error: couldn't get fbconfig
                            NVIDIA Corporation
                                              GeForce 6600/PCI/SSE2/3DNOW!
                                                                           * Open gpu[0]
 * Init spu[0][libspuEternal.so.1.41]
 * Open spu[0]

```

What gives???

---

### Post by wiebeest on 2008-05-13
> **NightCrawler03X said:**
> Yes, it should work correctly.
(snip)
So, you're 3D acceleration works, but ePSXe won't run?
I have an idea, try:
```

glxinfo | grep render

```
on your terminal, and show me what it outputs

Owk, " glxinfo | grep render" in terminal gives: 
```
wiebeest@wiebeest-desktop:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: GeForce 6600/PCI/SSE2/3DNOW!
wiebeest@wiebeest-desktop:~$ 

```

Does this help?

---

### Post by NightCrawler03X on 2008-05-13
I did a quick search on the forums, and it seems that other people have the same error as you when using xgl2 plugin (i.e. "couldn't get fbconfig"). It seems that the plugin is looking for something, but can't find it in your gpu's driver.

Try the MesaGL plugin.

In fact:
from this page, [http://ubuntuforums.org/showthread.php?t=95835](http://ubuntuforums.org/showthread.php?t=95835)
Someones says this:
> 
Brilliant guide thank you.

On my system the xgl2 driver causes a "couldn't get fbconfig" error. I changed to the mesa plugin mentioned above and is working okay for me.


the xgl2 plugin is obviously looking for something that is obsolete or something (that happens as api's in video drivers change). And I assume that (like you) this person has an nvidia card.

Try the MesaGL plugin for me, and tell me if that helps.

---

### Post by NightCrawler03X on 2008-05-13
> **wiebeest said:**
> Owk, " glxinfo | grep render" in terminal gives: 
```
wiebeest@wiebeest-desktop:~$ glxinfo | grep render
**direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**
OpenGL renderer string: GeForce 6600/PCI/SSE2/3DNOW!
wiebeest@wiebeest-desktop:~$ 

```

Does this help?
You don't have 3D Video Acceleration enabled.
Ignore my above post for now while I search for a solution.

Ok, I've just remembered something. I remember that beryl/compiz will disable direct rendering.
Disable compiz/beryl/xgl effects, then restart your X server (ctrl + alt + backspace, or do a system restart), then try glxinfo | grep render again. If this time direct rendering says "yes", try ePSXe again.

If ePSXe still doesn't work, try using the MesaGL plugin as I've explained above.

If even *that* doesn't work, use the software plugin.

---

### Post by wiebeest on 2008-05-13
MesaGL works!! 
Without disabling Compiz in the fist place. 

- (how does one disable Compiz inthe fist place, is there a setting/option for it?)
 
Anyhow, everything works super-fast with MesaGL with about every setting maxed-out!

Only full screen gives multiple errors in the terminal (in comparrison pSX doesnt allow fullscreen) and ePSXe doesnt recognise my Logitech Rumblepad2 (pSX does by default).

- Are there gamepad plugins available that'll make my rumblepad work?

I'll go and screw around with it some more and keep you informed.

Thanks for all the help so far mate. As memory served me well ePSXe plugin system makes the visuals much sweeter than pSX can, which was why I wanted to get ePSXe to get working in the fist place.

Wiebeest

---

### Post by NightCrawler03X on 2008-05-13
I'm glad you sorted your problem out :)
And I'm glad to be of service.

padJoy is pretty good if you want to use a joypad:
```

cd ~/epsxe/plugins
wget http://members.chello.at/erich.kitzmueller/ammoq/down/padJoy082.tgz
tar -xf padJoy082.tgz
rm padJoy082.tgz
mv ~/epsxe/plugins/padJoy/bin/cfg* ~/epsxe/cfg
mv ~/epsxe/plugins/padJoy/bin/*.so ~/epsxe/plugins

```
But I'm not sure about vibration support.
Hope that helps


I'm not sure now that you need to disable compiz anyway. If 3D works, then you don't need to disable it.

---

### Post by crouchingturbo on 2008-05-13
NightCrawler, glad to see the issues fixed.  Don't take it personally, but I felt it was important to warn people in a prominent way.  Cheers!

---

### Post by NightCrawler03X on 2008-05-14
> **crouchingturbo said:**
> NightCrawler, glad to see the issues fixed.  Don't take it personally, but I felt it was important to warn people in a prominent way.  Cheers!
Yeah, I know you weren't attacking me. You were attacking the issue, and the issue was that the script was dangerous. 

But I'm glad you warned everyone, since I was then aware of it, and thus able to fix it.

You are listed as a credited contributor on my first post in this thread.

---

### Post by NightCrawler03X on 2008-05-14
Updated the script:
 - Now downloads Pete's Software plugin (video) for those without 3D acceleration
 - Now downloads AmmoHQ's Joypad plugin, for those wanting to use a joypad

If anyone has any suggestions to improve the script, just mention it in this thread.

I've updated the links on my first post in this thread, so go download from there.
You can also download the new script here:

---

### Post by xjgnsdof on 2008-05-25
Does anyone know how to get USB controllers working. When I go into Config -> Game Pad -> Pad1, I see a dropdown menu that says "Digital Only." When I click the menu, there are no other options. How did you guys get your controllers to function?

Edit: I had to go to Ext. Game Pad and set my options there. Oops...

---

### Post by NightCrawler03X on 2008-05-26
Yep, recently added a few lines in the script to make it download AmmoHQ's joypad plugin. How's it going for you?

---

### Post by xjgnsdof on 2008-05-26
The controller works just fine. I used to run games in PCSX, but I find the simple yet thorough customization options in ePSXe to make it a far superior emulator.

---

### Post by NightCrawler03X on 2008-05-26
By the way guys, ePSXe 1.7 has been released (after donkeys of years, they decided to continue development again).

When they port it to linux, I'll create a script that downloads the new version (though it will be separate -- I'll keep on here the one that downloads 1.52, but as an addition have the one that downloads 1.7).

---

### Post by nemodot on 2008-11-06
Hi, I followed the steps and it worked good with the Iso's. 

But, there's a weird problem. The keyboard game pad doesn't fully work. most buttons do work but the directional keys don't :confused:

So, I can use the circle, the 'X', the triangle and the square but not the directional keys, what can I do?

---

### Post by ua6icab7 on 2008-11-06
[WOW Gold](http://www.gold4power.com/) was released in 2000 and is part of the WOW Hits series.It was a single 2-CD/2-cassette collection of contemporary Christian music from the 1960s to the time it was released. Marketing & distribution responsibilities for this title in the WOW Hits series was relegated to Brentwood Records (now Provident Music Group). The album reached #111 on the Billboard 200 chart.

---

### Post by manyyellowbirds on 2008-11-07
> **nemodot said:**
> Hi, I followed the steps and it worked good with the Iso's. 

But, there's a weird problem. The keyboard game pad doesn't fully work. most buttons do work but the directional keys don't :confused:

So, I can use the circle, the 'X', the triangle and the square but not the directional keys, what can I do?

I doubt you'll be coming back to check this after a year has gone, nemodot, but a workaroud is to assign the number keys to letter keys when you're in epsxe. :)

---

### Post by wiebeest on 2008-11-13
Guys, a tad off topic, but epsxe 1.7 works flawlessly under Wine.
If the program gives the error that it can not find the GPU plugins, just direct it to the corresponding directory through the wizard and you're ready... :-) 

Wiebeest

---

### Post by frankob on 2009-02-06
I have libgtk1.2 installed, but I still got the  error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Any idea?

---

### Post by Enji on 2009-02-21
I updated this script and would like to share it with you.

[http://rapidshare.com/files/200713211/installepsxe2.tar.gz.html](http://rapidshare.com/files/200713211/installepsxe2.tar.gz.html)

If you'd like to mirror it, please feel free.

Basically changes it to system wide install, updated for newer plugins, and has an uninstall function

to install:
go to terminal
tar -xz installepsxe2.tar.gz
sudo ./installepsxe -i 152 (or 160 for 1.6.0)

to remove:

sudo ./installepsxe -r

frankob I'd suggest you do this:

Open a Terminal

cd /usr/lib
find . -name libgtk1.2*

sudo ln -s (insert one of your matches here) libgtk-1.2.so.0

basically you're creating a symbolic link to the newer libraries with the name of the old to fool epsxe to use the newer gtk1.2

---

### Post by NightCrawler03X on 2009-03-04
Hey Enji, I haven't been here for a while, but I looked over your code and I quite like what you've done.

It's certainly much more sleek than mine, and makes certain things a lot easier.

---

### Post by Shademp on 2009-04-11
Downloaded ePSXe a few hours ago, from this site.
[http://www.emulator-zone.com/doc.php/psx/epsxe.html](http://www.emulator-zone.com/doc.php/psx/epsxe.html)

So I installed Delta, unpacked the two other zips, and downloaded several graphics plug-ins in hope that Delta would detect any of them. At first hand I am trying to find a "2D-game"-compatible plugin as I am trying to get my Mega Man X5 disc working on the emulator, and the plugin that is supposed to work is the
P.E.Op.S. Soft GPU.
[http://www.pbernert.com/html/gpu.htm#SOFTWIN](http://www.pbernert.com/html/gpu.htm#SOFTWIN)

Alas Delta refuses to detect any plug-ins.
I chose Settings --> Options --> Pcsx2 Overrides - Plugin Location,
then browsed for the zip with the plugin and then restarted Delta. However I can still not select any GPU Plugins on the Psx Graphics settings.

Problem with Bios too; there is only one file in the bios folder. "erase.me" Described as a ME-file, 25 byte. It can not be selected through
Settings --> Options --> Pcsx2 Overrides - Bios Location.

I don't know what to do. Note also that after I get the 2D-game Mega Man X5 working I also want my copy of FFVII to run. But like I said, I should have the proper plug-ins. They just aren't detected.

---

### Post by gimox on 2009-04-24
I've made an update version of you script, now it install epsxe 1.6, some updated version of plugins, and solve libgtk-1.2.so.0 problem.

---

### Post by markitoxs on 2009-04-26
> **gimox said:**
> I've made an update version of you script, now it install epsxe 1.6, some updated version of plugins, and solve libgtk-1.2.so.0 problem.

How many fps are we talking about?

---

### Post by Ceiling Fan Man on 2009-06-16
> **Enji said:**
> I updated this script and would like to share it with you.

[http://rapidshare.com/files/200713211/installepsxe2.tar.gz.html](http://rapidshare.com/files/200713211/installepsxe2.tar.gz.html)

If you'd like to mirror it, please feel free.

Basically changes it to system wide install, updated for newer plugins, and has an uninstall function

to install:
go to terminal
tar -xz installepsxe2.tar.gz
sudo ./installepsxe -i 152 (or 160 for 1.6.0)

to remove:

sudo ./installepsxe -r

frankob I'd suggest you do this:

[B]Open a Terminal

cd /usr/lib
find . -name libgtk1.2*

sudo ln -s (insert one of your matches here) libgtk-1.2.so.0

basically you're creating a symbolic link to the newer libraries with the name of the old to fool epsxe to use the newer gtk1.2[/B]

I'm suffering from the libgtk1.2.so.0 problem as well, but this does not work for me. The find command turns up nothing, and when I spt-get libgtk1.2 it just says I have the newest version already.

[QUOTE=gimox]I've made an update version of you script, now it install epsxe 1.6, some updated version of plugins, and solve libgtk-1.2.so.0 problem.[/QUOTE]

I installed your package, libgtk-1.2.so.0 problem persists.

I came to trying to install this emulator because I could not get pSX to work in Ubuntu Jaunty AMD64.

I tried pSX because the PCSX from the repositories plays FF8 (Final Fantasy VIII) way too fast without PS1 BIOS supplied, and way too slow with the BIOS.

..So frustrating. :(

---

### Post by NightCrawler03X on 2009-07-27
The libgtk1.2 problem: perhaps perform some sym link magic. Voila.
I barely even play PS1 games (emu or real thing) anymore, but came back to this thread out of boredom.

Thanks for making all these wonderful updates to my script while I was absent. Now, I will be absent again.

Hell, I don't even use emulators on the odd occasion I play PS1 games now. I did that "special thing" to my playstation (had to search the entire seven seas to find one of those things though, since they are now rare and everyone focuses on the ps2, which I've also done something special on), and now I just play everything on the real thing.

---

### Post by closetmonsterrr on 2009-09-22
hi, stupid question, but i must have done something wrong to begin with, or SERIOUSLY dont what what im doing. kinda both i feel...
im new to Linux and Ubuntu hardy specifically, but i cant even get the "cd" command (directory command right?) to work.
i downloaded the installer on the first post and its  on my desktop so i type in "cd /home/daniel/Desktop/installepsxe" and my terminal/konsole reads back "no such directory or file"
ive already downloaded the lib1.2 file and the upx-ucl-beta file.
did i miss something? was i supposed to actually download epsxe from there site with all of this?...
yours truly,
   Ubur-n00b

---

### Post by mastapat11 on 2009-10-23
> **closetmonsterrr said:**
> hi, stupid question, but i must have done something wrong to begin with, or SERIOUSLY dont what what im doing. kinda both i feel...
im new to Linux and Ubuntu hardy specifically, but i cant even get the "cd" command (directory command right?) to work.
i downloaded the installer on the first post and its  on my desktop so i type in "cd /home/daniel/Desktop/installepsxe" and my terminal/konsole reads back "no such directory or file"
ive already downloaded the lib1.2 file and the upx-ucl-beta file.
did i miss something? was i supposed to actually download epsxe from there site with all of this?...
yours truly,
   Ubur-n00b

If i read this correctly, the problem is that u don't have a folder on ur desktop called 'installepsxe' but a file called 'installepsxe.tar.gz'. correct??  If so then, use 
"cd /home/daniel/Desktop/".  Then untar it (tar -xf installepsxe.tar.gz), then type "sh installepsxe" (without the quotes).

hope that helps

---

### Post by mastapat11 on 2009-10-23
> **Ceiling Fan Man said:**
> I'm suffering from the libgtk1.2.so.0 problem as well, but this does not work for me. The find command turns up nothing, and when I apt-get libgtk1.2 it just says I have the newest version already.

I installed your package, libgtk-1.2.so.0 problem persists.

I came to trying to install this emulator because I could not get pSX to work in Ubuntu Jaunty AMD64.

..So frustrating. :(

I have Hardy x64. I'm running into this too._ i think it's an amd64 problem_ (just don't know what the solution is).  Here's a printout of my listing:

p@Go:~$ ls -l /usr/lib/libgtk*
lrwxrwxrwx 1 root root   19 2008-06-24 02:38 /usr/lib/libgtk-1.2.so.0 -> libgtk-1.2.so.0.9.1
-rw-r--r-- 1 root root 1.5M 2008-01-05 11:43 /usr/lib/libgtk-1.2.so.0.9.1
.
.
.

p@Go:~$ ls -l /usr/lib64/libgtk*
lrwxrwxrwx 1 root root   19 2008-06-24 02:38 /usr/lib64/libgtk-1.2.so.0 -> libgtk-1.2.so.0.9.1
-rw-r--r-- 1 root root 1.5M 2008-01-05 11:43 /usr/lib64/libgtk-1.2.so.0.9.1
.
.
.

Everything seems to be in place but i still get the error:
".../*epsxe: error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory*"

**Anybody have ANY ideas? tnx**

---

### Post by Rave Gloves on 2010-01-21
> **mastapat11 said:**
> If i read this correctly, the problem is that u don't have a folder on ur desktop called 'installepsxe' but a file called 'installepsxe.tar.gz'. correct??  If so then, use 
"cd /home/daniel/Desktop/".  Then untar it (tar -xf installepsxe.tar.gz), then type "sh installepsxe" (without the quotes).

hope that helps

Im facing the same problem, i cant get any codes to work at all.

andrew@andrew-laptop:~/Documents$ cd /home/andrew/downloads
bash: cd: /home/andrew/downloads: No such file or directory

---

### Post by angeloftheodd910 on 2010-01-23
Okay. I'm literally completely and totally new to Ubuntu. Yes. I am a n00b and I bow to those with skill.

Now that that's out of the way...I have owned MANY PlayStations. Literally. I've gone through 7, and I'm coming up on number 8--my (errr...new?) PS1 is going out on me, which is I guess to be expected given its age, but I'm honestly tired of having to mess with buying them over and over again. I'm hoping an emulator will last me a little longer, given that my computers don't fart out on me like the PlayStations do.

(And I've gone through 3 PS2s, just for the record--I would rather play the system on, well, the SYSTEM, than the computer, but, c'est la vie.) 

The games I want to play, I also own: I want to play Legend of Dragoon, which I own (but disc 3 is screwed); Final Fantasy VIII, similar problem; and Castlevania, Symphony of the Night. That's it, I own them.

Problem: I'm on a netbook and can't put a disc in. There's no disc drive.

So. This leads me to one single question.

I own this PS1. Where on it, or in it, is the BIOS I'm supposed to be looking for? The links for that stuff here have been coming up as "broken" in Google Chrome as of tonight, so...I have NO CLUE what the PS1 BIOS even *is*.

So what is the BIOS, and where from on or within this dumb box do I get it?

---

### Post by awinterbreeze77 on 2010-02-12
Google PSX or PSOne bios, click on the first link you see.. should have it. I would recommend downloading the PSX bios actually. Extract the files from the downloaded package into the bios folder within your epsxe folder. Then, once in epsxe, go to config -> bios and select the file that is named (I _think_) schp1001.bin or something very similar to that. For me, the file is always in all CAPS so it is easy to differentiate. 

That should do it. Any other questions about bios, just google them, should come up with an answer.

:)

---

### Post by burnsdm on 2010-02-26
Ceiling Fan Man - I have the same problem as you. I have libgtk-1.2.so.0 installed (as proven by ldconfig -p), yet epsxe still reports it cannot find it. Very frustrating.

> **Ceiling Fan Man said:**
> I'm suffering from the libgtk1.2.so.0 problem as well, but this does not work for me. The find command turns up nothing, and when I spt-get libgtk1.2 it just says I have the newest version already.

I installed your package, libgtk-1.2.so.0 problem persists.

I came to trying to install this emulator because I could not get pSX to work in Ubuntu Jaunty AMD64.

I tried pSX because the PCSX from the repositories plays FF8 (Final Fantasy VIII) way too fast without PS1 BIOS supplied, and way too slow with the BIOS.

..So frustrating. :(

---

### Post by ubunterooster on 2010-02-26
WOW!! cool.

---

### Post by burnsdm on 2010-02-26
Solution for those running 64 bit for whom epsxe reports: 

"error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Before/After running one of the generously provided install scripts, get the following three packages

[http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)
[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)
[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2)

For libglib1.2ldbl and libgtk1.2, make sure you download the 32 bit (i386) versions. You can then install them as follows:

dpkg -i **[B][B]--force-architecture **[/B][/B]filename

---

### Post by trent_2v on 2010-04-03
Hello.. I am new with ubuntu and i have ubuntu 9.10 so i dont very familiar with steps that i had to execute in the terminal.. please someone could tell me in especific and detail words what a had to do to install the emulator.. im already unzip the tar and execute the file that was inside of that but then a dont know what to do.. i apologise for my ignorance.. but please.. I need help.. Thank you..

---

### Post by TempleNav on 2010-06-16
I keep getting this error message everytime that I try to configure either the video or the sound plugins 
 * Running ePSXe emulator version 1.5.2.
plugins/libgpuPeopsMesaGL.2.so.1.0.78: undefined symbol: glColorTableEXTbrian@brian-desktop:~$ 

Someone told me that it has happened because the lib file might have been compiled for another computer. What exactly is going on here? everything else comes up except for the PEOPS sound and graphics plugins... And I tried installing 2 different versions of epsxe and they both crash whenever I get plugins and I go to configure them... This has me at my wits end...

---

### Post by NightCrawler03X on 2010-06-23
I'm not sure why people still use epSXE on Linux now. pcsx-df is better, and still supports all the same plugins. It also has decent AMD64 support, and is open source.

pSX might work on AMD64. It did for me, but the sound skipped. Though, that's probably because of the ALSA emulation (I deleted ALSA and Pulseaudio from my system, and replaced with OSS4.2 from 4Front)

---

### Post by syred on 2010-11-10
try this one 

[http://rapidshare.com/files/430092080/epsxe-install.tar.gz]("http://rapidshare.com/files/430089201/epsxe-install.tar.gz")

---

### Post by Yfrwlf on 2010-12-17
> **NightCrawler03X said:**
> I'm not sure why people still use epSXE on Linux now. pcsx-df is better, and still supports all the same plugins. It also has decent AMD64 support, and is open source.

pSX might work on AMD64. It did for me, but the sound skipped. Though, that's probably because of the ALSA emulation (I deleted ALSA and Pulseaudio from my system, and replaced with OSS4.2 from 4Front)

Thanks for your installer.  It's amazing to me though that any of these emulators get used much since none of them have nice installers, only have source files, or are just broken due to dependency hell.  Even including your improved installer, running these on Linux is way way way harder than running them on Windows for anyone but Linux geeks (and of course makes life more difficult for Linux geeks, too), which is a real shame.  Linux can't get ahead with these kinds of ridiculous problems still persisting even past 2010.

When the day comes when you don't need guides to do something simple like download and click on a Linux program to install/run it, Linux may actually start *really* taking off for normal PC users.

---

### Post by Yfrwlf on 2010-12-17
I recommend just getting PCSX-Reloaded from [http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)

Even though it's on Microsoft's Codeplex site which always recommends that you download the Windows version of binaries, unlike Sourceforge which actually heeds your browser string...

But, at least they have binaries that are easily installable, even if they aren't a nice cross-distro solution.

---

### Post by Simeo on 2011-01-07
> **Yfrwlf said:**
> When the day comes when you don't need guides to do something simple like download and click on a Linux program to install/run it, Linux may actually start *really* taking off for normal PC users.

It's true. I SO want to turn my friends on to Ubuntu...but because they aren't as tech savvy as me it's hard for them. We need the double click...  [-o<

---

### Post by Yfrwlf on 2011-01-08
> **Simeo said:**
> It's true. I SO want to turn my friends on to Ubuntu...but because they aren't as tech savvy as me it's hard for them. We need the double click...  [-o<

At least there's [Zero Install]("http://zero-install.sourceforge.net/") for cross-distro packages.  It's the closest thing I've been able to find to a solution.  Supposedly you can quickly and easily resolve all dependency issues with it and it will automatically download and install them all in a decentralised way. (I say "supposedly" only because I want to be sure that this works in every situation, but no doubt things like programs wanting to install hardware drivers will throw major issues, even though that should be uncommon.  ZI definitely works though for most things!)

I think the biggest problem holding it back my simply be adoption, and better integration with the existing what I call proprietary package managers.  If Ubuntu started shipping with a package manager which included support for ZI packages, that would really help it take off, but either it is severely lacking in some area (which I'm not sure where or how it's lacking) or distros are simply failing to acknowledge one of the biggest problems still facing Linux adoption today, since decentralised software distribution/sharing is one of the biggest enablers of adoption.

This thread is proof of that, proof that there is a demand for that feature, and proof that it's a headache for Linux users.  Linux needs to be the opposite of a headache. :(

The other possibility is they don't want to make software sharing easy because they are more interested in having all users have to come directly to them as the sole source for software.  If that is true, it is partially greed then that is stopping true Linux software freedom which certainly would be a real shame and definitely goes against the principals of the ubuntu philosophy.  Linux has such a small share of users already that infighting is the worst thing it can do to itself.  It takes standards to create true freedom, and not end up destroyed due to a rehashing of the Unix Wars.  Sure, open source can't be completely destroyed ever, but it can be code rotted and fall severely behind due to adoption problems caused by a lack of incredibly useful features like installation standards.

---

### Post by djaqed on 2011-02-16
So I ran the installer and when I attempted to run the program I was confronted with the following:

```
/home/skewter/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

what do I do?

---

### Post by Yfrwlf on 2011-03-29
> **djaqed said:**
> So I ran the installer and when I attempted to run the program I was confronted with the following:

```
/home/skewter/epsxe/epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

what do I do?

You need to get that library somehow and put it where it's searching for it.  It's the result of the lack of a proper package management system utilizing cross-distro standards.

Find out what libgtk version you have, find where the lib is, and find the version it wants and put it next to the one you have already.

---

### Post by MestreLion on 2011-05-14
> **Simeo said:**
> It's true. I SO want to turn my friends on to Ubuntu...but because they aren't as tech savvy as me it's hard for them. We need the double click...  [-o<

For me a .DEB file ***is*** a double-click, painless, trouble-free, install. And it has dependecy checking and auto-update (if using repositories)

ePSXe is a 2003 software. Ubuntu didnt even existed back then, but ive found at least one PSX emulator that works out-of-the-box in Maverick: **PCSX-Reloaded** (based on PCSX-DF)

[http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)

Installation cant be easier: download, double-click, go to menu, play. Nice, simple GUI. Cant tell about performance or settings or plugins (just tested FF7), but it looks promising, and its a nice one to suggest to people that coming from windows and new to ubuntu/linux

---

### Post by Yfrwlf on 2011-05-14
> **MestreLion said:**
> For me a .DEB file ***is*** a double-click, painless, trouble-free, install. And it has dependecy checking and auto-update (if using repositories)

ePSXe is a 2003 software. Ubuntu didnt even existed back then, but ive found at least one PSX emulator that works out-of-the-box in Maverick: **PCSX-Reloaded** (based on PCSX-DF)

[http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048)

Installation cant be easier: download, double-click, go to menu, play. Nice, simple GUI. Cant tell about performance or settings or plugins (just tested FF7), but it looks promising, and its a nice one to suggest to people that coming from windows and new to ubuntu/linux

Once again, there are lots of Linux distros out there, so developers providing a package for each of them is **not an option**.  I also do NOT want to have copies of all those different packages if they do make lots just in case I switch distros, and I don't want a different version of the package for every version of the distro for when I upgrade distro versions.  I want a program package that will basically be capable of surviving forever, with maybe a few tweaks in the future if it becomes really old, but preferably the system will always be able to cope, I'll always have access or be able to store all needed dependencies easily, etc.

There has to be a universal package format, end of story.  Everyone should use Zero Install until all the major package managers a) make DEB, RPM, or any of the others compatible with the major managers, or b) adopt a new format if needed and make all managers compatible with it.  Whatever it takes to install the stupid correct versions of the stupid libraries on my stupid system to run the stupid software!  lol  End users don't **care** about the details, they just want their god damn software to be easily installable and to work, and until that can happen in a **standardized cross-distro decentralized** way so that developers can actually easily package for Linux, and so that users can easily click on a single Linux package and get the software downloaded and installed **from any source**, Linux = fail.

There is also this AppStream thing happening which supposedly is meant to do just that, if I understand it correctly:

[http://www.youtube.com/watch?v=BHeP2ZBwS_U](http://www.youtube.com/watch?v=BHeP2ZBwS_U)

---

