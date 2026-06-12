---
title: "Can't get internet"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by Craig_Baird on 2013-09-24
Hi all, 

Very interested in working with ubuntu but having a problem that I hope you can help me with. I have installed ubuntu on my inspiron 6000 (no apparent problems with the installation, all seemed to go ok).  My 6000 has a little "wi fi" sign on it but I have never been able to access wifi normally on it. When I go to the "select network" bit it only has broadband and land line options, no wireless options.  It has never detected wifi sources and it doesn't detect my Telstra wifi.  

This situation has never been a problem because when I plug in my Telstra wifi to the 6000 via usb it all works ok.  

The problem is that when I plug in my wifi via usb with ubuntu, ubuntu doesn't recognise it.  This of course means that I can't access the net with ubuntu.  

I'm happy to use the usb to connect my wifi to the inspiron 6000 so I'm wondering if anyone has any suggestions to make it all work with ubuntu?

Thanks in advance.  

Craig.

---

### Post by varunendra on 2013-09-24
Welcome to the forums Craig_Baird ! :)

While the USB (wifi adapter?) is plugged in, please post the outputs of -
```
lsusb
lspci -nnk | grep -iA2 net
```

And please elaborate a little on your situation. Your statements seem a little confusing or even contradictory. You said -
> This situation has never been a problem because **when I plug in my Telstra wifi to the 6000 via usb it all works ok**. 
Then immediately next statement -
> The problem is that **when I plug in my wifi via usb with ubuntu, ubuntu doesn't recognise it.**

Are you talking of two different scenarios? One in widows the other in Ubuntu? Please elaborate.

---

### Post by Craig_Baird on 2013-09-24
Thanks for the welcome varunendra.  Sorry for the confusion, to clarify, you are correct in suggesting that I was referring to two different scenarios: I have installed ubuntu along side windows xp.  The wifi unit I have is a "pocket" wifi, one that you can carry around with you in your pocket if you want to.  My inspiron 6000 has never been able to detect this pocket wifi unit (or any other wifi source) but the 6000 can detect the wifi unit when I connect it to the computer with a usb cable when using windows xp.  However the 6000 does not detect the wifi unit when it is connected to the 6000 by usb cable when I'm using ubuntu. 

Also, I'm afraid I don't know how to perform the action you indicated.  I understand to connect the pocket wifi to the 6000 via usb cable when using ubuntu but I don't know what to do next.  How do I bring up/access the "code" screen so that I can then enter the: lsusb etc.  

And what is that sign in front of the susb?  is it an "l" like in lunch?

I greatly appreciate you help, thanks,

craig.

---

### Post by varunendra on 2013-09-24
> **Craig_Baird said:**
> How do I bring up/access the "code" screen so that I can then enter the: lsusb etc.

Ah, sorry, my fault this time. Providing details on how/where to enter commands and how to post back the outputs is part of our general protocol that I missed.

The commands "lsusb and lspci...." are to be entered in a terminal. To open the terminal, either press the shortcut key combination Ctrl-Alt-T, or type "terminal" in the dash menu (the top button on the Unity launcher on the left) and press 'Enter'.

Type the two commands separately (type or copy-paste "lsusb" > press Enter, then the "lspci..." one > Enter)

> And what is that sign in front of the susb?  is it an "l" like in lunch?
**EDIT:** If you mean the **[COLOR="#FF0000"]l[/COLOR]** as in **[COLOR="#FF0000"]l[/COLOR]**susb (shortcut for "list usb"), then yes, it is small "L".

However, if you mean the one between "lspci -nnk" and "grep" in the second command (lspci -nnk **[COLOR="#FF0000"]|[/COLOR]** grep -iA2 net), it is a 'pipe' symbol ("|", not small "L"). It is on the same key as "\" above the "Enter" key on my US-104 style keyboard. To avoid errors, you may copy-paste the commands (copy to a text file > open it in Ubuntu > copy back to the terminal using mouse pointer).

To post back the outputs, just copy the whole output using your mouse pointer, then paste here in your next post.

