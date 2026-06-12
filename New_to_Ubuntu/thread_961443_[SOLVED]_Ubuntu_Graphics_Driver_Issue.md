---
title: "[SOLVED] Ubuntu Graphics Driver Issue"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-10-28
Hello everyone,

I am a Linux and Ubuntu noob user, I know the ATI/NVIDIA graphics driver problem is not the fault of either Linux or Ubuntu, but as a new user I find not being able to use the 3D functions of my graphics card extreamly annoying and may even be enough to put new users off using Linux/Ubuntu completely.

I have tried to install the drivers but have no luck EnvyNG doesn't even display an Icon or menu and the default version woundn't acknowledge the correct .deb file. I find not having and automatic (or GUI Based) video driver a major obstacle in using linux as a new user.

Is their any particular card which will auto install with 3D effects on Ubuntu 8.04 or higher without having to use the shell? 

As I am beginning to think it would be easier to dispose of My Nvidia 6600GT and buy a card that isn't such a pain to use with Linux.

Thanks In Advance

Sharkster

---

### Post by Titan8990 on 2008-10-28
What do you mean Envyng doesn't display an icon or menu? If you installed it via the synaptic package manager or sudo apt-get install envyng-gtk then it should be located under Applications -> System Tools.

Envyng should work fine with your 6600GT.

---

### Post by sharkster2007 on 2008-10-28
I also heard of Nouveux but this is under development and only seems to be using 2D if this supported 3D this would be an ideal solution.

---

### Post by sharkster2007 on 2008-10-28
Thanks Titan8990

I ll have a look for that and try again, I double clicked the .deb file (My PC Is not on the internet hence I was using a downloaded .deb file from another PC I have access to) which seemed to bring the synaptic package manager up to install it, I couldn't find the program afterwards.

Cheers for your help

---

### Post by gekk0 on 2008-10-28
> **Titan8990 said:**
> What do you mean Envyng doesn't display an icon or menu? If you installed it via the synaptic package manager or sudo apt-get install envyng-gtk then it should be located under Applications -> System Tools.

Envyng should work fine with your 6600GT.

But it doesn't work with my Radeon 9600 Series, why?:?

---

### Post by Titan8990 on 2008-10-28
> But it doesn't work with my Radeon 9600 Series, why?


Because ATI has a history of poor Linux support. They have been getting their act together since they got purchased by AMD but are still not quite there.

---

### Post by Tom--d on 2008-10-28
> **sharkster2007 said:**
> 'snip' Nvidia 6600GT 'snip'

Nvidia have great drivers for linux, infact, they are the best! Closed source but I would use the evil closed sourced drivers over the open source drivers atm.

All you need to do is go into System > Admin > Hardware Drivers and enable the Nvidia driver. Simple.

---

### Post by sharkster2007 on 2008-10-28
Thanks Tom-d but this too doesn't work

When the installer reaches installation from the ubuntu server it fails (as my machine is not on the internet)

The .deb files i am using are envyng-core.1.1.1ubuntu10.all.deb for EnvyNG and Nvidia-glx-legacy_71.86.04.+2.6.24.13-19.45_i386.deb for the Nvidia driver.

The EnvyNG seems to install as the installer button changes to reinstall when you try the 2nd time but no icon or toolbar exists to use it with.

The Nvidia driver seems to install in around two seconds but when you click the .deb file again it just says install on the button not re-install.

Neither work I am i right to asume the .deb file I am working with are broken as the installer claims all dependacies are satified for both?

Custom Built: Pentium 4 2.4Ghz - 1GB Ram - 3 HDD's 160GB, 80GB, 160GB - Ubuntu 8.04

---

