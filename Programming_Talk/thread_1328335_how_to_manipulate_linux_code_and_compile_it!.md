---
title: "how to manipulate linux code and compile it!"
date: 2009-11-16
forum: Programming Talk
---

### Post by moosavi.amir on 2009-11-16
hi all:D
i wanna know how to customize my own linux! how to compile it's source code and how to change it! i am tired of searching on the net, its all about compiling a program on linux from source code!
please help me!
thank u!!!:popcorn:

---

### Post by 0cton on 2009-11-16
IF you really knew how to write and understand code you would have already known how to compile as well.

---

### Post by Zugzwang on 2009-11-16
> **moosavi.amir said:**
> hi all:D
i wanna know how to customize my own linux! how to compile it's source code and how to change it! i am tired of searching on the net, its all about compiling a program on linux from source code!


That's because what you call "Linux" basically is a collection of libraries, programs and the kernel (and its drivers). Therefore there is no thing like a source code for Linux.

---

### Post by moosavi.amir on 2009-11-16
thanks for your quic reply! but would you please tell me what to do? i dont know anything about it! i need a reference! thanks again!

---

### Post by benj1 on 2009-11-16
learn C

---

### Post by julianb on 2009-11-16
I recommend you pick something more specific you'd like to work on.

For example, if you feel like there's something you'd like to change about how the interface for the program "Aptitude" works when you type "sudo aptitude" in the command line, someone could help you learn to do that.

Or if you wanted to change the program "Synaptic" maybe someone could help with that, too!

---

### Post by moosavi.amir on 2009-11-16
> **benj1 said:**
> learn C

thanks friend but i learned it before! but i cant understand where to start!

---

### Post by moosavi.amir on 2009-11-16
> **julianb said:**
> I recommend you pick something more specific you'd like to work on.

For example, if you feel like there's something you'd like to change about how the interface for the program "Aptitude" works when you type "sudo aptitude" in the command line, someone could help you learn to do that.

Or if you wanted to change the program "Synaptic" maybe someone could help with that, too!

you know! i wanna understand how does it work and delete some parts that i dont need and compile it! for example i dont want to have usb port at all or somthing...
thanks dude!!!

---

### Post by Zugzwang on 2009-11-16
> **moosavi.amir said:**
> you know! i wanna understand how does it work and delete some parts that i dont need and compile it! for example i dont want to have usb port at all or somthing...
thanks dude!!!

Oh, in that case use google for finding information on compiling a custom kernel in Ubuntu. There's already a built-in system for getting rid of unneeded kernel modules. Note that understanding how the kernel works is a heavy-weight task. It has millions of code lines. There are however books on this topic you want to get the high-level view.

In general, there is no clear answer to your problem: Each library and program has its own structure, on which the "right" way to modify it depends. So if you want to modify some part of Linux, you will need to look into the structure of the individual component you are interested in. For getting an overview of the components, read some general Linux book from your local (university?) library (or buy one).

---

### Post by scorp123 on 2009-11-16
> **moosavi.amir said:**
> for example i dont want to have usb port at all or somthing... 

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

These instructions were written with an older Ubuntu release (6.10 "Edgy") in mind, but they should still work up and until Ubuntu 9.04 .... Not so sure about Ubuntu 9.10 though, it seems a few kernel packages changed their names there ... 

But you should start from there.

---

### Post by realzippy on 2009-11-16
Hm.A gentoo stage 1 installation is the right thing for you:

[http://www.gentoo.org/](http://www.gentoo.org/)

---

### Post by moosavi.amir on 2009-11-16
> **Zugzwang said:**
> Oh, in that case use google for finding information on compiling a custom kernel in Ubuntu. There's already a built-in system for getting rid of unneeded kernel modules.

In general, there is no clear answer to your problem: Each library and program has its own structure, on which the "right" way to modify it depends. So if you want to modify some part of Linux, you will need to look into the structure of the individual component you are interested in. For getting an overview of the components, read some general Linux book from your local (university?) library (or buy one).

thanks buddy! do you know any specific book that is useful for me? im totally mixed up!

---

### Post by moosavi.amir on 2009-11-16
let me explain what i'm thinking about! im working on an opencv project and i wanna run it without any OS! I just wanna have my own OS. I want to turn on my pc and the program runs it self! a linux with just what it needs!  you guys got that?

---

### Post by xxsa on 2009-11-16
One idea could be to get sources for some basic command like 'time' and build that (sudo apt-get source time).

---

### Post by moosavi.amir on 2009-11-16
> **xxsa said:**
> One idea could be to get sources for some basic command like 'time' and build that (sudo apt-get source time).

excuse me! what are u talking about?:o

---

### Post by Zugzwang on 2009-11-16
> **moosavi.amir said:**
> thanks buddy! do you know any specific book that is useful for me? im totally mixed up!

I don't know as I never read such a book. For the kernel stuff, you might want to have a look into "Linux Kernel Development". But I don't know if it helps you, so use a library that has it.

For an overview about the components of a modern GNU/Linux distribution, I don't know any book.

---

### Post by benj1 on 2009-11-16
> **moosavi.amir said:**
> let me explain what i'm thinking about! im working on an opencv project and i wanna run it without any OS! I just wanna have my own OS. I want to turn on my pc and the program runs it self! a linux with just what it needs!  you guys got that?

well you will still need some kind of os, why don't you use the ubuntu alternate install or something like tiny core. any thing further than that would be distro building or os coding

---

### Post by Simian Man on 2009-11-16
> **moosavi.amir said:**
> thanks friend but i learned it before! but i cant understand where to start!

I'm sorry to tell you this, but you absolutely do not know C.  If you knew C in any real way, you'd understand first off how to compile things and secondly that any serious C program is a very complex beast that can't be just manipulated in the care-free way you seem to imagine.

If you are serious about learning to program, I'd suggest you slow way down.  Programming is hard work and you are not going to be able to "modify linux code and compile it" in any meaningful way within a year.  Buy a book and start slow by learning to write your own programs.

---

### Post by Zugzwang on 2009-11-16
> **Simian Man said:**
> 
If you are serious about learning to program, I'd suggest you slow way down.  Programming is hard work and you are not going to be able to "modify linux code and compile it" in any meaningful way within a year.  Buy a book and start slow by learning to write your own programs.

Actually, it seems to me that this is not even necessary, now that the OP revealed his/her real intention: 

Modifying the boot-up procedure of a distribution such that the login window is not presented but instead a single program is run (probably in conjunction with the X server) as a restricted user and access to other stuff (like the USB subsystem) is restricted doesn't require a single line of code, just some knowledge about the boot-up procedure, rights management, which components are needed and probably a little bit of scripting.

Only the "opencv" application that needs to be run has to be programmed, but this can be done in the usual way.

---

### Post by moosavi.amir on 2009-11-16
> **benj1 said:**
> well you will still need some kind of os, why don't you use the ubuntu alternate install or something like tiny core. any thing further than that would be distro building or os coding

yes your right! but how? where to start? would you please give me a reference?

---

### Post by Zugzwang on 2009-11-16
> **moosavi.amir said:**
> excuse me! what are u talking about?:o

This is basically an answer to the question on "where to get started". The poster suggested that you start with tweaking some terminal utility ("time") such that you can get your hands on modifying existing code.

---

### Post by benj1 on 2009-11-16
> **moosavi.amir said:**
> yes your right! but how? where to start? would you please give me a reference?

its just a case of finding a distro that satisfies your dependencies and setting your app to autostart when you boot.

---

### Post by moosavi.amir on 2009-11-16
ok guys!!! its really nice of u! but i confused! this is my questions:
1- how to make a small version of linux that does not contain any other part that i dont need.
2- how to run my opencv project on it.
(thank u guys! your really cool!)

---

### Post by CptPicard on 2009-11-16
> **moosavi.amir said:**
> 
1- how to make a small version of linux that does not contain any other part that i dont need.

Do you really *need* something genuinely stripped down?

Why not a small Gentoo or Debian install with unneccessary stuff uninstalled?

> 
2- how to run my opencv project on it.

Depends on how you want to run it on it. Find out how to run stuff on Linux in general :)

---

### Post by benj1 on 2009-11-16
> **moosavi.amir said:**
> ok guys!!! its really nice of u! but i confused! this is my questions:
1- how to make a small version of linux that does not contain any other part that i dont need.
2- how to run my opencv project on it.
(thank u guys! your really cool!)

