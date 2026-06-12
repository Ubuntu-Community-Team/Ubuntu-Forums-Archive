---
title: "Installing Ubuntu 11.10"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Maese909 on 2011-11-12
Hello all. I am in the process of installing Ubuntu 11.10 on my desktop via a DVD that has the .iso file burned on it. I am on the screen in Ubuntu that says 
"""Install Ubuntu alongside Windows 7
    Allocate drive space by dragging the divider below"""
 
Underneath it are two sections that are labeled "file" and "Ubuntu"
For the file, it says 509.3 GB and for Ubuntu it says 475.8 GB
Is this what I should go with?
 
P.S. I do want to dual boot with Windows7 and Ubuntu.
My machine has a 1TB harddrive. I will be using Windows a lot too.

---

### Post by lolpenguin on 2011-11-12
Change the partition size by dragging the slider (as instructed). You could go with the default, which is about half-half for both OSes, or you could shrink the Windows partition, make space for another partition to store files on, etc. Have the sizes to suit your needs. Don't have a 512GiB partition when you'll only use 16GiB, unless you plan to have the extra space used up.

---

### Post by Mark Phelps on 2011-11-12
Do NOT drag the slider to shrink Win7.  Doing that risks corrupting the Win7 OS and leaving it in an unbootable state.

Instead, use the Win7 Disk Management utility to shrink the Win7 OS partition.  Leave the new unallocated space as unformatted.

Then, when you boot from the Ubuntu CD, you will need to use Manual Partitioning to format the unallocated space.  BE very careful to not accidentally reformat your Win7 OS partition.

A good idea, to prevent catastrophe in Win7, is after you do the shrinkage, use the Backup feature to create and burn a Win7 Repair CD.  That will allow you to later repair the Win7 Boot Loader -- should that become necessary.

---

### Post by Maese909 on 2011-11-12
Hmm. The thing is that I will be using Windows as the primary OS, so the 478 GB that is labeled under Ubuntu seems wayyy to much. I just got my 1TB harddrive and I don't feel comfortable setting aside that much. Any suggestions on how much I should be using for Ubuntu? I am very nervous to click "Install now" (I've been on this screen for 2 hours lol) because I just bought this desktop yesteday and don't want to mess it up
 
P.S. I will be using Ubuntu for my web development stuff. so Python, vim, HTML, javascript, etc.

---

