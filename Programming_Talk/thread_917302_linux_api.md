---
title: "linux api"
date: 2008-09-11
forum: Programming Talk
---

### Post by pavel989 on 2008-09-11
windows has win32 (windows.h) but what does linux have? like is there an api to get mouse motions nd stuffs?

---

### Post by forger on 2008-09-11
Usually the linux applications take arguments to modify some stuff for them once you run them.

What do you specifically want to do?

Welcome to bash scripting :)
```

echo -e "Moo\n\nmeow"
echo -e "Moo\n\nmeow\n\nbark" | grep bark
zenity --info --width 150 --height 150 --text "Yo yo yo"

```
[Perl]("http://www.perl.org") and [python]("http://www.python.org") are also good.

Some say gambas is good too: [http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)
```
sudo apt-get install gambas2 gambas2-ide gambas2-doc
```
If you're still looking for mouse movements, maybe python-dogtail will help:
[http://www.redhat.com/magazine/020jun06/features/dogtail/](http://www.redhat.com/magazine/020jun06/features/dogtail/)
```
sudo apt-get install python-dogtail
```

---

### Post by LaRoza on 2008-09-11
> **pavel989 said:**
> windows has win32 (windows.h) but what does linux have? like is there an api to get mouse motions nd stuffs?

Windows is closed source, and there are no options.

Linux has a lot more. For mouse motions and "stuffs", you can use many API's. Probably on X I think or whatever environment you are using.

So you have to be more specific. Linux is a kernel, and I don't think you are looking for such programming.

---

### Post by pavel989 on 2008-09-11
yea didnt think about that. So, no matter what window system i use, there should be an api package in the repos?

this is for c++ btw

---

### Post by forger on 2008-09-12
> **pavel989 said:**
> yea didnt think about that. So, no matter what window system i use, there should be an api package in the repos?
this is for c++ btw

I think so, yes - usually the apis and development packages have "-dev" at the end of the package name (correct me if I'm wrong).
For example, python-gtk2 is the package with the binary files, python-gtk2-dev contains the wrappers for building/compiling applications

For C++, I'm not sure, but I think it's on of these:
> libglibmm-2.4-1c2a - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dbg - C++ wrapper for the GLib toolkit (debug symbols)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libglibmm-2.4-doc - C++ wrapper for the GLib toolkit (documentation)
libgtkmm-2.4-1c2a - C++ wrappers for GTK+ 2.4 (shared libraries)
libgtkmm-2.4-dbg - C++ wrappers for GTK+ 2.4 (debug symbols)
libgtkmm-2.4-dev - C++ wrappers for GTK+ 2.4 (development files)
libgtkmm-2.4-doc - C++ wrappers for GTK+ 2.4 (documentation)


---

### Post by pmasiar on 2008-09-12
> **pavel989 said:**
> windows has win32 (windows.h) but what does linux have? like is there an api to get mouse motions nd stuffs?

Linux the kernel is not concerned abut GUI at all. Whole GNU/Linux stack is modular, and except for the kernel you have multiple solutions in each layer. Check your windows manager (likely X) or desktop API.

---

