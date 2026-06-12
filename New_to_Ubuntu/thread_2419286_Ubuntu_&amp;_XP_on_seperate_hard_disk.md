---
title: "Ubuntu &amp; XP on seperate hard disk"
date: 2019-05-19
forum: New to Ubuntu
---

### Post by electros6 on 2019-05-19
Hi guys, 
      I like to switch from windows to Linux(Ubuntu). I used windows for more than  10 years, and since I am a newbee to Linux I decide to gradually switch from windows to Linux. So I install Ubuntu in seperate hard disk. When I boot into Ubuntu everything works fine but when I boot to windows the windows not enter into the OS and stays in the welcome screen. When I detatch the Linux hard disk windows works fine but Linux works fine when both hard disk connected. Some please help me to get start in Linux .
 Regards 
N.Baskaran  from India.

---

### Post by DuckHook on 2019-05-19
If you are still running Windows XP, then you are better off simply going all in with Linux and run XP in a heavily jailed VM for those apps that simply must use Windows. XP is years out of support and probably the worst OS ever developed in terms of malware, security holes and just generally awfulness. Every moment you run it is a moment that you are wide open to being pwned.

Just back up your important data, nuke XP from orbit, install Linux and restore your data. If you feel that you are not ready for Linux, at least install W10.

---

### Post by ajgreeny on 2019-05-19
There is, incidentally a patch from Microsoft for an XP vulnerability that they feel is worth acting against, in spite of XP losing support 5 years ago.

You can get it at [https://support.microsoft.com/en-gb/help/4500705/customer-guidance-for-cve-2019-0708](https://support.microsoft.com/en-gb/help/4500705/customer-guidance-for-cve-2019-0708)

Just download the .exe file then install it in your XP install.
Incidentally, I fully support DuckHook's comment about using a VM of XP rather than a bare metal install.  I have it running still as a VM in order to update my SatNav device which does not work with Linux.  I keep a good snapshot of the XP system which I can use if the OS should become corrupt or attacked by virus.

---

### Post by DuckHook on 2019-05-19
Thanks for the link ajgreeny. I also still run XP within a VM, but with no virtual NIC, so no access to the outside world whatsoever. Frankly, I don't know why MS bothered to address this problem… in the five years that it has been out of support, the list of CVEs that compromise XP has grown to be as long as one's arm. I'm not sure how closing off this hole really matters when there's about a hundred other ways to penetrate XP.

In fact, it only serves to create a false sense of security. But that's just my opinion.

@OP. Sorry if I come across as strident, but running XP is equivalent to putting a sign outside your door saying: "Come right in and help yourself to everything I own. There's no alarm, no dogs, I'm never home and the door is unlocked."

---

### Post by electros6 on 2019-05-19
Sorry guys , I wrongly mentioned that I am using XP I am using windows 7

---

### Post by Rubi1200 on 2019-05-20
> [COLOR=#000000]Some please help me to get start in Linux[/COLOR]

What exactly do you want to do or know?

---

### Post by yancek on 2019-05-20
If your problem is still the booting you referred to in post one, I would suggest that when booted into Ubuntu, you go to the site at the link below and get the boot repair software.  Use the 2nd option referred to on the page as it is more up to date then download and run according to the instructions.  Select the option to Create BootINfo Summary rather than trying any repairs.  When it finishes, it will give you a link which you can post here and the information provided should be enough for someone to suggest a possible solution.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mastablasta on 2019-05-21
> **electros6 said:**
> Sorry guys , I wrongly mentioned that I am using XP I am using windows 7

i did this in January but with winXP. 

it is important that GRUB is on linux hard disk. it is also important that it finds all boot options. with windows 7 there should be 2 options (one is actually recovery, the other one is for windows boot). windows 7 is not that much different form windows XP and it should work fine if you installed it all properly. at the moment we can only guess your setup. so use bootinfo script (do not do a boot repair) to create the online report and provide us with the system setup data.

more here:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

