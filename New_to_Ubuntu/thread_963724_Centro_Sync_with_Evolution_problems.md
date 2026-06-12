---
title: "Centro Sync with Evolution problems"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by skywalkin1138 on 2008-10-30
Hello,

I'm running Hardy Heron and am having problems syncing my new Centro with Evolution Calendars and Tasks.  I read the <a href="http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=326">archived thread</a> and it looked like some other people were having problems, but no posted solution.
I added (then removed) the visor module and am using "usb:" for the connection.
When I press the HotSync button, it says that it is communicating and it completes with no errors, but I see no calendar or task data in my pda.
Using gnome-pilot for syncing, conduit ECalendar configure to Sync and keep setting One Time function to "Copy to PDA".  Another issue I've run into is the conduit doesn't always remember the selected mailbox (trying to sync with an IMAP/Exchange accout).
Also tried deleting the one VersaMail account, but VersaMail won't let me.

Any help would be appreciated (I really don't want to have to use Windows).  Thanks in advance.

---

### Post by wyrless2002 on 2008-11-09
In this other thread ([http://ubuntuforums.org/showthread.php?t=973158&highlight=gnome-pilot](http://ubuntuforums.org/showthread.php?t=973158&highlight=gnome-pilot)) underdog512 mentions that there is a bug recorded in launchpad that contains a workaround for this.  [https://bugs.launchpad.net/gnome-pilot/+bug/282491](https://bugs.launchpad.net/gnome-pilot/+bug/282491)

Good luck.

---

### Post by skywalkin1138 on 2008-11-10
Thanks for the information, but unfortunately, I'm not running Ibex yet.  I'm running 32 bit 8.04 LTS - Hardy Heron.

Turns out I can get gnome-pilot to sync with the local calendar/tasks/etc.; just not with my Exchange account (tried various things like making them available offline, saving to files, etc.).  If I copy all the data from my Exchange account to the local system, I can sync.  This is not practical for me.  And yes, I did modify the conduit settings various times and like I stated below, it did not always remember my selections and would not sync with them.

---

### Post by Doby on 2009-01-21
I can sync my centro with evolution but I have to change the one time sync to sync, or it won't sync, anyone have a workaround for this problem?

---

