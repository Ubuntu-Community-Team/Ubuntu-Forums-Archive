---
title: "New notebook with Windows 8: best way to back it up?"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by fparri on 2013-06-29
Hi everybody!

I've just bought a new notebook, with Windows 8 pre-installed. I am removing it in favor of Ubuntu. I will keep it for a 2-3 years but, eventually, I will sell it to change PC. Since I have no recovery DVD, what is the best way to back up windows 8 in order to restore the machine to an 'almost new' situation, when I will sell it?

Sorry for my English, I hope I was clear enough. Otherwise, I'll try to clarify myself :))))

---

### Post by squakie on 2013-06-29
Most laptops and a lot of desktops haven't shipped when any recovery media.  Instead, the manufacturer normally has pre-installed a utility to let you create "restore to factory defaults" disks.  This procedure varies by manufacturer, but it is usually found in the Windows 8 menus for the manufacturer.

I'd check closely (remember - there are "hidden" objects on the Windows 8 menu screen, right-click near the bottom right and it should give you an option to show all) to see if the utility has been provided.  It may be called system backup or something similar.

---

### Post by claracc on 2013-06-29
I think that you will do the task better with the own windows tools.

 Note, that in order to re install win 8 you will need a win 8 installation DVD.

Here, there are two links to do a "recovery disk" and resseting the pc to its original settings:
[http://www.techrepublic.com/blog/window-on-windows/create-a-recovery-drive-in-windows-8/7261](http://www.techrepublic.com/blog/window-on-windows/create-a-recovery-drive-in-windows-8/7261)
[http://www.techrepublic.com/blog/window-on-windows/reset-your-pc-from-a-windows-8-recovery-drive/7438](http://www.techrepublic.com/blog/window-on-windows/reset-your-pc-from-a-windows-8-recovery-drive/7438)

For more information I would ask in a windows forum.

---

### Post by squakie on 2013-06-29
And the manufacturer supplied tool does exactly that - no need to use 3rd party products if the manufacturer has supplied their own.  Theirs will do the work for you - just start it and load disks as it asks.  No need to make things more difficult than the need be for a new user.

---

### Post by Cheesemill on 2013-06-29
I use [Clonezilla]("http://clonezilla.org/") to make an image of all of my new machines before wiping them and installing Ubuntu.

---

### Post by fparri on 2013-06-29
I see. Thanks for all the info. I'll check and see all the links I was give.

As far as Clonezilla is concerned, will it work also with Windows 8 partitions?

Also. What if I recover my Windows 8 product code and use it to re-install my system via an OEM DVD, when I need it?

Ok, I reckon we're moving a little too Windows-ish, so I'll stop my doubts here :))))

Again, thanks a lot for the precious info :)

---

### Post by claracc on 2013-06-29
You are welcome

---

### Post by Mark Phelps on 2013-06-29
Win8 provides a way to make full system backups -- that is what you should use, not Clonezilla or other Linux utilities.

You could also use a very good, free, third-party tool known as Macrium Reflect, to image off the entire disk.  Do NOT just back up the OS. To restore the PC to its current state, you need to image off the entire disk.

Also, the product code for Win8 preinstalled PCs is generally NOT printed anywhere on the machine; instead, it is embedded in the BIOS.

Seriously,  if you want detailed accurate Win8 advice -- then go to the Win8 forums: eightforums.com.

---

### Post by oldfred on 2013-06-29
I liked the suggestion one user said he does.

He just removes hard drive and installs a SSD. Then when he wants to sell system he just puts hard drive back in. And with SSD system is a lot faster.

---

