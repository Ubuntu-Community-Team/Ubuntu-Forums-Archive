---
title: "Atheros 5007 Wifi Chipset Hardy (8.04LTS) Install"
date: 2008-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by k33bz on 2008-05-20
After alot of toying around trying to find how I can get my wireless working in my Acer Aspire Laptop I came across this post.

The originally post is in German. 

I have place the contents below.



 If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

First make sure of your Network card. But do be careful, for some reason it might report back to being AR5006 or might come up as  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


More than likely if you get either one of those reported back to you it is in fact AR5007.

Run this code in your terminal

```
lspci
```
For i386 Users:

First go to System> Administration-> Hardware Drivers "and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then reboot your system

Preparing your System

Go to System->Administration->Software Sources 
Make sure you have "Universe" & "Multiverse" checked.

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

```
sudo apt-get install build-essential

wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot 
```

That’s it now your wireless should work without any problem.




PROCEDURE FOR UBUNTU HARDY HERON 64 bits USERS
(NEW INFO PROVIDED BY ANDUU FOR YOU 64BIT USERS. GO TO HIS THREAD:[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780") AND THANK BRAVEERUDITE FOR POINTING THIS OUT)

64-bit users please let me know if the above solution works.

Go to System / Administration / hardware drivers and disable all referring to your network card

HAL and support for Atheros Card

 Ensure you have your kernel headers and build the essential package. Use Synaptic or: 


```
sudo aptitude update 

sudo aptitude install linux-headers-$ (uname-r) build-essential

Install ndisgtk.
```

Use Synaptic or: 


```
sudo apt-get install ndisgtk
```

Get 64 bits XP drivers from blakemartin:

```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz 


tar xvf ar5007eg-*.tar.gz tar xvf ar5007eg tar.gz-*.

tar xvf ndiswrapper-newest.tar.gz 
```

Blacklist the default driver 

```
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
```

Load Ndiswrapper and XP driver:

```
sudo ndiswrapper -i net5211.inf Sudo ndiswrapper-i net5211.inf
```

Load up ndiswrapper every time Linux is loaded

```
sudo modprobe ndiswrapper Sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules 
```

Restart your system using the following command Restart your system using the following command

```
sudo reboot 
```

At this point your network card must work OK if not try to load XP driver with ndisgtk.
(blue led in some laptops will not work or still red but its a minor problem)

This information was taken from forums.
 When you reboot your PC in most cases AR5007EG does not work anymore (maybe find networks but can not connect to them)

Victor Nieto has written a script to solve the problem but this script must be executed before X server starts, I tried this and works ok EVERY TIME TURNS YOU ON YOUR PC.

first of all here is the script:
Use an editor and copy-paste this: (pay attention in the 1st. Line in other posts looks like "# bin / bash", correct it)

```
#! bin/bash 
modprobe-r ndiswrapper
cp /etc/modprobe.d/blacklist
sed ’s/#blacklist ath_pci/blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist 
ndiswrapper -ma && sudo ndiswrapper -mi
modprobe ndiswrapper
sed ’s/blacklist ath_pci/#blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist blacklist3 /etc/init.d/networking restart
```

Save the file as subirwifi

Copy file into / etc / init.d and change file mode

```
sudo cp subirwifi /etc/init.d subirwifi
```

Now we need to make a symbolic link in / etc/rc5.d to load driver before X server starts.

Go to / etc/rc5.d

```
sudo ln -s /etc/init.d/subirwifi S09subirwifi
```

if all was correct you should see a line like this when you do ```
ls -l
```

lrwxrwxrwx …………… S09subirwifi -> /ect/init.d/subirwifi 

reboot your system and… Luck!!! 


Thanks to all who contribute to make Linux grow up, and specially to Victor Nieto for the script.

---

### Post by be4truth on 2008-05-21
Hi k33bz,
the org. German link is local /media/disk. Does that mean you have a German USB stick?:) Can you post the Internet link. I have trouble with this wireless card and will try your suggestion as soon as I am back on that laptop.

---

### Post by k33bz on 2008-05-22
> **be4truth said:**
> Hi k33bz,
the org. German link is local /media/disk. Does that mean you have a German USB stick?:) Can you post the Internet link. I have trouble with this wireless card and will try your suggestion as soon as I am back on that laptop.

No, it probable did that because I had saved the document for easy viewing while off line. I will try to find the real link again.


cant seem to find that link now, so I will just remove the link I have here.

---

### Post by Anduu on 2008-05-22
Regarding the ndiswrapper 64 bit method:

I am in a bit of a pickle....

Everything goes well up until using the script on reboot.As far as I can tell I did everything correctly regarding copying and symlinking it however it doesn't seem to have any effect.I can see wireless networks but cannot connect.

Once rebooted if I run the script manually ie sudo sh /etc/init.d/subirwifi I can ***usually*** get connected.Sometimes I have to disable/re-enable wireless through the network manager to be able to connect.

During my testing on the odd occasion I have been able to get connected without doing anything!

Something kinda flakey is going on here...any ideas.

---

### Post by k33bz on 2008-05-22
> **Anduu said:**
> Regarding the ndiswrapper 64 bit method:

I am in a bit of a pickle....

Everything goes well up until using the script on reboot.As far as I can tell I did everything correctly regarding copying and symlinking it however it doesn't seem to have any effect.I can see wireless networks but cannot connect.

Once rebooted if I run the script manually ie sudo sh /etc/init.d/subirwifi I can ***usually*** get connected.Sometimes I have to disable/re-enable wireless through the network manager to be able to connect.

During my testing on the odd occasion I have been able to get connected without doing anything!

Something kinda flakey is going on here...any ideas.

To tell you the truth, I am not sure, hope someone else comes by and lets you know. I dont run a 64 bit machine. I just found this post, and it worked perfectly for me on my machine. But I dont have the hardware to test on a 64 bit.

---

### Post by Anduu on 2008-05-23
Well I think I have it sorted out now....I added ```
/etc/init.d/networking restart
``` to the end of the script and after rebooting a few times it has been connecting consistently so far.

---

### Post by k33bz on 2008-05-23
Sounds good, for others I will add that at the end of the script I have up there.




SCRIPT FIXED

---

### Post by Jaded Misanthrope on 2008-05-26
I got this method working once, but after restart I could not connect to wireless anymore. I haven't tried going through the steps again, but I am pretty sure that would allow me to connect again; is there a way around having to go through the steps each reboot?

Just a note: I'm running i386 / 32 bit or whatever and followed the first set on instructions.

EDIT: Okay, running the instructions starting from cd madwifi-ng-r2756+ar5007 works, but is there a way to not have to go through the instructions from there each time I reboot when the wireless works?

---

### Post by k33bz on 2008-05-26
> **Jaded Misanthrope said:**
> I got this method working once, but after restart I could not connect to wireless anymore. I haven't tried going through the steps again, but I am pretty sure that would allow me to connect again; is there a way around having to go through the steps each reboot?

