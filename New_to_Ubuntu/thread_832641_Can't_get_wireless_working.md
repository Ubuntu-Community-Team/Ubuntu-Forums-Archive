---
title: "Can't get wireless working"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by hmfai on 2008-06-17
I am running on Ubuntu 8.04 and using the D-Link 120+ wifi adapter.
I can't manage to get the it working.

Any help?

---

### Post by RomeReactor on 2008-06-17
Hi. Please open a terminal (Applications->Accessories->Terminal) and write or paste:
```
lspci
```
then press ENTER, and paste the output here. You may need to use the windows drivers.

EDIT: If it's a USB adapter, run this instead:
```
lsusb
```
and post the output.

---

### Post by hmfai on 2008-06-17
lsusb

```
Bus 002 Device 005: ID 054c:0243 Sony Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 003: ID 2001:3b00 D-Link Corp. [hex]
Bus 001 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp.
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by RomeReactor on 2008-06-17
Sorry for the tardiness. It seems you need to download a driver:
```
wget http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2?modtime=1202678385&big_mirror=0
```

Anfter it finishes, you should have a file called **acx-20080210.tar.bz2** in your home directory. Right-click on it, select 'Extract here', and you should get a folder called **acx-20080210**.

Now please post the output of:
```
uname -r
```

---

### Post by hmfai on 2008-06-18
```
2.6.24-16-generic
```

---

### Post by RomeReactor on 2008-06-18
Also post the output of this:
```
 ls /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/
