---
title: "wireless internet"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by HelterSkelter1989 on 2008-10-13
i just installed ubuntu, and i get no internet. i was reading the help screen in ubuntu and it said to go to administration-network manager, however there is no network manager in administration, just network and network tools, neither of which helped me receive my wireless internet. its no a problem with the card or my router because vista is picking it up right now, its more of a problem of me not knowing what i am doing at all.  i have an atheros wireless card built into my laptop. is there a driver i need to install? if so how would i get it into ubuntu with no internet? 

if u have a solution to the problem, please explain it in excruciating detail, since i am very easily confused. :{

---

### Post by taqkavar on 2008-10-13
on the upper right of the screen there should be a computer icon ( or wireless signal bars ) . left click on it and see if it lists the wireless networks. If it doesn't list anything go to Programs > Accessories > Terminal and write: 
> lspci
Copy and Paste using mouse, and post the output here.

---

### Post by HelterSkelter1989 on 2008-10-13
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
jonathan@HAL:~$ 

sorry if its a lil messed up, it was hard getting it from ubuntu to vista :}

---

### Post by taqkavar on 2008-10-13
looks like support for your wireless adapter has been added only very recently to linux. From what I read here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252554](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252554) , support for your wifi will be probably available in 8.10 release out of box.

But you can also use ndiswrapper to get it to work, see the last two posts here:

[http://ubuntuforums.org/showthread.php?t=737206](http://ubuntuforums.org/showthread.php?t=737206)

And about Ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by HelterSkelter1989 on 2008-10-13
i'll see if that works.

---

### Post by HelterSkelter1989 on 2008-10-13
lawl i have no idea how to install stuff in ubuntu. i'm used to just clicking on things and them installing. how do i go about installing those files?

also u said that the new version should support my wireless card without me adding anything to it, does this mean that if i install teh 8.10 beta it will get wifi?

---

### Post by parajuito on 2008-10-13
beta version is just for testing , its not recommended to install it until the final version its out.

it depends on wich kind of files you want to install like if its a deb you just double click it.

heres a little guide for you to install get your wireless working

(guide from [http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/](http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/))

1. First things first,make sure all the repos are enabled:

sudo nano /etc/apt/sources.list

From there make sure you uncomment anything that starts with &#8220;deb&#8221; in there. So changer it from &#8220;#deb&#8221; to &#8220;deb&#8221; Something along thoes lines. To exit and save hit &#8220;CTRL+X&#8221; the answer &#8220;YES&#8221; to do you want to save, then finally hit &#8220;ENTER&#8221;.

2. Make sure you have all the latest updates:

sudo apt-get update && sudo apt-get upgrade

And answer yes to any thing it wants to install. Wait till it is complete and reboot.

3. Now the fun part. Install the build tools to compile and install the Madwifi drivers:

sudo apt-get install build-essential

4. Now install the kernel headers for your architecture. I have only tested this on X86 and I know it works,but for 64-Bit systems I just have not had the time to test it. This below command will install the headers based on what ever your current type of kernel is installed. By default the generic kernel is installed.

sudo apt-get install linux-headers-2.6.24-19-generic

5.  Next we install subversion. Learn more about subversion here.

sudo apt-get install subversion

6. No we get the subversion driver package.

sudo svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng

7. Move yourself to the newley created &#8220;madwifi-ng&#8221; directory.

cd madwifi-ng

8. Build the installer and install it :)

sudo make && sudo make install

9. After that is complete we have one final step and that is to add the module &#8220;ath_pci&#8221; to the /etc/modules file.

sudo gedit /etc/modules and add &#8220;ath_pci&#8221; to the end of the file, without the quotation marks.

Save and close. you need to reboot.

---

### Post by HelterSkelter1989 on 2008-10-13
you have to talk to me like i am an idiot, what do you mean sudo ...... ? whats that? i have never used anything but windows before.

---

### Post by HelterSkelter1989 on 2008-10-14
cmon guys i need this working for school tomorrow, what do i do with those instructions? where does it all go? plz?

---

### Post by 3rdalbum on 2008-10-14
Any of the lines that don't make sense (the ones that start with "sudo" or "cd") are meant to be typed into a terminal window (Applications > Accessories > Terminal)

---

### Post by HelterSkelter1989 on 2008-10-14
thank u thank u thank u :D

---

### Post by HelterSkelter1989 on 2008-10-14
i did what it says to do there but for everything it said it could not be found or it failed. none of the updates that ubuntu says are available will ever install it just says that it failed. also it said there was no cmd sudo: svn: whatever that means.

---

### Post by lemmy999 on 2008-10-14
@HS1989

Do you have your ubuntu box connected to the internet on an ethernet cable.Parajuito's guide relies on you being able to download the madwifi drivers.

re "there was no cmd sudo: svn: whatever that means. " I think you will find that the command was sudo svn which is very different. I would advise you to cut and paste each command into a terminal. The howto is a good one and will work. If one of the commands throws up an error then please stop at that point and post the output from terminal here.

---

### Post by HelterSkelter1989 on 2008-10-14
i did put it in as sudo svn, it said "no cm sudo: svn:" and i have the driver downloaded. also it won't connect to the internet through and ehternet cable for some reason.

