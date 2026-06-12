---
title: "Device Manager (windows) = ? (Ubuntu)"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by nalinib on 2008-05-30
What is Device Manager (windows) equivallent in Ubuntu ?

I am using Ubuntu 8.04 live cd (not yet installed on hdd)

Thanks

---

### Post by rampageoberon on 2008-05-30
its gnome-device-manager for ubuntu

---

### Post by nalinib on 2008-05-30
How can I access it in live cd ?

---

### Post by vishzilla on 2008-05-30
type it in the terminal

---

### Post by sam_delta on 2008-05-30
in this thread
[http://ubuntuforums.org/showthread.php?t=472267](http://ubuntuforums.org/showthread.php?t=472267)

some people claim it to be on system>admin>device manager
others claim to have it under System>Preferences>Hardware Information

it depends on your ubuntu version i guess. 

just to notice that in ubuntu, things are handeled a little bit diferent from windows, you wont do much in the device manager

tell us what are you trying to do, and we might be able to help you

sam

---

### Post by nalinib on 2008-05-30
I typed in terminal

1]    "genome device manager" and got "command not found"

2]    "sudo genome-device-manager" and again got "command not found"

---

### Post by RSingh on 2008-05-30
> **nalinib said:**
> I typed in terminal

1]    "genome device manager" and got "command not found"

2]    "sudo genome-device-manager" and again got "command not found"

not 'genome', its 'gnome'

---

### Post by ad_267 on 2008-05-30
The command doesn't have any spaces. It's "gnome-device-manager"

---

### Post by sam_delta on 2008-05-30
if it claims that you dont have it installed, install it by typing WItH internet connection
```
sudo apt-get install gnome-device-manager
```

---

### Post by nalinib on 2008-05-30
Extrmely sorry!

I did type "gnome" in terminal but inadvertently typed "genome" here in the post.

---

### Post by nalinib on 2008-05-30
```
if it claims that you dont have it installed, install it by typing WItH internet connection
Code:

sudo apt-get install gnome-device-manager


```

Thanks !  It appears gnome device manager is not installed.

