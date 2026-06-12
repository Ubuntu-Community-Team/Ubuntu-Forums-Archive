---
title: "[SOLVED] Virtualbox - Where's my new 'hard drive'??!!"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by slibuntu on 2008-11-23
I created a new HDD for my virtualbox XP install.

Where is it?? Take a look at the pic below, the HDD icon at the bottom lists there being 2 HDD's, so where is the second one??

[IMG]http://compsoc.nuigalway.ie/~slibuntu/vb.png[/IMG]


Thanks!

---

### Post by beno1990 on 2008-11-23
On the main Virtualbox window (the one where you load your VMs), select the XP VM from the menu and choose settings, and go to "Hard Drives". Make sure both drives are listed there. If not, on the right hand side there should be an icon of a hard drive with a little "+". Click that and choose the new hard drive you want to attach to your VM.

---

### Post by slibuntu on 2008-11-23
I did that, and that's why at the bottom of the screen if you hover over the little hard drive icon, it shows up the two disks, it's puzzling me!

---

### Post by slibuntu on 2008-11-23
Found the answer

In XP,

Control Panel -> Administrative Tools  -> Computer Management -> Storage -> Disk Management

Then initialise the new disk and create a new NTFS partition on it

---

