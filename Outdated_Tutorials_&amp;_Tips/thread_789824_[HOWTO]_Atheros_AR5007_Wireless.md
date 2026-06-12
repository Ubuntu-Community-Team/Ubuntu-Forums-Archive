---
title: "[HOWTO] Atheros AR5007 Wireless"
date: 2008-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by gkrules on 2008-05-10
i know a lot of you are having troubles with getting the Atheros AR5007 wireless card working with Hardy Heron. I sent a help request on the madwifi site and i got a modified version for the AR5007 for Hardy.
Heres the tutorial:
First disable Atheros Hardware Access Layer [HAL]:
Go to System>Administration>Hardware Drivers
and uncheck Atheros Hardware Access Layer
then reboot

after reboot type these into a terminal window:

```
sudo apt-get install build-essential
```
```
wget http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
```
```
tar xfz madwifi-nr-r3366+ar5007.tar.gz
```
```
cd madwifi-nr-r3366+ar5007
```
```
sudo make
```
```
sudo make install
```
```
sudo modprobe ath_pci
```
then reboot and it should work!

---

### Post by presston on 2008-05-12
tried this way on 5006 - dont work. only with driver for windows (with NdisWrapper)

---

### Post by Pooka2132 on 2008-05-12
Total newb but I did everything in post #1 and it still didn't work. Any more suggestions? Many thanx

---

### Post by presston on 2008-05-12
look here

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)

---

### Post by nicant on 2008-05-12
Work on laptop Aser Aspire 7720Z !

THANKS !!!

---

### Post by gkrules on 2008-05-12
Yea it wont work if u have an AR5006 
only AR5007

---

### Post by balagosa on 2008-05-12
dude...this crashed my Hardy on reboot. i can not log in anymore.

the situatuion....


Loading Kernel Modules
Loading Manual Drivers.... then after 30mins of wait, still nothing.

i tried booting into recovery mode and this is what i got...
*Reading files needed to boot
lp: driver loaded but no devices found
ndiswrapper version 1.52 loaded (smp=yes, preempt = no)

using Xubuntu 8.04, kernel 2.6.24-16-generic. i am using NDiswrapper though...not madwifi. so i think when i "modprobe", this caused my problem?

---

### Post by balagosa on 2008-05-13
uhm...bump

---

### Post by nicedude on 2008-05-13
First off the AR5007 reports in lspci as being a AR5006 so if your trying to diagnose your problems you should verify your chipset through your PC makers info not lspci.

My acer 5520-5716 has dual boot with both Gutsy & Hardy, both now how have fully functional wifi with madwifi patched drivers. Hardy was more complicated than gutsy and gave me several problems, my final solution was to just remove the following and then install drivers myself

Linux restricted modules ( Drivers for Nvidia & Wifi ) had to go bye-bye as did the pathetic Jockey restricted driver manager software. Without these to confuse things all that was left was to obtain required drivers from Madwifi and from Nvidia then install them myself which wasn't hard but you will need the packages "make" & "build-essentials" to allow you to compile stuff.

Link to Madwifi driver for AR5007 with Hardy ( 32 Bit )
[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)  

Link to Nvidia Graphics Driver ( 32 Bit )
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

I also removed network manager & gnome network manager and replaced them with Wicd as my network manager. Before someone chimes in to say how great network manager is compared to Wicd, I say if it works for you great but it wasn't working right for me ( silly little requirement I have that things actually work ). So if network manager isn't working for you then try Wicd instead.

You can install WICD by doing this -> Go to Administration > Synaptic Package Manager > Settings > Repositories > Third Party Software > Click add and insert this -> deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

Now in synaptic you can install wicd to manage your network connections.

I now am a happy camper with a fully functional laptop. Maybe in the coming weeks or months they will find more bugs in hardy to make these things behave correctly, but if not there is always a fix if you use your head instead :-)

Good luck with your Ubuntu journey all.

---

### Post by balagosa on 2008-05-13
hey nicedude, i do have a 5007EG Wireless. its a long story.

to clarify it, i will post my "lspci" later.

and trust me, it is a 5007EG. i spent hours to look for it's driver.

and i know about the 5007EG being a 5006, i read the Atheros news about that.

info: on 7.10, My WiFi worked flawlessly. having NDiswrapper as program of choice. on 8.04, everything worked fine, including my bluetooth, except the WiFi.

---

### Post by balagosa on 2008-05-13
i would appreciate any way to undo it though.

**i think one would be recompiling the damaged kernel.**

