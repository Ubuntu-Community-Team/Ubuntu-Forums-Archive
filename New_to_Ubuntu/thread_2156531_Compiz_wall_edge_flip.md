---
title: "Compiz wall edge flip"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-06-22
On Ubuntu 12.04 (Compiz 0.9.7.12) I use the wall plugin and checked all the boxes for 'edge flipping' in ccsm as well as setting the key bindings (attached) 

I have seen a bug report on this [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/771448](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/771448) (which is old but apparently still not resolved in 12.04) but my experience is somewhat different and kind of strange. It is not that the flipping doesn't work, but it is rather sporadic so that sometimes it works perfectly and other times not at all. This morning there was a compiz update (i think from proposed) and now I am in version 0.9.7.12.  When first boot up, edge flipping doesn't work at all. Then when the computer has been on for a while (maybe an hour or 45 minutes..) then it starts working but only partially (only right flip works), then wait a bit longer it is working perfectly now. I tried reboot several times and the same thing happened all the time: at first not working at all, then started working on and off in only one direction, then waited for about an hour and it totally worked. 

Does anyone have a theory of what is happening and the status of this bug? (fixed, not fixed, fixed a little bit) Thanks.
'
Edited: I should clarify that I didn't fiddle with or even launch ccsm at any point. Edge flip just kind of started working spontaneously after a while.

---

### Post by monkeybrain2012 on 2013-06-24
Ok, I found a work around, now desktop wall edge flip is enabled on start reliably. Basically this is the same solution for fixing scale addon in 12.04 (found that one on AskUbuntu). Open gconf-editor, go to apps > compiz-1 > general > screen0 > options and edit the active plugin list so that wall should be down on the list, but it doesn't have to be at the very bottom. I have it ahead of scale and scale addon and all work. Now of course you have to enable edge flipping in ccsm in the first place (may need to set the bindings as well, see attached screenshot above)

Hope it may help someone having the same issue.

Really, all these are fixed in newer releases of Compiz (raring and quantal(?))and the fixes should be backported to the LTS. I am not sure what is the point of offering to "upgrade" to just another known broken version.

---

### Post by monkeybrain20122 on 2013-10-19
Ok, apparently edge flip is broken again in 13.10 and the work around above doesn't work any more. Any suggestion??

---

### Post by Paper Bag on 2013-10-19
> **monkeybrain20122 said:**
> Ok, apparently edge flip is broken again in 13.10 and the work around above doesn't work any more. Any suggestion??
Works here on 13.10 x64, Compiz 1:0.9.10+13.10.20131011-0ubuntu1. I did have this bug in 13.04 though.

---

### Post by mc4man on 2013-10-19
Don't use Wall here (rotate), but set up a new user & edge fipping works fine in wall.
The only thing was it wasn't default enabled for that new user, after enabling works fine

---

### Post by monkeybrain20122 on 2013-10-19
If I logout and log back in then it works, but on boot up it doesn't.

---

### Post by mc4man on 2013-10-19
> **monkeybrain20122 said:**
> If I logout and log back in then it works, but on boot up it doesn't.
Always seems to be something with edge fipping..
This time here in 13.10 with rotate it works fine, but if i disable grid it breaks. Re-enable grid it works again. So for the moment will leave grid.
Probably could dump grid & get working somehow, either unset & reset or what's usually effective is to disable 'automatic plugin sorting' in compiz

---

### Post by monkeybrain20122 on 2013-10-20
> **mc4man said:**
> either unset & reset or what's usually effective is to disable 'automatic plugin sorting' in compiz

How do you disable 'automatic plugin sorting'?

Edit: Ok, found it in ccsm.Will see if this works.

---

### Post by monkeybrain20122 on 2013-10-20
Hi, mc4man,

It is working. I unchecked 'automatic plugin sorting' in ccsm (under Preferences) and manually put wall and the bottom on the right panel and then restarted Ubuntu, edge flip has been working consistently since. Thanks!

---

### Post by mc4man on 2013-10-20
> **monkeybrain20122 said:**
> Hi, mc4man,

It is working. I unchecked 'automatic plugin sorting' in ccsm (under Preferences) and manually put wall and the bottom on the right panel and then restarted Ubuntu, edge flip has been working consistently since. Thanks!
The only thing to beware of when plugin sorting is disabled is that there is no conflict resolution in compiz when adding plugins &  or changing bindings 
However not a big deal if one pays attention or enables before changes, then disable.
If 14.04 decides to stick with unity7 & compiz for desktop installs I may look at why this nonsense occurs & how does compiz order plugins when auto loading

---

### Post by monkeybrain20122 on 2013-12-01
It seems that this thread is never really solved. Just discovered another little annoying thing. Edge flip stops working if I drag an icon from the dash and put it on the Unity launcher. Opening ccsm and go to Preferences> Plugin list and move the wall plugin up and down again restores the functionality (automatic sorting already disabled as per mc4man's workaround)  Rearranging icons on the Unity launcher doesn't cause any problem.

This happens apparently only when the Nvidia driver is used. With nouveau it is safe to move icon from dash to launcher without breaking edge flip. Ubuntu 13.10 64 bit (I have another 13.10 with identical compiz settings on an external drive which I use as a portable but use the nouveau driver. Boot up in the same machine and this doesn't happen)

I understand that compiz is a low priority now, that they are moving to the next great thing with more new bugs, but since it is going to be hosting Unity 7 in the next LTS I hope they fix some of these old bugs. Aside from these annoyances Compiz is a great piece of software espcially with the performance tweaks since Unity 7 (for the same video with vdpau compiz uses about 3 % of cpu while kwin and gnome-shell uses over 10% e.g) and it is really smooth ( even more so with nouveau than Nvidia blob), it is a shame if it is left unmaintained for the next LTS.

---

### Post by monkeybrain20122 on 2014-02-08
To recap, I have two Ubuntu 13.10 isntalls. One uses the Nvidia blob another uses noveau. Edge flip works without issue (after disabling auto configuring of plugins) on the one with nouveau but on the one with the Nvidia blob edge flip would stop working whenever I drag and drop an item from one folder to another or drag and drop a launcher icon from the dash to the Unity launcher bar.  Both run on the same machine (the install with nouveau is on an external hard disk and I can boot it off the same machine or other machines)

I have replaced all the compiz configuration files in the second install with the "good" ones from the first (/etc/compizconf and /etc/X11/Xsession.d/65compiz_profile-on-session and all the comiz config files in /home:.compiz, .config/compiz-1, .gconf/apps/compizconfig-1) but the problem persists.

It leads me to think that it may have something to do with the Nvidia driver rather than corrupted configuration or settings, but I am not sure if that theory makes any sense.

Edited: **To the mods**, wonder if it is possible to remove the "solved" tag to this thread because unfortunately it is not really solved dispite my initial optimism.

---

