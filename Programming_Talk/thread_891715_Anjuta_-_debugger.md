---
title: "Anjuta - debugger"
date: 2008-08-16
forum: Programming Talk
---

### Post by cork.kyle on 2008-08-16
Hi All -

I'm new to GNU/Linux. Have just installed Ubuntu 8.04 LTS and used the Synaptic Package Manager to download Anjuta 2.4.1.

I'm having trouble figuring out how to set breakpoints.

I don't see a "debug" menu - the manual says there should be one. Do you know how I enable this menu? Or is there something else I need to install to enable debugging?

The Anjuta-specific packages that I have installed are:
  anjuta
  anjuta-common
  anjuta-dbg
  anjuta-dev

Thanks!

---

### Post by cork.kyle on 2008-08-16
Okay, I figured it out.

Once you install Anjuta, you need to enable the debugger first.
  - From the main menu, select Edit/Preferences.
  - Choose "General" in the left pane.
  - Select the "installed plugins" tab.
  - Check the checkbox in front of "Debugger - Debug Manager Plugin".

I was confused because I assumed that the debugger would be automatically enabled for Anjuta. When discussing debugging in the Anjuta manual, it would be nice if they'd insert a quick note for newbies like myself stating how to turn on debugging and not start by saying "click on the debug menu" when the debug menu doesn't exist.

---

