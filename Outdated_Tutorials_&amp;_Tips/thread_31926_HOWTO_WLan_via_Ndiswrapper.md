---
title: "HOWTO: WLan via Ndiswrapper"
date: 2005-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Hieronymus on 2005-05-05
On this forum I see there are a lot of questions about installing WIFI using ndiswrapper, I have figured it out and I want to share it with you all. I made a howto in which I have combined all the solutions I have found. This is the system I use:
 
HP Pavilion zv5133ea  
AMD64 3000+ met 512 Mb intern 
Nvidia GeForce4 440 Go 64M 
Broadcom 802.11b Wlan 
Realtek RTL8139 NIC 
Ubuntu Hoary Hedgedog 5.04 64Bit / WinXp dual boot 
 
HOWTO: 
The first problem I have encountered was that the ndiswrapper-1.1 version didn't work. My drivers were installed however the command iwlist did't show any APs, the solution I found was to install the newest version of ndiswrapper:[ Ndiswrapper-1.2-RC1 ]("http://sourceforge.net/projects/ndiswrapper/").

The next step is to get drivers, I'm working with 64 Bit Ubuntu so I need 64 Bit drivers, here is a link to get windows wlan drivers for most Wlan cards: [ Wlan drivers ]("http://www.linuxant.com/driverloader/drivers.php").  This link provides also 64 bit drivers for all broadcom cards. 

Ok, on to the installation:

Step 1: Remove the old ndiswrapper and all links to it's driver.
```
 			  
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper 

```       
 
Step 2: Install Linux-headers.
 
```
 		     
sudo apt-get install linux-headers-2.6.10 (enter your version of linux headers or usr the synaptic package manager)


```
 
Step 3: Install Ndiswrapper.
 
```
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /home/username/ndiswrapper-1.2-rc1/ 
sudo make 
sudo make install

```
  
Step 4: Load drivers with ndiswrapper.
 
```

cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i bcmwl5.inf (fill out your own drivers for bcmwl5.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

```
 
Step 5: Load ndiswrapper and check if it worked.
 
```

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```
 
Step 6: Make sure Ndiswrapper is loaded during bootup.
 
```

sudo ndiswrapper -m 

```
 
Step 7: Configure your Wlan card.
 
```
     
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
sudo ping -c 3 [www.ubuntu-linux.nl]("http://www.ubuntu-linux.nl/") (tests the connection) 


```
 
Step 8: If you are using WPA encryprion check this thread [ WPA encryption voor Ndiswrapper ]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa"). 
 
I hope this will help some people. If there are comments or extra info you have please add it to this thread, it could help somebody.

Greets Hieronymus

---

### Post by poofyhairguy on 2005-05-05
HEY MODS!!!

This needs to be moved!!!!

---

### Post by kassetra on 2005-05-09
[QUOTE=poofyhairguy]HEY MODS!!!

This needs to be moved!!!![/QUOTE]

moved.  :)

---

### Post by maspro on 2005-05-14
That's about the same procedure I used, it's funny how people sometimes unknowingly reinvent the wheel.  ;-) 
I have a laptop with a 64-bit AMD processor, but I used the 32-bit version of Ubuntu 5.04, with Ndiswrapper v1.1.  :smile: 

Here's what I came up after some research and posted in [another thread](http://www.ubuntuforums.org/showthread.php?t=25683) [here](http://www.ubuntuforums.org/showthread.php?t=25683) on the Ubuntu forums:

> **maspro] 
Well to get my Wif-fi working on my Acer Ferrari 3200 I did the following and it worked perfectly  :grin: :
Although I have a laptop with a 64-bit AMD processor, I used the Ubuntu 32-bit version for x86 systems, with the Ndiswrapper v1.1.

- First I plugged in the UTP cable to get internet access (since Wi-fi doesn't work yet   said:**
> http://ndiswrapper.sourceforge.net/[/url] 
- You will also need an appropriate .inf driver for your Wi-fi, I used bcmwl5.inf.
- If you can't find a suitable driver then take a look here: [http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)
- Then I downloaded **build-essential, linux-headers** and ndiswrapper utils through Synaptic. Although the ndiswrapper utils that are provided through Synaptic aren't really necessary I think because later on there are replaced by a newer version. 

Then I typed the following commands in a terminal-window:
[i]
sudo su <your own password> 
Copy the ndiswrappersource tar file to /usr/src
cd /usr/src
tar xvzf ndiswrapper*
cd ndiswrapper*
debian/rules binary
cd ..
dpkg -i ndiswrapper*.deb
Switch to your driver's directory with the cd command.
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
modprobe ndiswrapper
iwconfig
iwconfig wlan0 essid <fill in your own essid>
iwlist wlan0 scan
iwconfig wlan0 mode Managed
iwconfig wlan0 key restricted <your own wep-key 10 hex digits for 40-bit  encryption or 26 hex digits for 128-bit encryption>
iwconfig wlan0 essid <fill in your own essid>
ifconfig wlan0 up (or dhclient wlan0)
[/i][i]
- I then disabled my eth0 (the port with the UTP cable) in the Gnome GUI network utility. 
- Then use the Gnome GUI network utility to configure your wireless interface.
- Optionally you can download the KWifimanager through Synaptic and also make some configurations there, it also allows you to see if you have any signal strength and if you get an IP-address on your Wi-fi nic.
[/i]
When all works well I typed the following last command:

*ndiswrapper -m*
 
And I added the following line to my /etc/modules: *ndiswrapper*

Maybe there is some redundant stuff that I did in the above list, but it's works perfectly for me. 
So I guess that there are several ways to get your Wi-fi working in Ubuntu!  :razz:

Looks very similar, doesn't it...  :)

---

### Post by jonny on 2005-05-14
Hieronymus, maspro

You've probably seen the [How To](http://ubuntuforums.org/showthread.php?t=25683) that I wrote for Broadcom cards (I managed to get the repository ndiswrapper to work), and I imagine it didn't work for you.  I'd like to point my How To to yours so that users who have similar problems aren't left high and dry.  You mention AMD64.  Are you using AMD64 ubuntu?  If so, I imagine that these are the users that need redirection.

The other thread has had around 7,000 hits so far, so Broadcom cards are obviously presenting huge problems.  It would be good to be able to present a cast iron solution set between us.

One minor point that might trip up some unwary noobs: I think that, from a fresh ubuntu install, you'd also need to do apt-get install build-essential before compiling ndiswrapper.

---

### Post by maspro on 2005-05-14
[QUOTE=jonny]Hieronymus, maspro

You've probably seen the [How To](http://ubuntuforums.org/showthread.php?t=25683) that I wrote for Broadcom cards (I managed to get the repository ndiswrapper to work), and I imagine it didn't work for you.  I'd like to point my How To to yours so that users who have similar problems aren't left high and dry.  You mention AMD64.  Are you using AMD64 ubuntu?  If so, I imagine that these are the users that need redirection.

The other thread has had around 7,000 hits so far, so Broadcom cards are obviously presenting huge problems.  It would be good to be able to present a cast iron solution set between us.

One minor point that might trip up some unwary noobs: I think that, from a fresh ubuntu install, you'd also need to do apt-get install build-essential before compiling ndiswrapper.[/QUOTE]
Will I cross-linked this thread with your thread at [HOW TO: Configure wireless cards with Broadcom chipsets](http://ubuntuforums.org/showthread.php?t=25683) The more info the better!  :smile: 

It's my understanding that Hieronymus uses Ubuntu 64-bit on a AMD64-bit, I'm using Ubuntu 32-bit on a AMD64-bit. And in both situations we were able to get Wi-fi working. Hieronymus used the Ndiswrapper v1.2RC1 and I used the Ndiswrapper v1.1 final. 

And indeed the **build-essential** that's available through APT is indeed necessary for a successfull end result. I think with your how-to and the how-to of Hieronymus that it should not be a huge problem anymore to get Wi-fi working for most people.  :grin:

---

### Post by Fuzzhead on 2005-05-17
I'm a newbie, and this is probably a dumb question, but I'll ask anyways.

In step #2, the command to get the linux headers. 
sudo apt-get install linux-headers-2.6.10 

Does this pull out of local files, or does it have to pull from an online repository?
How can I go online, if what I need to get online is retreived by going online?

TIA,
Michael

---

### Post by maspro on 2005-05-18
[QUOTE=Fuzzhead]I'm a newbie, and this is probably a dumb question, but I'll ask anyways.

In step #2, the command to get the linux headers. 
sudo apt-get install linux-headers-2.6.10 

Does this pull out of local files, or does it have to pull from an online repository?
How can I go online, if what I need to get online is retreived by going online?

TIA,
Michael[/QUOTE]
Well most people who want to install wireless internet already have a internet connection in one form or the other. I simply plugged-out the network cable of my other computer and plugged it in to my laptop to get a internet connnection. From there on I fixed the wireless connection and them plugged-out the network cable from my laptop and put it back in my primary computer again.

But I think it's possible to get apt/synaptic to work with local repositories on your harddrive. I don't know if the  linux-headers are on the install-cd of Ubuntu, maybe you can get them from the cd. But I'm a n00b also, so I don't know for sure.  ;-)

---

### Post by Fuzzhead on 2005-05-18
[QUOTE=maspro]Well most people who want to install wireless internet already have a internet connection in one form or the other. I simply plugged-out the network cable of my other computer and plugged it in to my laptop to get a internet connnection. From there on I fixed the wireless connection and them plugged-out the network cable from my laptop and put it back in my primary computer again.

But I think it's possible to get apt/synaptic to work with local repositories on your harddrive. I don't know if the  linux-headers are on the install-cd of Ubuntu, maybe you can get them fron the cd. But I'm a n00b also, so I don't know for sure.  ;-)[/QUOTE]
 I booted into windows, and downloaded the  linux-headers-2.6.10 file, a .deb  file. I have that on the main HDD, and I can get to it after booting the LiveCD and mounting the drive.  But, what is the command to install the  linux-headers-xxx.x.x..deb file?  (NOTE: This particular machine must run on the wireless, as it sits on the second floor, and my cable router/ap is in the basement.)   Thanks! :)

