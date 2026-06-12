---
title: "Vista/Ubuntu Dual Boot with RAID 0"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by taylorbr on 2008-05-14
Hi, I'm a complete noob, so I hope this question isn't too stupid.  I have 4 hd's, 2 250 gb and 2 500 gb both set up in RAID 0 arrays.  I have Vista installed on the 250 gb array (along with all of the programs) and am using the 500 gb array for all my documents.  I have used the shrink tool within Vista to shrink the size of the 250 gb array where I planned on installing Ubuntu at.  My goal would be to have Vista and Ubuntu installed on the 250 gb array sharing the 500 gb array for all of my files.  

Upon using the live cd it appeared that Ubuntu wasn't seeing the disks as arrays (it saw all of them separately) and it didn't look like it was going to install on the RAID 0 array, it looked like it was going to install just on one of the disks.  Is there a way to have Ubuntu "see" the arrays and install on the shrunk portion of one?  Thanks!

---

### Post by shifty_powers on 2008-05-14
heh, well tbh, i think raid 0 is a waste of time anyways, and is playing dice with your data.

as for ubuntu, [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid) will start you off.

tbh, not that well up on raid and installing ubuntu ;)

---

### Post by dstew on 2008-05-14
To install Ubuntu to a software-assisted hardware RAID (also called FakeRaid), you need to install the dmraid program, and install Ubuntu "by hand". It can be done. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

---

### Post by kansasnoob on 2008-05-14
Just the thought of FOUR hard drives blows my mind ..... but you might start here regarding RAID:

[https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)

Hardly a nOOb project!

---

### Post by yanom on 2008-05-14
Vista! Blegh. Use XP if you must use Windows. You could sell you copy of Vista to cancel out the price of XP, but I don't know if that is legal. I don't know much about software law, but I don't need to. Commercial software (especially Microsoft) Is evil.

---

### Post by taylorbr on 2008-05-14
Thanks for the replies, looks like I have some reading to do...

---

