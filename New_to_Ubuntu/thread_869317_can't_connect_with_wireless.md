---
title: "can't connect with wireless"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ksuttles13 on 2008-07-24
i recently installed Ubuntu on my Toshiba Satellite and when i started it there is no wireless connection. Is there anything i can do to get it working.

I think it might be because Ubuntu doesn't recognize my wireless hardware.:mad:

---

### Post by northern lights on 2008-07-24
Can you please post the outputs of```
sudo lshw -C network
```and ```
iwconfig
``` Thanks.

---

### Post by aomlives on 2008-07-24
You can check here to see if your wireless card is supported.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by HieroPosche on 2008-07-24
One thing you might try is going into System>Administration>Hardware Drivers and see if your card is listed there. You can activate it there and see if it works.  

Personally I had to have a wired connection to download a couple of things (they were initialized automatically when I activated the driver if I remember correctly) but that got my system working properly.

---

### Post by ksuttles13 on 2008-07-24
> **HieroPosche said:**
> One thing you might try is going into System>Administration>Hardware Drivers and see if your card is listed there. You can activate it there and see if it works.  

Personally I had to have a wired connection to download a couple of things (they were initialized automatically when I activated the driver if I remember correctly) but that got my system working properly.
I looked and made sure the network driver was enabled and in use.
still don't know why it isn't working thanx for the help though.

---

### Post by northern lights on 2008-07-24
Please post the requested information for further assistance. Thank you.

---

### Post by ksuttles13 on 2008-07-24
> **northern lights said:**
> Can you please post the outputs of```
sudo lshw -C network
```and ```
iwconfig
``` Thanks.
How do I do this...sorry.

---

### Post by northern lights on 2008-07-24
Open a terminal (Alt+F2, gnome-terminal), paste the first line, hit enter, copy the output here. Proceed with the second line.

---

### Post by ksuttles13 on 2008-07-24
> **northern lights said:**
> Open a terminal (Alt+F2, gnome-terminal), paste the first line, hit enter, copy the output here. Proceed with the second line.
Okay I just did it and this is what i got


lo no wireless extension

eth0 no wireless extension

---

### Post by Xamiga on 2008-07-24
> **ksuttles13 said:**
> Okay I just did it and this is what i got


lo no wireless extension

eth0 no wireless extension

Excuse the thread hijack, but i just solved this problem.

Applications->Accesories->Terminal

type in: lsusb

you should see something like:

Bus 006 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 0000:0000

post back here if this is what yours is like (has the Realtek Semiconductor Corp.  line).

---

### Post by ksuttles13 on 2008-07-24
> **Xamiga said:**
> Excuse the thread hijack, but i just solved this problem.

Applications->Accesories->Terminal

type in: lsusb

you should see something like:

Bus 006 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 0000:0000

post back here if this is what yours is like (has the Realtek Semiconductor Corp.  line).
no mine just has zeros in every line

---

### Post by ksuttles13 on 2008-07-24
> **Xamiga said:**
> Excuse the thread hijack, but i just solved this problem.

Applications->Accesories->Terminal

type in: lsusb

you should see something like:

Bus 006 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:0840 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 0000:0000

post back here if this is what yours is like (has the Realtek Semiconductor Corp.  line).

no my just has zeros everywheree

---

### Post by Xamiga on 2008-07-24
Have you installed ubuntu in its own partition, or did you install it in Vista?

---

### Post by jimrz on 2008-07-24
what wifi card are you trying to use?

to check, open terminal and enter```
lspci
```
(this is assuming your lappy is using either an oboard pci card or you have a pcmia card inserted)

then post the output here

---

### Post by ksuttles13 on 2008-07-24
> **jimrz said:**
> what wifi card are you trying to use?

to check, open terminal and enter```
lspci
```
(this is assuming your lappy is using either an oboard pci card or you have a pcmia card inserted)

then post the output here
Antheros AR5007EG

---

