---
title: "Ubuntu Loads with Onboard Graphics but unable to with Geforce 6200..."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Foghornleghorn on 2008-05-25
Hello all,
           I've tried many suggestions to get my Nvidia Geforce 6200 card to work,but it's like finding a needle in a haystack. I know the card is functioning ok because i can dual boot into XP using the Geforce. 
When i try to Boot into Ubuntu with the Geforce, after the first initial screen it just sits on the third bar without progressing further.
Please help me to resolve this issue as it's driving me nuts.
Thanks in Advance,
Regards,
Foghornleghorn.

---

### Post by cprofitt on 2008-05-25
you should have two options at boot up...

pick the one that says (recovery mode) at the end. This option will boot with text scrolling across the screen and no splash screen. You will then get to a recovery menu and should select root shell prompt.

From here do the following:

```

nano /boot/grub/menu.lst

```

This should load your grub menu (boot options). You need to edit this:

```

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1ca68426-7705-4ce0-a10a-90a79e296d25 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

```

to this

```

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1ca68426-7705-4ce0-a10a-90a79e296d25 ro
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

```

Then try rebooting.

I have to be honest I had this problem with my Nvidia card up until 8.04; in 8.04 I do not have the issue.

---

### Post by Foghornleghorn on 2008-05-25
> **PrivateVoid said:**
> you should have two options at boot up...

I have to be honest I had this problem with my Nvidia card up until 8.04; in 8.04 I do not have the issue.

Sorry i'm dual booting with XP ...no recovery (mode) option available.I can select XP or Ubuntu. On selecting Ubuntu with Geforce 6200 attached,that when the problem occurs. I then reboot and select onboard graphics,Ubuntu loads without any problems strange.
regards,
Foghornleghorn

---

### Post by cprofitt on 2008-05-25
Two possible solutions:

1.  Go in to bios and disable your onboard graphics card (usually this is done automatically, but being that you are able to boot to it maybe it is not)

2  Boot using the onboard graphics and edit the file as detailed in my original post.

---