---

### Post by Heliode on 2005-05-18
To manually install .deb files:

```

dpkg -i [file]

```

---

### Post by maspro on 2005-05-18
You will also need the "build-essential" deb file which is also available through APT.

I don't know al the commands because I installed in through Synaptic, this a is graphical front-end for APT that automatically installs the software including all of it's dependencies without ever typing one single command.  :) 

Since your a newcomer yourself it would be far more easier to take your laptop to the basement and plugin a network cable from your router to your laptop (be sure that the router works with DHCP) then install/run Ubuntu and then install al of the necessary software through Synaptic. 

I asume that you read this whole thread and not just the beginning of the thread.  :)

Also a VERY usefull guide about Ubuntu: [http://ubuntuguide.org/](http://ubuntuguide.org/)
Has lot's of usefull information that might come in handy!

---

### Post by Fuzzhead on 2005-05-19
Thanks for the replies...
Three things:  
"... including all of it's dependencies ..."   makes me think that simply installing one package may not be sufficient.  Does the installation of .deb files kick out error messages if dependencies are not available?

second thing:  unfortunately the system on the second floor  is NOT a laptop, but desktop.  I don't want to move the system, either temporarilly for installs,
or permanently.  

Lastly, that same system has an LCD monitor, and although this has not
been a problem with Ubuntu, it doesn't handle some distros...

-Michael

---

### Post by maspro on 2005-05-19
> **Fuzzhead]Thanks for the replies...
Three things:  
"... including all of it's dependencies ..."   makes me think that simply installing one package may not be sufficient.  Does the installation of .deb files kick out error messages if dependencies are not available?[/QUOTE]You're absolutely correct about this. Installing one piece of software often needs some other piece of software, in turn this other piece of software may also need  some another piece of software. All of the needed software to install the main software you wish to use are called dependencies. This does not only apply to Ubuntu, but is true for Linux in general. If dependencies are not correct or not available you will see errors and messages that certain things went wrong and will not work.  And that's why APT/Synaptic is really cool, because it's solve all dependencies automatically. 

[QUOTE=Fuzzhead]
second thing:  unfortunately the system on the second floor  is NOT a laptop, but desktop.  I don't want to move the system, either temporarilly for installs,
or permanently.[/QUOTE]Oke that's clear. Maybe a really long network cable you can use temporary?   said:**
> 
Lastly, that same system has an LCD monitor, and although this has not
been a problem with Ubuntu, it doesn't handle some distros...Can't help you there, hardware support is not always the same in different linux distro's, if there isn't a (open-source) driver available, then it's trial and error and just see what works for you.

---

### Post by maspro on 2005-05-19
@Fuzzhead:

The following software is absolutely essential for a successful install:

- ndiswrapper-source v1.1 or v1.2RC1 (NOT the deb file) [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) 
- appropriate .inf driver for your Wi-fi ([http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List))
- build-essential (available through APT)
- linux-headers for you specific kernel (available through APT)

Maybe you can browse the FTP repositories of Ubuntu from you computer which has an internet connection and download the build-essential and linux-headers manually. As far as I can tell you only need to download the above software and first install build-essential, then the linux-headers and then the ndiswrapperwrapper source. If you do this in this order then dependencies should not be a problem. (At least I hope so  ;-) )

---

### Post by Fuzzhead on 2005-05-19
Thanks again for your help. It really is great to get such detailed, and personalized feedback/instruction.  I'll boot into Windows, download those apps/packages, then boot to LiveCD and follow your suggested steps.  Stayed tuned!   

I'm just starting down the path of exploring Linux distros to see what's out there, how they work, how they differ, etc.  I imagine taking several months to learn enough to move the house to a Linux environment, although I think I'll need at least one dual boot system as we have some very specific Windows based apps that aren't available on Linux.

=8^)
Fuzzhead

---

### Post by maspro on 2005-05-19
Myself I tried Suse, Mandrake, Linspire, Xandros, Mepis, Kubuntu, Ubuntu and a really long time ago Redhat and Slackware.

They all have there own cool stuff and they all have there downsides, but one thing is for sure APT-GET really rocks, all Debian based systems, like Linspire, Xandros, Mepis, Kubuntu, Ubuntu, etc.  have the ability to use APT-GET, while the RPM based systems such as Mandriva, Suse, Fedora, etc. have there own way to solve dependencies, such as URPMI, YAST and YUM. 

But in all the distro's i've tried none of them had a working Wifi internet connection from the start! And the Ubuntu approach to get Wifi working is different then if you were to use Mandriva (formerly Mandrake).

---

### Post by kleeman on 2005-05-19
Yeah thanks a lot for this Howto, worked well for me! I had a d-link g650 for which the madwifi driver with Ubuntu Hoary didn't work. The plans for wireless support in Breezy sound absolutely fabulous.....

[http://udu.wiki.ubuntu.com/LaptopMission](http://udu.wiki.ubuntu.com/LaptopMission)

---

### Post by Fuzzhead on 2005-05-19
[QUOTE=maspro]@Fuzzhead:

The following software is absolutely essential for a successful install:

- ndiswrapper-source v1.1 or v1.2RC1 (NOT the deb file) [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) 
- appropriate .inf driver for your Wi-fi ([http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List))
- build-essential (available through APT)
- linux-headers for you specific kernel (available through APT)

Maybe you can browse the FTP repositories of Ubuntu from you computer which has an internet connection and download the build-essential and linux-headers manually. As far as I can tell you only need to download the above software and first install build-essential, then the linux-headers and then the ndiswrapperwrapper source. If you do this in this order then dependencies should not be a problem. (At least I hope so  ;-) )[/QUOTE]
 Next question, I should have guessed earlier to ask it, is where are the files that Synaptic Package Manager downloads?   

Should I just copy the entire  /usr/share/ directory onto my HDD ?  (Shot gun approach?)

I need to know both the build-essentials, and Linux Headers for 2.6.10.5 - 386

Is there a way to copy the list of files from this file "essential-packages-list" ?
base-files
base-passwd
bash
bsdutils
coreutils
debianutils
diff
dpkg
e2fsprogs
findutils
grep
gzip
hostname
login
mount
ncurses-base
ncurses-bin
perl-base
sed
sysvinit
tar
util-linux

BTW, this is a LiveCD running on my Server hardware, in the basement with wired connection. Boot up was great! Quick and easy, YEAH!!!! Good Job Ubuntu developers!!    

Thanks,
Michael
aka  Fuzzhead   =8^)

---

### Post by maspro on 2005-05-20
For the build-essential I would recommend to download the Ubuntu add-on cd, which you can find here: [http://ubuntuguide.org/add-on-cd/](http://ubuntuguide.org/add-on-cd/)  this is the easiest way and also you will have all kinds of multimedia appz and codecs. 

Both the build-essential and the linux-headers are available in one of the following repositories, I don't know where exactly:
 
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) 
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) 

[quote=Fuzzhead]Should I just copy the entire /usr/share/ directory onto my HDD ?[/quote] I don't know that one, I'm to much of a n00b for that.  ;-) 

Good luck!

---

### Post by Fuzzhead on 2005-05-21
[QUOTE=maspro]For the build-essential I would recommend to download the Ubuntu add-on cd, which you can find here: [http://ubuntuguide.org/add-on-cd/](http://ubuntuguide.org/add-on-cd/)  this is the easiest way and also you will have all kinds of multimedia appz and codecs. 

Both the build-essential and the linux-headers are available in one of the following repositories, I don't know where exactly:
 
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) 
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) 

 I don't know that one, I'm to much of a n00b for that.  ;-) 

Good luck![/QUOTE]
 I have acquire the files I think I need:
Add On CD, and installed it, seemed to work ok
For the Headers, I went with i386, rather than AMD64. (my other machine is an intel..so seemed to make sense to reuse the same build, seemed to work)