Just a note: I'm running i386 / 32 bit or whatever and followed the first set on instructions.

EDIT: Okay, running the instructions starting from cd madwifi-ng-r2756+ar5007 works, but is there a way to not have to go through the instructions from there each time I reboot when the wireless works?


MMMM, I am not sure about that, I only did these instructions once, never had a problem after rebooting. Only thing I can suggest is to go over the steps again, and make sure you did everything.

sorry.

---

### Post by Jaded Misanthrope on 2008-05-27
Yeah, I just rebooted after going to bed last night and I could connect to my router straight away; not sure what happened--hopefully it'll work like that all the time now.

---

### Post by k33bz on 2008-05-28
> **Jaded Misanthrope said:**
> Yeah, I just rebooted after going to bed last night and I could connect to my router straight away; not sure what happened--hopefully it'll work like that all the time now.


sounds good, let me know if it still connects properly.

---

### Post by Jaded Misanthrope on 2008-06-05
It was working correctly each time until today; I'm about to leave the house, but I'll try doing what I did last time in the terminal again when I get back. I think I'll just have a text file containing this command stashed somewhere on Ubuntu so I don't forget it.

---

### Post by k33bz on 2008-06-05
> **Jaded Misanthrope said:**
> It was working correctly each time until today; I'm about to leave the house, but I'll try doing what I did last time in the terminal again when I get back. I think I'll just have a text file containing this command stashed somewhere on Ubuntu so I don't forget it.


or you can just make a script and place it in your home folder. Other than that if you find a work around where you never have to run the commands again, let me know how you did it. That way I can add it to the How-to. ANd other than that sorry, I never came acros this problem with Feisty or with Hardy. Diferent scripts and drivers for both versions.

---

### Post by daehenoc on 2008-06-06
Hi,

Thanks for the useful post, it worked great for me when I did my initial install of 8.04 on my MSI EX600 laptop :)

