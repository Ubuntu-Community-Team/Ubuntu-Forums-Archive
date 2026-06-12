---
title: "sudo to su"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by SeePU on 2008-09-14
Hello,
Can anyone tell me how I can convert the sudo system to a more traditional su system that is used, for e.g., in Debian or any of the other debian-based distros.  I would really appreciate it.  

I was living with sudo when I had Ubuntu going but I would like to install 8.10 Intrepid Ibex when it's released but I was hoping for an option of using the su (root user) system.  

One issue I have is when I have to do a lot of root commands at once and I have to keep typing sudo.  Or I need to do something that requires root privileges but the sudo way causes a problem/issue.  I don't have an example right now but I'm sure someone will know what I mean.  I don't care about the problems of su as I don't worry about it.  I don't forget to exit a root shell or to get out of root.  I don't worry about borking my system because I forgot I was root.  Therefore, I would like to use 'su' and that's one of my issues with Ubuntu.  

Wireless works decently in Ubunutu and although I prefer KDE, I think if I had to use sudo and no other distro met my preferences and wireless compatibility, I would use it but if I had an option to use su, it would make it that much better.

Thanks for any instructions, advice and info!

---

### Post by Mornedhel on 2008-09-14
Right, so :

sudo -i will give you all the power of sudo in interactive mode, which is almost like using traditional su, with the added benefit of the sudo model of security.

If you really need su :

sudo passwd
[type your password]
[at prompt for UNIX password, type your new root password]
[again for confirmation]

and you can now use su.

---

### Post by overdrank on 2008-09-14
Hi and you can find more on the forum policy here
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by overdrank on 2008-09-14
> **gregphil said:**
> <snip>.

Please read the link posted. Thread closed.

---

