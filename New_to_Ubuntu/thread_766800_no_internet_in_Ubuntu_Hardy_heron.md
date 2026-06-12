---
title: "no internet in Ubuntu Hardy heron"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by gerben1 on 2008-04-25
I have a laptop with a broadcom card. Inn Ubuntu Gutsy it also took me a long time to get the wireless working, but I got it working in the end. Since the upgrade to Hardy Heron it did not work anymore, so I started looking on the web for solutions. I tried one which did not work and now my internet does not work at all anymore even the WIRED connection does n0ot work anymore...

I followed this HOWTO:
[http://ubuntuforums.org/showpost.php?p=4635345&postcount=18](http://ubuntuforums.org/showpost.php?p=4635345&postcount=18)

My wired internet connection worked before I did that but not after. I thought I could easily undo all that, but apparently not.

What I did first is:

(1) make the script /etc/init.d/bcm43xxfix.sh
(2) cd /etc/init.d/ && sudo chmod 755 bcm43xxfix.sh
(3) sudo update-rc.d bcm43xxfix.sh defaults
(4) sudo gedit /etc/modprobe.d/blacklist and comment out blacklist bcm43xx
and then, as this did not work, following some other suggestion
(5) sudo aptitude remove b43-fwcutter

This still did not work and even worse now also the wired internet was not working anymore...

so then in order to try to undo all that I did:

(1) download b43-fwcutter_011-1.deb on another computer (and then copy it to my laptop)
(2) double click b43-fwcutter_011-1.deb to install the package
(3) sudo rm -f /etc/init.d/bcm43xxfix.sh
(4) update-rc.d bcm43xxfix.sh remove
(5) sudo gedit /etc/modprobe.d/blacklist and blacklist bcm43xx again

I had hoped that then everything would be as i started again, but I cannot connect to the internet at all anymore.

Can someone please give me some suggestions on how to get my internet connection back?

---

### Post by Hesperion on 2008-04-25
HELLO?? This guy's not alone on this. Any help coming?? No connection AT ALL of any kind after upgrade.
!!

---

### Post by ezekielnin on 2008-04-25
Same thing here EXCEPT that I'm on a FRESH install!!! (with wubi)
My laptop is a dell 1501.. everything is supposed to work fine on this baby...

thks

---

### Post by sam_delta on 2008-04-25
you have already installed b43-fwcutter, have you tried to activate drivers by going into system>administrator>hardware driver?

---

### Post by ezekielnin on 2008-04-25
hey. I Just tried to reboot and reset my modem and router and I'm now connected with the wired network connection. I will try to see if the wireless works too.

---

### Post by sam_delta on 2008-04-25
alright, if wireless dont work, ull have to reinstall f43-fwcutter, WITH aptitude , NOT synaptic, i read this few days ago , this is due to a firmware fetch that synaptic does not make, it worked for me, and for some people i recomended this process, so if wireless dont work just follow these steps 

make sure you have your wired connection and do this

go to a terminal and type to remove

```
sudo aptitude purge b43-fwcutter
```

update your repos with

```
sudo aptitude update
```

to reinstall type

```
sudo aptitude install b43-fwcutter
```

then restart pc, goto system>.administrator>hardware drivers drivers, and activate broadcom driver

heres one of the posts where it worked
[http://ubuntuforums.org/showthread.php?t=762248](http://ubuntuforums.org/showthread.php?t=762248)

tell us how it goes
sam

---

### Post by Hesperion on 2008-04-26
As above I went through the "upgrade" which went uneventfully. After that: NO INTERNET CONNECTIONS OF ANY KIND AT ALL! I expected to have to do some work in the case of the wireless but there is nada, zip here to work with. All the possibilities seem to require a working connection so this leave few options. I did the upgrade from 7.10 to 8.04. The previous installation (Gutsy) worked fully. This one does not. I gave up on the "upgrade" and burned a DVD image which I used to install a clean install with full partitioning. The same result was had. No internet, wired OR wireless (blue light for the wireless radio is on btw). I am installing on an EeePc 4g surf. My home network is through a Belkin G MIMO router. I have even tried connecting this computer directly to the modem. There is no connection. I noticed that when a system is connected to the router it shows up by lighting an indicator light that corresponds to the connector that it is plugged in to. The eeepc does not light the light on the router and if I swap the connections around it doesn't light any of the lights it is connected to although all the other systems do. I am at a loss here because I have read the forums back and forth, up and down and do not find anything like it here. I have always been able to reason out network problems before but this has me completely baffled. I cannot update any drivers or software = no internet. I cannot get the restart of the networking to work in terminal = just ignores the command. I tried to manually insert the config for the wired connection and this has no effect. The ip that comes up using the ifconfig is nonsense not related to anything I ever saw. I rarely ever ask for help but this one has me beat! Please help get my head on straight here and start me in the right direction. Please?

---

### Post by Dr.Gringo on 2008-04-26
It might seem obvious but all of you who are having problems tried the enabling the restricted drivers, right???

---

### Post by sam_delta on 2008-04-26
heres a way that will help you reinstall b43-fwcutter, but please note that this will be significally harder w/o connection, but since there is no other choice, lets go!!

download and copy the following files into a USB flashdrive

(build-essetials)
[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb)

(f43-fwcutter)
[http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)

(Broadcom Firmware)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

go back to your ubuntu 8.04 pc and copy build essential.deb and  b43-fwcutter-011.tar.bz2 file into the desktop

just run the build essentials and let them install

now lets get to fwcutter

open a terminal and type 
```
 cd Desktop 
``` 
then

to extract
```
 tar xjf b43-fwcutter-011.tar.bz2 
```

to change directory
```
 cd b43-fwcutter-011 
```

to compile
```
 make 
```

to get back to desktop 
```
 cd .. 
```

then we must install b43 with the firmware together

copy the broadcom-wl-4.80.53.0.tar.bz2 archive into your desktop and extract it (right click, extract here), it shuld make a folder with the same name
then open a terminal and type

```
 cd Desktop
```
Now our working directory is desktop, same place where we unpacked broadcom firmware

then we change working directory 
```
 cd broadcom-wl-4.80.53.0/kmod
```

then we copy/install the firmware by typing this

 ```
 export FIRMWARE_INSTALL_DIR=&#8221;/lib/firmware&#8221; 
```

finally to install
```
 ../../b43-fwcutter-011/b43-fwcutter -w &#8220;$FIRMWARE_INSTALL_DIR&#8221; wl_apsta.o 
```

restart pc and try to enable hardware drivers through system>administration>hardware drivers and should work
let us know if you have any problems with any command, thx, 


procedure taken from: (i made the necessary modifications to make it without internet connection
[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)


sam

---

### Post by Hesperion on 2008-04-26
ok, not to derail this momentum we have going here but I did a little experimenting and ran a USB cable direct from my cable modem to the Eeepc and it recognised the connection First sign of life so far) and referred to it as "unknown USB communications interface". Also it enabled the previously grayed out connection information button. This shows IPs and so forth of all zeros. I am not able to get on the net still but this was an interesting, if not yet understood turn of events. LOL. 
Anyway I return my attention to the teacher. I will follow these instructions as I go but of course in my case it will not involve the "Broadcom firmware". I am just trying to establish any working internet connection at all. Wirless will come after surmounting all the other obstacles.

---

### Post by gerben1 on 2008-04-26
sorry double post - delete please

---

### Post by gerben1 on 2008-04-26
This worked for me, thank you very much Sam_delta!

I assume I can now get rid of ndiswrapper? Or is ndiswrapper still being used?

---

### Post by sam_delta on 2008-04-26
> **gerben1 said:**
> This worked for me, thank you very much Sam_delta!

I assume I can now get rid of ndiswrapper? Or is ndiswrapper still being used?

yes,,get rid of ndiswrapper, 

ndiswrapper should be avoided at all cost, ndiswrapper is just the last alternative to native linux drivers.

glad it worked, 
sam

---

### Post by Joeb454 on 2008-04-26
ndiswrapper is for those cards that are awkward and don't work in Linux, it just allows you to run Windows drivers on Linux :)

Makes me glad I have an intel chip for my wireless :)

---

### Post by Hesperion on 2008-04-26
Got the files you specified. Went to install the build-essential one. Got "Error: Dependency is not satisfiable: libc6-dev|libc-dev"

Are these file understood to be toward the goal of restoring wired connectivity? I have hit a blockage here. Further, the broadcom references do not pertain to my situation. I have an Atheros L2 NIC and an Atheros Atheros AR5BXB63 wireless device. I discovered last night that the machine reacted to being directly connected to the cable modem via USB. This did not achieve any connectivity and the IP's all show zeros. Does this indicate something however about my problem? Hope you can help.

---

### Post by sam_delta on 2008-04-26
alright hesperion , nope, that method i posted was to get boradcom wireless to work, not wired. 
about the error you got, it means that on order to install build-essentials, you must have libc6-dev, but dont bother, since you dont have a broadcom wireless.

now lets try to fix your problem, first, since ive never used/fixed atheros wireless hardware ill have to research a bit on how to make your hardware work, hopefully ill find a solution. until then, ill like to see the output of the following commands while the usb cable is connected

```
 iwconfig 
```

---

### Post by pwinterrowd on 2008-04-26
I'm just trying to get the wired connection to work as well.  I have no interest in wireless.  For me iwconfig produces:

lo        no wireless extensions.
eth0      no wireless extensions.
eth1      no wireless extensions.

---

### Post by Joeb454 on 2008-04-26
for standard ethernet I believe it is ```
ifconfig
```

---

### Post by pwinterrowd on 2008-04-26
eth0      Link encap:Ethernet  HWaddr 00:1a:92:5b:8f:02  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:214 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:5b:9d:76  
          inet addr:192.168.0.153  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe5b:9d76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:0 errors:0 dropped:42 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10155 (9.9 KB)
          Interrupt:213 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126776 (123.8 KB)  TX bytes:126776 (123.8 KB)

---

### Post by josel777 on 2008-04-26
> **pwinterrowd said:**
> eth0      Link encap:Ethernet  HWaddr 00:1a:92:5b:8f:02  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:214 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:5b:9d:76  
          inet addr:192.168.0.153  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe5b:9d76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:0 errors:0 dropped:42 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10155 (9.9 KB)
          Interrupt:213 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126776 (123.8 KB)  TX bytes:126776 (123.8 KB)

I have the same problem as you. I am still looking for a solution.

---

### Post by Hesperion on 2008-04-26
Interesting development: I disconnected that USB cable. I shut down, I unplugged the AC, I removed the battery, I made coffee. I came back and installed the batt. restarted and the miniBeast now shows up on my router. Still only shows the Manual Configuration option in tne manager however. I opened the Synaptic and it hung while rechecking. had to reboot to get hold again. I went to the networking manager and input manual setting appropriate to my network/router. I re-surveyed the network using my router control panel and the eeepc now shows up with an IP!! I went to the terminal and typed [sudo apt-get update] (I am so proud, one of the very few cmds that i know. LOL) it connected and went through the process without errors and retrieved some stuff. 

Since you asked: the output of the cmd: iwconfig is the same as those for "pwinterrowd"'s response. This is no surpise though. The output for ifconfig however is:

eth0 Link encap:Ethernet HWaddr 00:1e:8c:94:79:f0
inet addr:192.168.2.51 Bcast:192.168.2.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:5305 errors:0 dropped:0 overruns:0 frame:0
TX packets:3114 errors:0 dropped:0 overruns:0 carrier:2
collisions:0 txqueuelen:1000
RX bytes:7910262 (7.5 MB) TX bytes:0 (0.0 B)
Memory:fbfc0000-fc000000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 KB) TX bytes:0 (0.0 KB)  

