---
title: "installing wine on an external HD"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by DCompson on 2008-08-05
Hi, 
 I'm a noob to Linux, having recently installed Ubuntu 8.04 (64 bit) to duel boot with Windows XP. However, since at this point I am still primarily using XP, I didn't make a very big partition for Ubunutu. Now this is a problem as I've installed Wine, but don't have space to try and use it to install any games. 

Is there a way to install Wine to an external hard drive? Or somehow set Wine's "C" drive to use the external drive? 

Thanks

---

### Post by Ru$$i@N on 2008-08-05
yeah there is
go to Applications > Wine > Wine configuration
click on "Drives" tab
change the field "Path" to wherever you mounted the external HD (like /media/externalhd, or browse for it)
click "Add"
Then when you install games, install them on that letter (whatever letter Wine assigned to the drive), instead of C:

-- Edit

the drive might be already auto detected for you, then it should be in the list there

---

