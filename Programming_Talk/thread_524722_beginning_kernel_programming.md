---
title: "beginning kernel programming"
date: 2007-08-13
forum: Programming Talk
---

### Post by u04f061 on 2007-08-13
i want to start kernel programming. the contents of my /usr/src directory are> linux-headers-2.6.20-15  linux-headers-2.6.20-15-generic  rpm


i read from the book that i need to compile the Linux Kernel for this.
do i need this?

please tell me how to compile and run hello world  program for kernel.
assuming my helloworld.c is in home directory. please also tell me how to create a makefile for it. i am using gcc 4.1 and i am using kubuntu 7.04

---

### Post by aks44 on 2007-08-13
> **u04f061 said:**
> please tell me how to compile and run hello world  program for kernel

:shock: You sure don't wan't to mess with the kernel sources... What you want to do is to learn programming. :roll:

I won't advise you to begin with C or C++, maybe Python would suit you better. Others on this board will give you good starters for sure.

---

### Post by CptPicard on 2007-08-13
What kind of kernel programming are you planning on doing? Hacking the kernel proper or writing modules? If the latter, no, you shouldn't need to recompile a kernel, in the former case, yes... and if you need this answered, I am not sure why you are looking into kernel programming. May I ask what part of the kernel are you interested in working on?

I suspect that with a "hello world program" you mean something like printing into the kernel log, which happens by using the printk function. Look it up. Creating a trivial module that does nothing but calls printk should be easy from a googled example for a programmer who is realistically considering kernel programming. Again, you're in over your head if you don't find the concept "hello world program" to be a bit odd in the context of kernel programming.

Also, I am disturbed by the fact that you don't know how to use make, and are asking about kernel hacking... :p

---

