---
title: "GUI for CLI"
date: 2007-12-08
forum: Programming Talk
---

### Post by AJB2K3 on 2007-12-08
I need to build a GUI for a cli tool I use but I have no idea were to star.

The gui need to have
 a drop down list which shows the hardware type and will pass the value of the patch.file for the command to run.
A file open dialog that list files that need patching
and a button with the label Patch.

It will need to run the cli commaned that looks something like this.
```
CLI patch.file filetopatch
```

Can someone tell me how to do this or point to a tutorial that does this?
**If I made a mess trying to explain this its because I don't know anything about programming.**

---

### Post by ekravche on 2007-12-08
You can give java a chance. Write once run anywhere... If you are interested in doing this in java you'll need to use swing or AWT.

---

### Post by pmasiar on 2007-12-08
> **AJB2K3 said:**
>  I don't know anything about programming.

So maybe you should start at basics, and not at advanced topics like GUI. You need to learn plain programming first. Did you decided what language?

---

### Post by AJB2K3 on 2007-12-08
I've got Kdevelop installed (as standered?)
I once made a basic do nothing app in devcpp before but that was along time ago.

---

### Post by MicahCarrick on 2007-12-08
My 2 cents, if you're coming from little-no experience, you might want to tinker around with Python command line basics first. Just find a python tutorial. Then move into GUIs using GTK and python (PyGTK). As you get better acquainted with programming, learning a bit of C would be beneficial.

---

### Post by pmasiar on 2007-12-08
If you want to go with Python (which I highly recommend),  wiki in my sig has links to online books and training tasks.

---

### Post by AJB2K3 on 2007-12-10
Dumb response but ..

How does all that help me?

I already have the pre compiled program I just want a simple gui that will launch the program with parameters I pass it from the gui.

---

### Post by aaaantoine on 2007-12-10
> **AJB2K3 said:**
> Dumb response but ..

How does all that help me?

I already have the pre compiled program I just want a simple gui that will launch the program with parameters I pass it from the gui.

You could use Glade to create the interface using a GUI instead of programmatically, but it would still help to understand how GTK works.

Or you could probably use Kdevelop, except I know nothing about that program and what it's capable of.  Is this application targeted for Gnome or for KDE?

Once you have your interface, you will still need to fill in the necessary code that will launch the CLI application based on the user's manipulation of the interface.

---

