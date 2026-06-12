---
title: "bash script?"
date: 2009-02-09
forum: Programming Talk
---

### Post by ussndmac on 2009-02-09
Hi,

When I shutdown my home net, I can either step up to my firewall/nat box, log in, and shutdown.

Or, I ssh into it from whatever machine I happen to be using and do a shutdown.

This is all fine for me, but, when I not around and my wife wants to shutdown, she's mystified.

So, I think I want to write a script that can be run on her machine that ssh's into the firewall and shuts down.

I'm pretty sure I can get a script to run when a local terminal window is activated, but how do I enter commands to ssh, and subsequently to the firewall box?

Regards,
Mac

---

### Post by stroyan on 2009-02-09
If you have a ssh login to your firewall box that does not require a password then you can use "ssh hostname command" like "ssh firewall shutdown -h 0".  If you need a more complicated dialog such as entering a password then you could use the expect command.  It is a scripting language specifically designed for carrying on a predefined dialog with a command.

If you are using gnome then you can create an icon in the top panel for a shell script or other command using the "Add to panel" right mouse button menu option and the "Custom application launcher" item.

Don't make it too easy to do something unintentionally.
You could use the zenity command to show a confirmation dialog.
```
#!/bin/bash
if zenity --question --text "Shutdown the network?"
then
 ssh firewall shutdown -h 0
fi

```

---

