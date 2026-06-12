---
title: "HOWTO: Latest Madwifi driver"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by kleeman on 2005-05-24
My Wireless laptop card is a DWL-G650 (d-link) which was supposed to work with
the madwifi drivers in hoary but did not because the firmware is too new. So I decided to manually install the drivers. Here is my (rough) howto.

WARNING: If you are uncomfortable with manipulating kernel modules or at all unfamiliar with such concepts do not use this HOWTO. In addition this is bleeding edge software and as such may not work as advertised. You have been warned!
It is worth pointing out that ndiswrapper often works with atheros chipsets and should be preferred if the above applies to you. For a howto on this see, for example,

[http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)


0) Install the basic development  packages for Ubuntu (see another HOWTO) 

1) Install the linux-headers package for your kernel. Make sure carefully that the headers package you install correspond with your version of the kernel you have installed. So I have linux-image-2.6.10-5-686-smp installed so I installed linux-headers-686-smp as well as linux-headers-2.6.10-5-686-smp

2) Install the linux-source package and set up (If not already done):
cd /usr/src
sudo tar jxvf linux-source-2.6.10.tar.bz2
ln -s linux-source-2.6.10.tar.bz2 linux

3) Install the sharutils package
 
4) Grab the latest madwifi source tarball from here
[http://madwifi.otaku42.de/madwifi-cvs-current.tar.bz2](http://madwifi.otaku42.de/madwifi-cvs-current.tar.bz2)
and decompress
tar jxvf madwifi-cvs-current.tar.bz2

4)a As of mid July it looks like they have changed the driver  ](*,)  so instead download and uncompress 

[http://madwifi.otaku42.de/2005/07/madwifi-cvs-snapshot-2005-07-01.tar.bz2](http://madwifi.otaku42.de/2005/07/madwifi-cvs-snapshot-2005-07-01.tar.bz2)

5) Go into the madwifi directory created by step 4) and type
sudo make clean
sudo make
sudo make install

6) All going well  ;-) you should now have the drivers in
/lib/modules/2.6.10 (a new subdirectory) but now you need to replace the existing drivers. These are in four places:

Assuming you have the standard kernel installed (2.6.10-5-386) they are:

/lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath/ath_pci.ko
/lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath_hal/ath_hal.ko
/lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
/lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/net80211/wlan*.ko (TOTAL of six files here)

A total of 9 files in all which should be the number of files in /lib/modules/2.6.10
(Note if you use the  2.6.10-5-686-smp kernel replace 2.6.10-5-386 with 2.6.10-5-686-smp in the paths above)

So now all you do is replace  all the first 9 files with the corresponding new files in /lib/modules/2.6.10. As an example 
sudo cp /lib/modules/2.6.10/ath_pci.ko /lib/modules/2.6.10-5-386//kernel/drivers/net/wireless/ath/ath_pci.ko

and so on .....

reboot and the madwifi drivers will now hopefully work as expected. See
[http://www.ubuntulinux.org/wiki/WiFiWithSomeoneElsesRouterHowTo](http://www.ubuntulinux.org/wiki/WiFiWithSomeoneElsesRouterHowTo)
Step 0) for further instructions....

You can now trash ndiswrapper Yay!

One downside to all this is that everytime a new kernel is installed all this needs repeating (groan). Of course breezy will have the latest madwifi driver  ;-)  ;-)

---

### Post by RastaMahata on 2005-05-24
whats the difference between ndiswrapper and madwifi? :(

---

### Post by benplaut on 2005-05-24
[QUOTE=RastaMahata]whats the difference between ndiswrapper and madwifi? :([/QUOTE]

madwifi is a native driver for wireless cards with the Atheros chipset

ndiswrapper is a "quick-fix" for cards that have no linux drivers... it is a compatibility layer to use windows drivers in linux 

 :razz:

---

### Post by RastaMahata on 2005-05-24
[QUOTE=benplaut]madwifi is a native driver for wireless cards with the Atheros chipset

ndiswrapper is a "quick-fix" for cards that have no linux drivers... it is a compatibility layer to use windows drivers in linux 

 :razz:[/QUOTE]
 great to know! Any tips then on buying a laptop? So it's easy to have wifi configured?

---

### Post by kleeman on 2005-05-25
Well I thought I was being smart by buying a D-Link DWL G650 because the list on the Ubuntu wiki said it was supported. The problem is that the manufacturers are constantly changing things (hardware/software) so it is a moving target. Very frustrating!!! ](*,)  ](*,)

---

### Post by sfc_bugger on 2005-05-25
Roger that!! I did lots of shopping and returning of cards before I finally got one to work, two actually, one is a Proxim 8410, which actually has the good old Luncent chipset, works out of the box in 12 different distros and every live CD I've ever run, great for war driving with a knoppix STD live cd. The other card is a Proxim 8480 that is Atheros based, worked first time out with Ubuntu and Mepis 3.3.x ---->>>>NOT IN THE TERRIBLE LIBRANET 3 though!! Have had mixed success with WPA in any distro. Bottom line: SHOP, SHOP, SHOP, make sure you look at the revision # of the chipset(should be on the cards box, or check with the vendors support folks, and look through every forum post possible prior to making the buy. NDISwrappers is a nice package, but generally you dont get the full attributes of the card when you use it (IMHO); Microsoft friendly vendors change chipsets all the time!!!