Note: in my Gutsy installation (which was working well) there was none of this manual config required. Only just to plug in the connection. Also there was the "Connection Information" button available which in this case is grayed out. Just some observations. Also, Firefox now responds and browses. Where do I go from here to get correct drivers and install what i need. Then there is the next issue of the wireless. BTW: I think you guys are great. You have helped me so much and are so knowledgeable. You are under-appreciated. THANK YOU.

---

### Post by sam_delta on 2008-04-26
alright hesperion, good thing you made your wired connection to work, having wired connection, getting the wireless to work gona be much easier.

ive been looking into the internet, and a quick solution to your problem is to install ndiswrapper and install windows drivers using ndiswrapper

the first step is to install ndiswrapper, you can do this, by going into the system>administration>synaptic package manager, and serch for the package Ndiswrapper, and mark for installation, click apply

one ndiswrapper is intalled, well need to get the apropiate windows driveres for your wireless card, you can find those on your manufacturer website, if you cant find them, tell us, we can help you find them, once we have them, we go into the terminal go into the same directory as the windows drivers , for example, if you have windows drivers in your desktop type

```
cd Desktop
```

then, we install drivers by typing

```
 sudo ndiswrapper -i driver.inf 
```

then we make sure drivers installed correctly by typing 

```
 sudo ndiswrapper -l 
```

