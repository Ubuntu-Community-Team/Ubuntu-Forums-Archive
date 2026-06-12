---
title: "[SOLVED] Help new user, wireless and nvidia"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by banana jama on 2008-10-27
Hello im very new to ubuntu i just downloaded it yesterday (vista crash and want a change). I have a HP pavilion dv6000 with a 2.0 GHZ processor, 2GB  of ram and a250 hd. after i instal ubuntu i couldn't get on the internet. the drivers for my atheros wireless card was found it said it was restricted but they were enable. also when i press manually configure there is no wireless option. set up ubuntu to work properly with my wireless laptop. oh yea its a atheros card. Also i do i make sure that my Nvidia graphic card is working i've read alot that Nvidia does't work on Ubuntu. thatnks.  O yea im using ubuntu 8.04

---

### Post by bodhi.zazen on 2008-10-27
You have two options with nvidia, 

Open source :

Open a terminal and type :```
sudo apt-get install nvidia-glx-new nvidia-settings
```

Re boot, log in and set your resolution with :

```
gksu nvidia-settings
```

You need to save your settings.

For the wireless you need to install the drivers, probably with ndiswrapper.

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by banana jama on 2008-10-27
I asked A question eariler but forgot to say that i have no internet access other than my wifi. I am very new to ubuntu(just downloaded it yesterday) and i downloaded it on to a HP pavilion dv6000. it has 2.0 ghz 250 gb hd and 2gb of ram. I have a atheros wifi thing that connects me to the internet(as you can see me computer lingo is horrible!). when I use ubuntu it discovers my driver for atheros but says its a resrticted driver. i think its called a atheros 5700(im not sure all it says on ubuntu is atheros 802.11) how can i set up atheros on ubuntu so i can get on the internet. Remember other than wifi i have no internet and without atheros i have no wifi. PLEASE HELP ME!!! 
   O yea i also want to get my nvidia working but the code someone gave me did work because it reqires internet. it was 
  sudo apt-get install nvidia-glx-nex nvidia settings 
is there anyway i gave get it working without internet on ubuntu.

More info: ubuntu on my laptop is dual boot on vista. i get internet on vista.

---

### Post by Elfy on 2008-10-27
Your post was moved - it is here complete with an answer

[http://ubuntuforums.org/showthread.php?t=960555](http://ubuntuforums.org/showthread.php?t=960555)

this isn't actually a thread to ask questions in :D

---

### Post by banana jama on 2008-10-27
> **bodhi.zazen said:**
> You have two options with nvidia, 

Open source :

Open a terminal and type :```
sudo apt-get install nvidia-glx-new nvidia-settings
```

Re boot, log in and set your resolution with :

```
gksu nvidia-settings
```

You need to save your settings.

For the wireless you need to install the drivers, probably with ndiswrapper.

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)
i don't have internet. so im not able to use those codes is there another way without using internet.

---

### Post by Nxion on 2008-10-27
So when yo go into System >Administration > Hardware Drivers it says that your Atheros card is already enabled?

If so when you single right click on the network icon in the Gnome task bar which is the bar on the top of your screen, two options should show up. One said " Enable Networking" and the other shold say "Enable Wireless" and both should be checked.

If that is true, if you single left click on the network icon, you should see a list of wireless networks you can connect. Do you see any?

EDIT:

Do you have the ability to plug in directly to your router or modem via a ethernet cable?

---

### Post by bodhi.zazen on 2008-10-27
It will be much more difficult if you do not have a network connection. Can you plug it into a wired network until you wireless is working (probably your best option).

---

### Post by banana jama on 2008-10-27
when i click on network on the gnome task bar there is only networking is chack there is no option for wireless there only networking.  no i don't have a ethernet cable but im trying to get one but, its unlikely that i will get it. what should i do now  

       to forestpixie:sorry about posting this here but when i send a reply for some reason it ends up on this page.

---

### Post by bodhi.zazen on 2008-10-27
> **banana jama said:**
> to forestpixie:sorry about posting this here but when i send a reply for some reason it ends up on this page.

lol

---

### Post by banana jama on 2008-10-27
ok so i've made alsot of head way i got the an ethernet cable connect to the internet and got nvidia up and running. i tried putting that command from that website to get the atheros up and running but it didn't. i no its atheros but i don't think its 5700. what do i do no 
  EDIT: I FOUND out its a Artheros AR5009 WLAN

