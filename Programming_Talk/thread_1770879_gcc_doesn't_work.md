---
title: "gcc doesn't work?"
date: 2011-05-29
forum: Programming Talk
---

### Post by gufide on 2011-05-29
when I try to build my project, I got:
```
checking for g++... g++
checking whether the C++ compiler works... no
configure: error: in `/home/master/prog/test_opengl/Debug':
configure: error: C++ compiler cannot create executables
```

I'm in anjuta IDE, I got build essentials installed, and gcc too...

---

### Post by muteXe on 2011-05-29
It's looking for g++?

---

### Post by Zugzwang on 2011-05-30
The golden rule of using an IDE (at least, when using Linux): when having problem, try to see if things work when not using the IDE.

1. Try to get a more meaningful error message. Try out (in some subdirectory of /home/master/prog/ to be sure) what is written in [this post]("http://ubuntuforums.org/showpost.php?p=10856183&postcount=16"). Does it work? If not, copy & paste the exact error message here.

2. One possibility for your error message is that you are trying to compile in a directory that is mounted in a way such that the executable bit of a file cannot be set. One example is working on a FAT/NTFS formatted disk, which do not have this bit.

---

### Post by MadCow108 on 2011-05-30
look in the config.log for the error message.

---

### Post by SeijiSensei on 2011-05-30
Permissions problem in the target directory perhaps?

---

### Post by Petrolea on 2011-05-30
> **gufide said:**
> when I try to build my project, I got:
```
checking for g++... g++
checking whether the C++ compiler works... no
configure: error: in `/home/master/prog/test_opengl/Debug':
configure: error: C++ compiler cannot create executables
```

I'm in anjuta IDE, I got build essentials installed, and gcc too...

Try manually and see if error still occurs. If it doesn't work, check whether the final directory is protected from writing.
If nothing works with g++ in any directory (not even a simplest Hello World program) that means it could be a g++ problem.

---

### Post by gufide on 2011-05-30
The configure file work only on terminal, and the error don’t occur on the terminal only. No idea?

---

### Post by MadCow108 on 2011-05-30
yes, look in the config.log and see what the real error is.
before you post that its mostly guessing.

---

### Post by Zugzwang on 2011-05-31
> **gufide said:**
> The configure file work only on terminal, and the error don’t occur on the terminal only. No idea?

Huh? There were three posts containing helpful ideas in this thread. Why don't you see if any of them helps?

---

