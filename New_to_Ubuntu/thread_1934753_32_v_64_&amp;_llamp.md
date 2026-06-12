---
title: "32 v 64 &amp; llamp"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by topdog2009 on 2012-03-02
I get this message when trying to start xammp (actually llamp) by using this:-
sudo /opt/lampp/lampp start


XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

What do I do now?

Brian

---

### Post by grahammechanical on 2012-03-02
This is not a satisfactory answer but a lot of work has been done in 12.04 on something called Multiarch. It means (I think) a set of libraries so that a 32bit program or application will run better on 64bit Ubuntu than at present.

I have found this regarding 11.10

[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta1]("https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta1")

Note this heading

> **Improved handling of 32-bit compatibility on amd64 systems**

And this

> Ubuntu 11.10 Beta 1 enables "multiarch" support for installing 32-bit library and application packages on 64-bit systems. For all amd64 installs and upgrades, select 32-bit software, including skype and flash, will be installable directly using the same 32-bit packages that are used on i386 installations, without the need to install the ia32-libs compatibility package. For users this means 32-bit libraries will always be available at the same time as their 64-bit counterparts, even in the case of security updates, and users will only need to install those 32-bit libraries needed by the applications they have installed.

As your program may not be one of the select programs of 32bit software referred to, you may need to install the ia32-libs compatibility package. But this is just a guess on my part.

Regards.

---

### Post by topdog2009 on 2012-03-03
> you may need to install the ia32-libs compatibility package

OK, how?

If I try:=
sudo aptitude install ia-32libs I get:
sudo: aptitude: command not found

If I try :-
echo foreign-architecture i386|sudo tee/etc/dpkg/dpkg.cfg.d/multiarch

I get 
tee/etc/dpkg/dpkg.cfg.d/multiarch: command not found

BTW, I have no real idea what those commands do, just copied them from Ubuntu forums.

Brian

---

### Post by jerome1232 on 2012-03-03
```
sudo apt-get update
sudo apt-get install ia32-libs
```

Auto completion is your friend on the command line, just type out like the first 4 or 5 words of a command then tap or double tap tab to auto complete or get an auto complete list.

---

### Post by topdog2009 on 2012-03-03
Got the update but the install gave me:

Unable to locate package ia32

And I could not see it listed (not sue that I should) in the listing of the update files.

Brian

---

### Post by mcduck on 2012-03-03
You might actually have easier time using Ubuntu's own LAMP stack instead of XAMP...

Actually I'd recommend even if you weren't having issues with 32/64-bit, as the native LAMP stack is better integrated with the rest of the system, and of course also has the benefit of automatic security updates through Ubuntu's package management. :)

...and the quick&simple way to install the native LAMP stack on Ubuntu:
```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```
...and more info, & more detailed installation information if you need more features or want to hand-pick the components instead of using tasksel: [https://help.ubuntu.com/11.10/serverguide/C/index.html]("https://help.ubuntu.com/11.10/serverguide/C/index.html")

---

### Post by topdog2009 on 2012-03-03
That worked. Many thanks.

Now Ihave to learn how to use it :KS

Brian

---

