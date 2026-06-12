---
title: "Learning from TWM"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by sbussy89 on 2008-06-21
I am soon to be working on a window manager for a school project, and I was told to look at TWM to learn about X window programming.  I have a few questions about working with it.  I know that I can download twm through the synaptic package manager, but I have some more questions:

How can I look at the source code for twm?

How can I go about changing the source code for twm, and then running it to see the effects of my changes?

Thank you for any help!

---

### Post by sdennie on 2008-06-21
Try this:

```

mkdir twm
cd twm
apt-get source twm
sudo apt-get build-dep twm

```

You should now a directory called twm-1.0.3.  To configure it type:

```

cd twm-1.0.3
./configure

```

To build it:

```

make

```

The actual code is in the src directory.  And, if you modify twm, you can see your changes by killing your window manager and starting twm.  For example, if you are using gnome without compiz:

```

pkill metacity && twm &

```

Then to get back to metacity:

```

metacity --replace

```

Hope that helps.

---

