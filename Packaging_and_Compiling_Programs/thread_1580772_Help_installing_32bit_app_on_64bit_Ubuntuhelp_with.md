---
title: "Help installing 32bit app on 64bit Ubuntu/help with building a chroot"
date: 2010-09-23
forum: Packaging and Compiling Programs
---

### Post by ornages on 2010-09-23
Hi!

I am trying to run chuck (audio programming language) on 64bit Ubuntu (I have 10.04 Lucid). Although chuck is inside the repositories, it doesn't work on 64bit (see here: [http://electro-music.com/forum/post-262038.html](http://electro-music.com/forum/post-262038.html)).

My next approach was to install ia32-libs. chuck still doesnt work.

My next step was to create a chroot simulating a 32bit Ubuntu. Here i got stuck. At first i followed these instructions: [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

I managed to successfully create /srv/chroot/hardy_i386. 

But when I try to list my configured roots (step 4 in the guide) i get: ```
christoph@F:/var/chroot/hardy_i386/bin$ schroot -l
W: line 88 [hardy_i386]: Deprecated key ‘run-setup-scripts’ used
I: This option will be removed in the future; please update your configuration
W: line 89 [hardy_i386]: Deprecated key ‘run-exec-scripts’ used
I: This option will be removed in the future; please update your configuration
hardy_i386
lucid
```
//NOTE: At first I got 'location' instead of 'run-exec-scripts'. I replaced 'location' with 'directory' inside the chroot.conf and now i get this new error with 'run-exec-scripts'. However this is merely a warning and cannot be the true source of my problems.

Ignoring this step of the guide and moving on to the following, I get:
```
christoph@F:~$ schroot -c hardy_i386 -u root
E: hardy_i386: Chroot not found
```
//NOTE: Also here I got the same warnings as above but I omitted them in the output message.

I then decided to follow another guide: [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Also here I could create the chroot directory successfully. But when it came to switching to the console inside chroot, I got a similar error message:
```
christoph@F:/etc/schroot$ sudo chroot /var/chroot/
chroot: cannot run command `/bin/bash': No such file or directory
```
//NOTE: I used /var/chroot/ for this one, so the path is not the problem.

Please help me, I don't know what else to try out. Maybe if someone knows a way around this which still gets a 32bit version running on 64bit Ubuntu, post this as well! My primary wish is to install chuck, not to setup a chroot. But idk how else I can install it successfully!

Thanks for your replies!

---

### Post by Yellow Pasque on 2010-09-29
Use lucid, not hardy for your chroot since you are running lucid. Be careful deleting your current chroot if you bind mounted partitions.

---

### Post by emoguitarist06 on 2010-11-06
I just tried using [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot) and I also ran into frustrations in step 4
 that I think resulted from step 3 so I also followed [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) next

**The first difference** I noticed is that BasicChroot Tutorial first tells us to use ```
sudo mkdir /var/chroot
```

**Next:** It ask us to edit schroot.conf NOT hard_i386.conf as the first tutorial suggested

Next:** ```
sudo debootstrap --variant=buildd --arch i386 lucid **/var/chroot/ http://mirror.url.com/ubuntu
``` is also different as it's using */var/chroot/* instead of */svr/chroot/* like the first turtorial
(note: I used [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/))

**Then** we setup the chroot using
```
sudo mount -o bind /proc /var/chroot/proc
sudo cp /etc/resolv.conf /var/chroot/etc/resolv.conf
```

and **Viola!** you should be able to go into your chroot using ```
sudo chroot /var/chroot
```

---

### Post by emoguitarist06 on 2010-11-06
My question is now that I have my chroot setup how I do use it?
I want to run pcsx2 which I in my personal downloads folder but how do I get my chroot to access it?

---

