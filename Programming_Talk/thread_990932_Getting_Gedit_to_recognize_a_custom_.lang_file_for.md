---
title: "Getting Gedit to recognize a custom .lang file for GtkSourceView"
date: 2008-11-23
forum: Programming Talk
---

### Post by peterswinkels on 2008-11-23
I copied a Yabasic language definition for GtkSourceView 2.0 from some forum and saved it as yabasic.lang in the /usr/share/gtksourceview-2.0/language-specs folder. According to to some users at that forum, GEdit should automatically recognize the new .lang file. I however, can't find the new language definition in the "Highlight Mode" menu.

Some people have suggested simply replacing another .lang file with the custom one. But, this not something I want to do. As far as I understand it, this website ([http://library.gnome.org/devel/gtksourceview-2.0/stable/lang-reference.html](http://library.gnome.org/devel/gtksourceview-2.0/stable/lang-reference.html)) explains how to create a reference to a new .lang file. Unfortunately I can't make any sense of the explanation there.

I tried the following things to solve my problem:
-Reinstalled GEdit. No result.
-Checked the file permissions for Yabasic.lang. These are identical to those of the other lang files.
-Checked for settings that could cause the problem. Found none.
-Searched the Internet. Found no useful information.
-Checked whether the .lang file is corrupt. As far as I can tell it isn't. There is script (check.sh) which apparently verifies the defintions files. It detects Yabasic.lang and doesn't complain about it.

I'm using Ubuntu 8.10 with GNOME 2.24.1 and GEdit 2.24.1. There are other language defintions which I can use that work fine in GEdit btw.

My original thread about this problem at Basic Programming.org: [http://forum.basicprogramming.org/index.php?topic=498.0](http://forum.basicprogramming.org/index.php?topic=498.0)

---

### Post by xingmu on 2008-12-29
Can you post your lang file here?

Also, try running gedit from the terminal.  You should hopefully see some debug messages indicating what the problem is.

---