something like "XXXXX : driver installed device (XXXX:XXXX) present" should appear

then we run the correspondint modules 

```
sudo ndiswrapper -m 
```
and 
```
sudo modprobe ndiswrapper 
```

restart, check if works, if it dosnt work, 

type this:
to remove other wireless modules
```
 sudo modprobe -r b44     
```
```
 sudo modprobe -r b43
```
```
 sudo modprobe -r b43legacy
```
```
 sudo modprobe -r ssb
```
```
 sudo modprobe -r ndiswrapper
```

then run ndiswrapper and b44 module again
```
 sudo modprobe ndiswrapper 
```
```
 sudo modprobe b44
```

check/restart and see if it works

tell us how it goes,
Sam

---

### Post by Hesperion on 2008-04-26
Thanks for sticking with me here. I did as you said and searched for ndiswrapper in the synaptic and it is not there. SO...download it from someplace?

---

### Post by sam_delta on 2008-04-26
it should be there but ull need to activate universe and multiuniverse repos. go into synaptic, then settings>repositories, and mark with the the checkbox of every repo (canonical supported, comunity mainteined, propietary driveres, software restricted....) mark them all, and you should be able to find ndiswrapper

---

### Post by egan_mccomb on 2008-04-26
I have this problem as well (no wired (or wireless) internet). I would love to get this figured out so that I can start actually using Ubuntu.

