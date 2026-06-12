---
title: "how to speed up unity for an old computer."
date: 2012-10-24
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2012-10-24
Hey guys,

My house is finally a fully unix based house! I don't know for how much longer though because the last computer I just loaded Ubuntu on moves incredibly slow running ubuntu. I running 12.04 Unity 2D but that doesn't really seem to help. Is there anything I can do to speed things up? Although I learned ubuntu on gnome, I prefer to stay in unity because of the search feature. Heres a little background on my machine

Acer Aspire
4GB DDR3
70 GB HDD (with 66GBs remaining)

I don't run many programs at once. Let me know what you think because unity :guitar:'s

---

### Post by rushikesh988 on 2012-10-24
visit this link ...

[http://mygeekopinions.blogspot.in/2011/07/how-to-make-ubuntu-unity-desktop-run.html]("http://mygeekopinions.blogspot.in/2011/07/how-to-make-ubuntu-unity-desktop-run.html")

---

### Post by lykwydchykyn on 2012-10-24
Man, time has flown by if a machine using DDR3 is now "old".

If a machine with those specs is slow, it's most likely a graphics card issue.  What's your graphics hardware?

---

### Post by jiggajoe506 on 2012-10-24
I was just reading that... I thin mozilla just takes up too many resources also because I was just running chrome fine and it was pretty speedy. Is there a way to run the search function unity has in gnome?

---

### Post by jiggajoe506 on 2012-10-24
> **lykwydchykyn said:**
> Man, time has flown by if a machine using DDR3 is now "old".

If a machine with those specs is slow, it's most likely a graphics card issue.  What's your graphics hardware?

How do I check that so I can give you that information.

Also How do I check my DDR just to make sure I am right its DDR?

---

### Post by Mopar1973Man on 2012-10-24
The only thing I can think of is back down on the desktop and head over to LXDE desktop. It will help a bunch but still might be heavy load for the older series. I managed to get a 13 year old Sony VAIO laptop to run on Ubuntu 12.04 (LXDE desktop) but its still slow. (800 MHz AMD, 192MB RAM, 10 GB hard Drive)

---

### Post by NikTh on 2012-10-24
> **jiggajoe506 said:**
> How do I check that so I can give you that information.

Also How do I check my DDR just to make sure I am right its DDR?


Open a terminal (Ctrl+Alt+T keys combo) and paste here the results of these commands 

```
lspci -nnk | grep -iA2 vga
sudo dmidecode -t 5,6,17
``` 

Put the results here between the brackets **[noparse]```
here
```[/noparse]** so can be easy to read. 

Thanks

---

### Post by jiggajoe506 on 2012-10-24
first command results:
```
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6100 nForce 405] [10de:03d1] (rev a2)
    Subsystem: Elitegroup Computer Systems Device [1019:2601]
    Kernel driver in use: nvidia

```

Second command results:
```
# dmidecode 2.11
SMBIOS 2.3 present.

Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 16384 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        Standard
        DIMM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 4
        0x0009
        0x000A
        0x000B
        0x000C
    Enabled Error Correcting Capabilities: None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0
    Current Speed: 10 ns
    Type: Other Unknown EDO
    Installed Size: 1024 MB (Single-bank Connection)
    Enabled Size: 1024 MB (Single-bank Connection)
    Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: 10 ns
    Type: Other Unknown EDO
    Installed Size: 1024 MB (Single-bank Connection)
    Enabled Size: 1024 MB (Single-bank Connection)
    Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: 4
    Current Speed: 10 ns
    Type: Other Unknown EDO
    Installed Size: 1024 MB (Single-bank Connection)
    Enabled Size: 1024 MB (Single-bank Connection)
    Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A3
    Bank Connections: 6
    Current Speed: 10 ns
    Type: Other Unknown EDO
    Installed Size: 1024 MB (Single-bank Connection)
    Enabled Size: 1024 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0023, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0024, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0025, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0026, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

```

Thanks

---

### Post by NikTh on 2012-10-24
Ram has not the info that should has. The info in dmidecode depends in what the manufacturer passed in to the chip. In my results in section 17 (memory device) I have the info from the Type of Ram. 

My results 

```
Handle 0x001D, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x001A
    Error Information Handle: 0x001F
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK 2
    **Type: DDR3**
    Type Detail: Synchronous
    Speed: 1067 MHz
    Manufacturer: Not Specified
    Serial Number: 3555B50B
    Asset Tag: Unknown
    Part Number: HMT351S6CFR8C-H9  
    Rank: Unknown
```Your results 
> **jiggajoe506 said:**
> 
```
Handle 0x0023, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    **Type: Unknown**
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0024, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    **Type: Unknown**
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0025, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    **Type: Unknown**
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

Handle 0x0026, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0022
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: A3
    Bank Locator: Bank6/7
    **Type: Unknown**
    Type Detail: None
    Speed: Unknown
    Manufacturer: None
    Serial Number: None
    Asset Tag: None
    Part Number: None

```

Personally I cannot understand what type of Ram you use (DDR1 or DDR2 or DDR3), neither speed is available in the info section. 

The graphics card seems OK, you have nvidia proprietary driver installed.

---

### Post by jiggajoe506 on 2012-10-24
I suppose I can log in the windows side and download crucial's program that tells me what type of ram I have. Now I am concerned about why it couldn't figure out what type of DDR it is. Let me try to reboot and run that command again.

---

### Post by Rob Sayer on 2012-10-24
You may be attached somewhat to unity but I'm with moparman.  Unity is plain slow.  Sorry, but it's true.  There have been complaints about unity and compiz performance since they came out.

My i3 laptop could play 1080p video just fine under windows 7 but not under unity.  Gnome classic is faster but it's not very configurable.

I tried ccsm settings but I just don't like having to **** around with settings that can make the system unstable.  It kind of worked but the system felt glitchy afterwards.

I haven't tried lxde but I recently installed xfce over ubuntu 12.04.  It's *fast*.  I mean snappy.  it's not quite as plug and play but it's also highly configurable.  You have drop down application menus and can also set up custom launchers, which I far prefer to having everything on a huge list.

Also, it works better.  The dual monitor support actually works properly.  In ubuntu and gnome  only extended desktop is supported.  If you have an external monitor plugged into the laptop and you close the lid to suspend you lose cursor  control and have to do a hard shutdown.  If there's an answer for that I can't find it.  Xfce does not act like this.

I just don't think unity is suitable for old computers, any more than windows vista is.

---

### Post by juancarlospaco on 2012-10-24
I just installed Cairo Dock 3.x it automagically combines with Unity making it more lightweight and faster, the new "Cairo-Unity" session appears on login screen if you reboot, it replaces the Dash with Cairo Dock 3, its faster with more visual effects, the same, or no effects, you can configure it.

---

### Post by jiggajoe506 on 2012-10-24
I don't care what interface I use, I just want the search feature that unity has. Where you put the windows key type in what your looking for (File or Program) and takes you right to. I heavily rely on this. So I am open to changing unity as long as I have that feature. As for visuals I don't care... just work fast and don't be choppy.

---

### Post by dannyboy79 on 2012-10-24
> **jiggajoe506 said:**
> I don't care what interface I use, I just want the search feature that unity has. Where you put the windows key type in what your looking for (File or Program) and takes you right to. I heavily rely on this. So I am open to changing unity as long as I have that feature. As for visuals I don't care... just work fast and don't be choppy.
if I recall correctly cairo-dock does have that search thing that unity has. It's been a long time since i used it but I recall it having the search thingy. Good luck

---

### Post by lykwydchykyn on 2012-10-24
> **jiggajoe506 said:**
> I don't care what interface I use, I just want the search feature that unity has. Where you put the windows key type in what your looking for (File or Program) and takes you right to. I heavily rely on this. So I am open to changing unity as long as I have that feature. As for visuals I don't care... just work fast and don't be choppy.

KDE has a similar feature, though the keyboard shortcut is different.  I think the new XFCE that comes with Quantal has something similar, but you can also install something like gnome-do, synapse, or kupfer on any desktop to get this kind of feature.

---

### Post by jiggajoe506 on 2012-10-24
> **lykwydchykyn said:**
> KDE has a similar feature, though the keyboard shortcut is different.  I think the new XFCE that comes with Quantal has something similar, but you can also install something like gnome-do, synapse, or kupfer on any desktop to get this kind of feature.

Awesome thanks for the help guys. Can you point me in the right direction to correctly installing KDE? I really appreciate all the help.

---

### Post by NikTh on 2012-10-25
I think that KDE is a little bit heavy , but you decide . 

```
sudo apt-get install kubuntu-destkop
``` is the command to install the KDE desktop in already installed Ubuntu. 

If you want a fresh installation the download Kubuntu from here: 
[http://www.kubuntu.org/news/12.04-release](http://www.kubuntu.org/news/12.04-release)
Thanks

---

### Post by jiggajoe506 on 2012-10-25
I did A fresh instal of kde last night and man is it snappy but it seems harder to use. Ubuntu seemed more strait forward with printer setup and software center. I think I am going to go back to Ubuntu and run gnome 2D and install one of the apps mentioned.

---

### Post by Mopar1973Man on 2012-10-25
> **jiggajoe506 said:**
> I did A fresh instal of kde last night and man is it snappy but it seems harder to use. Ubuntu seemed more strait forward with printer setup and software center. I think I am going to go back to Ubuntu and run gnome 2D and install one of the apps mentioned.

Give LXDE a try...
[http://lubuntu.net/](http://lubuntu.net/)

Like booting up my desktop here I'm at about 250-300 MB used from 4GB... More like Windows environment.

---

### Post by jiggajoe506 on 2012-10-25
Couple of things guys...

1. I had to open up the tower of the computer and realized its 4 sticks of DDR2 1GB each. 
2. I decided just to use gnome classic but I do appreciate all the help offered. (I just don't have the time to get use to another atmosphere.)
3. I am going to be playing around with a lot of the search things you recommended. 
4. Lastly I decided the ubuntu community is the best to be a part of and probably the most patient. Thank you guys!!!! I will mark this as solved. 

you guys :guitar:

---

