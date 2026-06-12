---
title: "[SOLVED] On bootup, i got a routine check of drives. why?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-11
I restarted my computer after adding a splash image to the bootloader menu.lst. when i selected ubuntu, on the ubuntu splash screen with the orange loadbar, is said something along the lines of Routine Disk Check: (Ubuntu: /dev/sda3).

i guess it found nothing wrong, because i didnt get anyother messages. i have never seen this before, and was wondering what it checks, and how routine is routine? was it because i messed with config files? 

thanks.

---

### Post by SunnyRabbiera on 2008-08-11
This is common, dont worry.
The os checks the filesystem for errors every 20 boots or so (the number is random though from my experience)
You did nothing wrong, its supposed to do that.

---

### Post by Victormd on 2008-08-11
This is normal behavior. It does the check every 30+ times you boot. Don't worry about it. It's similar to checkdisk under windows...

---

### Post by OutOfReach on 2008-08-11
Yes, Ubuntu does a routine check of the hard drive, every i believe 30 (?) boots.

---

### Post by SunnyRabbiera on 2008-08-11
> **OutOfReach said:**
> Yes, Ubuntu does a routine check of the hard drive, every i believe 30 (?) boots.

It is between 20 and 30 in my experience, its never quite that consistent.

---

### Post by vikramaditya on 2008-08-11
mine does it every time i've been a bad boy  ;)

---

### Post by alienexplorers on 2008-08-11
Mine does a disk check on bootup if I have been running windows before switching over to Ubuntu.  Seems kind of odd since they are on seperate disks and I don't use the Ubuntu drive while in windows.

---

### Post by OutOfReach on 2008-08-11
Actually now that I remember, when I have been messing around with my partitions, resizing them, etc... and when I boot up into Ubuntu it checks my drives, But that might just be a crazy coincidence.

---

### Post by deathvalleyjoker on 2008-08-11
accually alienexplorers, i was just in my windows partition. so maybe that could be it? I rarely use my windows partition after my first install of ubuntu, and only boot into it for gamming.

Thanks everyone. I got a little crazy when i found all the things i could play with in linux, and have been messing with config files like everyother day, on my path to learn how everything works. I got a little scared when i saw that though.

---

### Post by zuner2012 on 2008-08-11
as posted before "this is normal, you have done nothing wrong", is correct. just press esc when it start. No big deal really just ubuntu making sure it's working correctly.

---

### Post by shae on 2008-08-11
If your Windows partition is on FAT32 and is mounted in Ubuntu, it might be checked every time you boot Ubuntu.  This behavior can be removed from your fstab file.

Instructions: [http://ubuntuforums.org/showpost.php?p=2554034&postcount=3](http://ubuntuforums.org/showpost.php?p=2554034&postcount=3)

---

### Post by ajgreeny on 2008-08-11
You can also change the frequency of the disk check from the default 30 to a higher number; useful if you boot up more than once a day.  Have a look at tune2fs by using ```
man tune2fs
``` in terminal

---

### Post by dan100 on 2009-06-22
Why would it do this if I haven't asked for it.
How cr*p is that.

I'm going to enable root login just to piss them off.

---

### Post by shifty_powers on 2009-06-22
> **dan100 said:**
> Why would it do this if I haven't asked for it.
How cr*p is that.

I'm going to enable root login just to piss them off.

well you could a big security hole in your pc just because ubuntu is doing it's job....

---

### Post by dan100 on 2009-06-22
> **shifty_powers said:**
> well you could a big security hole in your pc just because ubuntu is doing it's job....

It's only a computer

---

### Post by Mornedhel on 2009-06-22
It's *your* computer that will be compromised, but the botnet it will be part of will be making *our* lives miserable. Just because you don't care that your machine will be used to send spam doesn't mean we don't care that our inboxes are clogged with the stuff.

At least make sure your root password isn't easy to guess (hint : "root" and "test" are not good passwords and neither is any word from the dictionary).

---

### Post by dan100 on 2009-06-22
> **Mornedhel said:**
> It's *your* computer that will be compromised, but the botnet it will be part of will be making *our* lives miserable. Just because you don't care that your machine will be used to send spam doesn't mean we don't care that our inboxes are clogged with the stuff.

At least make sure your root password isn't easy to guess (hint : "root" and "test" are not good passwords and neither is any word from the dictionary).

Ok. No worries, I'll wipe it and install Debian tomorrow. So your live won't be so miserable.
Anyway I was just trying ubuntu for mythtv, but it's got to many annoying things in it and hard drive check for no reason was one of them.

---

### Post by shifty_powers on 2009-06-22
heh, well thats up to you. Thats the beauty of having so many distro's, you can choose the one that suits you.

But seeing as Ubuntu os based on Debian, you might not be as happy as you think...

---

