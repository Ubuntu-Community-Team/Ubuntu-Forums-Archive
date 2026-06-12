---
title: "Grub restore problem"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by uppidada on 2008-11-27
1.One of my friend has xp and installed ubuntu in other partition
2.Now unfortunately he using live CD re-installed ubuntu in same partition(/ and swap).All that was fine.
3.While restarting he's getting grub but with no windows been listed after ubuntu re-installation.
4.He yet again re-installed windows in its earlier partition.
Now he's lost grub.
5.Using live cd ,i've typed as follows in terminal
          sudo grub
          find /boot/grub/stage1
            o/p: (hd0,1)   
          root (hd0,1)
          setup (hd0)
          quit
After quit we are getting msg as "There needs to be change in Bios settings and a lot of time might take to load devices ......." of such sort.
 On restarting we've lost grub and are unable to load either of OS's..
 Seems a weird problem.
 He's installed Ubuntu in C:\  and Windows in G:\     
 Plz help me.We're in great of correcting this problem..

---

### Post by uppidada on 2008-11-27
Some one please help me with this....

---

### Post by bumanie on 2008-11-27
If the output from find /boot/grub/stage1 is (hd0,1) that is what you should put at root. > sudo grub > root (hd0,1) > setup (hd0) > quitReboot and see whether that fixes it. If not please post the output of > sudo fdisk -lu from a live ubuntu cd.

---

### Post by randiroo76073 on 2008-11-27
Here's a good thread on it:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Dedoimedo on 2008-11-27
A great program for solving GRUB issues is Super Grub Disk:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I have a nice tutorial on GRUB, check my signature if you want. Or if you write grub tutorial, it's the first thing to come up on Google.

Dedoimedo

---

