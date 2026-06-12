---
title: "new kernel won't boot, HELP !!!!"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-10-15
while i was gone my wife allowed aN ubuntu update which installed the new 2.6.24-21 kernel. i went to restart and i noticed it wouldn't boot, i got a kernel panic. in the boot menu had the new kernel entry and my 2.6.24-19 one. i am only able to boot into the 19 kernel. i edited my menu lst and made it default boot the earlier kernel with no problems. the question i have is, do i really need the new kernel or can i continue to use the 2.6.24-19 one ? :confused:

---

### Post by bobnutfield on 2008-10-15
This new kernel seems to be wreaking quite a lot of havoc.  There are other posts here that suggest that a bug has been posted on Launchpad.  I have not seen it, but it is perfectly fine to continue to use a working kernel until a further update fixes this one.

---

### Post by smooth3006 on 2008-10-15
> **bobnutfield said:**
> This new kernel seems to be wreaking quite a lot of havoc.  There are other posts here that suggest that a bug has been posted on Launchpad.  I have not seen it, but it is perfectly fine to continue to use a working kernel until a further update fixes this one.

thanks, good to know it wasn't just me. i thought the new kernel was just going to be for the 8.10 upcoming ubuntu version ? :confused:

---

### Post by bobnutfield on 2008-10-15
> **smooth3006 said:**
> thanks, good to know it wasn't just me. i thought the new kernel was just going to be for the 8.10 upcoming ubuntu version ? :confused:

No, Intrepid uses 2.6.27, currently at -7.  I have used it since Alpha 5.  This kernel update was strictly a Hardy update, nothing to do with Intrepid, unless the kernel updates are in preparation of some kind for those who want to upgrade, but I doubt it.

---

### Post by tjwoosta on 2008-10-15
i also had issues with the new kernel 

it gets as far as setting up nfs and my caps lock button starts blinking and the computer freezes

---

### Post by bobnutfield on 2008-10-15
Yes, there appears to be something awry in the 2.6.24-21.  Use the previous kernel until the next update.

---

### Post by smooth3006 on 2008-10-15
> **tjwoosta said:**
> i also had issues with the new kernel 

it gets as far as setting up nfs and my caps lock button starts blinking and the computer freezes

same here and i lost my wifi with it before i restarted

---

### Post by starcannon on 2008-10-15
While waiting for a patch, or to get back to a gui:

[LIST=1]
[*]Press teh Esc key when prompted during the initial boot process, right after bios is done posting.
[*]In the menu choose the last known working kernel 2.6.24-19-generic I believe it is.
[*]Press Enter
[/LIST]
That should get you back up and running until you can resolve the new kernel issues, GL.

---

### Post by lsutiger on 2008-10-15
Linus Torvalds would not approve :p

---

### Post by smooth3006 on 2008-10-15
what new changes are in the new kernel for 8.04 ? :confused:

im waiting to install 8.10 but i may wait till the 1st of the year, give them time to work bugs out.

---

### Post by bobnutfield on 2008-10-15
I did not read the changelogs before I updated (I only have Hardy on my desktop), but most of the updates were for Jockey and video drivers and restricted modules.  I was fortunate not to have any issues in my upgrade.  

Intrepid has been almost rock solid for me.  No where near the issues I had while Hardy was new.  A great improvement, at least on my laptop where I am running it.

---

### Post by whitethorn on 2008-10-15
I have video problems with my kernel, can't use xv and dri is no longer running.  I already started a thread about it b4 seeing this thread, nice to know I'm not alone.

---

### Post by CowboyFunk on 2008-10-16
For me it broke all the previous kernels so I can't boot at all. :(

---

### Post by leeko on 2008-10-17
Yup, same problems for me - the .21 kernel won't boot. It gets to running local boot scripts, but won't go further. It does allow me to get to tty1-6, but I'm scoobied if I know what to do when I'm there... 

If I try to boot into .21 kernel's recovery mode, it gets one step further (setting up NFS), but stops just the same. 

Luckily, I'm still able to use kernel .19. My sympathies to those who can't boot at all - I feel your pain!

Lee

---

### Post by lsutiger on 2008-10-17
I am getting a kernel panic error, tells me to use the noapic in the boot string. I can do that in grub, but where do I do it for a permanent solution?

---

### Post by Crash87ss on 2008-10-19
having problems here too, locks up on boot, even on recovery mode. It gets to mounting cifs shares I have set up, complains it can't find them and locks up. The -19 kernel still seems to work.

---

### Post by smooth3006 on 2008-10-19
> **Crash87ss said:**
> having problems here too, locks up on boot, even on recovery mode. It gets to mounting cifs shares I have set up, complains it can't find them and locks up. The -19 kernel still seems to work.

just skip the new kernel update and stick with 19 until a fix can be made.

---

### Post by hopper333 on 2008-10-28
similar problem here with 2.6.24 update

on hardy server-amd64, dual quad-core opterons on Tyan Thunder mobo, software RAID 1 with mdadm

upgraded to -21 and now it hangs for a long time then drops into busybox saying it "can't find /dev/md2"  i.e. my /  strangely though, it *can* find /dev/md1 -> /boot and /dev/md3 -> home with no problem

dropping back to -19 & everything is OK again

without wanting to be unappreciative of the excellent Ubuntu setup in general I have to ask - for a LTS server OS shouldn't testing have picked this up?

M

---

### Post by tjwoosta on 2008-10-28
for me, with the 2.6.24-21 kernel it loads up as far as setting up nfs, then all of a sudden i get kernel panic and, my caps lock button starts blinking, then everything completly freezes up


all of the other kernels still work fine though

---

