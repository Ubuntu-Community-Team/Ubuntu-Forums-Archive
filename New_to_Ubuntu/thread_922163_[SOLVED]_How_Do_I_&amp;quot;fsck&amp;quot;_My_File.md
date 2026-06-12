---
title: "[SOLVED] How Do I &amp;quot;fsck&amp;quot; My File Systems or Use &amp;quot;iptables&amp;quot;?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-17
A few questions ago (in my "[SOLVED] Ubuntu Security and Maintainance Questions" question), Lucutus of Borg said:

> **Locutus_of_Borg said:**
> fsck your file systems every once in a while and use iptables and you should be fine

Now, I suspect that I might have a bad sector in my hard drive and that I may have installed Ubuntu on a part that had it. How do I make sure? Or fix it if such is the case?

Thanks for your time!

Take care,
RedStarYellowSun

---

### Post by tuxxy on 2008-09-17
Boot into recovery mode by pressing escape at grub screen, now manually rcun fsck from terminal, or type this into terminal and it should auto fsck, once you reboot

```
sudo touch /forcefsck
```

---

### Post by prshah on 2008-09-17
> **RedStarYellowSun said:**
> 
Now, I suspect that I might have a bad sector in my hard drive and that I may have installed Ubuntu on a part that had it.

If you suspect a bad sector, boot from a live CD and give the following terminal (Applications-Accessories-Terminal) command```

sudo badblocks -v /dev/sda1
``` (Replace /dev/sda1 with the actual device for the partition you want to check). Note that this command can be used to check any type of filesystem, not just ext3.

This will not harm the data as it performs a readonly check. It will show a progress count, but if it spits out any block number (seperate from the progress count, on a line by itself) then those are bad sectors.

If you find you have bad sectors, you can "repair" them (ie, mark unusable) with the command ```
sudo fsck -c /dev/sda1
```

IMPORTANT NOTES: 
[indent]
a. This "repair" is only possible on ext2/3 file systems. 
b. Run only from live CD since partitions MUST be unmounted during this check (In general, for all fsck operations, the partition must be unmounted / not mounted)
c. There is a small chance of losing the data/hard disk altogether if the badblock happens to be in a sensitive area (Eg., MBR, Partition table, etc), EVEN if the area in question is not being checked. A backup, if possible, is highly recommended.
d. in the fsck command above, -c performs a good check, and will take a (relatively) long time. If you are paranoid and want a more through check, use -cc instead of -c. Note that this is a NON-DESTRUCTIVE READ WRITE check of each sector, so the time will be MUCH longer and the potential for data/HDD loss HIGHER.
e. All advice at your own risk, sorry.
[/indent]

---

### Post by Locutus_of_Borg on 2008-09-17
Hey, that's me!

to run a simple (f)ile (s)ystem (c)hec(k)
```
sudo touch /forcefsck && telinit 6
```
will reboot and run fsck during boot

if you have more serious problems, you will want to boot form a live cd and use this command:
```
sudo e2fsck -c -c -k -v /dev/sda#
```
just change sda# to your partition

for bad sectors, i suggest the following also from a live cd:
```
sudo badblocks -n -v /dev/sda#
```

both of those last two commands take a long time to run, but will try to repair any errors you have


for iptables i suggest making input and forward drop, then opening only the ports you use, leave output accept and close the ports you dont want open

to do this:
```
sudo -i
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

```

now you probably cannot use the internet which means it is working, but its too strict so you just need to open up some ports to use,

firstly you need "related and established" which i never figured out what exactly is meant, but its necessary, so input this in that same root terminal:
```
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 

```

you also need to allow the lo interface to communicate with your computer
```
iptables -A INPUT -i lo -j ACCEPT 

```

to allow using a web browser:
```
iptables -A INPUT -p tcp -m tcp --dport 53 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT 
iptables -A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT 

```

use that same syntax for all other services, just find out what port it uses

for instance AIM is:
```
iptables -A INPUT -p tcp -m tcp --dport 5190 -j ACCEPT 

```

to use torrents:
```

iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 6881:6889 -j ACCEPT
``` 


for IRC,
```
iptables -A INPUT -p tcp -m tcp --dport 194 -j ACCEPT 

```

feel free to ask me if you have other questions.

---

### Post by Orange_and_Green on 2008-09-17
Re. iptables, you could also install "firestarter" or "shorewall" from Synaptic. Both work by giving you a GUI, letting you choose options and then auto-translating your settings into iptables rules.

Firestarter is quite basic but should suit most people's needs. Shorewall is more fine-grained but perhaps a little less intuitive to use.

Good luck:KS Have a nice day

---

### Post by alienexplorers on 2008-09-17
Firestarter as I beleive is obsolete.  UFW is the new firewall starter and gufw is the gui for that.

---

### Post by Orange_and_Green on 2008-09-17
Wow alienexplorers, thank you for the info! I feel old now:mrgreen:

In fact, i found out that ufw is already installed in my system, so I guess it came preinstalled with Hardy. I cannot find gufw on the repositories though.. I'll check on that.

Thanks:KS

---

### Post by RedStarYellowSun on 2008-09-17
What is "grub screen"? That is the screen what Ubuntu starts loading, right?

Take care,
RedStarYellowSun

---

### Post by Locutus_of_Borg on 2008-09-17
the grub screen is the boot loader you see shortly after you turn your computer on displaying a list of which operating system you want to use

---

### Post by RedStarYellowSun on 2008-09-18
Thanks everyone! No problem remains.

Take care,
RedStarYellowSun

---