---

### Post by bodhi.zazen on 2008-10-27
google search your atheros model and ubuntu

If you find a how-to , an need help, let us know (post link)

---

### Post by Elfy on 2008-10-28
> to forestpixie:sorry about posting this here but when i send a reply for some reason it ends up on this page.This is your thread now, the posts in the beginneres team are all here  - post away :)

---

### Post by banana jama on 2008-10-29
i found this link [http://ubuntuforums.org/showthread.php?t=865971&highlight=madwifi]("http://ubuntuforums.org/showthread.php?t=865971&highlight=madwifi") that's suppose to solve my problem. but i need help with it. i don't know what he means by "Just watch what the file is that is extracted."  i put in the first set of commands posted but now im stumped. 

this is what i got after putting first set of commands:
```
akeem@akeem-laptop:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for akeem: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 8707kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com hardy-updates/main linux-libc-dev 2.6.24-21.43 [699kB]
Get:2 http://us.archive.ubuntu.com hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Get:3 http://us.archive.ubuntu.com hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu3 [1187kB]
Get:4 http://us.archive.ubuntu.com hardy-updates/main g++-4.2 4.2.4-1ubuntu3 [2784kB]
Get:5 http://us.archive.ubuntu.com hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get:6 http://us.archive.ubuntu.com hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 http://us.archive.ubuntu.com hardy/main patch 2.5.9-4 [95.6kB]           
Get:8 http://us.archive.ubuntu.com hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:9 http://us.archive.ubuntu.com hardy/main build-essential 11.3ubuntu1 [7066B]
Fetched 8707kB in 17s (507kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 114375 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-21.43_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-21.43) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu3) ...
Setting up g++-4.2 (4.2.4-1ubuntu3) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) .
``` 
now i need help with the second set of commands i put them in EXACTLY AS THEY ARE IN HIS POST (i don't now if im suppose to modify it). 
this is what i got after putting in the second set of commands:
```
akeem@akeem-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
akeem@akeem-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
akeem@akeem-laptop:~$ sudo modprobe ath_pci
akeem@akeem-laptop:~$ sudo reboot

```
 
so can someone please help me please!!!!!!!!!!!!!!! did i do something wrong

---

### Post by Elfy on 2008-10-29
before you can run make you need to change onto the directory - I assume you're talking about post #4 in that thread

in the terminal - try ```
cd Desktop
```

now use auto complete to change into the driectory of the extracted file

```
cd mad<tab>
```

don't copy the <tab> but use your tab key to complete name

then run the make make install commands

---

### Post by nhasian on 2008-10-29
i just installed ubuntu 8.10 on a new toshiba laptop yesterday and had the same problem with the Atheros wifi but was able to resolve it.  you'll need to use a wired connection temporarily to fix it.  do all the updates and reboot for ubuntu then type:

```
iwconfig
```

if it doesnt show any wifi adaptors (wlan0) then do this:

```
sudo vi /etc/modprobe.d/blacklist
```

at the end of the file append:

blacklist ath_pci
blacklist ath_hal

save reboot and see if its working.  it should show up in the iwconfig now.  if it doesnt, do this last step:

Go to System/Administration/Synaptic package manager and install linux-backports-modules-intrepid

again this is for the new ubuntu 8.10 Intrepid ibex :)

---

### Post by banana jama on 2008-10-29
aaahhh!!! once again no luck. hey forestpixie should i just wait for ubuntu 8.10 to come out and download it. will they'll be a better chance that the new os will support ny driver.

o yea nhasian i didn't try your command yet because im still using 8.04 i'll try it if i up grade.

---

### Post by Elfy on 2008-10-29
possibly - but I couldn't be sure, I've never needed to use wireless - a blessing in disguise it sometimes appears ;)

---

### Post by locbart5 on 2008-10-29
Have you installed all available updates yet? I installed my wireless card driver using ndiswrapper, and my wireless card only worked after I installed an update package, which has me running the HH kernel number ending in .21 (I'm at work and don't have access to my laptop to check the full number). Like I said, until I install the driver using ndiswrapper AND install updates - no wireless.

---

### Post by banana jama on 2008-10-29
yea i just check my updates are up to date.
i don't know whatelse to do i've tried everything i've found on the internet and still no luck. i'm going to upgrade to 8.10 once its release but if that doesn't work then i'm just plan on buying one of those use wifi modems.

