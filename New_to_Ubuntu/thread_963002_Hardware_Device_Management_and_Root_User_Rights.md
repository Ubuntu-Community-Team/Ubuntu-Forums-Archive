---
title: "Hardware Device Management and Root User Rights"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by rrriles on 2008-10-29
I'm new to xubuntu.  Had great difficulty getiing a successful download, then of burning an iso that my old, old laptop would read.  I finally wound up making a successful installation of xubuntu 8.04.1 on my dell latitude cpi d266xt.

I ran the partition manager to set up a duel boot of xp and of xubuntu.  The reason I chose a linux distro is because xp runs to slow on my laptop and I figured that linux would be a less resource intensive operating system than xp.  I had previously installed a redhat distro on another old computer at work successfully and it didn't require much power from that old pc to operate at better speeds than any microsoft operating system that had been on it.

So... I now have xbuntu on my laptop, but I am not able to connect to the internet.  I can't even find the device manager in xubuntu to check and see what other hardware isn't functioning.

Also, I tried to use some commands I found in a help forum inside the terminal editor to solve my hardware issues, but I was prompted that I needed root user privileges to run these commands.

My questions are:

1. What's the best way to get my wireless card running? I have a Linksys RangePlus Wireless G notebook PC Card.

2. How do I give myself root user privileges?  Why didn't it create an admistative rights account for me during the install?

3. My mouse pad is only semi-operational. I don't have a right-click function on it.  How do I make the mouse pad work correctly?  When I opened the mouse section in ubuntu, it gave me a blank page, which I assume is for editing specific scripts for the mouse.

4. What's the best online source for complete documentation of xubuntu?  What I have found so far is somewhat basic and fails to give solutions quickly, without having to do extensive searches on what I consider the slowest pc I have ever used. I literally have been slogging through this install for about a week.  Some of that has been hampered by this dinasour of a laptop I'm trying to streamline with a linux distro.

Finally, I would like to say that I have virually no programming experience; however, I am an above average computer user who is basically the equivalent of an A+ technician.  I have worked for seveal comapnies running their networks and taking care of hardware, so I am fairly competent, but I have very little experience in linux.

Please give any suggestions you might think will help me.

Thank You.

---

### Post by randy78 on 2008-10-29
In Ubuntu (and a lot of other Linux distros), you grant yourself admin rights through sudo. 

You would type sudo to get root, i.e.: sudo apt-get install build-essential in a terminal(Menu>Accessories>Terminal) would install the build-essential package (just a random package I picked as an example). 

It will take some time to get used to (like anything else) but you'll come around.

Windows automatically grants admin rights, which is very dangerous for many reasons (beyond the scope of this thread) and Linux grants admin rights on an 'as needed' basis.

In a terminal, type lshw and post the output of it here.

Then, (in a terminal) type: ifconfig and see if an ip address has been assigned to a networking interface (eth0, eth1).

If nothing, try typing: sudo ifconfig eth0 up (you can try substituting eth1 for eth0 if eth0 doesn't work)
then type: sudo /etc/inet.d/networking restart

Let us know if this helps!

Also, check this out... it may help you with any future problems :)

[https://help.ubuntu.com/xubuntu/desktopguide/C/index.html]("https://help.ubuntu.com/xubuntu/desktopguide/C/index.html")

---

### Post by mfarquhar on 2008-10-29
*Randy78 beat me to it lol, and he sounds more experience than myself, so if my advice conflicts with his, probably listen to him ^_^*
> **rrriles said:**
> So... I now have xbuntu on my laptop, but I am not able to connect to the internet.  I can't even find the device manager in xubuntu to check and see what other hardware isn't functioning.

Also, I tried to use some commands I found in a help forum inside the terminal editor to solve my hardware issues, but I was prompted that I needed root user privileges to run these commands.

My questions are:

1. What's the best way to get my wireless card running? I have a Linksys RangePlus Wireless G notebook PC Card.If the GUI works, and you can get to the setting for it at Applications>System>Network, Do you have a Wireless Connection (most likely unactivated/unconfigured) listed there? if not you'll probably need to hit the command line.
try typing
```
lspci
``` at the terminal and let us know if it lists your wireless card there, my own wireless card shows up as an entry like this```
00:13.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```your own will be different, but I assume that it should at least say network controller (or similar) next to it
> 2. How do I give myself root user privileges?  Why didn't it create an admistative rights account for me during the install?Your main account that you set up during the install should have administrative rights via the "sudo" command (stands for SuperUserDo), this is usually limited  to the terminal, so if you're at the command line, just type ```
sudo <command you want to run>
```it should prompt you for your password, and then it should go right ahead.

If you try to change things in the GUI (graphical desktop), then anytime you try to access an administrative function it will prompt you for your password, and ussually let you in to do whatever you're doing. the place to look on the desktop for settings is under Applications>Settings and Applications>System

but due to your comments about the systems age below, the GUI may or may not be all that practical for you. I have somewhat similar concerns, as my desktop is close to 8 years old, but since you're on a laptop, you may be even more limited than I am.

Note: I'm still a novice myself at Linux/Ubuntu, so other posters should feel free to correct me where I'm wrong

---

### Post by randy78 on 2008-10-29
Excellent advice mfarquhar!

---

### Post by rrriles on 2008-10-30
[FONT="Verdana"][/FONT]Thank you all for your comments and advice. I will try them as soon as I get home from work today, as this beast of a machine takes too long to shut down and restart in xp to do it all while I eat breakfast before I go to work!:)