```
and the *complete* output of this:
```
sudo lshw -C network
```

There's the possibility of not having to use to use the windows drivers for your USB wireless, but keep them at hand in case they're needed. It seems your card is somewhat tricky to get going.

---

### Post by hmfai on 2008-06-18
ls /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/

```
adm8211.ko    b43         libertas       prism54         wavelan.ko
airo_cs.ko    b43legacy   netwave_cs.ko  ray_cs.ko       wl3501_cs.ko
airo.ko       bcm43xx     orinoco_cs.ko  rt2x00          zd1201.ko
arlan.ko      hermes.ko   orinoco.ko     rtl8187.ko      zd1211rw
atmel_cs.ko   hostap      p54common.ko   spectrum_cs.ko
atmel.ko      ipw2100.ko  p54pci.ko      strip.ko
atmel_pci.ko  ipw2200.ko  p54usb.ko      wavelan_cs.ko
```

sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:40:05:31:7b:19
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

As for the Windows driver, the driver I downloaded on D-Link was an installation of a utility that handles the wifi adapter. These was no .inf file or such.

Thanks for the constant input. I really appreciated.

---

### Post by alspal on 2008-06-18
Hello I am an absolute newbie to ubuntu/linux and have similiar problems installing my dlink g510 network card and connecting to existing network. So far I have had success installing the card but now i have problems connecting to network. something like 
no dcpoffers recieved when i run iwconfig. please help i have been at it for weeks. thank you

---

### Post by RomeReactor on 2008-06-18
Hi alspal. Have you searched the forums for your wireless model?  If you haven't been able to find information on it, it would probably be a good idea to start a new thread, since your card is different form the one here.

hmfai, please post the output of:
```
ls /lib/modules/2.6.24-16-generic/ubuntu/wireless
```

If you see a folder named **acx**, then the drivers are already installed. It may be a matter of configuring your card, or if we're unable to get the card going with those drivers, we'll probably need to download windows drivers and use NdisWrapper.

---

### Post by hmfai on 2008-06-18
yes. There is a folder named acx.

---

### Post by RomeReactor on 2008-06-18
Had to go away for a while; sorry.

Have you tried configuring your wireless card in Network Manager? Or using WICD instead of NM? Have you tried installing the windows drivers with NdisWrapper before?

The output of lshw -C network doesn't show a driver for your card. By the looks of it, you'll need NdisWrapper and the windows drivers. If you don't have them:
```
wget ftp://ftp.dlink.com/Wireless/dwl120+/Driver/Wavelink/dwl120+_driver_102.zip
```

Make a folder (name it whatever you want) and place the **Setup.exe** file there. Are you posting from your Ubuntu system--meaning, do you have wired internet? If so, you need to install ndiswrapper, cabextract and unshield:
```
sudo aptitude install cabextract unshield ndiswrapper-common ndiswrapper-utils-1.9
```

Please post back with the answers.

---

### Post by hmfai on 2008-06-18
Is it possible to install ndiswrapper without internet?
I don't have internet connect on my other computer...

---

### Post by hmfai on 2008-06-18
Does the ndiswrapper here work?

[http://ndiswrapper.sourceforge.net/joomla/index.php?/content/view/23/2/](http://ndiswrapper.sourceforge.net/joomla/index.php?/content/view/23/2/)

---

### Post by RomeReactor on 2008-06-18
There are Ubuntu packages that are easier to install, but first we need to know: Is this computer running Ubuntu also? Is your other computer--the one we're trying to get wireless working--running Ubuntu 32-bit, or 64?

---

### Post by oldsoundguy on 2008-06-18
noticed that no one has mentioned using System> Administration> network ... sign in ... highlight the wireless connection and shut off roaming.  Then select your network and enter your wep code.  

I have two 510 cards in Gutsy machines that work perfectly.

---

### Post by hmfai on 2008-06-18
I am running on Windows XP in this computer.
The one I am trying to get the wireless working is running Ubuntu 32-bit.

oldsoundguy:
I don't have the wireless connection option in the network manager.

---

### Post by RomeReactor on 2008-06-18
These are the packages you need to download:

* [ndiswrapper-common]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb")

* [ndiswrapper-utils-1.9]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb")

Move them to your Ubuntu system and first double click on ndiswrapper-common to install it, then ndiswrapper-utils. You can follow cazique's instructions to install the windows drivers [in this thread]("http://ubuntuforums.org/showthread.php?t=525750&page=2"), which discusses the same card as yours; the last post links to another thread which might be useful. Please post back with the results.

EDIT: Here are the .sys and .inf files, so you don't need to install cabextract and unsheild. Extract them in your home folder on your Ubuntu system, and follow cazique's instructions; just remember to change **windowsdriver.inf** to **tiacxusb.inf** in the fifth step.

---

### Post by hmfai on 2008-06-18
It still doesn't work...

I installed ndiswrapper and the driver.
After I plug the adapter back in, it seems like Ubuntu doesn't recongize it as a wifi adapter.

nothing came up when I use
sudo lshw -C network

---

### Post by RomeReactor on 2008-06-18
Did you blacklist the acx module and removed it from the kernel before installing the driver with ndiswrapper? Did you check if the driver installed correctly?
```
ndiswrapper -l
```

Also post the output of:
```
ifconfig -a
```
and
```
iwconfig
```

Have you rebooted since?

---

### Post by hmfai on 2008-06-18
I did reboot but still no luck.

ndiswrapper -l

tiacxusb : driver installed

ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64600 (63.0 KB)  TX bytes:64600 (63.0 KB)



iwconfig

lo        no wireless extensions.

The acx module was removed.

---

### Post by RomeReactor on 2008-06-18
> **hmfai said:**
> ipconfig -a
I can't run the commend.

Make sure you run it as **ifconfig -a**, though I imagine that's just a typo.

I'm more than a little rusty on installing wireless drivers with NdisWrapper, but it looks like cazique missed a couple of instructions:
```
sudo depmod -a
```

```
sudo modprobe ndiswrapper
```

**ndiswrapper -m** should be run as root:
```
sudo ndiswrapper -m
```

and
```
sudo echo "ndiswrapper">/etc/modules
```

After running that, reboot and post again the output of:
```
sudo lshw -C network
```
```
ifconfig -a
```
and
```
iwconfig
```

---

### Post by hmfai on 2008-06-18
yea... sorry for the typo.. been a windows user for few years#-o

anyway, when i type these

sudo echo "ndiswrapper">/etc/modules

i got
bash: /etc/modules: Permission denied

---

### Post by RomeReactor on 2008-06-18
That's odd; let's see the contents of the file:
```
cat /etc/modules
```
if you don't see **ndiswrapper** in there, try:
```
gksudo gedit /etc/modules
```
this will open the file in gEdit, the text editor. Once it's open, add **ndiswrapper** as the final line--not on the same line as the last entry. Save the file, close it, reboot, and run the last three commands from my previous post.

---

### Post by hmfai on 2008-06-18
sudo lshw -C network still have nothing come up..
other two are the same

iwconfig

fai@fai-desktop:~$ ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71300 (69.6 KB)  TX bytes:71300 (69.6 KB)
```