But I will not install it right now as I am running live cd (If I install it now It won't be permanent)

I will first install the os on hdd and then install the device manager.

Thanks everybody

---

### Post by rrcs on 2008-05-30
(Argh, I'm still not sure about the protocol of crashing threads when you have a similar problem, as opposed to posting a new thread with the same problem?)

I just came online to ask the same question: what is the Ubuntu equivalent of Device Manager.

In my case, I'm trying to manually add my HP deskjet printer, which isn't automatically detected when I connect it via a USB-to-parallel cable. I have asked for help earlier here: [http://ubuntuforums.org/showthread.php?t=808147](http://ubuntuforums.org/showthread.php?t=808147)

I mailed the cable manufacturer and got back instructions, which I was able to follow and get the printer to work in Vista. But I'd love to get it working in Ubuntu, as well. These are the instructions I was given, if anyone can help me "translate" them to Ubuntu:

> 1. Unplug physically BF-1284 connection from printer 

2. Unplug BF-1284 connection from Laptop 

3. Plug in the BF-1284 cable itself (without connecting to printer). 

4. Go to start >control panel > system > Hardware tab > device manager >
Universal Serial Bus Controller (extend it) 

5. It should detect "USB Printing Support" correctly without any yellow sign
or band sign 

6. If it detects the cable correctly, then you can connect the cable to the
printer at this point.

7. Go to start > printers and faxes and right click on the printer >
properties > ports tab to make sure the printer port should be USB 001/002
instead LPT port. 

8. Restart the computer.

Many apologies, if this is hijacking the OP's thread!

---

### Post by nalinib on 2008-05-30
Welcome rrcs !

I am very much interested in the solution you get here. (That will give solution to my problem as well).

Please go ahead.

---

### Post by ad_267 on 2008-05-30
Plug in the printer and turn it on.
Go to system - administration - printing and click on new printer.
Your printer should be listed here and you can click forward to install your printer.

HP have the best linux support out of any printer manufacturers so I'd be surprised if you can't get your printer to work easily.

---

### Post by rrcs on 2008-05-30
> Go to system - administration - printing and click on new printer.
Your printer should be listed here and you can click forward to install your printer.
I have already tried this - several times, in fact, as I naively hope maybe this time my printer will magically appear :P

When I click New Printer, this is the window I get: [http://img.photobucket.com/albums/v322/skufster/Screenshot-NewPrinter.png](http://img.photobucket.com/albums/v322/skufster/Screenshot-NewPrinter.png)

I read that as my printer not having been detected, and don't know where to go from there :/

---

### Post by ad_267 on 2008-05-30
Is your printer listed as supported here: [http://hplip.sourceforge.net/supported_devices/index.html](http://hplip.sourceforge.net/supported_devices/index.html)

---

### Post by rrcs on 2008-05-30
Yes to Installer, GUI, Status, USB - No to Parallel, cf. also [my original thread]("http://ubuntuforums.org/showthread.php?t=808147").

---

### Post by nalinib on 2008-06-08
> **sam_delta said:**
> in this thread
[http://ubuntuforums.org/showthread.php?t=472267](http://ubuntuforums.org/showthread.php?t=472267)

some people claim it to be on system>admin>device manager
others claim to have it under System>Preferences>Hardware Information

it depends on your ubuntu version i guess. 

just to notice that in ubuntu, things are handeled a little bit diferent from windows, you wont do much in the device manager

tell us what are you trying to do, and we might be able to help you

sam


Thanks sam_delta

I am using ubuntu 8.04.  I don't see "system>admin>device manager" or "System>Preferences>Hardware Information"

However I have installed ubuntu on usb hdd and installed "gnome-device-manager".

But I read in wiki that there are commands to be used in terminal that give you driver information etc.

Thanks a lot everybody

---

### Post by GROMS on 2008-10-06
[QUOTE=nalinib;5076252]I typed in terminal

---

### Post by GROMS on 2008-10-06
> **sam_delta said:**
> in this thread
[http://ubuntuforums.org/showthread.php?t=472267](http://ubuntuforums.org/showthread.php?t=472267)

some people claim it to be on system>admin>device manager
others claim to have it under System>Preferences>Hardware Information

it depends on your ubuntu version i guess. 

just to notice that in ubuntu, things are handeled a little bit diferent from windows, you wont do much in the device manager

tell us what are you trying to do, and we might be able to help you

sam

Sam,

Just tried your suggestion and got this:
:~$ sudo apt-get install gnome-device-manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gnome-device-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnome-device-manager has no installation candidate

Now What??? Oh yea, I'm on 64 bit version if that makes any difference.:confused:

---

### Post by bwang on 2008-10-06
If you want to do stuff in terminal:

```
sudo lshw
```

lists hardware

```
sudo lspci
```

lists PCI devices

```
sudo lsusb
```

lists USB devices.

---

### Post by taladan on 2008-10-06
a note on the lshw....if you put it into 
```
lshw -html > sysinfo.html
```

it'll output it to an html page named sysinfo.html that you can open with your browser to peruse at your own convenience.

Tal

---

### Post by Bartender on 2008-10-06
If you want to do this the easy way, open Synaptic Package Manager and type "gnome-package-manager" into the Search function.  Synaptic will mention that it needs an additional dependency, go ahead and let it do that, Apply the changes, gnome-package-manager will be installed automagically and you'll find the launcher under Applications>System Tools>Device Manager.

As far as the guy with the printer problems, go to Synaptic and do a Search for HPLIP.  Let it install HPLIP and all dependencies.  This is a wonderful program developed by HP.  Once installed, find HPLIP under System>Preferences>HPLIP Toolbox.  Plug in your printer, turn it on, wait a minute, then go into HPLIP and it should identify the printer.

You have to be online of course for Synaptic or any package manager to work.

---

