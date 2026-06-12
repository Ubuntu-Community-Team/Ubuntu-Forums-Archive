---
title: "Log out button in gDesklets Starterbar"
date: 2005-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Nonno Bassotto on 2005-07-08
I've recently installed gDesklets, and found it really impressive. :razz:  Now my desktop features some monitor and Starterbar, the MacOS-like bar to call programs.

I wish I could add a button to invoke the logout dialog, but I don't know which command I may use (I mean, I know of shutdown and reboot, but I'm looking for the gnome dialog). This button can be put in the gnome panel, but I don't know if it can be called like other applications.
Thank you
Andrea

I edit the post since I don't know if I've been confusing. The point is not gDesklets. I'm looking for a terminal command to invoke the logout dialog.

---

### Post by mtron on 2005-07-09
Hi Nonno! 

Create a new Launcher with the following parameters: 

Name: Log out
Command: gnome-session-save --kill
Type: Application
Run In Terminal: unchecked

---

### Post by gammyhand on 2005-07-10
[QUOTE=mtron]Hi Nonno! 

Create a new Launcher with the following parameters: 

Name: Log out
Command: gnome-session-save --kill
Type: Application
Run In Terminal: unchecked[/QUOTE]
 I hope this question is allowed as it's kind of relevant. Is there a funky SVG logout icon floating around?

---

### Post by Nonno Bassotto on 2005-07-10
Thank you, it was just was I was looking for. As for the icon, I didn't find one yet, so I us a nonscalable one    :-|  . I hope to find something fine in Noia style soon.

Andrea

---

### Post by Nonno Bassotto on 2005-07-11
Now it works. The only fastidious thing is that when the logout dialog is called, the icon is still bouncing. So if I exit, i receive a notice that gDesklets was terminated while running. I was wondering if the dialog could also be delayed, so that the icon has finished bouncing. I tried something like

sleep 3; gnome-session-save --kill

but the (unexpected) result is that:
1. the icon too is stopped for 3 seconds and
2. the second command is ignored.
Any suggestion for this?
Thank you again

Andrea

EDIT: Ehmmm.. This happened twice, now it doesn't happen anymore. I don't know why, but now it works fine.

---