I really do apprecriate the community spirit around Ubuntu! Thanks again! And, I'll let you all know if these suggestions resolve my issues. Oh yeah, I did figure out how to run root last night, but still need to try the network controller commands you've suggested.

---

### Post by stalkingwolf on 2008-10-30
go to System > Administration > Synaptic Package Manager, Click Search.
Type in Device Manager, select the Xubuntu version, click apply and it
will download and install.

After you have an internet connection of course.

---

### Post by rrriles on 2008-10-30
Okay...
I tried some of your suggestions and I think I figured out the root stuff before, but I've been doing so many things to try to get this wireless working, that it's all turned into a bit of a blur, and I think I made a mistake previously by renaming my device to another name. As I stated, my wireless is a Linksys RangePlus G pcmcia.

Anyway... I used the folling commands and somehow missed the part about the info I was supposed to supply should be relevant to my specific device. OOps! So I copied the info I found on the Ububtu Wireless Troubleshooting section verbatim. Maybe I should slow down and read the entire page before I go haphazardly running commands! Doh!

I entered:

[COLOR="Blue"]sudo pccardctl indent[/COLOR]

and got nothing
so then I entered:

[COLOR="blue"]gksudo gedit /etc/pcmcia/config.opts
card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"After making this change run this command: 
  sudo kill -HUP `cat /var/run/cardmgr.pid`[/COLOR]

[COLOR="Black"]So when I entered:[/COLOR]
[COLOR="Blue"]sudo lshw -C[/COLOR]

I got this info back:

[COLOR="Red"]
*-network UNCLAIMED     
description: Network controller
product: AR5416 802.11abgn Wireless PCI Adapter
vendor: Atheros Communications Inc.
physical id: 1
bus info: pci@0000:01:00.0
version: 01
width: 32 bits
clock: 66MHz
capabilities: cap_list
configuration: latency=0
riley@ubuntu:~$ 
[/COLOR] 

Notice that the info about Atheros is almost exactly what I had input before? Nothing about Linksys RangePlus appears.

My questions are:
1. Is the system seeing my Linksys with some other info that I've attributed to it? What does 'network UNCLAIMED' mean?

2. What can I do to make this Linksys card work? Do I have to edit this device again or kill it and start over? What's the best solution?

3. Once the system does recognize my network controller, what's the best method to make it operational? I've read quite a bit of online manuals suggesting I use the ndiswrapper tool found on the install iso. Is that the most elegant solution?

Thanks again to the community. Your comments have been helpful!

---

### Post by mfarquhar on 2008-11-02
I'm not sure what to tell you about that, I'm assuming that you are correct in your assumption that you have overwritten the data for your card with atheros info. I'm unsure how to undo that, at least not without the appropriate info from your previous setup. 

is this where you got those commands from? 
_[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)_

I do know from looking at another topic that the "Unclaimed" part means that no driver has "claimed" the device.

Do you know the Model Number for your actual card? if you do, see if you can spot it here
_[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA)_

Do you know what Chipset your card uses? knowing that will make it much easier to find a driver for it, if one exists. if there is not a native linux driver, you will need to use the ndiswrapper to use a Windows driver.

---

