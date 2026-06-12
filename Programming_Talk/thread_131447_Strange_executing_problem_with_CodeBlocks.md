---
title: "Strange executing problem with Code::Blocks"
date: 2006-02-16
forum: Programming Talk
---

### Post by dee.dw on 2006-02-16
Hello,

I use the latest CB-Version for Ubuntu Breezer from [here](http://forums.codeblocks.org/index.php/topic,1194.0.html). Further I use the wxWidgets 2.4 headers and libraries instead of 2.6 because there are several changes in this version and I do not have the time to rewrite my code.

The standard "hello world"-example is no problem in compiling and executing. No I try to run my code (written with wxWidgets 2.4.2 under Windows). It compiles very well with
> Linking executable: /home/dee/home/test/fr/fr
Process terminated with status 0 (0 minutes, 27 seconds)
0 errors, 0 warningsBut if I select "run" I only get
> Checking for existence: /home/dee/home/test/fr/fr
Executing: "/home/dee/home/test/fr/fr"  (in .)
Process terminated with status 1 (0 minutes, 0 seconds)
0 errors, 0 warnings
The output is not very helpful... I don't even know where to start searching! :(

I tried kdevelop and it compiles, links and executes fine.

Thanks for any help,
Dee

---

### Post by dee.dw on 2006-02-16
It takes some time but I finally found my (?) mistake: I have created the whole project on a fat32-partition and I don't know why but C::B can not execute files from there.

The rights for the executable are> -rwxr-xr-x   1 dee dee 19472 2006-02-16 20:58 testBut I only get the error:
> dee@dexus:~/home/test$ ./test
bash: ./test: No rightsDid anyone knows where I did something wrong?

Edit:
Ah, I have the solution... I've (or better Unbuntu has) mounted the partition with the "user" option which implies "noexec", so even if I have the rights to execute something I'm not allowed to. I have changed this and add the "exec" option in my "fstab" and know everything works fine. :)

Greetings, Dee

---

