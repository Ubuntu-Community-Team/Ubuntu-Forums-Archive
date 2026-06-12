---
title: "HOWTO: Compile and Install TrueCrypt 5.1a on Ubuntu 8.04 LTS (Hardy Heron)"
date: 2008-04-25
forum: Outdated Tutorials &amp; Tips
---

### Post by stami on 2008-04-25
Hi all,
this night after a lot of retries I finally upgraded my Ubuntu box to Hardy Heron :D
As you know everytime you do an upgrade there are always some problems with software. So this morning when I woke up, I tried to mount my truecrypt volume as usually with forcefield, but I get an unknown error message from the gui. So I tryed to manually mount my volume from the command line, and I get this error message:

```
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module
```

After some googling, I found a guide which helps me to compile and install TrueCrypt 5.1a on my new Hardy Heron so I decided to write this howto. 

It's quite simple and it should not take a lot of time.

So now open a terminal and start follow this guide. :D

First of all install some packages with apt:

```
sudo apt-get install build-essential linux-headers-`uname -r` linux-source-2.6.24 libfuse-dev libgtk2.0-dev
```

Note: [I]If you will notice that are needed other packages please inform me.
[/I]

Then create a tmp directory in your home directory:

```
mkdir -p ~/tmp
```

Now download TrueCrypt source from the official website:

[http://www.truecrypt.org/downloads2.php](http://www.truecrypt.org/downloads2.php)


Go to the path where you saved TrueCrypt source and untar the file in your ~/tmp directory

```
tar -zvxf TrueCrypt\ 5.1a\ Source.tar.gz -C ~/tmp
```

Now you should download wxAll source code. You can pick it from here:

[http://switch.dl.sourceforge.net/sourceforge/wxwindows/wxWidgets-2.8.7.tar.gz](http://switch.dl.sourceforge.net/sourceforge/wxwindows/wxWidgets-2.8.7.tar.gz)


Go to the path where you saved wxAll source and untar the file in your ~/tmp directory

```
tar -zvxf wxWidgets-2.8.7.tar.gz -C ~/tmp
```

Now go to your ~/tmp/truecrypt-5.1a-source directory:

```
cd ~/tmp/truecrypt-5.1a-source
```

and launch this command line:

```
WX_ROOT=~/tmp/wxWidgets-2.8.7 make wxbuild
```

This will build the ./wxrelease subdirectory in the truecrypt source path. You'll probably will have some warnings from the compiler, but you can safely ignore.

Once you have your shell back, launch this command line to compile truecrypt:

```
WX_ROOT=~/tmp/wxWidgets-2.8.7 make
```

Probably you will get a lots of warnings from the compiler, but you can ignore it. They are just warnings.

Now go Main directory in TrueCrypt source:

```
cd ~/tmp/truecrypt-5.1a-source/Main
```

and start truecrypt gui:

```
./truecrypt
```

If everything is ok, you should have now the truecrypt gui running.

Now close you application from the Gnome notification area and copy your just compiled truecrypt binary in you /usr/local/bin directory:

```
sudo cp ~/tmp/truecrypt-5.1a-source/Main/truecrypt /usr/local/bin/
```

Now you have truecrypt binary in your path so you can run it simply with:

```
truecrypt
```

Now you can safely remove your working directories:

```
rm -rf ~/tmp/truecrypt-5.1a-source ~/tmp/wxWidgets-2.8.7
```

I hope that this guide could help someone. If you notice somenthing wrong or if this guide doesn't work for you please let me know.

Thank you,
Stami.

---

### Post by kef_kf on 2008-04-26
```
WX_ROOT=~/tmp/wxWidgets-2.8.7 make wxbuild
```

gave me some error message about missing "gtk+-2.0.pc" so i had to install "libgtk2.0-dev" from synaptic and it worked like a charm.
thanks for the wonderful guide :)

---

### Post by stami on 2008-04-26
> **kef_kf said:**
> ```
WX_ROOT=~/tmp/wxWidgets-2.8.7 make wxbuild
```

gave me some error message about missing "gtk+-2.0.pc" so i had to install "libgtk2.0-dev" from synaptic and it worked like a charm.
thanks for the wonderful guide :)

Thank you, I added to apt-get packages list libgtk2.0-dev

---

### Post by jaided on 2008-04-27
Thank you! This worked perfectly for me. It really is a great guide!

---

### Post by Kilarin on 2008-04-27
This worked for me as well.  It was a lifesaver.  Thankyou!

BUT, why on EARTH is an application that is so essential as TrueCrypt NOT part of the Ubuntu repository?  I know it's not GPL, but it is open source.  Every time I update to a new version of Ubuntu I have to jump through hoops to get truecrypt working again so I can get at all of the data on my encrypted drives.  This seems like something that should be part of the repository at least, if not part of the basic installation.

---

### Post by pennygov on 2008-04-27
I upgraded to 8.04 yesterday knowing I'd need to compile and reinstall truecrypt being as it's kernel specific. Thanks for the Howto BUT: I too needed to install the libgtk stuff to get the wxbuild (which worked). Then when I went to the "make" step it couldn't finish because it couldn't find "fuse.pc". I've done some searching but can't figure out what "fuse" package I need for that. I have searched my system for fuse.pc and it isn't anywhere - except "fuse" in the linux source headers (/usr/src/...). According to Synaptic I have fuse-utils and libfuse2 but neither supplies that file.

