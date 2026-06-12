---
title: "Dual Boot Windows Vista and Ubuntu"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by nickelbox on 2012-07-14
Hello All - 

I convinced my brother to allow me to setup his Windows Vista computer as a dual boot but I ran into a problem and need some advice. I've tried reading suggestions online but nothing seems to be satisfactory.

On his computer, he has his OS on the C drive with D as recovery. What is the safe way to go about freeing up space on his C drive to install Ubuntu on? I can't do a shrink on it through Windows Disc Manager since it's the C drive...

Thoughts?

---

### Post by NikTh on 2012-07-14
Hi , 
Yes , you cannot shrink the C drive as is mounted . You can do that either from ubuntu LiveCD with gparted or from a windows application called "partition magic" . You can find it and download (google it) its free and it will do the shrinking on reboot (before C drive mount). 
 BUT 
let me consider something , why you don't install Ubuntu Alongside windows ? don't you have this option at the installer window ? 
When you boot from Ubuntu live cd and continue with "Install Ubuntu" after language and initially staff you will see the Ubuntu installer window with 3 options. 
1) Install Ubuntu Alongside windows 
2) Replace windows with Ubuntu 
3) Something Else 
You will pick the first option and you can shrink from there and define the size of Ubuntu. 
Thanks

---

### Post by nickelbox on 2012-07-14
Doesn't installing "Ubuntu Alongside windows" essentially install Wubi? I'd like to avoid that if possible as I don't want to run Ubuntu inside Windows.

---

### Post by Shadius on 2012-07-14
> **nickelbox said:**
> Doesn't installing "Ubuntu Alongside windows" essentially install Wubi? I'd like to avoid that if possible as I don't want to run Ubuntu inside Windows.

Nope. The "Install Ubuntu Alongside Windows" does the Ubuntu install allowing you to dual-boot. It doesn't use WUBI, it is a "real" installation. As NikTh mentioned, this route would be your easiest way.

---

### Post by nickelbox on 2012-07-15
In all the articles I've read about dual booting, it was never once mentioned to simply install Ubuntu "alongside Windows". Every article talks about partitioning your hard drive and installing to the unallocated space. I wonder why this is if the solution is much simpler?

---

### Post by OrangeCrate on 2012-07-15
> **nickelbox said:**
> Hello All - 

I convinced my brother to allow me to setup his Windows Vista computer as a dual boot but I ran into a problem and need some advice. I've tried reading suggestions online but nothing seems to be satisfactory.

On his computer, he has his OS on the C drive with D as recovery. What is the safe way to go about freeing up space on his C drive to install Ubuntu on? I can't do a shrink on it through Windows Disc Manager since it's the C drive...

Thoughts?

A good set of instructions for dual booting Ubuntu with Vista can be found here:

[http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Shadius on 2012-07-15
> **nickelbox said:**
> In all the articles I've read about dual booting, it was never once mentioned to simply install Ubuntu "alongside Windows". Every article talks about partitioning your hard drive and installing to the unallocated space. I wonder why this is if the solution is much simpler?

Partitioning allows for more control of the installation. It's generally recommended for those who know what they're doing when it comes to partitioning. It isn't so hard once you read up about partitioning though. You might want to check out some documentation from [here]("https://help.ubuntu.com/community/GraphicalInstall#continueinstall").

---

### Post by nickelbox on 2012-07-15
The primary issue I am running into is resizing the C drive which contains Windows. The only other partition is D for recovery.

If I install Ubuntu "alongside" Windows without partitioning, will that work?

---

### Post by Shadius on 2012-07-15
> **nickelbox said:**
> The primary issue I am running into is resizing the C drive which contains Windows. The only other partition is D for recovery.

If I install Ubuntu "alongside" Windows without partitioning, will that work?

Yes, when you choose to install Ubuntu alongside Windows you'll reach a screen where you can allocate space for the new Ubuntu installation. It's basically just a matter of dragging the divider to the desired amount of space you want to allocate to Ubuntu. 

**[COLOR="Red"]Make sure you've backed up your Windows, if anything goes wrong[/COLOR]**. 

It shouldn't, but it's always good to have a backup anyway.

---

### Post by NikTh on 2012-07-15
> **nickelbox said:**
> The primary issue I am running into is resizing the C drive which contains Windows. The only other partition is D for recovery.

If I install Ubuntu "alongside" Windows without partitioning, will that work?
Hi ,
Ubuntu will locate the windows files partition (C) . When you choose the first option (alongside windows) ubuntu will make a typically partitioning . You will be able to shrink the partition (my suggestions is to 1) do a defrag of C drive with windows tool before install  Ubuntu and 2) shrink the partition from the end (right) to begin (left)) , and then Ubuntu will do this typical partitioning for / (root) and swap memory. Your home will be IN / (root) partition. 

Wubi  installation mentioned as INside windows and not Alongside. 
Thanks

---

### Post by HermanAB on 2012-07-15
1. Backup all your Windows data.
2. Run chkdsk in Windows.
3. Install 'alongside'.

---

