---
title: "Partitioning, dual boot"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Deadric on 2013-04-29
I recently shrunk my hard drive partition down (the one that contains windows 7) down by 50gb and left that space unallocated. My problem is that it wont let me re-allocate this space into the Ubuntu partition

[ATTACH=CONFIG]241964[/ATTACH]


There is no option for unmounting or moving the other partitions out of the way
And I have tried it from the live CD too

any help would be appreciated

---

### Post by oldfred on 2013-04-29
You have to use liveCD, and swap off as liveCDs often automount swap to speed things up. Click on swap and right click swap off.

You can then move left edge of extended into unallocated and move Linux partition left. I generally do not like moving left, only because it has to move all data and any interruption, power failure, etc corrupts data. So good backups are required. But it works almost all the time so we do not always make backups and that is when you accidentally kick the wrong switch. :)

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Deadric on 2013-04-29
It doesnt let me move the extended partition at all, the option for turning swap off is grayed out

---

### Post by oldfred on 2013-04-29
Are you using the liveCD? You cannot use the system you are running from.

---

### Post by Deadric on 2013-04-30
Yea, I was using the liveCD

---

### Post by Mark Phelps on 2013-04-30
That screenshot concerns me -- regarding sda3.  The utility should be able to read that partition -- but it appears it can not.

You need to boot into Win7 and run CHKDSK a couple of times to see if that clears the flag in the screenshot.

---

### Post by Deadric on 2013-04-30
Chkdsk instantly closes whenever I try use it which is annoying

---

