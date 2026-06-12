---
title: "Faulty 11.10 Oneiric Ocelot Upgrade"
date: 2011-06-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sentimentGX4 on 2011-06-13
Hi,

I recently upgraded from Natty Narwhal to Oneiric Ocelot but my NVIDIA drivers won't work with the new Ubuntu version and Ubuntu 11.10 isn't running at all. 

How do I downgrade and remove the Oneiric Ocelot files?

---

### Post by jtarin on 2011-06-13
I tell you if you tell me how to downgrade Win7 to XP? Deal?:p
Did you upgrade your drivers also?

---

### Post by beew on 2011-06-13
Yeah, why would you do that??? OO wouldn't be release til Oct and it is available only for testing and bug reporting. I will be very surprised if there is no major breakage.

---

### Post by jtarin on 2011-06-13
[Approved]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[Not Approved]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by nzjethro on 2011-06-13
> **sentimentGX4 said:**
> Hi,

I recently upgraded from Natty Narwhal to Oneiric Ocelot but my NVIDIA drivers won't work with the new Ubuntu version and Ubuntu 11.10 isn't running at all. 

How do I downgrade and remove the Oneiric Ocelot files?

Currently Oneiric is an Alpha, and is meant for testing and mucking around, not for a system that can't handle regular breakages (i.e. most people's day-to-day system). You are most likely going to have to back up your data, wipe 11.10, and reinstall natty.

By all means, when you're back to Natty, fire up Gparted and create a separate partition to run Oneiric to play around with (that's what I'm doing), but Oneiric won't be released in a stable form until October or so, and even then issues may persist for a few months, so I wouldn't recommend using it as your primary OS just yet.

---

### Post by sentimentGX4 on 2011-06-14
> **nzjethro said:**
> Currently Oneiric is an Alpha, and is meant for testing and mucking around, not for a system that can't handle regular breakages (i.e. most people's day-to-day system). You are most likely going to have to back up your data, wipe 11.10, and reinstall natty.How would I wipe 11.10? Do I have to repartition?

My computer still has Natty Narwhal and older Ubuntu versions available for use. My real question was how do I remove useless Oneiric Ocelot files without touching my other Ubuntu versions, not a literal "downgrade". Are those older Ubuntu verions tied with Oneiric Ocelot? Or are they separate?

---

### Post by dFlyer on 2011-06-14
> **sentimentGX4 said:**
> Hi,

I recently upgraded from Natty Narwhal to Oneiric Ocelot but my NVIDIA drivers won't work with the new Ubuntu version and Ubuntu 11.10 isn't running at all. 

How do I downgrade and remove the Oneiric Ocelot files?

Reinstall whatever version you want over 11.10. Remember 11.10 is very alpha right now and loaded with bug, and subject to multiple crashes, freezes and other bad stuff.

---

### Post by iClouseau88 on 2011-06-14
Hi everyone,

I also have GeForce 7300GT graphic card using nvidia-current driver in Natty.  I discovered a way to make Oneiric runs nvidia-current instead of default "nouveau" which causes my screen to show "NO INPUT AVAILABLE" on a black screen when I installed Oneiric directly, i.e. I chose "install" off the bat on the first menu.  Here's how:

1. Choose try Ubuntu Oneiric and just hit login.

2. Hit Install Oneiric icon on the upper left corner.

3. Ubuntu Software Center > Ubuntu Software > Nvidia X-org driver 173 (or 90) > Install

4. Now Synaptic Package Manager shows "nvidia-current" whereas it doesn't before. Put a check mark to the left, and hit Apply to install this driver. 

5. Reverse the process in Step 2 to un-install Nvidia X-org 173 (or 90) driver. Actually this can be done before or after restart in Step 6 below.

6. Restart.

---

### Post by nzjethro on 2011-06-14
> **sentimentGX4 said:**
> How would I wipe 11.10? Do I have to repartition?

My computer still has Natty Narwhal and older Ubuntu versions available for use. My real question was how do I remove useless Oneiric Ocelot files without touching my other Ubuntu versions, not a literal "downgrade". Are those older Ubuntu verions tied with Oneiric Ocelot? Or are they separate?

If you upgraded an old release to Oneiric then yes, that Oneiric version is "linked" to the version that you upgraded from, in that those files and folders are now the files and folders for your Oneiric. If you didn't upgrade, but installed it on a new partition, you should be able to wipe the Oneiric partition without messing with your other files. How did you go about your installs?
Maybe do you want to post a GParted screenshot, it'll clear things up a bit, and there's less chance of us nuking the parts of your system you want un-nuked. Haha.

---

### Post by VinDSL on 2011-06-15
> **nzjethro said:**
> Maybe do you want to post a GParted screenshot, it'll clear things up a bit, and there's less chance of us nuking the parts of your system you want un-nuked. Haha.
~Cool

GParted screenie / show n' tell  LoL!  :D

Here's mine:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-15-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-15-jun-2011.png")[/INDENT]


My UbuOO install is sitting in a partition named "Ubuntu 11.04".

It's Ubu00 repos, on a UbuNN Alpha-1 install. Heh!


BTW, in advance; yes, I know I can share swap partitions, but I prefer to keep them separate...  ;)

Anyway, this works out V well, for me, e.g. dual-booting a stable install with a dev release.

Got all my bases covered, you know?

---

### Post by lkjoel on 2011-08-02
Try this: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

---

