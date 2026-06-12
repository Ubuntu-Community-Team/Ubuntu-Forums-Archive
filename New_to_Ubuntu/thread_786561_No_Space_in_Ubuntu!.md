---
title: "No Space in Ubuntu?!"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Dragonlaw on 2008-05-08
I restarted my computer and when I logged into my account I realised that there was something wrong when firefox does not have my bookmarks.

And the bigger problem is that it says that I have no disk space in Ubuntu!

I was reading around but I have not been able to solve the problem, although I have ideas.

I typed "sudo du -hc --max-depth=1" And I got this:
[B]
668K	./var
4.0K	./srv
5.2M	./bin
0	./sys
13M	./etc
4.0K	./initrd
2.1G	./usr
274M	./lib
du: cannot access `./proc/7202/task/7202/fd/3': No such file or directory
du: cannot access `./proc/7202/task/7202/fdinfo/3': No such file or directory
du: cannot access `./proc/7202/fd/3': No such file or directory
du: cannot access `./proc/7202/fdinfo/3': No such file or directory
0	./proc
51G	./home
35M	./boot
104K	./tmp
6.7M	./sbin
87M	./opt
16K	./lost+found
203M	./root
8.0K	./media
112K	./dev
4.0K	./mnt
54G	.
54G	total[/B]

What do I do? I know that I have to clear the 51G in home. But I don't know how to?

---

### Post by warbread on 2008-05-08
Can you account for that 51 gigs?  I mean, is it your music collection, or is the amount of data there a surprise to you?  If it is, I would make sure your trash is empty.

---

### Post by Dragonlaw on 2008-05-08
Yea I can. Suddenly there is space! I don't know what I did with it but now I got another problem.

I posted the link there alerady.

[http://ubuntuforums.org/showthread.php?t=786572](http://ubuntuforums.org/showthread.php?t=786572)

---

### Post by oliviacond on 2008-05-08
do you put /home at another partition?

or try fsck your disk.

---

