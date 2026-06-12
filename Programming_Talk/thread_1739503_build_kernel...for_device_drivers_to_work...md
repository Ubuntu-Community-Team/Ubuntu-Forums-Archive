---
title: "build kernel...for device drivers to work.."
date: 2011-04-26
forum: Programming Talk
---

### Post by rohitkbuntu on 2011-04-26
Hello all,, 

 I am very much new to linux(ubuntu, although i am a developer :(  )  and now i want to learn developing device drivers ...so i used the following tutorial to get myself started....
[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C11]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C11")
but in this article they have mentioned certain things before running the script and i am not able to make any requierments fullfil for the code....the requirements are...
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Helvetica]
[LIST=1]
[*]Install the &#8220;kernel-image-2.6.x&#8221; package.
[/LIST]
but the thing is i am not able to install/download this file....

Can any of u guys out there help me out..this seems like a small issue but it's restraining me getting started on my way.

Thanks in advance,
Rohit

P.S: i am using ubuntu 10.04
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by r-senior on 2011-04-26
You might find these instructions more flexible for what you want to do:

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

I'd checkout the 2.6.38 to start with, rather than the bleeding edge. You'll need to become familiar with GIT:

[http://www.kernel.org/pub/software/scm/git/docs/gittutorial.html](http://www.kernel.org/pub/software/scm/git/docs/gittutorial.html)

You'll also need to be confident in configuring GRUB and switching back to old kernels if your own build doesn't work.

Lots of links here too:

[https://wiki.ubuntu.com/Kernel/Dev](https://wiki.ubuntu.com/Kernel/Dev)

---

### Post by dwhitney67 on 2011-04-26
@ the OP -

You do not need to build the entire kernel if all you are interested in doing is building a device driver.  With your Ubuntu OS, you have a kernel already in place, as well as the header files.

From there, you can build yourself a driver in user-land, and then load it (using insmod) as the root-user (i.e. using sudo).

If the module works per your requirements, then you can add it to the kernel.  To build the kernel, you could following these simple steps that are documented here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

