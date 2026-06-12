---
title: "REAL:LY Quick and Easy Title Bar Button Side Switching"
date: 2010-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by ALIENDUDE5300 on 2010-03-09
A **ton** of users are dissatisfied with the decision to change the buttons on the title bar, however, it's *incredibly* easy to change back and forth between the old (Karmic) look, and the new (Lucid Alpha) look. You do *not* have to be on Lucid to test out the new look. These commands work fine on Karmic and (probably) older, although I have only tested them on Karmic and Lucid. 

The fix is *ridiculously* simple. First, open up a terminal.

If you want your Title Bar icons to look like they do in Karmic (**RIGHT** side), copy and paste the following code into the Terminal and press Enter:
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

If you want your Title Bar icons to look like they do in Lucid Alpha (**LEFT** side), copy and paste the following code into the Terminal and press Enter:
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "maximize,minimize,close:"
```

It *really* is *that* easy. You're done! Enjoy! ;)

---

### Post by bu3askoor on 2010-03-10
i got this strange error:

Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

I am on ubuntu 9.10

---

### Post by rawny on 2010-03-10
Cool tip, thanks! :)

It's worth mentioning that on Karmic, your command will get rid of the application menu/icon (at the left end of the titlebar), which I believe is there by default.

To prevent that, try this instead:
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "menu:minimize,maximize,close"
```I don't know how this will behave on Lucid though, I only have Karmic.

---

### Post by Mervaka on 2010-03-24
works a treat, cheers!

rawny: the menu: bit works fine too.

---

### Post by Naggobot on 2010-05-01
Thank you!

Worked like a charm

I bookmarked this on the post day and upgraded to day :)

---

