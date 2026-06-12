---
title: "polkit-gnome-authorization, what went wrong?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-23
This may be the wrong sub-forum, but I didn't know where else to post..


I was (foolishly) playing with ```
polkit-gnome-authorization
```

and now I cannot mount any drives, except my boot drive partitions.

I get "you do not have privilage" errors.

Below is a screen-shot of my current Authorizations...

Notice that it states

**Granted by ernest**

Where a CLEAN install of Ubuntu shows this same screen as

**Auth as ernest**

and on this clean install all drives are mountable...

Can this be changed? I tried but kept getting the 'Granted By 'instead of 'Auth By'.

I want to get back to the original way that mounting worked,
before I messed it up...

Would this matter anyway?
Am I looking in the wrong place?

ErnestG

---

### Post by egalvan on 2008-09-23
Running Kconsole and trying to 'enable' the un-mountable' drive gives this error...

---

### Post by mc4man on 2008-09-23
What's kinda confusing is your other post was tagged kubuntu, but after reading the last couple of posts it seems your using ubuntu. This one starts as ubuntu but your showing a kde screen. do you have 2 separate installs or are you using ubuntu with a kubuntu desktop and or in a kde session?

 If so it's not a good idea to be switching permissions, ect. in the kde session

In any event the partition in question 'm7690n' can't be enabled without a mount point (/media/m7690n would be a guess.

If you are in a *kde session* see if in the administrator box you can 'modify' the partition. if so try setting to 'any user....' and give it a proper mount point. If you can't modify, open dolphin, removable media and see what's up.

Or go back to ubuntu and see if you can mount, if not make a mount point in /media/  (sudo mkdir /media/<whatever>), mount it under root in that directory and chown it back to your self (if possible

---

### Post by egalvan on 2008-09-24
> **mc4man said:**
> What's kinda confusing is your other post was tagged kubuntu, ...it seems your using ubuntu. This one starts as ubuntu but your showing a kde screen. do you have 2 separate installs or are you using ubuntu with a kubuntu desktop and or in a kde session?

Ubuntu with KDE meta-package loaded under Synaptic.
Logging in under KDE or Gnome, different sessions.


>  If so it's not a good idea to be switching permissions, ect. in the kde session

Aren't the permissions persistent based on the USER who logs in, not what desktop or windows manager is being used?
I thought it was USER-based.

In other words, 
if I log in using Gnome, change permissions on a file, 
log out and log back in using KDE, 
will the permissions on that file have changed, or not?
Aren't the permissions data stored with the file info?
Don't all desk-tops, windows managers and file managers use these?
Otherwise, how would permissions be set in removable media?

See my confusion?


> In any event the partition in question 'm7690n' can't be enabled without a mount point (/media/m7690n would be a guess.

But what about an external drive that is plugged into the USB port?
How can the clean install automatically mount them?


> 
If you are in a *kde session* see if in the administrator box you can 'modify' the partition. if so try setting to 'any user....' and give it a proper mount point. If you can't modify, open dolphin, removable media and see what's up.

Or go back to Ubuntu and see if you can mount, if not make a mount point in /media/  (sudo mkdir /media/<whatever>), mount it under root in that directory and chown it back to your self (if possible


And further....
Sorry for the  confusion.

I use mainly Kubuntu, but install it over a full Ubuntu install.

So at times i also use Gnome.

What I am trying to do is eliminate the "Lack Of Privilege" errors I am getting under one of my Ubuntu/Kubuntu installs.

As I stated before, I messed things up with that polkit thing.

I have already tried the 'chown' and other  approaches (such as permissions)
but those are just band-aids.... I really want to get to the root of the problem.

I know it works, because I swapped out the boot drive with a blank one, then did a full install of Ubuntu, with KDE loaded after.
And auto-mounting works.

The difference is that "**granted** by ernest" and "**authorized** by ernest".
I cannot seem to change it from "granted: to "authorized"

I really don't want to re-install, because I would like to learn this policy stuff.


and your help on this is, of course, greatly appreciated.

ErnestG

P.S.

I'm thinking of starting a post entitled...

**Are PRIVILEGES different than PERMISSIONS? Please explain to a newbie.**

---

