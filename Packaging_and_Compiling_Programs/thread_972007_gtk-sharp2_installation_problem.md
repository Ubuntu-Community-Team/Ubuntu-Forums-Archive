---
title: "gtk-sharp2 installation problem"
date: 2008-11-05
forum: Packaging and Compiling Programs
---

### Post by majkinetor on 2008-11-05
Hello there.

I installed monodevelop and created simple hello world gtk# project. 
On Ubuntu it works fine. When I copy it to Windows Vista it reports it is msising gtk-sharp 2.12 assembly. I found that gtk runtime installer for windows added 2.8 and 1.0 versions of mentioned assembly.

I returned to Ubuntu system, and in project options in monodevelop under GTK# Settings I found that under "Target GTK version" I can only choose 2.12 version. Besides this combobox there is sentence "(or upper)" which means that project should run on v2.8 but somehow it doesnt.

Anyway, some dude reported that i should install gtk# addin from monodevelop repository. Monodevelop couldn't connect for some reason to its repositories (although I can connect to the same address using browser) so I used apt-cache search ^gtk to see what I have and finally saw gtk-sharp2 package which seemed like a way to go :)

However, apt-get install reports I have some unmet dependencies. Following them I finish on:

```
The following packages have unmet dependencies:
       libvte4: Depends: libvte-common (= 1:0.12.2-5) but 1:0.16.13-1ubuntu1 is to be installed
E: Broken packages

$ sudo apt-get install libvte-common
libvte-common is already the newest version.

```

I see this kind of message quite often and I absolutely don't know what to do about it so I came here for advice. Can't I have multiple versions of the same library on the system?

Any help related to my intial problem or the last one would be appreciated.

Thanks in advance.

---

