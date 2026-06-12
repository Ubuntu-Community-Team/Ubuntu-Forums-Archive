---
title: "NetworkManager is a disgrace to linux!!!"
date: 2009-12-20
forum: Recurring Discussions
---

### Post by dragos240 on 2009-12-20
It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endcompletelyuselessrantthathasnopoint]

EDIT:

Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares. Weird.....

---

### Post by TheNessus on 2009-12-20
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endrant]

Of course, don't bother to tell us which ubuntu version or what hardware you use, I mean, this is just totally irrelevant, right? :-\"

Works great for me, anywhoo.

---

### Post by dragos240 on 2009-12-20
> **TheNessus said:**
> Of course, don't bother to tell us which ubuntu version or what hardware you use, I mean, this is just totally irrelevant, right? :-\"

Works great for me, anywhoo.

It does this on EVERY linux distro I use. Not just ubuntu. Arch/gentoo/ubuntu/fedora/etc.

---

### Post by slakkie on 2009-12-20
I take it you submitted a bug report to explain the situation to the developers so they could look into the problem, fix it and ask you to test their fix.

The people of NM are really helpful, they fixed issues I had, I've tested them and gave them feedback and now I have no issue at all with it.

---

### Post by pwnst*r on 2009-12-20
works great here - 3 different machines.

---

### Post by MooPi on 2009-12-20
Network manager has worked flawlessly on all my computers(4). The issue is most likely to do with the wireless adapter. Do you have the specs for yours?

---

### Post by Hetor on 2009-12-20
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endrant]

Cool, use your bash script then. NM works for me.

---

### Post by Dr Belka on 2009-12-20
I have used ubuntu with several versions on many machines and I have never had a single problem.

why is it that when people have a problem with something they have to go on a little rant about how awful it is?

---

### Post by The Real Dave on 2009-12-20
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endrant]

Hmmm, I've been blaming my piece of sh...*cough*, my em,  bad wireless adapter for the disconnection. Whats that bash script? :)

---

### Post by jimi_hendrix on 2009-12-20
> **pwnst*r said:**
> works great here - 3 different machines.

+1

---

### Post by RiceMonster on 2009-12-20
Generally works fine for me, though occasionally it refuses to reconnect on resume and I have to reboot. That's pretty rare though.

Try wicd. Never had any problems with it.

---

### Post by dragos240 on 2009-12-20
Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares.

---

### Post by NoaHall on 2009-12-20
It does it sometimes - on Fedora. But then I just make it available to all users, works fine then.

---

### Post by RiceMonster on 2009-12-20
> **dragos240 said:**
> Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares.

uhhh...

---

### Post by dragos240 on 2009-12-20
> **The Real Dave said:**
> Hmmm, I've been blaming my piece of sh...*cough*, my em,  bad wireless adapter for the disconnection. Whats that bash script? :)

```

ifconfig wlan0 up
iwconfig wlan0 essid yournetwork
iwconfig wlan0 mode Managed
#wpa_supplicant -B -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf (if you have a wpa connection, uncomment this line.)
dhclient wlan0

```

wpa_supplicant needs it's own setup. However, it works like a dream.

---

### Post by The Real Dave on 2009-12-20
> **dragos240 said:**
> ```

ifconfig wlan0 up
iwconfig wlan0 essid yournetwork
iwconfig wlan0 mode Managed
#wpa_supplicant -B -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf (if you have a wpa connection, uncomment this line.)
dhclient wlan0

```

wpa_supplicant needs it's own setup. However, it works like a dream.

Thanks :)

---

### Post by slakkie on 2009-12-20
> **dragos240 said:**
> ```

ifconfig wlan0 up
iwconfig wlan0 essid yournetwork
iwconfig wlan0 mode Managed
#wpa_supplicant -B -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf (if you have a wpa connection, uncomment this line.)
dhclient wlan0

```

wpa_supplicant needs it's own setup. However, it works like a dream.

Why use a bachscript if you can configure this in your interfaces file.

---

### Post by original_jamingrit on 2009-12-20
Actually, I've been having the same issues as dragos240.  It's subtle; I never noticed any problem until switching to Slackware and then switching back for a little while.  The funny thing is that Windows XP works just as well as NM, but initiating a connection with Slackware's rc script system almost never drops my connection.

Now I have Slackware and Ubuntu, dual boot, but using Ubuntu on my laptop from my bedroom is a pain.  Maybe my bedroom is just far enough away from my WAP for GNOME NM to want to say "Oh, this connection is poor, let me disconnect to try to find something better, oh, nothing better, maybe I'll twiddle my anthropomorphised thumbs".  There may be an option in NM to disable this "smart" behaviour, but I haven't found it.

I'm going to sign up on GNOME's bugzilla and report, if it's not already there.  Dragos, could you post your lspci?

Real Dave, if your problem is indeed the same, maybe do the same?  It may take a couple days to really notice the lack of disconnects.

