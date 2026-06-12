---
title: "mounting problem"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by boblemur on 2008-08-04
hey all, im wondering if their is any way i can force ntfs drives to be -o force by default??

because i have an external hard drive... and it has about 10 partitions on it... and all of them keep getting locked (by windows) so i need to find a way that i can make them force mount...

thanks in advance..

---

### Post by ajgreeny on 2008-08-04
Are they locked in windows, as you put it, because you don't use the "Remove safely" option in the windows system tray?  That is usually what stops external drives mounting in ubuntu.  If that is not the case, I don't know what else to suggest, nor do I know of any way to get the drive and its partitions to force mount automatically.

---

### Post by oedha on 2008-08-04
did you shutdown your windows properly ?
or just like what ajgreeny told you

---

### Post by boblemur on 2008-08-04
yes even occasionally when i have shutdown properly they still lock... also i have the 10 partitions so its hard to safely remove all 10 of them.... and id rarther not shut down the computer every time i want to move it...

but i was more wondering if i could make it force mount by default... because its rather annoying having to go and manually force mount each one of them...

---

### Post by Living2007 on 2008-08-04
> **boblemur said:**
> yes even occasionally when i have shutdown properly they still lock... also i have the 10 partitions so its hard to safely remove all 10 of them.... and id rarther not shut down the computer every time i want to move it...

but i was more wondering if i could make it force mount by default... because its rather annoying having to go and manually force mount each one of them...
Because it is a removable disk. you will get the lock ups. Little USB drives aren't a problem, but External Hard Drives are different. The hold more data, and store information like it is built apart of the computer. Mounting at login will not be a solution!

---

### Post by bpowell2005 on 2008-08-04
Yes, you can add the "Force" option to your FSTAB...that's what I've done.

/dev/sda1       /mnt/win_c      ntfs-3g force 0 0

Now, this assumes the drive is always present...if you're using an external drive that you connect on the fly, then that's not covered in fstab, and I'm not 100% sure how to make "force" the default.

---

