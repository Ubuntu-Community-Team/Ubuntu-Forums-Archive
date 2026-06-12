---
title: "Ubuntu Not Loading"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by mpenney on 2013-03-29
I have it set up with duel boot (windows) and during an update my laptop battery died.  Now when i try to start Ubuntu it wont even get me to the login prompt.....

Any suggestions on fixing this

Thanks in advance

---

### Post by PhantomTurtle on 2013-03-29
Are you at least able to get into the GRUB menu (which gives you the choices to select an operating system)? If so, you can go into Recovery mode, select "Drop to root shell prompt". After this, you can run the command,

```
sudo apt-get install -f
```
 
which will repair any broken packages.

If you cannot get into the GRUB menu, you can repair it using an Ubuntu live CD. To do this follow the instructions on the Ubuntu wiki, [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Once that is finished, you can follow the instructions above in the GRUB menu to repair any broken packages.

Hope that helps :)

-Phantom

---

