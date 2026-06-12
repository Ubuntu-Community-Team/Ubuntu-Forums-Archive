---
title: "grub&gt; after upgrading"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by VeryFoggy on 2011-10-14
1. Loaded ubuntu 11.04 a few days ago. The drive was formatted and not partitioned. Ubuntu is the only OS I have.
2. Upgraded today. It says it needs to restart the computer. 
3. Computer comes up with:
 
GNU GRUB version 1.99~rc1-13ubuntu3
 
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
 
grub>
 
 
 
???????????????
How do I fix this
????????????????????

---

### Post by drs305 on 2011-10-14
Please boot the LiveCD to the Desktop and download/run the Boot Info Script. Post the contents of RESULTS.txt 

This file will show us the status of your boot files and most likely show us the problem.

You can access the script page by clicking on the "BIS" link in my signature line.

Your other option is to install the Boot Repair Tool, which may fix it or give you the opportunity to run the BIS from the app.
[http://ubuntuforums.org/showpost.php?p=11137700&postcount=79]("http://ubuntuforums.org/showpost.php?p=11137700&postcount=79")

---

### Post by VeryFoggy on 2011-10-14
> **drs305 said:**
> Please boot the LiveCD to the Desktop and download/run the Boot Info Script. Post the contents of RESULTS.txt 
 
This file will show us the status of your boot files and most likely show us the problem.
 
You can access the script page by clicking on the "BIS" link in my signature line.
 
Your other option is to install the Boot Repair Tool, which may fix it or give you the opportunity to run the BIS from the app.
[http://ubuntuforums.org/showpost.php?p=11137700&postcount=79](http://ubuntuforums.org/showpost.php?p=11137700&postcount=79)
 
 
I don't understand. I am using my mom's computer to look for answers. My computer is stuck at "grub>".

---

### Post by drs305 on 2011-10-14
> **VeryFoggy said:**
> I don't understand. I am using my mom's computer to look for answers. My computer is stuck at "grub>".

If you insert the Ubuntu Installation CD and reboot the computer should boot the CD rather than your hard drive. When asked, select "Try Ubuntu without Installing".

That will take you to the desktop, where you can open Firefox to browse the web. You can download the script and then open a terminal to run it. To open a terminal you can use ALT-F2 and type gnome-terminal.

You may prefer to install the Boot Repair Tool (it will temporarily install even with the CD) and see if that can fix your system.

---

### Post by VeryFoggy on 2011-10-14
[http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/](http://aaron-kelley.net/blog/2011/04/grub-prompt-after-upgrade-to-ubuntu-11-04/)
 
This looks like my probelm, and I understand his explaination, and I am going to attempt the last solution that is listed, once I figure out what X, Y, and Z are.
 
UPDATE
grub> set root=(hd0,1)
grub> linux /vmlinuz root=/dev/sda1 ro
grub> initrd /initrd.img
grub> boot
 
it comes up (happy dance)
on reboot, it comes up grub (unhappy shuffle)
 
Nextt set of instructions says to open a terminal and enter the following code
 
sudo grub-install /dev/sda1
sudo update-grub
 
so I open the terminal and enter the first line and am told among other things "This is a BAD idea.." and "error: will not proceed with blocklists."
 
I am going to bed and will bang my head against this one in the morning.

---

### Post by VeryFoggy on 2011-10-14
> **drs305 said:**
> If you insert the Ubuntu Installation CD and reboot the computer should boot the CD rather than your hard drive. When asked, select "Try Ubuntu without Installing".
 
That will take you to the desktop, where you can open Firefox to browse the web. You can download the script and then open a terminal to run it. To open a terminal you can use ALT-F2 and type gnome-terminal.
 
You may prefer to install the Boot Repair Tool (it will temporarily install even with the CD) and see if that can fix your system.
 
It will take me a bit. I used my thumb drive to download and install, and then I wiped the thumb drive because I needed it for data transfer.

---

### Post by oldfred on 2011-10-15
If you still can manually boot your install instructioins were almost correct. You were installing to sda1 a partition when you want to install to the MBR.

sudo grub-install /dev/sda   <-Note just sda not sda1
sudo update-grub

Another way:

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc

---

### Post by drs305 on 2011-10-15
As *oldfred* says, you were almost there. The commands you entered at the grub prompt are non-persistent - they are only good for that one boot and are not retained the next time you boot.

The good thing is that since it booted when you entered the commands it means your grub files are intact and all you have to do is point the MBR to the correct location. Running the commands as *oldfred* posted (i.e. *sda* and not *sda1* will do that.

If it works please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

---

### Post by suspicion4u on 2011-10-15
i have the same problem but i did not upgrade from the live cd but did so from the repository updates. Please help. maybe im slow for right now because of lack of sleep

---

### Post by oldfred on 2011-10-15
@suspicion4u
Your system is different so please start a new thread. Post as much info as you can about your config and the boot info script (in drs305 signature) or from this which may also fix system:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by VeryFoggy on 2011-10-15
> **oldfred said:**
> If you still can manually boot your install instructioins were almost correct. You were installing to sda1 a partition when you want to install to the MBR.

sudo grub-install /dev/sda   <-Note just sda not sda1
sudo update-grub



You guys rock. The code worked. [happy dance]

---

### Post by oldfred on 2011-10-15
Glad that worked. :)

We do not seem to have a Smilie for [Happy Dance]

---

