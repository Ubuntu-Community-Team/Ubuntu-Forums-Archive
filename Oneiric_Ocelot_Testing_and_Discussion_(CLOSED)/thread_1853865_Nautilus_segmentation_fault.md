---
title: "Nautilus segmentation fault"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-10-03
Segmentation fault with nautilus-open-terminal extension installed 

```
luca@tower:~$ nautilus
** (nautilus:1832): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

(nautilus:1832): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed

(nautilus:1832): Gtk-CRITICAL **: gtk_action_set_visible: assertion `GTK_IS_ACTION (action)' failed
Errore di segmentazione

```

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/865194)

---

### Post by dino99 on 2011-10-03
just installed this package for testing. I'm surprised to see installation comment: delayed built («*triggers*») for «*gconf2*»...

hm, still using gconf instead of gsetting/dconf ?

i dont get this issue (i386) on my system.

---

### Post by lucazade on 2011-10-03
> **dino99 said:**
> just installed this package for testing. I'm surprised to see installation comment: delayed built («*triggers*») for «*gconf2*»...

hm, still using gconf instead of gsetting/dconf ?

i dont get this issue (i386) on my system.

I was surprised as well.. i just noticed the gconf messages during uninstall.
I was able to replicate on 2 different machines.. what is strange that the only update i made today was about zeitgeist and gsd..

---

### Post by sgage on 2011-10-03
I am getting a segfault when I try to view the "extra pane". Open-in-terminal works for me, though.

[Edit: I am getting a segfault when I try to do anything! Except, I can right click on a directory, and open-in-terminal works fine. But as soon as I try to open a directory, or view the extra pane, segfault.]

---

### Post by mc4man on 2011-10-03
will have to try those updates.. (did a fresh 09/02 install last night - my previous was losing wireless in nm-applet constantly, so did the new one so dumped nm for wicd

typically here I'd only see the "Initializing .." when using gksudo nautilus from a terminal which I hardly do anyway
(either use run or the 'Open as Admin..'

I gather you've tried a full restart?

---

### Post by lucazade on 2011-10-03
thanks for the feedbacks guys.

yes.. i've tried a full restart and the issue is persistent.
only removing the open-terminal extension seems to solve or mitigate the issue but maybe it is just a case that doesn't crash.

---

### Post by mc4man on 2011-10-03
Curious - with the ext. installed can you run gksudo nautilus from terminal without a crash?

---

### Post by Bowmore on 2011-10-03
There's one new bug causing nautilus segmentation fault.
[https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/865115](https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/865115)

If you have nautilus-open-terminal installed remove it temporarilly until that bug is fixed.

---

### Post by dino99 on 2011-10-03
> **lucazade said:**
> thanks for the feedbacks guys.

yes.. i've tried a full restart and the issue is persistent.
only removing the open-terminal extension seems to solve or mitigate the issue but maybe it is just a case that doesn't crash.

maybe a conflict with third repo package(s), i'm using only genuine ones now.

---

### Post by lucazade on 2011-10-03
> **mc4man said:**
> Curious - with the ext. installed can you run gksudo nautilus from terminal without a crash?

yes and it works well, odd.

---

### Post by lucazade on 2011-10-03
> **Bowmore said:**
> There's one new bug causing nautilus segmentation fault.
[https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/865115](https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/865115)

If you have nautilus-open-terminal installed remove it temporarilly until that bug is fixed.

thanks for pointing this out.. seems the same bug. subscribed

---

### Post by H3g3m0n on 2011-10-05
I'm also getting this error. I notice that the open terminal extension had an update recently but it didn't help.

I was wondering if it would be possible to manually implement similar functionality using "open with" file association thingy and "gnome-terminal --working-directory /tmp".

Unfortunately it seems that the crack geniuses of the Gnome 3 design  have decided to totally remove the ability for users to specify a command manually in the "Open With" dialog box so if your application isn't registered in their list (ie every non-gnome app or anything that might need a command arg) your now just screwed.

I can only assume the text box was confusing their target audience of little old ladies and mentally handicapped school children. Of course of the applications listed there is have things like rundll32 and okular listed about 2 dozen times. USABILITY!

I've tried poking around in gconf-editor but I can't see the option in there. I'm searching by application name though so maybe they have decided to use some kind of id scheme which would make manually overriding it a pain.

---

