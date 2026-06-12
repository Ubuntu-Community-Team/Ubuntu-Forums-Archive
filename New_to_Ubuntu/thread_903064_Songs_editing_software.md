---
title: "Songs editing software"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by pkj on 2008-08-27
Hi,

Looking for some software that can help me edit songs...
I want to cut a song and join multiple pieces of different songs to produce a new song...

pkj

---

### Post by garyed on 2008-08-27
I think Ardour might do what you want.

---

### Post by jgrabham on 2008-08-27
> **pkj said:**
> Hi,

Looking for some software that can help me edit songs...
I want to cut a song and join multiple pieces of different songs to produce a new song...

pkj

Most people I know, myself included use a program called audacity, just open a terminal and type ```
sudo apt-get install audacity
``` and it'll be installed

[Audacity's web page]("http://audacity.sourceforge.net/")

---

### Post by OutOfReach on 2008-08-27
For what you are wanting to do (edit songs) Audacity would definitely be the best, it's also in the repositories so you can just search for it in the Synaptic package manager.

---

### Post by pkj on 2008-08-28
Hi,
Downloaded audacity..

Seems to have some problem...

When i start the application..the audacity window opens..but i do not see the menu options..Moving the cursor on the horizontal bar (which is blank) shows some dropdown options...

Basically unable to use audacity..

Any solution

pkj

---

### Post by OffAxis on 2008-08-28
sounds like a video driver or package dependency problem; what's your card and are you using the restricted driver?

you could also try starting it from the terminal and see if any errors pop up.

---

### Post by pkj on 2008-08-28
There are no errors popping-up even if i start up from the terminal...The problem however persists

How do i firnd out as to which is my video card...

pkj

---

### Post by markbuntu on 2008-08-28
Audacity has a lot of problems with Ubuntu as you are finding out. I gave up on it myself and switched to ardour.

You should really try ardour, it is the professional heavyweight champion for sound mixing/editing in linux.

---

### Post by pkj on 2008-08-31
Downloaded Ardour using "Syneptic"

When launching the application from the Command line.. Following error message appears

Ardour/GTK 0.99.3
   (built using 1.4.1 with libardour 0.908.2 and GCC version 4.1.2 20061103 (prerelease) (Ubuntu 4.1.1-18ubuntu2))
Copyright (C) 1999-2006 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
Loading UI configuration file /etc/ardour/ardour_ui.rc
exec of JACK server failed: No such file or directory
ardour: [ERROR]: Unable to connect to JACK server
ardour: [ERROR]: Could not connect to JACK server as  "ardour"

How to proceed

pkj

---

### Post by wankel on 2008-08-31
I recall there's an option in Synaptic to see recommended packages as dependencies. That would mean: software that is seen as quite useful in combination with the to be installed package, is also installed.

In my apt config, it is probably turned on. When giving <code>sudo aptitude install ardour</code> on the commandline, the following packages are also installed:

<code>
ardour jackd liblo0 liblrdf0 python-crypto python-openssl python-pam python-pyopenssl python-serial python-twisted python-twisted-bin python-twisted-conch
  python-twisted-core python-twisted-lore python-twisted-mail python-twisted-names python-twisted-news python-twisted-runner python-twisted-web python-twisted-words
  python-zopeinterface qjackctl
</code>

To install those packages, you can type on the commandline <code>
sudo aptitude install jackd liblo0 liblrdf0 python-crypto python-openssl python-pam python-pyopenssl python-serial python-twisted python-twisted-bin python-twisted-conch
  python-twisted-core python-twisted-lore python-twisted-mail python-twisted-names python-twisted-news python-twisted-runner python-twisted-web python-twisted-words
  python-zopeinterface qjackctl
</code>

or select the packages by hand in synaptic.

Good luck!

---

