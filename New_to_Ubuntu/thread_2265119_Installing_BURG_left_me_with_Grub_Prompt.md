---
title: "Installing BURG left me with Grub Prompt"
date: 2015-02-12
forum: New to Ubuntu
---

### Post by Ironic57 on 2015-02-12
Fresh install of 14.10 on dual boot with win xp on an old net book. I managed to set up Grub to boot option into Win XP listed first. I pushed my luck attempting to "decorate" and installed Burg (which I learned since hasn't been supported since 2010). Now I'm left with a bunch of text and a Grub prompt "grub >" prompt after reboot. I'm a total noob with Linux and would appreciate any help in recovering from this hell I found myself in- a least painful method would be awesome.

---

### Post by oldfred on 2015-02-12
Can you manually boot?

 ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command. Also change the sda5 to sdaX where X is partition number.
configfile (hd0,1)/boot/grub/grub.cfg

If configfile does not work:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Ironic57 on 2015-02-12
@OldFred- Thank you for your reply. I have the net book on live usb and have the online report here: paste.ubuntu.com/10194143
At the bottom of the report it suggests I run a default repair of the Boot-Repair Utility... 
I only have the one thumb drive that is the Live USB, and no CD-rom drive for the net book, so I have to either go buy another thumb drive (tomorrow- I'm old also) or try to wrap my mind around the logistics of how I can run boot-repair. I've tried the apt-get through the Live USB, it installed- but I can't find it through either the terminal or Dash. I appreciate your help, especially after realizing I left very little info on my problem when I posted this thread.

---

### Post by yancek on 2015-02-12
Did you instal boot-repair to the Live CD you have on the flash drive as explained in the 2nd option at the link below?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You should be able to start it by typing boot-repair in the Search box from the dash menu, or boot-repair in a terminal.  I don't know if you need to preface it with sudo, I've never used it so you might try that.  You need to enter it as:  boot-repair, with the dash and all lower case letters.  If you are using a Live system on the flash, you can't reboot before running it.

---

### Post by oldfred on 2015-02-12
You ran the Boot-Repair summary report, so you can run the repairs. Every time you reboot with live isntaller, you do have to reinstall Boot-Repair as live installer does not save anything.

---

### Post by oldfred on 2015-02-13
Then run Boot-Repair's summary report again.

---