### Post by Mark Phelps on 2012-07-16
If you use the option to shrink the Vista install from inside the Ubuntu installer by moving a slider -- you are risking corrupting the Vista install and rendering it unbootable.

A safer approach is to shrink the Vista partition using the Windows Disk Management utility.  That typically requires a reboot -- since it really shrinks the partition while Windows is not running.

If that won't work for you, another safe option is to Google for and download the Partition Wizard Boot CD, burn that, boot from that -- and use that to shrink the Vista OS partition.

---

### Post by nickelbox on 2012-07-16
Well, I went with the "Install Alongside" option and have a couple issues:


[LIST]
[*]Install seemed to go well and currently goes to Grub2 but when I load Ubuntu, it is horrifically slow - to the point that if I select anything, it dims as if it is thinking.
[/LIST]
**Note** During install, I selected the option to import documents and settings. Also allowed 50GB for the Ubuntu install (using the slider and then Ubuntu partitioned the hard drive during install). System has 3GB of Ram. Is it possible I didn't allow enough hard drive space for the transfer of the documents and settings which is causing a lack of hard drive space for swap?


[LIST]
[*]There are two options in Grub2 for Vista with the distinction /sda1 and /sda2. I chose /sda1 and when Windows loaded, it went to chkdsk, performed the task, and then shut down.
[/LIST]
Unfortunately at this point, I had to leave my brother's house and told him I would look more into the issue.


Suggestions?

---

### Post by nickelbox on 2012-07-16
Update - 

Looks like I got all the issues resolved except for the wireless driver for the computer. I am looking at a Gateway M-6750 laptop and can't find the driver on the Gateway site. Anyone know of alternative sites I can go to to download this driver?

---

### Post by HeroOfCanton on 2012-07-16
> **nickelbox said:**
> Update - 

Looks like I got all the issues resolved except for the wireless driver for the computer. I am looking at a Gateway M-6750 laptop and can't find the driver on the Gateway site. Anyone know of alternative sites I can go to to download this driver?

I've had linux on my M-6750 for years. This "top dog" wireless card has never worked for me with any linux distro. Tried everything you will find on google, and more. Finally gave up and bought a compatible card. If you value your time convince your brother to just [buy a usb wireless adapter compatible with linux]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux").

---

### Post by NikTh on 2012-07-16
> **nickelbox said:**
> Update - 

Looks like I got all the issues resolved except for the wireless driver for the computer. I am looking at a Gateway M-6750 laptop and can't find the driver on the Gateway site. Anyone know of alternative sites I can go to to download this driver?

Hi , 
well glad to hear that resolved all your problems with installation. 
As for the wireless issue , i suggest to run this command in a terminal ```
lspci -nnk|grep -iA2 net
``` to see your wireless card id and model , then you can open a new thread at Networking & Wireless section. 
Thanks

---

### Post by OrangeCrate on 2012-07-17
> **nickelbox said:**
> Well, I went with the "Install Alongside" option and have a couple issues:


[LIST]
[*]Install seemed to go well and currently goes to Grub2 but when I load Ubuntu, it is horrifically slow - to the point that if I select anything, it dims as if it is thinking.
[/LIST]
**Note** During install, I selected the option to import documents and settings. Also allowed 50GB for the Ubuntu install (using the slider and then Ubuntu partitioned the hard drive during install). System has 3GB of Ram. Is it possible I didn't allow enough hard drive space for the transfer of the documents and settings which is causing a lack of hard drive space for swap?


[LIST]
[*]There are two options in Grub2 for Vista with the distinction /sda1 and /sda2. I chose /sda1 and when Windows loaded, it went to chkdsk, performed the task, and then shut down.
[/LIST]
Unfortunately at this point, I had to leave my brother's house and told him I would look more into the issue.


**Suggestions?**

Start over, and follow the instructions I linked you to in my previous post.

Edit:

Also, read/pay attention to Mark Phelps' post in this thread.

---

### Post by nickelbox on 2012-07-18
> **NikTh said:**
> Hi , 
well glad to hear that resolved all your problems with installation. 


Not quite.
Yesterday, both Windows and Ubuntu loaded fine. Today, Windows loads and then goes right back to GRUB regardless of what mode you select (normal or safe). Ubuntu still loads fine.

Any ideas?

---

### Post by mebomechanicno1 on 2012-07-18
I am lost. What is the difference between 'Dual Boot' and 'Alongside'

---

### Post by NikTh on 2012-07-18
> **mebomechanicno1 said:**
> I am lost. What is the difference between 'Dual Boot' and 'Alongside'

Nothing. Same thing. 


> **nickelbox said:**
> Not quite.
Yesterday, both Windows and Ubuntu loaded fine. Today, Windows loads and  then goes right back to GRUB regardless of what mode you select (normal  or safe). Ubuntu still loads fine.

Any ideas?

Yes , i have an idea. 
Boot in Ubuntu  and open a terminal (ctlr+alt+t)  and write 
```
sudo update-grub
``` 
reboot and see if you can boot in windows. 
Thanks

---

