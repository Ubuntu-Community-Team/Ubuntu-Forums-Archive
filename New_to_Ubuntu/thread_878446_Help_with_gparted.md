---
title: "Help with gparted"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ulster_con on 2008-08-02
> When I installed gparted, I saw that I cannot format, resize etc.....my partitions. All I can do is to Unmount, manage flags and information. What's wrong?

Secondly, it's taking to long to open the partition editor (scanning devices). Is it normal in Ubuntu 7.10 ?


hey all, sorry to be such a noob :D

i have a similar issue, wana resize the main drive, 
but i get a message can only unmount, flag or more info...

my question is, if i unmount, is this likely to lose all information?
as i want to partition a 110Gb drive, so that 30Gb can be dedicated elsewhere.. 

Con :D

---

### Post by bodhi.zazen on 2008-08-02
this thread came from tips and tutorials.

@ulster_con : FYI, as stated in the stickies in tips and tutorial, and in the post immediatly before yours, tips and tutorials are not support threads and your support request is off topic to the tutorial in which you posted. Please be aware this is not the best way to get assistance.

I moved you thread to a more appropriate area.

You should manage your partitions from a live CD. They need to be unmounted before you can resize them. Partitions can be unmounted either from the command line :```
sudo umount /dev/sdxy
```where "sdxy" is the partition to be unmounted. If it is a swap partition ```
sudo swapoff /dev/sdxy
```

Or you can do it from the gparted menu.

    Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

Please feel free to ask for further clarification if you are having continued dificulty.

---

### Post by sh4d0w808 on 2008-08-03
ulster_con, the main problem is that U cannot edit a mounted partition. If U wanna resize or delete a partition, I recommend to use gparted livecd.

If U unmount a partition, U will not loose any of that datas, only cannot access, while not mount that partition again.

---