I have this header file,    linux-headers-2.6.10-5_2.6.10-34_i386.deb
but need command syntax to install it.
I tried:    "sudo install linux-headers-2.6.10-5_2.6.10-34_i386.deb"  but get an error 
saying too few parameters. I read the help, but it didn't make sense. Do you happen
to know what the correct args would be,and correct directory? 

Thanks,
Michael

---

### Post by Fuzzhead on 2005-05-21
[QUOTE=maspro]For the build-essential I would recommend to download the Ubuntu add-on cd, which you can find here: [http://ubuntuguide.org/add-on-cd/](http://ubuntuguide.org/add-on-cd/)  this is the easiest way and also you will have all kinds of multimedia appz and codecs. 

Both the build-essential and the linux-headers are available in one of the following repositories, I don't know where exactly:
 
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) 
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) 

 I don't know that one, I'm to much of a n00b for that.  ;-) 

Good luck![/QUOTE]
 Related question... I will be using a USB storage device to save my files, packages, and settings.. I should like to reboot with LiveCD and load these up.  My HDD is NTFS, so can't write to it, correct?  How do I find the path to the USB device. BTW it shows up automatically on the Desktop when I plug it in... and I can read/write to .Very nice.. thanks

---

### Post by maspro on 2005-05-21
[QUOTE=Fuzzhead]I have acquire the files I think I need:
Add On CD, and installed it, seemed to work ok
For the Headers, I went with i386, rather than AMD64. (my other machine is an intel..so seemed to make sense to reuse the same build, seemed to work)

I have this header file,    linux-headers-2.6.10-5_2.6.10-34_i386.deb
but need command syntax to install it.
I tried:    "sudo install linux-headers-2.6.10-5_2.6.10-34_i386.deb"  but get an error 
saying too few parameters. I read the help, but it didn't make sense. Do you happen
to know what the correct args would be,and correct directory? 

Thanks,
Michael[/QUOTE]
You say that you have a AMD64, but you run the 32bit version of Ubuntu? If so then I think you should have one of the following header files:

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5_2.6.10-34_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5_2.6.10-34_i386.deb)

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5-686_2.6.10-34_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5-686_2.6.10-34_i386.deb)

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5-386_2.6.10-34_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5-386_2.6.10-34_i386.deb)


And I think that you should install it this way:
*sudo dpkg -i yourpackagename.deb*

It seems that you can also use APT-GET locally without an internet connection, check the following link to see how this is done:
[Click for link here](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)

Normally if you would have an internet connection you would type the following to use APT-GET  online:
*sudo apt-get install yourpackagename*

for example: 
*sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10*

[quote=Fuzzhead]Related question... I will be using a USB storage device to save my files, packages, and settings.. I should like to reboot with LiveCD and load these up. My HDD is NTFS, so can't write to it, correct? How do I find the path to the USB device. BTW it shows up automatically on the Desktop when I plug it in... and I can read/write to .Very nice.. thanks[/quote]
Normally you can only read on NTFS partitions under linux, but read/write access seems to be possible with certain risks:

check the following links:
[http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)
[http://freshmeat.net/projects/linuxntfs/](http://freshmeat.net/projects/linuxntfs/)
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

About that USB device, can't you simply right-click on that device and see where it points to, for example /media/ or /dev/ or something?

---

### Post by cow_racer on 2005-05-21
I am getting this error.  What is wrong?

sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by cow_racer on 2005-05-21
I solve the above problem, now have a new problem.

sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

---

### Post by Vin_L on 2005-05-21
I am very new to linux and I hope some one can help. I have been trying to install the latest WG311v2 driver and after installin the latest ndiswrapper and then attempting to install the driver this is what I get

root@Main:/home/vin/WG311 # ndiswrapper -i wg311v2.inf
wg311v2 is already installed. Use -e to remove it

Then when I use the -e command I get

root@Main:/home/vin/WG311 # ndiswrapper -e wg311v2.inf
Driver wg311v2.inf is not installed. Use -l to list installed drivers

Then when I use -l I get 

root@Main:/home/vin/WG311 # ndiswrapper -l
Installed ndis drivers:
wg311v2 invalid driver!

It seems I have an invalid driver.

1. Am I looking in the right place? (//Home/vin/WG311 is where the new driver inf, sys and bin files reside)
2. If I am looking in the right place how do I remove the invalid driver.

Thanks very much I appreciate any help I can get.

---

### Post by stevenyu on 2005-05-21
Please read page 2 for my complete soultion on how toget wg311v2 working with ndiswrapper in Ubuntu or you can refer to this page if you want - [http://ubuntuforums.org/showthread.php?p=181293#post181293](http://ubuntuforums.org/showthread.php?p=181293#post181293)

---

### Post by kleeman on 2005-05-21
Couple of questions on ndiswrapper:

I got a d-link G650 (madwifi doesn't work) working following the instructions here (thanks a bunch!!!) but a
couple of wierd things happen:

1) If I try to change the channel using 
iwconfig wlan0 channel NUMBER
then it gives an error message. On the other hand

iwconfig wlan0 essid MYNAME
works fine so I'm thinking it is an ndiswrapper driver issue

2) I get a continual error message saying that the driver expects wireless extensions version 18 but that it (ndiswrapper?) was compiled with version 17 and that therefore some driver functions may not work (see 1)????)

Any ideas how to fix 1) and do I need to recompile ndiswrapper because of 2)??

I am able to reset the channel by 

sudo rmmod ndiswrapper
sudo modprobe ndiswapper

and it (wlan0) appears to come up with the right parameters for the nearest open network which I can then connect to but this seems pretty clunky...

---

### Post by maspro on 2005-05-22
For al the people that are having driver problems or who aren't sure if they have a correct Wifi driver, please check the following site, here you can find a list of compatible Wifi drivers for different laptop configurations. Note that NOT all drivers are compatible with all laptops, including your original driver on your installation cd-rom: 
*[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)*

Here's the Wiki site on Sourceforge about the ndiswrapper:
*[http://ndiswrapper.sourceforge.net/phpwiki/index.php/](http://ndiswrapper.sourceforge.net/phpwiki/index.php/)*

Here's how to correctly install ndiswrapper with the correct Windows driver:
*[http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)*

Here's how to uninstall the ndiswrapper and start over again:
*[http://ndiswrapper.sourceforge.net/phpwiki/index.php/Uninstall](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Uninstall)*

Also it's very important to do the installation of ndiswrapper with **root or sudo privileges** and that NO previous versions or installations of ndiswrapper are on your system! Also make sure that you have the **build-essential** and **linux-headers installed** before you begin with the installation of ndiswrapper!

**IMPORTANT:**
"Do NOT use drivers from your CD. They may work, but you may experience kernel crashes etc., if the driver on your CD has not been tested.

Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry List. To identify the driver that you need, first identify the card you have with "lspci" and note the first  column (such as 0000:00:0c.0) and then find out the PCI ID of the card that with "lspci -n"  corresponding to the first column of "lspci" output.

The PCI ID is third column (or fourth in some distributions) and of the form "104c:8400".  Now you need to get the Windows driver for this chipset. In the list of drivers, find out an  entry for the same PCI ID and download the driver corresponding to it.

Unpack the Windows driver with unzip/cabextract/unshield tools and find out the INF file (i.e., file  with .INF or .inf extension) and SYS file (i.e., file with .SYS or .sys extension).  If there are multiple INF/SYS files, you may look in the List if there are any hints about which of  them should be used. Make sure the INF file, SYS file and any BIN files (for example, TI drivers use  BIN firmware files) are all in one directory. Now use "ndiswrapper" tool to install the driver with ndiswrapper -i filename.inf"

[SIZE=1]quote from [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)[/SIZE]

---

### Post by kleeman on 2005-05-23
Thanks for the detailed instructions maspro. I checked out my installation of ndiswrapper (particularly the pci id) and everything seems fine. I read on the ndiswrapper site that certain options for iwconfig often do not work (and are not needed). Do you happen to know whether if you set essid with iwconfig then the channel (or frequency band) is also automatically adjusted? Also my iwconfig comes up automatically with the nearest default network (with the correct channel). Is this what one should expect on the road while roaming around? Thanks in advance for any tips on this.....

---

### Post by maspro on 2005-05-23
[QUOTE=kleeman]Thanks for the detailed instructions maspro. I checked out my installation of ndiswrapper (particularly the pci id) and everything seems fine. I read on the ndiswrapper site that certain options for iwconfig often do not work (and are not needed). Do you happen to know whether if you set essid with iwconfig then the channel (or frequency band) is also automatically adjusted? Also my iwconfig comes up automatically with the nearest default network (with the correct channel). Is this what one should expect on the road while roaming around? Thanks in advance for any tips on this.....[/QUOTE]
I don't exactly know the answer to your question, maybe the following text from the sourceforge site can help you:

[i]"How can I set bit rate? You don't need to set bit rate; if you associate with a node (by setting essid), the card will automatically switch to best possible rate. However, if you want to use specific network type (such as a/b/g), use "iwpriv wlan0 network_type <char>" to set the network type to what <char> represents, where <char> is one of a, b, g or any other characther. For example, to set to 802.11b, use "iwpriv wlan0 network_type b", and to set to auto, "iwpriv wlan0 network_type x". Most drivers allow changing the mode before associating only - once associated, mode can't be changed.

You can also specify a specific rate by changing appropriate setting in the .conf files in /etc/ndiswrapper/<driver> directory. What setting to change to what value depends on particular driver. See the .inf file for some hints (and sometimes some explanation) about what settings to change to what values. Once you change these values (you may need to change the settings in more than one file depending on the PCI id), reload ndiswrapper."[/i]

[size=1]quote from [http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ)[/size]

---

### Post by Fuzzhead on 2005-05-27
> **maspro]I don't exactly know the answer to your question, maybe the following text from the sourceforge site can help you:

[i]"How can I set bit rate? You don't need to set bit rate said:**
> 

[size=1]quote from [http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ)[/size]
 Is it possible for someone with Linux experience, to build a package/object for a given set of wlan drivers & Ubuntu distribution, and then post a link to it?  It seems like this is possible, correct?

---

### Post by maspro on 2005-05-27
[QUOTE=Fuzzhead]Is it possible for someone with Linux experience, to build a package/object for a given set of wlan drivers & Ubuntu distribution, and then post a link to it?  It seems like this is possible, correct?[/QUOTE]
Sure this is possible, if all of the necessary software and the correct driver is available, then a package could be build. This package could also be made that it auto-installs itself with one command. 

But I don't have the experience to do this, but for someone with more experience building such a package should not be to much work. 

Is you Wifi working now?

---

### Post by Fuzzhead on 2005-05-27
Not with Ubuntu, but I have been able to use WiFi card with the DSL distribution, which works very well on my old laptop (233mhz, 64MB RAM).   My goal is to use the LiveCD version of Ubuntu on my desktop, and then save apps/data/config etc.... onto a USB flash drive.  Once I'm confident enough with this Ubuntu distribution and Linux in general, I may move to a dual boot machine.  

Do you know of anyone who may have the experience and desire to build such a package for Ubuntu distribution?  Do you know if Ubuntu developers would respond to such a request?  

Thanks maspro for your quick and savvy replies!
Fuzzhead
=8^)

