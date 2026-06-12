---
title: "GTK+ question"
date: 2007-04-04
forum: Programming Talk
---

### Post by bluezapper on 2007-04-04
Hi all,

I am going to do programming in GTK+ using C programming language. I saw that there are two versions

GTK 1.2

GTK 2.0

I would like to know which version is more stable and better to use with lesser number of bugs.

thanks in advance,

bluezapper.:)

---

### Post by ndefontenay on 2007-04-04
I think you should go for the GTK 2.0 because the 1.2 is getting old.

---

### Post by lnostdal on 2007-04-04
Definitively go for 2.x.

```

sudo aptitude install gnome-core-devel build-essential

```

..should do it. Then use pkg-config (it is mentioned briefly in the GTK+ tutorial) to extract compile- and linker-flags.

---

### Post by bluezapper on 2007-04-05
Hi Inostdal,

I installed the latest GTK+ version with the command you have mentioned.It installed many libraries. Now I face some problem,

Actually I am writing gnome applications. Previously, I wrote a program which uses GTK1.2 and it used to compile perfectly. Now, I started using GTK 2.x API

For example when I use

```

G_SIGNAL_CONNECT instead of GTK_SIGNAL_CONNECT  I am getting the following errors:

/tmp/cc1KIdBt.o: In function `main':bluescangui.c:(.text+0xde): undefined reference to `G_CALLBACK'
:bluescangui.c:(.text+0xeb): undefined reference to `G_OBJECT'
:bluescangui.c:(.text+0x107): undefined reference to `g_signal_connect'
:bluescangui.c:(.text+0x113): undefined reference to `G_CALLBACK'
:bluescangui.c:(.text+0x120): undefined reference to `G_OBJECT'
:bluescangui.c:(.text+0x13c): undefined reference to `g_signal_connect'
collect2: ld returned 1 exit status

```
I am compiling using following commands. My program also uses some bluez libraries so

gcc -o bluescangui bluescangui.c -lbluetooth `gnome-config --cflags --libs gnomeui`

Can you tell me what I am doing wrong. I am not using any IDE just command line compilation and gedit.

regards and thanks in advance,

bluezapper.

---

### Post by bluezapper on 2007-04-05
ok guys solved the problem.Replacing gnome-config with pkg-config solved the problem.

gcc -o bluescangui bluescangui.c -lbluetooth `pkg-config --cflags --libs libgnomeui-2.0`

thanks,

bluezapper.

---

### Post by j_g on 2007-04-05
Don't forget the glade3 package. That's a tool to graphically create your user interface (ie, windows with menus, buttons, sliders, listboxes, etc).

---

### Post by Sluijsens on 2009-09-15
can't acces tutorial anymore, gives an 404 error:O
My question, how do I use the pkg-config?
I'm am a total noob here:P
Installed Ubunto 9.04 just 2 days ago:)

Thanks

---

### Post by dwhitney67 on 2009-09-15
> **Sluijsens said:**
> can't acces tutorial anymore, gives an 404 error:O
My question, how do I use the pkg-config?
I'm am a total noob here:P
Installed Ubunto 9.04 just 2 days ago:)

Thanks

pkg-config is executed from the shell.  The most common options used are --cflags and --libs.  Obviously one needs to specify the library package that they are interested in.

Note, not all libraries rely on the pkg-config feature; for those libraries, you will need to specify the header file path(s), if not /usr/include, and the library paths, if not /usr/lib (or /usr/local/lib), manually.

For include paths, use the GCC option -I.  For library paths, use the -L option.  Libraries are specified using the lowercase-l option, sans the "lib" and filename extension of the library.  For example:
```

g++ -I/some/include/path MyFile.cpp -L/some/lib/path -lsome -o myapp

```

---

### Post by PmDematagoda on 2009-09-15
Necromancy.

Thread closed.

---

