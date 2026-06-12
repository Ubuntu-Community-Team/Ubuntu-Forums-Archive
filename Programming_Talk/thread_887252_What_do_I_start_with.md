---
title: "What do I start with?"
date: 2008-08-11
forum: Programming Talk
---

### Post by blahbah7 on 2008-08-11
I'm lost with the things like kernel, packages, repositories, etc that you never saw in windows. I want to get into messing around with ubuntu's operating system. where would I start?

I'm guessing that someone will guide me to the Ubuntu wiki's main page, I've been there, the main page tells me nothing.  Give me a link to a useful page in the wiki (or any other site for that matter) to get me started.

---

### Post by CptPicard on 2008-08-12
By understanding the meaning of the terms you listed. :)

Essentially, the operating system is put together of the kernel, plus an assortment of system utilities plus applications.

The kernel is the core "manager program" of the whole thing. It allocates resources to applications. Every piece of the system comes from some "package", which contains the relevant piece plus dependency information (what other packages are needed) plus installation and configuration scripts.

Repositories are places on the net which contain packages. The package manager goes out to the repository and grabs the packages you need and installs them. This is a far superior way of doing things than anything you see on Windows, although it seems to be awfully confusing to beginners...

---

### Post by pmasiar on 2008-08-12
Start by reading in wikipedia what kernel is, and following all links. Get ready to spend couple years becoming C guru and learning about architecture of operating systems, I assume you are taking college classes about that?

Messing with kernel is not for sissies :-)

---

### Post by blahbah7 on 2008-08-12
> **CptPicard said:**
> By understanding the meaning of the terms you listed. :)

Essentially, the operating system is put together of the kernel, plus an assortment of system utilities plus applications.

The kernel is the core "manager program" of the whole thing. It allocates resources to applications. Every piece of the system comes from some "package", which contains the relevant piece plus dependency information (what other packages are needed) plus installation and configuration scripts.

Repositories are places on the net which contain packages. The package manager goes out to the repository and grabs the packages you need and installs them. This is a far superior way of doing things than anything you see on Windows, although it seems to be awfully confusing to beginners...

is the kernel itself made up of packages, or is it what brings all the packages together to actually do something?

@pmasiar: yeah I've got quite a few years to do that =P So I should start learning C not C++

---

### Post by pbpersson on 2008-08-12
> **blahbah7 said:**
> I'm lost with the things like kernel, packages, repositories, etc that you never saw in windows. I want to get into messing around with ubuntu's operating system. where would I start?


What exactly do you mean by "messing around"?

1.  Installing applications?
2.  Learning about system administration?
3.  Learning command line utilities?
4.  Learning how to fix things when they break?
5.  Learning how to create new applications for Linux?
6.  Learning how to fix problems inside the OS?

I am a little unclear as to exactly what journey you want to begin....

---

### Post by LaRoza on 2008-08-12
> **blahbah7 said:**
> is the kernel itself made up of packages, or is it what brings all the packages together to actually do something?

The kernel is about 22000 files of hardcore C and assembly. It is overlooked by Linus Torvald. The kernel is a file, for me it is: /boot/vmlinuz-2.6.24-19-generic

See for more on a kernel of this type: [http://en.wikipedia.org/wiki/Monolithic_kernel](http://en.wikipedia.org/wiki/Monolithic_kernel)

The kernel by itself is pretty useless, but provides the basis for every Linux distro. Many drivers and modules can be used as well.

Usually, the GNU Core Utils are also provied by GNU/Linux systems: [http://en.wikipedia.org/wiki/Coreutils](http://en.wikipedia.org/wiki/Coreutils)

(There are alternatives to them for special hardware or systems)

In addition, there is the X Window System which provies the basis for most GUI's (KDE and GNOME among many others) for Linux distros: [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

On top of that, there is the desktop environment and/or window manager (I use xmonad, which is not a desktop environment)

---

### Post by ThinkBuntu on 2008-08-12
I'd recommend learning Bash (the terminal shell) and common Linux/Unix commands. Understanding these interactions makes the OS easier to understand. You may find yourself learning a little Perl on the way. Maybe even some Python these days.

---

### Post by CptPicard on 2008-08-12
> **blahbah7 said:**
> is the kernel itself made up of packages, or is it what brings all the packages together to actually do something?

The kernel is delivered as one of the packages -- it is, if you will, the most important package of them all :) It is the job of the package manager (on Ubuntu, "apt", on RedHat, "yum", on Gentoo, "portage") to fetch the pieces and put them together. The package manager on the other hand runs as one of the application programs on top of the kernel.

> 
@pmasiar: yeah I've got quite a few years to do that =P So I should start learning C not C++

I suggest you learn about basic system structure and administration first :)

> **LaRoza said:**
> It is overlooked by Linus Torvald.

"Torvald**s**"

---

### Post by pmasiar on 2008-08-12
> **blahbah7 said:**
> is the kernel itself made up of packages, or is it what brings all the packages together to actually do something?

@pmasiar: yeah I've got quite a few years to do that =P So I should start learning C not C++

Looks like you have even more learning cut for you.