**PS:**
To preserve the formatting of the output in your post, it is highly recommended that you paste it in-between 'Code' tags. To see how to use code tags, please follow the "Using Code Tags" link in my signature below.

---

### Post by crunchbanger2 on 2013-09-25
Craig,

I have a Dell Vostro laptop that has a manual on/off  switch on the right-side by the DVD tray.  The icon is white and looks  like a little tower with radio waves.  This may be the reason your  on-board wireless doesn't work with any operating system.

Your portable wireless is also known as a dongle.

What to do when people post commands:

1.  Right-click the desktop and left-click, "open terminal here".  This will run your terminal emulator.

2. Insert dongle.

3. Open this web-page and copy varunendra's first line of code:
```
lsusb
```

4. (Input) Then paste inside your terminal emulator:  ctrl shift v
                                                                    4. b. Enter

5.  (Output) Highlight the output and copy: ctrl shift c (Remember, you want to post both outputs at the same time).

Example output:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

Now I copy and input varunendra's second line of code:
```
lspci -nnk | grep -iA2 net
``` 

(Remember, you want to post both outputs at the same time)

Example output:

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Dell Device [1028:02bb]
    Kernel driver in use: r8169
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

Good luck!

---

### Post by varunendra on 2013-09-25
Hey, Welcome to the forums crunchbanger2 !

Nice post, and nice tip too about the physical wifi switch :)

This part however -
> **crunchbanger2 said:**
> 1.  Right-click the desktop and left-click, "**open terminal here**".  This will run your terminal emulator.

..depends upon the Desktop Environment in use, and that right-click menu option is not available in all DEs.

But given the clarity and quality of your post, I'm sure your presence on the forums is going to be appreciated by all. Hope you'll enjoy it too. :)

---

### Post by crunchbanger2 on 2013-09-25
Thanks for the welcome.  You're right, I have Ubuntu Studio with the Xfce Desktop Environment. Would you recommend I 'edit' and add alternatives?

---

### Post by varunendra on 2013-09-25
> **crunchbanger2 said:**
> Would you recommend I 'edit' and add alternatives?

Not necessary, but of course you can, if it makes the post better. :)

All of us very often post steps that are not universally applicable (like "open a file with **gedit**"), but we don't even mention other alternatives because that may make the post confusing. So a general idea is - if you don't know the variables, assume everything to be at defaults, and "default" for Ubuntu means - Ubuntu with Unity.

In fact many of us prefer the command-line ways to do things just because they are quick, often simple, and universal across different environments. :P

Keeping a post both informative and simple is probably an art that only comes with experience, but I believe if someone has the desire to help, they will be helpful anyway.

---

### Post by Craig_Baird on 2013-09-25
Thanks varun and crunchbanger2, I think I'm one step closer!

Crunchbanger, I can't find any switch anywhere on the laptop. I can't remember but maybe I didn't buy the wifi option when I order the laptop from DELL.  Plus right clicking the desktop didn't work.  Not to worry as the ctrl-alt-t did work!  

The problem is that the output is on the laptop that does not have access to the internet and therefore to this forum so I couldn't work out how to cut and past the output onto this forum from the laptop. so i figured I'd just transcribe it all, so here it is:

~$ lsusb
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005:ID 1199:68a3 Sierra Wireless Inc.
Bus 005 Device 002:ID 046d:c016 Logitech, Inc optical wheel mouse

~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation Bcm4401-Bo 100Base-TX [14e4:170c] (rev 02)
Subsystem: Dell Inspiron 6000 laptop [1028:0188] Kernel driver in use: b44
03:03.0 Network Controller [0280]: Intel corporation PRO/Wireless 2200BG [calexico2] Network connection [8086:4220] (rev 05)
Subsystem: Intel corporation Dell Latitude D600 [8086:2722]
Kernel driver in use:ipw2200

The Sierra wireless is the wifi unit I have (You probably already knew that).

Hope this helps.  If so what's next?

Thank you both again,

Craig

---

