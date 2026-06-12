---
title: "Changing the root filesystem"
date: 2009-11-19
forum: Programming Talk
---

### Post by praytor on 2009-11-19
How do I change the root filesystem to another filesystem?  Does the answer to this question change if I say it's a FUSE filesystem?  The FUSE filesystem is intended to intercept filesystem calls to the 'old' ext3 root filesystem and modify the reads/writes for caching & statistics collection.  So at boot time I need to somehow mount the ext3 filesystem and the FUSE filesystem and then pivot to the FUSE filesystem from the initrd filesystem.  I know I can use pivot_root for this purpose but I'm not sure about the details.  It seems I need to modify initrc to do this?  Is that as complicated as it sounds?  Is there a better way to do this?  

Thanks,
praytor

---

### Post by meson2439 on 2009-11-19
The only way I knew is by formatting it. Sorry that I couldn't help.

If you happen to discover how to do it, please enlighten us.;)

---

### Post by holiday on 2009-11-19
It must be possible. You must dig into it. 

Maybe chroot would work if you could invoke it with your gui shell startup - assuming that's the scope of your concern and that such a wild idea is possible to implement. Grasping at straws here...

---

### Post by praytor on 2009-11-19
Hi guys, it's definitely possible, I've heard of people doing it before, I just don't know how to do it myself.  :)

I think it has to be done at boot time, while the system is still initializing.  It could be done during the GUI start up (eg when user logs into gnome desktop), like you said, but then I'm not sure pivot_root (see [http://linux.die.net/man/8/pivot_root](http://linux.die.net/man/8/pivot_root)) would have affected everything it should.  It needs to be done by some sort of init-like process so that all the children have been pivoted to the new root.

Edit: 
To clarify my problem, I'm not sure how to do pivot_root at boot time, and not sure this is even the best way of changing the root filesystem.  It sounds like there could be a different way of changing the root filesystem for all users, eg via fstab maybe?, that is simpler.  Whatever way I do it, it has to be transparent and not require the user to do the pivoting himself at the console after logging in.  

I'm also looking for a way to ensure that, if somehow my new root filesystem code (which I've written myself) is buggy and crashes, that I can somehow fallback to another filesystem (eg the old root filesystem)-- I'm assuming that this kind of behavior is not automatic.  It would be very nice if this could be possible, so that debugging my filesystem layer is easier for me..

---

### Post by holiday on 2009-11-19
Chroot is a shell setting. It's used, in one of its ways, as a way of locking users out of system files so that the root of the machine is the user's home directory. Or some arbitrary harmless place.  

$ls /

lists the shell's directory, not the  OS directory.  

So it seems - theoretically -  possible to me to chroot the session shell to the chosen file system. Probably you will want to include in the root of that file system some links to the rest of the machine. 

Or not...

---

### Post by Arndt on 2009-11-20
> **holiday said:**
> Chroot is a shell setting. It's used, in one of its ways, as a way of locking users out of system files so that the root of the machine is the user's home directory. Or some arbitrary harmless place.  

$ls /

lists the shell's directory, not the  OS directory.  

So it seems - theoretically -  possible to me to chroot the session shell to the chosen file system. Probably you will want to include in the root of that file system some links to the rest of the machine. 

Or not...

Calling chroot a "shell setting" seems misleading to me, but you seem clear about how it's used and its effects.

---

