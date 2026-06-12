---
title: "video drivers???"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by gene simmons on 2011-10-19
hi all,i am suffering from the dreaded freeze problems and i read chenging the video drivers may help,i dont have any propietary drivers in additional drivers so how would i uninstall and install and veiw what drivers i am curently using,my laptop is a hp g62 3g ram t4500 intel,thanx in advance

dave

---

### Post by Mark Phelps on 2011-10-19
Open a terminal, enter "lspci" and look for the line containing "VGA".  If, as I suspect, that says you have an Intel chip, the drivers are already installed.  The Additional Drivers option only applies to AMD or Nvidia cards/chips.

---

### Post by 3rdalbum on 2011-10-19
If you're getting freezing problems, it might be graphics drivers or it might be bad RAM.

If you're using Intel graphics, those are pretty stable on Linux. So your next stop should be checking for bad RAM using Memtest86+ (run it all night).

If there are no errors when you wake up in the morning, try Phoronix Test Suite's memory benchmarks - they can often crash the computer instantly if it's a RAM problem.

If you do have bad RAM, the only course of action is to get the RAM in your computer replaced.

---

### Post by gene simmons on 2011-10-19
thnx for the replys so far,ur rite it says intel graphics in terminal,i will try the memory test tonite and see what comes up,i just bought this last week so i would hope it doesnt have bad ram and windows 7 works fine on it,i havent tried many diferent distros on this machine,i am running luninux and i really like it so i hope i dont have to change,i updated the kernel to 3.1 as i read that may help and updated the bios hoping that would also help but none have so far,such a weird thing,it will freeze 5 times in one day then wont do it for 2 days,not sure what to do,return the laptop and try a diferent brand or specs or try a diferent distro,i have been reading mannnnnnny posts on freezing in 11.04 so i think its common,hope someone has a sollution soon,thanx for replys

---

### Post by crjackson on 2011-10-19
Hi Gene,

I bought a g6 yesterday with an i5 and 4GB Ram. It has Intel Video also.. I can't even get my to boot to the install screen unless I edit the boot line to include 'nomodeset' Otherwise I get a black screen.

I'm trying to figure out how to get the video supported well enough to get the correct screen resolution and 3D (read compiz) graphics.

Can you tell me what video driver you are using and other than the freezing, do you have 3D support with Ubuntu 11.10?

Did you have to clear the restore partition and/or the HP tools partition to make an available primary partition flag for your install?

Thanks...

Here's my request for help, but as usual, the community my requests.

[http://ubuntuforums.org/showthread.php?t=1864326](http://ubuntuforums.org/showthread.php?t=1864326)

---

### Post by collisionystm on 2011-10-19
> **gene simmons said:**
> hi all,i am suffering from the dreaded freeze problems and i read chenging the video drivers may help,i dont have any propietary drivers in additional drivers so how would i uninstall and install and veiw what drivers i am curently using,my laptop is a hp g62 3g ram t4500 intel,thanx in advance

dave


install htop

sudo apt-get install htop

open a terminal

run htop

htop


put it off in the corner and keep and eye on your CPU usage when its freezing. If the CPU is maxed, look to see what process is causing it. It should be listed at the top. It is probably compiz.

install gnome-shell to see if you get a smoother ride

For me, gnome-shell was a night and day difference to unity with an intel card.

---

### Post by 3rdalbum on 2011-10-19
Windows reserves up to 2 GiB of memory for itself, and never uses much of it. Linux only reserves what it uses, and tries to use as much as possible when it can to speed things up. Therefore, it's possible to not notice a problem in Windows because the faulty part is within the reserved-but-unused space.

---