---

### Post by maspro on 2005-05-27
No i don't know anyone who can do that, all my friends are Windows users.  ;-) 

If you've followed this guide precisely and read the whole thread and it's still not working then changes are that you are using a incorrect or faulty Wifi driver. 

When I first installed Wifi on Mandriva it took me quite some time to get it working correctly, then when I installed Ubuntu it again took me some time to get Wifi working, but the funny part is that the driver I used in Mandriva didn't work in Ubuntu and the driver I used in Ubuntu didn't work in Mandriva. In both cases I used the 32-bit distribution, but I needed two different drivers to get the same Wifi card working in two different distributions.  :-?  

So I would take a look at this site for a correct driver: [http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)

And take a look at the text below to correctly determine which driver is correct for your Wifi card:

---------------------------------
"Do NOT use drivers from your CD. They may work, but you may experience kernel crashes etc., if the driver on your CD has not been tested.

Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry List. To identify the driver that you need, first identify the card you have with "lspci" and note the first column (such as 0000:00:0c.0) and then find out the PCI ID of the card that with "lspci -n" corresponding to the first column of "lspci" output.

The PCI ID is third column (or fourth in some distributions) and of the form "104c:8400". Now you need to get the Windows driver for this chipset. In the list of drivers, find out an entry for the same PCI ID and download the driver corresponding to it.

Unpack the Windows driver with unzip/cabextract/unshield tools and find out the INF file (i.e., file with .INF or .inf extension) and SYS file (i.e., file with .SYS or .sys extension). If there are multiple INF/SYS files, you may look in the List if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files (for example, TI drivers use BIN firmware files) are all in one directory. Now use "ndiswrapper" tool to install the driver with ndiswrapper -i filename.inf"
---------------------------------

---

### Post by simianMiscreant on 2005-06-07
```
brady@theReal:~/Desktop$ sudo ndiswrapper -l
Installed ndis drivers:
rt2500usb       invalid driver!
wusb54g_20040903.exe    invalid driver!
``` 

```
brady@theReal:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
``` 

???

---

### Post by minimidgy on 2005-06-07
The first time I tried installing wlan on my broadcom wireless card, I installed ndiswrapper just fine.  I had to look around a little bit to find the cd that had all of my drivers on it. That wasn't too bad.  But when I got to the part where the computer has to recognize your wireless connection, that took me forever to figure out.  It just wouldn't show up in my network settings window.

I'm sure this HOWTO will help many people.  Hopefully they have another computer with the internet working so they can print this off.

---

### Post by clarke.rainey on 2005-06-10
For some reason I cannot get it to recognize my wireless after I get it working on the next bootup... what can I do to make it do so automatically?..

---

### Post by makisupa123 on 2005-06-10
clarke.rainey, 
> For some reason I cannot get it to recognize my wireless after I get it working on the next bootup... what can I do to make it do so automatically?..

I had the same problem.  Unfortunately, my solution is less than ideal.  Are you using a laptop with a PCMCIA card?  I have to unseat the card every time i reboot because the os doesn't properly shut down the service (the card still has power).  Basically, ndiswrapper has the ability start the card but not restart it, or use it from a started state.  Interestingly, if I try to hibernate (which fails) ubuntu does power down the card.  If someone could tell me how to get this to happen (pcmcia power down) when rebooting i would be grateful.

Thanks,
Mak.

---

### Post by borys on 2005-07-16
Ok.. i was doing all ok:

root@borys:/home/borys/driverto/DRIVERS/WinXP # ndiswrapper -l
Installed ndis drivers:
wluax1  driver present
wluax2  driver present, hardware present

 i was starting to get exited about it!, but however.. i got this :@

root@borys:/home/borys/driverto/DRIVERS/WinXP # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


Please please HELP!!!!!!!!!!!

---

### Post by stevenyu on 2005-07-16
sudo modprobe ndiswrapper

---

### Post by maspro on 2005-07-17
It sometimes absolutely amazes me how poorly some people read threads like this one. People keep asking questions that are already answered somewhere earlier in this thread. It sometimes seems that people only read the topic title and the opening post and then immediately start asking questions, instead of reading the whole thread!  :roll: 

For the people that did read the whole thread and are still asking questions that are already answered, it's important to tell us what you already tried in a detailed way, so you may get answers that aren't already given in this thread!  ;-) 

Sometimes the same answer is given several times in the same thread, that's a bit redundant don't you think!  :-?

---

### Post by Sephiriz on 2005-07-17
Hey, I have a slight problem, though it doesn't keep me from using the internet:

```

iwconfig  Wireless-Tools version 27
          Compatible with Wireless Extension v11 to v17.

Kernel    Currently compiled with Wireless Extension v17.

wlan0     Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v17.


```

Thats what I get when I do a quick iwconfig --version.

Now, is there a way to upgrade this to Wireless Extension v18 by using a newer Wireless-Tools version?  Are there any guides on this?  I'm a relatively inexperienced Linux user, so any help is appreciated.

---

### Post by borys on 2005-07-21
[QUOTE=maspro]It sometimes absolutely amazes me how poorly some people read threads like this one. People keep asking questions that are already answered somewhere earlier in this thread. It sometimes seems that people only read the topic title and the opening post and then immediately start asking questions, instead of reading the whole thread!  :roll: 

For the people that did read the whole thread and are still asking questions that are already answered, it's important to tell us what you already tried in a detailed way, so you may get answers that aren't already given in this thread!  ;-) 

Sometimes the same answer is given several times in the same thread, that's a bit redundant don't you think!  :-?[/QUOTE]

ok.. i would like you to read carefuly the thread cause im not asking questions already answered, im in the nbext step i already did a modprobe.. so, why dont you read my post and talk later?, aldo it didnt help me im very thankful to stevenyu and this community in general for trying to help.. Thanks..

---

### Post by juhanfg on 2005-07-29
[QUOTE=cow_racer]I am getting this error.  What is wrong?

sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted[/QUOTE]


How did you solve it? I'm having exactly the same problem and i have no idea what to do.

Thanks

Juan

---

### Post by b4k4 on 2005-07-31
> root@ubuntu:~ # ndiswrapper -l
Installed ndis drivers:
w29n51  driver present, hardware present
root@ubuntu:~ # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


Thanks for all the help in this thread. Does someone know how to fix this error?

---

### Post by raydr on 2005-07-31
I'm getting the same error as the last two posters (exactly).

I've tried everything in this thread (and others) at least 5 times.

Ubuntu has been updated.
Newest version of ndiswrapper.
Latest drivers.

I'm on an HP zd8000 laptop.

> 
root@mmatos-ub:/home/mmatos # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
root@mmatos-ub:/home/mmatos # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


