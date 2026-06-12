---
title: "Extract archive tgz file error"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by tn88test on 2013-06-17
I want to extract tgz file but I got an error: [B]Error creating directory: Permission denied

[/B]&#8203;Please help me! Thank you!

---

### Post by camurgo on 2013-06-17
**tl;dw**: prefix the command with sudo. It'll look something like this ```
sudo tar -xvf archive.tgz
```

Or, in case you were trying to extract by right-clicking the file, open the Terminal (I'll assume you know how to navigate in the to the place where your tgz file is) and use the command above instead, it does basically the same thing.

Explanation: It seems that the user you're currently logged in with doesn't have permissions to create folders in the directory where you're trying to extract your tgz file to. 
Make sure that it's ok to create files/folders where you're trying to.

---

### Post by tn88test on 2013-06-17
I'm sure I'm logged as administration because there is only one account user.
**sudo tar -xvf /home/home/Downloads/arm-linux-gcc.tgz** I enter password and it displayed like this. I couldn't find the extracted folder.


[IMG]http://s8.postimg.org/li6n3veat/ubuntu.png[/IMG]

I also tried to right click extract and the error occurred
[IMG]http://s12.postimg.org/ylefqh9bx/ubuntu1.png[/IMG]

---

### Post by MidnightGrey on 2013-06-17
Hi tn88test

> I'm sure I'm logged as administration because there is only one account user.
Even though your account is an Administrator account, it doesnt mean it has admin (or root) privileges all the time, only that it can turn on root privileges. the command **sudo** (meaning super-user do) turns on root access.
Whenever you try to do actions beyond that of a regular user, you will have to call **sudo**.

While you can disable this such that you always have root access rights, this is considered VERY UNSECURE and ill-advised.

When you called: **sudo tar -xvf /home/home/Downloads/arm-linux-gcc.tgz **it should have extracted the file to the current directory. that is the *current directory of the terminal*, not the directory the .tgz file is located in.

To designate a folder to extract to you can use this syntax: **tar -xvf <myfile>.tgz -C <target directory>**. ie:
```
 sudo tar -xvf /home/home/Downloads/arm-linux.gcc.tgz -C /home/home/Downloads
```

---

### Post by tn88test on 2013-06-17
WOW It worked perfectly! Thank you very much!

---

### Post by monkeybrain2012 on 2013-06-17
How did you get the tarball? It wouldn't need sudo just to extract it unless you downloaded it with sudo (sudo wget something something may be? usually you don't need sudo to run that) Another way is simply to change its ownership to yourself as a normal user inestead of root.

```
cd Downloads 
sudo chown yourusername arm-linux-gcc.tgz
```

Then you can extract the tarball without sudo in the terminal, or simply by right clicking it.

BTW why are you trying to install gcc from a tarball?

---

