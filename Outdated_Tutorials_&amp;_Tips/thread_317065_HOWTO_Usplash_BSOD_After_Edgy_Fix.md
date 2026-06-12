---
title: "HOWTO: Usplash BSOD After Edgy Fix"
date: 2006-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Jivicin on 2006-12-11
After weeks of usplash's "Black Screen of Death", and countless possible solutions to the problem, including but not limited to:

[http://www.ubuntuforums.org/showthread.php?t=315400](http://www.ubuntuforums.org/showthread.php?t=315400)
[http://www.ubuntuforums.org/showthread.php?t=307694](http://www.ubuntuforums.org/showthread.php?t=307694)

I finally got usplash working.  Here's the steps I took:

1. I changed my /etc/usplash.conf file to be 640 and 480.

2. Following step 1 of the first guide I ran "sudo update-initramfs -u".

3. The next step is where all my problems were occuring.  Apparent;y the placement of the "splash" keyword in the /boot/grub/menu.lst file is critical.  It **MUST OCCUR** at the end of the kernel line.  If you mix it in with other boot options, it will fail.  Here is my current working entry:

```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=af29ff18-9e31-445e-a654-c09e753a5edf ro noapic acpi=noirq splash
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

My specific problem was that my defoptions was = splash noapic acpi=noirq vga=791.  When I moved splash to the end of the line, it worked flawlessly.  The noapic and acpi=noirq options were used because I was having clock issues when I first installed Hoary.

4. Finally run "sudo dpkg-reconfigure linux-image-$(uname -r)" to ensure everything was updated.

NOTE:  I have the "quiet" keyword removed so I can see the specific processes executing during boot.  You can leave it in if you like.

After I confirmed that it was working in 640 by 480, I changed my usplash.conf to 1024 by 768 and reentered the vga=791 line (ensuring that it was placed before splash).

Hope this helps!

---

