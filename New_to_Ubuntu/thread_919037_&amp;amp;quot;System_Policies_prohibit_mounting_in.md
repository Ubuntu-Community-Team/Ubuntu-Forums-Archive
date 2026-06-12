---
title: "&amp;amp;quot;System Policies prohibit mounting internal media&amp;amp;quot; --  where to change?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-13
Under Kubuntu, I get an error similar to this:

**System Policies prohibit mounting internal media**

What is the recommended way to check and change this?


And testing under Ubuntu (same computer) the error is this:


**You are not privileged to mount the volume 'movies'**

(what a snob :) )

I don't use Gnome as much as KDE, so would rather a KDE fix.

---

### Post by ChanServ on 2008-09-13
you have to set permissions for the volume, easiest way is to open preferences for the volume and there is a permissions tab were you can change it

---

### Post by egalvan on 2008-09-13
> **ChanServ said:**
> you have to set permissions for the volume, easiest way is to open preferences for the volume and there is a permissions tab were you can change it

It doesn't show under "Places", where else can it be?

Under "media", it does not show "preferences" just natters about privileges.

Oops, I gotta go work an extra at the firehouse, be back Monday afternoon.

Thanks in the meantime

---

### Post by egalvan on 2008-09-15
Any help on **changing System Policies**?

I know there is a menu somewhere, but have not been able to find it again.
So far google has not been of any use...

---

### Post by egalvan on 2008-09-18
Bump

Still no luck with

"System Policies"

---

### Post by mc4man on 2008-09-18
Right click on bottom panel -> add applet. Add the settings (control center) applet, open it -> system administration -> Disk and File systems. Use administrator mode.
Highlight the partition you want -> modify

Inside you can adjust settings, it seems you must give it a mount point if you change the settings. (/media/whatever
 
Under advanced, the line 'fs_passno' was set at 1. After I changed the 'mount permissions' when I went back it had changed to 0

Just waited 15 min. for authentication to expire, above does work, now i can mount the partition without a password

Under mount options I choose 'any user..', 'device owner' may also work


Edit: this is one of the things about kubuntu that drives me crazy - looked for a long time the other day for those setting and couldn't find anywhere.

---

### Post by timcredible on 2008-09-18
it's your user account that's preventing this.  system->administration->users and groups, pick your account (assuming you have admin privileges), and choose preferences->user privileges and change your permissions for whatever you don't have permissions for now (i don't know which one is responsible for this)

---

### Post by egalvan on 2008-09-18
> **timcredible said:**
> it's your user account that's preventing this.  system->administration->users and groups, pick your account (assuming you have admin privileges), and choose preferences->user privileges and change your permissions for whatever you don't have permissions for now (i don't know which one is responsible for this)

OK, tried this (with suitable mods for Kubuntu)
and find that 

root account has NOTHING checked off....

my user account has EVERYTHING except "send and receive faxes" 
and "use tape drives" checked.


is this normal?

---

### Post by drs305 on 2008-09-18
> **egalvan said:**
> OK, tried this (with suitable mods for Kubuntu)
and find that 

root account has NOTHING checked off....

my user account has EVERYTHING except "send and receive faxes" 
and "use tape drives" checked.


is this normal?

Yes it is normal. Have you done what the previous posters have suggested without success?

---

### Post by egalvan on 2008-09-18
> **drs305 said:**
> Yes it is normal. Have you done what the previous posters have suggested without success?

Partial success.

All the desk-top icons (for these drives) have disappeared.

I have forced the usage of my external USB drive.

But I really want to find that screen that allowed changes to the

SYSTEM POLICIES

I know I messed with it a month ago, but i am too new to this stuff to really remember WHERE it was. 
I do remember I was following a "how-to" that described it as a "strange-looking" menu

---

### Post by drs305 on 2008-09-18
> **egalvan said:**
> 
I know I messed with it a month ago, but i am too new to this stuff to really remember WHERE it was. 
I do remember I was following a "how-to" that described it as a "strange-looking" menu

If the 'Users & Groups' section of System, Admin isn't what you were looking for, you may have changed the settings in gconf-editor (use gksu gconf-editor if the below doesn't work):
```
gconf-editor
```

Open it with the command above and go down to desktop > gnome > volume_management
There are automount options in that section. If that isn't the section you changed, use the search function (Edit, Find, and tick "search also in key names) to see if you can find the setting you altered.

---

### Post by mc4man on 2008-09-18
> System Policies prohibit mounting internal media
If that means other internal partitions (same drive or others) then the settings are where I described.
Just tried a 2nd partition using 'any one' and it also now mounts without password. You can also choose to have it automount at 'startup' if desired, set it by 'device name' or 'UUID',ect.

