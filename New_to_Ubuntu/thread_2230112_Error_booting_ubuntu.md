---
title: "Error booting ubuntu"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by karsten4 on 2014-06-17
Hello,

I'm trying to make Ubuntu run on an old computer:

AMD Athlon (tm) XP 1800+
AT/AT compatible
785 904 KB RAM

current OS: Windows2000 in Chinese language (which I can't read)

To do so, I created an USB-Livestick using UNetbootin and the "ubuntu-12.04.4-desktop-i386.iso"-file.
(while creation, I get a message from Avira "autorun blocked")

I even managed to make the BIOS boot from USB flash drive.
When switching on the computer, I get an UNetbootin start screen allowing me to choose between "Default", "Help", "Try Ubuntu without installing", "Install Ubuntu" etc.

I opt for "Try Ubuntu without installing".
Then I can watch the cursor blinking in the left lower edge of the screen for more than a minute, until I get a blank rectangle in the upper left quarter of the screen. After some time, multiple lines of the same text begin to appear:

"udevt[103] timeout: killing '/sbin/modprobe -bv pci: ....."

Afterwards, I get an Ubuntu splash screen (showing the word Ubuntu and five dots that turn from white to red to white and so on)

Then, a screen full of text appears, among others I could read: "ata", "device", then the text was pushed off the screen by multiple lines of:

"udevt[103] timeout: killing '/sbin/modprobe -bv pci: .....' [205]" - it keeps writing this line multiple times for several minutes

Then the screen goes black.

That is the point where I switch off the computer. The problem is reproducible.

As I'm an absolute newbie to Ubuntu/Linux..., I'd be very thankful for information that doesn't require specialist knowledge.
Please let me know if you need any other details.
Any advice/ideas? 

Best regards,

Karsten

---

### Post by sandyd on 2014-06-17
> **karsten4 said:**
> Hello,

I'm trying to make Ubuntu run on an old computer:

AMD Athlon (tm) XP 1800+
AT/AT compatible
785 904 KB RAM

current OS: Windows2000 in Chinese language (which I can't read)

To do so, I created an USB-Livestick using UNetbootin and the "ubuntu-12.04.4-desktop-i386.iso"-file.
(while creation, I get a message from Avira "autorun blocked")

I even managed to make the BIOS boot from USB flash drive.
When switching on the computer, I get an UNetbootin start screen allowing me to choose between "Default", "Help", "Try Ubuntu without installing", "Install Ubuntu" etc.

I opt for "Try Ubuntu without installing".
Then I can watch the cursor blinking in the left lower edge of the screen for more than a minute, until I get a blank rectangle in the upper left quarter of the screen. After some time, multiple lines of the same text begin to appear:

"udevt[103] timeout: killing '/sbin/modprobe -bv pci: ....."

Afterwards, I get an Ubuntu splash screen (showing the word Ubuntu and five dots that turn from white to red to white and so on)

Then, a screen full of text appears, among others I could read: "ata", "device", then the text was pushed off the screen by multiple lines of:

"udevt[103] timeout: killing '/sbin/modprobe -bv pci: .....' [205]" - it keeps writing this line multiple times for several minutes

Then the screen goes black.

That is the point where I switch off the computer. The problem is reproducible.

As I'm an absolute newbie to Ubuntu/Linux..., I'd be very thankful for information that doesn't require specialist knowledge.
Please let me know if you need any other details.
Any advice/ideas? 

Best regards,

KarstenHi, please check the MD5sum of the ISO (via [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows))

If you find that it is corrupted, downloading via torrent may yield better results.

---

### Post by karsten4 on 2014-06-17
Hi sandyd,

thank you for answering. I checked the MD5sum, it says "MD5 Check Sums are the same".

Any other ideas?

Best regards

Karsten

---

### Post by karsten4 on 2014-06-18
Hello everyone,

would it make sense to try another type of linux (xubuntu, mint, knoppix...)?
Or is my problem related to any kind of Linux?
Would it help to change any setting in the BIOS? If yes, which one?
I read about trying to make it run on a lower runlevel, but apparently init 1 doesn't make any difference.
Anything else I could try?

Regards

Karsten

---

### Post by /ADM on 2014-06-18
I would try a lite-weight distro, based on the fact that your CPU is quite old I do not think it would run Ubuntu 12.04 well.  You could try the following:

Lubuntu - For older computers,
Knoppix - Good for testing boot capabilities and recovery.

I would also try booting from CD (if it is possible).  This issue is actually quite common and if you search this on the internet, you get many posts about the same problem.

"udevt[103] timeout: killing '/sbin/modprobe -bv pci:"

Some have suggested in other forums to disable acpi "pci=noacpi" in custom boot options in the GRUB boot menu.  But I would not recommend it unless booting from CD also fails, it's a "last resort", IMO.

---

### Post by mörgæs on 2014-06-18
Some of the old Athlon XP's were born with Nvidia graphics cards from the 4 series, is this the case for you? 

The processor is not going to play Flash. Is this acceptable? 

Lubuntu is a good choice but 14.04 should be your first pick.

More advice in the link in my signature.

---

### Post by karsten4 on 2014-06-18
Hi abilbrou, hi mörgæs,

thank you for your answers.

> **mörgæs said:**
> Some of the old Athlon XP's were born with Nvidia graphics cards from the 4 series, is this the case for you? 


It says "WinFast GeForce2 MX Series", so apparently not.

I just prepared a lubuntu-CD. I'll tell you if it works.

Regards

Karsten

---

### Post by mörgæs on 2014-06-18
Sorry to say, but the 2 series is even worse. Let me know if you are lucky with Lubuntu.

---

### Post by karsten4 on 2014-06-18
Hi,

on the first attempt I ruined the CD and was wondering why  the computer always bootet windows. But with the second CD I reach at  least the splash screen (lubuntu with five blue/white dots).
But then, nothing else happens. After waiting for more than an hour, I rebooted using the noplymouth option this time.
The messages I get are similar to those in this [thread.]("http://ubuntuforums.org/showthread.php?t=1549579")  So I might try to boot with libata.force - but with which parameter?  And: Is this the right approach, or should I try something different?

Regards,

Karsten

---

### Post by mörgæs on 2014-06-18
Again, the link in my signature is the best advice I can give. Please read thoroughly, especially about workarounds for the old Nvidia cards.

---

### Post by karsten4 on 2014-06-20
Hi mörgæs, hi abilbrou,

as vga=791 didn't help, I tried a few other commands. One combination got me "kernel panic", but finally I found out that "pci=noacpi" was the clue (as abilbrou stated before). With this option everything works fine.
Anyway, thanks to both of you for your help. Without, I'd have given up, I think.
Now my next problem is to get the W-LAN running, but I still hope to solve that one on my own. If not, I'll start a new thread.

Best regards

Karsten

---

