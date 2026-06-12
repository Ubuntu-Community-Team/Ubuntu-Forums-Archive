---
title: "How to prevent dialog boxes from stealing focus?"
date: 2018-02-21
forum: New to Ubuntu
---

### Post by wrybread on 2018-02-21
I've got a an old Asteroids arcade cabinet converted to a MAME box, meaning it's used to play classic video games. Looks great, and convincingly retro, but if I leave it alone for a few days some dialog box will usually appear asking for a wifi password (it's at the edge of the wifi range), or telling me about something that abnormally terminated, or a system update, etc. It's not the end of the world, but it's annoying, and no game will run until someone takes out a keyboard and puts focus back on the MAME menu, which some people who use the machine don't know how to do. 

The machine is running Lubuntu (Ubuntu 17.10 with Openbox). I'm not married to Openbox as a window manager. 

Can anyone think of a way to either make the dialog boxes not steal focus, or make them appear in some other way, or to make MAME be always on top?

Thanks for any help.

---

### Post by wrybread on 2018-02-22
I made a little bit of progress. From googling, I found that adding these lines to the <applications> section of ~/.config/openbox/lubuntu-rc.xml makes a window on top of others:

<application class="Attract-Mode" name="attract" type="normal">
  <layer>above</layer>
</application>

This is an improvement, the dialog windows no longer appear above the Attract Mode MAME window. However, the MAME games becomes frozen. There's still sound, but they stop updating video until I kill the process and then dismiss the dialog window.

Hmm.

Incidentally I found a handy way to test it. From another machine, run:

ssh USERNAME@SERVERNAME zenity --error --title "testing" --text "test" --display :0

That will show a dialog box, provoking the error.

---

