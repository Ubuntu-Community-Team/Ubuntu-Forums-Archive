---
title: "Can't seem to work out how to get online"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by lsemmens on 2008-05-10
I'm an absolute noobie to Linux although I am competent with Windoze. I've loaded 7.10 on an old Compaq box that I built out of spares. By browsing around I found that dial up networking is not natively supported and  I managed to find drivers for the conextant  modem on the Dell website which seem to work. Now to my problems.
1 - On boot they system automatically dials my ISP - how do I stop that
2 - Can I set some manner of manually connecting when I need a connection a-la windoze popup?
3 - How do I manually disconnect when I complete a session?

That'll do for now as I'm typing this on my Windoze box.

BTW - I have the computer networked through a router so I can transfer any files across as needed. It's slow, but it works.

---

### Post by cmnorton on 2008-05-10
How are you connecting, wired or wireless?

If you are connecting via wireless, make sure your /etc/network/interfaces file starts out like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto lo

Using sudo and your password, assuming your username installed Ubuntu, make a copy of this file, and then edit it as noted above.

---

### Post by Mark_in_Hollywood on 2008-05-10
If you have used the Network Manager (NM) applet to dial out, you must reconfigure it to not dial out. I had the same problem some years ago. 

If the OS is dialing without NM, then you need to remove and reconfigure wvdial.

NM has a way to have multiple phone #s.

NM can be added once we have solved the problem you have. If it isn't already.

---

### Post by lsemmens on 2008-05-11
> **cmnorton said:**
> How are you connecting, wired or wireless?


As it's a dial up connection, the modem is physically installed in the computer. I do not set up network sharing for D/up connections for obvious reasons.

---

### Post by lsemmens on 2008-05-11
> **Mark_in_Hollywood said:**
> If you have used the Network Manager (NM) applet to dial out, you must reconfigure it to not dial out. I had the same problem some years ago. 

If the OS is dialing without NM, then you need to remove and reconfigure wvdial.

NM has a way to have multiple phone #s.

NM can be added once we have solved the problem you have. If it isn't already.

I am totally unfamiliar with Ubuntu, I can find no reference to NM in the menus. It this the same as Network Settings? I've disabled the modem there (I think) as it appears to have stopped the dial out on login.

---

### Post by HunterThomson on 2008-05-11
> **lsemmens said:**
> As it's a dial up connection, the modem is physically installed in the computer. I do not set up network sharing for D/up connections for obvious reasons.
Aw, you need something called "PPP" you can install "KPPP"

Yep you just install KPPP or gnome-PPP you can find it in add/remove in the Applications menu

Now to set it up you mite need to read thorough a HOW TO

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

Really you are better off installing it from synaptic package manager in system/administration just search for KPPP and check the box and click apply. Synaptic will make sure you have all the dependent packages downloaded too.

---

### Post by lsemmens on 2008-05-11
How do I invoke PPP? Can I install it from the CD? As I said in my first post, Windoze is a breeze, Linux is a new language.

---

### Post by HunterThomson on 2008-05-11
I edited my post read it now...

You will see it in Applications / Internet... in the task bar.
 It is a GUI:)

---

### Post by HunterThomson on 2008-05-11
> **lsemmens said:**
> How do I invoke PPP? Can I install it from the CD? As I said in my first post, Windoze is a breeze, Linux is a new language.

I was new just a few month ago. It killed me at first but now I love it and it is so EZ way EZ'r then window$ trust me stick with it:) You will love it.

A GUI is a graphical program with buttons and all not a comand line program:)

---

### Post by lsemmens on 2008-05-11
GUI - Graphical User Interface - I'm aware of the acronyms. Just as a bit of background, I am a mod on another PC Help Forum, so am familiar with DOS (remember that>) and Various incarnations of Windoze. 

If I try and install KPP using A/R programs, I get a popup telling me the list is not current and offers to re-fresh, problem is, it can't really achieve anything w/-out an internet connection and it won't let me do anything that way. By using the Synaptics PM, I cant find KPPP but it does report PPP as installed.

