---
title: "How to discover python scribtability of GNOME apps?"
date: 2006-01-30
forum: Programming Talk
---

### Post by moephan on 2006-01-30
Hi,

In AppleScript in Mac OS 9, I could open any app with the AppleScript "dictionary" (I think that's what it was called, it was a while ago). Is there any similar facility in GNOME? I have been led to believe that many GNOME apps are scriptable with Python, but I can't figure out how to discover which ones I can script and how.

Cheers, Rick

---

### Post by Van_Gogh on 2006-01-30
A lot of the apps are at least partly scriptable from the command line. For some application you could do
```

appName --help

```
or
```

appName -?

```
or whatever that app requires to a help message. You'll probably find some command line parameter that can control the app. Then you could create a pipe to Python using the subprocess module.

There you have it, though maybe not exactly what you asked for. Some apps have dedicated Python binding though, for example Gstreamer.

---

### Post by moephan on 2006-01-30
It is helpful to know that the normal way of scripting is via the command line, and that's easy to do from Python. It sounds like having python bindings is the exception, not rule though, and there is no way to command Python to reveal the bindings that do exist.

Thanks.

Cheers, Rick

---

### Post by Van_Gogh on 2006-01-30
Yeah, that's often the wayu it is. If you want to script a specific app through Python, you'd probably either go to the app's home page or to synaptic to see if you can find some module. If you don't find anything, you use subprocess to access the command line.

If you want to be productive in Python you could of course yourself write a module that wraps the calls to subprocess and then release it as a module. That would save others the hassle of setting up the subprocess pipes...

---

### Post by doclivingston on 2006-01-30
Some Gnome applications can also be controlled via DBus and/or Bonobo.

---

