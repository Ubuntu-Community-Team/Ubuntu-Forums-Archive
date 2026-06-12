---
title: "16 bit application"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by allarmguy on 2008-11-27
Hi all!I need to run a 16 bit application on my ubuntu machine.I need to run it on a server TVCC.The original program run only in win 98.Can I use it in ubuntu?BUT WITHOUT WINE...I need to know if ubuntu can run that app

---

### Post by Xiong Chiamiov on 2008-11-27
If it was written for Windows, you'll have to use Wine, unless you run Windows inside of a virtual machine, which just seems silly.  Is there a reason you don't want to use Wine?

---

### Post by allarmguy on 2008-11-27
I don`t want to use wine because is not working I already try it

---

### Post by flanagan on 2008-11-27
What does the application do? Most likely there is already something for Linux that does the same thing better, faster, and cheaper. There are lots of folks here who know more about available apps than I do, and I'm willing to bet they might have some suggestions.

---

### Post by allarmguy on 2008-11-27
the application is a server for a video surveillance.Allow user to see the images captured by the telecamera.It work ONLY with 98.

---

### Post by Xiong Chiamiov on 2008-11-27
If it does not work with Wine, then you cannot run it natively in Linux.  This is due to the way that code is translated into machine language, and the difference between the underlying nature of the operating systems.

If you cannot find a more updated software, then your only hope is to install Windows 98 in a virtual machine (such as VirtualBox or VMware).

---

### Post by flanagan on 2008-11-27
I would have a look through the repositories to see if anything fits your needs. There are tons of video apps there, perhaps camserv. Others who have used such apps may come back and make recommendations.

---

