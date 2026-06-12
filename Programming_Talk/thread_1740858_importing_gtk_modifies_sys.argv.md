---
title: "importing gtk modifies sys.argv"
date: 2011-04-27
forum: Programming Talk
---

### Post by Flimm on 2011-04-27
I spent a while trying to understand why some command-line options were swallowed seemingly randomly in my Python script. At first I thought it was due to a bug in argparse, but it wasn't.

I finally tracked it down to this:
[php]
>>> sys.argv
['./example.py', 'command', '--name', '--another-option', '--third-option']
>>> import gtk
>>> sys.argv
['./example.py', 'command', '--third-option']
[/php]

It looks like gtk automatically consumes --name, --screen, --display, --sync, --class and other options described in gtk-options man page. So don't blame argparse or getopts. Blame pygtk (see [bug report](https://bugzilla.gnome.org/show_bug.cgi?id=648801)).

I thought I'd share, if only to remind people of a good Python practise: **importing a module should never have side-effects**.

If your module does have side-effects (such as monkey-patching), make this explicit by offering an install function. This code is very clear:[php]import modulename
modulename.install()[/php]

---

