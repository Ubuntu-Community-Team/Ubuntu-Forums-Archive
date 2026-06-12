---
title: "Find version of gnome?"
date: 2011-07-26
forum: Programming Talk
---

### Post by hakermania on 2011-07-26
Hello. My program runs a command that is different on gnome2 and gnome3
So, how do I find gnome version?
The command is:
gnome2: gconftool-2
gnome3: gsettings
I would prefer neither to use gdm nor gnome-about as they are not pre-installed in oneiric!

Thanks in advance for any answers!

---

### Post by nvteighen on 2011-07-26
> **hakermania said:**
> Hello. My program runs a command that is different on gnome2 and gnome3
So, how do I find gnome version?
The command is:
gnome2: gconftool-2
gnome3: gsettings
I would prefer neither to use gdm nor gnome-about as they are not pre-installed in oneiric!

Thanks in advance for any answers!

First question: are you sure the command isn't available as a procedure in libgnome or any other library? It's very unlikely.

Second: GNOME "version" is a very blurry concept. When a new Debian release is prepared (the so-called "testing" branch), GNOME enters into a transition zone where you get lots of stuff from the new version on top of the old GNOME... and the version number displayed by gnome-about becomes unreliable. Exactly at this moment, my Debian testing runs a theoretical GNOME 2.30 mixed with GDM 3.0 and some GTK+3 GNOME 3 applications (that look painfully awful because the GTK+3 theme engine is not available yet...).

---

### Post by hakermania on 2011-07-26
[nvteighen]("http://ubuntuforums.org/member.php?u=273037"), thanks for the answer, so, do you suggest doing everything through a library and not by a system call?

---

### Post by nvteighen on 2011-07-27
> **hakermania said:**
> [nvteighen]("http://ubuntuforums.org/member.php?u=273037"), thanks for the answer, so, do you suggest doing everything through a library and not by a system call?

Yes, if it's available. If not, try using a pipe (popen) and resort to system() only if nothing else works. This is because libraries give you the full interface, while pipes only allow you to interface via I/O and system(), only through command line arguments and the command's exit code.

And just for correctness: a "system call" is actually something different. You mean "system command" or "shell command", i.e. calling stuff through system(). System calls are a bunch of functions implemented by the kernel.

---

### Post by hakermania on 2011-07-27
> **nvteighen said:**
> Yes, if it's available. If not, try using a pipe (popen) and resort to system() only if nothing else works. This is because libraries give you the full interface, while pipes only allow you to interface via I/O and system(), only through command line arguments and the command's exit code.

And just for correctness: a "system call" is actually something different. You mean "system command" or "shell command", i.e. calling stuff through system(). System calls are a bunch of functions implemented by the kernel.

I want to change a configuration value.
Is this what am I looking for?
[http://developer.gnome.org/libgnome/stable/libgnome-gnome-config.html#gnome-config-set-string](http://developer.gnome.org/libgnome/stable/libgnome-gnome-config.html#gnome-config-set-string)
(yes apparently, but I don't want to mess around and waste my time if it isn't this)

Also, do I have to install libgnomemm-2.6-dev, right?

---

### Post by nvteighen on 2011-07-27
> **hakermania said:**
> I want to change a configuration value.
Is this what am I looking for?
[http://developer.gnome.org/libgnome/stable/libgnome-gnome-config.html#gnome-config-set-string](http://developer.gnome.org/libgnome/stable/libgnome-gnome-config.html#gnome-config-set-string)
(yes apparently, but I don't want to mess around and waste my time if it isn't this)

Also, do I have to install libgnomemm-2.6-dev, right?

That's deprecated, it seems.

I've never done any GNOME programming, so I don't really know its API and all I can tell you is from what I know of the system itself.

For GNOME 2.x, I'd try using libgconf. Not sure if there's a C++ binding.

For GNOME 3, there's something called dconf, which seems to be the backend for gsettings. There's an API for it.

But be aware of the following: it makes almost no sense to develop a program aiming for both GNOME 2.x and 3... You can, but it's quite cumbersome; in C++ it might require some heavy preprocessor magic and possibly some autotools magic too.

---

### Post by hakermania on 2011-07-27
> **nvteighen said:**
> That's deprecated, it seems.

I've never done any GNOME programming, so I don't really know its API and all I can tell you is from what I know of the system itself.

For GNOME 2.x, I'd try using libgconf. Not sure if there's a C++ binding.

For GNOME 3, there's something called dconf, which seems to be the backend for gsettings. There's an API for it.

But be aware of the following: it makes almost no sense to develop a program aiming for both GNOME 2.x and 3... You can, but it's quite cumbersome; in C++ it might require some heavy preprocessor magic and possibly some autotools magic too.

maybe 2 different versions of the same program :)
one for gnome 3 and one for 2

---

