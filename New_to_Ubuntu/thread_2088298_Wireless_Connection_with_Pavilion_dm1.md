---
title: "Wireless Connection with Pavilion dm1"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by SkystheLimit on 2012-11-26
At last got Ubuntu to run on my netbook from USB stick.  However, this message appears:

"
 [B]Network
  Disconnected – you are now off line

before I get to the options to install message.[/B]   
"

The computer conects fine under Win 7 so I guess there must be a setting somewhere to tweak but being new to this I haven't a clue.

Any help welcomed.

Best regards

Alan

---

### Post by mlentink on 2012-11-26
At the top right you will find an icon for network connections. Click it and enter your Wifi-details (SSID, passphrase) and it will connect. You can however also do this later if you choose to first try out Ubuntu.
I either case, just as Windows, Ubuntu needs the info to connect.

---

### Post by SkystheLimit on 2012-11-26
Thanks mlentink

OK, found the icon, selected it and now faced with questions I do not understand.

Under the Wireless Tab

[LIST=1]
[*]First of all Connection Name.  Is it important or not what the name is?  Should it relate to anything else?
[*]SSID - can't seem to find anything in Windows Control Panel Networks about this.  Should I be looking elsewhere?
[*]Mode - infrastructure or Ad hoc?
[*]BSSID - ?
[*]Device MAC address.  Now I have heard of this but more to do with mobile phones than computers.  Haven't a clue about this or where to find it.
[*]Cloned MAC address - see 5
[*]MTU,  Is set to automatic but there is an option for -+ bytes
[/LIST]
Under the Wireless Security it is set to None so I guess there must be a clue in Windows somewhere.


Under IPv4 Settings
Method - Automatic (DHCP) and a lot of other options greyed out.
Additional DNS servers:
Additional search domains:
DHCP client ID
There is a check box with "Require IPv4 addressing for this connection to compete" unchecked.  There is also a box marked Routes...


Under IPv6 Settings
Seems similar to the IPv4 page

The information that I do have is that it is a Sky Wireless connection.  I have a wireless network name (maye useful for the first question).  I have a password and a PIN.


Not very intuitive to me so far so I appreciate the help.


Best regards


Alan

---

### Post by mlentink on 2012-11-26
Did you try to right-click it? It should present you with a list of Wifi-networks available. Just click yours and it will ask you to enter the passphrase and then you're done.

---

### Post by wildmanne39 on 2012-11-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by SkystheLimit on 2012-11-27
Thanks for getting back.

Yes, if I right click I get a drop down menu with these options:

. Wired Network disconnected (greyed out)
. VPN Connections >
. Enable Networking (ticked)
. Connection information (greyed out)
. Edit Connections ...

Best regards

Alan

---

### Post by SkystheLimit on 2012-11-27
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

Thanks for helping.

Being new to this I was not sure how to copy that into the laptop (I am using the desktop to reply).

Anyway, I typed that carefully into the Terminal and have got this message:

--2012-11-27 09:03:25-- [http://dl.dropbox.xom/u/57264241/wirelss_script](http://dl.dropbox.xom/u/57264241/wirelss_script)
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known.  wget: unable to resolve host address 'dropbox.com'
ubunu@ubuntu:~$

Hope that means something to you.

Best regards

Alan

---

### Post by ozxpat on 2012-11-27
G'day,

Being a novice myself it took me quite a while to get to know the ins and outs of Linux. 
So in terms that even I can understand:
wget is use to download info from Internet. If your system cannot "resolve" the url then you either do not have an Internet connection or you have a DNS (Domain Name Server) problem.

I think you've come full circle; you can't download this piece of software until you get your WiFi network connected. Unless you have ethernet cable connected and working???

I know it doesn't help much but at least know your not alone in this world.

Ron

---

### Post by mlentink on 2012-11-27
> **SkystheLimit said:**
> Wired Network disconnected (greyed out)
. VPN Connections >
. Enable Networking (ticked)
. Connection information (greyed out)
. Edit Connections ...

Which means your laptop does not 'see' any wireless networks or, more likely, your network controller does not work
> **ozxpat said:**
> I think you've come full circle; you can't download this piece of software until you get your WiFi network connected. Unless you have ethernet cable connected and working??? Right on the nail Ron.
@SkystheLimit: do you have a wired connection available?

---

### Post by audiomick on 2012-11-27
G'day.
Ozxpat is dead right: wild man gave you some commands that tell your computer to go off and get a script out of the net and execute it to get info about your network setup. This is, of course, not going to work if you don't have a network connection. ;)

For your info, this is the script that was meant to be downloaded.
[http://dl.dropbox.com/u/57264241/wireless_script]("http://dl.dropbox.com/u/57264241/wireless_script")
No great magic there. I just copied the url out of the command.

The chmod in the command would make it executable and the bit after the last && would run it.

If you really want to, you could copy that script from that site and save it on your computer and run it, but that would mean a fair bit of dicking around.

I rather suspect that you are not getting a connection (we are talking about a wireless connection, aren't we? ) because your machine has a wireless card that wants a proprietary driver. My netbook, for instance, which has a Broadcom wireless card, does not get a connection when booted into the live environment, i.e. from a USB stick.

My advice would be, if you can possibly manage it, to hang the machine on a cable for starters. I personally would never do an install whilst relying on a wireless connection. If you can get onto a cable, that is almost guaranteed to work, and will allow the additional drivers mechanism to go and get any proprietary drivers you need. 

Is it 12.10 you are trying out? If so, this post
[http://ubuntuforums.org/showpost.php?p=12374153&postcount=8]("http://ubuntuforums.org/showpost.php?p=12374153&postcount=8")
tells you how to get to the additional drivers function. It is talking about video drivers, but it should be the same for all proprietary drivers.

If you have 12.04, I think you have to click on the cog wheel icon next to the search box in the dash, or search "additional" in the dash.

Anyway, see if you can get on to a cable, see if it offers you a proprietary driver for your wireless, and see if the wireless then works.

Oh yeah, you might like to post here what your wireless card is. 
Open a terminal (search "terminal" in the search box on the dash or do ctrl+alt+t) and do
```
sudo lshw -C network
```
You should see a list which will include the name of your wireless card and the name of the ethernet (cable) interface.

---

### Post by SkystheLimit on 2012-11-27
Hi Guys

First of all , thank you for yourvaluable time which is most appreciated.

OK, yellow cable connected, reboot and - nothing in the Networks box.  It is version 12.10

I typed the sudo lshw -C network and got a list.  It's a bit long to type each line accurately but here goes:

*-network[INDENT]description:Network controller
Product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:16 memory:9350000-93503fff
[/INDENT]*-network[INDENT]Description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Seminconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:26:9e:e3:56:d7
size: 100Mbit/s
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vdp bus_master cap_list rom ethernet physical tp mii 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:44 ioport:2000(size=256) memory:91410000-91410fff memory:9140000-9140ffff memory 91420000-9140ffff
[/INDENT]ubuntu@ubunto:-$ sudo 1shw -C network

I hope I got that all down correctly.

Best regards

Alan

---

### Post by audiomick on 2012-11-27
> **SkystheLimit said:**
> OK, yellow cable connected, reboot and - nothing in the Networks box.

...
*-network[INDENT]description:Network controller
Product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation

...


[/INDENT]*-network[INDENT]Description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Seminconductor Co., Ltd.



Well, the yellow cable is presumably the ethernet cable to the router. But it didn't give you a connection automatically?

Your wireless card is indeed a broadcom one. In fact, both the wireless card and the ethernet inteface are the same as in my Lenovo S10-2 netbook. As I think I mentioned, I had that booted to a 12.04 USB stick the other day. The wireless does not work until I have installed the proprietary drivers. The wired connection does.

To go back to this post of yours

> **SkystheLimit said:**
> Yes, if I right click I get a drop down menu with these options:

[COLOR="Blue"]. Wired Network disconnected (greyed out)[/COLOR]
. VPN Connections >
. Enable Networking (ticked)
. Connection information (greyed out)
. Edit Connections ...


Is the entry for "wired network" still greyed out? Can you choose to activate it?

---

### Post by wildmanne39 on 2012-11-27
Hi, 
Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
[COLOR="Red"]Please copy and paste for accuracy.[/COLOR]
Watch for errors
Thanks

---

### Post by SkystheLimit on 2012-11-27
Audiomick
Doing this from memory for reasons you will see later.

Yes, yellow lead is the ethernet cable.

Found one of the options in the dropdown (Wired Network - I think) and selected it and hey presto, network connected.  Great I thought, I could move on to Wild Man's advice.

Firefox loaded - and then things have gone awry.

I tried to type in the forum address and found the computer no longer responded to the keyboard.  It also didn't respond to mouse clicks but the cursor did respond.

This gave the problem about how to close down the computer and try again as nothing was responding so, I had to force a close down but holding down the power button.

Now, it will not reboot.

I get a purple screen followed a b+w one with lots of numbers and commands, followed by a purple screen with Ubuntu which looks like it is loading - then it hangs.

Following messages on the screen:
[  9.354960] xor: automatically using best checksumming function:
[  9.392012]  pIII_sse : 4584.000 MB/sec
[  9.393427] device-mapper: dmraid45:initialized v0.2594b

Nothing else happens with or without the ethernet cable connected.

Tried a reboot in Win7 and all systems functioning correctly.

Best regards

Alan

---

### Post by wildmanne39 on 2012-11-27
Hi, my last post is the answer to fix your wireless issue without an internet connection.

You might try unpluggin the ethernet cable and rebooting if that does not fix it start a new thread with a descriptive title for that issue because you can only have one issue per thread.
Thanks

---

### Post by audiomick on 2012-11-27
> **SkystheLimit said:**
> Audiomick
Now, it will not reboot.
Tried a reboot in Win7 and all systems functioning correctly.

This was all still with Ubuntu booted from a USB stick into the live environment, wasn't it? 

I'd say the worst thing that could have happened is that the files on the stick are messed up. I would suggest setting the USB stick up again. It is perhaps possible that the stick is no longer useable. I believe they don't like just having the power pulled on them.

See if you can format the USB stick from Windows and then set it up again.

---

### Post by SkystheLimit on 2012-11-28
Good day guys.

Reinstated the USB drive to former status (and made a back up just in case).

Running Ubuntu with ethernet cable connected.

Enable Networking Ticked
Connection Information - lots of numbers under this one
Edit Connections
[INDENT]Wired connection 1
Wireless - nothing showing

[/INDENT]Copied the b43 zip and opened it as requested

Opened a Terminal and pasted Wild Man's code - no errors were shown.

Opened Firefox and it seems to be working and responding correctly.

So, back to the wireless problem.  I might even be able to reply through Ubuntu next time.

Best regards

Alan

---

### Post by audiomick on 2012-11-28
> **SkystheLimit said:**
> (and made a back up just in case).
always a good idea.

> 
Copied the b43 zip and opened it as requested.
...
So, back to the wireless problem.

Actually, if the operation with the zip file worked as intended, your wireless should be working now.

Be that as it may, now that your cable connection is working, I would have suggested trying to activate the additional drivers function as previously mentioned and letting the system get the drivers it sees fit. If you have a working internet connection, this should work fine, and my experience is that the wireless card shown in your lshw output works fine with the drivers that the additional drivers facility supplies. Maybe you would like to try that.

Edit: just for your information, as far as I can tell from reading the man pages, these commands
```
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Would do
force removal of existing b43 module (if any present)
force removal of ssb module
add b43 module (which would be taken from the files out of the zip).

Should that have worked, the wireless modules in the linux kernel should have been replaced by those in the zip file. As far as I know, the additional drivers facility should see them, and offer to replace them if it has another one on offer that it thinks is better. There is nothing to say that the module in the zip file that wild man provided would not work, assuming that they are the right drivers for the wireless card, but if the wireless is still not working then something else needs to be tried. As I said, I would try the additional drivers facility before anything else.

---

### Post by audiomick on 2012-11-28
Hallo again. Just found this thread
[http://ubuntuforums.org/showthread.php?t=2087990]("http://ubuntuforums.org/showthread.php?t=2087990")

which you might like to read through as well. There seems to be some good advice in there for when things don't work as expected.

Edit: and another one
[http://ubuntuforums.org/showthread.php?t=2088976]("http://ubuntuforums.org/showthread.php?t=2088976")

Seems like that wireless card is being a bit of a pain at the moment....

---

### Post by SkystheLimit on 2012-11-28
First the bad news.  I closed the lid on the laptop, as I would with Windows, and upon reopening the cursor went rather 'sticky' and reluctant to go where desired.  Managed to get a shut down but Ubuntu wouldn't load when rebooted.

Restored back up to the USB drive and now the good news - I am sending this from the laptop, wirelessly.

I think that qualifies as a success so thank you for your guidance.  Maybe see you again sometime.

Best regards

Alan

---

### Post by audiomick on 2012-11-28
Great to hear it. Could you mark the thread as solved if you are satisfied? That is in the "Thread tools" drop down at the top of the thread.

---

### Post by wildmanne39 on 2012-11-28
Glad to help!
Enjoy

---