---

### Post by banana jama on 2008-10-30
i just install ubuntu 8.10. but now i doesn't recogized my my wireless card any suggestions.

---

### Post by nhasian on 2008-11-01
great!  if you've installed the latest ubuntu 8.10 with all the updates, did you follow my instructions to blacklist the two bad drivers a few posts back?

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

---

### Post by banana jama on 2008-11-01
i enter the commands you gave and nothing happened. i don't know if i did something wrong. also when i went to the packeage manager to installes that thing you reccomended about 20 choices came up and i didn't know which one to pick (some on the list were already marked i think that means they were already install). 
            i don't know what else to do unlike 8.04 ubuntu 8.10 doesn't show HAL under resricted drivers. anyway to get hal to be recognized and will that make my wifi work.

---

### Post by nhasian on 2008-11-02
i dont think your wifi will work until you install linux-backports-modules-intrepid.  I know there are several similar lines, but there is only one.  you can also install it directly from the terminal with this command:

```
sudo apt-get install linux-backports-modules-intrepid
```

after it installs, reboot and your wifi should start working.

> **banana jama said:**
> also when i went to the packeage manager to installes that thing you reccomended about 20 choices came up and i didn't know which one to pick

---

### Post by banana jama on 2008-11-02
i entered the command you posted and still nothing. in restricted drivers there is now a new enable driver called "support for 5xxx series of atheros 802.11 wireless LAN cards" i could see why you said this should work. i found out the type of lan card i have by looking at hp website and entering my product number. do you think that i may not have this type of LAN card? is there a way for me to find out the exact model?

---

### Post by banana jama on 2008-11-02
i entered the command and in restricted drivers there is a new driver called support for 5xxx series of atheros 802.11 wireless LAN cards. but i still don't have wifi. i found out my lan model by looking at hp's website and now im starting to think that this isn't my lan models because none of the advice people gave worked. is there a way to find the model number

---

### Post by clb137 on 2008-11-02
hi,

i have just installed on 2 laptops with atheros wifi,
just follow the instruction on the following link and all will work

[http://ubuntuforums.org/showthread.php?t=964836](http://ubuntuforums.org/showthread.php?t=964836)

good luck

clint

---

### Post by clb137 on 2008-11-02
> **banana jama said:**
> i entered the command and in restricted drivers there is a new driver called support for 5xxx series of atheros 802.11 wireless LAN cards. but i still don't have wifi. i found out my lan model by looking at hp's website and now im starting to think that this isn't my lan models because none of the advice people gave worked. is there a way to find the model number

yes type lspci in the terminal, if you follow the link in my post above it will work

clint

---

### Post by banana jama on 2008-11-02
its not working when i enter the command i get this: > akeem@akeem-laptop:~$ wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2)
--2008-11-02 17:13:17--  [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2)
Resolving wireless.kernel.org... 83.246.72.84
Connecting to wireless.kernel.org|83.246.72.84|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1522534 (1.5M) [application/octet-stream]
Saving to: `compat-wireless-2008-10-31.tar.bz2'

100%[======================================>] 1,522,534    576K/s   in 2.6s    

2008-11-02 17:13:21 (576 KB/s) - `compat-wireless-2008-10-31.tar.bz2' saved [1522534/1522534]

akeem@akeem-laptop:~$ tar jxvf compat-wireless-2.6.tar.bz2
tar: compat-wireless-2.6.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
akeem@akeem-laptop:~$ cd compat-wireless-2008-10-31
bash: cd: compat-wireless-2008-10-31: No such file or directory
akeem@akeem-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
akeem@akeem-laptop:~$ sudo make install
[sudo] password for akeem: 
make: *** No rule to make target `install'.  Stop.
akeem@akeem-laptop:~$ 



---

### Post by banana jama on 2008-11-02
I DID IT !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! I GOT WIFI!!!!!!!!!! HAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHAHA!!!!!!!!!!!!!!!! thanks to everyone who help me out. i figure out that the ndiswrapper wasn't working properly and i followed this link to get there[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847") but thanks to everyone who gave me suggestions and code to help me solve this problem. this forum rules!!!! UBUNTU IS THE GREATEST!!!!!!!!!!!! this problem is offically solved!!!

---

