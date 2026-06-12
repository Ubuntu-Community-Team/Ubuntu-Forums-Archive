---
title: "Unable to use other hard drive"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by derek89 on 2008-10-29
I recently grew tired of my windows xp.Linux and other types of os has always been a place of interest for me.After much research I found Ubuntu,I downloaded burned and installed it without a single problem.I'm loving it its an awesome operating system but i have came across one problem.When I made the decision to install Ubuntu I was a little uncertain on how things would go so to protect myself and my files I installed and old 4 and a half gig hard drive i had lying around to put Ubuntu on.I now have it installed and full but I cant and dont know how to utilize the space on my other hard drive for downloaded files and other things could someone please help me.

---

### Post by dracayr on 2008-10-29
when you connect it, it should be mounted automatically. you can find the icon on your Desktop. If it doesn't mount, is there an error message?

dracayr

---

### Post by derek89 on 2008-10-29
it is on my desktop but i dont know how to get my downloads in firefox or limewire to go there

---

### Post by rakris on 2008-10-29
Do u want to know the path?
it should be something like /media/sda<number> 

Save it there...

or check it in /etc/fstab after seeing "fdisk -l".

---

### Post by vanadium on 2008-10-29
If the drive had been connected during install, Ubuntu would have automatically included it in /etc/fstab such that it would have been mounted automatically during startup. Now, you will need to include the line manually. It is not really difficult. If you want specific help, post the output of the commands

```

sudo blkid
cat /etc/fstab

```

---

