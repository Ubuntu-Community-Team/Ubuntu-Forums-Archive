---
title: "Removing corrupted files from a Micro SD card"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Cordelia on 2013-01-18
Hello, everyone!
I'm new to Linux, but loving it so far. I gotta say, though - it's been painful here, out of my "comfort zone"!

Well, today I tried to copy a large folder into a Micro SD card (16 GB) and for some reason I ended up with about 7 GB of corrupted files on it.

I'd like to know how to remove corrupted files from this card. I've tried many things I found here as well as on other sites, but nothing works.

I tried formatting it with GParted, but the SD card "disconnects" automatically and the whole process fails.

When I try to delete the files manually, it says I don't have sudo privileges - which I do.

There's nothing on that card that I'd miss, so if I could just format it, I'd be glad.

So... Anyone? :(

P.S.: Sorry, I forgot to say I'm using Ubuntu 12.10 (32-bit).

---

### Post by mcduck on 2013-01-18
First of all, did you remember to unmount the drive before using gParted? And did you try reformatting it, or actually removing the existing partition and creating a new one?

And second, while you do have sudo privileges, you also have to specifically tell the system when you want to use them. So when you tried to remove the files and go the message about sudo privileges, were you doing it in a terminal using command such as "sudo rm", or using a file manager window which was started using sudo?

---

### Post by Cordelia on 2013-01-18
> **mcduck said:**
> First of all, did you remember to unmount the drive before using gParted? And did you try reformatting it, or actually removing the existing partition and creating a new one?

And second, while you do have sudo privileges, you also have to specifically tell the system when you want to use them. So when you tried to remove the files and go the message about sudo privileges, were you doing it in a terminal using command such as "sudo rm", or using a file manager window which was started using sudo?

Hi, mcduck, thanks for replying.

Yes, I unmounted it. Whenever I'd try to reformat it, the card would simply "disappear" (I'm afraid I lack the knowledge to tell you what exactly happens there, but it's as if I had ejected the card).
As for removing the partitions, same problem: I actually can create a very small partition there (something like 3MB), but can't remove the other one. Since I didn't create any partition before, the corrupted partition is pretty much the entire card.

I tried using sudo commands in Terminal and also tried removing it by using Nautilus.

"sudo rm" doesn't seem to work. Nothing happens... :(

---

### Post by mcduck on 2013-01-18
If you mean that the card disappears from your desktop/file manager etc, that's what's supposed to happen when you unmount it. Anyway whatever is visible in these places is not the card, but the partition instead. And that's what you are trying to remove so it of course can't be mounted and accessed by the system at the time. Unmounting the partition will still leave the device itself accessible by the system so you can then edit the partitions on it.

And also, the *sudo rm* command requires the name of the file(s) you want to remove. Doing it alone will of course do nothing at all.

You can also run "gksudo nautilus" to open a file manager window with root permissions. If it's just a permission issue, that should be enough to allow you to delete the files. But be very careful with that window, and make sure you close it when you are done, as it would allow you to easily delete any important system files or directories as well...

---

### Post by farzad9108 on 2013-01-21
Hello,

I'm also a complete newbie on linux systems. 
I've setup Ubuntu 12.10 on my computer.

I want to **paste some files on the root of my external SD Card** (this SD card is formated into ext4). But I can't do this. In some forums they says that you should "become su" to have the privileges to do this action.

Is there a simple way to do this ?
If not, please tell me if there's a tutorial doing this.

thanks in advance.

---

