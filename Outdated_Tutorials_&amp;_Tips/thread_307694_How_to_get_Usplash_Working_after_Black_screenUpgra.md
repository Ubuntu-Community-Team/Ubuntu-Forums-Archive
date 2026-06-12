---
title: "How to get Usplash Working after Black screen/Upgrade to Edgy"
date: 2006-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Chazall1 on 2006-11-26
I have been working on this for weeks,(on and Off) I had upgraded to Edgy and had no Usplash, just a black screen with a blinking curser in the upper left corner. I have a Dell Dimension 3000, with a i82865G graphic card and a Dell E176FP monitor. Its all in the resolution, Here is what I did:

1.  sudo gedit /etc/usplash.conf set the resolution to 640x480
then run  sudo update-initramfs -u

2.  sudo gedit /boot/grub/menu.lst
FIRST: Check the line that looks like this   #defoptions=quiet splash    I had made changes to the setting from what I read, This is the default setting
SECOND: go to the end of Kernel line and it sould be   ro quiet splash

    sudo update-grub

3.  sudo dpkg-reconfigure linux-image-$(uname -r)

This worked for me, I did not think I would ever see Usplash, Hope this works for you!!!!!!

---

### Post by Jivicin on 2006-11-29
Followed this to the T... no dice.  I've had the blackness since the Edgy upgrade now. :( 

Here's my grub entry:

```
title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=af29ff18-9e31-445e-a654-c09e753a5edf ro quiet splash noapic acpi=noirq
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```

---

### Post by Jivicin on 2006-12-01
Bump.

---

### Post by Jivicin on 2006-12-11
Bump.

---

### Post by visvak on 2006-12-11
one more peice of advice to add, i had pretty much the same problem but i dint go away after following the above steps. because i have i386 machine and i had changed my kernel from the default generic to i386.

when i changed the kernel back to generic, everything worked fine.

---

### Post by sirlancelot on 2006-12-12
Yay! I can see usplash again!

One more issue I have to resolve now, and that's that the login screen still doesn't display (blank screen after usplash). I have to Ctrl+Alt+F1 then Ctrl+Alt+F7 to see it :-k

---