---

### Post by parajuito on 2008-10-14
lol you need to install svn fist :S

sudo apt-get install subversion

---

### Post by HelterSkelter1989 on 2008-10-14
lawl i see. it won't let me install anything though :/

---

### Post by HelterSkelter1989 on 2008-10-14
how do you get the wired connection to work? it asks me for a network name and a password when its just plugged into the cable modem. there is no password. what am i doing wrong there?

---

### Post by parajuito on 2008-10-14
> **HelterSkelter1989 said:**
> lawl i see. it won't let me install anything though :/

you dont have internet acces in ubuntu or why it wont? :S

---

### Post by HelterSkelter1989 on 2008-10-14
why won't it let me connect through a wired connection?

---

### Post by parajuito on 2008-10-14
idk :S ethernet should just work fine :S lol weird, i think we will need to google xD

---

### Post by HelterSkelter1989 on 2008-10-14
haha, i connect the cable, what else do i need to do after that?

---

### Post by parajuito on 2008-10-14
well just install svn xD and you are ready to follow the guide
sudo apt-get install subversion

---

### Post by parajuito on 2008-10-14
if you have an error post it here xD

---

### Post by HelterSkelter1989 on 2008-10-14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversion

 what does this mean?

---

### Post by parajuito on 2008-10-14
type svn it should tell you somethink like program subversion is not installed to install it type.... and type what it says

---

### Post by HelterSkelter1989 on 2008-10-14
jonathan@HAL:~$ svn
The program 'svn' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found
jonathan@HAL:~$ sudo apt-get install subversion
[sudo] password for jonathan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package subversion
jonathan@HAL:~$

---

### Post by parajuito on 2008-10-15
:S maybe you dont have your system updated check for updates in 
system > administration > update manager

---

### Post by HelterSkelter1989 on 2008-10-15
yeah it won't let the updates install. it always says it failed to connect. this is because i cannot access the internet. i tried a wired connection with an Ethernet cable, but it still won't connect. it says connect to secured network, but my network isn't secured, so why does it ask me for passwords and such?

---

### Post by parajuito on 2008-10-15
idk :S try and put your password

---

### Post by HelterSkelter1989 on 2008-10-15
i don't think there is a password. i've never had to use one before. there are just a bunch of different numbers on it.

---

### Post by parajuito on 2008-10-15
lol maybe we need more help with this, i have never heard about this problem before

---

### Post by parajuito on 2008-10-15
try going to a friend`s home and connect the ethernet cable and see if it works xD

---

### Post by HelterSkelter1989 on 2008-10-15
i dunno anyone whos ethernet calbe  i could use. :/

---

### Post by HelterSkelter1989 on 2008-10-15
if i just download the drivers and put them on a disk and then load up ubuntu and take it off the disk, can i install it then? if i can how tdo i do that and where do i get the drivers?

---

### Post by parajuito on 2008-10-15
> **HelterSkelter1989 said:**
> if i just download the drivers and put them on a disk and then load up ubuntu and take it off the disk, can i install it then? if i can how tdo i do that and where do i get the drivers?

maybe you can but i think those drivers wont work if you dont have your system updated.Just try to go out to someone`s house they surely have an ethernet cable to wich you can connect your computer xD

---

### Post by HelterSkelter1989 on 2008-10-15
none of my friends live near here. its not my internet i guarantee that. my internet works just fine. i don't see what difference it would make if it was someone else's. it there some way to update offline?

---

### Post by HelterSkelter1989 on 2008-10-16
if there is some way i can get the downloads i need without an internet connection in ubuntu, would someone please tell me? i really need to get this working for school.

---

### Post by pak33m on 2008-10-16
HelterSkelter1989,

In order to continue through the instructions that were posted about downloading from subversion earlier you will need an ethernet connection.

To do this you should simply plug an ethernet cable that you know is providing an Internet connection.  You could check this by plugging in another computer (if available) that you know will connect to make sure.

If you have verified that you have an Internet connection with the ethernet cable you should plug it into the ethernet port on your laptop.  At this point you should see the Network Manager icon in your panel tray attempting to make a connection.  The Network Manager icon will go from looking like a computer to a set of signal bars, like on a call phone.  If the Network Manage icon stays as a computer icon right-click on it and make sure that Enable Networking is checked.

If Enable Networking is checked uncheck it and recheck and see if it attempts a connection. Another way of course would be to restart the laptop with the ethernet cable plugged in.  If successful the Network Manager icon should display signal bars and you can right-click and select Connection Info to see what network connectivity you have.

You may also want to right-click on the Network Manager and make sure that Enable Wireless is checked too.

If you have a successful ethernet connection you can proceed with the instructions on downloading subversion to get wireless working.

Hope this helps.

---

### Post by adityad on 2008-10-16
Hi,

I have a similar question. I got a Dell Inspiron 1525 laptop, with Dell (TM) Wireless 1395 802.11g 54Mbps Wireless Mini Card. I have installed ubuntu 8.04 on it and I don't have any windows OS on it. 

So, now I have the question -- will the OS support my wireless adapter?
Will I be able to connect to wireless internet?
If yes, please let me know how should I do that?

Thank You.
Aditya

---

