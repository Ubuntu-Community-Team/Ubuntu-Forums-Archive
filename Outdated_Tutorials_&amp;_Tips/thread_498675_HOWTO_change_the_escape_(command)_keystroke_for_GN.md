---
title: "HOWTO change the escape (command) keystroke for GNU Screen"
date: 2007-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by rjseagraves on 2007-07-11
One of the great programs every command line user should know about is GNU Screen, the terminal window manager. One small issue that effects some users of Screen is that the default escape key (C-a) is also the "beginning of line" keystroke in Emacs.  This tutorial will explain how to configure the escape key in Screen. Note that the escape key is one of the many configurable parts of Screen.  For a more complete guide, see the Screen man page or [http://gentoo-wiki.com/TIP_Using_screen]("http://gentoo-wiki.com/TIP_Using_screen")  from the Gentoo wiki, from which this tutorial was drawn.

Screen reads configuration from the ~/.screenrc file (the file .screenrc in the users home directory).  To configure the escape key, add the following line to this file (after creating the file, if it does not already exist):

```
escape <escape key><meta key>
```

where <escape key> is the escape key and <meta key> is the meta key (the key for the screen command that sends the escape key to the current shell).  To denote the Control key, use "^".  For example, to set the escape key to C-` (Control-Backtick), and the meta key to ` (Backtick),  add the line

```
escape ^``
```

to the .screenrc file.  When Screen is then run, the escape key will be C-`.

Note: If one want to use the literal characters "^" or "\", you can escape them using "\".  So to set the escape key to C-^ and the meta-key to \\, add

```
escape ^\^\\
```

to the .screenrc file.

---

