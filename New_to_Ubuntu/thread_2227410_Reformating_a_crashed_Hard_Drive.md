---
title: "Reformating a crashed Hard Drive"
date: 2014-06-01
forum: New to Ubuntu
---

### Post by jorden3 on 2014-06-01
So I am trying to fix my friend's computer. It was running windows 7 buyt womn't make it past the BIOS screen. I am trying to reformat the hard drive using the ubuntu disk. It froze twice during the installation process and now the computer is saying that there isnt enough space available to install Ubuntu. Any suggestions? I am currrently running Ubuntu from the disk on the computer.

---

### Post by Mark Phelps on 2014-06-01
A "crashed" drive physically will not work, which does not sound like your problem.

Did you try to install Ubuntu using the "entire disk" selection?   Freezing during installation is an indication of possible sector damage -- which will prevent Ubuntu from working, just like it will prevent Win7 from running.

If booting from the Ubuntu disk and trying to reformat the drive using GParted does not work, then it's time to consider trying to recover individual files and/or folders from the drive. And, to do that with a drive previously formatted with Windows filesystem, tends to work better with Windows data recovery tools. Since the drive was originally formatted for Windows filesystem, if the filesystem is merely corrupted, there is a chance you could fix that using Windows CHKDSK.

---

### Post by Duncubuntu on 2014-06-02
Yes using something like CHKDSK will help your cause, you can also look for something you can boot up with and "zero out the drive". Essentially it does just that, completely rewrites the drive with zero's. While this may not solve your problem, it has worked for me countless times when faced with this problem with older/re-used hardware. You can get more info here: [http://dban.org/](http://dban.org/)

---

### Post by stalkingwolf on 2014-06-03
you could also use the hirens boot disk hard drive regen tool. ive saved several drives using it. it works with linux or windows .

---

