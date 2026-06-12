---
title: "Custom kernel compile on Hardy."
date: 2008-06-08
forum: Packaging and Compiling Programs
---

### Post by redrob on 2008-06-08
Compiling custom kernels for Hardy.

I compiled the linux kernel the Ubuntu way.... using debian/rules.
I found it impossible to add extraversions on to the kernel version, and generate a package.](*,)

In the end I created a custom kernel flavor.

I used the instructions in  binary-custom.d directory, and apart from the fact that the instructions appeared out of date, it appeared to work well.

To get it working, I had to add the flavor to the following variables:
all_custom_flavours in the 0-common-var.mk file.
custom_flavours in the i386.mk file. (Note: this will vary depending on your architecture.)

So my questions are:

1. Is this a sensible way to make a custom kernel.
2. Is this future proof?
[INDENT]--How will compiling kernel change in future.[/INDENT]
3. Is the method I registered the custom flavour correct?
[INDENT]	Shouldn't the flavour auto-detect, and update the debian config files automatically?[/INDENT]
4. Where should I send feature requests/ideas for kernel compiles?
5. Why is it recommended to compile a stock kernel the debian way?
[INDENT]	Wouldn't it be better to copy the debian directory into the stock kernel tree, and run debian/rules?[/INDENT]
6. Is there any place to go to understand the difference between the Ubuntu way of kernel compiling, and debian?

Note that my main reference for kernel building was the following page:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by stari4ek on 2008-06-09
do you use 32bit or 64 bit version?

I have problems with compiling kernel on 32bit system.
Take a look at bug: [https://bugs.launchpad.net/bugs/237528](https://bugs.launchpad.net/bugs/237528)

I've tried to compile different versions, different gcc (4.2.3 & 4.3.0) - all time i get 'unresolved externals'-error.

Last kernel from kernel.org compiles without any problems.

---

