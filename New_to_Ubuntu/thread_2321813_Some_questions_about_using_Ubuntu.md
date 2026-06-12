---
title: "Some questions about using Ubuntu"
date: 2016-04-24
forum: New to Ubuntu
---

### Post by rattskjelke on 2016-04-24
I want to switch to Linux but some of the Windows software I need won't run on Wine. I'm also afraid if I let MS upgrade me from 7 to 10 it will ruin my Linux installation.

---

### Post by DuckHook on 2016-04-24
> **rattskjelke said:**
> I want to switch to Linux but some of the Windows software I need won't run on Wine. I'm also afraid if I let MS upgrade me from 7 to 10 it will ruin my Linux installation.Please start your own thread for advice and support in this forum. We must refrain from hijacking the OP's thread.

---

### Post by QIII on 2016-04-24
Moved to its own thread.

Hijacking is not only impolite to the OP.  It also makes things confusing for those who would like to help.

---

### Post by grahammechanical on 2016-04-24
In other words, please start again from the beginning. What is the partition layout? Does this motherboard have a UEFI boot system or BIOS boot system? Does the hard drive have an MBR partitioning scheme or GPT partitioning scheme? What version of Ubuntu?

My advice based on people posting on this forum is to expect any upgrade to Windows 10 to disable loading into Ubuntu. So, prepare in advance by backing up your data; researching Boot Repair and even think about re-installing Ubuntu.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by sammiev on 2016-04-24
> **rattskjelke said:**
> I want to switch to Linux but some of the Windows software I need won't run on Wine. I'm also afraid if I let MS upgrade me from 7 to 10 it will ruin my Linux installation.

Hi,

Run both Linux and Windows.

You can Dual boot Windows and Linux or you can run Linux from a VM or visa versa.

Why limit yourself. :)

---

### Post by UbuntuAddict99 on 2016-04-25
Greetings Rattskjelke,

First off welcome  to Ubuntu and second. Do not worry when i first made the bold and daring  move to the freedom of Linux i was as well
afraid that my Windows  programs would not work. Now, depending on what software you want to use  the WINE (software) can help you.

Although i recommend just dual  booting why infect Linux with Microsoft code. And to answer your  question about the dual booting i had the same issue.

I dual booted Linux Ubuntu 14.04 LTS with my Windows 7 PC it was all sunshine and rainbows. 
But then i upgraded to Windows 10 and it broke GRUB. The solution was fairly simple

ALSO  NOTE (If after the upgrade it is only booting straight into Windows  follow this artical to try ad get GRUB back and or follow my steps to  resolve it
URL [http://itsfoss.com/no-grub-windows-linux/](http://itsfoss.com/no-grub-windows-linux/)

1) Disable Secure boot in my BIOS/UEFI after installing Windows 10.
2) Run Ubuntu from a Live DVD/CD and install Boot repair.
3) Restart the PC without the Live DVD/CD and GRUB will be working again.

But please NOTE!

When i first did this GRUB named my Windows 10 OS in its list as Windows Vista it is just a typo error.

I do hope this has answered your question and feel free to post again.




"Ubuntu the final frontier."
                                 -UbuntuAddict99

---

### Post by rattskjelke on 2016-04-28
I didn't realize making a comment was considered thread hijacking. I wasn't asking for help or support.

---

### Post by Geoffrey_Arndt on 2016-04-28
Hmmm, . . OK.

---

### Post by yetimon_64 on 2016-04-28
> **rattskjelke said:**
> I didn't realize making a comment was considered thread hijacking. **I wasn't asking for help or support.**And if you posted a non helpful "comment" or bit of "opinion" that does not go toward helping the OP, by definition, you are distracting or hijacking a thread.

I didn't see the original thread this was posted in so don't know the full context of the "comment". Being a regular helper here since 2010 I often come across "comments" or "discussion like" posts in support threads and find they often only lead to confusion when posted in a thread that someone is actually asking for technical support in. Try to understand the difference between a general discussion (as occurs in the cafe for instance or in real life) and threads posted in the general help forums (a means of getting technical help with a problem).

Regards, yeti.

---

