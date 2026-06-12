---
title: "Can we Recover Deleted Data??"
date: 2012-09-18
forum: New to Ubuntu
---

### Post by Mohan1289 on 2012-09-18
hey Guys

I got a doubt when my friend asked me..

Can we restore the data that is deleted accidentally by using the command 

"rm -rf"

can we restore the LOST data?

---

### Post by mips on 2012-09-18
Not easily.

You could set up an alias for rm so instead of deleting things it moves it to your trash.

[http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html](http://www.webupd8.org/2010/02/make-rm-move-files-to-trash-instead-of.html)

---

### Post by androssofer on 2012-09-18
> **Mohan1289 said:**
> hey Guys

I got a doubt when my friend asked me..

Can we restore the data that is deleted accidentally by using the command 

"rm -rf"

can we restore the LOST data?

yes. but as long as you don't add anything new to the drive. it might still be possible if you did, but its less likely.

here is a page on how to do it:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by audiomick on 2012-09-18
> **androssofer said:**
> yes. but as long as you don't add anything new to the drive. it might still be possible if you did, but its less likely.


Yes, this agrees with what I have read on the subject. I have thankfully never needed to do this, but have read a fair bit about it. It seems there are several programs that have a very good chance of getting things back. The most important thing is to stop using the drive immediately that you realise you have deleted something by mistake.

When things are deleted (this also applies to Windows and Mac), they are not removed from the drive by the deletion. It is only the index for the data that is deleted. That means the bits and bytes are still there until that area of the drive is re-used to store something else. This is why it is important to stop using the drive; to prevent the system from writing to the area that you want to recover from.

Recovery programs attempt to identify files from the raw data on the drive. Since files generally have header bits and what not to identify what type of file it is, the chances are relatively good for getting a lot, if not all, of the data back. As long as nothing has been written over the lost data.

---

### Post by Mohan1289 on 2012-09-21
Thanks for the help guys

---

### Post by Deepak A on 2012-09-21
Ofcourse we can. We can recover the deleted data or even partitions using SystemRescueCD. 

[http://space.dl.sourceforge.net/project/systemrescuecd/sysresccd-x86/3.0.0/systemrescuecd-x86-3.0.0.iso](http://space.dl.sourceforge.net/project/systemrescuecd/sysresccd-x86/3.0.0/systemrescuecd-x86-3.0.0.iso)

See the System tools available in Rescue CD

[http://www.sysresccd.org/System-tools](http://www.sysresccd.org/System-tools)

*testdisk* command will be useful while retrieving deleted data or partitions.

Now download and boot from the System Rescue CD.
:) :)

Deepak

---

### Post by Mohan1289 on 2012-09-21
Thank you Deepak

---

### Post by Deepak A on 2012-09-21
> **Mohan1289 said:**
> Thank you Deepak


You are welcome brother....

---

