---
title: "Need help compiling Dreamcast homebrew from source."
date: 2011-11-13
forum: Packaging and Compiling Programs
---

### Post by Selim873 on 2011-11-13
Just as the title says, I got the homebrew Doom For Dreamcast which is known as the best Doom port for the console, but you have to compile it yourself.  I've barely compiled anything, so I'm pretty unfamiliar with it.  I tried following the instructions, but there's something that it says that I have to do, in which I have no idea how to do...  I already replaced my CD Drive's mount location on the makefile, and I replaced the shareware Doom iWad with my retail one in the folder specified.  Here's the output from the terminal.

```
ty@ty-Aspire-one:~$ cd Downloads/Doom
ty@ty-Aspire-one:~/Downloads/Doom$ make clean
Makefile:4: /Makefile.rules: No such file or directory
make: *** No rule to make target `/Makefile.rules'.  Stop.
ty@ty-Aspire-one:~/Downloads/Doom$ sudo su
[sudo] password for ty: 
root@ty-Aspire-one:/home/ty/Downloads/Doom# make clean
Makefile:4: /Makefile.rules: No such file or directory
make: *** No rule to make target `/Makefile.rules'.  Stop.
root@ty-Aspire-one:/home/ty/Downloads/Doom# 

```

Here's the installation section of the homebrew's readme.

```
Installation
============
Copy DCDoom.sbi into the SBI directory of SelfBoot Inducer. Run SBI,
select DCDoom, and click Extract. Then switch over to a Windows file
manager. Insider the inducer directory, copy your main WAD files into
the iwad directory, your patch WAD files into the pwad directory, and
your DeHackEd files into the deh directory. Go back to SBI and create
an disc image. If you don't have any other files, making a disc image
after extracting the SBI will allow you to play the shareware version
of Doom.

The makefile in the source now allows you to make a self-booting disc
by running "make clean", "make all", then "make selfboot". You should
know about making Dreamcast homebrew before attempting this. The CD
writer is set to /dev/cdrom by default in the makefile. If your writer
is at some other device, edit the makefile before trying this.

Building Doom from source also requires you to patch the biosfont
routines in KOS. Look for the diff file in the kos-fixes directory
in the source directory. If you can't patch and rebuild kos, you
probably shouldn't be attempting to build Doom from the source.
```

Any help will be greatly appreciated!  :)

EDIT:  I know the method for Windows users is there, but I don't have access to a Windows PC.

EDIT2:  I tried Google, I'm having a VERY difficult time finding out specifically how to do this...  :(

---

### Post by Selim873 on 2011-11-13
Bump?
I just realized that this got buried down to almost the third page already.  :(

---

### Post by oldos2er on 2011-11-13
Moved to Packaging & Compiling Programs. Please don't bump your post more than once in 24hrs.

---

