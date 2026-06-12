---
title: "Not enough hard drive space"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by Puzzleman on 2012-07-06
When transferring files to my relatively new Ubuntu 12.04 installation I receive a lack of space warning. The files stop transferring and the computer gives me the option to STOP or CONTINUE. The wording of the "error message" may not be exact; I should have written it down.

I continued on and the computer froze, popping up more messages. I finally got those to clear but Firefox and other programs would not load. I then deleted two folders which contained perhaps 12G of files. The computer then responded normally. Later I added more files without incident. But now I am getting the same messages again when I try to transfer large blocks of files.

I posted this question a day or so ago and thought the problem had gone away; it hasn't.

My hard drive is an equally partitioned 750G drive. I seriously doubt if I have more than 100G on Ubuntu side at this point. I see the "/dev/loop0" use is at 91% (with only 1.6G available) so that might be where the problem lies. The files added are all being stored as folders,  sub-folders, and files under the HOME folder.

Why do I get this message?

How do I proceed?

larry@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   15G  1.6G  91% /
udev                   1.8G  4.0K  1.8G   1% /dev
tmpfs             741M  824K  740M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  220K  1.9G   1% /run/shm
/dev/sda5       350G   52G  299G  15% /host
/dev/sda2       350G   19G  331G   6% /media/Ubuntu

Thanks for any help I get.

---

### Post by oldos2er on 2012-07-06
> **Puzzleman said:**
> 
/dev/sda5       350G   52G  299G  15% /host


I'm assuming from /host you used Wubi to install Ubuntu? If you intend to run Ubuntu for any length of time I would suggest installing it in its own partition. Wubi is limited to 30GB.

---

### Post by Puzzleman on 2012-07-06
I believe you have hit the nail squarely on the head. I did not personally do the installation. I had played with Wubi and was not aware of the difference.

Perhaps my friend who did the install was also unaware.

Thank you so much.

---

