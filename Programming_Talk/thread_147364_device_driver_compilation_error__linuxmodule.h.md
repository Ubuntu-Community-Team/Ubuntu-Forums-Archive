---
title: "device driver compilation error : /linux/module.h"
date: 2006-03-20
forum: Programming Talk
---

### Post by paulipe on 2006-03-20
Hi,
I have written my own device driver which only prints one line both during insmod and rmmod (just as an exercise for more complicated things). I have been facing a lot of compilation issues for the same.
First of I had done the following

```
paulipe@paulipe:~/kernel$ gcc -c hello.c
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from hello.c:2:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from hello.c:2:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from hello.c:2:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
paulipe@paulipe:~/kernel$

```

After looking around a lot i managed to solve half the problem by downloading sanitized headers [http://ep09.pld-linux.org/~mmazur/linux-libc-headers/]("http://ep09.pld-linux.org/~mmazur/linux-libc-headers/") and including them in my path.

Now I am stuck at the following place.

```
paulipe@paulipe:~/kernel$ gcc -I ../temp/linux-libc-headers-2.6.12.0/include/ -c hello.c
In file included from ../temp/linux-libc-headers-2.6.12.0/include/linux/sched.h:16,
                 from ../temp/linux-libc-headers-2.6.12.0/include/linux/module.h:9,
                 from hello.c:2:
../temp/linux-libc-headers-2.6.12.0/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from ../temp/linux-libc-headers-2.6.12.0/include/linux/sched.h:79,
                 from ../temp/linux-libc-headers-2.6.12.0/include/linux/module.h:9,
                 from hello.c:2:
../temp/linux-libc-headers-2.6.12.0/include/linux/resource.h:2:2: warning: #warning "You should include <sys/resource.h>. This time I will do it for you."
In file included from hello.c:2:
../temp/linux-libc-headers-2.6.12.0/include/linux/module.h:41: error: field ‘attr’ has incomplete type
../temp/linux-libc-headers-2.6.12.0/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
paulipe@paulipe:~/kernel$
```

Can anybody help me out? I had tried substituting all types of various linux/module.h files to see if any of them worked but to no avail.

This is the hello.c file that I had written (got it of the net).

```
#define MODULE
#include <linux/module.h>

int init_module (void)
{
	printk("Hello Kernel\n");
	return 0;
}

void cleanup_module (void)
{
	printk("Goodbye Kernel\n");
}
```

Any help would be appreciated. Thanks

---

### Post by toojays on 2006-03-20
If the build doesn't have access to the kernel config that was used, all kinds of strange compile problems can happen. I suggest you have a look at some kernel module which lives outside the tree (bcm43xx springs to mind) and see what their makefile does.

---

### Post by paulipe on 2006-03-20
I just got a reply from Mariusz Mazur that the sanitized headers were not to be used for kernel programs/modules (i should have figured it out but i was just happy with cutting a few errors). Further i looked at the bcm43xx and none of the source files include linux/module.h so the way they are compiling it doesnt really matter either.
I am trying to look for other drivers that might include it but if anyone can help with my original problem which is to get the device driver module to compile on a breezy5.10 setup it would really help.
I had even tried using the kernel linux-headers and gcc-3.4 in all sorts of combinations but to no avail
thanks

ok i was just re-editting my post and thought i would try out a new combination and it works!!:)
awesome
i think it is absolutely necessary to pass the -D__KERNEL__ argument. I'm surprised it wasn't working before. I'm not sure why. Anyway the exact command is below
```
paulipe@paulipe:~/kernel$ gcc -c -Wall -D__KERNEL__ -DMODULE -I /usr/src/linux-headers-2.6.12-10-386/include/ hello.c
paulipe@paulipe:~/kernel$

```

So if any of you guys want to start of on writing kernel modules too you know how to compile atleast:)

insmod doesnt seem to be inserting the module. I might post that in another thread.

---

### Post by virgoptrex on 2008-09-28
Ok I am a beginner too. But I solved this problem. Used Ubuntu Hardy Heron 2.6.24.19 to build my own kernel 2.6.24.7-custom

Solution for this problem Build a kernel yourself and make sure you set the load/unload kernel in 'config' file in the following tutorial: 

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

just replace 2.6.18.1 in the above tutorial everywhere by whatever kernel you would like. In my case I did 2.6.24.7

next after installing the kernel

follow the instructions below

if you have not set password for super user already then follow this otherwise go to the next step
-----------------
sudo passwd root
-----------------
type your password twice and "REMEMBER IT"
----------------------
su -
---------------------
Type the password
now your prompt should change to root
verify this by
----
pwd
----
now you need to port your "hello.c" file here

if you know the path/directory where this is situated do the following
e.g if its on your Desktop
----------
cp /home/xxxx/Desktop /root
----------

If you can't do this create hello.c. 

-----------
nano hello.c
-----------

(you can also use vi editor if you are comfortable with it)
open this copy and paste driver code above and Don't forget to save it before exiting

----------
nano Makefile
----------

Type in the following
-----------------------
obj-m += hello.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
-------------------------
the command (shell uname -r) will automatically find kernel version for you

next save it and close it

then type
----
make
----

to see what types of files are created
------
ls -al
------
you should see file 'hello.o', 'hello.ko' etc
if everything goes well then you should see a prompt promptly without pc being freezing :)
now insert module
------
insmod ./hello.ko
------

The module should insert successfully if everything was done as per procedure

then you must unload the module

----
rmmod hello
----

To see the messages "hello world" and "goodbye world" or whatever you had
type
------
cat /var/log/messages
-----------

Thats it!!! It should give you a headstart!!!

Follow the tutorial

[http://en.tldp.org/LDP/lkmpg/2.6/html/index.html](http://en.tldp.org/LDP/lkmpg/2.6/html/index.html)
Thanks to "gizmo","AlexOoO" and many others on the internet for their helpful posts!!!
----------------------------------------------------
Don't create problems. CREATE SOLUTIONS!!!

---

