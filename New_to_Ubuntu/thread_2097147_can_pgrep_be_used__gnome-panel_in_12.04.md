---
title: "can pgrep be used  gnome-panel in 12.04"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by allynm on 2012-12-22
Hello everyone,

I am trying to use a script which finds a DBUS session bus.  I am using the command

```

pids=`pgrep -u $user gnome-panel`

```As nearly as I can tell, this command fails to function as intended.  I am very new to linux and the various versions of UBUNTU preceding Precise.  In searching the internet I get the impression that 12.04 may no longer support the gnome-panel.  

Could someone suggest what the correct code for finding the process id's?

Thanks,
Mark Allyn aka allynm

---

### Post by steeldriver on 2012-12-22
I think the code itself is OK although the preferred syntax now is [FONT=Courier New]value=$(some command)[/FONT]rather than the older backtick form [FONT=Courier New]value=`command`[/FONT] 

However if the process simply isn't running, you will get nothing - and I think you're right, gnome-panel isn't part of the desktop any more - is there a different process you could check for? what exactly is the purpose of the pid check?

---

### Post by allynm on 2012-12-22
Good morning, Steeldriver,

I'm pretty certain that 12.04 does not support gnome-panel.  I would need to use some variation of this approach by identifying whatever is the new form of "gnome-panel".  Don't know what that is.

The reason I was looking for the pids for gnome-panel was to use them to find the DBUS_SESSION_BUS_ADDRESS for a session.  In looking around the web for an alternative to your .XAUTHORITY workaround for using zenity to pop a notification window on the desktop (when a flashdrive was inserted), I bumped into an old UBUNTU forum post by Rackstar on March 13, 2009.  This post gave code that used the "notify-send" command to open a notification window.  Rackstar had figured out a way using the DBUS_SESSION_VARIABLE to run a script that allowed notify-send to write to the current desktop.  Rackstar was running  an earlier version of UBUNTU (oneiric)  that had gnome-panel functionality.

Rackstar's approach bears a superficial resemblance to  your .Xauthority method.

I'm at a very frustrating impasse with this whole business, and yet I'm learning quite a bit about linux in the process.  

Best regards,

Mark Allyn aka allynm

---

### Post by steeldriver on 2012-12-22
Hi Mark - I know NOTHING about dbus, iirc there is at least one real dbus wiz on here though - have a search around

I found this syntax on the web:

```
tr '\0' '\n' < /proc/${pid}/environ | grep "DBUS_SESSION_BUS_ADDRESS"
```I wondered if it might be possible to use the actual gnome-session for the pid? e.g.

```
tr '\0' '\n' < /proc/$(pgrep -u $USER gnome-session)/environ | grep "DBUS_SESSION_BUS_ADDRESS"
```This seems to work on my 12.04 box:

```
$ tr '\0' '\n' < /proc/$(pgrep -u $USER gnome-session)/environ | grep "DBUS_SESSION_BUS_ADDRESS"
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-PbU8R2hqEK,guid=ec64c06a86fbc0a19ac2e2aa00000028

```BTW that Xauthority script I posted in the other thread *does* seem to be broken - it's stopped working for me. If I manage to debug it I will update that thread.

---

### Post by allynm on 2012-12-22
Hi Steeldriver,
 
I started to read as much as I could about DBUS, but the documentation that is out there is beyond my grasp.  Perhaps, and I hope sincerely, the DBUS expert will take an interest in this thread and help out.
 
As far as your code for Xauthority goes, here's a small update.  I interspersed "echo messages"  through each of your main commands.  All the commands appear to run successfully, i.e. echo reports them as having run, but Zenity does not kick in.  
 
It would be great if you could debug the routine.
 
I'll take a look at the snippets you have included in your reply.  This is a very good learning experience for me, especially your bash code (which I'm still carefully practicing).
 
Cheers,
Mark

---

### Post by allynm on 2012-12-23
Good morning, Steeldriver,

Betraying my naivete...but why do we need to transliterate from \0 to \n?

Must now run off to the shoppes to buy some gifts for my noble wife...Back in 3 hours.

Cheers,
Mark

---

