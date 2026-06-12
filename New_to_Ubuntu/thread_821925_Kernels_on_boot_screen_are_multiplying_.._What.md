---
title: "Kernels on boot screen are multiplying? .. What?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by QuizasQuizas on 2008-06-07
I'm dual booting Hardy and Vista, so every time I boot up, GRUB asks which partition to use - but about a week ago, a second kernel appeared on the boot screen, and now (as of yesterday), a third. What on earth does this mean? Must I have so many kernels? How many kernels *should* be present?? (Is the result of a system update, or did I pull a stupid?)

Any advice is appreciated, and thank you for your time!

---

### Post by mgranet on 2008-06-07
> **QuizasQuizas said:**
> I'm dual booting Hardy and Vista, so every time I boot up, GRUB asks which partition to use - but about a week ago, a second kernel appeared on the boot screen, and now (as of yesterday), a third. What on earth does this mean? Must I have so many kernels? How many kernels *should* be present?? (Is the result of a system update, or did I pull a stupid?)

Any advice is appreciated, and thank you for your time!

There's been a few kernel updates recently, which for some reason are adding to the list, instead of replacing. Edit your /boot/grub/menu.lst file to remove the kernels you don't want to boot to.

---

### Post by drs305 on 2008-06-07
As new kernels are introduced, they are added to the grub menu list. Go to System > Administration > StartUp-Manager> Advanced. Limit the number of kernels in boot menu.
For more information on StartUp-Manager and boots displays, please take a look at:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by bumanie on 2008-06-07
The list grows as new/updated kernels are released. It is a good idea to have at least one old kernel around in case a new breaks. You can > gksudo /boot/grub/menu.lst  and put a # in front of the lines of the older kernels to stop them coming up in the list. This does not remove them, just makes them not seen on the list. You could remove the oldest kernel if you wish (via synaptic), but I would always keep at least one that is known to work, just in case something goes wrong.

---

### Post by Toadmund on 2008-06-07
I always assumed it was because, that if the kernal update borked, you always had the option to go back to your old kernal and fix the problem or wait till the update was fixed.

---

### Post by ImpressMe on 2008-06-07
I removed both of the old kernels. I released 400MB! It is just great usability to let end users choose between kernel versions. They will know exactly what it is about...

---

### Post by Xerp on 2008-06-07
Yeah, lots of updates recently. I take the old ones out :)

---

### Post by drs305 on 2008-06-07
> **Toadmund said:**
> I always assumed it was because, that if the kernal update borked, you always had the option to go back to your old kernal and fix the problem or wait till the update was fixed.

That's a good reason. There is another 'safety' feature in StartUp-Manager (and in grub menu itself). You can set it to either use the new kernel immediately (well, at next boot) or you can leave it set to continue to use the same kernel until *other users* determine that it is relatively bug-free. When you are ready, then you can go in and select the newer kernel.

This is covered some in the link provided in my previous post.

---

### Post by gameryoshi600 on 2008-06-07
Keep some of the old ones as backup.

---

### Post by Promaster91 on 2008-06-07
If you want to remove any old kernels and save some space on your hard drive, go to Synaptic Package Manger and search for linux-generic. There you can remove any old kernels that are not needed. Watch out that you don't remove the kernel that you are currently using!! The grub boot loader will automatically update to the changes made. Also, keep one for a backup, just in case :).

---

