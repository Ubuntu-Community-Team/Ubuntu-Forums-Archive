---
title: "ubuntu source code question"
date: 2005-10-04
forum: Programming Talk
---

### Post by jatos on 2005-10-04
Hello
I want to edit some of the ubuntu source code for my own purposes, but I have only found the source on cd, yet I only want a tiny fraction of the source, is there anywhere where I can get just a small amount of the source code as appossed to entire CD of it?
Jamie

---

### Post by LordHunter317 on 2005-10-04
You can download it via apt-get if you have a proper deb-src line in your /etc/apt/sources.list (which Ubuntu includes by default).  Just say sudo apt-get source package.

It's a one time download to whatever directory you're in, so make sure it's where you want it.

---

### Post by toojays on 2005-10-04
You don't need to be root to download source packages (as long as you are in a directory you can write to as a user), so you can leave off the "sudo" part.

---

### Post by SSTwinrova on 2005-10-04
Sounds like if you don't want the CD, then you don't have Ubuntu installed (or else you'd have/need the disc). If that's the case, try looking here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by UbuWu on 2005-10-04
[QUOTE=SSTwinrova]Sounds like if you don't want the CD, then you don't have Ubuntu installed (or else you'd have/need the disc). If that's the case, try looking here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)[/QUOTE]

The source is not on the installation disc. In fact you can only get cd's with the source on special request.

---

### Post by fsshl on 2005-10-07
for example I read insmod.c which used in 5.10
---------------------------------------------------------------------
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/mman.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <errno.h>
#include <asm/unistd.h>

#include "backwards_compat.c"

#define streq(a,b) (strcmp((a),(b)) == 0)

extern long init_module(void *, unsigned long, const char *);

static void print_usage(const char *progname)
{
	fprintf(stderr, "Usage: %s filename [args]\n", progname);
	exit(1);
}

/* We use error numbers in a loose translation... */
static const char *moderror(int err)
{
----------------------------------------------------------------------------------------
------------only font segment of whole porgram------------------------------
------------------------------------------------------------------------------------------

my question about searching source code are
(1) where is the .c or .c++ source code of these include .h files, like unistd.h, fcntl.h, errno.h  (usualy is orig.tar.gz or tar.gz, I search the whole content of tarball of build-essential can not find them)?
(2)  I know there .h file usually in /usr/include/
  but how do I find the source code of the function used in the porgram, like        moderror()?
  
  looking for any linux porgramming advancer's help, and thanks in advance
fsshl

---

### Post by toojays on 2005-10-07
I think what you are trying to ask is "where is the source code for the standard C library?". Get the source for libc.

Here is one way to find out where the source code relating to a particular header file is like this:

1) Find package which includes header file, e.g. "dpkg -S /usr/include/stdlib.h" shows that stdlib.h is from libc6-dev. 

2) Remove "-dev" from the name you got in part 1. This leaves you with "libc6", and that is where the functions in stdlib.h are from.

3) Once you have the name, just "apt-get source libc6" to get the source. It should be in there somewhere ;)

For understanding massive sources, some good tools to learn how to use are etags (comes with Emacs, use M-. to find function definitions) and cscope (either use it within Emacs, or get the cbrowse viewer).

---

### Post by fsshl on 2005-10-07
[QUOTE=toojays]

1) Find package which includes header file, e.g. "dpkg -S /usr/include/stdlib.h" shows that stdlib.h is from libc6-dev. 

2) Remove "-dev" from the name you got in part 1. This leaves you with "libc6", and that is where the functions in stdlib.h are from.

.[/QUOTE]
[COLOR="RoyalBlue"]Thanks your reply, it improve my knowledge a lot, [/COLOR]

---

### Post by fsshl on 2005-10-07
but even I got  libc5 , linux-kernel-headers, gcc-3.4, gcc-4.0
I still can not find where is source code of moderror in the insmod.c

please help
fsshl(in 5.10-2.6.12-9)

---

### Post by toojays on 2005-10-08
I don't get it . . . you quoted the top part of it in a previous message, where you put some of the source from insmod.c. This is the whole thing:```

/* We use error numbers in a loose translation... */
static const char *moderror(int err)
{
        switch (err) {
        case ENOEXEC:
                return "Invalid module format";
        case ENOENT:
                return "Unknown symbol in module";
        case ESRCH:
                return "Module has wrong symbol version";
        case EINVAL:
                return "Invalid parameters";
        default:
                return strerror(err);
        }
}

```Am I misunderstanding something?

---

### Post by fsshl on 2005-10-08
thanks your reply first.

yes, so it looks like it was defined there
but when
ret = init_module(file, len, options);
	if (ret != 0) {
		fprintf(stderr, "insmod: error inserting '%s': %li %s\n",
			filename, ret, moderror(errno));
called it, where is errno defined?

will make sended pamameter err as one of the switch cases
    (1)ENOEXEC or (2) ENOENT, etc?

I find this
#define	ENOEXEC		 8	/* Exec format error */
in 
linux-kernel-headers-2.6.11.2/include/linux/errno.h
(is this file be called and used by insmod.c? or other file that ENOEXEC be defined and used in insmod.c?)
but no matter "ENOEXEC" or "8" , all can not explain where it can from to make disaster in insmod.c.

  like to see anyone fully understand insmod.c source code and capable to modify it.

---

### Post by jerome bettis on 2005-10-08
i would really like to know what you're doing

it sounds like you're wasting your time and whatever it is you're trying here can be done in a much easier way - or you're sweeping a misconfiguration problem under the rug by hacking the source code instead of fixing it.

---

### Post by fsshl on 2005-10-08
thanks your reply first,

I like to modify insmod.c so when I am execute
insmod spca5xx.ko
is not response "Invalid module format" error
my 5.10(2.6.12-9 kernel seem compiled by gcc3.4) my spca5xx.ko was compiled by gcc4.0.2

  so I like to know where is source producing that error, so far I need to know how ENOEXEC be assigned in insmod.c(that cause "Invalid module format")

  have any good idea?

---

### Post by toojays on 2005-10-08
Okay, Jerome is right. What you are trying to do is really wrong. What you should do is compile your kernel module with gcc-3.4, instead of trying to hack insmod, which will not solve your problem. You can install gcc-3.4 on your system without removing gcc-4, and just use gcc-3.4 for kernel modules.

In answer to your other question, errno is a global variable which is part of standard C. See the man page errno(3) for more information.

---

### Post by az on 2005-10-08
[QUOTE=fsshl]thanks your reply first,

I like to modify insmod.c so when I am execute
insmod spca5xx.ko
is not response "Invalid module format" error
my 5.10(2.6.12-9 kernel seem compiled by gcc3.4) my spca5xx.ko was compiled by gcc4.0.2

  so I like to know where is source producing that error, so far I need to know how ENOEXEC be assigned in insmod.c(that cause "Invalid module format")

  have any good idea?[/QUOTE]


But spca5xx is already in the Breezy kernel.

---

