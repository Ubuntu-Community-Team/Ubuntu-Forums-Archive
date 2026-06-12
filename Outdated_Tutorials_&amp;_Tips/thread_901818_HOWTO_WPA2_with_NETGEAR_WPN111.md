---
title: "HOWTO: WPA2 with NETGEAR WPN111"
date: 2008-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by itsjareds on 2008-08-26
**[SIZE="3"]This tutorial was written and tested for Ubuntu 8.04 and 8.10. If you are using Ubuntu 9.04, please see [this post]("http://ubuntuforums.org/showpost.php?p=7487917&postcount=3").[/SIZE]**

--------------
The NETGEAR WPN111 doesn't connect easily with Ubuntu. If you're reading this post, then you're probably having trouble as well. 
This tutorial will let you connect to the internet with a WPN111 adapter using WPA2 encryption.


I was able to connect on two of my computers, both are running 32bit Ubuntu (sorry 64bit users, NETGEAR hasn't released a 64bit driver). 

Step-by-step:

**1.** Install ndiswrapper-common, ndiswrapper-utils, ndisgtk, and wicd. I provided attachments to the versions that I used -- these have worked. Other versions may work but haven't been tested.

Download these packages here - [ATTACH]83059[/ATTACH]

I provided only i386 versions of everything because NETGEAR hasn't released a x64 bit version of their driver. Only 32 bit Ubuntu will work.

Before installing wicd, you must uninstall networkmanager. Go to System -> Administration -> Synaptic Package Manager. Search for "networkmanager".

Mark for complete removal. This will uninstall another package (I can't remember the name). Click OK. After this, you can install Wicd fine.


**2.** Install your driver in ndisgtk. Go to System -> Administration -> Windows Wireless Drivers. Click "Install Driver" and locate your .inf file in your Windows partition, if you are dual-booting. For me, it was located in /host/Program Files/NETGEAR/WPN111/Driver. If there are two .inf files, install both of them. Otherwise, just install the single one.

If you are not dual-booting, find another computer with internet to download the software from [the NETGEAR site]("http://kbserver.netgear.com/products/wpn111.asp"), if you do not have the software already. Alternatively, you can download my attachment of the same v2.0 driver I used - [ATTACH]83057[/ATTACH]

Select the 2.0 version of the driver if possible, this will allow you to re-plug your adapter if it ever gets unplugged on accident. The 1.1 version will not allow you to do this. The 2.0 version is also better because NETGEAR condensed their driver to one .inf file, rather than two. This just speeds up the process.


**3.** With any luck, you should see your adapter light blinking once you installed the driver. We're almost connected. Open Wicd (Applications -> Internet -> Wicd) and click "Preferences". Change "Wireless interface" to "wlan0". You can also optionally set your DNS servers -- mine are for OpenDNS. The server numbers are 208.67.222.222 and 208.67.220.220.

Click OK, then click "Refresh". Your adapter should scan and display the list of networks nearby. Open your network tree, then open the "Advanced settings" tree. Look down to "Use Encryption". Check it, change the password type to WPA 1/2, and type in your ASCII password in the field. Once you have this done, you can click connect!

Here is what it says in my status when connecting (my ESSID is Charlotte Martin):
> 
Charlotte Martin: Obtaining IP Address


If you see this, then you will connect. When you are officially connected, it will say "Connected to Charlotte Martin". Open up Firefox and go to Google, it will come up!


All attachments:

[ATTACH]83059[/ATTACH] contains ndisgtk, ndiswrapper, and wicd

[ATTACH]83057[/ATTACH] contains the WPN111 driver files (Version 2.0)

---

### Post by aolias on 2008-11-10
Hi I have followed your tutorial and for me it does not work

I am using Ubuntu 8.10

WPN111 v2 and v2.1
ndiswrapper 1.53 (the one provided with Ubuntu)
WICD the version for Ubuntu Intrepid.

I also upgraded the firmware of my router to the latest version.

WEP is working fine with no problem.  WPA2 at the WICD seems to validate the password but gets stalled while getting an IP address. 

This afternoon I will give a try at home with static IP address to see if that makes any difference, and I will post the results.

Cheers
Alfonso

---

### Post by itsjareds on 2009-06-20
Update: I recently re-installed Ubuntu with Jaunty. I uninstalled a few months ago after I couldn't keep my connection stable (constant random disconnects). Anyways, I found that this solution does not work in Jaunty, at least for me using the same computer. Here's the way I got my adapter to receive signal in Jaunty:

1. Installed the packages I attached on the first post. These are still needed.

2. Install your NETGEAR driver in ndiswrapper (For a GUI, use ndisgtk at System > Admin. > Windows Wireless Drivers).

3. Open Wicd at Applications > Internet > Wicd Network Manager. Once the window is open, find and click the Preferences button at the top.

Set your _WPA Supplicant Driver_ to **wext**, not ndiswrapper. Using the command line shows that ndiswrapper doesn't seem to work. You still need ndiswrapper to get your adapter blinking. Then, set _Wireless interface_ to "wlan0". Close the preferences.

4. Refresh the connections list by clicking the Refresh button. Then, find your network and select it, and open the Advanced Settings section. Select _Use Encryption_ and set your encryption type to WPA 1/2 (Passphrase). Enter your passphrase in the text box next to it.

5. You should be good to go. Try connecting, you'll be happy to see that it worked.

6. *UPDATE* I've been able to reconnect ONE TIME after losing connection. This is possible if you install ndiswrapper v1.55 from the source ([download page]("http://sourceforge.net/projects/ndiswrapper/files/")).

Then, run my script in the attachments when you lose connection (reinstalls the wireless driver on ndiswrapper). This only has partial success, it will only work after the first time you lose connection and it doesn't always work. It's better than nothing. 

Make sure before you run the script to change the location of the .inf file that your netgear driver is saved in. If you point it to your existing ndiswrapper driver folder, it won't work because ndiswrapper deletes that directory when uninstalling a driver. Create another folder with your driver and point to that .inf file.

If you have any problems, please ask me. I wrote this *after* I successfully connected, and don't want to risk messing up my delicate connection again by re-doing it. I may have skipped a step accidentally, so don't hesitate to ask.

---

### Post by deankovell on 2009-06-29
I tried your installation how to for jaunty. but when I opened up the wicd and changed the settings to what you suggested It still wouldn't recognize any networks at all. your how to for 8.04 said to uninstall network manager. I couldn't find networkmanager in jaunty. Is it called something different or has it been replaced with another program that I need to shut off before wicd will work. this is just my 3rd day using linux.  It's a bit confusing and I don't want to mess up the system. help is greatly appreciated.

---

### Post by itsjareds on 2009-06-29
If you have Wicd already installed, network-manager should have already been uninstalled (You are forced to uninstall network-manager before installing wicd).

Try running these two commands in the terminal (Applications > Accessories > Terminal). You probably forgot the dash between "network" and "manager" :P

```
sudo apt-get remove network-manager
sudo apt-get autoremove
```

---

### Post by itsjareds on 2009-08-04
Alright, I was finally able to get a new adapter, a Rosewill RNX-EasyN1. I've got that driver installed now and I should hopefully have a stable connection now. I still have the WPN111, so if anybody needs me to do testing for it, I will.

Thanks for all the support shown so far, I (and I'm sure many others) really appreciate it.

---

### Post by PeaSoup on 2009-10-02
I'm trying to get WPN111 Netgear stick to work with Ubuntu 9.04 on a 64 bit machine.  The tutorial above specifies 32 bit only. Any advice on how to get it working with 64 bit?

Zero experience of Ubuntu / Linux generally so any hand-holding much appreciated!

---

### Post by itsjareds on 2009-10-02
Sorry, there is no 64bit version of the WPN111 driver, not even for Windows. Many Vista users have complained about this to Netgear but so far no 64bit driver has been released.

If possible, I would recommend getting a different wireless card as the WPN111 is a pain in the neck to get working on Ubuntu. I switched to a Rosewill RNX Easy-N1 (usb adapter) which has native drivers for Linux (Ralink chipset).

If you can't get a different card, you will need to install 32bit Ubuntu to install the 32bit version of the WPN111 driver. I hope this isn't too much of an issue for you if this is the route you have to take.

---

### Post by PeaSoup on 2009-10-02
Not checked it yet, but do you happen to know if there's a 64 bit version of the WG111v2? I could actually use that instead...

---

### Post by PeaSoup on 2009-10-02
Gulp. I really do feel silly. I got the WG111v2 working and I don't think its because of any of my prior fiddling. It seems to work straight out of the box without any driver installations, when I just click on the wireless connections bit at the top right of my screen and select my normal connection details.

[http://ubuntuforums.org/showthread.php?t=1135835&highlight=WG111v2](http://ubuntuforums.org/showthread.php?t=1135835&highlight=WG111v2)

On the other hand I don't think that works for the WPN111.

---

### Post by itsjareds on 2009-10-02
So you are good with the WG111 adapter? Glad to hear it :)

edit: For anyone who is still having issues and needs to install the 64bit driver, there IS a 64bit driver for the WG111v2. It is available from the Netgear website.

[http://kb.netgear.com/app/answers/detail/a_id/713]("http://kb.netgear.com/app/answers/detail/a_id/713")

You need to install that driver software in Wine, then take the correct .inf file from the installation.

---

### Post by Sir Thingie Of Whatsit on 2009-10-23
> **itsjareds said:**
> Update: I recently re-installed Ubuntu with Jaunty. I uninstalled a few months ago after I couldn't keep my connection stable (constant random disconnects). Anyways, I found that this solution does not work in Jaunty, at least for me using the same computer. Here's the way I got my adapter to receive signal in Jaunty:

1. Installed the packages I attached on the first post. These are still needed.

2. Install your NETGEAR driver in ndiswrapper (For a GUI, use ndisgtk at System > Admin. > Windows Wireless Drivers).

3. Open Wicd at Applications > Internet > Wicd Network Manager. Once the window is open, find and click the Preferences button at the top.

Set your _WPA Supplicant Driver_ to **wext**, not ndiswrapper. Using the command line shows that ndiswrapper doesn't seem to work. You still need ndiswrapper to get your adapter blinking. Then, set _Wireless interface_ to "wlan0". Close the preferences.

4. Refresh the connections list by clicking the Refresh button. Then, find your network and select it, and open the Advanced Settings section. Select _Use Encryption_ and set your encryption type to WPA 1/2 (Passphrase). Enter your passphrase in the text box next to it.

5. You should be good to go. Try connecting, you'll be happy to see that it worked.

6. *UPDATE* I've been able to reconnect ONE TIME after losing connection. This is possible if you install ndiswrapper v1.55 from the source ([download page]("http://sourceforge.net/projects/ndiswrapper/files/")).

Then, run my script in the attachments when you lose connection (reinstalls the wireless driver on ndiswrapper). This only has partial success, it will only work after the first time you lose connection and it doesn't always work. It's better than nothing. 

Make sure before you run the script to change the location of the .inf file that your netgear driver is saved in. If you point it to your existing ndiswrapper driver folder, it won't work because ndiswrapper deletes that directory when uninstalling a driver. Create another folder with your driver and point to that .inf file.

If you have any problems, please ask me. I wrote this *after* I successfully connected, and don't want to risk messing up my delicate connection again by re-doing it. I may have skipped a step accidentally, so don't hesitate to ask.


[COLOR=Pink][SIZE=3][FONT=Verdana][COLOR=Black]Hello there.  Do I still need to un-install "Network Manager"?[/COLOR]
[/FONT][/SIZE][/COLOR]

---

### Post by itsjareds on 2009-10-24
You could give it a try with NetworkManager, but I never had any success (never tried too hard). I wish I could test it now but I don't have this adapter anymore.

---

### Post by fierypianist on 2009-11-15
Hi, I installed ubuntu with my friend today, and it's great! after he left, I got to work on setting up the Internet. I have followed all of your steps succesfully with the WPN111 adapter, and it's worked fine, so far. The only problem is, that when I refresh the network list, nothing shows up!! Please help me with this!

---

### Post by itsjareds on 2009-11-16
Hi, thanks for following my tutorial. Just a warning that I'm not a linux guru (yet) so I might not know it all :). I just posted this howto with what information I gathered while figuring it out myself.

Can you open a terminal (Applications > Accessories > Terminal) and type "iwconfig" with no quotes? Please copy and paste the output from the terminal and post it in a [code] tag.

---

### Post by Sir Thingie Of Whatsit on 2009-11-20
Hey itsjareds.  Downloaded your drivers and followed your instructions.  Worked like a charm.  Many thanks :).

---

### Post by itsjareds on 2009-11-20
Have fun :D

---

### Post by fierypianist on 2009-11-22
I did what you said and it came up with:
alec@Alec-comp:~$ iwconfig
lo                no wireless extensions

eth0            no wireless extensions

wlan1          IEEE 802.11g       ESSID: "NETGEAR"
                    Mode:Managed    Frequency:2.437  GHz  Access Point: 00: 1E: 2A: 50: 0B: 86
                    Bit Rate=54 Mb/s
                    Link Quality:40/100   Signal level: -70 dBm Noise level: -96 dBm
                    Rx invalid nwid:0 Rx invalid crypt:0  Rx invalid frag:0
                    Tx excessive retries:0   Invalid misc:0  Missed beacon:0

by the way, my network NETGEAR is now showing up when I use wlan1 instea of wlan0. The problem is, when I click connect, it loads for a minute or so, and then nothing happens...   Please help!

---

### Post by itsjareds on 2009-11-22
Which network manager are you using? I would recommend installing Wicd. If you haven't changed your network manager then you are using NetworkManager Applet (default). With Wicd you can change the scanning interface to wlan1 if that is what works.

---

### Post by james2c19v on 2009-12-28
I just wanted to update this thread for anyone using Karmic Koala 9.10. With an out of the box installation, I used the wired connection to download and install the three ndis packages mentioned in the first post (common, utils, and the GUI). I used the GUI to install the driver attached to the first post, and it worked. No fiddling, no uninstalling of network managers, etc.

I should note however that the GUI gave me some odd messages. When I chose the INF file, it said "could not detect hardware" or something, and yet in the left pane it said the opposite. Also, the "network configuration" button in the GUI didn't work. I just went through the network applet that's in the GNOME panel.

I'm only using WEP, so I don't know if it works with WPA.

---

### Post by Areleos on 2010-04-05
Do you have 32 or 64 bit installed?

Didn't seem to work for me... Although I did get the same messages

---

### Post by kmarien on 2010-04-05
Your how to works for me on Ubuntu 9.10 Karmic.

However, when I restart (reboot) the system, the led stays lit (blinking) and the WPN111 does not work anymore.

My solution for this is:

Shutdown the system and restart (to unload WPN111 and reload WPN111)

OR

unplug the WPN111 and plug it back in
and
use ndisgtk to remove and reinstall the driver


Does anyone knows a better solution for this problem?

---

### Post by itsjareds on 2010-04-05
> **Areleos said:**
> Do you have 32 or 64 bit installed?

Didn't seem to work for me... Although I did get the same messages

I had 32 bit installed -- NETGEAR has not released a 64 bit of the WPN111 driver, much to the chagrin of 64 bit Vista users.


> **kmarien said:**
> Your how to works for me on Ubuntu 9.10 Karmic.

However, when I restart (reboot) the system, the led stays lit (blinking) and the WPN111 does not work anymore.

My solution for this is:

Shutdown the system and restart (to unload WPN111 and reload WPN111)

OR

unplug the WPN111 and plug it back in
and
use ndisgtk to remove and reinstall the driver


Does anyone knows a better solution for this problem?

I don't know of a better solution, this same issue occurred for me when I used this wireless card. What I always did was, as the computer was restarting, before it booted into Ubuntu, I unplugged and replugged the adapter. Not sure what the issue was.

---

### Post by Areleos on 2010-04-06
I tried it with both and it didn't work either time... Might be that the encryption is WAP.

---

### Post by itsjareds on 2010-04-06
Not sure, I only had a WPA2 network to test it on, and it was tricky. I don't have the adapter anymore to test with, sorry, but if you find any method that works for you in the future, I'd like to hear it :)

---

### Post by eliseo.arias on 2010-06-13
> **itsjareds said:**
> Alright, I was finally able to get a new adapter, a Rosewill RNX-EasyN1. I've got that driver installed now and I should hopefully have a stable connection now. I still have the WPN111, so if anybody needs me to do testing for it, I will.

Thanks for all the support shown so far, I (and I'm sure many others) really appreciate it.

i do appreciate it :)

but i have a problem, i currently have 2 usb wireless adapters: the wpn111 and the rnx-easyn1. i followed your instructions to install the wpn111 and it worked, but i never got over the problem of the dropping connections.

that's when i decided to buy the rnx-easyn1, i followed the same instructions, just replacing the driver files, but i keep getting an error saying that the driver was invalid.

i used the driver that comes in the CD, so what could be wrong then?

would you mind elaborating on how did you manage to install the rnx-easyn1? or maybe post the driver files that you used.

thanks.

---

### Post by itsjareds on 2010-06-13
Since Karmic, using the RNX-EasyN1 has been much simpler. The driver is included by default. Now all you have to do to enable the driver is follow these steps:

```
sudo rmmod rt2800usb
sudo modprobe rt2870sta
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Then you may have to unplug and re-plug your adapter to allow the adapter to scan for networks. The last step I listed was to add rt2800usb to the module blacklist -- it seems that r2800usb was "overpowering" the driver/module that the RNX-EasyN1 needed, so disabling that one allows the correct driver to be used when rebooting.

---

### Post by eliseo.arias on 2010-06-13
oh so the drivers come with ubuntu already? i didn't know that...

i did a clean install and followed your steps, they worked to make the usb card detect the networks, but i was unable to connect to my home wireless. here's the output of each command:


```
$ sudo rmmod rt2800usb
ERROR: Module rt2800usb does not exist in /proc/modules
$ sudo modprobe rt2870sta
$ echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf 
blacklist rt2800usb
$
```after this the card was able to detect the networks. yet when i tried to connect to my network it didn't connect. it won't give me an error message either, it'll just spin for like a minute or two and then ask for my password again, if i enter it again it'll spin again and ask for it again, and so on. i use wpa2.

i also tried restarting the pc and even connecting to an unsecure network with no luck.

i'm no linux expert but i've seen people use dmesg, here's the output of mine:
```
$ dmesg | grep rt28
[   13.884724] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.928255] usbcore: registered new interface driver rt2870
$ 
```any idea what the problem could be?

---

### Post by itsjareds on 2010-06-13
Yeah, the drivers come in Ubuntu by default because Ralink (the maker of the chipset in our adapter) released a Linux version of the driver with configuration files and everything. There is not a Linux driver for the WPN111 so we had to rely on ndiswrapper, which was basically a way to use Windows network driver binaries in Linux.

I just always have to unplug and re-plug the adapter before I try to connect to any networks. I'm not sure what the issue is but that is quick and simple. I only have to do it that one time.

---

### Post by plaintiger on 2010-07-02
well! i followed these instructions in 10.04 and they showed no evidence of working, but then i read farther into the thread and found everybody talking about unplugging and replugging the adapter, so - with little hope, as i've tried to get this thing working many times and the one time i succeeded, a restart killed it once and for all - i unplugged the adapter and plugged it back in, then uninstalled and reinstalled the driver, and ta-dah! it works.

thanks a bunch everybody.  :)

---

### Post by loorjackal on 2010-10-20
i instald the inf using wirless network drivers and it says "invalid driver"  what did i do rong?

---

