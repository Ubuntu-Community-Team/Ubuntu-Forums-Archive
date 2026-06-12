---
title: "Excessive HDD Activity"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by corowakid on 2008-08-04
Hi. I have Ubuntu 8.04 installed on a C2D dual-booted with GRUB with Win XP. Instal went OK, actually I upgraded from v7.10 via the Update option.

Things work OK, but I've noticed that after booting, sometimes within minutes, sometimes longer, the HDD activity light shows red constantly. When I run Firefox the screen darkens, and the Firefox pages stop loading. The screen then lightens, and normal activity resumes. This HDD activity can last 10 minutes.

A possible clue is when I do Updates - I get a message that only a Partial Update can be done, due to errors in previous updates (?). After loading the updates I then request another update check, and am told there's no further updates availble, yet when I next request Updates I get the same error message. Could this be connected to the screen darken/lighten and HDD light activity?

I can't figure out a way to correct this situation, mainly because I don't understand what might be causing the problem. Any help/advice really appreciated.

---

### Post by Elfy on 2008-08-04
It might be tracker - I turned it off myself, top panel on default installation - you can configure it there.

With regard to firefox I had the same problem and ended up using opera instead.

---

### Post by AdamWood on 2008-08-04
I've got a couple of suggestions:

1) I agree with forestpixie, tracker can cause problems to disable it go to:
System -> Preferences -> Search and Indexing
Make sure "enable indexing" and "enable watching" are disabled.

2) Since you mention the updates you could try a manual fix of broken packages:
press ALT+F2 and type gnome-terminal in the field, then press run.
In the window that appears you want to type:
```
sudo apt-get install -f
```
You'll be asked for your password so, like with any forum advice, you should check out what this command does yourself before running it.
It's possible you'll get some error about [FONT="Courier New"]dpkg[/FONT] not running properly, if you copy and paste any response to that command here it'll will probably help someone to fix it.

3) I guess there could be some issue with a swap partition but you should try the other things first.

---

### Post by corowakid on 2008-08-05
> **AdamWood said:**
> I've got a couple of suggestions:

1) I agree with forestpixie, tracker can cause problems to disable it go to:
System -> Preferences -> Search and Indexing
Make sure "enable indexing" and "enable watching" are disabled.

2) Since you mention the updates you could try a manual fix of broken packages:
press ALT+F2 and type gnome-terminal in the field, then press run.
In the window that appears you want to type:
```
sudo apt-get install -f
```
You'll be asked for your password so, like with any forum advice, you should check out what this command does yourself before running it.
It's possible you'll get some error about [FONT="Courier New"]dpkg[/FONT] not running properly, if you copy and paste any response to that command here it'll will probably help someone to fix it.

3) I guess there could be some issue with a swap partition but you should try the other things first.

Thanks for that - here's a screenshot (apologies if its not right format):

Just as I type this, the problem occurred again - so I hope someone can give me a clue as to what's wrong.

---

### Post by cdtech on 2008-08-05
Try running in a terminal "sudo apt-get autoremove && sudo apt-get clean"

---

### Post by AdamWood on 2008-08-05
Did you try disabling the file indexing?

The screenshot shows there are 4 upgrades available so maybe we should go ahead and try to get those installed. in the same way as before can you try this command:
```

sudo apt-get upgrade

```

---

