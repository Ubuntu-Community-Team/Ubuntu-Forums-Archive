---
title: "getting rid of dual booting"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by Jordiston on 2012-09-24
I wanted to set up Ubuntu on an external usb hard drive. So I did that. Got it all installed on the external drive with a boot CD, but it set it up as a dual boot on my computer. Now if I don't have my external drive plugged in I get an error on boot up so I cant even load windows.

What I wanted was to set my pc to search for a usb to boot from first, and if their was one it would boot ubuntu from it, and if it's not plugged in then boot from the internal drive (windows) as normally.

So I guess I messed up my boot settings on my internal drive. I was hoping by installing Ubuntu on the external drive it wouldn't have to change anything at all on my main one, and it never asked to in the installation, but it must have.

If anyone could help me get this to work the way I first envisioned it t00, that would be great! Also I have a laptop with windows 7 on it originally and Ubuntu 12.04.1 on my external drive. I DO NOT have a windows 7 installation disc or any kind of back up.

---

### Post by houseworkshy on 2012-09-24
I think that what is happened is that you may have put the bootloader onto the external drive instead of the hard drive.  If so you will need to move it back or reinstall it in the proper place.  This guide and links from it will show you how
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Extra, 

Reading through again I think that this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) would be a much easier way to go.  If my guess is right the tab you'd need in this tool would be the one refering to the location of the bootloader.  If not the diagnostics in this program would let you to post the information needed to get better help without you having to dive into the command line.
I see that this is your first post.  Welcome to the forums.

---

### Post by Jordiston on 2012-09-24
Thanks! Yea I don't really know how to do anything with the command terminal. So it's a good thing that boot repair program fixed everything for me lol.
I just installed it and ran it from the terminal just typing in what it said. Now my pc boots windows 7 when the external drive is disconnected and if I boot up my pc with the usb hard drive connected it gives me a choice! So pretty much what I wanted lol.
Thanks again!

---

### Post by YannBuntu on 2012-09-25
Good job :)
Please use the Thread Tools at the top of the page, to mark the thread as [SOLVED].

---