EDIT:  For anyone curious, I have an Atheros adapter, using the recently added ath5k module. {{06:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)}}.

---

### Post by dragos240 on 2009-12-20
Hmm.... well my script works but okay.
Here is the output of lspci on my box, I just used -v and snipped the wireless card part.

```
01:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
    Subsystem: Linksys Device 0055
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fdff8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci

```

---

### Post by original_jamingrit on 2009-12-20
Cool, thanks.  My rule of thumb is that if it's worth a rant, it's worth a bug report; that's one of things that keep the open source engine running.

---

### Post by Psumi on 2009-12-20
> **dragos240 said:**
> Hmm.... well my script works but okay.
Here is the output of lspci on my box, I just used -v and snipped the wireless card part.

```
01:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI
    Subsystem: Linksys Device 0055
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fdff8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci

```

*cough cough*

[http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/comment-page-1/](http://home.facticity.org/2009/07/26/ralink-rt2561rt61-802-11g-on-ubuntu-9-04-jaunty-jackalope/comment-page-1/)

Read all the comments for a new driver link.

---

### Post by stoffepojken on 2009-12-20
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endcompletelyuselessrantthathasnopoint]

EDIT:

Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares. Weird.....

Can you share that fantastic shell script?

---

### Post by Psumi on 2009-12-20
> **stoffepojken said:**
> Can you share that fantastic shell script?

[Click Here](http://ubuntuforums.org/showpost.php?p=8531008&postcount=15)

---

### Post by gradinaruvasile on 2009-12-20
Try [_Wicd_]("http://wicd.sourceforge.net/download.php"), as someone suggested before. It works really well.

---

### Post by dragos240 on 2009-12-20
> **gradinaruvasile said:**
> Try [_Wicd_]("http://wicd.sourceforge.net/download.php"), as someone suggested before. It works really well.

It does. VERY well. is there a cli app for using it? The gui tool works well. But cli is more fun.

---

### Post by lukjad on 2009-12-20
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endcompletelyuselessrantthathasnopoint]

EDIT:

Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares. Weird.....

Ermm...... What? I kinda don't follow you. It starts off with a title that is somewhat flameworthy, then goes into a possibly legitimate complaint about your computer disconnecting, then there is the vanity statement about the bash script, then it just goes into a retraction, then what appears to be a retraction of the retraction with a confirmation of the original title... I don't know what to say really...

---

### Post by gradinaruvasile on 2009-12-20
> **dragos240 said:**
> It does. VERY well. is there a cli app for using it? The gui tool works well. But cli is more fun.

There is wicd-curses. From version 1.6 upwards, it is included in the package. It is a text-mode gui.
If you want command line only, there are the specific linux apps like iwconfig, wpa-supplicant, etc.

---

### Post by dragos240 on 2009-12-20
> **gradinaruvasile said:**
> There is wicd-curses. From version 1.6 upwards, it is included in the package. It is a text-mode gui.
If you want command line only, there are the specific linux apps like iwconfig, wpa-supplicant, etc.

Which is what I use for my shell script.

---

### Post by lukjad on 2009-12-20
So... What do you want? Your problem was fixed, you don't seem to want to try other network managers, and you seem to keep contradicting yourself.

---

### Post by dragos240 on 2009-12-20
> **lukjad007 said:**
> So... What do you want? Your problem was fixed, you don't seem to want to try other network managers, and you seem to keep contradicting yourself.

That's the fun of confusion. :lolflag:

---

### Post by lukjad on 2009-12-20
Blahsdkfjsognaiognlgwerioniowneroingvoav. :\

---

### Post by cprofitt on 2009-12-20
The beauty of Linux is demonstrated so aptly in this thread...

Something doesn't work and you can:

1.  Roll your own solution (OP script)
2.  Report the bug

Ain't life grand?

---

### Post by squilookle on 2009-12-20
No problems here, except for the fact that I seem unable to connect to my wireless network using 64 bit WEP: this shouldn't be a problem as I desparately want to move to something more secure, but doing so would break access to the network for a certain Windows computer that uses the network: opening the Wireless settings on said Windows computer freezes it completely for some reason... so I cant get in to change the settings.

---

### Post by Psumi on 2009-12-20
> **cprofitt said:**
> The beauty of Linux is demonstrated so aptly in this thread...

Something doesn't work and you can:

1.  Roll your own solution (OP script)
2.  Report the bug

Ain't life grand?

2. Report the bug.
-- Wait 3 months
---- No Fix
-- Wait Another 5 months
---- No Fix
-- Screw it and use a different distro/program/hardware.

---

### Post by Crunchy the Headcrab on 2009-12-20
I've never had an issue with NetworkManager.  Bad driver?

---

### Post by Icehuck on 2009-12-20
Network manager is crap. Using the CLI tools sucks because you can't connect to WPA networks who have symbols in their keys. WICD seems to be the better solution, but WIFI and Linux don't like each other :P

