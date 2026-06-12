---
title: "Cannot make these .sh scripts executable"
date: 2008-05-10
forum: Programming Talk
---

### Post by dryder on 2008-05-10
Hi,

I have two scripts that I want executed both manually (without Terminal) and via cron. They are:

> #/dev/sdb2
sudo mount UUID=58E86D78E86D5572 /media/hardy32-backups ntfs-3g defaults,locale=en_AU.UTF-8 0 22
and> #!/bin/sh
sudo umount /media/hardy32-backupsI have tried everything I can think of but to no avail.
1.  Are the scripts wrong, please? Er, if so - where?
2.  How can I make them executable manually and via cron without needing terminal please?

I appreciate your help.

David

---

### Post by inportb on 2008-05-10
Your first script looks incorrect. To find out how to use mount, try

```
mount --help
```

How do you know your scripts are not executable? How did you try making them executable?

---

### Post by dryder on 2008-05-10
My apologies - I posted the wrong first script.

In answer to your question - they don't mount /unmount the drive.

David

---

### Post by WW on 2008-05-10
I don't think you want to use **sudo** in your script.  Instead, the cron job should itself be root.

There are several ways to set up cron jobs.  How are you doing it?

Does your script work when you run it by hand?

---

### Post by Thanoulis on 2008-05-10
Did you make them executable? Try:
```
chmod +x <scriptname>
```

---

### Post by dryder on 2008-05-10
Hi WW and Thanoulis,

Thanks for your replies.

Yes, it is executable, no it won't execute manually. As part of fstab the mount works, though. But I have commented it out in fstab as I only want it manually & by cron.

sudo is there for the manual test - I assumed (?) using cron I would delete sudo.

David.

---

### Post by DBrocks on 2008-05-10
make sure cron is running 
```
sh /path/to/your/script.sh
```
and NOT

```
/path/to/your/script.
```

putting the "sh" before should make it work

---

### Post by dryder on 2008-05-10
Thanks DBrocks,

I will try that when I can get it to work manually.

I appreciate everybody's replies.

David

---

### Post by DBrocks on 2008-05-10
how are you trying to run the script?

---

### Post by WW on 2008-05-10
The way parameters are specified in fstab is not the same as the way they are given to the mount command.  Take a look at **man mount**.

---

### Post by dryder on 2008-05-10
The manual script uses sudo, so I click on it and select 'Run in Terminal' - without luck.

This is where I got some info about it:[http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script]("http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script")

---

### Post by dryder on 2008-05-10
Sorry, but I have read mount --help many times and just can not see the problem - even mounting by uuid.

Any suggestions would be appreciated.

David

---

### Post by WW on 2008-05-10
There is much more information in the man page.  In a terminal, enter the command **man mount**.

I don't have a device to test this on, but it looks like a mount command something like this should work:
```

mount -t ntfs-3g -U 58E86D78E86D5572 /media/hardy32-backups

```
Try it (with sudo, if necessary) in a terminal.

---

### Post by dryder on 2008-05-10
WW,

Yes! that works, thank you - as does my unmount script.

I apologise for my learning curve - in my experience reading was one thing (which I did) but doing it the proof of understanding.

Comparing our codes with the man page, I see now why my syntax (order) was wrong on all the methods I experimented with.

Please accept my gratitude, everybody, for your help - leading to more knowledge for me.
:-)
David

---

### Post by dtmilano on 2008-05-11
There's no need to reproduce your fstab line and perhaps to use sudo either, check man mount:

> 
       (ii)  When  mounting  a  file system mentioned in fstab, it suffices to
       give only the device, or only the mount point.

       (iii) Normally, only the superuser can mount  file  systems.   However,
       when  fstab  contains  the user option on a line, anybody can mount the
       corresponding system.


---

### Post by dryder on 2008-05-13
dtmilano,

Thanks - appreciate that though it is not in fstab. I had looked at mtab when it was mounted.

I did read/print the man pages and research this long before I posted - IMHO these are good tools but can be confusing, sometimes.

The explanations given here help in understanding the facts - if that makes sense ? :-)

---

