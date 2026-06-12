---
title: "Gtk+"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by traisen on 2008-06-26
I'm new to Ubuntu 8.04 (install 2 days ago) I'm trying to install GNU classpath 97.2

How do I get all of GTK+ that I need - not just parts? 
How can I see I have GTK+? Is there a general package?
What do you look for with pkg-config to see gtk+?
I have applications installed that say they are based on gtk2+ so parts of it must be there.
How can I let ./configure know I have GTK+?

Here's the errors I getting and what I've tried...
Doing a ./configure for GNU classpath I get gtk2+ errors and need help.

I've tried installing various dev pkgs and applications that use GTK++
I get a little bit further, but now get...
gtk+-2.0 was not found
No package 'gdk-pixbuf-2.0' found

But dont find a package with these to install in add/delete or synaptic pkg mgr... I do find and have installed:
gtk2-engines-pixbuf 2.12.x Pixbuf-based theme for GTK+ 2.x

Where do I look?

I found [https://launchpad.net/ubuntu/+source/classpath](https://launchpad.net/ubuntu/+source/classpath)
but don't know how to use it... It uses classpath 96.x and I wanting to install 97.x, but it might install the dependencies I need.

Thanks, Carolyn

Specfic message:
checking for gtk+-2.0 >= 2.8 gthread-2.0 >= 2.2 gdk-pixbuf-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gdk-pixbuf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdk-pixbuf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gdk-pixbuf-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.8 gthread-2.0 >= 2.2 gdk-pixbuf-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by traisen on 2008-06-26
Is this the right forum to ask this? if not where?
More info libgtk2.0-dev is installed like similar questions suggested.

---

### Post by AtrejuT on 2008-06-26
You might try running 
```

sudo apt-get build-dep classpath

```
that should (in theory) pull in all dependencies needed to build it. If these dependencies changed from 96 to 97 you might still run into problems, but it is rather likely that it will work.

Good luck!

atreju

---

### Post by traisen on 2008-06-26
Thanks - no dependencies listed, but I listed the packages via Synaptic for classpath. classpath 96 install fine with sudo and restall via Synaptic ...

I got gtk+2 to work installing as many dev pkgs that looked like it had similiar dependencies, but now  get...

 "Package gconf-2.0 was not found in the pkg-config search path."

I restallled it (shows installed in Synaptic), but problem is still there.

Why is it listed as installed in Synaptic, but pkgconfig doesn't see it.
The suggestion is a .pc file... With find I think I know what goes there, but when is right to add manually like that and when is it a real problem?

Why do some installed packages have an Ubuntu symbol next them and others just the filled in checkbox to show they are installed?

Thanks

---

### Post by AtrejuT on 2008-06-27
The ubuntu symbol next to a package AFAIK means that it is in main (as opposed to universe or multiverse), so it has nothing at all to do with whether it is installed.
as to gconf. maybe you have to install libgconf2-dev ?

sorry for the delay

atreju

---

### Post by iaculallad on 2008-06-27
Since Ubuntu's desktop environment GNOME makes use of GTK+2, there should be no need for you to install the GTK sources. Ubuntu is pre-installed by default with the GTK+2 library. 
Try to getting the header files instead (libgtk2.0-dev).

---

