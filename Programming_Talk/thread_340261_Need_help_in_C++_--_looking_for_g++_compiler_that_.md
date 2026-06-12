---
title: "Need help in C++ -- looking for g++ compiler that will install"
date: 2007-01-16
forum: Programming Talk
---

### Post by Ozwego on 2007-01-16
Hi I just made the jump to linux for my first second year programming class.  Doing projects in C++.  To be able to do assignments at home I need to have a 3.4.6 g++ compiler.  I haven't been able to locate one that will install correctly.

I have a cd that contains a g++ compiler, but am unable to figure out how to get it to install on my machine.  I'm running ubuntu on a Dell Dimension 8300, pentium 4, 512 ram machine.  

Any help would be much appreciated.  Thank you in advance.

---

### Post by meng on 2007-01-16
Try installing from repositories.
Enable universe repositories: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
then
sudo aptitude install g++-3.4

---

### Post by Ozwego on 2007-01-17
Thank you so much.

---

### Post by Ozwego on 2007-01-17
After I install the packages -- where is this put on my system?

Edit: I ask this because I oh so smoothly put 4.1 on instead.  And I need (3.4).

---

### Post by Engnome on 2007-01-17
Try writing the g++ and then hit tab twice (fast). Should print out g++ and then everything else that starts with g++. g++ 3.4 should be there.

Want to know where a binary is use ```
whereis command
```

---

### Post by amo-ej1 on 2007-01-17
or you can use 

```

dpkg -L package_name

```

to see what a certain packages installed

---

### Post by jblebrun on 2007-01-17
Rather than using the command g++, use the command g++-3.4

If you plan on using g++3.4 primarily, you can update the symbolic link:

```

sudo ln -sf /usr/bin/g++-3.4 /usr/bin/g++

```

The command means: make a symbolic link called g++ that points to the actual file g++-3.4. The -s means it's a symbolic link as opposed to a hard link, and the -f means to remove the existing g++. You can change it back later with:

```

sudo ln -sf /usr/bin/g++-4.1 /usr/bin/g++

```

---

### Post by Ozwego on 2007-01-17
Thanks so much again.

---