Note: using 'device owner' resulted in permissions denied ( no offer to authenticate 

Any permission issues for write can be resovled with  sudo chown <username>:<username> /media/<whatever> (or wherever & whatever the chosen mount point is
see screens
(hope they're okay, alt+Prt Scr doesn't seem to work in kubuntu

---

### Post by egalvan on 2008-09-18
> **drs305 said:**
> If the 'Users & Groups' section of System, Admin isn't what you were looking for, you may have changed the settings in gconf-editor (use gksu gconf-editor if the below doesn't work):
```
gconf-editor
```

Open it with the command above and go down to desktop > gnome > volume_management
There are automount options in that section. If that isn't the section you changed, use the search function (Edit, Find, and tick "search also in key names) to see if you can find the setting you altered.

OK, this looks a lot closer to the type of menu i was using, but not the same....
and lordy, there is NO WAY I would remember the name... I can't remember the LOOKS :confused:

Actualy, 'mc4man' had it right in one sense with the "disk & file permisions".
 I recognize that as something I tried changing, and totally messing up the <mount-points> and labels.....

Yes, I should not have been changing so much a once... I know better...

I guess I got over-confident when I solved my "can't-play-music-or-dvd" problem by finding and following a "how-to" on this forum.

Seriously, at this point, I think I am going to save all these posts, and then re-install Ubuntu when 8.10 comes out... I also want to change to 64bit.

I'll keep on trying different ideas that you all have come up with...
I'm learning a lot about mount points and /dev and fstab, which is always a "good thing"...
 and I don't think I can make it any worse. :)

I have to go now, I'll be back in a day or three...

ErnestG

---

### Post by egalvan on 2008-09-18
> **mc4man said:**
> If that means other internal partitions (same drive or others) then the settings are where I described.
Just tried a 2nd partition using 'any one' and it also now mounts without password. You can also choose to have it automount at 'startup' if desired, set it by 'device name' or 'UUID',ect.

Note: using 'device owner' resulted in permissions denied ( no offer to authenticate 

Any permission issues for write can be resovled with  sudo chown <username>:<username> /media/<whatever> (or wherever & whatever the chosen mount point is
see screens
(hope they're okay, alt+Prt Scr doesn't seem to work in kubuntu



Came out crystal-clear... and I recognize the screens as ones I had trouble with... 

Are there any 'man' pages or similar that I could read, to try to understand all the options given?

---

### Post by mc4man on 2008-09-18
> Are there any 'man' pages or similar that I could read, to try to understand all the options given?

Not anything I found, your left to figure it out by yourself (in kubuntu

Turns out that settings menu is also available from entering 'kcontrol' in konsole

> I solved my "can't-play-music-or-dvd" problem that's one of my biggest disappointments with kubuntu - almost nothing  works *well* 'out of the box'. If you have 2 cd/dvd drives your very much 'sol', I think the developers figured 1 drive is plenty enough

edit:
I can actually run Amarok better and in more varied and useful ways in ubuntu than kubuntu

---

### Post by mc4100 on 2008-09-18
I don't use Kubuntu (or even Hardy), but you might try:
```
polkit-gnome-authorization
```

---

### Post by egalvan on 2008-09-20
> **mc4man said:**
> Not anything I found, your left to figure it out by yourself (in kubuntu

Turns out that settings menu is also available from entering 'kcontrol' in konsole

 that's one of my biggest disappointments with kubuntu - almost nothing  works *well* 'out of the box'. If you have 2 cd/dvd drives your very much 'sol', I think the developers figured 1 drive is plenty enough

edit:
I can actually run Amarok better and in more varied and useful ways in ubuntu than kubuntu

Hey, playing mp3 and commercial CSS-DVD's doesn't work "out of the box" under Gnome, either.....

Let's be fair... :)

and what problem does having 2 optical drives create?
both opticals and both SATA drives worked OK at first...

until I started "playing" with settings, trying to teach myself Linux'y things :) 
(gotta play some more, I get to keep both pieces)


I have two HP MultiMedia machines...
one a laptop, and one a desktop.

At the moment, my laptop is still OK, I haven't "played" with it yet..
just loaded KDE on top of Gnome, and ran the "multimedia" how-to I found on this forum.
Exactly the same as on the desktop.

Well, I'm off to see the wizard, er, I mean try that 
```

polkit-gnome-authorization
```

and

*entering 'kcontrol' in konsole*


thing. Wish me luck.

Thanks!

ErnestG

---

### Post by egalvan on 2008-09-20
> **mc4100 said:**
> I don't use Kubuntu (or even Hardy), but you might try:
```
polkit-gnome-authorization
```

Wow, I think that is IT!

My problems may be over, or just begining to get worse,
as I think that window is what got me into trouble in the first place.

I'm too tired to think that well right now.

Gotta do my shift at the firehouse.

Will post back later Sunday.

Thanks!

---

### Post by egalvan on 2008-09-23
OK, it's not quite IT...

still having mount problems....

runnign kconsole and trying to enable the un-mounted drive gives this...


```
An error occurred while enabling m7690n.
The system reported: fuse: mount failed: Device or resource busy

Return code from mount was 21.
"incorrect invocation or permissions"
"internal mount bug or missing nfs support in mount"
"problems writing or locking /etc/mtab
```

I have another post specifically for this problem...

---

