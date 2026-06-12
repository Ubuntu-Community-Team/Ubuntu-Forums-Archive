---
title: "GIMP Toolbox not working-can't click"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by VisionaryVanGogh on 2011-09-21
Hi, I'm a fairly new Ubuntu user, I have 11.04. I loaded up GIMP today and found I couldn't click on any items in my tool box. (but I could in the Layers, Channels, Paths window for some reason) And when I went to save an image, I couldn't click the save button, (but I could still save by pressing enter. I tried resetting preferences, doing a complete reinstall, and I'm still having this problem. If I could get any help, I'd appreciate it, thanks.

---

### Post by MG&amp;TL on 2011-09-21
Have you used GIMP before? I find it's not very user-friendly on the pointy-clicky front.

Could you attach a screenshot?

Also run GIMP from a terminal:

```
gimp
```

And any interesting error message should show up there.

---

### Post by VisionaryVanGogh on 2011-09-22
> **MG&TL said:**
> Have you used GIMP before? I find it's not very user-friendly on the pointy-clicky front.

Could you attach a screenshot?

Also run GIMP from a terminal:

```
gimp
```

And any interesting error message should show up there.

(gimp:1968): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0

Yes, I've used GIMP before, both on Windows, and on my new Ubuntu system. I'm used to the interface. I'm not a GIMP expert, but I know how to use it. The problem is that I can't click on any of the buttons on the tool box. This problem, as far as I know, occurred yesterday. It all of a sudden became broken. Anyway, the error above is what appeared when I ran GIMP through the terminal.

---

### Post by VisionaryVanGogh on 2011-09-22
Also, while using the program....(I was able to capture my screenshot, then crop the image in GIMP, even though I couldn't select the tools by clicking, I could still use the shortcuts) these errors also occurred in the terminal:

(gimp:1968): LIBDBUSMENU-GTK-WARNING **: Could not parse 'scan cover test.jpeg': Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(gimp:1968): GLib-GObject-WARNING **: invalid cast from `GimpView' to `GtkImage'

(gimp:1968): Gimp-Widgets-WARNING **: gimp_dialog_factory_dispose: stale non-toplevel entries in factory->open_dialogs

---

### Post by MG&amp;TL on 2011-09-22
How did you get GIMP? It would seem there is an error in the source (well duh!). The major reason I can see as to why you cannot click on the GIMP tools is that the window is not selected, or "active".

Try cycling through the windows open with Alt-TAB and see whether you can select it so that at least one of the window buttons become orange/grey. EDIT: Scratch that, just noticed the terminal.

Google search does not pull anything up. I think the problem is the mouse. Most programs will generate warnings, I find (in my programs at least) that it's "functional programming" that does not catch EVERY exception.

Try:

```
man gimp
```

and then see if there is a --verbose or --debug mode.

I can't really help, I'm just providing debugging procedures.

---

### Post by MG&amp;TL on 2011-09-22
And did you remove preferences, then reinstall? Or one of those at a time?

To do both at once, use:

```
sudo apt-get remove --purge gimp
```

---

### Post by VisionaryVanGogh on 2011-09-22
> **MG&TL said:**
> And did you remove preferences, then reinstall? Or one of those at a time?

To do both at once, use:

```
sudo apt-get remove --purge gimp
```

I tried that, and reinstalling it through the Synaptic Package Manager, and the same error is still occurring. But yeah, thanks for the help anyway. Hopefully someone else can help me out.

---

### Post by MG&amp;TL on 2011-09-22
File a bug. Hopefully it will get fixed. Well, have fun. ;)

---

### Post by VisionaryVanGogh on 2011-09-22
> **MG&TL said:**
> File a bug. Hopefully it will get fixed. Well, have fun. ;)

I filed it to bugzilla.gnome.org. That's where I should have sent it, right?

---

### Post by MG&amp;TL on 2011-09-22
I personally file bugs to launchpad.net:

[https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

But you may need to create an account. The devs seem to read launchpad. Come to think of it, *I* read launchpad-and I'm not  a developer by any stretch.

---

