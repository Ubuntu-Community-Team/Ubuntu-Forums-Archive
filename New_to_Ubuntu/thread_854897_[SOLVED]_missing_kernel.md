---
title: "[SOLVED] missing kernel?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Chelidon on 2008-07-09
Hello Good Linuxers!

I'm quite confounded on this one. I have two different entries in my GRUB: Ubuntu 7.10 2.6.22-15 generic (and recovery, etc) and Ubuntu 7.10 ... -14. My default is -15. The day before yesterday I loaded 201 new updates, six of which failed because of my spotty wifi. I intended to go back and reload them but forgot. The next time I booted I got Error 15. Upon being thoroughly disheartened I resolved to wipe my drive and reinstall. But then I noticed the -14 and lo! it works!

So my question is, what happened to 2.6.22-15? Is there a way to recover it? Should I even bother now that I'm just happy it boots?

---

### Post by ChameleonDave on 2008-07-09
So you're saying that you have 2.6.22-14 and 2.6.22-15 installed and available via the GRUB menu, but only -14 works for you?  Just use -14 then!

Do you want help with making -14 the default option?

---

### Post by Chelidon on 2008-07-09
Well, only that I find it quite mysterious that my -15 died suddenly. -14 works fine, as far as I can tell.

As for editing GRUB, that I can do. What I don't remember how to do is back up menu.lst command line style. Otherwise I simply change default from 0 to 3, if I can figure out how to replace things with either nano or vim.

---

### Post by ChameleonDave on 2008-07-09
I don't know much about -15, because I use -19.  We could investigate to see what kernel packages you have installed, but if -14 works fine, I don't see the point.

To back up the menu.lst file, do this:
```

cd /boot/grub/
sudo cp menu.lst *menu.lst.backup*

```

The bit in italics can be whatever you like.

I advise against vim, unless you are already an expert in it.  It is highly counter-intuitive.  It's not even obvious how to exit the program.

Nano is a much better choice; it's very easy.  You can also use graphical editors from the command line, with "gksudo gedit" or "kdesu kwrite".

---

### Post by Chelidon on 2008-07-10
Thanks a bunch! I did go through 400 lines of a vim tutor on my school's server, so I do know how to do a few simple things (including exit!) but I will use nano anyway.

---

### Post by nowshining on 2008-07-10
have u tried - re-updating the system again? re-run the update to finish up.

---

### Post by Chelidon on 2008-07-13
Looks like adept was interrupted and failed to load something called linux headers in -15. Adept had also been locked in read only since -15 died, and luckily I found the [solution]("http://ubuntuforums.org/showthread.php?t=459781&highlight=unlocking+adept&page=2") quite easily. I haven't rebooted since I recovered my missing updates, but I will report back if indeed I am able to access -15 now.

*edit* yes, I can boot into -15. Woo hoo!

---