### Post by ksuttles13 on 2008-07-24
> **Xamiga said:**
> Have you installed ubuntu in its own partition, or did you install it in Vista?
i thinik it is on its own partition cuz i have a choice at startup to shoose Ubuntu or Vista

---

### Post by jimrz on 2008-07-24
> **ksuttles13 said:**
> Antheros AR5007EG

ok, have not had to deal with that one but searched here for "AR5007EG" and found [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766529&highlight=AR5007EG") thread, which looks promising

---

### Post by powerpleb on 2008-07-24
> **ksuttles13 said:**
> Antheros AR5007EG

I have that chipset, which is a bit annoying to install because Hardy detects it as something else, however I got it working by following these instructions:
[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

Note: these only work with the 32bit version of Hardy. If you have a 64bit edition you will need to follow the link at the end of the linked post.

When you reboot it should prompt you to connect to one of the available networks, however if it doesn't you can test to see if it is working by entering these in the terminal:
```

iwconfig
iwlist scan

```

---

### Post by ksuttles13 on 2008-07-24
> **powerpleb said:**
> I have that chipset, which is a bit annoying to install because Hardy detects it as something else, however I got it working by following these instructions:
[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

Note: these only work with the 32bit version of Hardy. If you have a 64bit edition you will need to follow the link at the end of the linked post.

When you reboot it should prompt you to connect to one of the available networks, however if it doesn't you can test to see if it is working by entering these in the terminal:
```

iwconfig
iwlist scan

```
what's hardy?

---

### Post by ksuttles13 on 2008-07-24
> **powerpleb said:**
> I have that chipset, which is a bit annoying to install because Hardy detects it as something else, however I got it working by following these instructions:
[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

Note: these only work with the 32bit version of Hardy. If you have a 64bit edition you will need to follow the link at the end of the linked post.

When you reboot it should prompt you to connect to one of the available networks, however if it doesn't you can test to see if it is working by entering these in the terminal:
```

iwconfig
iwlist scan

```
ANd when i typed that in it said interface doesn't support scnaning

---

### Post by powerpleb on 2008-07-24
> **ksuttles13 said:**
> what's hardy?

Hardy is the current version of Ubuntu. To find out if you are 32 or 64 bit do this:
```
uname -m
```

64bit will report back x86_64
I imagine 32bit is something like i386 or i686

---

### Post by powerpleb on 2008-07-24
> **ksuttles13 said:**
> ANd when i typed that in it said interface doesn't support scnaning

Did you follow the instructions in the thread I linked to first?

---

### Post by thschiavo on 2008-07-24
There are some Satellite models that don't have the wireless board. I have a friend who has a Satellite M~( don't remember more) and I found that this model has no wireless hardware. And more, this laptop of my friend has a button on the side, and we can read "Wireless: on/off".

Have you checked about that?

---

### Post by powerpleb on 2008-07-24
> **thschiavo said:**
> There are some Satellite models that don't have the wireless board.

This can't be the case because the lspci command recognizes the device.

---

### Post by thschiavo on 2008-07-24
Oh, I see. :-#

---

### Post by ksuttles13 on 2008-07-24
yeah i tried it a few times and it wouldn't work at all
any other suggestions?

---

### Post by ksuttles13 on 2008-07-24
yeah its 32 bit

---

### Post by powerpleb on 2008-07-24
> **ksuttles13 said:**
> yeah i tried it a few times and it wouldn't work at all
any other suggestions?

You will have to use Ndiswrapper then.
1. Install Ndiswrapper GUI:
```
sudo aptitude install ndisgtk
```

2. Locate the Windows drivers either on a driver CD or at [http://www.atheros.cz/](http://www.atheros.cz/) (Go for the 32bit Windows XP drivers)

3. Extract the drivers the move the folder containing the .sys and .inf files into /etc/ndiswrapper/
```
sudo mv foldername /etc/ndiswrapper/
```

4. load up ndisgtk and use it to install the drivers.
```
sudo ndisgtk
```

5. Ensure ndiswrapper module is loaded & working properly
```
sudo modprobe wlan0
```

When you reboot they should be working.

---

### Post by ksuttles13 on 2008-07-25
> **powerpleb said:**
> You will have to use Ndiswrapper then.
1. Install Ndiswrapper GUI:
```
sudo aptitude install ndisgtk
```

2. Locate the Windows drivers either on a driver CD or at [http://www.atheros.cz/](http://www.atheros.cz/) (Go for the 32bit Windows XP drivers)

3. Extract the drivers the move the folder containing the .sys and .inf files into /etc/ndiswrapper/
```
sudo mv foldername /etc/ndiswrapper/
```

4. load up ndisgtk and use it to install the drivers.
```
sudo ndisgtk
```

5. Ensure ndiswrapper module is loaded & working properly
```
sudo modprobe wlan0
```

When you reboot they should be working.
right from the start when i entered
sudo aptitude install ndisgtk
it came back and said nothing was found...

was i supposed to download soemthing ahead of time? 
Like Ndiswrapper GUI: becuz I don't know where to find it.
On the other habd i did find the drivers for the wirless card. 
what should i do about the Ndiswrapper? download the GUI?
If so, where?
Thanks.

---

### Post by bluzepher on 2008-07-25
How to: Install Ubuntu Hardy Heron on a Toshiba l40-10O

[http://www.catswhocode.com/blog/os/gnu-linux/how-to-install-ubuntu-hardy-heron-on-a-toshiba-l40-10o-17](http://www.catswhocode.com/blog/os/gnu-linux/how-to-install-ubuntu-hardy-heron-on-a-toshiba-l40-10o-17)

maybe this will help with your wireless woes >>

Good Luck

---

### Post by powerpleb on 2008-07-25
> **ksuttles13 said:**
> right from the start when i entered
sudo aptitude install ndisgtk
it came back and said nothing was found...

was i supposed to download soemthing ahead of time? 
Like Ndiswrapper GUI: becuz I don't know where to find it.
On the other habd i did find the drivers for the wirless card. 
what should i do about the Ndiswrapper? download the GUI?
If so, where?
Thanks.

You don't need the GUI, it just makes things easier.

Once you have put the Windows drivers in /etc/ndiswrapper/ just enter this into a terminal:

```

sudo ndiswrapper &#8211;i /etc/ndiswrapper/path/filename.inf

```
Replace path with directory that driver is in.

```

sudo ndiswrapper &#8211;m
```
Then
```

gksudo /etc/modules
```

This will open the modules configuration file for editing. On a new line at the bottom, add the following.
```

ndiswrapper
```
Ensure you press Enter after adding the line.

Reboot, and it should be working.

I stole a lot of this from here: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

---

### Post by ksuttles13 on 2008-07-25
okay sorry ijust figured out that i was suppose to have my laptop connected to the internet through and ethernet cable when putting in the codes. I was instead using another computer to view this but when i did connect it and try it it worked until the part where im supppose to extract the files into the folder. It continually says it is ubale to create the files. So idk whats next i even re tried the other tutorial you sent me before and it also didn't work. Is there anyway I can have you do it remotely? Thanks.

---

### Post by Xamiga on 2008-07-25
> **ksuttles13 said:**
> i thinik it is on its own partition cuz i have a choice at startup to shoose Ubuntu or Vista

If you have only 2 lines on the screen 

Vista
Ubuntu

you have installed ubuntu inside Vista.

Hardware-access-wise I think that makes a difference.  (sorce OP Firewall forums)

:confused:Someone post me if this is wrong.

---

### Post by powerpleb on 2008-07-26
> **ksuttles13 said:**
> it worked until the part where im supppose to extract the files into the folder. It continually says it is ubale to create the files.

You need to extract them in your home directory and then move them into that folder using 'sudo mv'

You don't have permission to modify any parts of the file system normally. You need to become 'root' (similar to admin) to do this. You can temporarily gain root priviledges by entering 'sudo' before any code your enter in the shell (terminal) or 'gtksudo' before running any GUI programs.

---

