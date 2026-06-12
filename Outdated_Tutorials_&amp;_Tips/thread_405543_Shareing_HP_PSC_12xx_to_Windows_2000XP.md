---
title: "Shareing HP PSC 12xx to Windows 2000/XP"
date: 2007-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by MikeEvans on 2007-04-09
**OS:** Ubuntu 6.10 & 7.04 32bit

Explanation: How to connect Windows 2000/XP to a HP PSC USB printer hosted on Ubuntu (or other host type)

**Sources:** Ubuntu wiki/docs/forum, [ShareEverythingUSB thread]("http://www.everythingusb.com/forums/showthread.php?threadid=1916")

I have a HP PSC 1210 xi connected to Ubuntu 6.10 (Edgy)  via USB.  Had no trouble setting it up in Ubuntu, followed an on-line guide on enabling CUPS printer sharing, but when it came to connecting windows XP to the share I had lots of trouble.  What I found is many, if not all, of HP's PSC printers do not support network printing, although the do automatically share between windows machines.  The windows print wizard detects the printer but will not accept any official HP drivers.  To get it to work follow these directions, you must be at a point where windows 'sees' the printer and is requesting a driver.

[LIST=1]
[*]Install the official HP driver pack from the included CD or HP's website.
[*]Run the windows 'new printer' wizard.
[*]Specify that you want to connect to a network printer using an URL ([http://host](http://host) IP/printers/printer-name).
[*]Windows will ask for a driver, choose anything on the list thats supported (I used 'HP Deskjet 550c)
[*]When the wizard is complete open the properties of the newly installed printer
[*]On the advanced options section you should see a driver selection box.  Change the print driver to 'HP PSC 1200'
[*]Apply the changes and print a test page
[/LIST]

Note: 1 user reported having to locally attach and install the printer on windows XP before moving it to their Ubuntu machine.  Read thread for more details.

---

### Post by silkstorm on 2007-04-19
I can confirm this worked for me with my PSC-1200.

So far this forum has helped me save a lot of time changing some Windows Desktops/Servers to Ubuntu in a linux/windows hybrid office.

Hopefully soon I'll have a few tricks of my own to give out.

The web based printer management features in cups far outweigh the cost/benefits of using the windows 2000 server I was using to share this and 2 other printers.  Another windows 2000 server license flushed.  Again, thanks for the tip.

---

### Post by LKRaider on 2007-06-17
I tried this on a WinXP and it didn't work. At step 6, there is still no correct driver listed for my printer (HP PSC 1210) :(

Is there any other way to do this? Maybe by copying the files manually from the install disk somewhere?

---

### Post by MikeEvans on 2007-06-18
If possible, try installing the printer locally(directly connected) on your windows machine and make sure it's working.  Once it is then you should see the driver as an option for the remote print queue.  If not you can open the properties of the local print queue and setup a new port pointed at your Linux server, using a URL like the directions indicate.  Please post back if you have success.

---

### Post by krakerjak on 2007-07-07
I am having the same problem.  Printer works local (UBUNTU Feisty Fawn), and networked with a Vista machine (Go Figure), but not my XP machine.

Trying to install locally on the XP machine results in setup creating a USB001 Virtual Printer Port, and a DOT4_001 Port which is described as psc printer.

I tried grabbing the drivers off of the vista box, but it puked on that, too.

Anyone have an idea?

KJ

---

### Post by MikeEvans on 2007-07-10
krakerjak, I had the same issue and my instructions are a workaround for getting the driver assigned to a URL port instead of the USB and DOT ones the setup creates.  Once you install that software and you have  a printer defined using the HP driver (that we want) and the special port (that we don't want) you need to create another new printer using windows print wizard.  You create your own url port to your UBUNTU print server and choose ANY pre-installed print driver that windows will allow you to get away with (even if it doesn't work).  Once its created you should be able to change the driver windows uses on that printer(with the proper URL port) to any driver you have installed.  You want to pick the driver that HP's software installed on the USB printer definition. Once its working you can delete the printer definition that HP's software installed.

If you still can't get it to work please describe which step is not working they way I explained in my initial post.

---

### Post by krakerjak on 2007-07-12
Hi, I finally got it to work.  I ended up having to hook the printer up to another XP machine, and install it as a network printer, then move the printer back to the UBUNTU box.  Then I was able to get the proper driver to show up so I could install it the way I wanted it.

Thanks for the help.
KJ

---

### Post by LKRaider on 2007-07-15
Oops, forgot to post back.

I succeeded in sharing the printer by using SAMBA and making the Ubuntu box serve the drivers. The instructions are here:
[Basic Setup Instructions]("http://www.novell.com/coolsolutions/feature/18850.html")
[Important workaround for Ubuntu]("http://wdhawes.blogspot.com/2007/03/sharing-printers-with-windows-clients.html")
[Another how-to on the subject]("http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876")

This made the process even easier on the Windows side, since it now configures automagically :P Specially useful if you have to serve several machines on the network.

---