network card: Broadcom 440x 10/100 Integrated Controller

Note that once I have wired internet working, I ought to be able to get wireless working as well.

I'm wondering if Hesperion's solution might work for me...

Any advice would be greatly appreciated.

---

### Post by Hesperion on 2008-04-26
got everything activated and found and installed the ndiswrapper. Now looking for the correct atheros drivers not sure how best to find them. This, as I said, is an EeePc 4G surf the specs say Atheros LAN L2 and wireless = AR5BXB63. I see looking in the System > Admin > Hardware Drivers there are 2 items listed: Atheros (HAL) and the Support for Atheros 802.11 wireless LAN cards (Enabled and In use are checked).

---

### Post by sam_delta on 2008-04-26
> **egan_mccomb said:**
> I have this problem as well (no wired (or wireless) internet). I would love to get this figured out so that I can start actually using Ubuntu.

network card: Broadcom 440x 10/100 Integrated Controller

Note that once I have wired internet working, I ought to be able to get wireless working as well.

I'm wondering if Hesperion's solution might work for me...

Any advice would be greatly appreciated.

try procdure in post number 9

sam

---

### Post by sam_delta on 2008-04-26
> **Hesperion said:**
> got everything activated and found and installed the ndiswrapper. Now looking for the correct atheros drivers not sure how best to find them. This, as I said, is an EeePc 4G surf the specs say Atheros LAN L2 and wireless = AR5BXB63. I see looking in the System > Admin > Hardware Drivers there are 2 items listed: Atheros (HAL) and the Support for Atheros 802.11 wireless LAN cards (Enabled and In use are checked).

