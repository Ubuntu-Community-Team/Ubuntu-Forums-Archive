---
title: "Finding out system information on Ubuntu Linux"
date: 2005-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by crazybill on 2005-04-23
Finding out system information on Ubuntu Linux

In order to get system navigation, change your login from user to root. On Ubuntu Linux type

$ **sudo –s –H**
You will be prompted for a password. Type in your password. Now your termimal will change from $ to # and you are in root.
To get our information we will use the *head* command. The *head* command displays on the screen the first few lines of the file from which you are obtaining the information. It is convenient because the information you want in these cases are on the first few lines and head displays the information and closes.

**To obtain CPU information**:

# **head  /proc/cpuinfo **

An example of what you might get is shown below (In this case there is an AMD Atholon 1700 CPU running at 1469.793 MHz):

[B][I]
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 6
model name      : AMD Athlon(tm) XP 1700+
stepping        : 2
cpu MHz         : 1468.793
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
[/I][/B]

**To obtain Linux version and Debian version information**

# **head /proc/version**

Here is a sample display. In this case I had a Ubuntu Linux 5.04 machine --- but the Linux and Debian numbers for that version of Ubuntu is different. Sometimes you want to know what version of Linux and/or Debian you have in order to see if a certain software distribution is compatible.
[B][I]
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005[/I][/B]

**To obtain memory (RAM) information**

# **head /proc/meminfo**

Here is a sample display for a computer with 256 MB of SDRAM
[B][I]
MemTotal:        256812 kB
MemFree:           14944 kB
Buffers:              36772 kB
Cached:             73916 kB
SwapCached:      3708 kB
Active:             141032 kB
Inactive:            46184 kB
HighTotal:                 0 kB
HighFree:                  0 kB
LowTotal:        256812 kB
[/I][/B]

**To obtain partition of your swap space:**

# **head  /proc/swap**

Knowing thw swap partition is important when you do upgrades. This sample output shows that the partition is hda5:
[B][I]
Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       499928  20612   -1
[/I][/B]


** To obtain partition sizes:**

# **head  /proc/partitions**

This output shows how a 30GB hard drive is divided:
[B][I]
major minor  #blocks  name

   3     0   40021632 hda
   3     1   39521632 hda1
   3     2          1 hda2
   3     5     499936 hda5
 254     0   39521632 dm-0
 254     1     499936 dm-1
[/I][/B]

---

### Post by dewey on 2005-04-23
Just a spelling correction.
```
$ sudu –s –H
```

To "$sudo -s -H"

---

### Post by crazybill on 2005-04-23
Thanks. I corrected the keyboard error.

---

### Post by magicfab on 2005-04-25
uname -r will also give the version running.

---

### Post by seven on 2005-04-25
you can use lsb-release to find details about your dist
df -H -T will also give info about partitions
and free -m for mem info

---

### Post by Sam on 2005-04-25
Two other typos:
[quote=crazybill]# head/proc/version[/quote]
[quote=crazybill]# head/proc/meminfo[/quote]
They should have a space between "head" and the rest of the line.

Another thing, maybe "cat" would be better than "head". Ok, not the infos are useful, but eg. if you have more than 8 partitions you will miss something.

---

### Post by crazybill on 2005-04-28
Thanks. I didn't notice that. I must have been "spacedout"!  I edited it with the space in case anyone tries to copy paste .. instead of type.

Concerning **head** vs **cat**, I prefer **head** in general because it puts less in the terminal window (I do most stuff through the network). In most cases that works fine. Of course, if you need to see more, **cat **is command of choice.

---

### Post by stevenyu on 2005-04-28
for those people running a server (forexample , a LAMP server), you can install lm_sensor and phpsysinfo to find out all youy need to know regarding to the states of your server

---

### Post by fifoKamb3 on 2009-11-09
I get this:


administrator@server1:~$ cat /proc/swap
cat: /proc/swap: No such file or directory

---

### Post by lavinog on 2009-11-09
> **fifoKamb3 said:**
> I get this:


administrator@server1:~$ cat /proc/swap
cat: /proc/swap: No such file or directory

try:
```

cat /proc/swaps

```

---

### Post by oserdavid on 2010-04-27
This thread looks really useful. Thanks. 

Now, since I'm having severe display problems upgrading to Lucid from 9.10, which is preventing upgrade, how do I find out, via Ubuntu, exactly what display is in my old HP Compaq Nx5000, so that I can more efficiently get help? The system specs from HP sources are too vague to be of use (Radeon mobile, is all...)

Best
David

---

### Post by lavinog on 2010-04-27
lspci and lshw are good commands to use.

---

### Post by oserdavid on 2010-04-27
> **lavinog said:**
> lspci and lshw are good commands to use.
Thanks lavinog - found out the old fashioned way, but useful commands to have, anyway
Best
David

---

