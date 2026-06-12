---
title: "How to compile TrueCrypt from source"
date: 2008-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by JRSeys on 2008-05-29
I found some conflicting advice about setting up TrueCrypt on Hardy Heron.  When I finally got it working, however, I it turned out to be pretty straightforward.

In particular, you absolutely do not need to do any kernel magic to make TrueCrypt work.  I successfully set up TrueCrypt on the most recent stock Ubuntu kernel (2.6.24-17-generic).

I found some threads that suggested you need to download kernel patches from Gentoo or compile your own kernel modules.  Luckily, that advice is outdated.  Neither of these is necessary now, which is good because you don't want to do them!

TrueCrypt implements its file system code with FUSE, a very clever project that lets file system designers break code out of the kernel.  FUSE does require in-kernel support, but Ubuntu's most recent kernel already includes it, so you're good to go!

Aside from FUSE, TrueCrypt also needs wxWidgets and GTK to compile.  Install these packages with apt.  Also, you always need the build-essential package when compiling from source.  It includes GCC and important build utilities.

Step 1: Install necessary packages
sudo apt-get install build-essential libfuse-dev libgtk2.0-dev

You don't need to install any wxWidgets packages because TrueCrypt's build system automatically builds wxWidgets from source for you.  That means you do need to download the wxWdigets source, however.

Step 2: Get wxWidgets
Download wxWidgets from [http://www.wxwidgets.org/downloads/]("http://www.wxwidgets.org/downloads/")
From the source archives list, choose the wxAll tarball.
Once it downloads, unpack anywhere you want.

A note about wxWidgets:
TrueCrypt's Makefile includes an option to build it without GUI support.  This is tempting to people who don't feel like doing all the additional setup required to have a GUI (installing libgtk2.0-dev and compiling wxWidgets).  Unfortunately, compiling with the command line only still fails if you don't set up wxWidgets.

Step 3: Get TrueCrypt
Download the TrueCrypt source from [http://www.truecrypt.org/downloads2.php]("http://www.truecrypt.org/downloads2.php")
Choose the Mac Os X/Linux source distrubtion.  Untar it anywhere you want.

Step 4: Have TrueCrypt compile wxWidgets for you
Change directories to the TrueCrypt source directory you just unpacked and execute the command:
make WX_ROOT=PATH_TO_WXALL wxbuild
Replace PATH_TO_WXALL with the directory of the wxWidgets source directory you unpacked in step 2.  This will take a few minutes to complete.

Step 5: Build TrueCrypt
You should still be in the TrueCrypt source directory.  Execute the command:
make

Step 6: Margaritas
TrueCrypt doesn't take so long to build that you'll have time to make and enjoy a Margarita.  If you happen to have a Margarita on hand, however, now would be the time.

Step 7: Run
If TrueCrypt finishes compiling without errors, it places its main binary in the Main directory.  Test it out with:
Main/truecrypt

If you're familiar with the Windows version of TrueCrypt, you already know how to use the GUI.  If not, you'll find that it's straightforward to learn.

Unfortunately, TrueCrypt's readme does not provide any advice for installing the compiled package.  I tend to run compiled programs from the directory I compiled them in anyway, since I don't like to put files in my /usr directory that aren't managed by a package manager.

Step 8: Mount an encrypted file system
In Windows, you can mount your encrypted file system on drive letters A: through Z:.  On Linux, you have the numbers 1-32.  If you mount an encrypted file system in slot 1, you'll find its files in /media/truecrypt1.

True Crypt is probably the best way to store encrypted data on your system.  It's easy to use once you have it set up, and the TrueCrypt team is very serious about security.  Additionally, as an open source project, it benefits from the scrutiny of external security experts.

You'll also find that you can use encrypted file systems you created on Windows with the Linux version.  I haven't tried the reverse, but I'm confident that it would also work.

--Justin

---

### Post by jaalto on 2008-09-28
For older 4.3a sources, see article [[color=blue]"Using truecrypt-installer to help install Truecrypt for Debian"[/color]](http://www.debian-administration.org/articles/506). With one command you can get the software running:

tc-dpkg --auto --install

---

### Post by Francewhoa on 2008-12-27
Thanks for the guide JRSeys.

Another how-to install TrueCrypt [guide here]("http://www.randyjensenonline.com/blog/installing-truecrypt-51a-on-ubuntu-804"). Great for absolute beginners. It worked with Ubuntu Desktop 8.04.1 and TrueCrypt version 5.1a or 6.1a.

---

### Post by kevdog on 2008-12-28
Link above broken!!

---