if you really want to make your own version of linux [http://www.linuxfromscratch.org/lfs/view/stable/]("http://www.linuxfromscratch.org/lfs/view/stable/")
once youve done that, you should know how to run your project on it.

---

### Post by moosavi.amir on 2009-11-16
> **benj1 said:**
> if you really want to make your own version of linux [http://www.linuxfromscratch.org/lfs/view/stable/](http://www.linuxfromscratch.org/lfs/view/stable/)
once youve done that, you should know how to run your project on it.
you know, i dont wanna make an OS! i just wanna have an OS that can run my program and it doesnt contain any thing more! is it possible to compile a kernel in the way i want or it crash? does it need all the classes that is in source folder or we can delete a section and compile other sections?

---

### Post by CptPicard on 2009-11-16
> **moosavi.amir said:**
> is it possible to compile a kernel in the way i want or it crash?

Yes, it is possible. Google for some documentation about how to compile your own kernel. Instructions for that are all over the place.

---

### Post by moosavi.amir on 2009-11-16
> **CptPicard said:**
> Yes, it is possible. Google for some documentation about how to compile your own kernel. Instructions for that are all over the place.

ok, thanks a lot man! ill work on it and if i had a question ill ask! thank u all!:popcorn:

---

### Post by Simian Man on 2009-11-16
> **moosavi.amir said:**
> you know, i dont wanna make an OS! i just wanna have an OS that can run my program and it doesnt contain any thing more! is it possible to compile a kernel in the way i want or it crash? does it need all the classes that is in source folder or we can delete a section and compile other sections?

Why?  Who is going to be using your program and what does it do?  The reason we developed operating systems in the first place is to run more than one program ya know :).

---

### Post by benj1 on 2009-11-16
> **moosavi.amir said:**
> you know, i dont wanna make an OS! i just wanna have an OS that can run my program and it doesnt contain any thing more! is it possible to compile a kernel in the way i want or it crash? does it need all the classes that is in source folder or we can delete a section and compile other sections?

what exactly are you wanting?
you will probably require more than just the kernel to run your program, you will essentially be making an os, albeit a highly specialised and limited one.

you seem to be under estimating what you are trying to do. by far the easiest solution would be to find an extremely barebones distro and work from there.

---

### Post by moosavi.amir on 2009-11-16
> **Simian Man said:**
> Why? Who is going to be using your program and what does it do? The reason we developed operating systems in the first place is to run more than one program ya know :).

my program should work in a pc witch has no output way! nothing! military stuff... you know........

---

### Post by Simian Man on 2009-11-16
> **moosavi.amir said:**
> my program should work in a pc witch has no output way! nothing! military stuff... you know........

Which military are you working with?  I want to be sure to never visit that country.

---

### Post by moosavi.amir on 2009-11-16
> **Simian Man said:**
> Which military are you working with?  I want to be sure to never visit that country.
we all work together for our country and it doesnt matter how! it's our way! all for peace not war! i respect americans because peoples are respectable where ever! but it seems you dont! never mind, good luck!
thank you again!

---

### Post by CptPicard on 2009-11-16
I suspect he is just afraid of this computer vision system running on some dangerous equipment near him... ;)

---

### Post by WitchCraft on 2009-11-17
What you want is "Linux from scratch". Google for it, it has a complete documentation for how to compile an entire LSB Linux distro.

You might also want to have a look at [www.kernel.org](www.kernel.org), to get the latest Linux kernel.

I basically have my personal version here:
[http://ubuntuforums.org/showthread.php?p=7295561](http://ubuntuforums.org/showthread.php?p=7295561)

Then, if you want a minimal Linux distro, try Damn Small Linux.
50 Megabytes are as good as it can get.
Or maybe you should try to get to the sources of Debian-Netinstall.

To modify login procedures for the gnome environment, you have to modify gnome-session and gnome-settings.

```

apt-get source gnome-session
apt-get build-dep gnome-session

```

You have to be at the linux command line to replace those daemons:
```

/etc/init.d/gdm stop

```

Also note that the command line has a login procedure of its own.
If you need to edit sourcecode on the command line, you will need an easy to use text editor, such as nano.
You can configure nano to have mouse support on the command line, just install gpm and modify nanorc.
You'll also need syntax highlighting. So I suggest you use emacs instead of nano.

The boot manager of Linux is grub (legacy), or newly grub2.
So IF you want to modify the bootup procedure, you've to apt-get source grub2.

Also important is to compile gcc yourself, because IF a really sophisticated backdoor is installed, as I am sure there is, it is, apart from the kernel, most likely to be in the compiler itself, so you won't see it when you check the sourcecode...

Also note that although Linux is under the GPL, some programs (and they maybe parts of the core-utils) specifically prohibit military use.
See here: [http://slashdot.org/article.pl?sid=06/08/14/1850219](http://slashdot.org/article.pl?sid=06/08/14/1850219)
It will be illegal to sell military devices which make use of such components.


I must admit, compiling Linux from scratch is a mamoth taks, which will take days, especially with 3rd world equipment.
And with a lack in programming and even basic Linux knowlegde, and without the ability to search google, and with most people not inclined to hep you respectively your military, I wish you good luck, because you'll need it.

---

### Post by realzippy on 2009-11-17
Weird.
Which military has to look out in ubuntuforums for help?
Salvation army?

---

### Post by dwhitney67 on 2009-11-17
> **moosavi.amir said:**
> you know! i wanna understand how does it work and delete some parts that i dont need and compile it! for example i dont want to have usb port at all or somthing...
thanks dude!!!

If you do not want USB support on your system, the easiest way to prevent its use is to blacklist the driver.  I believe the driver is 'usb_storage'.

Thus something like this *should* work (but I don't promise anything):
```

sudo echo usb_storage > /etc/modprobe.d/blacklist-usb.conf

```
Then reboot your system.

The other alternative to to re-configure the kernel on your system so that the drivers are not built.  The basics on doing this are:
```

$ cd /lib/modules/`uname -r`/build

$ sudo su

# make mrproper

# make menuconfig

# make && make modules_install

```
You would add or subtract functionality from the kernel when running the 'make menuconfig'.

After the build is complete, then you need to move the resulting kernel image and related file(s) to /boot/grub, update menu.lst, etc.

Here's more detailed instructions that you can follow:
[Rebuilding Ubuntu Kerne]("https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way")l

---

### Post by Zugzwang on 2009-11-17
> **realzippy said:**
> Weird.
Which military has to look out in ubuntuforums for help?
Salvation army?

None. Looks more like a student project with applications in the military domain.

BTW: A computing system without *any* kind of output or whatsoever is quite unlikely to produce any result. ;-)

---

### Post by ajackson on 2009-11-17
> **Zugzwang said:**
> None. Looks more like a student project with applications in the military domain.
Delusions of grandeur sounds more likely.

> **Zugzwang said:**
> BTW: A computing system without *any* kind of output or whatsoever is quite unlikely to produce any result. ;-)
Very true, the computer has to do something with what it gets otherwise it isn't even as useful as a dustbin.

---

### Post by CptPicard on 2009-11-17
Well, if it has no I/O it's not necessarily useless, but very nearly Haskell... :)

---

### Post by moosavi.amir on 2009-11-17
Ok all! thanks for your time! but in many countries there is a web site or some thing that military or some other organizations put their projects definition and pay for it!  who can do this? we will pay for it x$! and every on can participate! stuff like [www.darpa.com]("http://www.darpa.com")(Defense Advanced Research Projects Agency) in america! i work and get my money! i hate to become an army slave! i work free. now would you stop talking about that!;) anyway... thank you from your answers!

