---
title: "Booting issue"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by joe_smith on 2014-01-22
Okay so I was running Ubuntu off my MacBook via USB. I ended up wiping my Mac partition by accident so Ubuntu was the only thing operating on it. It was working fine for 1-2 years until today.




Okay, so this afternoon I tried booting Debian off a USB and it didn't work. I didn't touch dev/sda only dev/sdb which I'm 100 percent positive is my USB because I put crunch bang on here. So anyway installation messed up so I exited the installation via menu and turned my computer back on I get a folder with a question mark, I tried resetting the PRAM, get a terminal, boot from recovery etc. is there anyway to fix it? And if I got the install disk would it work or is there any other way? I had semi important stuff on there so yeah..thanks guys.

---

### Post by Dreamer Fithp Apprentice on 2014-01-23
Much of this is unclear to me, especially
> **joe_smith said:**
> and turned my computer back on I get a folder with a question markWhat does that mean? You sucessfully booted, started a file browser and found only an empty folder with the name "?" where there had been data? I'm not trying to be a smart-ass, but I can't form any clear picture of what you were doing. Because of that I have great trepidation at making any suggestion.

But, and I'm guessing here, it sounds like you have an internal device your system calls /dev/sda that has only one partition and you have or had data and a system that WAS bootable  on that device. And that you have a usb port and when you plug a media device such as a thumb drive, external optical drive, or external hard drive into it that device becomes sdb.

It sounds like you were trying to install Debian from some unspecified sort of installation media, and this part is particularly confusing because it sounds like you were installing it from sdb to sdb. Which actually is possible if sdb were a hard drive with 2 or more partitions, but that would be a VERY unusual scenario.

Anyway, the one thing I can suggest that might help, if it is applicable to your case, and I can't tell for sure if it is, I can put in a very generalized way:

If you had a bootable partition (doesn't matter if it was the only one on the drive or one of many - it's still a partition) and you had another partition (regardless of whether it was on the same device or a different one) to which you attempted to install a second system so you could dual boot, presumably doing the installation by booting from yet another device, typically a cd or thumb drive, as long as you didn't get which partition was which mixed up, your data should be safe, and the system that was bootable should be pretty easy to make bootable again.

If, if, IF, that's what happened, and your sure that's what happened, you just need to try again to install to the partition you were trying to install to when the installation failed.  An installation that fails part way through can leave the system in a state where it is looking for boot instructions in the wrong place. That's happened to me more than once. If that is your situation and you're sure that's your situation I'd try again to install something on the partition you tried to install to before. Anything in the debian family, which includes all 'buntus, should recoginse the other system and give you a grub that will let you choose either. It might the particular installation media you used was bad. Did you check the hash of the downloaded iso against what it was supposed to be? Verify a hash of the actual burned disk or thumb? It could also be some compatibility problem with that particular version of that particular distro. You might try something else. If you do, I'd keep real careful track of any error messages and write them down in case of problems. If you can't install ANYTHING to that partition, you can still regain normal use of the other one with one of those fix-grub utilities disks. In that event, ask and someone will elaborate.

I can not be too strenuous in warning that I'm not clear if any of what I said applies to your situation. If you're not sure it does, DON'T DO IT. In the absolute worst case, and it doesn't sound that bad, at least some of your data, most likely all of it, can still be recovered. But if you aren't absolutely sure you know what you are doing don't do anything that has any chance of overwriting it. Once you overwrite data it becomes astronomically more difficult (for normal purposes, often impossible) to recover it. If this doesn't help, you haven't solved it on your own, and nobody else has a more useful suggestion, try being very step by step explicit in describing your setup and exactly what you did and what happened. Good luck.

-------------

Added afterthought: If in ANY doubt about how to proceed, the safe thing to do is get some media you can boot from, maybe a bootable thumb drive or cd, and some you can write to that has enough capacity to copy all your files and copy them all. You should have them backed up anyway, so if you haven't maybe you should do that first.

---

### Post by joe_smith on 2014-01-23
Basically when I boot it I get a blinking folder with a question mark in a folder, I can't get to my desktop I can't see my mouse, it's just a grey screen with a blinking question mark in a folder. I can't do anything at all.

---

### Post by Dreamer Fithp Apprentice on 2014-01-23
> **joe_smith said:**
> Basically when I boot it I get a blinking  folder with a question mark in a folder,  . . . it's just a grey screen  with a blinking question mark in a folder.I'm not trying to be  pedantic. I'm just trying to get you to be clear. This is meaningless.  "Folders" are files more descriptively and traditionally called  "directories". They contain information about other files, files usually  said to be "in" the folder (although I think that metaphor more  misleading than helpful). Information such as where the files are on the  drive, how big they are, what type of file they are, etc. You see a  folder by either typing "ls" at a command prompt or by opening it with a  graphical file manager like Nautilus, Windows Explorer, or thunar, or a  "traditional" file manager like Midnight Commander. A folder cannot  contain a blinking question mark. A folder contains, or to be more  accurate and less metaphorical, consists of, information, called  metadata, about other files. I suspect (though I'm not certain) whatever  you see consists of white characters on a black borderless screen.  Maybe you are calling square brackets a "folder"? Something like this:
[?]
maybe?

> **joe_smith said:**
> I   can't see my mouseA mouse is a piece of hardware. I assume you  mean the "pointer", often called the "mouse cursor". That would be  consistent with what sounds like a system that hung up before x, the  software that manages the graphical part of all the "grapnical user  interface" or GUI, got started.


> **Dreamer Fithp Apprentice said:**
> If this doesn't help, you haven't solved it on your own, and nobody else has a more useful suggestion, try being very step by step explicit in describing your setup and exactly what you did and what happened.I'm sorry, but I really don't know a better way to say that. If anyone is to have any chance at all of helping you that is essential.

---

