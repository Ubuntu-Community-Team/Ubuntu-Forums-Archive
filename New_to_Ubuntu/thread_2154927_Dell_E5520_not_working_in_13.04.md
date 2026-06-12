---
title: "Dell E5520 not working in 13.04"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Whamola on 2013-06-16
Hi there, so I installed 13.04 on this laptop and have not been able to get the wireless to work.  During the installation I got it to work for my home network for a couple minutes, then it disconnected and the install hung, so I had to do it again.  I tried removing and installing "bcmwl-kernel-source" with no luck.  I've tried connecting at my work and it doesn't even pull up a list of networks in that area.  Any help would be helpful!

Thanks

---

### Post by mirrorz on 2013-06-16
run the following commands :
iwconfig
and 
rfkill list all

---

### Post by mirrorz on 2013-06-16
]run the following commands :
iwconfig
and 
rfkill list all

---

### Post by mirrorz on 2013-06-16
try the following commands:
> iwconfig
rfkill list all

---

### Post by Whamola on 2013-06-19
So I ran: 

Sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install bcmwl-kernel-source

that I found in another thread and was able to pick up the wifi network at my work, but when I got home I was still unable to connect to that network.  I haven't tried the commands mirrorz listed above at home, but when I try it at work "rfkill list all" turns up as all no's.

---

### Post by Rob Sayer on 2013-06-19
What wireless adapter do you have?  Open a terminal and enter:

lspci -nnd 14e4:

---

### Post by Whamola on 2013-06-19
> **Rob Sayer said:**
> What wireless adapter do you have?  Open a terminal and enter:

lspci -nnd 14e4:

I get this:

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4724] (rev 01)
0a:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)

---

### Post by Rob Sayer on 2013-06-20
I can't find a reference for 14e4:4724.  Did you type that yourself or  copy and paste from the terminal?  It's a version of the Broadcom 4313  adapter.  Unfortunately there are several versions of the 4313, which  confuses newbies.

I'm definitely not one of the wireless experts  here.  Try asking the question in the wireless section.  Ask the  question more specifically.  "Dell E5520 not working in 13.04" isn't  descriptive enough, I'm afraid.  It's like taking a car to a garage.   The better you can describe the problem the better service you'll get.   In the thread title mention your specific wireless adapter.

When you ask the question, paste the output from the above mentioned commands in the terminal.  Please put code tags around it.

Your  home router may not be set up in a way that's working with your wifi in  linux.  But there are people here who are infinitely better at this  than I am, and they're more likely to be found in the wireless section.

---

