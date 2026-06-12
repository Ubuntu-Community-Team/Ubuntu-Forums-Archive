---
title: "Docky acting different on xubuntu than on Mint Cinnamon."
date: 2013-05-07
forum: New to Ubuntu
---

### Post by Cinaed666 on 2013-05-07
Hi, I just migrated from mint linux, and I've always had a very good experience with docky. It's acting a bit weird here, though.
For instance, certain applications will "clone" themselves on the bar, with the clone not having an icon.
I added the shortcut to my home directory to my dock, and tried to open it: resulting in a clone. (Because it has a different title?)
I've never had that on mint, another app that has this behaviour is the terminal.

Also, I'm used to "open a new window" of something in the dock with middle mouse, and scrolling through buttons with multiple windows behind them, but this all doesn't work here?
Why is it acting so different?

---

### Post by Cinaed666 on 2013-05-07
Okay, so I've found a fix: for people interested: it was missing some icons for some reason.
Fix: [FONT=Ubuntu Mono]sudo cp /usr/share/applications/xfce4-terminal.desktop ~/.local/share/applications
[/FONT]
sudo cp /usr/share/applications/Thunar.desktop ~/.local/share/applications

---

### Post by screaminj3sus on 2013-05-07
> **Cinaed666 said:**
> Hi, I just migrated from mint linux, and I've always had a very good experience with docky. It's acting a bit weird here, though.
For instance, certain applications will "clone" themselves on the bar, with the clone not having an icon.
I added the shortcut to my home directory to my dock, and tried to open it: resulting in a clone. (Because it has a different title?)
I've never had that on mint, another app that has this behaviour is the terminal.

Also, I'm used to "open a new window" of something in the dock with middle mouse, and scrolling through buttons with multiple windows behind them, but this all doesn't work here?
Why is it acting so different?

The no icon thing doesn't have anything to do with "clone" issue (separate issues). i've seen both issues, and here's how to work around them:

To fix the no icon do this for the effected apps. copy its .desktop file from /usr/share/applications to /home/yourusername/.local/share/applications/. For example for thunar: cp /usr/share/applications/thunar.desktop /home/yourusername/.local/share/applications/

I don't know why docky has this issue with XFCE (I don't see this problem with cairo-dock, plank, or dockbarx).

For the clone, for some reason certain apps are picky about which icon you pin to the dock, I see this issue with thunar in other dock programs too. to fix it right click the "clone" and pin it to the dock, and un-pin the other one. For me this made it so there was always just one thunar icon on the dock as expected.

EDIT: I see you figured out the no icon issue :), but the fix for the duplicate launchers may still be helpful.

---

### Post by Cinaed666 on 2013-05-08
Thanks for the reply :) What I did was open a fresh copy of thunar instead of using the link to my homedir. Since it defaults to that folder anyways It's alright, and it doesn't produce a clone!

---