as for the windows drivers, try searching for them on the manufacturer page, this case, atheros.com, or google it, if you cant find them ill take a look

as for the drivers listed in hardware drivers appear to be in use, but does not work, just uncheck them as they are not working and thats why we re installing ndiswrapper
sam

---

### Post by Hesperion on 2008-04-26
still searching for drivers. Linux version drivers for this specific card...is that what you have in mind? 

Meanwhile concerning this wired connection: It is currently running on manual configuration. Under 7.10 it was simply recognise when connected and showed as a wired connection. Is this a concern or is it just a product of the new OS not having the drivers as yet? It's working so I am not complaining, just wondered about the difference against 7.10.

---

### Post by sam_delta on 2008-04-26
no, we are not searching for linux drivers, we are searching for WINDOWS drivers, thats whay ndiswrapper do, it let you install drivers for windows in linux.
some manufacturers do not support linux drivers and thats why we use ndiswrapper to install easy-to-get windows drivers.

as of the wired card, i do not have a clear explanation on what happened, i would need further investigatin on why it didt worked like 7.10

thx, sam

---

### Post by Hesperion on 2008-04-26
OK, I found a download of xp drivers for this card and d/l to the Desktop. It was a zip file and I right click selected extract here. it coughed up a file folder named 'lan' I used the cmds you specified above and it said there was no such file or folder. I changed directories down to the file this extracted and the only file ending in .inf I could locate was one called 'oemsetup.inf' i ran the code again and it came up with could not find parts of the information, continuing anyway, Driver installation may not be complete. I ran a check as you said and it said oemsetup : not a valid driver. I removed it by name using the ndiswrapper -r cmd. Sort of stuck now. Is it likely that I found a wrong driver? It is more likely that I just don't know what the heck I am doing and it is something I am not seeing. 
We'll get to the wired question later, thanks.

---

### Post by Hesperion on 2008-04-26
Ok sorry I am such a twit. <LOL. I did get the driver installed using what you outlined and what is left of my brain. It shows up: 
driver installed
device (1969:2048 ) present (alternate driver: atl2)

So moving on i ran the "corespondant module" cmd and got:
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
[box bounded by astrisks]
"The update-modules command is deprecated and should not be used!"

Should this be alarming somehow?? Should I go on with your procedure now?

---

### Post by Hesperion on 2008-04-26
i couldn't find out anything about this error message so I decided to go ahead with the rest of your process. When I type the cmd sudo modprobe ndiswrapper it takes it and goes directly to the next command line with ready cursor. (I hope this is what it is supposed to do.) Then when trying to type the next entry the keyboard appears to have stopped responding. So i close the Terminal and reopen it and do the next line of your code and hit return. Then same thing happens when trying to type the next line. I rather doubt that this is normal. At any rate, after restart is didn't give wireless connectivity. So I went on with your other cmds and then after another restart still no wireless. So now I am completely stumped. Could I have gotten the wrong driver. It came from the ASUS EeePc support site. I was fairly confident that it was the correct one. What do you suggest from here?

---

### Post by sam_delta on 2008-04-27
ok, they seem like the correct drivers, since they installed correctly and says "device present", now, i need specific details on what commands where you typing where it got stuck, just to point one thing

