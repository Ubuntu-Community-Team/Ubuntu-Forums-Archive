---
title: "Help with Glade-3 error messages."
date: 2010-01-30
forum: Programming Talk
---

### Post by towheedm on 2010-01-30
I'm in the process of learning to program under Linux using Python, PyGTK and GTK+.  After reading through some other treads I decided to install Glade3 and Gazpacho.  They were installed from the repos.

I only prior programming experience is VisualBasic and VBA under MSWin.  After reading much of the tutorials around for GTK+ I've just about grasp the concepts of containers in GTK.

My problem is that when I launch Glade3 from a terminal I get the following errors:

```
towheed@ga1a4ch:~$ glade-3

(glade-3:18578): GLib-WARNING **: g_set_prgname() called multiple times
GladeUI-Message: No displayable values for property GtkScaleButton::size
GladeUI-Message: No displayable values for property GtkImage::icon-size

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-sizegroup' was found for object class 'GtkSizeGroup'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-accelgroup' was found for object class 'GtkAccelGroup'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-adjustment' was found for object class 'GtkAdjustment'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-uimanager' was found for object class 'GtkUIManager'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-treemodelfilter' was found for object class 'GtkTreeModelFilter'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-treemodelsort' was found for object class 'GtkTreeModelSort'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-treeselection' was found for object class 'GtkTreeSelection'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-statusicon' was found for object class 'GtkStatusIcon'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-textbuffer' was found for object class 'GtkTextBuffer'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-texttag' was found for object class 'GtkTextTag'.
GladeUI-Message: No displayable values for property GtkTextTag::direction

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-texttagtable' was found for object class 'GtkTextTagTable'.

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-gtk-filefilter' was found for object class 'GtkFileFilter'.
GladeUI-Message: 1 missing displayable value for GnomeDateEdit::dateedit-flags
GladeUI-Message: No displayable values for property GnomeIconList::selection-mode

(glade-3:18578): GladeUI-WARNING **: No icon named 'widget-anjuta-vcsstatus' was found for object class 'AnjutaVcsStatusTreeView'.

(glade-3:18578): GladeUI-CRITICAL **: Unable to load module 'vte' from any search paths

(glade-3:18578): GladeUI-WARNING **: Failed to load external library 'vte'

(glade-3:18578): GladeUI-WARNING **: We could not find the symbol "vte_terminal_get_type"

(glade-3:18578): GladeUI-WARNING **: Could not get the type from "VteTerminal"

(glade-3:18578): GladeUI-WARNING **: Failed to load the GType for 'VteTerminal'

(glade-3:18578): GladeUI-WARNING **: Tried to include undefined widget class 'VteTerminal' in a widget group

```Also, the following error after launcing Gazpacho:

```
towheed@ga1a4ch:~$ gazpacho 
WARNING: GTK+ and GObject modules are not loaded from the same prefix

```Should I be concerned about these error messages and if so , how do I correct them?

Thanks for all your help.

---

### Post by lookitseman on 2010-02-16
I'm in the same boat.

Another symptom is that when I place a button on a "Window" widget, and try to make it a stock button (General Tab > Configure Button Content > Stock Button) the button icon fails to show up.

Hope we can get this ironed out soon.

---

### Post by towheedm on 2010-02-16
Yes, the same problem here.  Noticed it while following a tutorial.  I think perhaps the problem is in the $PATH variable.  I'm trying to find the directory that has these images and then I'll include it in my PATH.

Please post back if you find a solution.

BTW, I thought this was a programmers forum.  How come no one can answer this question?

---

### Post by lookitseman on 2010-02-17
> **towheedm said:**
> BTW, I thought this was a programmers forum.  How come no one can answer this question?

This is a community-based forum, so while this community is here to help one-another, they may not always be able to help.  The more common and universally reproducible a problem is, the more likely they'll be able to help.  If the problem is unique to you and I, the community may not be of much help...however once we've solved this problem, our notes on how to solve it will be available forever, in order to help anyone else who has a similar issue.

If I do figure it out, I'll be sure to post it here, and please do the same if you figure it out.

---

### Post by oldfred on 2010-02-17
I have been using glade off and on but launching with the app menu and I saw no messages. I just tried using terminal and I did see those error messages. Whatever I am doing in glade it must not use anything related to the messages.

The only issue I had with the latest glade in Karmic is the initial load of a file has some boxes in the wrong orientation even though they worked in my python app. All I had to do was change the orientation and they still worked.

---

### Post by towheedm on 2010-02-18
> **lookitseman said:**
> This is a community-based forum, so while this community is here to help one-another, they may not always be able to help.  The more common and universally reproducible a problem is, the more likely they'll be able to help.  If the problem is unique to you and I, the community may not be of much help...however once we've solved this problem, our notes on how to solve it will be available forever, in order to help anyone else who has a similar issue.

If I do figure it out, I'll be sure to post it here, and please do the same if you figure it out.

Yes, I understand it's a community based forum, but this problem is not specific to just you and I.  I have seen other post on other forums where the same problems were mentioned.  Can't remember the URL's at this time though.

---

