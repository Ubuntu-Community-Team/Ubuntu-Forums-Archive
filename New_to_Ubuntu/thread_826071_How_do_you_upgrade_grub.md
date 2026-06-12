---
title: "How do you upgrade grub?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by wil313 on 2008-06-11
I recently used the update manager to up grade to Hardy, but towards the end it started to give a bunch of error messages and it did not make it around to the clean up stage, so at this point I'm not sure what is going on with my computer. Also I did some research on how to speed up Ubuntu, and found that on grub they were able to type profile at the end, but all I can do is select which kernel I wanted to boot from... I know the kernel was updated, but I'm not sure that grub was updated... Suggestions?:confused:

---

### Post by sdennie on 2008-06-11
You should be able to make grub update its generated kernel list with:

```

sudo update-grub

```

---

### Post by wil313 on 2008-06-11
Thanks, that took care of that, but what was the clean up process supposed to do?

---

### Post by sdennie on 2008-06-11
I think that's to remove the Gutsy kernels if you were upgrading from Gutsy.  Not doing that is not really an issue because it just means that you'll have extra grub menu items.  Though, I'm not sure if the cleanup part does anything else so, it may eventually cause problems (it may not though, it's hard to say).

---

### Post by wil313 on 2008-06-11
Is there away to remove the other kernel?

---

### Post by sdennie on 2008-06-11
Yes.

First, run:

```

dpkg -l | grep linux-image

```

Make *SURE* you have at least one linux-image-2.6.24 version of the kernel.

Then

```

uname -r

```

And make sure that it's a 2.6.24 version you are currently running so you know it's safe to remove the older versions.

Finally:

```

sudo apt-get remove linux-image-2.6.22*

```

I have no way to try that but, it should be safe.  Alternatively, you can just leave the old kernels.  Other than occupying a little disk space, they aren't causing you any other problems.

---

### Post by wil313 on 2008-06-11
Thanks for the help! :)

---

### Post by wil313 on 2008-06-11
Problem, I ran the last code and it deleted both kernels, how do you reinstall the kernel from the Edubuntu cd without installing everything else? I have the cd in recovery mode, but I don't know the code...

---

### Post by sdennie on 2008-06-11
That's not good.  But, it should be fairly easy to fix.  Completely boot into the live CD and then go to Applications->Accessories->Terminal.  Once in the terminal type:

(Note: This assumes that the partition Ubuntu is installed on is /dev/sda1.  It may be another partition like /dev/sda2, etc).

```

sudo mkdir /mnt/old
sudo mount /dev/sda1 /mnt/old
sudo chroot /mnt/old
sudo apt-get install linux-image-generic linux-restricted-modules-generic

```

Now you should be able to reboot and things should be fine.

---

