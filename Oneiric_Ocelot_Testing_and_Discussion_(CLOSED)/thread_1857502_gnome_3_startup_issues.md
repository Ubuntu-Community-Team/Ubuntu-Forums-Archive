---
title: "gnome 3 startup issues"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by odror on 2011-10-10
[FONT="Courier New"][SIZE="1"](I was asked to re-post in this forum)[/SIZE][/FONT]

I have upgraded from ubuntu 11.04 to 11.10.

I have the following issues:

1. There is a significant delay on start-up. and logout (when compared to Unity or kde)

2. I get a minimal useless shell. with a panel but no system tray or any other useful menu. I have a black bar on the top with no date or any of the system tray items. On the left side it has the following items file, edit, view, go, bookmarks and help. I do not have the Unity bar. It looks like an empty shell with no theme. The defualt theme or shell are not activated. (all of theme are installed). I have to use CTR-ALT-DEL to get out of it. 

3. On dual monitor (using separate X display) the second display is white with no active display manager. (the same issue is in Unity, but not in kde)

---

### Post by effenberg0x0 on 2011-10-10
Hey,

1) See Lucazade solution, mainly post #25, here: [http://ubuntuforums.org/showthread.php?t=1853484](http://ubuntuforums.org/showthread.php?t=1853484)
2) Try to follow the steps in this thread ([http://ubuntuforums.org/showthread.php?t=1856517](http://ubuntuforums.org/showthread.php?t=1856517)), post #2 and report your results.
3) Do you have an Nvidia VGA Card? See if this relates: [http://ubuntuforums.org/showthread.php?t=1849562](http://ubuntuforums.org/showthread.php?t=1849562)

Regards,
Effenberg

---

### Post by odror on 2011-10-10
> **effenberg0x0 said:**
> Hey,

1) <wait>
2) Try to follow the steps in this thread ([http://ubuntuforums.org/showthread.php?t=1856517](http://ubuntuforums.org/showthread.php?t=1856517)), post #2 and report your results.
3) Do you have an Nvidia VGA Card?

Regards,
Effenberg

I will try it this evening when I get home, but I do have an nvidia cards (GT(X os S) 240. I have done the upgrade by taking the OS drive (SSD) from Dell XPS420 to DEL XPS9000 ( where the upgrade was done.

---

### Post by effenberg0x0 on 2011-10-10
I see. The HDD move from system to another is not guaranteed to work. During install / update, some settings automatically made are specific to the host hardware. After the HDD is moved, these settings might not work in the new host hardware. But most things can easily be fixed.

You must consider removing / purging video drivers and reinstalling nvidia-current as an option.

Post your results / doubts when you're at the PC.

Regards,
Effenberg

---

### Post by odror on 2011-10-10
> **effenberg0x0 said:**
> I see. The HDD move from system to another is not guaranteed to work. During install / update, some settings automatically made are specific to the host hardware. After the HDD is moved, these settings might not work in the new host hardware. But most things can easily be fixed.

You must consider removing / purging video drivers and reinstalling nvidia-current as an option.

Post your results / doubts when you're at the PC.

Regards,
Effenberg

I fixed  minor things so that the OS was working on the new computer before the upgrade. I did delete the xrog.conf file reinstall nvdia driver and created new xorg.conf file. Everything is working fine with kde (2 monitors) and Unity(except for the second monitor)

---

### Post by odror on 2011-10-11
Problem solved, but Nvidia/gnome3(or Ubuntu 11.10) incompatibility is detected.

All the issues above were resolved when I changed the nvidia setting from "separate X Screen" to "TwinView"

---