### Post by varunendra on 2013-09-25
> **Craig_Baird said:**
> 
Bus 001 Device 005:ID **1199:68a3** Sierra Wireless Inc.
....
03:03.0 Network Controller [0280]: Intel corporation PRO/Wireless 2200BG [calexico2] Network connection [8086:4220] (rev 05)
Subsystem: Intel corporation Dell Latitude D600 [8086:2722]
Kernel driver in use:**ipw2200**

It seems both your devices are natively supported in Linux (yes you do have an internal wireless adapter - Intel pro 2200BG), and you should have proper drivers for them already loaded.

So, for a deeper diagnostics report, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Simply attach the "wireless-info.txt" file generated by the script in your next post.

---

### Post by Craig_Baird on 2013-09-25
hi varun,

I hit a problem.  I copied the wireless_script.txt to my ubuntu machine, followed your instructions up to where it says to "run" it however there is no "run" option there. Retracing my steps, I went to "permissions" as suggested and ticked the execute box (interestingly the box didn't stay ticked, but the "Allow executing file as program" text stays coloured) then closed the screen.  But then when I click the wireless_script.txt icon (immediately after closing the screen as indicated) there is no "run" option, only options such as open, save undo etc. 

Any suggestions? 

Thanks Craig.

---

### Post by varunendra on 2013-09-25
> **Craig_Baird said:**
> I went to "permissions" as suggested and ticked the execute box (**interestingly the box didn't stay ticked**, but the "Allow executing file as program" text stays coloured)
..indicates that probably you are trying to make it executable while it is on a non-linux partition. Is it on a windows partition while trying this? If so, please notice this part of the post -
> ....and choose to "Save" the link target. **Copy the downloaded file to your Ubuntu machine** (see the "NOTE 2" below) and run it from there as follows -
....
[COLOR="#800000"]*[NOTE 2: You can't make the script executable if it is on a non-linux partition, for example - a pen drive with FAT32 partition.*[/COLOR]


Accordingly, please copy it to your Ubuntu desktop, make it executable there and try to run.

If you are on Ubuntu 13.04, then also do this as mentioned in point 2 there -
> *[COLOR="#800000"][NOTE 1: In Ubuntu 13.04, the default behaviour is to open the file as text even when it is made executable. To change this, please open any folder > go to "Files > Preferences > Behaviour" tab, and select "Ask each time" option under "Executable Text Files" section.][/COLOR]*

**PS:** Going to edit that post to make the copying part a bit more clear.

---

### Post by Craig_Baird on 2013-09-26
I was in ubuntu when it wouldn't run.  I copied the file (from your link) using a different machine that was running windows 8 and I copied in onto a usb memory stick. But the Inspiron 6000 was definitely on the ubuntu partition when I saved the file from the memory stick to the 6000.  I'll try the whole process again. 

cheers, 
Craig.

---

### Post by robbie 348 on 2013-09-26
Craig, on the Inspiron 6000 isn't the wi-fi switch on the F2 button?

---

### Post by varunendra on 2013-09-26
> **Craig_Baird said:**
> I was in ubuntu when it wouldn't run.  I copied the file (from your link) using a different machine that was running windows 8 and I copied in onto a usb memory stick. But the Inspiron 6000 was definitely on the ubuntu partition when I saved the file from the memory stick to the 6000.  I'll try the whole process again. 

cheers, 
Craig.

If having problems again, just do the following -

[LIST=1]
[*]It seems the file has been renamed to "wireless_script.txt" during download (happens sometimes). Although not a problem, just to avoid confusion, rename it to "wireless_script" again (that is, delete the extension name if there is any).
[*]Copy it to your Ubuntu's Desktop
[*]Open a terminal and run the following commands in it -
[/LIST]
```
cd Desktop
chmod +x wireless_script
./wireless_script
```

Almost immediately after running it, it will ask for your password. Enter your login password and press Enter (you won't see the password while typing it).

As soon as the script finishes its job (usually less than 4 seconds), a file named "wireless-info.txt" or "wireless-info.txt.tar.bz" will be created on your desktop. Attach this file in your next post.

---