Any help would be GREATLY appreciated.

---

### Post by raydr on 2005-07-31
[http://ubuntuforums.org/showthread.php?p=280593#post280593](http://ubuntuforums.org/showthread.php?p=280593#post280593)

This thread has a note about not using an SMP kernel.

I'm awaiting a confirmation...as that may be my problem??

---

### Post by timelord726 on 2005-08-01
Another victim of the same exact problem.

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by b4k4 on 2005-08-02
success!
I downloaded the source again from sourceforge, and this time through it worked.

I had a problem with the interface name. wlan0 gave errors. eth1 turned out to be the name that worked.

Question: How can I get the wireless connection to connect and authenticate automatically? I have to do system/admin/networking which involves entering the password. These laptops are for classroom use with generic auto-logins. Since everything is sudoed in ubuntu, I was hoping to keep the passwords secret and not have kids run any sudo commands.

thanks a lot

---

### Post by Thornsten on 2005-08-02
Okey dokey, I greatly appreciate this howto for sure.  I have a unique (I think...) problem that's not crippling, but annoying.

Everything's working fine, I used System/Administration/Networking to set up wlan0 and de-configure eth0.  wlan0 is using DHCP to get an IP.  It works great.  Until I reboot.  iwconfig shows the interface, but the essid is set to Any.  If I go back in to System/Administration/Networking, click wlan0 and click Properties, then just click Ok until the Networking utility is closed, then it's working again.

Any idears?

---

### Post by Thornsten on 2005-08-02
Heh, figured it out.  Originally I had a script I wrote that I executed via rc2.d to set up my wlan0.  I had to add a sleep 2s after the ifconfig wlan0 up to allow ndiswrapper to load before the rest of the configuration steps ran.  Apparantly when I changed to using Ubuntu's built-in network configuration tool the same problem was occuring.  ndiswrapper wasn't being loaded until the network interfaces were loaded and the rest of the configuration was happening before the driver was fully loaded.

I added ndiswrapper to the /etc/modules so that it's loaded before the network configuration takes place and that fixed it.

---

### Post by ubuntuguy on 2005-08-03
[QUOTE=timelord726]Another victim of the same exact problem.[/QUOTE]

Me too. modprobe ndiswrapper will not insert the module, complaining a fatal error.

How was this problem solved? I read the whole thread, I've even tried recompiling the kernel so the kernel and the module would have been produced by the same compiler version, with no success. Someone please write a how-to to get around this problem.

---

### Post by shthap3ns on 2005-08-03
Hey all,

Newb here.

I'm getting an odd error when I enter the "sudo modprobe ndiswrapper" code. It completely freezes my system...mouse stops working, everything. All I can do is do a hard reboot. I followed the instructions to the letter, I installed the build essentials, linux headers, and then installed ndivwrapper-1.2. Everything went well, but when I type the modprobe command it just freezes my computer. Device manager says my card is a Broadcom BCM4306 - 802.11b+g Wireless card. I downloaded the drivers from Linuxant and used bcmwl5.inf....

Any suggestions?

BTW, I'm on a HP Pavilion ze9805 laptop, with Windows XP and Ubuntu on dual-boot. The wireless card works fine in Windows XP.

---

### Post by Jeffj on 2005-08-03
I wasn't sure which inf file I needed. I have a 7510GX gateway with an AMD64 chip.
The sticker on the bottom says fcc id is BRCM1016.
I found two different files named bcmwl5.inf
I used one of them and it seems to work. Is there a way to get a look at the difference? I think one is for NT and the other for Windows.
Is that the one for the 64 bit version of ubuntu? It seems to work.
I can't seem to get rid of the netbc564 driver I accidently installed earlier.

root@ubuntu:/home/jjm/80211g/80211g # ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
netbc564        driver present
root@ubuntu:/home/jjm/80211g/80211g #

---

### Post by Jeffj on 2005-08-04
just to help me find it.

---

### Post by grayskies on 2005-08-08
```
root@hp:~/Desktop/ndiswrapper-1.2.tar.gz_FILES/ndiswrapper-1.2# sudo make install
make -C driver install
make[1]: Entering directory `/home/adam/Desktop/ndiswrapper-1.2.tar.gz_FILES/ndiswrapper-1.2/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-amd64-k8/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/adam/Desktop/ndiswrapper-1.2.tar.gz_FILES/ndiswrapper-1.2/driver'
make: *** [install] Error 2
[email]root@hp:~/Desktop/ndiswrapper-1.2.tar.gz[/email]_FILES/ndiswrapper-1.2#
``` 

any ideas on why this is happening?

---

### Post by duminas on 2005-08-09
I'm not too familiar with the 64-bit side of things, but have you installed the **linux-headers** package that your version needs?

If not, try doing this at the terminal (this assumes you have ethernet or something available):
```
sudo apt-get install linux-headers-`uname -r`
```and see if that helps any. If this fails, you can always look up the package(s) you'll need [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=hoary&release=all). The output from```
uname -r
```may be pertinent, so if the apt-get fails, run the above command and make note of what it gives you.

---

### Post by ubuntuguy on 2005-08-18
If you get a Fatal error when trying to modprobe ndiswrapper, try using ndiswrapper version 1.1, not version 1.2. This worked for me.

I do hope ndiswrapper support is better for Breezy Badger than it is with Hoary Hedgehog.

---

### Post by jamesrw on 2005-08-20
not working for me.. dunno whats wrong, ive tired a few versions of ndiswrapper a few times :(

ndiswrapper (check_nt_hdr:162): Windows driver is not 32-bit; bad magic: 020B
ndiswrapper (load_sys_files:481): unable to prepare driver 'bcmwl5'
ndiswrapper (ndiswrapper_load_driver:93): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'

---

### Post by jamesrw on 2005-08-20
works after using the driver from my windows partition.... what windows good for something??

---

### Post by lonetree on 2005-08-24
[QUOTE=Thornsten]Heh, figured it out.  Originally I had a script I wrote that I executed via rc2.d to set up my wlan0.  I had to add a sleep 2s after the ifconfig wlan0 up to allow ndiswrapper to load before the rest of the configuration steps ran.  Apparantly when I changed to using Ubuntu's built-in network configuration tool the same problem was occuring.  ndiswrapper wasn't being loaded until the network interfaces were loaded and the rest of the configuration was happening before the driver was fully loaded.

I added ndiswrapper to the /etc/modules so that it's loaded before the network configuration takes place and that fixed it.[/QUOTE]

Hi Thornsten,

can you guide most of us how you add the ndiswrapper to the /etc/modules, so that it is loaded before network configuration takes place. Facing this problem for ages and still can't solve it

Thanks

---

### Post by lonetree on 2005-08-24
Ok, I think I have added ndiswrapper sucessfully in /etc/modules
 It loads up fine before configuring network interfaces, however, I think the wireless connection is not establish at all. I have to wait till ubuntu fully loaded up and login and go into network manager, deactivate wireless and activate wireless again. Then, I got my connection up sucessfully, in this situation, my network drives were not mounted at all.

Anyway, I use wep key #4 and 128 bits Dlink DI-724P+

Where do I go wrong again?

Regards,

---

### Post by GameManK on 2005-08-25
hi
i'm stuck here:
```
$ sudo iwlist wlan0 scan
 wlan0     Interface doesn't support scanning. 
```

it seems like its installing the driver but doesnt see the card

EDIT: after 2 reboots that problem seems to be solved, but now i have another one. it seems that the card is connecting and everything but it is disabled. when i try to enable it in the control center it enables it for a second then disables.

---

### Post by emotional1 on 2005-09-03
[QUOTE=Hieronymus]On this forum I see there are a lot of questions about installing WIFI using ndiswrapper, I have figured it out and I want to share it with you all. I made a howto in which I have combined all the solutions I have found. This is the system I use:
 
HP Pavilion zv5133ea  
AMD64 3000+ met 512 Mb intern 
Nvidia GeForce4 440 Go 64M 
Broadcom 802.11b Wlan 
Realtek RTL8139 NIC 
Ubuntu Hoary Hedgedog 5.04 64Bit / WinXp dual boot 
 
HOWTO: 
The first problem I have encountered was that the ndiswrapper-1.1 version didn't work. My drivers were installed however the command iwlist did't show any APs, the solution I found was to install the newest version of ndiswrapper:[ Ndiswrapper-1.2-RC1 ]("http://sourceforge.net/projects/ndiswrapper/").

The next step is to get drivers, I'm working with 64 Bit Ubuntu so I need 64 Bit drivers, here is a link to get windows wlan drivers for most Wlan cards: [ Wlan drivers ]("http://www.linuxant.com/driverloader/drivers.php").  This link provides also 64 bit drivers for all broadcom cards. 

Ok, on to the installation:

Step 1: Remove the old ndiswrapper and all links to it's driver.
```
 			  
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper 

```       
 
Step 2: Install Linux-headers.
 
```
 		     
sudo apt-get install linux-headers-2.6.10 (enter your version of linux headers or usr the synaptic package manager)


```
 
Step 3: Install Ndiswrapper.
 
```
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /home/username/ndiswrapper-1.2-rc1/ 
sudo make 
sudo make install

```
  
Step 4: Load drivers with ndiswrapper.
 
```

cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i bcmwl5.inf (fill out your own drivers for bcmwl5.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

```
 
Step 5: Load ndiswrapper and check if it worked.
 
```

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```
 
Step 6: Make sure Ndiswrapper is loaded during bootup.
 
```

sudo ndiswrapper -m 

```
 
Step 7: Configure your Wlan card.
 
```
     
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
sudo ping -c 3 [www.ubuntu-linux.nl]("http://www.ubuntu-linux.nl/") (tests the connection) 


```
 
Step 8: If you are using WPA encryprion check this thread [ WPA encryption voor Ndiswrapper ]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa"). 
 
I hope this will help some people. If there are comments or extra info you have please add it to this thread, it could help somebody.

Greets Hieronymus[/QUOTE]
 I have a question on step 3 of your how-to where it lists the command

cd /home/username/
sudo tar xvzf ndiswrapper-1.2-rc1/

when I hit enter on second command I get

The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 71063 files and directories currently installed.)
Removing ndiswrapper-utils ...
eric@ubuntu:~$ sudo rm -r /etc/ndiswrapper/
rm: cannot remove `/etc/ndiswrapper/': No such file or directory
eric@ubuntu:~$ sudo rm -r /etc/modprobe.d/ndiswrapper
rm: cannot remove `/etc/modprobe.d/ndiswrapper': No such file or directory
eric@ubuntu:~$ cd /home/eric
eric@ubuntu:~$ sudo tar xvzf ndiswrapper-1.3rc1/
tar: ndiswrapper-1.3rc1/: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

the ndiswrapper-1.3rc1.tar.gz is on my desktop, why is there a no file error message?
yes, I did type out the whole name and I still got the same error message no file or directory
How would one make the file or directory, and then place the ndiswrapper in it?
I do not apologize for my ignorance of how to do this and don't know enough to even search for the how-to to do this.  Obviously I am a complete newbie, but want, genuinely, to have the choice to use ubuntu and not contribute to the empire ($MS) anymore than my gov't has whored out to them.  please help

Eric

---

### Post by gsal on 2005-09-12
Hi:

Well, I have searched quite a few places regarding the setting of wlan with ndiswrapper and most postings focus on working instructions!  Not much is said what to do when things go wrong.  I hope I can get some help here.  

Just installed Ubuntu for the first time. Got version 5.04

Installed TRENDnet wireless card TEW-423PI, which somebody somewhere (in one of the soo many pages that I visited...like a list of hardware that has worked with ndiswrapper) said it worked with ndiswrapper before.

Used Synaptic to install recommended software, like kernel patch and ndiswrapper.

Acording the Synaptic, I installed ndiswrapper-utils version 0.12+1.0rc2.1  ...don't quite know what all that means.

Anyway, followed the typical instructions and got stuck with FATAL error when trying to execute "**sudo modprobe ndiswrapper**", as follows:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted.

The instructions followed included the installation of the Windows XP driver from cd.   After the installation, the command "ndiswrapper -l" responds the following:

Installed ndis drivers:
mrv8000c    driver  present, hardware present

Does anybody have any idea what's killing me?  Any help would be very much appreciated.

Forgive my ignorance.  And if the info provided is not good enough, please go ahead and ask for whatever you would like me to post, like answers to other commands or file contents.

Thanks. Looking forward for some replies.

GSal

---

### Post by gsal on 2005-09-14
Never mind...I got it working all by myself...o.k., maybe that is not quite true.  I followed the instructions in 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

and they worked just fine.

Thanks.

GSal

---

### Post by Domie on 2006-03-29
[QUOTE=Hieronymus]On this forum I see there are a lot of questions about installing WIFI using ndiswrapper, I have figured it out and I want to share it with you all. I made a howto in which I have combined all the solutions I have found. This is the system I use:
 
HP Pavilion zv5133ea  
AMD64 3000+ met 512 Mb intern 
Nvidia GeForce4 440 Go 64M 
Broadcom 802.11b Wlan 
Realtek RTL8139 NIC 
Ubuntu Hoary Hedgedog 5.04 64Bit / WinXp dual boot 
 
HOWTO: 
The first problem I have encountered was that the ndiswrapper-1.1 version didn't work. My drivers were installed however the command iwlist did't show any APs, the solution I found was to install the newest version of ndiswrapper:[ Ndiswrapper-1.2-RC1 ]("http://sourceforge.net/projects/ndiswrapper/").

The next step is to get drivers, I'm working with 64 Bit Ubuntu so I need 64 Bit drivers, here is a link to get windows wlan drivers for most Wlan cards: [ Wlan drivers ]("http://www.linuxant.com/driverloader/drivers.php").  This link provides also 64 bit drivers for all broadcom cards. 

Ok, on to the installation:

Step 1: Remove the old ndiswrapper and all links to it's driver.
```
 			  
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper 

```       
 
Step 2: Install Linux-headers.
 
```
 		     
sudo apt-get install linux-headers-2.6.10 (enter your version of linux headers or usr the synaptic package manager)


```
 
Step 3: Install Ndiswrapper.
 
```
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /home/username/ndiswrapper-1.2-rc1/ 
sudo make 
sudo make install

```
  
Step 4: Load drivers with ndiswrapper.
 
```

cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i bcmwl5.inf (fill out your own drivers for bcmwl5.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

```
 
Step 5: Load ndiswrapper and check if it worked.
 
```

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```
 
Step 6: Make sure Ndiswrapper is loaded during bootup.
 
```

sudo ndiswrapper -m 

```
 
Step 7: Configure your Wlan card.
 
```
     
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
sudo ping -c 3 [www.ubuntu-linux.nl]("http://www.ubuntu-linux.nl/") (tests the connection) 


```
 
Step 8: If you are using WPA encryprion check this thread [ WPA encryption voor Ndiswrapper ]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa"). 
 
I hope this will help some people. If there are comments or extra info you have please add it to this thread, it could help somebody.

Greets Hieronymus[/QUOTE]


Nice, but apt-get will not work if I have no internet connection. For the internet connection, I need ndiswrapper. You see the problem?

---

### Post by cadumg on 2006-03-29
Until this 

```
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```

Everything was ok. When I tried "dmesg" I've got thousand lines, so I do not know if this step was ok.

After, when I tried the scan, I've got:
```

cadumg@Rome:~/Desktop/driver$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

Taking a look on my networking configuration, I've seen that I do not have a wlan0, but a eth1 ? Is that a problem ? 

[[IMG]http://img145.imageshack.us/img145/8812/screenshotnetworksettings8rb.th.png[/IMG]](http://img145.imageshack.us/my.php?image=screenshotnetworksettings8rb.png)

Anyway, when i tried with it:
```

cadumg@Rome:~/Desktop/driver$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.
```

---

### Post by Uries on 2006-03-30
Okay, another complete newbie when it comes to Linux in general.  

I have 5.1 as well as Fedora Core 4 and Windows 2000 installed on my system, however I can only connect to the internet from WiFi as the port is in the other room.  I have the drivers for Windows, but Linux obviously cant see it.  I would like to convert most of my application usage to linux, but I can't without internet.  

I have the TrendNet TEW-424UB USB 802.11 g adapter.  

I can't find it anywhere on Linux websites, but I am wondering if there is a possibility I can get it to work with 5.10.  If there is a chance, I will go ahead and give it a try, using ndiswrapper or something else, it will be a good learning experience.  I just need the go ahead telling me it will not be a complete waste of time. 

If the TrendNet is useless in Linux, whats a good USB wifi card to get to be able to use in both OS's.

---

### Post by iAlta on 2006-03-31
whay can't ndiswrapper not just come stansard on Drake?

---

### Post by stevenyu on 2006-04-01
[quote=iAlta]whay can't ndiswrapper not just come stansard on Drake?[/quote]

Unh, Drake doesn't have ndiswrapper package in there?  OMG  :evil:

---

### Post by Audiophiliac on 2006-04-03
I installed Ndiswrapper. Then installed my drivers. Driverand harware can be seen. After sudo modprobe ndiswrapper my wifi card blinks. But when I run wireless tools, it says device doesn't support scanning. Plus my adapter doesn't appear on my Networking panel. Should it?

---

### Post by DarthMandeep on 2006-05-14
[QUOTE=stevenyu]Unh, Drake doesn't have ndiswrapper package in there?  OMG  :evil:[/QUOTE]


The Dapper LiveCD includes the ndiswrapper module in its kernel, but it doesn't have ndiswrapper-utils, which is needed to intall any drivers and actually make ndiswrapper work. This pissed me off to no end.

The text-mode install cd for Dapper, however, includes the ndiswrapper-utils package. I have no idea why the Dapper LiveCD can afford to include "Dive Into Python" but not ndiswrapper-utils.

---

### Post by Mordak on 2006-06-19
Will this howto work with the netgear WPN111 wireless usb adapter? I've been reading around a lot lately and havn't found much, but rumor has it this should apply.

If so, can someone help me out on how to get ndiswrapper-utils on my installation of ubuntu, and then how to get the damn thing working? im so new to linux this howto may even be too difficult for me. :(

---

### Post by linux_author on 2006-06-28
- sorry ubuntu, but leaving out ndiswrapper-utils from 6.06 is pretty bad... (just confirmed on the x64 live cd)

- very disappointed here - bad, bad move!

<sigh>, i guess i'll have to stick with KANOTIX64 and Slax-USB for my AMD64 notebook...

---

### Post by scoo007 on 2006-08-08
hii all 

when i do this :

sudo make 
sudo make install

i get this eror:

sudo: make: command not found

---

### Post by jbmigel on 2006-08-29
Great howto! worked like a charm in dapper with BCM4311BG
The hardest part was finding it since it is buried here in the hoary archives

---

### Post by jameswrogers on 2006-09-27
I am experiencing difficulties getting my Belkin wireless card working with ndiswrapper on Kubuntu.

I get as far as here without any problems:

Installed ndis drivers:
bcmwl5a         driver present, hardware present


Then when I modprobe ndiswrapper I get no errors but the lights on the card remain off. The message I see when I modprobe with verbose is:

# modprobe -v ndiswrapper
insmod /lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko


When I check the system logs I see:
kernel	[17179718.568000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)


I believe there should be a couple of other entries in the log:

ndiswrapper version <version> loaded
ndiswrapper: driver ''driver1'' added


These two entries are missing from my log, so that's obviously the problem. But I can't figure out why.

If you have any ideas I would greatly appreciate the help. By the way, I am a novice when it comes to operating systems.

---

### Post by jameswrogers on 2006-09-27
One thing I forgot to mention:

# lsmod | grep ndiswrapper
ndiswrapper           177364  0
usbcore               130820  4 ndiswrapper,usbhid,uhci_hcd


Does that look right?

---

### Post by gondilon on 2006-09-30
When I try to install my driver I get the following error:
couldn't copy bcmwl5.sys at /usr/sbin/ndiswrapper line 144.
please help!

---

### Post by gondilon on 2006-09-30
When I try to install the driver I get :couldn't copy bcmwl5.sys at /usr/sbin/ndiswrapper line 144.
please help

---

### Post by leetcharmer on 2006-10-27
I get problems starting with modprobe ndiswrapper

```
leetcharmer@lappyx64:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

ideas?

---

### Post by SniperSlap on 2007-01-28
These instructions served as a very reliable outline.

I'm on 6.06LTS.

I have a Broadcom 43xx based WiFi NIC by Linksys.  There are quite a few versions of drivers on their web site, but I found one that works best.

DO NOT use cutter.  Between a flakey and unreliable 2wire ADSL abomination and the cutter, I had nothing but nightmares with my internet connection.  I got the NDISwrapper drivers going and everything is awesome.

I also swapped up for a Westell ADSL modem as opposed to the 2wire, if you're an ADSL customer, I reccomend avoiding 2wire.  Tries to be too much and does a very sloppy job of it.

Anyway.  The process I used was to delete the firmware files from /lib/firmware and /lib/firmware/kernelversion.  I also added the 43xx module to the blacklist file in /etc.  Then I added ndiswrapper to load on boot.  That was of course after following (somewhat) these instructions.

Improvements?  Speed, reliability, ability to connect to APs, ability to have NIC retain a working config at boot...

---

### Post by PhoenixGSU on 2007-05-11
.inf installed properly but:

sudo ndiswrapper -i bcmwl5.sys
installing bcmwl5.sys ...
couldn't get manufacturer section - installation may be incomplete

sudo ndiswrapper -l
bcmwl5.sys : invalid driver!
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

:confused:

---

### Post by bushwacker on 2007-06-05
I just want to say that ndiswrapper works with the  WPC54GX Linksys Wireless G card using their latest drivers, at least on Feisty. It may not say that the device exists when you do ndiswrapper -l initially, but it will kick in after you run modprobe.

---

### Post by IchigoKurosaki on 2007-06-07
> 
Ndiswrapper : [ Ndiswrapper-1.46 ]("http://sourceforge.net/projects/ndiswrapper/").
Wlan Drivers : [ Wlan drivers ]("http://www.linuxant.com/driverloader/drivers.php"). 

Ok, on to the installation:

Step 1: Remove the old ndiswrapper and all links to it's driver.
```
 			  
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper 

```       
 
Step 2: Install Linux-headers.
 
```
 		     
sudo apt-get install linux-headers-$(uname -r)

```
 
Step 3: Install Ndiswrapper.
 
```
     
cd /home/$USERNAME/Desktop
tar xvzf ndiswrapper-1.46.tar.gz 
cd /home/$USERNAME/Desktop/ndiswrapper-1.46/ 
make 
sudo make install

```
  
Step 4: Load drivers with ndiswrapper.
 
```

cd /home/$USERNAME/Desktop/the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i bcmwl5.inf (fill out your own drivers for bcmwl5.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

```
 
Step 5: Load ndiswrapper and check if it worked.
 
```

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```
 
Step 6: Make sure Ndiswrapper is loaded during bootup.
 
```

sudo ndiswrapper -m 

```
 
Step 7: Configure your Wlan card.
 
```
     
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
sudo iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
ping -c 3 [www.ubuntu-linux.nl]("http://www.ubuntu-linux.nl/") (tests the connection) 


```
 
Step 8: If you are using WPA encryprion check this thread [ WPA encryption voor Ndiswrapper ]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa"). 
 

Fixed someone got a little too sudo Trigger Happy ;)

---

### Post by PenguinLover4Life on 2007-07-27
THANK YOU!!!!!! I have been trying to get my wireless card to work since about 10pm last night it's not 10 til 9 in the morning!!!! 

For future readers. I have a Toshiba A105-S2101. The Atheros AR500EG7 DOES WORK WITH UBUNTU. It will require a little work and alot of patience... for me at least.

Thank You!

---

### Post by sharmaneet on 2007-08-31
When I try to install my driver I get the following error:
couldn't copy bcmwl5.sys at /usr/sbin/ndiswrapper line 144.
please help! + [switch utilities](http://www.switch-utilities.com)

---

### Post by Meph1st0 on 2007-09-26
I'll admit it.  I didn't read all nine pages of this thread.  I was able to get Ndiswrapper installed, drivers loaded and I even got the machine on the network and pinged ubuntu.com.

But then I rebooted.  And now I'm no longer connected to the network.  Is there anyway I can get it to save the config?  I don't want to run through the same steps (enter the SSID, retype the WEP key, etc.) every time I reboot to get my machine back on the network.

---

### Post by potatan on 2007-11-21
Hi

Very useful post and I have follwed it almost to the end (after figuring out how to solve a few other issues along the way).

When I run the sudo dmesg I get the following output:

[ 2093.198825] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2142.986505] ndiswrapper version 1.50rc1 loaded (smp=yes, preempt=no)
[ 2143.005903] usbcore: registered new interface driver ndiswrapper
[ 2227.300586] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2376.777465] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2529.366457] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


All the previous steps worked (eventually).  

Any ideas?

Ubuntu 7.10 using 64 bit version on an AMD 64 Pavilion 5200

I'm a bit of a linux newb but can follow most instructions.  Many thanks

---

### Post by ishkabibble on 2008-01-05
I tried it with several different .inf files and got "no ndiswrapper utils found!" for each one.  Am I doing something wrong?

---

### Post by ishkabibble on 2008-01-07
Well, I found the solution to my last problem.  The utilities weren't installed, only ndiswrapper.  My card (Encore ENWLI-W) has several drivers and I think I installed the wrong one first.  How do I *un*install it?

From my dmesg:
[16041.131373] ndiswrapper version 1.45 loaded (smp=yes)
[16041.185866] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[16041.185888] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[16041.185901] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[16041.185914] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[16041.185926] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[16041.185938] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[16041.185951] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[16041.185963] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[16041.185976] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[16041.185999] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[16041.186012] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[16041.186025] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[16041.186037] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[16041.186050] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[16041.186088] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[16041.186129] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[16041.186149] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[16041.186161] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[16041.186177] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[16041.186196] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[16041.186230] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[16041.186243] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[16041.186256] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[16041.186268] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[16041.186280] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[16041.186299] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[16041.186309] ndiswrapper (load_sys_files:216): couldn't prepare driver 'netmw13b'
[16041.199599] ndiswrapper (load_wrap_driver:118): couldn't load driver netmw13b; check system log for messages from 'loadndisdriver'

---

### Post by ishkabibble on 2008-01-08
Well, figured that one out as well.  I've got what I think is the correct driver installed, but it doesn't appear to be finding the wireless card.  iwconfig yields:
lo        no wireless extensions.
eth0      no wireless extensions.

And dmesg now shows:
[ 1313.680301] ndiswrapper version 1.45 loaded (smp=yes)
[ 1313.789396] ndiswrapper: driver mrv8000c (Marvell,02/22/2005,3.1.1.7) loaded
[ 1313.789931] ACPI: Unable to derive IRQ for device 0000:04:03.0
[ 1313.789936] ACPI: PCI Interrupt 0000:04:03.0[Q]: no GSI - using IRQ 10
[ 1313.791515] ndiswrapper: using IRQ 10
[ 1314.705826] ndiswrapper (mp_init:263): couldn't initialize device: C0000001
[ 1314.705839] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
[ 1314.705857] ndiswrapper (mp_halt:305): device f4552500 is not initialized - not halting
[ 1314.705868] ndiswrapper: device eth%d removed
[ 1314.705890] ACPI: Unable to derive IRQ for device 0000:04:03.0
[ 1314.705904] ndiswrapper: probe of 0000:04:03.0 failed with error -22
[ 1314.705968] usbcore: registered new interface driver ndiswrapper

I think I'm going to try a different slot for the card.  Any other ideas?

---

### Post by bnmjosh on 2008-05-22
Hi, thanks for writing this up, but I need some help.

When I type "sudo make install" after sudo make, etc, I get this:

> josh@josh-laptop:~/internet2/ndiswrapper-1.2$ sudo make
make -C driver
make[1]: Entering directory `/home/josh/internet2/ndiswrapper-1.2/driver'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/josh/internet2/ndiswrapper-1.2/driver \
		NDISWRAPPER_VERSION=1.2 \
		EXTRA_VERSION= modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/josh/internet2/ndiswrapper-1.2/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/josh/internet2/ndiswrapper-1.2/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/josh/internet2/ndiswrapper-1.2/driver'
make: *** [all] Error 2

What can I do? Thanks.

---

### Post by oni5115 on 2008-08-11
Just wanted to post a thanks.  I have been working on an old old laptop, stuck in the command line for several hours because the actual adm8211 drivers are broken, or least don't seem work with WEP.  Using this guide, and the windows driver disk the card came with.  BOOM... working. Yay I can finally install fluxbox/icewm and mess with them.  :lolflag:

---

### Post by kinrose on 2008-08-20
> **Hieronymus said:**
> On this forum I see there are a lot of questions about installing WIFI using ndiswrapper, I have figured it out and I want to share it with you all. I made a howto in which I have combined all the solutions I have found. This is the system I use:
 
HP Pavilion zv5133ea  
AMD64 3000+ met 512 Mb intern 
Nvidia GeForce4 440 Go 64M 
Broadcom 802.11b Wlan 
Realtek RTL8139 NIC 
Ubuntu Hoary Hedgedog 5.04 64Bit / WinXp dual boot 
 
HOWTO: 
The first problem I have encountered was that the ndiswrapper-1.1 version didn't work. My drivers were installed however the command iwlist did't show any APs, the solution I found was to install the newest version of ndiswrapper:[ Ndiswrapper-1.2-RC1 ]("http://sourceforge.net/projects/ndiswrapper/").

The next step is to get drivers, I'm working with 64 Bit Ubuntu so I need 64 Bit drivers, here is a link to get windows wlan drivers for most Wlan cards: [ Wlan drivers ]("http://www.linuxant.com/driverloader/drivers.php").  This link provides also 64 bit drivers for all broadcom cards. 

Ok, on to the installation:

Step 1: Remove the old ndiswrapper and all links to it's driver.
```
 			  
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper 

```       
 
Step 2: Install Linux-headers.
 
```
 		     
sudo apt-get install linux-headers-2.6.10 (enter your version of linux headers or usr the synaptic package manager)


```
 
Step 3: Install Ndiswrapper.
 
```
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /home/username/ndiswrapper-1.2-rc1/ 
sudo make 
sudo make install

```
  
Step 4: Load drivers with ndiswrapper.
 
```

cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i bcmwl5.inf (fill out your own drivers for bcmwl5.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

```
 
Step 5: Load ndiswrapper and check if it worked.
 
```

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```
 
Step 6: Make sure Ndiswrapper is loaded during bootup.
 
```

sudo ndiswrapper -m 

```
 
Step 7: Configure your Wlan card.
 
```
     
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
sudo ping -c 3 [www.ubuntu-linux.nl]("http://www.ubuntu-linux.nl/") (tests the connection) 


```
 
Step 8: If you are using WPA encryprion check this thread [ WPA encryption voor Ndiswrapper ]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa"). 
 
I hope this will help some people. If there are comments or extra info you have please add it to this thread, it could help somebody.

Greets Hieronymus
All worked well and I pinged, it replied: 10 packets transmitted 10 received 0% packet loss.  When i pinged my ISP [www.talktalk.net](www.talktalk.net) I got the following: 461 packets transmitted 0 received 100% loss.
I can ping yahoo, google and the BBC but not ebay.
I right clicked on the connection icon at top right hand of screen. It says Speed 11% and all the other settings look right.
I have followed Kevdogs instructions and also installed ndiswrapper 1.53
Any help appreciated.

---

### Post by degarb on 2010-01-25
There is no way in hell that the average person, including me cn type all these lines without typos.  I don't know why a a simple himan interactive batch like file isn't whipped up for these occasions.  In dos this can  be done easily , asking for user input to variables.  Like 5 hours of time could save endusers millions of collective hours.  I cannot even read the solution without my eyes rolling back in my head long enough to see what appears to me little more meaningful than a combination to a very complex combination lock.  aGAIN,  this should be scripted or programmed.   

At very least is there not some simple scripting language a user that find this can post into some bat file, enter input dialog and distrubute in forum.  Like a bat file posting.

---

### Post by paulcalabro on 2010-08-07
> **Hieronymus said:**
> On this forum I see there are a lot of questions about installing WIFI using ndiswrapper, I have figured it out and I want to share it with you all. I made a howto in which I have combined all the solutions I have found. This is the system I use:
 
HP Pavilion zv5133ea  
AMD64 3000+ met 512 Mb intern 
Nvidia GeForce4 440 Go 64M 
Broadcom 802.11b Wlan 
Realtek RTL8139 NIC 
Ubuntu Hoary Hedgedog 5.04 64Bit / WinXp dual boot 
 
HOWTO: 
The first problem I have encountered was that the ndiswrapper-1.1 version didn't work. My drivers were installed however the command iwlist did't show any APs, the solution I found was to install the newest version of ndiswrapper:[ Ndiswrapper-1.2-RC1 ]("http://sourceforge.net/projects/ndiswrapper/").

The next step is to get drivers, I'm working with 64 Bit Ubuntu so I need 64 Bit drivers, here is a link to get windows wlan drivers for most Wlan cards: [ Wlan drivers ]("http://www.linuxant.com/driverloader/drivers.php").  This link provides also 64 bit drivers for all broadcom cards. 

Ok, on to the installation:

Step 1: Remove the old ndiswrapper and all links to it's driver.
```
 			  
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper 

```       
 
Step 2: Install Linux-headers.
 
```
 		     
sudo apt-get install linux-headers-2.6.10 (enter your version of linux headers or usr the synaptic package manager)


```
 
Step 3: Install Ndiswrapper.
 
```
     
cd /home/username/ 
sudo tar xvzf ndiswrapper-1.2-rc1 
cd /home/username/ndiswrapper-1.2-rc1/ 
sudo make 
sudo make install

```
  
Step 4: Load drivers with ndiswrapper.
 
```

cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i bcmwl5.inf (fill out your own drivers for bcmwl5.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

```
 
Step 5: Load ndiswrapper and check if it worked.
 
```

sudo modprobe ndiswrapper 
sudo dmesg (shows that the card is installed (hopefully)) 
sudo iwlist wlan0 scan (shows all APs surrounding you) 

```
 
Step 6: Make sure Ndiswrapper is loaded during bootup.
 
```

sudo ndiswrapper -m 

```
 
Step 7: Configure your Wlan card.
 
```
     
sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
sudo dhclient wlan0 (gets a dynamic IP adress) 
sudo ping -c 3 [www.ubuntu-linux.nl]("http://www.ubuntu-linux.nl/") (tests the connection) 


```
 
Step 8: If you are using WPA encryprion check this thread [ WPA encryption voor Ndiswrapper ]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa"). 
 
I hope this will help some people. If there are comments or extra info you have please add it to this thread, it could help somebody.

Greets Hieronymus

Hieronymus YOU ARE THE MAN!! 
I had it going a long time ago. 
Tried the same exact same procedure... no luck!
The whole purge startover bit probably did the trick, I just wasnt sure of the procedure! 

THANKS SOOO MUCH!! :D

---

### Post by bildr on 2010-08-07
enter the flamebait - don't use ndiswrapper...use native drivers

sorry, i know it isn't very constructive, but i despise ndiswrapper and wireless cards are cheap

---

