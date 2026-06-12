---
title: "I've really messed something up. And then some more."
date: 2014-08-14
forum: New to Ubuntu
---

### Post by alex_selby on 2014-08-14
System:
AMD Phenom II x4
Asus M4A79XTD Evo Motherboard
16GB DDR3 1600Mhz ram
EVGA Geforce GTX 750TI
500GB Samsung HDD (Win7 64) -sda
256GB Crucial MX100 SSD (Ubuntu 14.04 GNOME) -sdb



So, I converted to Ubuntu 14.04 about 2 months ago, and have mostly been getting along swimmingly. The last couple weeks, though, Gnome has been causing me a degree of trouble. It's bee crashing under various circumstances. It will usually crash and immediately give me full or partial access to whatever process was in the foreground at the time of the crash. I could Ctrl+Alt+F1 to get back to the command line, and would either reboot or startx to return to the desktop. 

Yesterday, I did a search from an error on the crash log  (which I won't be able to provide unfortunately,) that was created when I rebooted, and it led be to learn that my display driver was out of date (my driver was nVidia 334.21, I believe) and so I decided to try to update it, thinking myself smart, and that I'd get it all sorted. I followed the highest-voted directions in this thread: [http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver](http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver) and everything seemed to go off without a hitch. I rebooted, and then decided to run 'sudo apt-get update' and 'sudo apt-get upgrade'. Well, Gnome crashed on me again while apt-get upgrade was doing it's thing. 

From there, I exited to the command line, restarted the computer, and my gnome desktop wouldn't boot from grub. Blank screen. Exit to command line again, and kind of panic. This is where I really started flailing wildly, by the way. I really should have deferred to experts from here on, but decided to go it alone. I started looking up what to do, and somehow decided that trying to install a different desktop environment would help my situation. I installed KDE, and could then get a login screen after grub that prompted me for a password and requested I pick which desktop environment to use. Whatever option I picked, I was only given a blank screen and had to Ctrl+Alt+F1 out. 

I freaked again, and decided I needed to boot from externally. Instead of booting to Windows, I booted from my install LiveDVD. There, I...messed up even more. I decided my data was meagre and as long as I got my system up and running I could take care of getting everything back in due time. I reinstalled Ubuntu-Gnome. Everything looked good for a minute. I rebooted and after BIOS I received a 'grub rescue>' prompt. After a bit of research, I downloaded Boot-Repair, ran it, and was given these two logs: [http://paste.ubuntu.com/8041859/](http://paste.ubuntu.com/8041859/) and [http://paste.ubuntu.com/8041862/](http://paste.ubuntu.com/8041862/) for email or posting here. 

So here I am. I'm at a loss. I'm in over my head. If I could currently boot to Windows, I would do so, reformat my SSD, and reinstall from scratch (which I realize is incredibly brute-force, but I don't know what else to do at this point). But, since I used grub to decide which disk to boot to, I'm currently only able to boot from LiveDVD. 

I'm sorry to take so much of anyone's time, and that I've piled mistake on mistake before asking for help. I'm not sure what further information I can provide, but I can follow explicit directions. 

Please advise. Thanks in advance.

---

### Post by Jonor on 2014-08-14
I would go into the mobo BIOS and select the boot disk from there.
If problematic, switch off and unplug box, remove ssd, reboot to Windows.
Then repeat with ssd replaced, going into BIOS again if necessary.

---

### Post by yancek on 2014-08-14
The second windows entry in your grub menu should boot windows 7.  The first entry (sda1) appears to be a recovery partition.  Do they both fail to boot?  The simplest solution to that is to reinstall the windows bootloader to the mbr of sda as that is a windows only drive.  If you don't have an installation medium, it will be considerably more difficult.  You might check out the microsoft site or a windows forum to see if there is an alternative.

Do you get the same problem when you have sdb (the Ubuntu drive) set to first boot priority in the BIOS?

---

### Post by alex_selby on 2014-08-14
With sdb first in boot order, I get grub rescue, and same with sda first in boot order, as long as sdb is plugged in. Unplugging sdb did allow me to log into windows properly, should be able to wipe sdb and start fresh from here, unless there's some further advice.

---