However, with the recent kernel upgrade to 2.6.24-18-generic, this fix no longer works for me :(

After disabling the drivers and rebooting, the kernel modules were still loading, so I did a 'sudo rmmod ath_pci' and 'sudo rmmod ath_hal' to remove those modules before starting the build process.

Here is the output from the various steps:
Compile works fine.

$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-18-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

7$ dmesg | tail
[  256.400248] ath_pci: disagrees about version of symbol ieee80211_announce
[  256.400252] ath_pci: Unknown symbol ieee80211_announce
[  256.400340] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[  256.400344] ath_pci: Unknown symbol ieee80211_chan2ieee
[  256.400707] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch
[  256.400710] ath_pci: Unknown symbol ieee80211_dturbo_switch
[  256.400784] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[  256.400788] ath_pci: Unknown symbol ieee80211_crypto_encap
[  256.400926] ath_pci: disagrees about version of symbol ieee80211_getrssi
[  256.400930] ath_pci: Unknown symbol ieee80211_getrssi

Any hints?

---

### Post by Gokee2 on 2008-06-07
This made the wireless work for me on a new HP Pavilion dv9810us.  Thanks!  The 64 bit version could use a little cleanup, a few places where you have the command twice on a line and such also the linux header command did not work for me (take out $ () and put in `` instead around uname to make that work).  Also the script did way more things then I needed to.  I did not have a problem on bootup with ath mods being loaded however I did need to unload and reload the ndiswrapper module to make wireless work.  That seems rather odd but just having a script modprobe -r ndiswrapper then modprobe ndiswrapper worked for me.

Thanks!

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by k33bz on 2008-06-08
> **braveerudite said:**
> Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

Just dont forget to mention that it is only for the 64bit OS's. For the 32 bit until someone finds better, stick with whats on first page.

---

### Post by daehenoc on 2008-06-09
OK, I got my card working with the r3366 patch from madwifi: [http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

I also had trouble for a few days, BECAUSE THE WIFI WAS OFF!!!  Stupid button-press on/off switch on wifi card!!!

---

### Post by be4truth on 2008-06-09
> **daehenoc said:**
> OK, I got my card working with the r3366 patch from madwifi: [http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

I also had trouble for a few days, BECAUSE THE WIFI WAS OFF!!!  Stupid button-press on/off switch on wifi card!!!

Do you run 32 or 64 bit?

---

### Post by daehenoc on 2008-06-09
Oh yeah, sorry, 32 bit.

---

### Post by Joe Driller on 2008-06-09
Howto setup AR5007EG in Hardy Heron 64 Bits



PROCEDURE FOR UBUNTU HARDY HERON 64 Bits USERS

Go to System/Administration/Hardware drivers and disable all referring to your network card

HAL and support for Atheros Card

Ensure you have your kernel headers and the build essential package. Use Synaptic or:

sudo aptitude update

sudo aptitude install linux-headers-$(uname -r) build-essential

Install ndisgtk. Use Synaptic or:

sudo apt-get install ndisgtk

Get 64 Bits XP drivers from blakemartin:

wget [http://blakecmartin.googlepages.com/...-64-0.2.tar.gz](http://blakecmartin.googlepages.com/...-64-0.2.tar.gz)

Extract driver using the following command

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

Blacklist the default driver

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

Load Ndiswrapper and XP driver:

sudo ndiswrapper -i net5211.inf

Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

sudo reboot

At this point your network card must work O.K. if not try to load XP driver with ndisgtk.
(blue led in some laptops will not work or still red but its a minor problem)

This information was taken from forums.


Unfortunately when you reboot your Laptop you can view some wifi's but you will not be able to connect to it. This problem was finally solved, Victor Nieto was written a Script to solve it, I tried it but doesn't work every time I reboot so reading other forums I found a modified script, this script works for me but only if I make the symbolic link in execution level 2 (rc2.d)


first of all here is the Script:

Use an editor and copy-paste this:

#!/bin/bash
sudo modprobe -r ndiswrapper
cp /etc/modprobe.d/blacklist .
sed 's/#blacklist ath_pci/blacklist ath_pci/g' /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist
sudo ndiswrapper -r net5211
sudo ndiswrapper -i /usr/lib/ar5007eg/net5211.inf
sudo ndiswrapper -ma && sudo ndiswrapper -mi
sudo modprobe ndiswrapper
sed 's/blacklist ath_pci/#blacklist ath_pci/g' /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start


save the file as subirwifi (or what else you want)

Copy file into /etc/init.d and change file mode

sudo cp subirwifi /etc/init.d
chmod +x subirwifi

Now we need to make a symbolic link in /etc/rc2.d to load driver before X server starts.
go to /etc/rc2.d

sudo ln -s /etc/init.d/subirwifi S09subirwifi

if all was correct you should see a line like this when you do ls -l

lrwxrwxrwx …………… S09subirwifi -> /ect/init.d/subirwifi

reboot your system and… Luck!!!

I am using this in a Compaq C735EM Laptop with Hardy Heron 64 Bits and works fine (execept blue led)

Thanks to all who contribute to make Linux grow up, and specially to Victor Nieto for the Script.



This is a modification of my previous post on NETWORKING & WIRELESS


I've heard aroubd that MADWIFI has now support for this hardware so be wired ....

---

### Post by be4truth on 2008-06-13
> **daehenoc said:**
> OK, I got my card working with the r3366 patch from madwifi: [http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

I also had trouble for a few days, BECAUSE THE WIFI WAS OFF!!!  Stupid button-press on/off switch on wifi card!!!

Could you be more specific which computer you have and what exactly you did. I can't get my card going with this packet.
thx

---

### Post by misiu369 on 2008-06-14
> **k33bz said:**
> ```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
```

Since madwifi.org is down, could anybody please share the tar.gz?
Would be greatly appreciated...

---

### Post by tim183 on 2008-06-14
I am also looking for a copy of this file??????

---

### Post by williamson389 on 2008-06-14
same here, i think i saw someone uploaded it in one of the threads pertaining to this.

---

### Post by tim183 on 2008-06-14
I've searched everywhere!!!???

---

### Post by tim183 on 2008-06-14
any luck?

---

### Post by blonder on 2008-06-14
[http://muckefuck.sicde.de/kleinesknoppix/madwifi-ng-r2756+ar5007.tar.gz](http://muckefuck.sicde.de/kleinesknoppix/madwifi-ng-r2756+ar5007.tar.gz)

---

### Post by tim183 on 2008-06-14
legend.... thanks

---

### Post by tim183 on 2008-06-14
unfortunately thats not the right version of the patch...

i need the updated file

madwifi-ng-r3366+ar5007.tar.gz

do you have a copy of that as well??

thanks

---

### Post by tim183 on 2008-06-14
I gave it a go and tried to install following the nstructions on the fist page. on reboot i got nothing. so tried again.

tim@tim:~/Program Files/madwifi-ng-r2756+ar5007$ sudo make
[sudo] password for tim: 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/tim/Program Files/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
make[1]: *** No rule to make target `Files/madwifi-ng-r2756+ar5007'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [modules] Error 2
tim@tim:~/Program Files/madwifi-ng-r2756+ar5007$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/tim/Program Files/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
make[1]: *** No rule to make target `Files/madwifi-ng-r2756+ar5007'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [modules] Error 2

any ideas?

---

### Post by mickinator on 2008-06-14
tim183 you need to make sure you have g++ gcc sun-java6-jdk

sudo apt-get install g++ gcc sun-java6-jdk

And when you're making it...

first of all...

make

then 

sudo make

---

### Post by David Benjamin on 2008-06-14
Can anyone share the propper file, because the madwifi.org site is down. :(.

---

### Post by daehenoc on 2008-06-14
> **be4truth said:**
> Could you be more specific which computer you have and what exactly you did. I can't get my card going with this packet.
thx

I have an MSI EX600 (not the -YA edition) and I followed the instructions on the front page almost exactly, with the exception of having to manually remove the ath_hal and ath_pci modules manually ('sudo rmmod ath_pci' and 'sudo rmmod ath_hal') after the first reboot, as these modules were still loaded after the restricted drivers were disabled.  (Even with blacklisting them in the /etc/modprobe.d/blacklist file!)

So my steps were:
1) disable restricted drivers; reboot
2) sudo rmmod ath_(hal|pci)
3) sudo make
4) sudo make install
5) sudo modprobe ath_pci
6) MAKE SURE THE WIRELESS IS TURNED ON!!!

Hope this helps.

p.s. I can download the madwifi file just fine... is madwifi repository up now?

---

### Post by kvcxn on 2008-06-25
After doing this, the monitor mode is not allowed. Is there a way to get it so that it is a valid option?

---

### Post by lynxy on 2008-06-25
> **k33bz said:**
> After alot of toying around trying to find how I can get my wireless working in my Acer Aspire Laptop I came across this post.

The originally post is in German. 

I have place the contents below.



 If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

First make sure of your Network card. But do be careful, for some reason it might report back to being AR5006 or might come up as  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


More than likely if you get either one of those reported back to you it is in fact AR5007.

Run this code in your terminal

```
lspci
```
For i386 Users:

First go to System> Administration-> Hardware Drivers "and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then reboot your system

Preparing your System

Go to System->Administration->Software Sources 
Make sure you have "Universe" & "Multiverse" checked.

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

```
sudo apt-get install build-essential

wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot 
```

That’s it now your wireless should work without any problem.




PROCEDURE FOR UBUNTU HARDY HERON 64 bits USERS
(NEW INFO PROVIDED BY ANDUU FOR YOU 64BIT USERS. GO TO HIS THREAD:[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780") AND THANK BRAVEERUDITE FOR POINTING THIS OUT)

64-bit users please let me know if the above solution works.

Go to System / Administration / hardware drivers and disable all referring to your network card

HAL and support for Atheros Card

 Ensure you have your kernel headers and build the essential package. Use Synaptic or: 


```
sudo aptitude update 

sudo aptitude install linux-headers-$ (uname-r) build-essential

Install ndisgtk.
```

Use Synaptic or: 


```
sudo apt-get install ndisgtk
```

Get 64 bits XP drivers from blakemartin:

```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz 


tar xvf ar5007eg-*.tar.gz tar xvf ar5007eg tar.gz-*.

tar xvf ndiswrapper-newest.tar.gz 
```

Blacklist the default driver 

```
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
```

Load Ndiswrapper and XP driver:

```
sudo ndiswrapper -i net5211.inf Sudo ndiswrapper-i net5211.inf
```

Load up ndiswrapper every time Linux is loaded

```
sudo modprobe ndiswrapper Sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules 
```

Restart your system using the following command Restart your system using the following command

```
sudo reboot 
```

At this point your network card must work OK if not try to load XP driver with ndisgtk.
(blue led in some laptops will not work or still red but its a minor problem)

This information was taken from forums.
 When you reboot your PC in most cases AR5007EG does not work anymore (maybe find networks but can not connect to them)

Victor Nieto has written a script to solve the problem but this script must be executed before X server starts, I tried this and works ok EVERY TIME TURNS YOU ON YOUR PC.

first of all here is the script:
Use an editor and copy-paste this: (pay attention in the 1st. Line in other posts looks like "# bin / bash", correct it)

```
#! bin/bash 
modprobe-r ndiswrapper
cp /etc/modprobe.d/blacklist
sed ’s/#blacklist ath_pci/blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist 
ndiswrapper -ma && sudo ndiswrapper -mi
modprobe ndiswrapper
sed ’s/blacklist ath_pci/#blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist blacklist3 /etc/init.d/networking restart
```

Save the file as subirwifi

Copy file into / etc / init.d and change file mode

```
sudo cp subirwifi /etc/init.d subirwifi
```

Now we need to make a symbolic link in / etc/rc5.d to load driver before X server starts.

Go to / etc/rc5.d

```
sudo ln -s /etc/init.d/subirwifi S09subirwifi
```

if all was correct you should see a line like this when you do ```
ls -l
```

lrwxrwxrwx …………… S09subirwifi -> /ect/init.d/subirwifi 

reboot your system and… Luck!!! 


Thanks to all who contribute to make Linux grow up, and specially to Victor Nieto for the script.
> Atheros 5007 Wifi Chipset Hardy (8.04LTS) Install

I recently purchased an Acer aspire laptop, windows vista installed. Could not connect to internet via wireless connection. I ditched vista and installed Hardy 8.04 lts, hoping to resolve this problem, but no joy until following your instructions for i386 users, and hey presto up and working now..... many thanks...

---

### Post by k33bz on 2008-06-28
> **kvcxn said:**
> After doing this, the monitor mode is not allowed. Is there a way to get it so that it is a valid option?


not that i know of, If anyone out there does, please do post, I would love to be able to put my laptop in monitor mode.

---

### Post by scottro on 2008-06-28
There's a snapshot now, thanks to FreeBSD's Sam Leffler, that works with 64 bit as well. 

I have a page on this, [http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007) with a link to the snapshot.

For what it's worth, Mandriva's Spring 2008 already works in 32 bit out of the box.  The livna-testing fedora repo also works.  So, hopefully, this card will soon become one of the easy ones. 

(This is not to denigrate any of the tutorials above.  My own page is pretty much Fedora oriented, but there is advice for Ubuntu users as well.  The important issue here is the latest snapshot.)

---

### Post by Ketara on 2008-06-30
I'm running 32bit Ubuntu and the above hasn't been working. After doing everything, I can detect wireless networks, but cannot connect to them.

=/

---

### Post by frecel on 2008-07-02
It doesn't work on my toshiba satellite. I don't have ath0 

iwconfig
```

lo         no wireless extnsions.

eth0       no wireless extensions. 

```

Can anybody help me?

---

### Post by cupotka on 2008-07-03
> **mickinator said:**
> tim183 you need to make sure you have g++ gcc sun-java6-jdk

sudo apt-get install g++ gcc sun-java6-jdk

And when you're making it...

first of all...

make

then 

sudo make

I had the same issue with compile errors - thank you very much for this non-trivial addition!

---

### Post by jeffegg2 on 2008-07-14
Compaq Presario C700 with the Atheros 5007 chipset, hardy 8.04LTS install.

I tried these scripts, had no errors, but still no wireless shows up. Any help? using 32 bit. The C700 has Pentium dual core, am I even using the correct version of ubuntu?

thanks...

---

### Post by jeffegg2 on 2008-07-15
> **jeffegg2 said:**
> Compaq Presario C700 with the Atheros 5007 chipset, hardy 8.04LTS install.

I tried these scripts, had no errors, but still no wireless shows up. Any help? using 32 bit. The C700 has Pentium dual core, am I even using the correct version of ubuntu?

thanks...

OK, here is where I am so far. I went to this link: 

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Here I found someone that got the drivers to work with Compaq C700. I had to install the 64 bit 8.04 Ubuntu and followed the instructions at the link.

My wireless now works.... sort of. I can see the wireless, I entered the WEP, and chose auto, and it will not connect. But at least I can see all the wireless that are in range. Now, how come Ubuntu is not using the connection?? I am so close..... Help Please!!!!

---

### Post by cetheriel on 2008-07-19
from [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) comments:
> #  Ignacio Says:
June 27th, 2008 at 9:13 am

A quick note for those without wifi after Ubuntu update.

My cousin had the same problem and we discovered that 2.6.24-19 kernel was the problem. Booting from the previous version (2.6.24-18) solved it. Give it a try!
i didn't try yet, afraid of losing connection, so i just stick with 2.6.24-18, but if anyone updated, try reinstalling the driver (then PLEEEEASE post here for feedback).

---

### Post by jeffegg2 on 2008-07-19
> **jeffegg2 said:**
> OK, here is where I am so far. I went to this link: 

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

Here I found someone that got the drivers to work with Compaq C700. I had to install the 64 bit 8.04 Ubuntu and followed the instructions at the link.

My wireless now works.... sort of. I can see the wireless, I entered the WEP, and chose auto, and it will not connect. But at least I can see all the wireless that are in range. Now, how come Ubuntu is not using the connection?? I am so close..... Help Please!!!!

I finally got everything working.. with my compaq presario c700, I installed the 64 version, and followed the instructions for 64 users. It showed up like the 32 version, then I configured the pp with username and password, I've been online with  the atheros drivers for ever since!!

---

### Post by cetheriel on 2008-07-25
reinstalled, and it works.

---

### Post by tim89 on 2008-07-30
> **jeffegg2 said:**
> I finally got everything working.. with my compaq presario c700, I installed the 64 version, and followed the instructions for 64 users. It showed up like the 32 version, then I configured the pp with username and password, I've been online with  the atheros drivers for ever since!!
I've been having troubles connecting with my Compaq C700 laptop as well. I'm pretty new to linux, so please bear with me.

I have done the 32 bit wireless fixes, but am having the problem where I can see the wireless networks but cant connect.

Did you install the 64 bit version of ubuntu onto a 32 bit machine to get around this problem?

Thanks for any help.

Tim

---

### Post by jeffegg2 on 2008-08-02
> **tim89 said:**
> I've been having troubles connecting with my Compaq C700 laptop as well. I'm pretty new to linux, so please bear with me.

I have done the 32 bit wireless fixes, but am having the problem where I can see the wireless networks but cant connect.

Did you install the 64 bit version of ubuntu onto a 32 bit machine to get around this problem?

Thanks for any help.

Tim

Yes, I installed the amd64 version. I have dual core, so perhaps that is the correct version? I don't know, just that it now works... and I am also new... the Ubuntu 8.04 amd64 is the only operating system on my compac presario c700.

---

### Post by cetheriel on 2008-08-02
64bit is not the same thing as dual-32bit...

---

### Post by cetheriel on 2008-08-10
atheros offer drivers for linux, hope this means good news to us all...
[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

---

### Post by money2themax on 2008-08-10
is there a version of this for 7.10 and the x86 ver cuz i can't get anything to work and i'm getting really frustrated

---

### Post by kaffeboy on 2008-08-22
hey guys...I'm running 32 bit Ubuntu on a Compaq Presario c700 (c776nr, to be exact) and I follow the steps on the 32 bit config but I'm stuck at the **"Sudo Make"**  command. It says there is no makefile. What am I doing wrong. Last night I was up until 3:00am trying to figure out what I was doing. Cartoon Cat from the IRC Ubuntu chat helped me, but we were going nowhere fast...:confused:

I'm afraid to have to wipe out the disk and do a fresh install of 64 bit Ubuntu just to get wireless to work on my laptop. I'll give it one last try if you guys can suggest something. Thanks in advance. :KS
[I]

I'm on a Compaq Presario c776nr 1.86Ghz Intel Dual Core 3GB of RAM. I'm running 8.04 - 32 bit. [/I]

---

### Post by scottro on 2008-08-22
This card will be supported out of the box on the 2.6.27 kernels.  (It's working with the ath5k driver on Fedora Rawhide.)

At any rate, did you type sudo Make or sudo make?  You need the lower case m, not an upper case one.

---

### Post by kaffeboy on 2008-08-23
I typed lower case in all my terminal needs...\\:D/

---

### Post by kaffeboy on 2008-08-23
Update: I have wiped out my Ubuntu and reinstalled the 64 bit version. I need detailed instructions so I don't go around in circles. Should I use the one Jeff sent in or the one at the beginning of the thread?:KS

---

### Post by gizmoarena on 2008-08-26
How to check if my wifi is working or not?

If I use ndiswrapper, Wireless option appears in "Network", besides iwconfig and ifconfig shows the wireless interface.

Now (after following this how to) nothing appears anywhere. Only the manual network configuration icon shows Edit wireless network. Thats all.

Thanks.

EDIT: I am using ubuntu hardy on acer aspire 4715z.

---

### Post by scrobby4 on 2008-08-27
Hi, everyone,

    I have just purchased an HP dv5 1002nr with AMD 64 processor. I am currently using Ubuntu Hardy 8.04 with Kernel Linux 2.6.24-19 generic and Gnome 2.22.3. I am not an expert in Linux or Ubuntu, just started using it this summer. 
    I spent a couple of days trying many different solutions using mad-wifi and other drivers until I found this thread. I did the procedure in the first post for this thread and it worked fine for standard wifi without security. I hope this serves as a reference for other users of this same laptop model.
    However, for my wireless with WPA enabled, it does not work. Ubuntu simply halts, which is something I would only expect from Windows. I probably am doing something very wrong, but do not know what. If anyone has succeeded in accessing security enabled networks with Hardy and 64-bit processors, please let me know.
    Thanks,

---

### Post by cetheriel on 2008-08-27
can you see the "create new wireless network"option?
are you near a wi-fi router?

---

### Post by kaffeboy on 2008-08-28
Reinstalled 32bit Ubuntu...nothing is working.

---

### Post by Minteh on 2008-08-31
I've been wrestling with my AR5007 and 8.04 for a day or two now, and the closest I've got was a function card that stopped functioning when I restarted :(

I could restart functionality by re-modprobing the two mod (ath_pci, wlan_scan_sta) but I had to do this every login. So, I tried putting a simple script to do that for me in init.d, restarted and now nothing works xD (E.g. doesn't work automatically, doesn't work re-modprobing).

So I'm going to take the Windows root and reinstall and try again :D Maybe it'll work properly this time :)

---

### Post by scottro on 2008-08-31
I'm tempted to say if you're going to reinstall the whole thing anyway, go with Intrepid Ibex, and while wirelessly connected, do the latest updates which should bring you the 2.6.27 kernel.  That kernel's ath5k module supports most versions of the AR5007EG card.  (On the other hand, it's taken away the sysctl variable for the LED lights, and I haven't found their new name yet--that's not Ubuntu, that's the 2.6.27 kernel itself, even a vanilla one.)

Oops, I write while wirelessly connected, I meant while connected with wired Internet.

---

### Post by Desumancer on 2008-09-02
The instructions worked for me on my HP dv5z. Ubuntu can detect my Atheros wifi card and can connect to unsecured wireless connections, but not so on the secured wireless ones like mine sadly. When I try to connect to my wireless connection it asks for my password then tries to connect for a while but then just goes back to asking for my password.

  Any help on the last part would be appreciated but I'm still happy that I can actually browse the internet with Ubuntu at this point. So thanks to the OP... :)

---

### Post by money2themax on 2008-09-04
i try to contact Atheros and they gave me this "insightful information":

```

Thank you for your interest in products containing Atheros Communications' technology.

However, we do not offer the WiFi card or end-user tech support that you're inquiring about.
Atheros typically sells chips to module manufacturers and therefore would not be able to help you with this task.
For issues regarding configuration and usage of your product, please contact Compaq's technical support department.
We suggest you refer to Compaq's website, as they typically offer online technical support pages where software drivers, updates, and other related information can be obtained.

Thank you for your understanding.
Atheros Communications, Inc.

```

---

### Post by kaffeboy on 2008-09-05
Like contacting Compaq will help!?!
Compaq doesn't even offer support for Windows XP. Now what would make you think they'd offer support on this. I think I'll let Atheros know a piece of my mind! ](*,):twisted:

---

### Post by money2themax on 2008-09-05
you do that but i doubt it will help any

---

### Post by alfaifi on 2008-09-07
THAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANX

U R THE BEST

i tried many many ways but yours is the only one that worked for me

just notice that the tar ball link changed

---

### Post by money2themax on 2008-09-07
i've got it working but i want the light to change right now it stays amber but the button works

---

### Post by be4truth on 2008-09-07
> **alfaifi said:**
> THAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANX

U R THE BEST

i tried many many ways but yours is the only one that worked for me

just notice that the tar ball link changed

Hi, would you mind to be a bit more verbose? Maybe a "U R THE BEST" -v?
What did work for you and which link did you use?
Thx
:)

---

### Post by LuisPT on 2008-09-12
A new HAL has been made available by Sam Leffler (0.10.5.6) that supports AR2425 chips (AR5007* chipsets).

This is a full HAL release so it should work for all platforms - that means x86-64.
You can download the full HAL from [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)


But, my previous instalations worked much better with the patch madwifi-ng-r3366+ar5007.tar.gz.

This patch ([h**p://snapshots.madwifi.org/special/madwifi-ng-**r3366**+ar5007.tar.gz) is no longer available at madwifi site.


Could anybody provide a link to a copy of madwifi-ng-**[COLOR="Blue"]r3366[/COLOR]**+ar5007.tar.gz 



This is very important. Thanks in advance.

---

### Post by LuisPT on 2008-09-12
Jesus, I've just found a link for madwifi-ng-r3366+ar5007.tar.gz  

Grab this patch before it goes away.

**[Download madwifi-ng-r3366+ar5007 HERE]("http://eeedora.googlecode.com/svn-history/r160/trunk/generate-rpms/madwifi/madwifi-ng-r3366+ar5007.tar.gz")**

Hope it will help you also.

---

### Post by scottybee on 2008-09-12
This atheros chipset is driving me nuts:(

Please could someone point me in the right direction. Just scratching me head constantly and no its not nits.
Just recently installed 32bit ubuntu hardy on compaq presario a910em all working out of the box except wireless. Tried ndiswrapper no joy. Removed the hal within restricted drivers, rebooted and downloaded latest madwifi when doing the install make command this errors saying cannot stat `ath_pci.ko. 

Please be easy on me only starting to get to grips with linux.

Many Thanks

Scottybee :)

---

### Post by LuisPT on 2008-09-12
> **scottybee said:**
> This atheros chipset is driving me nuts:(

Please could someone point me in the right direction. Just scratching me head constantly and no its not nits.
Just recently installed 32bit ubuntu hardy on compaq presario a910em all working out of the box except wireless. Tried ndiswrapper no joy. Removed the hal within restricted drivers, rebooted and downloaded latest madwifi when doing the install make command this errors saying cannot stat `ath_pci.ko. 

Please be easy on me only starting to get to grips with linux.

Many Thanks

Scottybee :)


Procedures are below:


1. Go to System > Administration > Hardware Drivers

2. Disable the following options:

- Atheros Hardware Access Layer (HAL)
- Support for Atheros 802.11 wireless LAN cards (in some cases this one is not necessary to disable)

3. Download this Driver Patch from **[HERE]("http://eeedora.googlecode.com/svn-history/r160/trunk/generate-rpms/madwifi/madwifi-ng-r3366+ar5007.tar.gz")** 

4. Reboot your system

5. After reboot, open a terminal and issue the following:

sudo apt-get install build-essential

tar xfz madwifi-ng-r3366+ar5007.tar.gz *(this comand has to be issue in the same folder where you downloaded the file from point nr. 3)*

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci


6. Done! If everything went well, your wi-fi is ready to use!

In order to verify it, you can issue the following:

ifconfig wifi0


Hope it works for you :KS

---

### Post by LuisPT on 2008-09-12
> **Minteh said:**
> I've been wrestling with my AR5007 and 8.04 for a day or two now, and the closest I've got was a function card that stopped functioning when I restarted :(

I could restart functionality by re-modprobing the two mod (ath_pci, wlan_scan_sta) but I had to do this every login. So, I tried putting a simple script to do that for me in init.d, restarted and now nothing works xD (E.g. doesn't work automatically, doesn't work re-modprobing).

First of all, delete the script you had put on init.d :lolflag:

Do this instead:
# sudo gedit /etc/modules

Add the following at a new line of the file!
“ath_pci” (Without quotes)

Save and exit!

---

### Post by LuisPT on 2008-09-12
Instead of use this guide [HERE]("http://ubuntuforums.org/showpost.php?p=5774374&postcount=72") you can also use this procedure:

Since MadWiFi drivers updates quite often, it's better to use and compile the last one, so:

(Do this as ROOT or use SUDO before each command):
> sudo wget h++p://snapshots.madwifi.org/madwifi-trunk-current.tar.gz  ->(replace h++p for http)
sudo tar -xzf mad*.tar.gz
sudo cd madwifi-trunk-r*
sudo cd scripts
sudo ./madwifi-unload
Note: the laste line, just unload thw wifi drivers.


Let´s continue (as root):

> cd ..
make
sudo make install
sudo modprobe ath_pci

Compilation and Instalation has finished :popcorn:

Additionally do this:
> sudo gedit /etc/modules
and add the following at a new line of the file!
&#8220;ath_pci&#8221; (Without quotes)
Save and Exit!



I recommend you to reboot now! 

sudo shutdown -r now



Hope it works for you ):P

---

### Post by lee1019 on 2008-09-12
Thank you so very much. I already had that software installed but I guess having the HAL on hinders everything

---

### Post by scottybee on 2008-09-12
:popcorn:hooray got it working with no security on it.
just need to set it up with my wep key etc

With Thanks

Scottybee:)

---

### Post by scottybee on 2008-09-12
:( hmmm
my router uses a wep 128 passphrase used the key and nothing?](*,)
any ideas?

nearly aswell

---

### Post by manav_1001 on 2008-09-19
> **LuisPT said:**
> Procedures are below:


1. Go to System > Administration > Hardware Drivers

2. Disable the following options:

- Atheros Hardware Access Layer (HAL)
- Support for Atheros 802.11 wireless LAN cards (in some cases this one is not necessary to disable)

3. Download this Driver Patch from **[HERE]("http://eeedora.googlecode.com/svn-history/r160/trunk/generate-rpms/madwifi/madwifi-ng-r3366+ar5007.tar.gz")** 

4. Reboot your system

5. After reboot, open a terminal and issue the following:

sudo apt-get install build-essential

tar xfz madwifi-ng-r3366+ar5007.tar.gz *(this comand has to be issue in the same folder where you downloaded the file from point nr. 3)*

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci


6. Done! If everything went well, your wi-fi is ready to use!

In order to verify it, you can issue the following:

ifconfig wifi0


Hope it works for you :KS

Hi,

I followed your steps until step 5. after that when i enter the command "tar xfz madwifi-ng-r3366+ar5007.tar.gz" i get an error saying:-
tar: madwifi-ng-r3366+ar5007.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can you please tell me what i'm doing wrong?
Thanks.

---

### Post by manav_1001 on 2008-09-19
> **k33bz said:**
> After alot of toying around trying to find how I can get my wireless working in my Acer Aspire Laptop I came across this post.

The originally post is in German. 

I have place the contents below.



 If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

First make sure of your Network card. But do be careful, for some reason it might report back to being AR5006 or might come up as  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


More than likely if you get either one of those reported back to you it is in fact AR5007.

Run this code in your terminal

```
lspci
```
For i386 Users:

First go to System> Administration-> Hardware Drivers "and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then reboot your system

Preparing your System

Go to System->Administration->Software Sources 
Make sure you have "Universe" & "Multiverse" checked.

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

```
sudo apt-get install build-essential

wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot 
```

That’s it now your wireless should work without any problem.


Hi,

I was following your steps but after i enter the command sudo make i get an error saying:-

make: *** No targets specified and no makefile found.  Stop.

Can you please tell me what i'm doing wrong?
Thanks.

---

### Post by cetheriel on 2008-09-19
something went wrong when you ran the untar command. did you run it ok? i mean, were you on the right folder, and was the madwifi-ng-r2756+ar5007 subfolder created?

---

### Post by manav_1001 on 2008-09-21
Finally I've got it working.
Now is there any way of enabling monitor mode?

---

### Post by scottybee on 2008-09-22
:popcorn:

Thanks to all those who helped.
The wireless is now all working fine, re-configured my wireless router and security, bingo!!!!

Thanks Again

scottybee

---

### Post by eeeandrew on 2008-09-22
hi guys, thanks for a great how to. I installed the drivers on a 32 bit system this afternoon. I had one small problem tho. After I ran updates(it was a brand new install) the wifi stopped working. Running the make and sudo make install commands seemed to work but entering the modprobe ath_pci made the indicator lights flash and the laptop freeze. I'm assuming this is due to the kernel updates that ran. I reinstalled the original Kernel from the live CD and got it working again. Could anyone advise me on which kernels this card currently works with and how to get drivers for future versions? My laptop is a Toshiba Equium L40-10X. I followed the post from Luis PT on page 8.

who dares wins,
Andrew

---

### Post by smooth3006 on 2008-10-04
be aware i think this guide needs to be update as madwifi-ng-r2756+ar5007.tar.gz isn't a valid tar anymore. it only gives you a readme file in the folder and no makefile.

---

### Post by kvcxn on 2008-10-04
> **manav_1001 said:**
> Finally I've got it working.
Now is there any way of enabling monitor mode?

I was having trouble putting it into monitor mode as well.

The following method didn't work for me:

```
 
ifconfig ath0 down
iwconfig ath0 mode monitor
ifconfig ath0 up

```


But I found recreating the interface to work:

```
 
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up

```

To put it back to the mode it was in (managed):

```
 
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0
ifconfig ath0 up

```

And of course, replace ath0 and wifi0 with your interface names. 

I suppose instead of destroying ath0 and recreating it, you can create ath1 or something under monitor mode and use that, but I've just never tried it. I put those commands in a script instead.

Hope this works for people having trouble putting it into monitor mode.

---

### Post by smooth3006 on 2008-10-04
i got the wireless working now but i cant get my wireless led indicator and switch to work on my hp laptop. can anybody help ?

---

### Post by smooth3006 on 2008-10-19
> **smooth3006 said:**
> i got the wireless working now but i cant get my wireless led indicator and switch to work on my hp laptop. can anybody help ?

anybody ?

---

### Post by scottro on 2008-10-19
On Hardy or on Intrepid?  With Intrepid, I don't know of a way to do it.  The sysctl options in the 2.6.26 kernel are gone from the 2.6.27 kernel and I haven't found another way to do it. (This isn't just Ubuntu, it holds for the vanilla 2.6.27 kernel as well.)

In Hardy you should be able to do

sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

That should work.

---

### Post by smooth3006 on 2008-10-19
> **scottro said:**
> On Hardy or on Intrepid?  With Intrepid, I don't know of a way to do it.  The sysctl options in the 2.6.26 kernel are gone from the 2.6.27 kernel and I haven't found another way to do it. (This isn't just Ubuntu, it holds for the vanilla 2.6.27 kernel as well.)

In Hardy you should be able to do

sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

That should work.

do i just add those lines to it ?

---

### Post by smooth3006 on 2008-10-19
i tried your method and it did nothing. im not talking about the led blinking when connected to a wifi network. im talking about the led that turns blue when i have the wifi kill switch on the "on" position. i cant even get the kill switch to work at all ? i do have the wifi working and it picks up networks though. i heard a rumor that 8.10 will allow the leds to work "out of the box" ? i was just hoping there may be a solution for this in the meantime. i know this isn't a hardware issue because it worked when i had vista installed.

---

### Post by scottro on 2008-10-19
My apologies, I misunderstood.  The sysctl options are only for the wifi light blinking.  

Sorry.

I'm using Intrepid on an Aspire One and I get no LED's at all, so I don't know about that (that they should work out of the box.)  On the other hand, I've done little searching about it.

---

### Post by smooth3006 on 2008-10-19
> **scottro said:**
> My apologies, I misunderstood.  The sysctl options are only for the wifi light blinking.  

Sorry.

I'm using Intrepid on an Aspire One and I get no LED's at all, so I don't know about that (that they should work out of the box.)  On the other hand, I've done little searching about it.

im just wondering why i can't get my wifi killswitch to work at all ?

---

### Post by kaffeboy on 2008-10-20
Whats funny is that PC-BSD 7 is fully supporting this card out of the box. The bad thing is that PC-BSD is still very much unstable and hard to use, with KDE 4 and all.

I want to know for sure if this card will be supported out of the box in Intrepid, since I've tried this how-to and it didn't work and I'm getting SICK of Vista.

---

### Post by kmresh on 2008-10-20
> **k33bz said:**
> After alot of toying around trying to find how I can get my wireless working in my Acer Aspire Laptop I came across this post.

The originally post is in German. 

I have place the contents below.



 If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

First make sure of your Network card. But do be careful, for some reason it might report back to being AR5006 or might come up as  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


More than likely if you get either one of those reported back to you it is in fact AR5007.

Run this code in your terminal

```
lspci
```
For i386 Users:

First go to System> Administration-> Hardware Drivers "and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then reboot your system

Preparing your System

Go to System->Administration->Software Sources 
Make sure you have "Universe" & "Multiverse" checked.

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

```
sudo apt-get install build-essential

wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot 
```

That’s it now your wireless should work without any problem.




PROCEDURE FOR UBUNTU HARDY HERON 64 bits USERS
(NEW INFO PROVIDED BY ANDUU FOR YOU 64BIT USERS. GO TO HIS THREAD:[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780") AND THANK BRAVEERUDITE FOR POINTING THIS OUT)

64-bit users please let me know if the above solution works.

Go to System / Administration / hardware drivers and disable all referring to your network card

HAL and support for Atheros Card

 Ensure you have your kernel headers and build the essential package. Use Synaptic or: 


```
sudo aptitude update 

sudo aptitude install linux-headers-$ (uname-r) build-essential

Install ndisgtk.
```

Use Synaptic or: 


```
sudo apt-get install ndisgtk
```

Get 64 bits XP drivers from blakemartin:

```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz 


tar xvf ar5007eg-*.tar.gz tar xvf ar5007eg tar.gz-*.

tar xvf ndiswrapper-newest.tar.gz 
```

Blacklist the default driver 

```
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
```

Load Ndiswrapper and XP driver:

```
sudo ndiswrapper -i net5211.inf Sudo ndiswrapper-i net5211.inf
```

Load up ndiswrapper every time Linux is loaded

```
sudo modprobe ndiswrapper Sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules 
```

Restart your system using the following command Restart your system using the following command

```
sudo reboot 
```

At this point your network card must work OK if not try to load XP driver with ndisgtk.
(blue led in some laptops will not work or still red but its a minor problem)

This information was taken from forums.
 When you reboot your PC in most cases AR5007EG does not work anymore (maybe find networks but can not connect to them)

Victor Nieto has written a script to solve the problem but this script must be executed before X server starts, I tried this and works ok EVERY TIME TURNS YOU ON YOUR PC.

first of all here is the script:
Use an editor and copy-paste this: (pay attention in the 1st. Line in other posts looks like "# bin / bash", correct it)

```
#! bin/bash 
modprobe-r ndiswrapper
cp /etc/modprobe.d/blacklist
sed ’s/#blacklist ath_pci/blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist 
ndiswrapper -ma && sudo ndiswrapper -mi
modprobe ndiswrapper
sed ’s/blacklist ath_pci/#blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist blacklist3 /etc/init.d/networking restart
```

Save the file as subirwifi

Copy file into / etc / init.d and change file mode

```
sudo cp subirwifi /etc/init.d subirwifi
```

Now we need to make a symbolic link in / etc/rc5.d to load driver before X server starts.

Go to / etc/rc5.d

```
sudo ln -s /etc/init.d/subirwifi S09subirwifi
```

if all was correct you should see a line like this when you do ```
ls -l
```


lrwxrwxrwx …………… S09subirwifi -> /ect/init.d/subirwifi 

reboot your system and… Luck!!! 


Thanks to all who contribute to make Linux grow up, and specially to Victor Nieto for the script.


Thank you!!
 
Am using acer aspire one ZG5 Model. what driver i can install to my aspire one.and how to install that

please help me

---

### Post by smooth3006 on 2008-10-20
> **kaffeboy said:**
> Whats funny is that PC-BSD 7 is fully supporting this card out of the box. The bad thing is that PC-BSD is still very much unstable and hard to use, with KDE 4 and all.

I want to know for sure if this card will be supported out of the box in Intrepid, since I've tried this how-to and it didn't work and I'm getting SICK of Vista.

i heard 8.10 will support it as well as finally getting the led and kill switches to work ? i know mandriva 2009 supports the card with no 3rd party driver needed but the led doesn't work still. it can't be that hard to get the led to light up and the switch to work, i mean if the built in card works why not the lights or switch ? makes zero sense to me at all. :mad:

i may just buy one of those usb wifi adapters to be sure my wifi will work.

---

### Post by kaffeboy on 2008-10-23
So youre saying that I should try Ubuntu 8.10?

Right now, Im on Mandriva 2009. Its a good distro, but Ubuntu was always my first love. And you know how it is.

Okay, its settled. Im going to install Intrepid as soon as it comes out. Hopefully, this will be resolved by then.

Has anyone tried the beta?! Has it worked?

---

### Post by kaffeboy on 2008-11-01
Fixed...
Ubuntu 8.10 Intrepid Ibex currently supports this card. Hooray!:popcorn:

---

### Post by mngsailing on 2008-11-28
The insturctions in your second code panel  
sudo make 
and 
sudo make install 
do not work for me.  They seem to be incomplete.

That makes this another dead-end in my search to get my wireless to work.
  
mngsailing



> **k33bz said:**
> After alot of toying around trying to find how I can get my wireless working in my Acer Aspire Laptop I came across this post.

The originally post is in German. 

I have place the contents below.



 If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

First make sure of your Network card. But do be careful, for some reason it might report back to being AR5006 or might come up as  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


More than likely if you get either one of those reported back to you it is in fact AR5007.

Run this code in your terminal

```
lspci
```
For i386 Users:

First go to System> Administration-> Hardware Drivers "and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then reboot your system

Preparing your System

Go to System->Administration->Software Sources 
Make sure you have "Universe" & "Multiverse" checked.

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

```
sudo apt-get install build-essential

wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot 
```

That’s it now your wireless should work without any problem.




PROCEDURE FOR UBUNTU HARDY HERON 64 bits USERS
(NEW INFO PROVIDED BY ANDUU FOR YOU 64BIT USERS. GO TO HIS THREAD:[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780") AND THANK BRAVEERUDITE FOR POINTING THIS OUT)

64-bit users please let me know if the above solution works.

Go to System / Administration / hardware drivers and disable all referring to your network card

HAL and support for Atheros Card

 Ensure you have your kernel headers and build the essential package. Use Synaptic or: 


```
sudo aptitude update 

sudo aptitude install linux-headers-$ (uname-r) build-essential

Install ndisgtk.
```

Use Synaptic or: 


```
sudo apt-get install ndisgtk
```

Get 64 bits XP drivers from blakemartin:

```
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz 


tar xvf ar5007eg-*.tar.gz tar xvf ar5007eg tar.gz-*.

tar xvf ndiswrapper-newest.tar.gz 
```

Blacklist the default driver 

```
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
```

Load Ndiswrapper and XP driver:

```
sudo ndiswrapper -i net5211.inf Sudo ndiswrapper-i net5211.inf
```

Load up ndiswrapper every time Linux is loaded

```
sudo modprobe ndiswrapper Sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules 
```

Restart your system using the following command Restart your system using the following command

```
sudo reboot 
```

At this point your network card must work OK if not try to load XP driver with ndisgtk.
(blue led in some laptops will not work or still red but its a minor problem)

This information was taken from forums.
 When you reboot your PC in most cases AR5007EG does not work anymore (maybe find networks but can not connect to them)

Victor Nieto has written a script to solve the problem but this script must be executed before X server starts, I tried this and works ok EVERY TIME TURNS YOU ON YOUR PC.

first of all here is the script:
Use an editor and copy-paste this: (pay attention in the 1st. Line in other posts looks like "# bin / bash", correct it)

```
#! bin/bash 
modprobe-r ndiswrapper
cp /etc/modprobe.d/blacklist
sed ’s/#blacklist ath_pci/blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist 
ndiswrapper -ma && sudo ndiswrapper -mi
modprobe ndiswrapper
sed ’s/blacklist ath_pci/#blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist blacklist3 /etc/init.d/networking restart
```

Save the file as subirwifi

Copy file into / etc / init.d and change file mode

```
sudo cp subirwifi /etc/init.d subirwifi
```

Now we need to make a symbolic link in / etc/rc5.d to load driver before X server starts.

Go to / etc/rc5.d

```
sudo ln -s /etc/init.d/subirwifi S09subirwifi
```

if all was correct you should see a line like this when you do ```
ls -l
```

lrwxrwxrwx …………… S09subirwifi -> /ect/init.d/subirwifi 

reboot your system and… Luck!!! 


Thanks to all who contribute to make Linux grow up, and specially to Victor Nieto for the script.

---

### Post by isuck@linux on 2008-12-19
do u need an internet connection for:

*sudo apt-get install build-essential*

to work because my computer always says there is an error

---

### Post by sdegrace on 2009-03-01
NOTE: If you're trying the find the madwifi files, I know what happened to them. It seems like the Madwifi project moved without leaving a forwarding address on their original webpage. If you replace madwifi.org with madwifi-project.org in your wget commands, you'll get the files no prob.

I have a new HP G50 laptop and I'm running 8.10. I tried 8.04 when I couldn't get the wireless wot work on Intrepid, since all the directions out there seem to be for Hardy, but this laptop is really badly supported by Hardy, when you try to install the proprietary nVidia drivers, you get perpetual blank screen, and it seems to be having problems with the sound card, too. Intrepid is perfect, except for the one flaw of the wireless not being correctly supported. Since discovering the fate of madwifi.org I decided to put on Intrepid again and try this again, this time without using skeezy files I found in random internet hidey-holes ;).

But anyway, I have found that the wireless card is definitely not working out of the box for me in 8.10. I'll let you know if I do get it to work.

Stephen

---

### Post by sdegrace on 2009-03-01
If you're using Intrepid, follow the directions here:

[http://ubuntuforums.org/showthread.php?t=1076466](http://ubuntuforums.org/showthread.php?t=1076466)

I found the answer originally here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937)

My wireless works perfectly now - I'm posting from it! Much, much easier than getting this card working with Hardy, although it was very hard to find the right answer and I spent a lot of useless time mucking about with madwifi until I got it.

---

### Post by peoplenamed on 2009-04-02
SOLVED!! just install the newest version of ubuntu!! Jaunty jackalope 9.04 MID it works right out of the box im running a pavilion dv7 with atheros 5007 i havent even completed instaling! its at 99% right now! if only it would recognize my ati radeon hd 3200 graphics card.. i havent checked yet but i can download the latest driver from the site anyway..

---

