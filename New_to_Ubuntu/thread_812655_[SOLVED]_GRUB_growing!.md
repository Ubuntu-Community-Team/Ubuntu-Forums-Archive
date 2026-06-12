---
title: "[SOLVED] GRUB growing!"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-05-30
Hi,

OK, hands up. It must be my fault 'cause things don't just happen. Having said that, I've no idea what I've done.

Anyway, I have a dual boot option. Usually I have 6 options (I can't remember all of them) but they're along the lines of -

1. Ubuntu....
2. Ubuntu....kernel
3.
4.
5.Windows XP....
6.

I know that XP was no.5 in the list 'cause I made a point of remembering this so I didn't have to put my glasses on every time I booted:)

However, when I booted my machine yesterday evening I noticed 2 extra lines - basically, the first two lines were repeated. Is it safe for me to edit menu.lst and just remove these?

---

### Post by markoloka on 2008-05-30
They're probably new kernel. Read what it exactly says on each line. Numbers are different. It's ok to edit menu.lst. Just comment them out w/ # mark.

---

### Post by forestpixie on 2008-05-30
When kernel changes occur then the menu.lst changes - if you don't know which you're removing you could get yourself in a bit of a mess :)

You can post it here if you like for a look

---

### Post by angry_johnnie on 2008-05-30
You could just comment out the lines you don't want.  (add # signs at the beginning).

Even if you deleted them, I think a grub update would restore them back, so don't bother. :-)

Besides, all those extra lines are older kernel versions, and sometimes it's handy to have at least one, just in case the latest kernel refuses to boot.

---

### Post by 505 on 2008-05-30
If you edit them, edit the third and forth line. Probably a new kernel was installed, causing the installer to add this new kernel to the GRUB menu. If the new kernel works you can delete the reference to the old kernel from the menu, or even remove the whole kernel via apt. This will also remove them from the GRUB menu. Note that is it recommended to keep at least two kernels on you system, in case the newest fails due to some error.

---

### Post by Tim Silver on 2008-05-30
Ah, thank you.

I would have edited lines 1 and 2 - silly me!

---

### Post by dwhitney67 on 2008-05-30
Yes, it is safe.  Just edit with courage!

The menu.lst is a simple file that, based on the data, references files that are located within your partitions.  The most prominent partition (well at least I think so) is the one containing your Ubuntu kernel.  Generally this is in /boot and /boot/grub.

The next time you boot into Ubuntu, check to see which kernel you are running.  Here's how:
```
$ uname -r
```
Whatever version number is spit out is the kernel that you are booting.  Examine your /boot/grub/menu.lst to confirm this.  Any kernel versions which are older can be removed (i.e. deleted).  _Be careful_ not to remove the one that boots your M$ partition.  It should be "obvious" which one is this.

After you complete this task, don't be surprised if your current Linux kernel and your Windows kernel are the only two entries remaining in your menu.lst file.

P.S.  If you have other Linux partitions (i.e. Linux distros such as Fedora) on your system, then there may indeed be a bonafide reason to have other entry points in your menu.lst.  Thus far, from what you have mentioned, this is not the case.

P.S.S.  If you are worried about deleting entries from your /boot/grub/menu.lst file, then don't... just preface each entry that you want the Grub boot-loader to ignore with a '#' character.

---

### Post by forestpixie on 2008-05-30
Further - once you are sure that you no longer need the older kernels you can delete them properly, removing them from menu.lst only does that.

Although I would suggest making sure you have 2, current and previous available.

---

### Post by kpkeerthi on 2008-05-30
Search for **linux-image** in synaptic and mark the kernels you don't need for complete removal. Your GRUB will be automatically updated. 

If you just remove the entries from /boot/grub/menu.lst, you will still have kernel packages installed, occupying space unnecessarily.

---

### Post by Tim Silver on 2008-05-30
Once again, thanks all.

I don't have my laptop with me at the moment but will comment out this evening.

I don't have to worry about partitions (as such) - being a scaredy-cat (and also to maintain my machine integrity:)) I installed the heron to an external USB HDD.

However, being a noob to any OS other than Windows I wasn't sure what was going on. The only other time I've dual-booted was when I first tried XP along-side 2000!

I guess the extra lines were added after a system update earlier yesterday - nice to know it wasn't something foolish that I'd done:)

However, re-reading this just before posting, I notice I haven't maintained my machine integrity! I cannot start my laptop if the external drive is not plugged in. Is there a way around this? What happens if the external drive packs-up?

---

### Post by Duck2006 on 2008-05-30
> However, re-reading this just before posting, I notice I haven't maintained my machine integrity! I cannot start my laptop if the external drive is not plugged in. Is there a way around this? What happens if the external drive packs-up?

Thats because your MBR of your internal drive has grub files loaded on it and it you remove your external drive grub can't find the files that it needs to boot. You will have to restore your internal drive's mbr and then install grub on your external drive's mbr.

---

### Post by Tim Silver on 2008-05-30
Me again,

Don't bother answering my last question - just found a post by meierfa in 'Installation and Upgrades' that covers it.

Thanks all the same.

---

### Post by Tim Silver on 2008-05-30
Sorry Duck,

Didn't mean to appear rude - our posts crossed.

---

