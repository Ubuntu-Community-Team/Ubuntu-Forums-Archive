---
title: "how to make a os installer"
date: 2007-10-21
forum: Programming Talk
---

### Post by snickers295 on 2007-10-21
Hi i was wondering how to make a OS installer like the one on the Ubuntu alternate CD.
if there is source to that that would be great but if not could you tell me how to make one.

---

### Post by Engnome on 2007-10-21
> **snickers295 said:**
> Hi i was wondering how to make a OS installer like the one on the Ubuntu alternate CD.
if there is source to that that would be great but if not could you tell me how to make one.

Read up on debian installer and ncurses. That's all I can say, no one is going to explain this to you and there probably aren't any "How to make an operating system installer in x easy steps." out there. Good luck to you but beware, it's not for beginners.

---

### Post by dwhitney67 on 2007-10-21
Ah, the proverbial question for which there is no easy answer.

Many distros like to state that it is easy to create a Linux distro using their setup, however what they fail to mention is that it is near impossible to create a minimal setup that is void of all the crap (e.g. gnome, web browsers, email clients, etc) that comes with a traditional distro.  How is one supposed to know what packages are needed and which are not (for dependency issues), unless one examines each package in detail... and there are 1000's of them.  It comes down to the point that the easiest thing to do is to create your own distro.

Take a peek at the documentation of LFS ([Linux from Scratch]("http://www.linuxfromscratch.org/lfs/view/stable/")) and BLFS ([Beyond Linux from Scratch]("http://www.linuxfromscratch.org/blfs/view/stable/")).  These are both helpful guides, however there is no mention on how to create bootable media in which one can use to install on OS onto a HDD.  They assume that if you complete their guides, that you will boot into the OS on your HDD.

---

### Post by snickers295 on 2007-10-21
all it is is a installer on a iso right?
i know how to make a iso but not the installer.

---

### Post by dwhitney67 on 2007-10-21
There's a lot more to it than just an "installer".  Essentially one must create a minimal-Linux system that they can boot from CD.  That system must at a minimum have a kernel, glibc, gcc run-time libraries, grub, device nodes (e.g. console and null), and a perhaps simple shell as provided by busybox.  The CD is made bootable using Grub's El-Torito loader.  If you want a GUI, then X11 will be needed, plus whatever GUI app you require and the libraries to support such.

The installer script will need to setup the HDD (create partitions, format them, etc), then install the software packages onto the HDD that make up the Linux distro you are interested in delivering.  Once again, not an easy task, but doable.

Anyhow, there is probably lots more to this task than I can possibly condense into a few paragraphs, and since I have no idea what you are attempting to build, it is hard to give you concrete advice on how to approach your problem.

BTW, these are the packages (and versions) that my employer uses for their Linux distro:

[PHP]BASE_TARGETS  = base \
                busybox-1.2.2.1 \
                e2fsprogs-1.40.2 \
                eject-2.1.5 \
                expat-1.95.7 \
                gcc-4.1.1 \
                glibc-2.4 \
                grub-0.97 \
                hwclock-2.23 \
                linux-2.6.17.13 \
                ncurses-5.4 \
                openssh-3.9p1 \
                openssl-0.9.7d \
                qt-x11-free-3.2.3 \
                tinyxml_2_3_1 \
                X11R6.9.0 \
                zlib-1.2.1

# The EXTRA_PACKAGES are not used by the CD-R; they are copied
# to the HDD of the target system.
#
EXTRA_TARGETS = dvdrtools-0.1.6 \
                lockdev-1.0.1 \
                portmap-5-3 \
                setserial-2.17 \
                xpm-3.4k[/PHP]

The base contains the FHS directory structure, along with configuration files for passwd, group, hosts, xorg.conf, you name it.

---

### Post by snickers295 on 2007-10-22
i want to be able to install Linux from scratch to a hdd but i want to make it so i can install it.
so the files on the iso are a small system with partitioner compiler etc.?
p.s. what is the name of your company's distro?

---

### Post by dwhitney67 on 2007-10-22
You are going to need to create the mini-OS that runs on the CD yourself.  Most distros employ an initial RAM disk (initrd), which from what I understand is nothing more than a mini-application (shell script?) that is used to drive the installation process.  The initrd is launched automagically when the kernel boots.

Go to this website, and maybe you can get some ideas from Ubuntu's LiveCD customization tips:  [http://help.ubuntu.com/community/LiveCDCustomization](http://help.ubuntu.com/community/LiveCDCustomization)

As for my company's distro, it is not available for public "distribution".  The distro is bundled together with with my company's proprietary applications and provided "free" when customers purchase a product from my company.

P.S.  I forgot to mention earlier that the distro I use has all of the device nodes pre-made; most modern distros today depend upon udev.  So that's an additional package that you might have to consider including on the CD-R and installed on the HDD.

---

