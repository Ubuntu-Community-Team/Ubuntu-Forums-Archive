---
title: "looking for a small LIVE CD distro to extract data from portable hardrives"
date: 2008-04-06
forum: Other OS Talk
---

### Post by shuttleworthwannabe on 2008-04-06
Let me explain what happened. I have 3 laptop hard drives that I converted to portable drives and that I used earlier for data storage. Now for some wiered reason, no OS (linux or XP) can see these USB hardrives. But what I have noticed is that when I connect the hardrives into an old Laptop (PIII, 128MB, IBM Thinkpad R31) and boot from live CD (I used Xubuntu LIve 7.04) I could read the contents of the hardrive. But the problem is that the IBM has a huge difficulty loading the desktop of the heavy weight Live CD's. I am looking for a simple Live CD OS that will allow me to boot into the desktop and read the contents of the hard drives. 
- The OS has to be a small download <200MB (I am a victim of ISP sabotaging my monthly cap--apparently legal in this lart of the world). 
- The Os must have the latest Linux kernel 2.6.24+; 
- able to allow me to boot in VESA mode
- ntfs read/write support
 
Options I have thought about:
 
1. SystemRescueCD: I tried this but does not seem to have file browser that I can recognize
2. DSL
3. Puppy linux
4. Zenwalk: what is the size of this ISO?
5. PUD (just release a dev version today on distrowatch)
 
Any other suggestions or alternatives for me to retrieve the data on these portable hardrives are welcome.
 
Thanks
S:confused:

---

### Post by myusername on 2008-04-06
zenwalk is the size of a normal distro... i think DSL would be the best choice

---

### Post by angry_johnnie on 2008-04-06
Puppy's a bit bigger than DSL, but it's still only about 100 megs, and it's really easy to mount / unmount drives.

---

### Post by Balazs_noob on 2008-04-06
SliTaz -->25mb , great distro
but no NTFS support :(

---

### Post by myusername on 2008-04-06
arch linux lol j/k i think dsl has ntfs support

---

### Post by Twitch6000 on 2008-04-07
DSL can probably meet your needs.

---

### Post by Antman on 2008-04-07
> **shuttleworthwannabe said:**
> 
- The OS has to be a small download <200MB (I am a victim of ISP sabotaging my monthly cap--apparently legal in this lart of the world).That leaves Zenwalk out. It's about 489 mb.
> **shuttleworthwannabe said:**
> 
- The Os must have the latest Linux kernel 2.6.24+; 
Why?? I've used puppy on older and some newer hardware and it's kernel is 2.6.21.7
> **shuttleworthwannabe said:**
> 
Options I have thought about:

4. Zenwalk: what is the size of this ISO? 

about 489mb or so. but the LiveCD is pretty nice. I have installed it on several PIII machines and it works well.
But if you can't download the CD just use Puppy. I don't know if DSL has r/w support for NTFS

---

### Post by Bungo Pony on 2008-04-07
I've used Parted Magic successfully to read and write to external HDs. It's also not very big.

---

### Post by lswest on 2008-04-07
Backtrack 2.0 or 3.0 (most up to date one) is normal size, but can be installed on a USB stick if that helps you (actually slightly faster than a liveCD i find)

---

### Post by MONODA on 2008-04-07
i use system rescue cd for all my rescue tasks, it comes with midnight commander and nautilus, go through the guide on the website and print it out.

---

### Post by Twitch6000 on 2008-04-07
Well you know you could do it the other free way.If you would like something such as ubuntu,kubuntu,etc...
Go to the ubuntu site and get the free cd shipped to you :).

---

### Post by Iandefor on 2008-04-09
How imperative is it that the kernel be 2.6.24 or newer? Will the computer you'll use it with not work properly with an earlier kernel?

---

### Post by shuttleworthwannabe on 2008-04-09
my bad: what i want is ntfs-3g write support; i assumed it came in the new kernel; but either way as long it has ntfs r/w support i am ok.

---

### Post by Balazs_noob on 2008-04-09
> **shuttleworthwannabe said:**
> my bad: what i want is ntfs-3g write support; i assumed it came in the new kernel; but either way as long it has ntfs r/w support i am ok.

IMHO puppy is the best for you as others have mentioned
but if you wouldn't have needed ntfs support then SliTaz ;)

---

