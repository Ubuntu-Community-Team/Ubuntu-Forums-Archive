---
title: "Deleting two other partitions on the hard drive."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-10-21
Hey, i've decided to give Vista the final flick after numerous blue screens - it looks like i'll be vmware'ing. I was just wondering, how to do i about deleting partitions in Ubuntu... and then creating ext3 partitions? and mounting them permanently?

Thanks in advance,
Kris

---

### Post by wolfen69 on 2008-10-21
gparted.

---

### Post by Dev'olution on 2008-10-21
Do I create a new primary partition?

---

### Post by ilrudie on 2008-10-22
Primary is fine as long as you have fewer than 4 per disk.

Not sure if you meant you'd be running vista in a vm but you should be careful.  I think running anything less than ultimate edition retail (not OEM) in a vm is illegal and running windows media player (10,11? whatever one comes with vista) in a vm is also illegal even if you are running a legal version of vista.  This was the case when vista was released but it may have changed.  Just a word of caution.

---

### Post by Ducatiboy Stu on 2008-10-22
Are you going to have Ubuntu as the only OS on the machine...

If so, then Ubuntu should just install over the top of whatever you have on the HD ( deleting everything )and use the all of the HD for itself with only 1 small swap partition...

You could use GParted first to delete partitions, but the LiveCD will do it for you

Virtbox is a good thing, I use it for XP, even the com & ethernet ports work

---

### Post by Dev'olution on 2008-10-24
Ok, i'm vmwaring xp, but the annoying thing is that i can't **permanently** mount the new ext3 partion. How do u do that?

---

### Post by b0b138 on 2008-10-24
create a folder somewhere, in /media is probably a good place. "sudo mkdir /media/newfoldername

then run "sudo gedit /etc/fstab" and add "/dev/sdxx /media/newfoldername ext3 defaults,errors=remount-ro 0 1" to it.

then run the command "sudo mount -a" This will mount everything listed in fstab.

---

### Post by Dev'olution on 2008-10-24
Will this remain the same when i boot the computer up the next time tho?

---

### Post by b0b138 on 2008-10-24
yes :)

---

### Post by rustutzman on 2008-10-24
To make it boot the same every time you'll have to use the label or UUID in fstab.

Russ

---

### Post by b0b138 on 2008-10-24
Why do you have to use the UUID?

---

### Post by Dev'olution on 2008-10-24
Ok the only issue i have now is that i cant copy anything onto the new drive. Is this because I have to chmod it?

---

### Post by b0b138 on 2008-10-24
[http://ubuntuforums.org/showthread.php?t=130898](http://ubuntuforums.org/showthread.php?t=130898)

---

