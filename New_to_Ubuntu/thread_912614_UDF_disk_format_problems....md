---
title: "UDF disk format problems..."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Mike_SMD on 2008-09-06
Hey everyone,
First off let's be clear that I'm a newbie.

If you are posting advice or help it has to be even more basic than you already think it does. One little bit of shorthand that 'everybody' knows and I'm immediately lost.

That set aside, I just got married and folks are sending me wedding pictures... they all use Vista and I can't get any of the disks to load in Ubuntu. The UDF file format just doesn't seem to work.

Now, I've tried manually editing the fstab by setting it to auto and changing the order around and deleting lines altogether... basically everything that has been posted up here on the forums to no avail. Doing some more Googling I came upon this fellow's solution;

[http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/](http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/)

But I'm stuck.
Once I get to the point where I'm supposed to add the patch ($ patch -l ../vista-patch) my terminal just seems to hang. Get stuck. Does this kind of thing usually take hours to run...? Or have I done something wrong? Just what PRECISELY has been omitted in the dot-dot part of "../vista-patch" anyway...? Do I have to point this 'patch' someplace for it to work...?

The author says to troubleshoot here if there are problems, but heck... I'm so utterly ignorant in these affairs that I can't even recognize whether there actually IS a problem here or not.

Has anyone else tried this method...?

Man, I am SO frustrated right now!

Any help would be greatly appreciated!

Thanks,

Mike_SMD

---

### Post by Irihapeti on 2008-09-07
Yes, the method does work. I tried it just now. I have a UDF DVD that I created with Vista (and had almost given up on) and I can now read it in Ubuntu. Thank you.

The two dots is just shorthand for the parent directory - that is, the directory that "src" is inside of. If you have followed the instructions as given, it should work as is. I think that if that were the problem, you'd get a message along the lines of "file not found" or "no such file or directory". However, just to check, this is what you should see in your terminal just before you enter that command.

~/root/udf-vista/udf-filesystem-2.5/src$ 

That means you are in the right directory.

Adding a patch of that size takes only a second or so, which suggests that something has gone wrong with the patch itself. 

I have to say that I don't know a lot about patches. Perhaps you didn't copy all of the text - I noticed when I visited the patch webpage that the text extends well beyond the right-hand edge of the frame. You could try copying and saving it again and then rerunning the command.

Did you remove the first line from the file? I.e.

```
diff -Nur linux-2.6.24-udf/fs/udf/super.c linux-2.6.24-udf-akw/fs/udf/super.c
```

If that were still in the file, it might cause some problems.

Beyond this, I don't know what else to suggest. Maybe a more knowledgeable individual can help out.

Irihapeti

---

