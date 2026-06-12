---
title: "How do I completely switch to Ubuntu"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Dj Melik on 2008-10-06
Ok, recently I duel booted my Ubuntu with my Windows XP using the new Wubi installer, and I just completely fell in love with Ubuntu. Its way better than Windows, both performance wise and visual appearance. Anyways how can I delete my Windows partition and just expand my Ubuntu partition.. The thing is I installed using Wubi and it seems a little confusing.

[img]http://omploader.org/vdDBz/Screenshot.png[/img]

There is a screenshot of my Partitioning.

---

### Post by SpenceMakesSense on 2008-10-06
well you can just format the ntfs hardrive into a linux format and ubuntu will be able to access it with no problem
EDIT: I actually just remembered that wubi installs things differently so remember what I said but dont do that right away

---

### Post by Dj Melik on 2008-10-06
> **SpenceMakesSense said:**
> well you can just format the ntfs hardrive into a linux format and ubuntu will be able to access it with no problem

Yeah but will my files on Ubuntu be formatted as well?

See this is the thing..


How does Wubi work?

Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.

If i format my windows, my ubuntu will be formatted as well.

---

### Post by rybaxs on 2008-10-06
Do you want to have an dual boot?
like Ubuntu and Windows?

- Try to give some space for the new partition by dragging the middle bar line to the center or any disk space you want.

 ok here's the visual

- Did you see that green box ( /dev/sda1 232.88GB), that is the Windows partition
- The other box is the broken line box at the right, try to drag the line between this boxes..
  this broken box is for your new OS(Ubuntu).

---

### Post by mikewhatever on 2008-10-06
Well, there is no Ubuntu partition to speak of. Wubi installs Ubuntu within the Windows NTFS partition, so that if you format it, Ubuntu will be gone.
One way to solve it would be to use GParted Live cd to resize the NTFS partition, create another partition to backup your files, and then reinstall Ubuntu wiping Windows in the process.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by OutOfReach on 2008-10-06
Wubi installs Ubuntu inside Windows (So I've heard) so Ubuntu is physically located inside the Windows filesystem, so my theory is that it will be a difficult to seperate Windows and Ubuntu. Unless you would want to reinstall Ubuntu...

---

### Post by Dj Melik on 2008-10-06
Aww, I was really hoping I wouldn't have to reinstall Ubuntu.. I just finally finished customizing and setting up all my programs :(.

Thanks everyone.

---

### Post by Patrick793 on 2008-10-06
You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to create a real partition out of your Wubi install (copies everything over, files, settings), and then wipe out the windows partition and expand the ubuntu one.

---

### Post by Dj Melik on 2008-10-06
> **Patrick793 said:**
> You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to create a real partition out of your Wubi install (copies everything over, files, settings), and then wipe out the windows partition and expand the ubuntu one.

Thank you!

---

### Post by OutOfReach on 2008-10-06
> **Patrick793 said:**
> You can use [LVPM](http://lubi.sourceforge.net/lvpm.html) to create a real partition out of your Wubi install (copies everything over, files, settings), and then wipe out the windows partition and expand the ubuntu one.

Hmm, never heard of this. Looks extremely useful.

---

### Post by zephyrcat on 2008-10-06
I found a link to this tutorial from the Wubi FAQ:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Hope that helps!

---

### Post by scradock on 2008-10-06
If you want to get rid of Windows completely, you will have to install a new Ubuntu system in a new partition, then move your linux files from the Wubi portion of your windows system to the new Ubuntu partition, then delete the Windows partition. As Wubi installs within the Windows partition you can't make it take over in a simpler way.

Of course, you can simply stop using any Windows programs and boot into Ubuntu using the Wubi boot option, but a lot of your hard-drive will be taken up by a Windows system you aren't using.

Even simpler, perhaps, if you can put all the files you really need to keep onto a flash drive, would be to do that, then wipe the old system completely and install Ubuntu from a live-CD. The 8.04.1 install is good, and will update to Intrepid Ibex anytime you're ready.

So, steps I would recommend:

1. Burn a new live CD of Ubuntu 8.04.1;

2. Copy all your files off the hard drive onto a memory stick, or even a CD;

3. Install 8.04.1 from the Live CD using all the hard drive space it can find;

4. Copy back your linux files to a suitable location in your new system.

And may the Force be With You!

---

### Post by louieb on 2008-10-06
> **Patrick793 said:**
> You can use [LVPM]("http://lubi.sourceforge.net/lvpm.html") to...
And from the WUBI section of the forum .  May want to take a look at the poll an see how well it has worked for others. [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

