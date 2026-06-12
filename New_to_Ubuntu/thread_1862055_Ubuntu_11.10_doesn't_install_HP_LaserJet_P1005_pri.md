---
title: "Ubuntu 11.10 doesn't install HP LaserJet P1005 printer driver automatically"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by H3R3T1K on 2011-10-16
This is a very common printer. I was used to just plugging the USB cable in, turning the printer on and watch Ubuntu 11.04 download and install the proper driver. Now in 11.10, it recognizes the printer and it shows in the 'printers' tab but the driver is not installed after the wizard shows it's downloaded and I'm unable to print. This is the error:

error: Plug-in file does not match its digital signature. File may have been corrupted or altered, Error code: 2

What can I do to make my printer work. For dummies please ;)

---

### Post by rburkartjo on 2011-10-16
h3r open up the ubuntu software center search for hplip toobox and install. follow instructions. should work had to do to get my hpdeskjet
f414o to work.

---

### Post by H3R3T1K on 2011-10-16
hplip toolbox shows the same error. Still cannot print :(

---

### Post by Mr Fredrick on 2011-10-16
I have this exact same problem, does anyone have a solution?

Thanks in advance,

MrFred.

---

### Post by Marco6308 on 2011-10-17
Same problem with ubuntu 11.10 on Acer Travelmate 7720G :(

---

### Post by bccoulomb on 2011-10-18
> **Marco6308 said:**
> Same problem with ubuntu 11.10 on Acer Travelmate 7720G :(

I have the same problem.
I also had something very similar when I first loaded Natty and it was registered as a bug which was cured later by an update.
Has this problem been registered as a bug?
Bccoulomb

---

### Post by mikechant on 2011-10-18
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=1362925](http://ubuntuforums.org/showthread.php?t=1362925)

Looks like the uninstall in step 2 was the key.

---

### Post by Xonu on 2011-10-19
Hi, 
I did the following to get this to work as the page openprinting.org seems to be down. Uninstalling the printer first might be a good idea. 

1. Install hplip Toolbox (just search for it from Ubuntu Software Center)
2. Then download the HPLIP-3.11.10 Plug-in, I found it here: [http://hplipopensource.com/hplip-web/plugin_download.html]("http://hplipopensource.com/hplip-web/plugin_download.html") (otherwise just search for "hplip-3.11.10-plugin.run" using google)
3. run sudo hp-setup
4. Leave the Connection (I/O) type at USB
5. With your printer conntected and on, it should show up in the list => Next
6. Instead of downloading the plugin automatically (which does currently not work), you can choose the location of the hplip-3.11.10-plugin.run file which you downloaded earlier, then click next
7. It will install, then add the printer

That did it for me, I now can print using my HP Laserjet P1005 with Ubuntu 11.10. 

Hope it works.
Greetings, 
Xonu

---

### Post by mdurham on 2011-10-26
> **Xonu said:**
> Hi, 
I did the following to get this to work as the page openprinting.org seems to be down. Uninstalling the printer first might be a good idea. 

1. Install hplip Toolbox (just search for it from Ubuntu Software Center)
2. Then download the HPLIP-3.11.10 Plug-in, I found it here: [http://hplipopensource.com/hplip-web/plugin_download.html]("http://hplipopensource.com/hplip-web/plugin_download.html") (otherwise just search for "hplip-3.11.10-plugin.run" using google)


Xonu, How did you download hplip-3.11.10? The latest version that I see in the repo is 3.11.7 and the plugin must match that number.
This printer stuff is a real pain. Aghhhh!
Cheers, Mike

---

### Post by ballantony on 2011-10-26
Right, done it at last...

First, I installed Synaptic, missing from my clean build 11.10

Second, I searched for Hplip on synaptic and removed all the old version packages

Third, go to here [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html) and download the latest version plip-3.11.10.run

Finally, make it executable and run it.

Success!

---

### Post by mkredler on 2011-10-26
Hi 

I have a similar problem:
I just switched to Ubuntu 11.10 and I have an HP LaserJet Professional P1606dp printer. Installation did not work automatically at first. After trying several things, I removed all things related to hplip in my Ubuntu Software Center, and I uninstalled hplip following [http://hplipopensource.com/node/188](http://hplipopensource.com/node/188). Then I installed hplip.3.11.10 from hplipopensource.com.

I can now run hp-install from the terminal, but only after following the advice from another forum and running:
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib64/

So here's the problem: When doing the "device discovery" step on hp-setup, I cannot see any entry for  printers.

The printer is connected and has worked before. It also seems that the system is recognizing it: When typing lsusb on a terminal, I get the following entry (which only appears when having the printer plugged in):

Bus 001 Device 002: ID 03f0:0a2a Hewlett-Packard 

I tried to use 03f0:0a2a for manual discovery using hp-setup, but it didn't work.

Hope that someone can help me!

---