when you type a "sudo modprobe ndiswrapper" or any "sudo modprobe_______" nothing happens, it just go through and u get a new command line where you should be able to type again
the first time you type a "sudo" comand, you have to type your password, you will no see any sign of letters nor any sign, you just type ypur password and type return

now, tell me which commands froze to figure out what happened
did "sudo modprobe ndiswrapper" and "sudo ndiswrapper -m"? went through with no problems? 

sam

---

### Post by sam_delta on 2008-04-27
also, you may want to uncheck the wireless driver on system>administrator>hardware driver,, since it might be conflicting with ndiswrpper

---

### Post by Hesperion on 2008-04-27
sorry to go off on my own here but i was having so much trouble with the changes i had made that i decided to untangle the mess. I used the live dvd and reinstalled Hardy. I then got all the updates i could get with the now-working wired connection and tried to get back to as clean as possible. I looked over some posts and found a bug report on this issue specific to the EeePc and Hardy. It got my mind working and i found a sort of recipe for doing the whole thing with MadWifi. I followed that procedure and it worked. In fact, I am typing this on the miniBeast using the wifi right now. I did try to make some adjustments that caused me to lose the connectivity again but I found a combination that worked. Part of it has to do with learning the differences with this Hardy against what I knew of gutsy. if you like I can post what i did exactly for those who might be interested. One thing i discovered is that the wireless connection insists on being set in roaming mode. I don't know why because I don't recall ever using that before, only DHCP settings off the router. Maybe you could shed some light on that for us...

The other issue that i was complaining about got resolved mostly in the re installation of the system. So Thank You SO Much for your help on that too. I think in the process of asking questions you get insights about possible answers. 

I did disable those propietary drivers you were asking about way back at the first so they weren't a factor. 

Thanks for your help. And like I said, if you would like I can post the code I put in to accomplish all this.

---

### Post by sam_delta on 2008-04-27
no problem hespiron im glad you made it work :),  

if it isnt too much truble, itll be nice that you post the code/procedure you used to make it work, so itll be  on ubuntu forum archives for further probles/researchers

thx, and again, glad you made it work :)

---

### Post by Hesperion on 2008-04-27
I found this procedure. It pertained to 7.10 but I could not find any significant differences in it that would seem to cause it not to work;

sudo apt-get update
sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz'
tar zxvf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
make clean
make
sudo make install
sudo

I had to set some specifics such as my computer's name and of course enter the network type and passkey. It worked after the reboot without doing much of anything. 

Keeping mind that I am running this on an ASUS EeePc 701 4G Surf with its Atheros AR5BXB63 wireless card on a clean install of Hardy. No other changes were made before trying this. So I am not sure if this is going to help everyone but it did work for me. 

Thanks again sam_delta for your help.

---

### Post by Corneilius on 2008-04-27
I am having the same problem in that after my upgrade to Hardy, I have been left with no internet.  no wireless or wired.

I am trying to follow the steps in post #9.  On the last step of the process, I am recieiving the error, failed to create output directory: Permission denied

---

### Post by sam_delta on 2008-04-27
type sudo before the command to gain permission. for example

sam@laptop:~$ sudo <type the command here>

,  remember that that procedure is for broadcom wireless,

sam

---

### Post by Corneilius on 2008-04-27
Thanks Sam!

It worked.  I have been using Linux for about 9 months now.  I really should have figured that one out on my own.  Thanks again

---

### Post by sam_delta on 2008-04-27
no problem corneilius, im glad i was able to help ya :), have fun, and enjoy ubuntu

---

### Post by josel777 on 2008-04-27
> **Corneilius said:**
> I am having the same problem in that after my upgrade to Hardy, I have been left with no internet.  no wireless or wired.

I am trying to follow the steps in post #9.  On the last step of the process, I am recieiving the error, failed to create output directory: Permission denied

I am having the same problem even after using the last command with sudo.

command:
sudo ../../b43-fwcutter-011/b43-fwcutter -w “$FIRMWARE_INSTALL_DIR” wl_apsta.o

---

