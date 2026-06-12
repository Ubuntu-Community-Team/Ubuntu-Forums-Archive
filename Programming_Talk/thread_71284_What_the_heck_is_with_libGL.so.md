---
title: "What the heck is with libGL.so ???"
date: 2005-10-02
forum: Programming Talk
---

### Post by kudu on 2005-10-02
Trying to build an OpenGL program using both gcc at the terminal and Anjuta but no matter what I do ld can't find libGL. So I looked in /usr/X11R6/lib to see what is what and when I right click on libGL.so to check out it's properties, it disappears!! Reinstall mesa stuff, disappears. Ad infinitum. What gives ??

I have libGL.a but it doesn't seem to make the linker happy. Please HELP!

kudu

---

### Post by Oberjaeger on 2005-10-03
A file dissapearing like that in nautilus can happen when it's a symbolic link to a file that doesn't exist. Try running 'ls -l /usr/X11R6/lib' in a terminal to see where libGL.so is pointing to. Probably something like /usr/X11Rg/lib/libGL.so.1 .

The real libGL will probably have a similar name, create the working link by issuing the command

ln -s /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so

In your case the actual name may vary slightly, libGL.so.1.1 for example.

---

### Post by kudu on 2005-10-03
This command doesn't seem to do anything, says the file already exists.

"ln -s /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so"

Is this correct ? Or maybe it's reversed ?

When I list the files in X11R6/lib the libGL.so sym link is highlighted red for some reason.

The case of the disappearing sym links continues...

kudu

---

### Post by kudu on 2005-10-03
I'm wondering do I have to compile mesa even though I installed it using synaptic ?? Is that why I have a bunch of symlinks to nonexistent files ?

How do you set up for OpenGL ?

Questions, questions, questions.

kudu

---

### Post by Oberjaeger on 2005-10-04
Sorry, I forgot to mention that you'll have to delete the broken link first as ln wont overwrite an existing file without the force (-f) option.

  rm /usr/X11R6/lib/libGL.so.1.2
  ln -s /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so

---

### Post by Lux Perpetua on 2005-10-05
[QUOTE=Oberjaeger]Sorry, I forgot to mention that you'll have to delete the broken link first as ln wont overwrite an existing file without the force (-f) option.
rm /usr/X11R6/lib/libGL.so.1.2
ln -s /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so[/QUOTE]
Hold on, there, partner! Your instructions will delete libGL.so.1.2 and create a dead link! I think you meant this:
> rm **/usr/X11R6/lib/libGL.so**
ln -s /usr/X11R6/lib/libGL.so.1.2 /usr/X11R6/lib/libGL.so
kudu - a highlighted and red file name from ls probably means it's a dead link.

---

### Post by Oberjaeger on 2005-10-05
[QUOTE=Lux Perpetua]Hold on, there, partner! Your instructions will delete libGL.so.1.2 and create a dead link! I think you meant this:[/QUOTE]

That's what I get for posting at 3am.:???:

---

### Post by drgreborn on 2005-10-05
Just a quick qustion. When I try to do ./configure it stats it can't find my GL is this a similar problem? Sorry to butt in like this.

---