---

### Post by cwestpha on 2005-05-25
What basic development packages are you talking about exactly? every different program has the potential for different development prerequsets. Personaly I just used the WINE stuff and am hoping that is going to work.

---

### Post by kleeman on 2005-05-25
I was thinking:
sudo apt-get install build-essential

---

### Post by cwestpha on 2005-05-25
[QUOTE=kleeman]I was thinking:
sudo apt-get install build-essential[/QUOTE]
oooohhh...
*bangs his head into the wall a few times*

Ok that was a stupid question.

---

### Post by jdong on 2005-05-25
guys, please stay on topic (installing Madwifi drivers, problems with the steps outlined in this howto, etc).

Though it's OK to go off-tangent sometimes in the Community Chat, doing so in a HOWTO article usually leads to one of those 50 page messes commonly found on Gentoo forums and Slashdot ;)

---

### Post by cwestpha on 2005-05-25
I do everything stated but I get the fallowing back:
```
root@I8000:/home/ # modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Any ideas?

---

### Post by jdong on 2005-05-25
Post output to the **dmesg** command.

 
this HOWTO seems unsafe and incorrect. Compiling against the raw Ubuntu source tree doesn't necessarily mean the binary modules will be compatible with the various Ubuntu kernel.
 
For example, a module for the i386 kernel will not insert into an i686 kernel, and so on.
 
You should really compile against your correct version of **linux-headers ,** such as **linux-headers-k7**. 
 
to the author: I **highly recommend you redo your howto using this method, instead.**

---

### Post by cwestpha on 2005-05-25
[QUOTE=jdong]Post output to the **dmesg** command.

 
this HOWTO seems unsafe and incorrect. Compiling against the raw Ubuntu source tree doesn't necessarily mean the binary modules will be compatible with the various Ubuntu kernel.
 
For example, a module for the i386 kernel will not insert into an i686 kernel, and so on.
 
You should really compile against your correct version of **linux-headers ,** such as **linux-headers-k7**. 
 
to the author: I **highly recommend you redo your howto using this method, instead.**[/QUOTE]
 I am a newbie... so how would I do that exactly? (hay atleast I could modprobe without help)

---

### Post by jdong on 2005-05-25
Just skip step two. If you already did it, do an **rm -f /usr/src/linux** to remove that symlink. It's simply not necessary. Madwifi's Makefile may have to be edited to reflect the /lib/modules/KERNELVERSIONS/build (or /include) directories, but I'll turn that back over to the HOWTO author, as I don't use Madwifi.

---

### Post by kleeman on 2005-05-25
I have edited the howto to make sure that the correct headers packages are installed. If this does not work let me know. I use the 686-smp kernel with the corresponding packages and had no problems and did not need to edit the makefile. Let me know if you have problems like that described what your kernel version is exactly (do uname -a to find out) and which kernel headers you have installed.

---

### Post by kleeman on 2005-05-25
To cwestpha: Are you sure you copied all 9 files into your /lib/modules directory structure as outlined in the howto? Your error message doesn't sound like a version conflict as suggested by jdong, it sounds more like the module is missing helper applications i.e. other modules. However just to make sure check carefully that your kernel package matches your kernel headers package (step 1 in the reedited howto).

---

### Post by Sniper PT on 2005-07-21
What i have did:
0) sudo apt-get install build-essential
1) sudo apt-get install linux-headers-2.6.10-5 and sudo apt-get install linux-headers-2.6.10-5-386
2) i don't have the file in /usr/src folder, so i **only** have copy the folder (in ubuntu CD) /pool/main/l/linux-source-2.6.10
3) i have try: sudo apt-get install sharutils, but that not works, and i have follow that steps: [http://www.ubuntuforums.org/showthread.php?t=38972&highlight=install+sharutils](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=install+sharutils)
4) tar jxvf madwifi-cvs-current.tar.bz2
5) sudo make clean
sudo make
sudo make install
6) and there is the problem...i don't have the new files in /lib/modules/2.6.10/

So, what is wrong? (in step 5) how i know that is run correctly?)

Thanks in advance

---

### Post by aranbanjo on 2005-11-18
Hi guys,
thank you for this howto which was very helpful in Hoary.
As you said, this card works out of the box in Breezy, but I would prefere a custom kernel :cool: 
I would like to set madwifi as a module but I didn't find it in menuconfig :( 
Do I need to install linux-headers of my custom kernel?

---

### Post by aranbanjo on 2005-11-19
[QUOTE=aranbanjo]Hi guys,
...
Do I need to install linux-headers of my custom kernel?[/QUOTE]

Yep, just do it!
Downloaded the latest driver and installed making
```
# cd madwifi
# export KERNELPATH=/usr/src/linux-source-'your version'
# export KERNELRELEASE='your custom kernel'
# make
# make install
```
reboot.
Cheers

---

