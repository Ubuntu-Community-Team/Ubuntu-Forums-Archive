---
title: "Second User Issue"
date: 2007-08-14
forum: Other OS Talk
---

### Post by guguma on 2007-08-14
Hello and good days,

In short my problem is this. I want to create a new user so that he will have access to only one partition and only some environment variables that he will not break things (I will try Linux From Scratch that is why I am trying to do it). But for the purposes of speed using and entertainment, I really want this user to have access to compiz-fusion and XMMS etc... that works fine with the first user.

The problem is this new user does not even have audio driers installed. I presume that the apps and drivers(compiz, xgl, ati drivers etc..) are installed locally for the first user. How can I make things better for this user also. I do not intend to reinstall everything for this user too, let alone I did not even install audio drivers for the first one (they are given to me by almighty ubuntu).

So what should I do at least where shall I start.

By the way I used 

```

groupadd lfs
useradd -s /bin/bash -g lfs -m -k /dev/null lfs

```

to create the user. 

NOTE: Do not tell me things like "Why are you trying LFS it is not appropriate for newbies" or so because I have heard it enough already and it is a useless comment to do. I am doing it for learning purposes so that I will not be asking boring questions like this post later on. And if there is really a moderate-painful way to do this without reinstalling everything for this user also (and you know it) please do not tell me to install everything again for this user. I do not intend to do it when there exists  a more convenient way.

Thanks in advance

---

### Post by aysiu on 2007-08-14
Well, in Ubuntu, you'd add the user to the *audio* group. I'm not sure if that method would work for LFS. If no one else from here responds, you may want to try the LFS mailing lists:
[http://www.linuxfromscratch.org/mail.html](http://www.linuxfromscratch.org/mail.html)

---

