---
title: "Newbie wants to delete an OS from the boot list"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Geemonster69 on 2012-02-02
Any help here appreciated im dual booting Linux Ubuntu 11.10 with Windows 7.
There are 2 windows 7's i want to clean up the boot list.

---

### Post by wolfen69 on 2012-02-02
Try
```
sudo update-grub
```

---

### Post by Matt__ on 2012-02-03
Try [Grub Customiser]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customiser") as detailed in this post.

---

### Post by Geemonster69 on 2012-02-20
Thanks folks will give it a try :)

---

### Post by Geemonster69 on 2012-02-22
> **wolfen69 said:**
> Try
```
sudo update-grub
```

Thanks but that just brings up my boot list i need to know which command to type in to delete the Windows 7 on /dev /sda1

---

### Post by cortman on 2012-02-22
> **Geemonster69 said:**
> Thanks but that just brings up my boot list i need to know which command to type in to delete the Windows 7 on /dev /sda1

Are you saying you want to erase Windows?

---

### Post by Geemonster69 on 2012-02-22
Yes i have Windows 7 on dev/sda1 and windows 7 on dev/sda2 and i want the sda1 one deleted as it can't find it.

---

### Post by cortman on 2012-02-22
In that case, you want to delete the partition using GParted. Then you can resize your other partitions to use the empty space, or just leave the space unallocated.

---

### Post by Geemonster69 on 2012-02-22
What happened is i was using a hacked copy of windows 7 and when i installed Ubuntu i all of a sudden had a this is not a genuine copy,so i used another windows loader to make it legit only now when i click on dev/ sda1 i get a black screen with loads of code,it basically can't find it so i have to click on Windows 7 loader on dev/sda2.
I want to remove the sda1 from the boot list just clean it up a bit you know?
I can't wait to become Ubuntu savvy...because i'll probably just drop Windoze alltogether.

---

### Post by wolfen69 on 2012-02-22
Talking about using illegal copies of software is prohibited in the forums.

---

### Post by Elfy on 2012-02-22
Indeed.

Closed.

---

