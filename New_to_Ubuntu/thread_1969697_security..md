---
title: "security."
date: 2012-04-30
forum: New to Ubuntu
---

### Post by sabre1467 on 2012-04-30
i have just used windows installer to install ubunto allongside windows. first time of using it and it looks nice and simple. do i need seperate security software or is it covered by the software i use for windows.

---

### Post by ubuntu27 on 2012-04-30
You most likely dont need any additional software for security.

If you want to learn more about security in Ubuntu, [see this thread]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by xedi on 2012-04-30
> **sabre1467 said:**
> i have just used windows installer to install ubunto allongside windows. first time of using it and it looks nice and simple. do i need seperate security software or is it covered by the software i use for windows.

What ubuntu27 said but I want to add that the security software on Windows does not cover your Ubuntu installation. I'm no expert on WUBI (the windows installer thingy) but my understanding is that even that virtual partition which is created within Windows is not accessible to Windows, so you have to see both operating systems as separate (With some exceptions like that Ubuntu is capable of seeing Windows' file system but not vice versa)

This does not mean, however, that you need to install any further security software on Ubuntu as an average user. A default Ubuntu install combined with smart and safe behavior should should be enough.

---

### Post by ubuntu27 on 2012-04-30
Oh. I missed that he used WUbi to install Ubuntu in Windows partition.

I just want to tell you that Ubuntu wubi is not as stable as the real deal (with a proper installation on its own partition).
The Ubuntu wubi install will have the same stability as the host OS/partition. 

So, let´s say that your NTFS partition is fragmented, and thus your Windows OS becomes slow. This will impact Ubuntu as well. 


On the other hand, if ubuntu was installed on its own partition with ext4 file-system or others, it wont have problem with fragmentation.


I just gave you one example. Ubuntu wubi is mostly used for preview. If you like what you see so far, and you are ready to jump to Ubuntu Linux. I recommend you to install it on its own partition.

And if you have any questions, don hesitate to ask on this forum. :)

GOod luck!

[Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/")

---

### Post by lisati on 2012-04-30
As others have said, if something goes wrong with your Windows installation, it *can* impact on your Ubuntu installation if you used Wubi to install it. Having said that, the best security process begins with being smart. 

You might find the [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") thread in the forum's [security sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=338") a good place to start.

---

