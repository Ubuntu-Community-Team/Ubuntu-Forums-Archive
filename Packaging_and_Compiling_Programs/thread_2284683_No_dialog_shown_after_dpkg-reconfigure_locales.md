---
title: "No dialog shown after dpkg-reconfigure locales"
date: 2015-07-01
forum: Packaging and Compiling Programs
---

### Post by Riccardo_Bello on 2015-07-01
Hello, I'm new to this forum and I hope I chose the right subforum for my question.
I just bought a new VPS and I kept getting messages about missing locales. Googled the solution and found that most people run 'dpkg-reconfigure locales', choose their locales from a dialog and solve their problem. On my system, instead, I get no dialog when I run dpkg-reconfigure locales. Here's what I get:
```

[FONT=Menlo]root@rickyb98:/home/rickyb98# dpkg-reconfigure locales
[/FONT][FONT=Menlo]perl: warning: Setting locale failed.[/FONT]
[FONT=Menlo]perl: warning: Please check that your locale settings:[/FONT]
[FONT=Menlo]    LANGUAGE = (unset),[/FONT]
[FONT=Menlo]    LC_ALL = (unset),[/FONT]
[FONT=Menlo]    LC_CTYPE = "UTF-8",[/FONT]
[FONT=Menlo]    LANG = (unset)[/FONT]
[FONT=Menlo]    are supported and installed on your system.[/FONT]
[FONT=Menlo]perl: warning: Falling back to the standard locale ("C").[/FONT]
[FONT=Menlo]locale: Cannot set LC_CTYPE to default locale: No such file or directory[/FONT]
[FONT=Menlo]locale: Cannot set LC_ALL to default locale: No such file or directory[/FONT]
[FONT=Menlo]Generating locales...[/FONT]
[FONT=Menlo]  en_AG.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_AU.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_BW.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_CA.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_DK.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_GB.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_HK.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_IE.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_IN.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_NG.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_NZ.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_PH.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_SG.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_US.ISO-8859-1... up-to-date[/FONT]
[FONT=Menlo]  en_US.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_ZA.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_ZM.UTF-8... up-to-date[/FONT]
[FONT=Menlo]  en_ZW.UTF-8... up-to-date[/FONT]
[FONT=Menlo]Generation complete.[/FONT]

```

What's wrong with it? I tried reinstalling locales with no success.
Thanks in advance,
Riccardo Bello

---

### Post by slickymaster on 2015-07-01
Hi Riccardo_Bello, welcome to the forums.

Please, run the following (to en_US.UTF-8 for example), in a terminal window:```
sudo locale-gen "en_US.UTF-8"
```and afterwards```
sudo dpkg-reconfigure locales
```

---

### Post by Hobart on 2015-07-16
> **Riccardo_Bello said:**
> Hello, I'm new to this forum and I hope I chose the right subforum for my question.
Welcome!

> **Riccardo_Bello said:**
> I just bought a new VPS and I kept getting messages about missing locales. Googled the solution and found that most people run 'dpkg-reconfigure locales', choose their locales from a dialog and solve their problem. On my system, instead, I get no dialog when I run dpkg-reconfigure locales.

You're running into a difference between Ubuntu and Debian.

On a Debian system, [the 'locales' package]("https://packages.debian.org/stable/locales") is part of the 'glibc' source package.  Debian's version of that package contains [a template]("http://anonscm.debian.org/viewvc/pkg-glibc/glibc-package/trunk/debian/debhelper.in/locales.templates?view=markup") for the "debhelper" subsystem, which produces the GUI when you run **dpkg-reconfigure locales**:
[IMG]http://i.imgur.com/XsBM5fj.png[/IMG]

On an Ubuntu system, 'locales' is a completely different package due to a move towards a different system that appears to have been dropped.  

Some history: [LocalesThatDontSuck]("https://wiki.ubuntu.com/LocalesThatDontSuck") (created 'langpack-locales'), [Switch to using the belocs locale packages]("https://launchpad.net/ubuntu/+spec/belocs-locales"), [remove belocs-locales-bin from jaunty]("https://bugs.launchpad.net/ubuntu/+source/belocs-locales-bin/+bug/335306")

Ubuntu's Launchpad bug-tracker has an open bug on this: [ "dpkg-reconfigure locales" does not work properly]("https://bugs.launchpad.net/ubuntu/+source/belocs-locales-bin/+bug/48573")

I believe the current workarounds are to either add "language pack" packages, or manually edit config files in /etc and regenerate the locales with dpkg-reconfigure.

---

