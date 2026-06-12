---
title: "[SOLVED] How to uninstall RealPlayer"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by shankhs on 2008-08-30
I have installed RealPlayer but I didnt like it.Now I want to uninstall it,using sudo apt-get remove --purge.
But nothing happened.
So I deleted the folder where I installed the RealPlayer.
Still no help.
Then I went to my home directory and deleted the postinst folder(this came with RealPlayer) still cant uninstall.
Is there any way to remove RealPlayer11.

---

### Post by Harisz750 on 2008-08-30
inside home folder find the realplayer folder... if it is hidden  press ctrl + h to display it. somewhere inside it should have a unistall file.  just open it and choose to run it in terminal. that should do the trick

---

### Post by drs305 on 2008-08-30
As Harisz70 said, the answer is in the .realplayer folder. If you can restore it to the location from which you deleted it (the location is in the Trash's "info" folder), do that. Then find the "postinst" subfolder and within that is the uninstall script. I believe it is called "postuninst.sh".

---

### Post by shankhs on 2008-08-30
I got it..
Thanx.

---

