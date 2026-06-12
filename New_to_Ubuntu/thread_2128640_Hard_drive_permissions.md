---
title: "Hard drive permissions"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Implactus on 2013-03-23
Sorry for the hijack.
I'm very new and not a dab hand at programing. So bare with me please.
I am attempting to clone my hard drive on my laptop as it has run out of space. I have installed 12.04 on a fresh drive and have managed to copy the home folder. I read somewhere on the forum that I also need to copy ect.
Every time I try this i get an error message telling me that I don't have permition. 
Why is that and what is the best way to go about cloning the original drive?

---

### Post by oldos2er on 2013-03-23
Post moved to its own thread.

---

### Post by NimalNet on 2013-03-23
I don't really get what you are trying to accomplish but you could try: $ sudo cp 

You could also make an image of your disk using Guymager

---

### Post by papibe on 2013-03-23
Hi Implactus.

This is what I would do:
[LIST]
[*]Clone the root partition with Clonezilla, or copy the the partition with gparted.
[*]Then use the Ubuntu installation media as a live CD/USB to access the fstab and update the disks UUIDs.
[*]Reboot, and get into the BIOS to update which disk to boot from.
[*]Once you got a working installation, I'd copy your personal files to your home directory.
[/LIST]
Just some thoughts.

Let us know how it goes.
Regards.

---

