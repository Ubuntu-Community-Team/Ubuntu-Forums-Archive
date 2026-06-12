---
title: "Swapped video card and now no GRUB menu"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-11-04
This 'puter has both Linux Oneiric Ocelot (ver. 11.10) and Win7 (64bit).

[SIZE="1"]Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3e1e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   143566847    71680000    7  HPFS/NTFS/exFAT
/dev/sda3   *   143572905   174176729    15301912+  83  Linux
/dev/sda4       174176791   781417664   303620437    5  Extended
/dev/sda5       174176793   764420894   295122051   83  Linux
/dev/sda6       764420958   781417664     8498353+  82  Linux swap / Solaris[/SIZE]


My EVGA 9500GT video card had to be sent back to the company. My motherboard, an MSI K9N6PGM2-v2 has an on-board nVidia 6150se "card". After I removed the video card, upon re-boot, I set the BIOS for "internal video".

Upon rebooting I no longer have a GRUB screen which allows me to select which OS I want running.

I tried using a LiveCD and running the GRUB update, but am too inexperienced to understand whether to place the GRUB on /dev/sda3. If I listen to the boot time computer noises and beeps, I can use the arrow cursor keys to load: 

Ubuntu from the pae
Recovery from same as above
or Windows

but I DO NOT see the typical screen with the entries.

---

### Post by jnorthr on 2011-11-04
certainly sounds like something got blitzed. can you try to choose windows to log into ? If you can log into windows and it seems to wok as expected, then the problem will be down to the ubuntu-side of life. If windows does NOT start, then things may be more serious.

---

### Post by Mark_in_Hollywood on 2011-11-04
I can boot into all that GRUB offered BEFORE the problem started. It's just I cannot see what I am doing. It would be hard to run the Memory test. Fortunately, GRUB self boots into Ubuntu (I'm currently running XFCE).

Maybe when I get the 9500GT back this will aright itself. Keep your fingers crossed.

---

### Post by davdo2004 on 2011-11-04
I had a similar problem when I changed my graphics card. If you install startup manager and set the resolution in the display section and also under the advanced tab to 1024 x 768 you should be able to see your boot options again.

---

### Post by Mark_in_Hollywood on 2011-11-06
> **davdo2004 said:**
> I had a similar problem when I changed my graphics card. If you install startup manager and set the resolution in the display section and also under the advanced tab to 1024 x 768 you should be able to see your boot options again.

Worked BRILLIANTLY! Thanks, Davdo2004. I can still remember the piece of Lancastrian cheese I had in 1995, visiting Bolton.

---

### Post by Mark_in_Hollywood on 2011-11-12
After changing the Advanced settings. All went well, until I replaced the RMA'd video card. Upon re-installing that, I can no longer enter GRUB time Recover mode. The screen goes dark (blank) and a moment later a message about:

(vga-769) is depracated . . .

I can press the **Enter** key, and could select one or more of the recovery modes available. I have usually pressed the Enter key without moving the cursor keys up or down. After the Enter key is pushed, the usual GRUB code runs. A moment later and I'm returned to my log-in screen to enter my User Password. I can enter Recovery Mode from that screen, but it's only a terminal, of course.

I've tried to run an Update Grub as well as sudo aptitude install -f, but I'm still seeing nothing at boot time (warm or cold boot).

---

