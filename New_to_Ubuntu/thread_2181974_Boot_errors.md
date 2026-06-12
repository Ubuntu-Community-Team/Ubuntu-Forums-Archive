---
title: "Boot errors"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by heroquestelf on 2013-10-19
I just updated to 13.10 and I'm getting errors... only I can't process the errors because I don't know what they are. They appear when I first boot up and they're on the screen less than 10 seconds before they disappear.

I tried going to the /var/log directory and pulling up the the various log files, specifically the boot.log file and the error message that displays when my system boots is not there... or I don't understand what I'm looking for. The boot error says something about there being some kind of mismatch and my boot.log doesn't have anything resembling that terminology. 

Suggestions?

---

### Post by heir4c on 2013-10-19
Is that when you are on the desktop or before?
And can you read the errors and post them here?
In /var/log there are many logs. Like the kernel.log or the one for xorg. 
You can post them here  if you want. (Use the #  (code tags) to put it here)

---

### Post by heroquestelf on 2013-10-19
Can I read them and post them here? In a word, "no". The only way I could do that is if I rebooted the computer eight or nine times so that I could write down one or two words every time it booted up... and I'd *reeeeeeeeally* rather not do it that way. That is the nature of the problem to begin with.

To your first question, it is before the "Ubuntu" logo even pops up on the screen, so *WAY* before the desktop system fully boots.

---

### Post by steeldriver on 2013-10-19
... might be easier to do something like

```
sudo grep --color -EIri '[m]is-?match' /var/log 2>/dev/null
```

---