---

### Post by dragos240 on 2009-12-20
> **Icehuck said:**
> Network manager is crap. Using the CLI tools sucks because you can't connect to WPA networks who have symbols in their keys. WICD seems to be the better solution, but WIFI and Linux don't like each other :P

You probably can.

---

### Post by Icehuck on 2009-12-20
> **dragos240 said:**
> You probably can.

Can what? Connect to networks with symbols in their networks? No, because it's a bug in wpa_supplicant and they don't feel a need to fix it. Which is when I travel, I don't bring my arch laptop because I only use CLI tools to do wifi on it.

---

### Post by dragos240 on 2009-12-20
> **Icehuck said:**
> Can what? Connect to networks with symbols in their networks? No, because it's a bug in wpa_supplicant and they don't feel a need to fix it.

Oh really?? Then how can we connect to networks with symbols in the keys with gui tools. They use wpa_supplicant.

---

### Post by speedwell68 on 2009-12-20
> **RiceMonster said:**
> Generally works fine for me, though occasionally it refuses to reconnect on resume and I have to reboot. That's pretty rare though.

Try wicd. Never had any problems with it.

Wicd FTW.:D  If I am using wireless I use Wicd and if I am hard wired I use Network-Manager.  Wicd is less bloaty than Network-Manager.  One niggle with Wicd is that the Ubuntu One Client doesn't work well with it.  But I hardly ever use Ubuntu One so it isn't a bother for me.

---

### Post by bapoumba on 2009-12-20
Moved to Recurring Discussions.

---

### Post by HansKisaragi on 2010-04-18
Network manager refuses to work correctly on ubuntu 9.10 and 10.4 beta.

Connects to network but there is no internet

---

### Post by Simian Man on 2010-04-18
For Fedora 13, NetworkManager now includes a command-line interface so you can use it even without a GUI.

And I find NM to be pretty much flawless on my machines, I can't understand why it would disconnect you, but you should at least file a bug report including your adapter.

---

### Post by toupeiro on 2010-04-18
Topics like this make me laugh.  Yes, linux has been completely besmirched by network manager!  RABBLE RABBLE!

---

### Post by eltonw on 2010-04-18
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endcompletelyuselessrantthathasnopoint]

EDIT:

Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares. Weird.....

[FONT="Comic Sans MS"][COLOR="DarkRed"]It would help if you posted some basic info on your hardware setup,:confused: especially what type of network card or controller.[/COLOR][/FONT] It's a safe bet that the Network Manager is NOT the culprit.

_Some cards may need special drivers in order to function reliably under Linux_. Perhaps this discussion might serve as enlightenment: [http://ubuntuforums.org/showthread.php?t=1438175]("http://ubuntuforums.org/showthread.php?t=1438175")

and here:[https://bugs.launchpad.net/linux/+bug/496093]("https://bugs.launchpad.net/linux/+bug/496093")

HTH...

---

### Post by Astenorh on 2010-04-18
Wait a second, there is a command line version for NetworkManager :P ???, is it installable on Ubuntu. 

I use sometimes unstable versions of Ubuntu on my laptop and fixing the system without internet connection is sometimes painful (when stuck in command line).

---

### Post by bruce89 on 2010-04-18
NetworkManager is one of the Project Utopia things that have made Desktop Linux usable. I'd hate to go back to the days before it and the other PU things.

---

### Post by dragos240 on 2010-04-19
Keep in mind. This is an OLD topic. I now use WICD.

---

### Post by Shining Arcanine on 2010-04-20
> **dragos240 said:**
> It constantly disconnects from my connection. Just running a bash script that I made works so much better! It NEVER disconnects, whereas network manager does this every 5 minutes. I am so fed up with networkmanager. I have no idea if the daemon is the cause or the applet. Networkmanager sucks!

[/endcompletelyuselessrantthathasnopoint]

EDIT:

Why am I flaming? I honestly don't support what I have just said. It doesn't work, fine. Dragos240, please don't flame other softwares. Weird.....

Have you tried using Wicd? I think it is a Canonical project that aims to replace Network Manager.

---

### Post by iponeverything on 2010-04-20
> **dragos240 said:**
> Keep in mind. This is an OLD topic. I now use WICD.

There always seems to be a few people with wireless problems and often the first thing that people suggest is to install wicd or ndiswrapper. 

I don't think that either of those should be the first things that people try. For one, more often that not it is module issue and not NM and I have also noticed that native drivers always work better. Generally I don't spend a lot of time trying to help people with wireless problems, beyond googling vendor model and ubuntu -- from looking at the lspci that someone else requested that they post - and seeing if it is working under ubuntu and then posting link a to what I consider promising tread. 

Don't get me wrong, while for the most part NM has just worked for me -- I do find its HAL like behaviour and mysterious Dbus shenanigans very annoying.

---