i currently have two kernels (dont have their names at the moment, but i will post it when i get home). and i can boot into one (older kernel). it seems that my **adventure** just messed up my new kernel.

Okay, as nicedude suggested i give a detailed info on what really happened. here it goes.

**Model of Laptop:** Asus A8LE, Dual Core 1.7Mhz
**Wireless:** AR5007EG (my sig is wrong, i will update it)
**Ubuntu version:** Xubuntu 8.04
**What i did:**
1) sudo apt-get install build-essential
2) wget [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)
3) tar xfz madwifi-nr-r3366+ar5007.tar.gz
4) cd madwifi-nr-r3366+ar5007
5) sudo make
6) sudo make install
7) sudo modprobe ath_pci
8 ) reboot

**The Effect:** 1st effect (in normal mode). Splash Screen shows up, then a bunch of lines appeared on the screen. i couldnt read/write them down because they passed by so fast. it stopped at: 

*Loading Kernel Modules
*Loading Manual Drivers

those two are the last lines

2nd effect (in recovery mode). Bunch of lines appear on the screen, same thing. i couldnt read/write them down because they were too fast. it stopped (again) at:

*Loading Kernel Modules
*Loading Manual Drivers
lp: driver loaded but no devices found
ndiswrapper version 1.52 loaded (smp=yes, preempt = no)


My "lspci" cut-out
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) <---this is AR5007EG, already had WiFi on 7.10.


Good Kernel: 2.6.22-14-generic
Messed-up Kernel: 2.6.24-14-generic

---

### Post by gkrules on 2008-05-13
balagosa...
my friend has an Asus A8LE... 
it doesnt have an Atheros AR5007 in it...
that is prolly wat caused the problem

u are getting that error because madwifi cant find the card 
i have no idea how to undo it
maybe a more advanced member can help u

---

### Post by balagosa on 2008-05-13
let me clarify on that. i would be posting my sources later as to why i said my card is a 5007EG. for the meantime:

[quote=me]
My "lspci" cut-out
02:00.0 Ethernet controller: **Atheros** Communications Inc. 802.11abg Wireless PCI Express Adapter (rev 01)
[/quote]
That surely didnt say Intel Wireless to me. but yet, i may be wrong.

and if you havent read the post, i **had** my WiFi on 7.10 using the 5007EG Driver that i downloaded from Atheros.

Here it is:
[Complete lspci on an Asus A8LE]("http://kerneltrap.org/mailarchive/linux-ath5k-devel/2007/12/13/504119") look for **02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)**

[quote=gkrules]
u are getting that error because **madwifi** cant find the card
i have no idea how to undo it
maybe a more advanced member can help u[/quote]

Madwifi?
lp: driver loaded but no devices found
ndiswrapper version 1.52 loaded (smp=yes, preempt = no)
are you sure it is madwifi, coz maybe i might try to remove any component and see what happens.

---

### Post by balagosa on 2008-05-14
cool, i fixed it. i just reinstalled linux-restricted-modules-(kernel number) and that was it. next problem is back to configuring my wifi. so it seems that this thread wont be of much help to me. back to ndiswrapper. 

nicedud, i might need your niceness on this.

---

### Post by gkrules on 2008-05-15
the package in the tutorial is a modified madwifi pack....

---

### Post by Monicker on 2008-05-16
Worked great for me.

Today I purchased a Toshiba Satellite A205-S5825 laptop.  Vista identifies wireless as AR5007EG.  lspci shows it as AR242X 802.11abg.  Followed OP's instructions and had no problems seeing all the wireless networks around me.  Connected to my WPA-PSK network right away.

Awesome.  :)

---

### Post by gkrules on 2008-05-17
yea mine showed up as a AR242X too
i have a compaq presario f756nr

---

### Post by Le Rob on 2008-05-26
I can confirm this works with an LG e500 with an AR242x. Didn't even have to reboot, but removing the module definitely caused wireless to stop working.

