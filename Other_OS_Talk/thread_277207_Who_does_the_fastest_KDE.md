---
title: "Who does the fastest KDE?"
date: 2006-10-14
forum: Other OS Talk
---

### Post by tseliot on 2006-10-14
Who does the fastest KDE?

I have noticed that Slackware's 11 KDE is fast but getting everything to work on my laptop would take too much time.

---

### Post by pelle.k on 2006-10-15
Hey, haven't i seen you in the arch forums? If so, you know who does the fastest kde ;)
Seriously, Arch kde is noticeably faster than most others... but i have heard slackware kde is really snappy. Too bad i can't stand slackware...

---

### Post by Engnome on 2006-10-15
Installing ubuntu-server and then adding kde-core is alot faster than installing kubuntu.

Just a tip...

---

### Post by tseliot on 2006-10-15
> **pelle.k said:**
> Hey, haven't i seen you in the arch forums? If so, you know who does the fastest kde ;)
Seriously, Arch kde is noticeably faster than most others... but i have heard slackware kde is really snappy. Too bad i can't stand slackware...

Well, I left Arch because I wanted something else (i.e. with frequency scaling and other things out-the-box) for my old laptop.

Unfortunately the mouse won't work in Slackware even if I install the modules for kernel 2.6.17 :(

---

### Post by tseliot on 2006-10-15
> **Engnome said:**
> Installing ubuntu-server and then adding kde-core is alot faster than installing kubuntu.

Just a tip...

I'll definitely give it a shot when Edgy is released ;)

---

### Post by Feanor on 2006-10-16
After a heavy use (and now exclusively) of linux I think I can choose a Server installation and select to install kde after. Now the question is: installing kubuntu-desktop in this way what difference makes?

Anyway I'm waiting for edgy release to cleanup my notebook and my desktop system. They have seen hoary, breezy and dapper and I think is necessary a little order :D

---

### Post by pelle.k on 2006-10-16
tseliot: Maybe you should try frugalware? It's slackware based, with pacman and abs (repoman in frugal) slapped upon it. It's also i686 optimized.
You could argue it's arch with less command line, more gui, but that's not really true since arch is built from scratch.
Oh, and it's kde is fast... :)

---

### Post by tseliot on 2006-10-16
> **pelle.k said:**
> tseliot: Maybe you should try frugalware? It's slackware based, with pacman and abs (repoman in frugal) slapped upon it. It's also i686 optimized.
You could argue it's arch with less command line, more gui, but that's not really true since arch is built from scratch.
Oh, and it's kde is fast... :)

Ok, I'll try it out.

Thanks ;)

---

### Post by arox on 2006-10-16
Fast distros have fast KDE - simple


You can always try to compile it yourself

---

### Post by Engnome on 2006-10-16
> **Feanor said:**
> After a heavy use (and now exclusively) of linux I think I can choose a Server installation and select to install kde after. Now the question is: installing kubuntu-desktop in this way what difference makes?


kubuntu-desktop is ALOT of applications. Every app you get when you do a normal install. 

I guess you can figure out what core means by yourself?

---

### Post by Feanor on 2006-10-16
So a server install + apt-get install kubuntu desktop = desktop install? Or there are differences also in terms of services and then in performance?

---

### Post by tseliot on 2006-10-16
> **Feanor said:**
> So a server install + apt-get install kubuntu desktop = desktop install? Or there are differences also in terms of services and then in performance?

It's the same.

You should try this instead:
[http://ubuntuforums.org/showthread.php?t=277090](http://ubuntuforums.org/showthread.php?t=277090)

---

### Post by Ob1 on 2006-10-17
The server edition of Dapper + KDE-core

---

### Post by kopilo on 2006-10-17
Maybe it is just my system but I've found Mepis to be fairly darn fast with KDE.

---

### Post by RAV TUX on 2006-10-17
> **tseliot said:**
> Who does the fastest KDE?

I have noticed that Slackware's 11 KDE is fast but getting everything to work on my laptop would take too much time.

Knoppix 5.0.1

---

### Post by nyinge on 2006-10-19
> **Engnome said:**
> Installing ubuntu-server and then adding kde-core is alot faster than installing kubuntu.

Just a tip...
Thanks.  No wonder installing kubuntu-desktop seems like forever.

---

### Post by jdong on 2006-10-22
FC6 with SELinux disabled, or OpenSUSE 10.2 will likely get you the fastest KDE, as both use DT_GNU_HASH now, which is meant to speed up dynamic linking (a significant portion of the time it takes to load a KDE app)

---

### Post by chaosgeisterchen on 2006-10-22
Thanks, but that would mean that I have to move from Kubuntu to... :-O

---

### Post by jdong on 2006-10-22
Perhaps... though there's still conflicting reports on the effects of DT_GNU_HASH.... Gentoo camp seems to say that it adds about 2MB's worth of hashes to every binary, which will certainly increase IO load.

KUbuntu is plenty fast for me on all of my systems, and Edgy feels a bit snappier than Dapper even.

---

### Post by chaosgeisterchen on 2006-10-22
Yes! I have to admit that I have mentioned 2 things as I went away from SuSE to Kubuntu:

Fonts were not a bit as smooth.. today it is a bit better but whenever I look at SuSE screens from November 2005.. I had Lucida Grande 7pt and it looked super smooth.

And KDE was a lot faster..

---

### Post by rattlerviper on 2006-10-24
PCLinuxOS minime edition...Choose to run the live disk from RAM...Smoking fast!!!  It's also the fatest I have run when installed.  But for the fastest just run it from RAM

---

### Post by tseliot on 2006-11-01
I think that Fedora Core 6 does the fastest KDE.

If you click on an app from the applications menu, the apps shows up in 1 second.

I have never seen anything that fast. It's much faster than Gentoo.

---

### Post by jdong on 2006-11-01
> **tseliot said:**
> I think that Fedora Core 6 does the fastest KDE.

If you click on an app from the applications menu, the apps shows up in 1 second.

I have never seen anything that fast. It's much faster than Gentoo.

That's probably DT_GNU_HASH at work then... The last time I tried it, it added way too much size onto binaries, which reduced performance due to cache missing and disk IO (though a second load would be substantially faster if the app is still cached)

Perhaps they fixed that already, or Fedora just prefetches most of the KDE binaries so you don't feel that initial lag as much.

---

### Post by RAV TUX on 2006-11-01
> **tseliot said:**
> I think that Fedora Core 6 does the fastest KDE.

If you click on an app from the applications menu, the apps shows up in 1 second.

I have never seen anything that fast. It's much faster than Gentoo.

If I could get it to work on my computer I might be able to respond appropiately. For me I still find KNOPPIX INSTALLED! 5.0.1 the fastest but I prefer to use Gnome.

---

### Post by tseliot on 2006-11-02
> **yozef said:**
> If I could get it to work on my computer I might be able to respond appropiately.
I know what you mean. Fedora Core 6 won't install on my father's computer. I get GRUB error when I try to boot the installer.

---

### Post by chaosgeisterchen on 2006-11-05
Interesting. I think it's worth trying out KDE with FC6. If that fails I will wait for SuSE 10.2

---

### Post by rattlerviper on 2006-11-08
> **tseliot said:**
> I think that Fedora Core 6 does the fastest KDE.

If you click on an app from the applications menu, the apps shows up in 1 second.

I have never seen anything that fast. It's much faster than Gentoo.
Confirmed at least on my PC...It is faster:D

---

