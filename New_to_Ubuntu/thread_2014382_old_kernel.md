---
title: "old kernel"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by ibbill on 2012-07-01
Have a old kernel showing on boot up.Ran ubuntu tweak and sudo update-grub after it removed it. Still shows on boot up page.

 Have checked in synaptic it is not installed now.I reinstalled it and rebooted re ran ubuntu tweak and  sudo update-grub checked in  synaptic it has been removed.  Still shows on the boot up screen.

I have pinguy os , Mint Mate, XP, and Ubuntu fall back installed which is the system that shows the  old kernel number is 3.2.0.-25

I am booting up ubuntu using the 3.2.0-26    64Bit.

Would really like to get this off my  boot up page please.

---

### Post by ibbill on 2012-07-01
Just found this file can I remove the lines from sub menu down and then click save.

Yikes this is fun.Thanks

---

### Post by jmfal on 2012-07-01
You should be able to remove it or comment it out by putting # in front of t he line(s).

---

### Post by ibbill on 2012-07-01
Okay thanks very much on my way will come back and mark solved if all went well. Thanks again.

---

### Post by ibbill on 2012-07-01
yikes no luck thanks for giving it a shot tried to date grub with syntax error after removing  all that stuff lol Will live with the extra entries on boot up no big deal thanks again.

---

### Post by NikTh on 2012-07-01
Open synaptic and search for **linux-image** and **linux-headers **of version that you want to remove . 
Right click and completely remove them both. Restart .
Its another thing also.. linux mint is ubuntu based OS , maybe kernel is from linux mint.. 
Please open a terminal and write
```
cat /boot/grub/grub.cfg
```**Copy the entire out put and paste between [CODE] brackets by clicking on # at the top of the message pane.**

---

### Post by miegiel on 2012-07-01
When updating GRUB (not upgrading!), it looks in */boot/* for the available kernels. You can safely remove the old kernel files in that directory (you can recognize them by the version number in the file name) and run *sudo update-grub*. After that the old kernels won't be in the boot menu anymore. Though it's recommended to keep 1 old kernel as a fail safe.

If you want to uninstall old packages that have been upgraded run:
```
sudo apt-get autoremove
```
That will remove all old packages you no longer need. But, even though the old kernel packages will be removed, the old kernel files in */boot/* will remain (unless you delete them manually).

---

### Post by ibbill on 2012-07-02
awesome thanks ever so much. Have marked solved thanks again.

---