### Post by sharkster2007 on 2008-10-28
To be honest I thank you all for trying to help, this ATI/Nvidia graphics issue is a total joke (Only its not funny at all to new users who don't yet wish to get involved in command lines).

I have recently heard reviews that Ubuntu 8.10 automatically sets up 3d effects and hope to god this is true as i accept that certain drivers may not work but for god's sake file system, sound and graphics are basic issues assumed to be included (& working)with every OS as standard.

I wish Microsoft would have had issues like this with windows 95 as the damn thing would never have took off and I wouldn't have been forced into buying a PC in the first place. 

Part of my reason for moving to Linux was because I was an Amiga 1200 user, with a 030 accelerator, 8mb ram, cd-rom drive and 20Gb hard drive that did everything my PC could do a damn site easier and more stable. I hung on until i could no longer and sold it to buy a "fridge" of a PC that quite honestly has been a pain in the rear (with both Windows & Linux) compared to my Amiga.

This will not deter me from using Linux though as fortunately I can dual boot between Windows XP SP3 and Ubuntu Linux.

I find issues like this a top priority for newcomers to linux, if others like me want to ditch windows totally this is a major roadblock to total migration to linux, all this issue does is make Microsoft look good and thats no help to any of us here.

Took Quote Linus (Linux Kernel Inventor) "Make it work first..."

---

### Post by sharkster2007 on 2008-10-28
Sorry If i come across ranting and annoyed but I am an intermediate user of Windows and was also trained in how to use MS-DOS. I can't remember the last time I have had to resort to using ms-dos commands to get things done (and never have with graphics cards they "Just Worked" until I could replace them with a better driver. 

I have also tried downloading the official Nvidia driver which is in some damned .run format (whatever the hell that is) and seems as much use as a chocolate fireguard as I seem to be able to read it but not much else.

Again sorry for the rant and thanks for trying to help, but problems like this are going to send more new linux users running for the (Windows) hills than encourage them to learn and become familiar with linux.

---

### Post by aktiwers on 2008-10-28
Some things are done differently on Linux than on Windows.. Actually I believe it is easier to help you with a set of commands, than trying to explain where you need to click and what to click next.

For the .run file, you will probably be scared all the way back to Windows land! :D

But here goes:.. (this is not the official way to install drivers though)
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Just change the .run file name to the same as the one you downloaded (the guide is a bit old)

---

### Post by sharkster2007 on 2008-10-28
Thanks aktiwers

Guess its back to the old MS-DOS days again (ironically I started using before I used Windows, so same story different system LOL)

I doubt this will work as every other method I've tried has failed even with Fedora, Suse, Linux Mint, Debian, etc. I am not in anyway questioning any other users Linux abilities but my own i find all this a bit much just to enable 3d effects as a new user but will try when I get the chance. 

Though I am very tempted to just "bugger it off" and wait until Ubuntu deals with this automatically and just to use it in 2D Mode and to hell with the effects as a new user. 

I have read most of "Rebel Code" by Glynn Moody, and understand the Linux worlds difference's and the benevolence of its creators and contributors, and those of the GNU project. 

I would add as a new user I don't really care whether the drivers are "open source" or "restricted" as long as they work. Though open-source alternative would become replacements for the "restricted ones" as they become available.

On the more positive side I would like to add that I find Linux users far more helpful than Windows ones and would like to thank those that replied for their help though.

---

### Post by aktiwers on 2008-10-28
Let me know how it goes :)
Just remember to change the filename to your own.. I used to have the same card ;)

---

### Post by aktiwers on 2008-10-28
After rereading the thread, it would really be more easy for you to plug it in to the net.. and go to System => Administration => Hardware drivers
Or restricted drivers or whatever it is called..

This way Ubuntu downloads and installs the driver for you automatically.

---

### Post by sharkster2007 on 2008-10-28
Thanks again but it is not possible in my case, I stated before the files are downloaded on a different desktop pc, the two pc's are not networked and the other user doesn't want linux on their pc (The Internet one).

Mine is a standalone desktop pc, I am using files downloaded by saving the required files with a usb stick from a windows based web-browser (firefox) and a windows download manager to aquire the .deb files needed.

It would be a lot easier with an internet connection I agree, but this is not possible in my case. I have a book on ubuntu linux 6.04 but in the chapter it says to use the internet to update too (very annoying if your PC is not on the internet) and cost over £25 pound for this advice. 

Thanks again for your help, may as well try to manual install as in a days time I plan to be using ubuntu 8.10 so nothing to lose really. I can dual boot and use the windows recovery consoles "fixmbr" command if needed.

---

### Post by gekk0 on 2008-10-28
Could some help me out to solve my Radeon 9600 problem.

> root@faris-desktop:/home/faris/Downloads# glxinfo |grep vendor
No protocol specified
Error: unable to open display :0.0