### Post by josel777 on 2008-04-27
This worked for me:

> sudo su
> ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o

My WIFI light is now blue, but I am still unable to obtain an IP address.

---

### Post by sam_delta on 2008-04-27
you using a broadcom wireless??

does your router have any type of encryption?

have you tried connectiong into any other network?

---

### Post by josel777 on 2008-04-28
> **sam_delta said:**
> you using a broadcom wireless??

does your router have any type of encryption?

have you tried connectiong into any other network?

you using a broadcom wireless?? Yes.

does your router have any type of encryption? Yes (I am connected to the router on XP).

have you tried connecting into any other network? Yes, I am unable to connect to open routers too.

---

### Post by sam_delta on 2008-04-28
you may want to start a new thread under the network/wireless section as i cant figure out what might be causing that.

if you have wired connection, you may try reinstalling b43-fwcutter drivers again, has worked for some people, the procedure on this is described on 
post # 6 of this same thread quick link to page: ([http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800))

---

### Post by josel777 on 2008-04-28
Thanks for the help sam_delta. I am now able to connect as long as I manually enter the IP.

---

### Post by sam_delta on 2008-04-28
no problem, glad its working, :)
 you may want to do a last effort and try to enable DHCP under the network manager, so you can connect without the need to enter your ip, if problem persist, post your problem under Network/wireless section of the forum

---

### Post by Hesperion on 2008-04-28
just wanted to jump in here and say I experimented with both and found if I enabled DHCP the connection was severed. The only way it will work at all, wired or wireless is in "roaming mode". Not at all sure why this is. Just thought I would mention it.

---

### Post by sam_delta on 2008-04-28
alright, thanks for pointing that out hesperion,,, then, roaming mode is the way to go, you shouldnt need to enter manualy any ip, it should just connect

sam

---

### Post by Hesperion on 2008-04-29
That has been my experience so far. This may not be the case for everyone.

---

### Post by josel777 on 2008-04-29
> **Hesperion said:**
> just wanted to jump in here and say I experimented with both and found if I enabled DHCP the connection was severed. The only way it will work at all, wired or wireless is in "roaming mode". Not at all sure why this is. Just thought I would mention it.

I have the exact problem. Very strange.

---

### Post by kenfeyl on 2008-04-29
Hey Sam,

Thanks for your post. I followed all your steps and populated the files into /lib/firmware. The trouble now is that when I go to System->Administration->Hardware Drivers only my nVidia card shows up, not the Broadcom drivers. I've rebooted several times. The wireless still doesn't work, and I'm not sure what to do next. Any tips?

Ken

---

### Post by sam_delta on 2008-04-29
do yu have wired connection?, also, you sure you have broadcom wireless?

if you have wired connection, try to reinstall b43-fwcutter using aptitude

see post # 6 from 
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)
NOTE__ make sure you answer Y for yes, when you get prompt if you want to fetch the firmware on "sudo aptitude install b43-fwcutter"
 

if still dosnt work, you may want to try ndiswrapper. but i recommend you to do your best trying to find a linux native solution before going to ndiswrapper.

sam

---

### Post by al-fil on 2008-04-30
Hi everyone, I've been trying to follow this thread and a couple other with the same issue. After updating to Hardy on my desktop my _wired_ connection went cold. I followed the steps in post #6 'b43-fwcutter' but my connection is still dead. I can only get online if I call the following commands which I found in another thread:
```

sudo modprobe -r forcedeth
sudo modprobe forcedeth msi=0 msix=0
sudo /etc/init.d/networking restart 
```

I have to input these every time I reboot. Someone suggested adding the commands to the boot-up (system>preferences>sessions) but that did not work either. I have an nvidia network card (not sure what 'the broadcom' or 'ndiswrapper' are). Any ideas?

---

### Post by sam_delta on 2008-04-30
you can write those commands into a shell script

to do this:

