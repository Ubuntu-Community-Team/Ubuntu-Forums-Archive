---
title: "Installation on 128 MB RAM PC using Desktop CD."
date: 2008-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by kagashe on 2008-01-02
I am not recommending running Ubuntu on 128 MB RAM machine but supposing you can't download and burn alternate CD and you have ordered free Ubuntu CD on shipit and have received it, how to proceed with the installation.

Ubuntu 7.10 Gutsy Gibbon has new boot option "only-ubiquity" which does not load the Gnome desktop and only starts Ubiquity installer on default Ubuntu background. I decided to try this option on one COMPAQ Desktop PC with 128 MB RAM.

Following are the steps to install:

1. I don't know whether this step was necessary or not but I booted with Puppy Linux Live CD and created a Linux SWAP partition using the Gparted utility (You could use any other Linux Live CD which can boot on 128 MB RAM or Gparted Live CD).

2. I booted with Ubuntu 7.10 Desktop CD and pressed "Esc" key on boot screen to quit the GUI and reach "boot:" prompt.

3. I typed the following:
boot: live only-ubiquity

4. After a few minutes Ubiquity installer opened in front of me on default Ubuntu background theme.

5. I made the selections on each step and selected "Manual" partitioning method.

6. I selected one empty NTFS partition (already present on the machine) as / partition and changed the format to ext3. The installer had already marked the SWAP partition created in step 1.

7. After entering the User details the installation started and took 3 hours but I could install Ubuntu 7.10 successfully on the machine.

The person for whom I did the job is very happy. I have told him that if he uses the Gnome desktop, it is going to be very slow and to solve this problem he should install Fluxbox and select it on Login screen.

I hope this will be useful to many people.

---

### Post by felker2 on 2008-01-05
kagashe, interesting stuff.

I tried to install **Xubuntu** on a 128 MB RAM system, but after a long startup time, there were a few desktop items, but nothing more. 

As a test, I booted Xubuntu in a 128MB RAM Virtual Machine, with the same disappointing result: no icons, not usable. So I increased the VM's RAM to 384 MB, and then Xubuntu was able to boot successfully and showed a bar with Firefox among other.

This leads me to the conclusion that you can't **install** Xubuntu on a 128MB RAM machine without swap. This seems to be confirmed by your method 1) you created a swap first and 2) you installation in a non-GUI environment.

---

### Post by kagashe on 2008-01-21
> **felker2 said:**
> kagashe, interesting stuff.

I tried to install **Xubuntu** on a 128 MB RAM system, but after a long startup time, there were a few desktop items, but nothing more. 

As a test, I booted Xubuntu in a 128MB RAM Virtual Machine, with the same disappointing result: no icons, not usable. So I increased the VM's RAM to 384 MB, and then Xubuntu was able to boot successfully and showed a bar with Firefox among other.

This leads me to the conclusion that you can't **install** Xubuntu on a 128MB RAM machine without swap. This seems to be confirmed by your method 1) you created a swap first and 2) you installation in a non-GUI environment.
It is not "non-GUI". "only-ubiquity" option loads Metacity WM and works only on Ubunutu CD (not on Xubuntu),

kagashe

---

### Post by az on 2008-01-21
> **kagashe said:**
> 
1. I don't know whether this step was necessary or not but I booted with Puppy Linux Live CD and created a Linux SWAP partition using the Gparted utility (You could use any other Linux Live CD which can boot on 128 MB RAM or Gparted Live CD).

6. I selected one empty NTFS partition (already present on the machine) as / partition and changed the format to ext3. The installer had already marked the SWAP partition created in step 1.


You certainly could have skipped these steps and picked *Guided partitioning - Use Entire Disk*.

I added your tutorial to UbuntuKnowledge.org:
[http://ubuntuknowledge.org/node/92](http://ubuntuknowledge.org/node/92)

---

### Post by tdrusk on 2008-02-08
This works with gOS too.

---