You don't program yet, right? Start with Python. C++ is way too complicated and C is more picky and less friendly.

As LaRoza said, most people do not care much about the kernel - it works, but all I care is to run my programs. It is way too complicated to understand deep details, but you have to grasp basic concepts of course.

---

### Post by ThinkBuntu on 2008-08-12
I don't thing that Scheme through SICM would be a bad choice either, while we're recommending languages. I wish I'd started there rather than JavaScript + PHP (after HTML and CSS).

---

### Post by conehead77 on 2008-08-12
Here is a picture of the kernel for you:
[http://www.makelinux.info/kernel_map.d/LKM63_2048.png](http://www.makelinux.info/kernel_map.d/LKM63_2048.png)

---

### Post by blahbah7 on 2008-08-13
> **pbpersson said:**
> What exactly do you mean by "messing around"?

1.  Installing applications?
2.  Learning about system administration?
3.  Learning command line utilities?
4.  Learning how to fix things when they break?
5.  Learning how to create new applications for Linux?
6.  Learning how to fix problems inside the OS?

I am a little unclear as to exactly what journey you want to begin....

I guess what I really want to know is how Ubuntu works.  With a better understanding of that I could get into more application building, and pretty much the whole list you just stated (well, im assuming that understanding Ubuntu will help).

---

### Post by pmasiar on 2008-08-13
> **blahbah7 said:**
> understanding Ubuntu will help).

Ubuntu is just a distro: a way to package and distribute packaged application. Start at wikipedia: [http://en.wikipedia.org/wiki/Ubuntu](http://en.wikipedia.org/wiki/Ubuntu) and follow the links :-)
You need to learn about debian (base distro), Linux the kernel, utilities and shell (bash), and some programming - depends of which language uses the project you are interested to learn deeper.

---

### Post by cespinal on 2008-08-13
> **blahbah7 said:**
> I'm lost with the things like kernel, packages, repositories, etc that you never saw in windows. I want to get into messing around with ubuntu's operating system. where would I start?

I'm guessing that someone will guide me to the Ubuntu wiki's main page, I've been there, the main page tells me nothing.  Give me a link to a useful page in the wiki (or any other site for that matter) to get me started.

> **blahbah7 said:**
> I guess what I really want to know is how Ubuntu works.  With a better understanding of that I could get into more application building, and pretty much the whole list you just stated (well, im assuming that understanding Ubuntu will help).

for me... a newbie recently turned into this world, and being COMPLETELY AWARE that linux it not by any means, windows, ubuntu works like this: 

Packages are: applications, programs, drivers, add-ons, plug-ins, etc. I mean, every extra piece of software you would like to add to your system. Magic about all this is that you can install everything you need pretty much from a single (or few) source. There is almost no need for buying cd's, downloading from sites, using torrents or P2P suites to get the software you need. 

Repositories are: the servers where the packages are stored. as simple as that! each linux distribution can have its own servers, while some other might be able to share them. 

A package manager is a program that tells you which softawe is already in your computer and which other software is available in the servers (repositories) for you to download them. The package manager also downloads, installs, and deletes existing sofware on your computer on command. Simple isnt it?. This is like going into Windows' control panel, an then on "add or remove programs" and with a few clicks you install everything you want and delete all the things you dont.

You also dont see Command Line Interfaces in Windows very commonly either, although you can open one when you click on "Run" from the start menu. In ubuntu is called terminal and it is usefull for installing/configuring things that just are not supported by windows, icons and menus (a graphical user interfase). The tricky thing about the CLI as that you dont regulary have pop up windonws warning you about the consequences of performing certain tasks, as commonly happens in Windows. So, you type 3 or 4 commands and you can break your system if you really dont know what you are doing.

There is no "Control Panel" in ubuntu, just go for "Preferences" and that's it. 

These are, to my understanding, the main "practical" differences you have to be aware of in order to start enjoying ubuntu without stumbling upon things that were expected to be there in Windows, but are apparently missing in this system :P

---

### Post by Reiger on 2008-08-13
> **cespinal said:**
> So, you type 3 or 4 commands and you can break your system if you really dont know what you are doing.

I would change that to 'if you vaguely know what you're doing' for someone who doesn't know what on earth he's doing doesn't know them dangerous commandline tools/sledgehammers.

I mean you got to know that rm delete's stuff before you accidentally type:
```

$ rm /*

```

Luckily the system will catch you in THIS case, but were you to prefix it with the command for "grant me Super Cow Powers" ... you simply had wiped everything mounted in your OS & associated files!

That in itself is a major benefit of complete unawareness of the (obscure abbreviations of) commands -- the complete and utter newbie can't break his system because he can't find the sledgehammer yet.

---

### Post by cmay on 2008-08-13
hi.
there is 3 books that was very usefull to me .
brian w kerninghan the unix programming enviroment
m.banahan & a.rutter the unix book
john r levine & margret levine young unix for dummies 
for better understanding of the linux kernel a 
book like andrew s tanenbaums operativ systems design and implementation .
 its the minix3 book that linus torvalds read and used as inspiration to write the linuxkernel.

hope it could help

---