### Post by u04f061 on 2007-08-13
thanks for replying. i want Linux modules programming. actually i wanna learn device driver programming. i have the book "Linux Device Drivers" which is about kernel 2.6. i am talking about the program which is given below.
> 
#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");
static int hello_init(void)
{
     printk(KERN_ALERT "Hello, world\n");
     return 0;
}
static void hello_exit(void)
{
     printk(KERN_ALERT "Goodbye, cruel world\n");
}
module_init(hello_init);
module_exit(hell


i am a java programmer and i do know bit about c language.
he is compiling with Makefile. i am using gcc 4.0. please tell me how to write Makfile for this sample program.
i hope now it would be clear for you.
thanks once again for replying

---

### Post by u04f061 on 2007-08-13
> Also, I am disturbed by the fact that you don't know how to use make, and are asking about kernel hacking

yes i don't know how to use make. actually i thought that that the book i have will be listing all the things for writing first kernel program. that was my mistake. i think if i can get a sample Makefile for my first program , i can use it for the rest of my programs by editing its target names.

i would expect a good response from you now. please mention any other thing which you can't understand in my post.

---

### Post by aks44 on 2007-08-13
> **u04f061 said:**
> thanks for replying. i want Linux modules programming. actually i wanna learn device driver programming.
[...]
i am a java programmer and i do know bit about c language.

Sorry if I sounded a bit harsh then... from your question I really thought you were one of those clueless newbies.

I guess I was wrong, you have my apologies.

---

### Post by daou on 2007-08-13
A Makefile for 2.6 kernel modules + some instructions:

[http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)

---

### Post by u04f061 on 2007-08-13
> **aks44 said:**
> Sorry if I sounded a bit harsh then... from your question I really thought you were one of those clueless newbies.

I guess I was wrong, you have my apologies.

never mind. it is fine.

---

### Post by CptPicard on 2007-08-13
Sorry too, I guess I've become suspicious after reading enough of grand n00b attempts at writing the next crazy OS in BASIC.. ;)

We've read the same book. This is the very example I had in mind when I referred to using printk in module.

The makefile example you got is, IMO, a bit confusing as it seems to refer to some particular module implementation's source, and it's not going to help you get to grips with make per se. Here, Google Is Your Friend... first of all, to get to grips with how make works in general, google for "make tutorial" (you want to understand the concepts of targets and dependencies), and then googling for "kernel module makefile" brings up as the first result the [specifics for writing makefiles for kernel modules]("http://www.faqs.org/docs/kernel/x204.html").

To cut the crap out of that example too, the stuff you want are the INCLUDE and CFLAGS variables. The ${TARGET}.o: ${TARGET}.c is where the beef is -- it compiles your "TARGET" (in the example, hello-1) c source into the object file.

---

### Post by daou on 2007-08-13
> **CptPicard said:**
> ... and then googling for "kernel module makefile" brings up as the first result the [specifics for writing makefiles for kernel modules]("http://www.faqs.org/docs/kernel/x204.html").
...

The link describes writing makefiles for 2.4 kernels. As I've understood, the method for compiling modules has changed quite a bit as of 2.6. Feel free to correct me on this, but the example I linked, I have used extensively and successfully as a skeleton for compiling 2.6 kernel modules.

---

### Post by CptPicard on 2007-08-13
Ok, I'm not contesting that if you say so. It just seems to me the example you're using needlessly(?) builds stuff straight into the kernel modules system path... but then again, I have never actually coded kernel modules, my knowledge on this is purely on theoretical basis :P I'd rather keep his examples to a minimum, see...

---

### Post by daou on 2007-08-13
If you are referring to the KDIR, it's required. The /lib/modules/(inset kernel version here)/build is a symbolic link the kernel source directory. Just a more portable way of writing it. And that is necessary for building kernel modules.

But I'm no expert, so I wouldn't be surprised if I was wrong.

---

### Post by Note360 on 2007-08-13
Just to wrap up the noob talk. I am probably far from a noob (far from advanced though), but I don't know to much about make either (mainly bc C is not my main language and I havent had much need for it yet). So rating some ones noobyness on 1) Lack of knowledge of Make or 2) Lack of knowledge of the kernel. Is kinda bad bc those are some of the most advanced parts of programming in general (not make really though)

---

### Post by pmasiar on 2007-08-13
"99 bottles of beer" as C kernel module: [just FYI](http://99-bottles-of-beer.net/language-c-820.html) - so you know what it is gonig to be from now on :-) Good luck!

---

### Post by csimons on 2007-08-13
Not to get too off-topic, but have any of you guys worked through the Novell "Linux Kernel Development" book, or any of the O'REILLY kernel books?  Any recommendations?

I feel like I am in the same position as a lot of people.  I've been through a couple years of college (no longer enrolled), and had introductory classes in computer science and written small programs to exemplify algorithms and data structures.  I'm comfortable looking at large amounts of code, using revision-control and debugging software, and turning business specs into reality.  I'm an administrator for a database application, and regularly write PL/SQL functions and routines and fairly-complex interactive SQL reports at work.  Although I've done a basic "Hello World" program in NASM and understand how memory addressing works, I've never yet gotten the opportunity to do any real low-level or systems programming, and I'd like to know how to get started.  I love problem solving and debugging, and I'd love to eventually do low-level programming for a living.  Should I shell out some cash and take a Computer Architecture/Organization class?  Is it worth it, or is there any way I could break into the field on my own?

I feel like I'm comfortable enough with programming and could learn the specific libraries and whatnot for whatever environment I'd be working in, but I feel green enough that I'm not sure I could really take care of business if I got hired for such a job.  For those who already work in this area, what would be an ideal way to get started in the field, or to work on projects that could give me valuable experience without me putting a corporation out training me?

---

### Post by AlexThomson_NZ on 2007-08-13
// Post deleted by me

---

### Post by u04f061 on 2007-08-13
> A Makefile for 2.6 kernel modules + some instructions:

[http://www.captain.at/programming/kernel-2.6/](http://www.captain.at/programming/kernel-2.6/)

thanks daou.
you are the person who first gave me positive response and i got confidence from your reply and your response by my private message to you. i worked the example given there in the link you provided. it worked well by your Makefile given there. my program also compiled with that makefile. i am thankful to you as well as others who provided  valuable information to me.  

> Just to wrap up the noob talk. I am probably far from a noob (far from advanced though), but I don't know to much about make either (mainly bc C is not my main language and I havent had much need for it yet). So rating some ones noobyness on 1) Lack of knowledge of Make or 2) Lack of knowledge of the kernel. Is kinda bad bc those are some of the most advanced parts of programming in general (not make really though)

i would quote Bill Gates from his book "The Road Ahead"
> A panhandler in Seattle told me to check out his Web site. I thought, Boy, this is really getting popular! Maybe it was only a line, but I was impressed enough to give him what he wanted

---

### Post by u04f061 on 2007-08-13
> Although I've done a basic "Hello World" program in NASM and understand how memory addressing works, that is good. however as far as i think, if you are learning programming for hardware interfacing, then you should go to assembly or c and if you want to develop desktop applications, than don't dive into them, use a high level object oriented programming language like C++ , Python and Java. however most open source lovers don't use Java because it is not opensource. however i use Java. but the choice is yours. you can search at Google with Java vs C++ , Java vs Python ,C++ vs Python. you will get an idea about the good and bad features of these languages.
> I love problem solving and debugging, and I'd love to eventually do low-level programming for a living
nice, try yourself by playing with microcontrollers, programming with assembly or c, and enjoy.
programming is fun. I am an electrical engineer but i think I am adicted to programming.

---

### Post by u04f061 on 2007-08-13
> "99 bottles of beer" as C kernel module: just FYI - so you know what it is gonig to be from now on  Good luck!
that does not works with my system. i only have kernel header files and i hav'nt compiled kernel. do i need to compile kernel for that song?

---

### Post by fct on 2007-08-14
> **u04f061 said:**
> that does not works with my system. i only have kernel header files and i hav'nt compiled kernel. do i need to compile kernel for that song?

I haven't checked the source code of that module, but unless you really need to touch the kernel code (driver programming, bug fixing, changes in internal functions...) all you need to make modules work is the kernel headers installed, plus the compiler.

I can give you an example of compiling a module I'm working on, called **visual.c**:

This is the *Makefile*:

```
obj-m := visual.o
```

And I compile it with this command:

```
make -C /usr/src/linux-`uname -r` SUBDIRS=$PWD modules
```

in your case, you might have to change /usr/src/linux-`uname -r` for /usr/src/linux-headers-2.6.20-16-generic (depending on the version you're using).

Also consider the possibility some change in the kernel source code or the modules build system makes the example not work, so you might have to do some homework to fix it. For example, modules for the 2.4 kernel series won't compile in the 2.6 ones without changes in the source code and build.

P.S.: And never forget to attach the error message to your posts if you want to get help beyond random guessing.

---

