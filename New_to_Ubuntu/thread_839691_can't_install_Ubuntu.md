---
title: "can't install Ubuntu"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by Rustbeard on 2008-06-24
So I have been trying to install Ubuntu but have been having a bunch of problems. Lately it just seems to freeze whenever I go to install it. Usually at the partition formatting stage on the live CD its at 5% on the alternative CD its 33%.
I originally tried dual booting with windows xp already existing on the hdd. It installed fine but the next day Ubuntu froze and I could not get back in it so I just used windows xp. But then a couple days later it wouldn't boot saying that the systems file was missing. So now I tried installing Ubuntu over them and it just keeps on freezing during the installation. I tried using various programs from Hiren's boot CD 8.9 but whenever they scan they always stop or freeze or slow down incredibly to the extent that they would need a whole week or more to scan my whole hdd. 
Does anybody have any idea whats going and what I can do to fix it? Is this just a hdd problem? I hope so cause I'm thinking of just buying a new hdd and try installing Ubuntu again; or take it somewhere to get fixed.
As I usually say to my friends I don't know to much about computers but I know enough to royally screw my self over.

---

### Post by phidia on 2008-06-24
From what you said it sounds like there could be a problem with space available on the hard drive? Is the hard drive reaching capacity? 
That just a guess though and if you try a new hard drive and install to that be sure that your ram meets the minimum requirements. I think you need a minimum of 384Mb for Hardy.

---

### Post by azurepancake on 2008-06-24
If your installing from a disk, when you first boot your computer with the Ubuntu disk, a menu will pop-up asking you to 'Install Ubuntu' or something along those lines. There should be a option to check the CD for errors. You should choose that option to get your disk checked out for any problems.

If problems do come up, then you should be able to burn the .ISO to a new disk and it should install with no problems. But - from the sounds of the hard drive diagnostic tools and you attempting it with both the Live and alternative CD, it might be a issue with your hard drive.

I this helped in some way. Good luck!

---

### Post by Rustbeard on 2008-06-24
phidia - There should be plenty of space now, the old partitions got wiped off when I tried to install Ubuntu over them, so it should be completely empty. I do have 1gb of ram
azurepancake - I did check the cd and it said it was fine, but I did re-download the iso and burned it to a new cd but I got the same problems

---

### Post by phidia on 2008-06-24
You have options you could try the alternate cd and you could also try a command line partitioner called cfdisk. BTW what is the output of sudo fdisk -l?

---

### Post by Rustbeard on 2008-06-25
Ok so I tried to reformat the hdd with my XP disc but it got only to 22% before stopping saying that my disk is damaged, so I'm justgoing to get a new new hard drive and install ubuntu onto it and then send my old one in to get fixed and hopefully that will solve my problems.
Can I install ubuntu straight to a new hard drive and will it format it for me, or should I format it with my XP disc before installing Ubuntu?

---

