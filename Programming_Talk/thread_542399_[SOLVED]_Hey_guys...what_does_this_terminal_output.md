---
title: "[SOLVED] Hey guys...what does this terminal output mean?"
date: 2007-09-03
forum: Programming Talk
---

### Post by isaacj87 on 2007-09-03
I'm running the latest version of Avant Window Navigator and I get this terminal output:

```

(awn-applet-activation:7120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(awn-applet-activation:7120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

I have a trash, stacks and taskmanager applets that seem to be running fine...meaning they show up...why I'm I getting this output.

AWN just received python bindings and I only ask it here because I plan on writing an applet in python and the test applet produces a similar output and I'm basing my applet on the test applet that came with the latest revision.

Oh and output from above, those applets aren't written in python. 

But like I said, everything seems to be working correctly, but the output says differently?

---

### Post by Lux Perpetua on 2007-09-03
I get things like that all the time with GTK apps launched from a terminal. I figured it was just sloppy programming, since the programs seem to work anyway.

---

### Post by DoktorSeven on 2007-09-04
Exactly.  With GTK programming, you can be sloppy with certain aspects of the code and GTK will output warning messages like that to tell the programmer.

In general, you can completely ignore them, though.

---

