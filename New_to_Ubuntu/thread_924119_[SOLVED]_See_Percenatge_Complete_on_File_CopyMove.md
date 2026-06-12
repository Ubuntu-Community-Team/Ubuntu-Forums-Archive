---
title: "[SOLVED] See Percenatge Complete on File Copy/Move"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by tomehb on 2008-09-19
Hi Guys,

Just wondering if it is possible to see the percentage when copying a file or even the amount currently done.... ie when coping a large file such as 4gigs, on to a different disc i would like to see how much it has currently done.. I have tried with the following:

mv -v /dir/file /locationdir/file
cp -v /dir/file /locationdir/file
tar cvf - file | (cd /locationdir/ tar xvfp -)


These dont show this, anyway to show what i want to see or is it impossible?

Thanks

---

### Post by Mornedhel on 2008-09-19
A quick man mv and man cp do not show anything like it. I do remember doing a lengthy cp operation on Mint and being completely astounded at the sight of a progression bar in the terminal, so it's possible, but apparently not with the regular mv and cp.

---

### Post by tomehb on 2008-09-19
Thanks for the reply,

It does not have to be using these commands, i just want too be able to see it, because i find it annoying when waiting for a file to transfer and i cant even tell how much it currently has transfered.. Maybe its just me who finds that annoying?

---

### Post by Mornedhel on 2008-09-19
Well well.

Apparently a patched version of coreutils does this (source : a Gentoo user).

URL : [http://www.aichler.net/fileutils/](http://www.aichler.net/fileutils/) (for patching and installation instructions)

I'll have to test this tonight.

---

### Post by tomehb on 2008-09-19
Thanks,
well let me no the outcome.. as i'm new to linux/ubuntu etc :) And i dont trust my self so much!

Cheers

Tom

---

### Post by MrWES on 2008-09-19
Hrmm...not to sound smart here, but if you're using Nautilus -- it will show you the progress of the file operation. Unless you perfer using CLI only.

Bill

---

### Post by philinux on 2008-09-19
The difference for large files is huge. In a test just now nautilus was copying at 8meg/second. With cp it was more like 100 meg/sec, (estimated of course).

---

### Post by tomehb on 2008-09-19
i want to use CLI....

---

### Post by bodhi.zazen on 2008-09-19
See if this helps : [http://clpbar.sourceforge.net/](http://clpbar.sourceforge.net/)

---

### Post by Mornedhel on 2008-09-19
The URL I gave previously has instructions on how to patch mv and cp for version fileutils 4.something. As cp and mv are now on coreutils 6.10 (and 6.12 is available from ftp.gnu.org), I decided to grab the patch from Gentoo and apply it myself.

Of note is a bit of text from the top of the patch :

> Upstream has been contacted about this a few times ...                          
                                                                                
they dont want progress bars in mv/cp:                                          
[http://lists.gnu.org/archive/html/bug-coreutils/2003-08/msg00114.html](http://lists.gnu.org/archive/html/bug-coreutils/2003-08/msg00114.html)           
[http://lists.gnu.org/archive/html/bug-coreutils/2003-09/msg00083.html](http://lists.gnu.org/archive/html/bug-coreutils/2003-09/msg00083.html)           
[http://lists.gnu.org/archive/html/bug-coreutils/2003-09/msg00084.html](http://lists.gnu.org/archive/html/bug-coreutils/2003-09/msg00084.html)           
                                                                                
but they don't seem to mind a general util ... add this to future patchset:     
[http://lists.gnu.org/archive/html/bug-coreutils/2003-09/msg00101.html](http://lists.gnu.org/archive/html/bug-coreutils/2003-09/msg00101.html)           
[http://lists.gnu.org/archive/html/bug-coreutils/2004-02/msg00071.html](http://lists.gnu.org/archive/html/bug-coreutils/2004-02/msg00071.html)
Upstream being, here, the coreutils devs. Apparently a bug has been filed in both Debian and Ubuntu as well. Debian marked the bug a non-issue and refused to fix it ; it's still on a Confirmed, Wishlist status for Ubuntu. I personally don't see the problem with a progress bar, especially if it's not the default, but oh well.

So I got the source, and the patch, and applied the patch to the source, and lo and behold, the patch failed (partially). So I fixed what had failed, and ./configure'd and make'd (sic), and lo and behold, it failed to compile.

As I am definitely not up to the task of fixing this manually, I'm giving up for now. I'll try and see if I can get a patched coreutils from a Gentoo user.

---

### Post by bodhi.zazen on 2008-09-19
See the link I gave you.

> bar -if /mnt/Data/ISO/ubuntu-8.04.1-desktop-amd64.iso -of ./ubuntu-8.04.1-desktop-amd64.iso
34.6MB at    4.9MB/s  eta:   0:02:13    4% [==                               ]

bar compiled without any problem and you should read the man page for usage.

The above command copied the Ubuntu iso to the current directory w/ a nice progress bar to go with :twisted:

---

### Post by tomehb on 2008-09-22
> **bodhi.zazen said:**
> See the link I gave you.



bar compiled without any problem and you should read the man page for usage.

The above command copied the Ubuntu iso to the current directory w/ a nice progress bar to go with :twisted:

Thats Brillant, thanks very much! :)

Thankyou to all of you Aswell...

---

