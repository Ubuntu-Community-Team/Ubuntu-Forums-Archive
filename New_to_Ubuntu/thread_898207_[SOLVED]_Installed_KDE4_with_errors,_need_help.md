---
title: "[SOLVED] Installed KDE4 with errors, need help"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by anewguy on 2008-08-23
I tried installing KDE4 according to another thread in this forum.  It had errors, so I did a bunch of apt-get update, apt-get build-dep, etc., and still had problems.  I went to Synaptic (guess I should have done that first after adding the repository!!) and it said I had a broken package.  At any rate, seemed to have gotten that cleared up and I can start a KDE4 session.  However I still have an error with the automatic updates.  It says it needs to update kopete-kde4, but always has errors.

I have attached 2 screen shots - the first is the error, the 2nd is the detail screen showing the error.

Can anyone help me with this?

Thanks in advance!  :)

---

### Post by eightmillion on 2008-08-23
Try running this:
> sudo apt-get clean
sudo apt-get install kopete-kde4

---

### Post by anewguy on 2008-08-23
Hey, I like your hedgehog thing - that's cute.

I tried as you suggested, with it resulting in the same abort.  I noticed it mentioned trying to overwrite a .so in a kde4 library right before it died, so I deleted that file and reran, still get the same error:

Install these packages without verification [y/N]? y
(Reading database ... 261938 files and directories currently installed.)
Preparing to replace kopete-kde4 4:4.0.3-0ubuntu1 (using .../kopete-kde4_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb) ...
Unpacking replacement kopete-kde4 ...
dpkg: error processing /var/cache/apt/archives/kopete-kde4_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/kde4/kopete_otr.so', which is also in package kopete-plugin-otr-kde4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kopete-kde4_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dave@dave-desktop:~$ 

I then did an apt-get remove of kopete-plugin-otr-kde4 and then reran the apt-get install of kopete-kde4 and it worked.  Somehow the packages must have conflicted.  I guess I'll find out later if kopete still works!

Thanks for the reply!  :)

---

