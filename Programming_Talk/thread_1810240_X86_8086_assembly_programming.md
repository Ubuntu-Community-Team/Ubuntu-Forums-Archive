---
title: "X86 8086 assembly programming"
date: 2011-07-22
forum: Programming Talk
---

### Post by gotatrust on 2011-07-22
I found a way to make kernal.bin load from a fat32 usb drive
im looking for a way to put a picture on the screen. i know how to change individual pixels should i start there?
how do i run a seperate file off the usb drive
how do i make the mouse work
and how do i make it know when you click
 
is there a book that answers these questions?
 
my idea is to have a development operating system that comes with compliers assembly and c. instructions on how to program good books. the kernal will be very basic comes with programs like paint and file manager. has an option for a second kernel that will run high level programming like c++ and python maybe java.
have it windowed like some linux so that you can switch between kernels.
 
i figure assembly is the way to go because its faster than everything else. i heard c is also good.
 
does anyone know a solid c book and a name of a compliler
 
anyone create thier own operating system?
 
id like to include an animation tool that converts animation into computer code. has anyone heard of this?

---

### Post by schauerlich on 2011-07-23
You don't want to write your own kernel. The fact that you don't even use the word right tells me you do not have the experience to do so. 

It sounds like what you want to do is make your own linux distribution - which is considerably easier (and boy is that an understatement). 

The easiest way to do this is to use existing tools, like [remastersys](http://www.psychocats.net/ubuntu/remastersys), to make a disk image based on a customized set of packages that you choose. That way you'll still have compatibility with Ubuntu, you can share its repos, and you'll be able to customize it to your needs. Once you have something like that working, you can look into making a true fork.

If that's not enough for you, you can start with a relatively minimal distro, such as [Arch](http://www.archlinux.org/) or [Gentoo](http://www.gentoo.org/), and then customizing it to your needs by pre-installing some packages. If that's still not enough, you can make a completely unique distro with [Linux From Scratch](http://www.linuxfromscratch.org/).

---

