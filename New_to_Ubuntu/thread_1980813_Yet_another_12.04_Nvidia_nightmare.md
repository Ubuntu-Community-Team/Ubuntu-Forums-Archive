---
title: "Yet another 12.04 Nvidia nightmare"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by fraterchristopher on 2012-05-15
I've been desperately trying to get Xubuntu 12.04 to work on the old, diesel-run Toshiba Satellite p20-842 that I use for my work, but I have a huge display problem. The laptop has a 1440X900 display, and an Nvidia Gforce FX 5200 card. After the install, everything seems to display correctly, but LibreOffice loses all of the text from the middle of the screen down. Also, when I open Terminal Emulator, if I move it down the screen, it slides behind the half-mark as if the screen were opaque at that point. I've tried many different proposed solutions, but nothing seems to work. Any ideas out there? 

Pax et Bonum

---

### Post by fraterchristopher on 2012-05-16
Well, I actually solved the problem myself, and I'm posting what I found, because it works, to my surprise! If you have an old Nvidia card like I do, open Synaptic Package Manager and see if "nvidia-nouveau" is installed by searching for it. If it is, this fix should work for you too!  

**Step 1**: Run a text editor of choice (I used "**sudo leafpad**" in the terminal emulator - "**sudo gedit**" or "**sudo vim**" may also work, I think depending on your flavour of Ubuntu)
 
**Step 2**: Create a new file with the following contents:

**options nouveau noaccel=1**  

**Step 3**: Save the file as **nouveau.conf** in the **/etc/modprobe.d/** directory. (Click on "File System", then the "etc" directory, and then the "modprobe.d" directory. Here's where you want to put your new file!)

That's it! No more half-screen issues. I guess there's some problem with the "nouveau" Nvidia drivers that this somehow limits. I've been issue-free since I did this. Hope someone else finds it helpful!

---

### Post by Journeyman1962 on 2012-06-04
Been scouring the internet for a week to find the solution to this problem.
Thank you so much!

Tim

---

