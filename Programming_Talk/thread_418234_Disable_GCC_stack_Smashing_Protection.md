---
title: "Disable GCC stack Smashing Protection"
date: 2007-04-22
forum: Programming Talk
---

### Post by Stuart_Young on 2007-04-22
Okay, this is a strange one...

One of the modules I am studying at University requires me to test code designed to be vulnerable to stack smashing.

Therefore I would like to know if it is possible to disable the protection?

I am not very Linux literate and only installed Feisty yesterday, so details may be required

Thanks in advance

---

### Post by duff on 2007-04-22
I'm sure you've already looked at the gcc man page for such an option, and couldn't find one.  So you can install an older version of gcc, before the stack smashing protection was introduced.

```
# sudo apt-get install gcc-3.3
```

Then just compile your code with the command "gcc-3.3" instead of plain ol' "gcc".

---

### Post by wgrant on 2007-04-22
> **Stuart_Young said:**
> Okay, this is a strange one...

One of the modules I am studying at University requires me to test code designed to be vulnerable to stack smashing.

Therefore I would like to know if it is possible to disable the protection?

I am not very Linux literate and only installed Feisty yesterday, so details may be required

Thanks in advance

Just add -fno-stack-protector to the gcc command line.

---

### Post by sriram.venkataramani on 2007-11-17
Hi,

I am using gcc 4.1.3 in Gutsy. Using -fno-stack-protector in gcc gives an error that is not a valid option. I checked the help pages of gcc and I'm not able to find the -fno-stack-protector option. My guess is that the compile option has been removed. Can someone confirm that for me? 

Is there any way to disable the stack protector other than using an older version of it? Thanks!

- Sri

---

### Post by volanin on 2007-11-17
```
$ man gcc

[...][I]
-fstack-protector
           Emit extra code to check for buffer overflows, such as stack smash&#8208;
           ing attacks.  This is done by adding a guard variable to functions
           with vulnerable objects.  This includes functions that call alloca,
           and functions with buffers larger than 8 bytes.  The guards are
           initialized when a function is entered and then checked when the
           function exits.  If a guard check fails, an error message is
           printed and the program exits.

           NOTE: In Ubuntu 6.10 and 7.04 this option is enabled by default for
           C, C++, ObjC, ObjC++.
[/I][...]
```

```
$ gcc --version

*gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)*
```

This is the gcc that comes with Gutsy.
Fujitsu is right: To disable the default stack-protector behaviour, just add **-fno-stack-protector** to the gcc options.
I just tried this here, and it is working ok.

---

### Post by sriram.venkataramani on 2007-11-17
you're right - it works. i had some issues with modifying my Makefile. Thanks!

---

### Post by Maky001 on 2009-04-27
Hi to all of you.

Have a bit of problem and maybe someone give me help.
I use Ubuntu 7.04 and have a prob with one program
that from time to time just stop and dissapear from
proceses and make crashlog where i can see that SSP
stopped him.
I am not author of that program and cant change anything in it
and just wanted to know is there a way maybe to disable
stack Smashing Protection or is problem in program itself how it is written.

I have found some infos about " just add -fno-stack-protector to the gcc options to disable "
but i didnt quite understand where excatly should that and how.

So please i am just begginer so if any of you can help me
i would be thankful for any help.

---

### Post by sriram.venkataramani on 2009-04-27
You would put this option in the Makefile so that when gcc compiles your code it does not include the stack protection. 

Hope this helps.

---

### Post by Zugzwang on 2009-04-28
> **Maky001 said:**
> 
I am not author of that program and cant change anything in it
and just wanted to know is there a way maybe to disable
stack Smashing Protection or is problem in program itself how it is written.


You need to have the source code of the program in order to do so. Also, disabling the protection is unlikely to make your program more robust as then it is then likely to crash or show unexpected behaviour if a stack smash occurs.

---

