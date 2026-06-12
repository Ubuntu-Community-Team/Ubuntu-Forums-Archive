---
title: "Install ubuntu on Alienware M11x R3 - Is there an easy way?"
date: 2017-03-24
forum: New to Ubuntu
---

### Post by gil80 on 2017-03-24
Hi all,

I'm new here, so I apologise in advance for newbie question. If I posted on the wrong forums, please remove my post.

I own an Alienware M11x R3 and Windows 10 doesn't work well on this laptop. For example, if the laptop is connected to external monitor (which is 100% of the time), after 24 hours, I can't get the screen to wake up. The laptop is working, but there's not display. I have to reboot it.
I believe it's the nVidia driver (latest) but I have no idea how to fix it.
The lead me to a point that I thought "what the heck, let's try Ubuntu".

After a bit of google search, it seems that it's not an easy thing to accomplish, however the posts I read were from 2012. I wonder if by now it is easier to install it.

Here are the specs of my laptop:
[[IMG]https://s29.postimg.org/u9z79t407/specs.png[/IMG]]("https://postimg.org/image/ggaukrber/")

I mostly use this laptop for streaming and browsing.
I need this laptop to connect to my external monitor via HDMI.

Thanks for the help!

---

### Post by RobGoss on 2017-03-25
Hello and welcome, Can you tell us what you've done to get Ubuntu installed on your machine?

Please give as much details as you can it will help us give you the best advice possible

---

### Post by aokurami on 2017-03-25
Hello, gil80!

If you are fine with removing Windows 10 from your laptop, you could just use LiveUSB with Ubuntu on it to boot and install from it a fresh version (Pretty straight forward actions, you'll see the choice "Install alongside Windows").
However, if you are looking for a way to dual-boot, that's would be a bit more complicated, but fun to do.

Please, notify all those willing to help you with your reply.

---

### Post by gil80 on 2017-03-25
> **RobGoss said:**
> Hello and welcome, Can you tell us what you've done to get Ubuntu installed on your machine?

Please give as much details as you can it will help us give you the best advice possible

Hi. I haven't installed it yet. I'm looking forward to get Ubuntu installed

> **aokurami said:**
>  
[FONT=georgia]**Hello, gil80!**

If you are fine with removing Windows 10 from your laptop, you could just use LiveUSB with Ubuntu on it to boot and install from it a fresh version (Pretty straight forward actions, you'll see the choice "Install alongside Windows").
However, if you are looking for a way to dual-boot, that's would be a bit more complicated, but fun to do.

Please, notify all those willing to help you with your reply.[/FONT]

Hi. I don't think I'll need a dual boot. I have an image of the SSD backed up, so worst case I can restore it.

I want to have my laptop boot only Ubuntu, but I'm not sure Ubuntu has the drivers to make everything work, like USB3.0, HDMI, nVidia GPU, etc.

---

### Post by oldrocker99 on 2017-03-25
> **gil80 said:**
> 

I want to have my laptop boot only Ubuntu, but I'm not sure Ubuntu has the drivers to make everything work, like USB3.0, HDMI, nVidia GPU, etc.

USB 3.0 does work, but I had to add a command in grub to make it work on my MSI motherboard. HDMI certainly works. The nVidia GPU does need proprietary nVidia drivers, which are easy enough to install. The Linux kernel has a lot of drivers built-in. You'll find that Ubuntu "just works."

---

### Post by RobGoss on 2017-03-25
**+1 Oldrocker99**

---

### Post by RobGoss on 2017-03-25
> I want to have my laptop boot only Ubuntu, but I'm not sure Ubuntu has the drivers to make everything work, like USB3.0, HDMI, nVidia GPU, etc.

Run the live installer for **16.04.2** that should give you a good idea of how things will work, in my experiences I never had any issues installing Ubuntu on any of my machines honest truth

---

### Post by aokurami on 2017-03-25
Make sure to partition your disk according to your needs using Gparted. Best case scenario:

- Root partition: "/" - comment.
- Swap partition: "swap" - 1-2 times of your RAM.
- Home patition: "/home" - comment.

---

### Post by gil80 on 2017-03-25
> **oldrocker99 said:**
> USB 3.0 does work, but I had to add a command in grub to make it work on my MSI motherboard. HDMI certainly works. The nVidia GPU does need proprietary nVidia drivers, which are easy enough to install. The Linux kernel has a lot of drivers built-in. You'll find that Ubuntu "just works."

That's what I asked in the title :) it seems then it's not an easy process after all. I don't know how to install nvidia drivers, unless it's an installation file. I don't know what's a grub command. It seems as it's not a case of "just works" if you manually have to do these installations.

> **aokurami said:**
> [FONT=georgia]Make sure to partition your disk according to your needs using Gparted. Best case scenario:

- Root partition: "/" - comment.
- Swap partition: "swap" - 1-2 times of your RAM.
- Home patition: "/home" - comment.[/FONT]

Does the live install allow to choose how to format the SSD like in Windows installation?
otherwise, I don't know how to do what you've just said because it will wipe the SSD while the OS is on it? :)

---

### Post by mastablasta on 2017-03-27
> **gil80 said:**
> That's what I asked in the title :) it seems then it's not an easy process after all. I don't know how to install nvidia drivers, unless it's an installation file. I don't know what's a grub command. It seems as it's not a case of "just works" if you manually have to do these installations.

Does the live install allow to choose how to format the SSD like in Windows installation?
otherwise, I don't know how to do what you've just said because it will wipe the SSD while the OS is on it? :)

the process of install itself is easy. it takes about 5 or so screens. dual boot could be a bit more complicated, but not if you are using MBR (rather than some other partitioning scheme).

drivers are installed via additional drivers aplication. you run it, select the drivers you want to add and click install. the issue with some laptops is that nVidia decided not to support optimus in Linux. for that you need bumblebee and do manual switch between intel and nVidia more here: [SIZE=2]https://wiki.ubuntu.com/Bumblebee
[/SIZE]
note that all commands can be copy pasted into terminal. in fact if you are sure you want to execute them copying them is the best way to avoid any typos.

GRUB is a boot loader. windows uses it's own boot loader (you can see it if you hold F8 on boot or at leats that was the case in older versions). windows boot loader can boot only windows. GRUB can boot various operating systems. 

live session - you boot from USB or DVD. it loads the whole OS in RAM. it uses opensource drivers only (part of linux kernel), which in nvidia case are reverse engineered and kind of crappy, but good enough for desktop work. when you exit it it will all be "forgoten", unless you do some changes on hard disk. it's a safe way to try the OS. however, in your case if oyu have nvidia Optimus (intel+nvidia) you will not be able to install drivers, to test the OS fully. you cna install them but you will need ot reboot to finish the install and as soon as oyu reboot the information is lost (because it is in RAM). but there is a workarorund - you can use USB and add a persistance file to it (check linux live USB for windows, A.k.a LiLi). a persistance file will keep system informaiton on USB. so if you use a USB , add say 2 Gb of persistance ot it, then install the drivers and reboot, the information will stay on USB. so you should be able to fully test the system that way, without making any changes to your hard disk. 

the install itself in live session will offer a number of things. you can go fully expert on it or just let it do it's thing. the point is you are in full ocntorl. best thing abotu live sesstion install you can surf the web while doing it or if you need help you can join the IRC channel and get live support from volunteers there while you install the OS.

---

### Post by gil80 on 2017-03-27
hi and thanks for the detailed reply.

I want to use this laptop for Kodi and some other basic stuff.
For this, I must have nVidia drivers installed. I'll try your suggestion with the live USB and persistent data option.

If I decide to install Ubuntu as the only OS, will it prompt for formatting the SSD to EXT4?
Should I choose a better option for the SSD?

thanks!

---

### Post by mastablasta on 2017-03-27
> **gil80 said:**
> 
If I decide to install Ubuntu as the only OS, will it prompt for formatting the SSD to EXT4?

check the community made manual in my link.

selecting "use whole disk" will automatically partition it and format it in ext4. the "something else" choice will give you full control over how you will parition it and the file system you want to use for certain parittion. ext4 is the recomended one (let's say "the sane default") but there are others. it will do fine for SSD.

if you are creating manual partitions then you will need at least two partitions 
1. the root partition (/) and 
2. the swap partition (/swap). 

others are optional.

---

### Post by gil80 on 2017-03-27
> **mastablasta said:**
> check the community made manual in my link.

selecting "use whole disk" will automatically partition it and format it in ext4. the "something else" choice will give you full control over how you will parition it and the file system you want to use for certain parittion. ext4 is the recomended one (let's say "the sane default") but there are others. it will do fine for SSD.

if you are creating manual partitions then you will need at least two partitions 
1. the root partition (/) and 
2. the swap partition (/swap). 

others are optional.

I went to the LiLi website and to the Ubuntu section. Which version should I choose? I run Intel i7 2770K.

---

### Post by mastablasta on 2017-03-28
if you already have Ubuntu installed then use the one for your Ubgutnu OS (either 32 bit or 64 bit depending in the OS)
if you have Windows installed, then use this one: [SIZE=2]http://www.linuxliveusb.com/en/download

as for which Ubuntu to use --> use 64bit

[/SIZE]32bit will work just as well, but 64 bit should be a tiny bit faster.

---

### Post by gil80 on 2017-03-28
So, today I installed Ubuntu Desktop via USB and my laptop gets stuck on random. for example, it didn't boot at first. It got stuck on purple screen. After a shutting down, it booted ok. Then the update process gets stuck. After a restart, the Installation of updates got stuck again mid-way.
I can open the file browser and wonder around the system, but it doesn't seem to update/install or really work as it should.

Can someone help me troubleshoot this?

---

### Post by mastablasta on 2017-03-29
make sure the downloaded image you used to create the USB is good. more here: [SIZE=2][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

you might need to use nomodeset on first boot. more here: 
[SIZE=2][https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

this uses basic VGA graphics (kind of like Windows safe mode), but if boot is successfull you can then proceed to install and configure the necessary additional drivers (nVidia proprietary + bumblebee).

[/SIZE]

[/SIZE]

---

### Post by gil80 on 2017-03-29
> **mastablasta said:**
> make sure the downloaded image you used to create the USB is good. more here: [SIZE=2][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

you might need to use nomodeset on first boot. more here: 
[SIZE=2][https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

this uses basic VGA graphics (kind of like Windows safe mode), but if boot is successfull you can then proceed to install and configure the necessary additional drivers (nVidia proprietary + bumblebee).

[/SIZE]

[/SIZE]

Ok,
so I was reading that there's a bug that .deb files cannot be installed.
I seem to have this bug.
so I did 'sudo apt-get update' and then 'sudo apt-get upgrade' and I got some error messages


a quick search got me to this: [http://askubuntu.com/questions/329450/e-some-index-files-failed-to-download-they-have-been-ignored-or-old-ones-used](http://askubuntu.com/questions/329450/e-some-index-files-failed-to-download-they-have-been-ignored-or-old-ones-used)


So I used the solution provided in this link. The 'rm -rf' command didn't work.
Anyway, I was then able to install .deb files but the App Market is changed and it doesn't show the suggested apps as you usually see when you have a new installation of Ubuntu.


Trying to run some apt-get commands, I always end up with the following:

dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/module-init-tools_3.16-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mastablasta on 2017-03-30
this looks like a completelly different issue from where we started. 

what kind of .deb files? which ones exactly? 

nVidia driver can be and should be installed via PPA (if additional drivers app doesn't offer it) as well as bumblebee. these are the recomended methods i believe, since AFAIK you will need the repository to patch the kernel upon its inevitable update.

bumblebee is for switching between nVidia and intel GPU. installing only nVidia drivers Will make PC run only using nVidia GPU which might not be a good idea if you want to save battery power.

---

### Post by gil80 on 2017-03-30
> **mastablasta said:**
> this looks like a completelly different issue from where we started. 

what kind of .deb files? which ones exactly? 

nVidia driver can be and should be installed via PPA (if additional drivers app doesn't offer it) as well as bumblebee. these are the recomended methods i believe, since AFAIK you will need the repository to patch the kernel upon its inevitable update.

bumblebee is for switching between nVidia and intel GPU. installing only nVidia drivers Will make PC run only using nVidia GPU which might not be a good idea if you want to save battery power.

any app I try to install from Ubuntu Software. 
I thought Ubuntu just works :/
I installed ubuntu from scratch and here is what I find:
1. Initial boot after finishing installing, fails. I need to reset the laptop. From that point, all booting goes well.
2. Any app I try to install from ubuntu software does not get installed. The install button will progress partially and then it will stop installing. The button will return to show 'Install'.
3. As for the nvidia driver, I do not know what to do really. I would like to use this laptop mostly for Kodi and for this I need the nVidia GPU to work.

I have no idea what is PPA.

---

### Post by mastablasta on 2017-03-30
> **gil80 said:**
> any app I try to install from Ubuntu Software. 
I thought Ubuntu just works :/

it should, it does.

and just like windows it has no problem working if the hardware is supported by manufacturers. in other words, try to install Windows on a Mac and see what happens.

in any case looking through threads from others it seem that while this model is not officially supported, the install will work. the only issue people had on this model was with optimus GPU switching, but even that was resolved (though a manual switch) in 2014/2015.

> 
I installed ubuntu from scratch and here is what I find:
1. Initial boot after finishing installing, fails. I need to reset the laptop. From that point, all booting goes well.

this should not happen. what does "fails" mean? an error message? blank screen?

> 
2. Any app I try to install from ubuntu software does not get installed. The install button will progress partially and then it will stop installing. The button will return to show 'Install'.

this might have something to do with no. 1. or not. try installing using command line for example let's install htop (a nice small command line utility for monitoring system resources) - start up the terminal and enter:

```
sudo apt-get install htop
```
it will ask for a password. type in your user password and press enter (you won't see anything displayed while you type - a security feature )
it will then say how much space it will take, what things will be installed etc. and ask you to cofnirm the install. 
confirm with Y and enter
now it should either succesfully install the application or it will throw out an error. if there is an error mark the text, right click it and post it here using code tags (the # icon in advanced reply). if it is not working porpperly the only way we can know why and how to help is by seing the erorr that is presented. or to guess.

some good advice for troublehsooting is found in [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

if nothing else you can see how to check if OS identified hardware correctly.

finally if Windows had issues on PC as well it might be worth to run hardware diagnostics (RAM, disk...). there are programs that will do it in Widnows. there are also some linux programs available for that.

> 
3. As for the nvidia driver, I do not know what to do really. I would like to use this laptop mostly for Kodi and for this I need the nVidia GPU to work.

I have no idea what is PPA. 

when opening additional drivers application it should offer you to install the nvidia drivers. if not then see my link on installing drivers via command line as well as the link regarding bumblebee.

PPA is personal package archive - it's is basically a repository that is packaged by someone other than Cannonical (the makers of Ubuntu). it can be made by an individual or a company. If you add it to your software sources, the software PPA was made for will appear in software center. it will also update along with other software updates.

---

### Post by gil80 on 2017-03-30
> **mastablasta said:**
> it should, it does.

and just like windows it has no problem working if the hardware is supported by manufacturers. in other words, try to install Windows on a Mac and see what happens.

in any case looking through threads from others it seem that while this model is not officially supported, the install will work. the only issue people had on this model was with optimus GPU switching, but even that was resolved (though a manual switch) in 2014/2015.


this should not happen. what does "fails" mean? an error message? blank screen?


this might have something to do with no. 1. or not. try installing using command line for example let's install htop (a nice small command line utility for monitoring system resources) - start up the terminal and enter:

```
sudo apt-get install htop
```
it will ask for a password. type in your user password and press enter (you won't see anything displayed while you type - a security feature )
it will then say how much space it will take, what things will be installed etc. and ask you to cofnirm the install. 
confirm with Y and enter
now it should either succesfully install the application or it will throw out an error. if there is an error mark the text, right click it and post it here using code tags (the # icon in advanced reply). if it is not working porpperly the only way we can know why and how to help is by seing the erorr that is presented. or to guess.

some good advice for troublehsooting is found in [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

if nothing else you can see how to check if OS identified hardware correctly.

finally if Windows had issues on PC as well it might be worth to run hardware diagnostics (RAM, disk...). there are programs that will do it in Widnows. there are also some linux programs available for that.



when opening additional drivers application it should offer you to install the nvidia drivers. if not then see my link on installing drivers via command line as well as the link regarding bumblebee.

PPA is personal package archive - it's is basically a repository that is packaged by someone other than Cannonical (the makers of Ubuntu). it can be made by an individual or a company. If you add it to your software sources, the software PPA was made for will appear in software center. it will also update along with other software updates.

1. I wasn't able to troubleshoot the 1st boot freeze. but this never happened again, so I let it be in the meantime.

2. As for installing .deb files. I saw a guide to install GDebi pacakge installer. I used this one. I then decided to install Chrome by using the default installer, and now it seems to be working. probably the command lines I've used to install GDebi Package Installer have fixes the problem when I install from Ubuntu Software.

3. I no longer get dependencies error messages when I try to install stuff using the 'sudo apt-get install {package-name}.

4. As for the nVidia GPU, when I go to the Software & Updates > Additional Drivers, I see the following:

* Using nvidia binary driver - version 375.39 from nvidia-375 (proprietary, tested)
* Using nvidia legacy binary driver - version 304.135 from nvidia-304 (proprietary)
* using nvidia binary driver - version 340.102 from nvidia-340 (proprietary)
* using x.org X server - nouveau display driver from xserver-xorg-video-nouveau (open source) <<-- Currently selected

unknown:unknown
using processos microcode firmware for the intel cpu's from intel-microcode. <<-- not selected

Which one should I choose? and should I manually take care to switch from intel GPU to Nvidia for power saving?

Thank you for the help so far!!!

---

### Post by mastablasta on 2017-03-30
> **gil80 said:**
> 
4. As for the nVidia GPU, when I go to the Software & Updates > Additional Drivers, I see the following:

* Using nvidia binary driver - version 375.39 from nvidia-375 (proprietary, tested)
* Using nvidia legacy binary driver - version 304.135 from nvidia-304 (proprietary)
* using nvidia binary driver - version 340.102 from nvidia-340 (proprietary)
* using x.org X server - nouveau display driver from xserver-xorg-video-nouveau (open source) <<-- Currently selected

Which one should I choose? 



try this one first:
*** Using nvidia binary driver - version 375.39 from nvidia-375 (proprietary, tested)**

> using processos microcode firmware for the intel cpu's from intel-microcode.

this is pacth for processor. might be good to install it but you can do it later on. here is a good explanation of what it is all about: [https://wiki.debian.org/Microcode](https://wiki.debian.org/Microcode)



>  and should I manually take care to switch from intel GPU to Nvidia for power saving?

after you install bumblebee (i do not have nvidia optimus, but i believe you are supposed ot do it after nvidia drivers install), you will be able to switch between GPU using optirun command. 

say you would want Kodi to use nvidia, you would use "optirun kodi" or something like that, eventhough i suspect intel GPU is good enough for decoding (watching) videos. i mean the RaspberryPi can handle it.

basically the bumblebee will default the GPU use to Intel GPU, but when you need nvidia for some extra power you can invoke it. unlike in windows where i believe this is then done automatically. again, i do not have optimus, just writing what i read. usage and install is better explained in the wiki page: [URL="https://wiki.ubuntu.com/Bumblebee"]https://wiki.ubuntu.com/Bumblebee
[/URL]
the reason why i am listing documentation rather than outright commnands is because when you use linux you are in full control of the PC and you decide it all. which can be overwhelming. but if you know what you want the end result to be, you will use the part of documentation that refers to it and it will (should) get you there.

---

### Post by oldfred on 2017-03-30
Some other Alienware threads:
 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr) 

      
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)

Are you installing in UEFI or BIOS boot mode?

---