Anyone out there who can help? :-(

---

### Post by pennygov on 2008-04-27
Never mind ... I just tried the deb package and it actually worked! Hmmm. I was sure it wouldn't work with the new kernel. Well, I won't complain except to myself for not trying it first.

Thanks anyway.

So the deb package for truecrypt 5.1a <http://www.truecrypt.org/downloads.php> works on Hardy! At least on my machine (Toshiba Satellite)

---

### Post by Pollywoggy on 2008-04-27
Thanks for the guide.  Once I upgraded to Hardy Heron, some things were broken, one of them truecrypt.  Thanks to your guide, I now have a nice GUI to go with truecrypt, but I still can't mount a volume (not even on the command line), I am getting the same errors as before.
Perhaps another reboot will fix it.  If not, I will need to do some Googling for a fix.

---

### Post by Pollywoggy on 2008-04-27
> **Pollywoggy said:**
> Thanks for the guide.  Once I upgraded to Hardy Heron, some things were broken, one of them truecrypt.  Thanks to your guide, I now have a nice GUI to go with truecrypt, but I still can't mount a volume (not even on the command line), I am getting the same errors as before.
Perhaps another reboot will fix it.  If not, I will need to do some Googling for a fix.

I think I know why it did not work before, I needed to enter the root password on the second prompt, not my volume password.

Any idea how to get this to work on the command line as well?
I am going to add a line for truecrypt to sudoers so that only trusted users can use it, without having to set the binary suid root.

---

### Post by stami on 2008-04-29
> **pennygov said:**
> Never mind ... I just tried the deb package and it actually worked! Hmmm. I was sure it wouldn't work with the new kernel. Well, I won't complain except to myself for not trying it first.

Thanks anyway.

So the deb package for truecrypt 5.1a <http://www.truecrypt.org/downloads.php> works on Hardy! At least on my machine (Toshiba Satellite)

Thank you for posting your expirience. However I wrote this howto because the deb package didn't works for me.
Of course if the deb package works, you can simply install it without follow this guide.

Thanks again,
Stami.

---

### Post by slackenerny on 2008-05-02
Did anyoneelse notice, that TC works reasonably slower now? Or is it just me/my machine?

best wishes

Mike

---

### Post by mrzaius on 2008-05-03
On the speed issues, this quote was presented by the deb package release mid-March for Truecrypt 5.1a:
 Due to a bug in some Linux kernel versions, you may experience
a very low performance or stalling when writing data to a TrueCrypt volume.
This problem can be solved by upgrading your kernel to the latest version.


As that might imply, I was able to get it installed without a hitch. Used this URL:
[http://www.truecrypt.org/downloads/truecrypt-5.1a-ubuntu-x86.tar.gz](http://www.truecrypt.org/downloads/truecrypt-5.1a-ubuntu-x86.tar.gz)   [I]Edit: By "it" I mean the .deb package inside that tarball. I did **not** have to compile it from source.
[/I]
There's a couple of things that freak me out about the new 5.x version, though: Beware the new automount. If you're like me and paranoid enough to never mount a partition "rw" if you're not writing to it, you must now pass a "-m ro" option to pass the mount option, since you're no longer manually mounting the loopback device. Also, note that the default mount points use truecrypt in the name. That word was in the default device naming in the 4.x builds, and the truecrypt processes will still show up in ps, so it's not a major concern, but do be aware of it.

---

### Post by skywalkin1138 on 2008-05-15
FYI, as of TrueCrypt 5.0, it no longer uses a kernel module, so you will not have to re-compile it each time the kernel upgrades.

---

### Post by chilli on 2008-05-19
> **skywalkin1138 said:**
> FYI, as of TrueCrypt 5.0, it no longer uses a kernel module, so you will not have to re-compile it each time the kernel upgrades.

yup, so just get the .deb from [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php), and install it

---

### Post by jdanov on 2008-05-21
Compiling and building took some time,

but it's DEFINITELY WORKING !!!!

Great How To thanks ):P

---

### Post by adpads on 2008-05-26
> **Pollywoggy said:**
> Any idea how to get this to work on the command line as well?

Sure, here are some instructions:
[http://pro.to.co.ls/linux/truecrypt-51a-command-line-version/](http://pro.to.co.ls/linux/truecrypt-51a-command-line-version/)

---

### Post by mosteo on 2008-06-09
> **mrzaius said:**
> On the speed issues, this quote was presented by the deb package release mid-March for Truecrypt 5.1a:
 Due to a bug in some Linux kernel versions, you may experience
a very low performance or stalling when writing data to a TrueCrypt volume.
This problem can be solved by upgrading your kernel to the latest version.


I suspect I may be experiencing said bug. Writing to a truecrypted external USB HD, I typically see short bursts of activity and long periods of near no disk access.

I have Hardy with all the updates:

Linux hostname 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

Is there more information on this? bug reports somewhere, possible solutions?

---

### Post by Francewhoa on 2008-12-27
Another how-to install TrueCrypt [guide here]("http://www.randyjensenonline.com/blog/installing-truecrypt-51a-on-ubuntu-804"). Great for absolute beginners. It worked with Ubuntu Desktop 8.04.1 and TrueCrypt version 5.1a or 6.1a.

---