1. make a new text file, open it with your favorite text editor and type in it
```
 
#!/bin/sh
sudo modprobe -r forcedeth
sudo modprobe forcedeth msi=0 msix=0
sudo /etc/init.d/networking restart
```

save the file as "wireless_script" and save it in a known location (for example Desktop)

open a terminal and type to make the script executable
```
sudo chmod +x ./Desktop/wireless_script
```

then, go into system>preferences>sessions, and click on "add" located at the right of the window, 

add any name, id recomend "Wireless script", where it says command, click on the small icon on the right to browse files, and go into desktop and select the file you just made. add any description if you want

next time you boot, the system should run the script at startup and therefore you wireless should work without typing anything

tell us how it goes
sam

---

### Post by al-fil on 2008-04-30
Thanks Sam,
I'll try this as soon as I get home from work.

---

### Post by sam_delta on 2008-04-30
> **al-fil said:**
> Thanks Sam,
I'll try this as soon as I get home from work.

no problem, tell us if you encounter any problem, or how it goes

sam

---

### Post by al-fil on 2008-04-30
Ok, for some reason adding the file to 'sessions' didn't work... Good news is: now I don't have to input the lines manually in terminal, I just simply open the executable text file (wireless_script) from my desktop and all I have to do is type my sudo password. So it's not fixed but it's a little less of a pain... Thanks again for the suggestion. Let me know if you can think of something else :)

---

### Post by sam_delta on 2008-04-30
> **al-fil said:**
> Ok, for some reason adding the file to 'sessions' didn't work... Good news is: now I don't have to input the lines manually in terminal, I just simply open the executable text file (wireless_script) from my desktop and all I have to do is type my sudo password. So it's not fixed but it's a little less of a pain... Thanks again for the suggestion. Let me know if you can think of something else :)

alright, after a few test i came up with something else ;p

open the "wireless_script" and remove all sudo's from it, youll end up with something like this:

```
#!/bin/sh
modprobe -r forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart
```

save it, and add it to sessions again, see if it works

tell us how it goes

sam

---

### Post by josel777 on 2008-05-01
For those with Broadcom cards, this really worked for me:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by al-fil on 2008-05-01
> **sam_delta said:**
> alright, after a few test i came up with something else ;p

open the "wireless_script" and remove all sudo's from it, youll end up with something like this:

```
#!/bin/sh
modprobe -r forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart
```

save it, and add it to sessions again, see if it works

tell us how it goes

sam

Blast! It didn't work from sessions and opening the file didn't do anything. It seems to only work if sudo is there...

---

### Post by sam_delta on 2008-05-01
alright then, add sudo to run manually, let me think of some other way of running it at boot time

---

### Post by al-fil on 2008-05-01
Success!

- Run gedit as root and open /etc/rc.local
- Atl+F2 -> gksu gedit /etc/rc.local
- Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

From: [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836)
========
Sam, thanks again for sticking with me. You're the embodiment of the ubuntu community!

---

### Post by sam_delta on 2008-05-01
alright al-fil, no problem, thats what we do, help and make people feel confortable here at the ubuntu community

im gald its working, enjoy ubuntu :)

---

### Post by andybob on 2008-05-01
Hey Sam, it looks like you really know what you are doing...

If you don't mind I could use a little help...

[http://ubuntuforums.org/showthread.php?t=775184](http://ubuntuforums.org/showthread.php?t=775184)

Thanks,



Andybob

---

### Post by Kidge on 2008-05-02
> **al-fil said:**
> Success!

- Run gedit as root and open /etc/rc.local
- Atl+F2 -> gksu gedit /etc/rc.local
- Paste the following lines between the comment lines and exit0:
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

From: [https://bugs.launchpad.net/ubuntu/+bug/136836](https://bugs.launchpad.net/ubuntu/+bug/136836)
========
Sam, thanks again for sticking with me. You're the embodiment of the ubuntu community!

PERFECT!

works as u expect from the ubuntu community You guys are life savers

---

