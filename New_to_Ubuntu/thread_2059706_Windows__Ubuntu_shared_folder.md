---
title: "Windows / Ubuntu shared folder"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by Sigma1 on 2012-09-18
Hello,
I've just installed 11.04 on a friend's machine, dual-booting with Windows 7. Now, he wanted to access his Windows desktop from Ubuntu, so I also created a desktop shortcut leading to C:\Documents and Settings\username\Desktop\ or something similar. So far so good.
However, on rebooting into Windows, he found his desktop empty of all files and folders. He eventually unearthed them in another desktop folder [sorry not to be more precise... but that's how he explained it]. This has apparently happened more than once.
I would guess it has something to do with file permission conflicts between W7 and Ubuntu, but it doesn't happen on my setup...
For the time being, I've suggested he work on a FAT32 external hard disk, but that's not really a solution.
Any help appreciated!

---

### Post by coffeecat on 2012-09-18
Ask your friend if he is hibernating Windows and then writing to the C: partition from Ubuntu while Windows is in hibernation. Windows 7 saves the state of the NTFS filesystem while in hibernation, and restores it to the pre-hibernation state if it has been changed by Ubuntu. Usually you only lose files saved from Ubuntu, but it is possible this is the problem.

But anyway, writing to the C: partition from another OS is not a good idea even if you shut Windows down properly. It's far better to have a shared NTFS data partition accessible by both operating systems. But even if you use a separate data partition, you must ensure you do not leave Windows in a hibernated state when using Ubuntu. Same story.

---

### Post by Sigma1 on 2012-09-18
Thanks a lot for the answer. I'll relay the information and follow it up... His first experiences with ubuntu have, unfortunately, been the cause of a few nasty cold sweats!

---

### Post by deadflowr on 2012-09-18
Most likely is the windows partition needs to be mounted.
If you create a shortcut to a folder which is on an unmounted partition, an empty page is all you'll get.
There are ways to add a windows partition to the /etc/fstab file which will automatically mount the partition on boot.

Here's one way

[http://www.psychocats.net/ubuntu/mountwindowsfstab]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

I had a similar experience, where I had a second hard drive which I added to fstab and then created a directory to that drive, then later I removed the drive(cleaned up fstab), but kept forgetting to remove the directory, and every so often, I would click on the directory and open up a blank page.

---

### Post by ShadowVegan on 2012-09-18
When I dual partitioned Windows and Ubuntu, I went to places -> Vista to mount my Windows partition within Ubuntu. From there I could navigate to any file I wanted and it worked flawlessly. However, I don't know how to access Ubuntu from Windows.

---

### Post by Sigma1 on 2012-09-19
Thanks deadflowr, yes, I got him mounting the Windows disk before trying to access the Desktop... Tried getting him to edit fstab, but, from a distance, it proved a bit dicey, so I gave that up.
Otherwise ShadowVegan, yes, it works fine for me too, but I'm wondering whether this is something specific to W7.
Thanks in any case. This will give me some new options to experiment with when next I'm in front of the machine.

---

