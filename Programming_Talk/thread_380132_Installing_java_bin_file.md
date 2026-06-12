---
title: "Installing java bin file"
date: 2007-03-09
forum: Programming Talk
---

### Post by geovino on 2007-03-09
How do I install this file?

/home/davek/Downloads/j2sdk-1_4_2_13-linux-i586.bin

everytime I want to use synaptic I get error messages about this and I guess I need to install it.

---

### Post by YoG%*@ on 2007-03-09
hi!

does it have to be installed from the bin file? you can do it otherwise:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0")

hth!
mux

---

### Post by laxmanb on 2007-03-09
so the error remains even after you move the file to another directory?? I don't think you need to install it... Synaptic has it's own little database of installed/to-be-installed packages... 

If Synaptic starts, just mark the *j2sdk1.4* packages for removal... see if that helps

otherwise here's how to install the SDK(from the .bin file):
[http://phossal.com/thread?view=702216931](http://phossal.com/thread?view=702216931)

---

### Post by phossal on 2007-03-09
> **geovino said:**
> How do I install this file? /home/davek/Downloads/[COLOR="Red"]**j2sdk-1_4_2_13-linux-i586.bin**[/COLOR] Everytime I want to use synaptic I get error messages about this and I guess I need to install it.


Whoa. You almost *never* want to install *that* file. That's a "previous version" of Java, and almost nothing *needs* that anymore. I can image two or three errors that you might be getting. Can you please post one?

[EDIT] In fact, the instructions in my signature will *not* work when installing j2sdk-1_4_2_13-linux-i586.bin without downloading an additional .so library, and then making a symbolic link. I'm fairly sure this isn't what you need.

---

### Post by geovino on 2007-03-09
This is the only message I got this morning when I go to Synaptic and hit reload:
[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz:](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found

That's probably a server problem that will be fixed at some point. I would have to wait until I install someting else and it comes up when it's finishing the install...



here's a screen shot of the error when synaptic is applying changes...

and after I enter no two times it completes and gives me this error:
E: j2sdk1.4-doc: subprocess post-installation script returned error exit status 1

---