---

### Post by sharkster2007 on 2008-10-29
Thanks Aktiwers

I think this may be the way forward but again I have encountered problems, least I've overcome the fear of the command line though :-)

Sudo aptitude install libc6 libc6-dev

This command worked

sudo aptitude install build-essential linux headers-$(unname-r)

This sommand seemed to fail on the -$(uname-r); 
"Bash: syntax error near unexpected token `('" was the message I got.

I continued with out the -$ (uname-r); part

I downloaded the linux driver from Nvidia's website, Log out worked, as did cd Desktop command.

sudo /etc/init.d/gdm stop

This command went ok

then it all went wrong my driver was on my desktop i could see it was there with the dir command but ubuntu would not install it said something along the lines of "0 packages installed, 0 modified". the same occured when booting back into main ubuntu (X Windows) and running the install commands their both with the .run file & the .deb file.  

I have renamed the NVIDIA Linux command to the current one as suggested, still no joy.

Any suggestions?

---

### Post by igknighted on 2008-10-29
Linux without any internet, even in the setup stage, is a very difficult proposition.  Linux uses shared libraries (as microsoft is starting to as well), and so they come packaged separately.  Therefor, to install one seemingly stand-alone program, you often need a horde of others that work behind the scene (or in the case of your drivers, you need compilers and header files for the kernel to build against).  This is because in linux, all drivers are part of the kernel.  Since the Nvidia driver cannot be shipped with the kernel due to license issues, it must be compiled for that specific kernel, and hence the complicated install.

I would recommend you look into something like Mandriva where these drivers like the nvidia one are pre-installed.  This way you don't have to worry about downloading a whole string of dependencies, and it should "just work".

---

### Post by sharkster2007 on 2008-10-29
Thanks againn igknighted,

I am off to try out Mandriva Linux One 2009, this doesn't appear to suffer the same licence issues that Ubuntu does, I liked Linux mint as it did a lot of setting up automatically for me on install without needing the internet.

This may well be the answer I am looking for thanks for your advice maybe I am for Linux, just need another distro. 

(Thank god there's still hope i don't want to be stuck with windows forever lol) ;-)

---

### Post by phidia on 2008-10-29
Sabayon also does a great job of having the nvidia & ati drivers scripted for automatic configuring-they even work in the live cd.

---

### Post by sharkster2007 on 2008-10-29
Thank you igknighted , Knix and the others

I have now migrated to Mandriva Linux One 2009, I find it's hardware support excellent, just what I wanted. 

Now I can explore linux without that blasted 3D effects prob (It even worked from the livecd before I installed it).

I now dual boot Windows Xp SP3 and Linux Mandriva Linux One 2009 and I am very pleased with my new Linux distro.  I did think of abandoning Linux full stop, but as I said before something keeps bringing me back to it. 

Thanks for the command line help and the Mandriva Linux One suggestion I am over the moon and still using Linux too.

Thanks to all who helped (& tried to help me) happy Linux computing to you all

Best wishes Sharkster2007

31/10/08 EDIT - I am back but this time using Ubuntu 8.10 (Final) and now have a "propriety" .deb file;
 "nvidia-173-kernel-source_173.14.12-0ubuntu3_i386", hope this solves my previous problems without the hassle i had before.

*If it wasn't for the help I received here and my temporary migration to Mandriva Linux One 2009 (& seen desktop effects working). I would have consigned this to the occult arts and given up on this issue, I also want to use ubuntu and have the latest Apress Book on Linux (Hardy Heron)*

---

### Post by aktiwers on 2008-10-29
No problem and happy Linux computing your self! 
Remember to check back if you have more questions ;)

---

### Post by sharkster2007 on 2008-11-01
Greyarea2 has the internet connected solution [http://ubuntuforums.org/showthread.php?t=965741]("http://ubuntuforums.org/showthread.php?t=965741")
and now I've added my sharkster2007 manual one for none internet connected users.

---

### Post by sharkster2007 on 2008-11-06
6th November 2008 I now have a better manual solution for Nvidia drivers & activation, compiz settings, nvidia settings and 3d cube set-up located here.

[http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=973038&highlight=nvidia)

Sharkster2007

---

