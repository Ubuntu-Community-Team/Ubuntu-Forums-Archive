---
title: "System crashed - Internal HDD and Live USB"
date: 2011-05-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-05-15
It did a filesystem check to show that my /home is corrupted and gave me three options to recover or ignore or something else i can't remember. I have not been able to boot since then. It goes blank after GRUB. There is no GDM screen. I was using btrfs.

I fired up Live USB. It is able to boot and my home folder is there but it crashes too.

I am running windows just fine so it is not a hardware problem.

Thanks.

---

### Post by dino99 on 2011-05-15
you get a kernel panic (as often on my system too :()

it should start on recovery mode, then select "repair packages", then select "classic" while logging into gdm, then watch logs to find errors

---

### Post by donniezazen on 2011-05-15
> **dino99 said:**
> you get a kernel panic (as often on my system too :()

it should start on recovery mode, then select "repair packages", then select "classic" while logging into gdm, then watch logs to find errors

The CLI might not be connected to wifi to download packages. 

I am making a kubuntu live USB to check if it works. I will try you suggestion in a few.

Thanks.

---

### Post by donniezazen on 2011-05-15
I have waited for 10-15 minutes but i can't get to recovery console. I will give it another try this evening. Please see the picture for error.

Why is Live USb crashing if Ubuntu installation is corrupt?

---

### Post by ssam on 2011-05-15
"Note that Btrfs does not yet have a fsck tool that can fix errors. While Btrfs is stable on a stable machine, it is currently possible to corrupt a filesystem irrecoverably if your machine crashes or loses power on disks that don't handle flush requests correctly. This will be fixed when the fsck tool is ready."

[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

however a corrupt filesystem should not stop a live USB/CD from booting. then there is a small chance you could mount the disk and rescue files.

---

### Post by donniezazen on 2011-05-17
Yeah, it won't let even USB live to work if i open the home folder. I just formatted the system.

Thanks.

---