EDIT: Okay, had some minor problems on restart. Could have been a myriad of reasons, but I think most likely is that I deleted the madwifi directory (I'm a stickler for a clean home directory). If for some reason you don't want your folder in /home/<you>/, then I'd just move the zip to the /opt folder and proceed from there.

That is: ```
sudo mv madwifi[tab] /opt
```

---

### Post by gmoque on 2008-05-27
[FONT="Arial"]Great work! thanks for the tip, I was using ndiswrapper for over 2 months but I had some problems using it like missing AP or missing information in the output of 'iwlist scan'.

Now that I installed the madwifi driver I can see even more AP

This is my lspci output for the wireless card:

```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

The version that I installed is the one referred on this thread

gmoque
[/FONT]

---

### Post by nkanouras on 2008-06-03
works perfect on toshiba satellite a210-16f !! thanks!

---

### Post by wwusnobrdr on 2008-06-03
Did anyone else's wifi disappear after they installed the new .18 kernel?  I booted into the new kernel and noticed there was no wifi in my interfaces and in network manager.  I have not had a chance to do much troubleshooting and this could just be an isolated issue.

---

### Post by zeerover on 2008-06-04
Yup. My EEE PC 900 with an Atheros 5007 has been useless since last night. I've spent six hours trying all sorts of things. Please post whatever solution you come up with. The best I can do is see wireless networks and hang on "waiting for network key from [networkx]". Anyone else?

---

### Post by ennika on 2008-06-04
Same here, just got the driver installed/wifi running, installed the updates, now nothing goes...

---

### Post by Alfred_McGee on 2008-06-08
Yeah, updates killed my wifi card last week, too. Fixed it by doing a fresh install, installing all updates, and THEN adding the ar5007eg fix, but I'm sure there's an easier way. Maybe try uninstalling and then reinstalling the Madwifi drivers? 

Hey zeerover, did you ever get that bug with your DVD drive figured out? DVDs won't mount for me, but CDs do.

---

### Post by zeerover on 2008-06-08
Ennia, Alfred & Co.,

Sorry I didn't post this sooner. I've fixed the problem that I think Ennika and I shared, and I also know the fix for Alfred's problem. 

Ennika: I don't know why this is, but I was able to fix this by going to Edit Wireless Networks (not sure how else to do this besides right-clicking the network icon in the top panel and choosing Edit Wireless Networks) and removing the network you are trying to connect to (click it once to highlight it, then click the Remove button directly below the list of saved networks). Close the Edit Wireless Networks window. Next, (left-)click on the network icon in the top panel and select the network you want to connect to (EVEN IF IT IS ALREADY SELECTED!). This worked fine for me to resolve the "waiting for network key" issue.

Alfred: Apparently the wireless will break every time we upgrade our kernel. As a result, you have to do the following fix each time:

```
sudo apt-get update
sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
tar zxvf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make clean
make
sudo make install
sudo reboot
```

That info came from an excellent website, properly entitled "getting Ubuntu 8.04 to work perfectly" [on the EEE]. The link is here:

[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly)

I strongly recommend going through all of the items on that page, but DO NOT use the scripts as they can cause problems. Do everything manually. Good luck!

Peace,
Isaac

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by F W Adams on 2009-05-25
I have an Acer Extensa with wireless not working. I tried the above but the file downloaded seems not to be a tar file. Here is what I get:

```
comp@user:~/tmp$ wget http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
--2009-05-25 14:53:16--  http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
Resolving snapshots.madwifi.org... 195.238.237.136, 195.238.237.137
Connecting to snapshots.madwifi.org|195.238.237.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 918 [text/html]
Saving to: `madwifi-nr-r3366+ar5007.tar.gz'

100%[==========================================================================================>] 918         --.-K/s   in 0s      

2009-05-25 14:53:16 (116 MB/s) - `madwifi-nr-r3366+ar5007.tar.gz' saved [918/918]

comp@user:~/tmp$ tar xfz madwifi-nr-r3366+ar5007.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
comp@user:~/tmp$ file madwifi-nr-r3366+ar5007.tar.gz
madwifi-nr-r3366+ar5007.tar.gz: HTML document text
comp@user:~/tmp$ 
```

Sorry, not sure how to proceed, surely something must have changed to make this fail

---

### Post by F W Adams on 2009-06-01
bump

Just checked again and still getting the same problem on loading either  madwifi-nr-r3366+ar5007.tar.gz or madwifi-ng-r2756+ar5007.tar.gz. Any help? The files seem tiny, only 918 and 938 bytes.

---

### Post by Astinsan on 2009-06-01
I haven't had any issues with ubuntu 9.04. Didn't even need to do anything to get it to work. It was active on first boot.



try leaving the z out. It apparently isn't a gz but just a tar file. "tar -xvf file.tar.gz"

---

### Post by F W Adams on 2009-06-01
On further investigation adding .html onto the end of the file says what's happening. It's nothing to do with the file I was trying to download, it's a message from my ISP ( Orange ) saying "the page you were looking for is no longer available"

change the downloaded file name to:
madwifi-nr-r3366+ar5007.tar.gz.html and double click it. Are other people getting the same result?

---