---

### Post by WitchCraft on 2009-11-18
> **CptPicard said:**
> Well, if it has no I/O it's not necessarily useless, but very nearly Haskell... :)

:lolflag: at that. The finding of the year.

---

### Post by WitchCraft on 2009-11-18
> **moosavi.amir said:**
> Ok all! thanks for your time! but in many countries there is a web site or some thing that military or some other organizations put their projects definition and pay for it!  who can do this? we will pay for it x$! and every on can participate! stuff like [www.darpa.com]("http://www.darpa.com")(Defense Advanced Research Projects Agency) in america! i work and get my money! i hate to become an army slave! i work free. now would you stop talking about that!;) anyway... thank you from your answers!

most likely, you mean Darpa.org

---

### Post by moosavi.amir on 2009-11-19
> **WitchCraft said:**
> most likely, you mean Darpa.org

Sorry! i mean [http://www.darpa.mil/](http://www.darpa.mil/) !!!

---

### Post by tbastian on 2009-11-19
if you want to run one and only one process, I'm told that you can get a free version of dos. This is handy because its not a batch OS. Its mainly used for real time stuff.

---

### Post by benj1 on 2009-11-19
> **tbastian said:**
> if you want to run one and only one process, I'm told that you can get a free version of dos. This is handy because its not a batch OS. Its mainly used for real time stuff.

A free DOS, what do they call it ? 


</straight face>

---

### Post by WitchCraft on 2009-11-20
> **benj1 said:**
> A free DOS, what do they call it ? 


</straight face>

FreeDOS.

Free **D**irty **O**perating **S**ystem. :D
or 
Free **D**enial **O**f **S**ervice. :D

---

### Post by Aayu on 2009-11-20
If you want to modify Linux to create your own version and know nothing about programming, system architecture, the Linux kernel itself or even how to modify and compile code without completely f'ing the whole process.. may I suggest you brush up on those subjects BEFORE tackling this?
 
Don't run, before you can walk.. or crawl.. or make gaa gaa noises ;)

---

### Post by WitchCraft on 2009-11-20
> **Aayu said:**
> If you want to modify Linux to create your own version and know nothing about programming, system architecture, the Linux kernel itself or even how to modify and compile code without completely f'ing the whole process.. may I suggest you brush up on those subjects BEFORE tackling this?
 
Don't run, before you can walk.. or crawl.. or make gaa gaa noises ;)

Well, it's not forbidden to try, and you'll never make it unless you try time and again. You just don't have to be disappointed if it doesn't work even after you invested hours.

---

### Post by moosavi.amir on 2009-11-21
> **Aayu said:**
> If you want to modify Linux to create your own version and know nothing about programming, system architecture, the Linux kernel itself or even how to modify and compile code without completely f'ing the whole process.. may I suggest you brush up on those subjects BEFORE tackling this?
 
Don't run, before you can walk.. or crawl.. or make gaa gaa noises ;)

you know dude... thats the way i allways do! i think about what i want and then try over and over and over and finally........ thats the way it is;) anyway, thanks for your comment!

---

