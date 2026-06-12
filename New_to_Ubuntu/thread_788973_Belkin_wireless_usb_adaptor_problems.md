---
title: "Belkin wireless usb adaptor problems"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by gazz1982 on 2008-05-10
I installed the ndiswrapper (utils,commomn and the other one)

I followed these instructions: [URL="http://blog.mcnicholl.com/2008/03/11/ubuntu-710-gutsy-and-belkin-usb-wireless-networking/"]http://blog.mcnicholl.com/2008/03/11/ubuntu-710-gutsy-and-belkin-usb-wireless-networking/
[/URL]

Then I restarted the connection but it came up with this:

Listening on .....
Sending on .....
DHCPDISCOVER on ....(this came up 4 times with different intervals)
No DHCPOFFERS recieved.
No workingleases in persistent database - sleeping.



the Belkin usb thingy flashes and shows up on the lsusb command, any ideas where I should be looking to try to fix this?

Thanks

---

### Post by BorisDBlade on 2008-05-10
are you on Gutsy or Hardy? Check belkin's website for new drivers native to linux. I had a pcmcia belkin wireless card when I had Fedora Core 1 installed years ago, ndiswrapper never worked for it. But new distros are supporting more and more wireless options and distributors. If you can return the usb to the retailer, I think linksys has a better chance of working, but I'm not 100% sure of that....but keep trying till you run out of options. Sorry this doesn't help much

---

### Post by james_vanb on 2008-05-10
I have Belkin F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin rt73. Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules (or gedit if using ubuntu)

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

This also worked for a Zonet ZEW 1502, without blacklisting anything.

---

### Post by abn91c on 2008-05-10
I have the same usb adapter, could not follow the suggestions here in these forums, however i installed dreamlinux 3.0 and it worked "out of the box", meaning dreamlinux detected it during set up and its running on my other 10 yrd old 400mhz intel celeron desktop pc

---

### Post by ubume2 on 2008-05-23
I didn t get a connection out of the box like abn91c, but I got it to work.

I have a Belkin USB adapter for my wireless desktop. I tried all that ndiswrapper stuff, and finally discovered I didn t need to do all that. I am using a WEP connection. The essid is hidden.

I have 8.04 on my hard drive, but I was fiddling with 7.10 on Live CD the other day and got an internet connection.  You would probably have to go through the ndiswrapper routine with Dapper 6.06.

Do an ```
sudo lshw -C network
``` and report what it says.

My wireless is eth1, and here is what I did:

```
ifconfig eth0 down

 ifconfig eth1 down
 dhclient -r eth1
 ifconfig eth1 up
 iwconfig eth1 essid "enteryouressid"
 iwconfig eth1 encryption on
 iwconfig eth1 key <enterkey> ASCII
#iwconfig eth1 mode Managed  ---I didn t need this
 dhclient eth1
```

Enter those from the terminal. Put sudo in front of each command. See if it works.

---

### Post by Fenris_rising on 2008-05-23
follow this link to the tut i used. if you have the driver cd for your dongle you need the 'inf' and the 'sys' files from it. put them in a folder called drivers as instructed from LINE 3 of the tut. its worked for my belkin, another unbranded USB adapter i have and my PCI wireless card. take your time its a good tut.

[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)
__________________

---