All that is listed in the Internet submenu of Applications is various clients (mail,  bittorrent, etc.

In my browsing, I found your link, Hunter Thompson, and got as far as the sudo commands and cam undone. I entered the command sudo adduser MYSUERNAME dip exactly as required being careful of case sensitivity and I get the response that MYUSERNAME doesn't exist. I **knew that**! What am I missing?

---

### Post by Mark_in_Hollywood on 2008-05-11
First, can you tell me if you have a "bar" at the top of your screen with the words: Applications  Places  System? I assume "yes", but if not let us know.

Next, see the screenshot (net-set.png) I've attached to this post. That applet is accessed from System/Administration/Network.

If your modem is highlighted (selected), click to un-select it.

Reboot. If the modem is still dialing, let me know.

You may have inadvertently set the modem up to dial when you installed Ubuntu. If you are at the place where you haven't transferred files or downloaded stuff into the hard drive under Ubuntu, it may be easiest to re-install the OS. Slowest, but easiest.

Hang in there.

---

### Post by lsemmens on 2008-05-12
I've found that, and disabled it, after some testing, I worked out that that was causing my main problem. Thanks for your help. Now, how can I set it up to connect and disconnect as I determine?

---

### Post by Mark_in_Hollywood on 2008-05-12
Try this for a start:

Alt-F2, then type (cut and paste, please)

gksudo gedit /etc/wvdial.conf

enter your password. This will come up in the GEdit (Gnome Editor, a program similar to M$ Notepad)

You should see the following:

[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

add your ISP's phone number

add your Username or ID or whatever your ISP calls you

add the password.

leave the New PPPD line alone.

SAVE the file.

Reboot your computer.

If you haven't installed the "Terminal" applet into a panel, let us do so now. You can remove it once we are done getting you online.

So: from the Applications/Accessories menu, pull down the menu and see the word: Terminal, right click once Terminal is highlighted. Select "Add to panel".

A moment later a small tv monitor screen icon should appear on your top (or maybe bottom) panel. Once you see the icon click it.

once you see your user name at computer, and by way of example mine is:

mark@lexington

type the following:

wvdial 

then press the enter key. The computer should now dial up and connect automatically. If it doesn't, please copy any messages (errors or otherwise) into the gedit and paste those here.

If this get you online, open System/Preferences/Synaptic package manager. Wait for the program to load (about 40 seconds). Search for the keyword: gnome-ppp

when that selection comes up, click the apply button. It will download and install itself. Once that is done, reboot (probably not necessary) and under Applications/Internet you should see the Gnome PPP or something similar. Click on it. Check it out. It's somewhat self explanatory form there. Let me know if you are good to go from here, so we can close this thread.

---

### Post by lsemmens on 2008-05-14
Thanks again for your help, Mark, I've managed to get then wvdial command to work for me, but can find no reference to gnome-ppp. in synaptic PM, which, incidently I find in the /system/administration menu.

---

### Post by Mark_in_Hollywood on 2008-05-15
My mistake, see:

Applications / Add-Remove Applications

Look under Internet for

Gnome PPP

add it. Once it is installed, right click, if you still need help, let me know.

---

### Post by SlappyPappy on 2008-05-15
Dude, I started in the end of April and I'm doing fine in Linux. Hang in there, you'll get the hang of it. It's actually easier than Windows and the people here are awesome with all their help and advice.

A quick note about Gnome PPP, it's a little wonky in that after you get it set up, and dial your ISP the little window will hang on "connecting". It connects just fine, it just looks like it doesn't complete the connection process. Don't sweat it. When you're done with the connection just click on cancel and it will disconnect you. At least that's the way it works for me in Gutsy.

It seems odd that you didn't find kppp in Synaptic. I did and installed it no problem. He's pretty good until he has to redial and then the little applet that sticks in the bar at the top disappears and it's harder to disconnect than say Gnome PPP. Then what you have to do is go to terminal type in ps -A to find the kppp PIDs along with the pppd PID and kill them with "kill -1 (whatever the PID number is). Kind of a pain but I don't have to do it that often. 

Hang in there my friend, you'll be up and running comfortably in no time!   :)

---

### Post by lsemmens on 2008-05-16
Thanks for the re-direct, Mark. I still can't find Gnome PPP there but I have found KPPP after a search for just PPP.

Slappy Pappy seems to indicate that this is the same, so I am about to log off my windoze box and try my Unix box now, back soon!):P

---

### Post by lsemmens on 2008-05-16
I'm back! Still on Windoze!

"KPPP cannot be installed on your computer type (i386). Either the applications requires special hardware features or the vendor decided not to support your computer type"

If I try and search on gnome PPP, I get a big fat zero. I'm now off to search for a gnome PP.deb package somewhere. If I find one, I may well be back tonight, otherwise, I'll see you all tomorrow!

---

### Post by lsemmens on 2008-05-16
gnome ppp works fine, except i still don't seem to have a valid session that firefox can access. 
here is a copy of the Connect log but the messages that it returns are not what I'd call encouraging. It does appear to have connected, however, or am I reading it wrong?
> home/lsemmens/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot set information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATM1L3DT0198308888
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATM1L3DT0198308888
WvDial Modem<*1>: CONNECT 115200 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ** Dial IP **
WvDial Modem<*1>: Username: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: wlsemmens
WvDial Modem<*1>: wlsemmens
WvDial Modem<*1>: Password: 
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>:     Entering PPP Session.
WvDial Modem<*1>:     IP address is 144.134.7.198
WvDial Modem<*1>:     MTU is 1524.
WvDial<*1>: Looks like a welcome message.
WvDial<Notice>: Starting pppd at Sat May 17 11:18:37 2008
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 5745
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 144.134.7.198
WvDial<*1>: remote IP address 139.134.59.227
WvDial<*1>: primary   DNS address 203.49.70.20
WvDial<*1>: secondary DNS address 139.134.2.190


---

### Post by _duncan_ on 2008-05-16
> gnome ppp works fine, except i still don't seem to have a valid session that firefox can access.

Can you check if Firefox starts in offline mode?

Click the "File" menu of Firefox, look at the "Work Offline" menu item (2nd to the last, the one above "Quit"). Make sure the box beside it is NOT checked. Then try browsing again.

---

### Post by Mark_in_Hollywood on 2008-05-16
As I try to recall from memory the:

WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.

I believe you may have run wvdial without sudo.

The trick here is to get online and get the gnome-ppp:

so in a terminal:

sudo wvdial

when you want to get offline, CTRL-C, will take the modem offline.

If this works, please, run Synaptic package manager, search for gnome-ppp. If it shows up, apply or install, whatever the radio button says (I forget). It will download and install itself. Go back to Applications/add-remove and see if you see a red telephone. Add it and try that. Sorry this has been so circuitous.

---

### Post by lsemmens on 2008-05-17
> **_duncan_ said:**
> Can you check if Firefox starts in offline mode?
Thanks Duncan, that's the first thing I checked.

---

### Post by lsemmens on 2008-05-17
> **Mark_in_Hollywood said:**
> As I try to recall from memory the:

WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.

I believe you may have run wvdial without sudo.

The trick here is to get online and get the gnome-ppp:

so in a terminal:

sudo wvdial

when you want to get offline, CTRL-C, will take the modem offline.

If this works, please, run Synaptic package manager, search for gnome-ppp. If it shows up, apply or install, whatever the radio button says (I forget). It will download and install itself. Go back to Applications/add-remove and see if you see a red telephone. Add it and try that. Sorry this has been so circuitous.

The error log was a cut and paste from the logfile created by gnome PPP.

---

### Post by lsemmens on 2008-05-17
I just tried sudo wvdial and, although the response log did not indicate anything flaky in terminal this time, Firefox still could not seem to find any sites, not even that of my ISP. All I get is a Page Not Found.

---

### Post by Mark_in_Hollywood on 2008-05-17
Assuming you can download a game or some useful package from the Synaptic Package Manager, that means your modem is OK, but Firefox needs to be told something.

Please try the Synaptic idea and let me know.

Also, the Gnome-ppp should be installed by right clicking on the top or bottom panel, (or where ever you have them). Select Add to Panel, find Modem Monitor. That might be it.

---

### Post by lsemmens on 2008-05-18
Thanks again, Mark. I've got Gnome PPP installed in the <Applications><Internet> menu and can seem to log on using it, I get an IP address assigned as per the report that I posted.
I've noticed that the "Connecting" pop up seems to freeze on "Authenticating".
I tried logging in again using SUDO WVDIAL
This is the TERMINAL log
> 
lsemmens@compaq:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT0198308888
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT0198308888
WvDial Modem<*1>: CONNECT 57600 
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ** Dial IP **
WvDial Modem<*1>: Username: 
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: wlsemmens
WvDial Modem<*1>: wlsemmens
WvDial Modem<*1>: Password: 
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>:     Entering PPP Session.
WvDial Modem<*1>:     IP address is 144.139.63.68
WvDial Modem<*1>:     MTU is 1524.
WvDial<*1>: Looks like a welcome message.
WvDial<Notice>: Starting pppd at Mon May 19 11:18:52 2008
WvDial<Notice>: Pid of pppd: 6163
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 144.139.63.68
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 139.134.59.231
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address 203.49.70.20
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 139.134.2.190
WvDial<*1>: pppd: HH&#65533;&#65533;&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]



I appear to have been successful at login and assigned an IP address, but that is all. Downloading stuff using Synaptic also seems unsuccessful.

Maybe I should give dial up a miss w/- Ubuntu and go looking at another package. Even Windoze Missed Edition wasn't this picky and that only lasted 2 hours on one of my boxes before I gave it the flick!

---

### Post by Mark_in_Hollywood on 2008-05-19
I never did learn the make, model and internal/external type of modem you have. The output from wvdial shows it's OK, you have a 'net connection. As to why you can't surf/down/up load is a problem beyond my skills. So sorry. Yet, now that you have dial-up handshaked and online, you might try posting here again. Start a new thread. Maybe give the title: online but can't surf. I've had good help from the Ubuntu boards. Patience is however part of the price of getting the help.

Let me know if I can be of any further help as to modems. 

Mark_in_Hollywood

---

### Post by lsemmens on 2008-05-20
Sorry, Mark, I thought I'd mentioned it. As to the specific make/model, I'm not certain as it was in Compaq Presario that I inherited from a mate. Everest reported it as a conextant and the Dell drivers that I tried seem to work ok. The computer itself is made up out of bits and pieces that I had lying around. P4 2.00GHz Processor, Cant remember MOBO, IIRC about 500Mb RAM - OS resides on a 30Gb Hdd in a cradle with 160Gb slave that holds data, Video is ATI Radeon 256Mb AGP. It now all resides in the case of that presario that I mentioned.

Anyway, thanks for your help. I will start a new thread and see where it takes me. It really is only a "suck it and see" setup, so, if I don't get it running, it's no biggie.

---

