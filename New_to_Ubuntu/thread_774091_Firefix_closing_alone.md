---
title: "Firefix closing alone"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-04-29
Firefox closing alone
It tends to do it when I'm the most stressed...
I might been downloading something from MU or checking my email, wandering about anything and just when I'm about to do something... PUF! Firefox close alone and no error, no bug message is given, so I open it again, restore my pages and keep working until it does that damn thing AGAIN!!! Some times it's a real pain in the .... please help? what might be wrong, I have java activated, don't play online games, only downloads and surf a lot...

---

### Post by skymera on 2008-04-29
That happened to me on 8.04.
Are you on 8.04? if so it could be a problem with Firefox 3, try install Firefox 2 and see if it resolves anything.

---

### Post by benste on 2008-04-29
It's the same thing for me, FF3 closed unexpectly without an error mesage when closing a tab which uses gmail.com
The only way to close it without a "crash"- is go to another tab (not gmail) - go back to gmail tab when all tabs has been loaded - close gmail tab.

This can't be th right way or?

Using Ubunut 8.04 (updated since Alpha 5) and firefox Beta5 (Build 2008041514) -> when will I be able to update to FF3 RC1 which is released but not for ubuntu yet?

---

### Post by arashiko28 on 2008-04-29
I don't associated it to FF3, because it happened also when I was on 7.10 with FF2. So for me it's not related whether if its a beta version or not. I think it's a bug either from Firefox or Ubuntu. But can't find a solution.

---

### Post by benste on 2008-04-29
It never happened before with 7.10 on my system this is only since FF3 is installed / i upgraded + this bug is only reproducable on 3 different ubuntu 8.04 system - 2 were upgraded to Alpha 6  (from 7.10) and one was a clean install.

Is there no ubuntu or firefox "hacker" who can reproduce this issue and explain what the "bug" is about? - should we post it into launchpad?

All presons reading this thread who has Gmail and FF3,
please open FF3 go to gmail, and close the tab

OR open a new gmail tab to your existing other tabs, close the gmail tab.

Does FF (Firefox) close there too for you???

---

### Post by arashiko28 on 2008-04-29
NO, no, no... Mine has nothing to do with it. Mine did it a couple of times while on 7.10 after some huge updates, but then I downloaded and installed 8.04 clean install no upgrade. And has nothing to do with gmail. I have been using MU when it happens.

---

### Post by mike555 on 2008-04-29
May be flash related , ads are now using flash and messing things up with firefox ...... you might try the "flash block" ext. for Firefox , it helped me .....

---

### Post by alienexplorers on 2008-04-29
Do you run any add-ons with firefox.  Some of them have been known to cause problems.  Check out this pare to see if any of the ones you use are listed:
[http://kb.mozillazine.org/Problematic_extensions]("http://kb.mozillazine.org/Problematic_extensions")

---

### Post by benste on 2008-04-30
I'm using adblock+ and tried several times to install google toolbar,
+ using ubuntu addon (which was preinstalled)

---

### Post by benste on 2008-04-30
It wasn't Adblock - I deactivated it and the crash was reproduceable

---

### Post by ibutho on 2008-04-30
You could start Firefox from gnome-terminal and when it crashes, take note of the error messages printed in the terminal. These can help you determine what exactly is causes Firefox to crash.

---

### Post by benste on 2008-04-30
```
benste@vaiofe31m:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e150: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e150: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e150: NP_GetValue
GCJ PLUGIN: thread 0x805e150: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e150: NP_GetValue return
GCJ PLUGIN: thread 0x805e150: NP_GetValue
GCJ PLUGIN: thread 0x805e150: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e150: NP_GetValue return
> 
(firefox:14770): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:14770): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

the qouted should be the error - isn't it?

---

### Post by arashiko28 on 2008-04-30
As an addon I've been using downthemall, but again... this problem was present before I used it and it's not related to gmail tabs o not tabbing gmail. Nor toolbars since I don't use them.

---

### Post by ibutho on 2008-04-30
What version of java are you using? I ask because of the error
```
GCJ PLUGIN: thread 0x805e150: NP_GetMIMEDescription
```
If you are using gcj, try using the sun-java6-plugin.

---

### Post by arashiko28 on 2008-04-30
sun-java-6 is the one I have, now that mentioned, there is a lot of flash going on, even if they're banners, they're flash based. But I need pages that are fully designed on flash, so removing it it's not an option. Again, don't get blinded, FF3 it's not the one to blame, I'm sure of it.

---