fai@fai-desktop:~$ iwconfig
```
lo        no wireless extensions.
```

---

### Post by RomeReactor on 2008-06-18
Does your wireless USB have an on/off switch? If it has a light, is it blinking?

EDIT: From your last output of ndiswrapper -l, it seems Ubuntu doesn't recognize your USB as being plugged in:
> **hmfai said:**
> I did reboot but still no luck.

ndiswrapper -l

tiacxusb : driver installed

The output should read:
```
tiacxusb : driver installed
	device (2001:3b00) present
```

---

### Post by hmfai on 2008-06-18
These is two lights.

The power light is solid but the Link, which i assume it represents the connectivity, is not on/blinking.

When I tried modprobe acx and rmmod ndiswrapper and re-plug the wifi adapter, the link light is blinking but i think ubuntu decteced that as  ethernet connection.

---

### Post by RomeReactor on 2008-06-18
Did you try configuring it with Network Manager then? As far as I know, the acx module is the one that wasn't working from the beginning. When did you remove the NdisWrapper module (rmmod ndiswrapper)?

---

### Post by hmfai on 2008-06-18
weird...
now the device id is shown 2001:3b01 instead of 2001:3b00 in lsusb

There is no wireless network in Network Manager when I was trying out the acx module...

---

### Post by RomeReactor on 2008-06-18
Does **ndiswrapper -l** show it too? If so post the output of **ifconfig -a** and **iwconfig**; if iwconfig and ifconfig show your wireless as **wlan0**, run:
```
iwlist wlan0 scanning
```
If it changed desgnation (ra0, ra1, eth1), change the command accordingly

---

### Post by hmfai on 2008-06-18
ndiswrapper -l doesn't show it...

---

### Post by RomeReactor on 2008-06-18
Did you blacklist acx again (in **/etc/modules**), and removed it (**sudo rmmod acx**), then reinserted ndiswrapper (**sudo modprobe ndiswrapper** and **sudo ndiswrapper -m**)? If not, do it and run iwconfig and ifconfig again.

---

### Post by hmfai on 2008-06-18
acx is still blacklisted and i reinserted ndiswrapper,
but it still doesn't work...

---

### Post by RomeReactor on 2008-06-18
I have no more suggestions at the moment; Ubuntu not recognizing the USB might have to do with plugging it before booting the system, or afterwards. I don't use USB adapters, so my experience with them is practically null. Hopefully someone else can offer more adequate advice. Sorry.

---

### Post by hmfai on 2008-06-19
I seem to able to get Ubuntu regonize the usb adapter by inserting the acx module and removing it(With ndiswrapper on for all the time). I was able to see my wireless connection in Network Manager; however, i wasn't able to connect to it.

fai@fai-desktop:~$ sudo lshw -C network
```
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:40:05:31:7b:19
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+tiacxusb driverversion=1.52+D-link,08/08/2003,3.0.32.1 link=no multicast=yes wireless=IEEE 802.11b
```

fai@fai-desktop:~$ ndiswrapper -l
```
tiacxusb : driver installed
	device (2001:3B00) present (alternate driver: acx)
```

fai@fai-desktop:~$ iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Channel:0  Access Point: Not-Associated   Bit Rate:22 Mb/s   
          Tx-Power:0 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

