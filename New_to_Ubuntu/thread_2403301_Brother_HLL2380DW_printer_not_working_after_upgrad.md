---
title: "Brother HLL2380DW printer not working after upgrade to 18.04"
date: 2018-10-09
forum: New to Ubuntu
---

### Post by ctmerrill on 2018-10-09
Hi, Friends, I've used threads on this forum so many times over the years to solve upgrade problems, and this time I am really stuck, so I am posting for the first time!

I upgraded from 16.04 to 18.04 and my printer stopped working. It's a Brother HLL2380DW. The scanner works. I've installed the drivers from the Brother website, following their instructions. The drivers installed without problem, but would not print a test page.

When I print a page, the printer turns on and shows "receiving data" on the screen, but no paper comes out, then it goes back to the main menu. CUPS then says that printing was completed. 

The printer is connected via USB. I also tried to set it up via Ethernet, and had similar problems. Actually, at one point, it did spit out a blank piece of paper when I tried to print something. 

As part of my troubleshooting, I have uninstalled then reinstalled CUPS, then reinstalled the printer driver. I've also rebooted my computer and printer and router a lot of times :)

Any help would be appreciated. I'm excited to learn.

---

### Post by Geoffrey_Arndt on 2018-10-09
Maybe some ideas here:   [https://askubuntu.com/questions/764497/brother-printer-does-not-work-after-installation](https://askubuntu.com/questions/764497/brother-printer-does-not-work-after-installation)

---

### Post by ctmerrill on 2018-10-10
Thanks, Geoffrey - I did find that thread before and tried all 3 suggestions without success :(

When I tried hooking up my printer with a network connection, I failed at the ping test. Clearly, the computer could connect with the printer enough to tell it to turn on and even spit out a page, but when I tried to ping it I got

christine@bituin:~/Downloads$ ping 192.168.001.010
PING 192.168.001.010 (192.168.1.8) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable

(192.168.1.6 is my desktop computer and 192.168.1.10 is my printer)

---

### Post by ctmerrill on 2018-10-10
Hey, everyone, I wanted to let you know I (sort of) solved my problem. I got Google Cloud Print to work. I don't know if I can print everything that way, but at least I can print the urgent items we have. If you have any thoughts about how to get my printer working the usual way, I'd appreciate them still!

---

### Post by kurt18947 on 2018-10-10
> **ctmerrill said:**
> Thanks, Geoffrey - I did find that thread before and tried all 3 suggestions without success :(

When I tried hooking up my printer with a network connection, I failed at the ping test. Clearly, the computer could connect with the printer enough to tell it to turn on and even spit out a page, but when I tried to ping it I got

christine@bituin:~/Downloads$ ping 192.168.001.010
PING 192.168.001.010 (192.168.1.8) 56(84) bytes of data.
From 192.168.1.6 icmp_seq=1 Destination Host Unreachable
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable
From 192.168.1.6 icmp_seq=3 Destination Host Unreachable
From 192.168.1.6 icmp_seq=4 Destination Host Unreachable

(192.168.1.6 is my desktop computer and 192.168.1.10 is my printer)

If your printer is attached via USB, I doubt ping will do anything, I think that's a network command. Something you could try is to install system-config-printer if it's not already installed. I run it from a command window (alt + f2). Once the app opens,  right-click the printer's icon then left-click properties. See if you notice anything amiss. Once thing I've had happen is that under **policies**, enabled was unchecked, no idea why. Checked that and I was in business. You can also check the URI, it should start with something like usb://xxxxxxxxxxxxxxxxxxxxx where x=letters & numbers.

---

### Post by mfct on 2018-10-24
Same problem with my Brother MFC-J5335DW.    I had upgraded to 18.04 and then went to Brother website and downloaded their installer for the new driver.    Printing stopped ! - found a post about "broken ghostscript configuration" - all Greek to me, but this worked like a dream: 

Open Terminal.    Type in these two commands (successively)

sudo rmdir /usr/share/ghostscript/9.25/iccprofiles  [ENTER]

[ you will be asked for your user password ] 

sudo apt-get install --reinstall libgs9-common  [ENTER]

[ exit Terminal and try to print - it worked instantly for me.    Good luck. Michael Taylor

---

