---
title: "Netflix-desktop help for a poor sap who installed last week's Silverlight update"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by hreichgott on 2013-04-22
Hi,

I have been using the netflix-desktop software from PPA along with wine-compholio and wine-browser-installer.

Last week an update to Microsoft Silverlight broke netflix-desktop.

Many people have posted workarounds that allow you to avoid doing the update in the first place. Unfortunately, I did not know the Silverlight update would break anything and so I foolishly installed it. I now have audio only on my Netflix, no video. Now I need either to get the current version working or to revert to the pre-update version and use one of the suggested workarounds.

Here is the bug on Launchpad with all the workarounds in the comments section
[https://bugs.launchpad.net/netflix-desktop/+bug/1168939](https://bugs.launchpad.net/netflix-desktop/+bug/1168939)

I have tried removing my entire .wine and .wine-browser directories, purging wine, wine-compholio, wine-browser-installer and netflix-desktop, and reinstalling all of the above, with no success.

I am wondering if the wine version of Firefox, which would include the Silverlight update, is hiding somewhere on my system outside of my .wine directory, and I need also to delete it and reinstall? I suspect this because I have noticed there is no Mozilla or Firefox in my Program Files folder under .wine.

Or is there something else I can do?

Edit: the most recent Launchpad comment is
"I've pushed an updated version to the build farm that will disable the Firefox auto-update."
What is a build farm, and how can I get this updated version, after such time as I get the broken version off my system?

thanks
hreichgott

---

### Post by oldos2er on 2013-04-23
Run ```
wine .wine-browser/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
``` go to menus Tools, Options, Advanced, Update tab, and disable automatic updates. Let me know if this works.

---

### Post by hreichgott on 2013-04-24
That worked! Thank you so much.

---

### Post by oldos2er on 2013-04-25
Great! Could you please mark the thread solved? See my signature if you need help doing so.

---

### Post by alex-bingham on 2013-08-14
Sorry to be a complete muppet but what do you mean by Run Code?

Does this need to be done in a terminal?

Sorry for being a bit of a clown.

---

### Post by The Cog on 2013-08-14
Yes. Open a terminal window and paste that command into it. You will need to press enter at the end of it.

Alternatively, I gather from the following instructions that it launghes a GUI program, so rather than entering the command into a terminal, you could press Alt-F2 and paste the command into that prompt. This second method is no good for command-line programs that print their output, but is OK for launching GUI programs. It doesn't leave a command-prompt window open.

---

### Post by alex-bingham on 2013-08-14
This is going to sound really stupid but when I paste this into the Terminal window and hit return it gives me 'No Command Wine found, did you mean:' with a whole buch of options.  Am I missing something?

---

### Post by The Cog on 2013-08-14
Actually, I think that command is wrong. I think he's just launching firefox in wine, and disabling automatic updates in that. If so, I think the command should be:
```
wine .wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```

---