fai@fai-desktop:~$ ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.0 KB)  TX bytes:1100 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:31:7b:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11012 (10.7 KB)
```

Thanks RomeReactor for the constant input. I really appreciated. :wink:

---

### Post by RomeReactor on 2008-06-19
Hi again. Sorry no one else has jumped in to offer you more help; it seems your USB wi-fi is particularly problematic. While you wait for someone to comment here, try the Ubuntu IRC channel (#ubuntu in irc.ubuntu.com or irc.freenode.net).

EDIT: Posted before seeing your reply.

Have you tried leaving the acx module inserted? ndiswrapper -l lists both, but uses the windows driver (tiacxusb). If your system recognizes the USB, then I think we can continue.

---

### Post by hmfai on 2008-06-19
Yes. I have tried leaving the acx module inserted but still no luck.
Also I have tried manual setting in Network Manager with dhcp setting, but it still doesn't work.

---

### Post by RomeReactor on 2008-06-19
If you manage to get your system to recognize the USB again, try leaving Network manager in 'Roaming' mode. Also, make sure you turn off the encryption--if any is in effect--in your wireless router to make it easier to establish a connection. Afterwards you can enable it again.

You could also try installing [WICD]("http://wicd.sourceforge.net/download.php"). Just take note that it will uninstall Network Manager, though I've found it to be very good. Since you don't have internet on your Ubuntu system, don't follow the instructions to add the repository, but do follow the ones regarding the tray icon. You can get it [here]("http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0").

---

### Post by oldsoundguy on 2008-06-19
do not know if this has been asked but, have you tested the USB port by plugging in some other USB device to see if the port itself is working properly?  Reason I asked is had this issue on a ladies Windows box recently and it turned out that USB was not activated in the BIOS and when we turned it on, I tested it with a printer and it was seen but did NOT work.  Moved to another port and all was well. (but Windows is a notoriously bad manager of USB devices.)  Still worth a look.

---

### Post by fisho on 2008-06-19
try this easy as but you may have to remove other u have installed, do a fresh install follow tute bingo wireless working

[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

---

### Post by hmfai on 2008-06-19
Thanks! RomeReactor. 
After some trial and error I was able to connect to the internet with WICD. :)

However, I can only connect to the internet when I don't use any encryption. When WEP encryption is enabled, I can't connect to the internet...
any suggestions to fix this?

---

### Post by RomeReactor on 2008-06-19
Did you make sure the only interface in **/etc/network/interface** was **lo**?
```
auto lo
iface lo inet loopback
```

Also, according to [WICD's faq]("http://wicd.sourceforge.net/wiki/doku.php?id=faq#why_doesn_t_my_wep_wpa_key_work"), you may need to wrap your key in quotation marks when writing it in the text box.

[This thread]("http://ubuntuforums.org/showthread.php?t=527159") may be of help.

Glad you managed to get it working!

---

### Post by hmfai on 2008-06-19
Thanks, but i have to be out now. I will report back when I get it working.
Thanks!

---

### Post by hmfai on 2008-06-21
It won't connect whenever WEP enabled. Tried putting the key in quotation marks but it still doesn't work. I also tried assigning a static ip to it but still no luck. Manually configurate the network doesn't work either...

---

### Post by RomeReactor on 2008-06-21
Are you using WICD now, or Network Manager? If you're using NM, leave it in 'Roaming' mode.

Did you try using WPA as posted in [this thread]("http://ubuntuforums.org/showthread.php?t=527159"), starting with post #4?

In the meantime, you can at least set up MAC filtering in your router.

---

### Post by hmfai on 2008-06-22
I've tired both WPA and WEP, but it still doesn't work... so i just decide to use MAC filter instead.

However, I still have one more question. Is it possible to setup a script that run after Ubuntu finish booting up? The problem I have is that if my computer's power is off completely(no power to the USB device when computer is off), I will have to insert acx manaually for my wifi adapter to work again. I've tried not to blacklist acx but it doesn't work. If acx is not blacklisted, I have to remove the acx module, and insert it again and replug the wifi adapater for ndiswrapper to see it. 

Thank you very much for answering my questions. It really helped a lot for making the transition from Windows to Ubuntu. I've learned a lot from the answers and searching around google and forums.

---

### Post by RomeReactor on 2008-06-22
Make sure acx is not in /etc/modprobe.d/blacklist, and try adding **acx** to /etc/modules:
```
sudo echo "acx">/etc/modules
```
Then reboot.

If you still get the same problem, try:
```
sudo modprobe acx
```
and reboot again. After booting up, if the wireless still isn't working, try:
```
sudo dhclient wlan0
```
If your wireless device has a different designation, substitute wlan0 accordingly.

If you want to undo these steps:
[COEDE]gksudo gedit /etc/modules[/CODE]
and remove **acx**; and
```
sudo rmmod acx
```
then reboot.

It might also be a good idea to try a post in the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section. People there are bound to be more knowledgeable about wireless than me.

---

