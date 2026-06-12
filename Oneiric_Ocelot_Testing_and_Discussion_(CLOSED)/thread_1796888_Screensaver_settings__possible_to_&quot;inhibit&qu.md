---
title: "Screensaver settings / possible to &quot;inhibit&quot;?"
date: 2011-07-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-07-04
I've had very little time to play with the compter at all this summer, and I'm slow at picking up on Unity altogether, but I still want to be able to use *parent* Ubuntu even though I intend to focus mostly on Lubuntu. (I'm thinking that'll be helpful with bug filing, etc.)

Anyway I was just playing with a fairly *virgin* Oneiric this AM (the only thing I've tweaked at all is getting rid of the overlay-scrollbars) and it hadn't been updated in nearly two weeks. 

But the one thing that baffles me with Gnome3 (regardless of whether I'm using Unity, Gnome-shell, or the new gnome-panel) is how to "inhibit" the screensaver if I'm watching flash videos on Hulu or such.

Actually the new gnome-screensaver baffles me altogether. I'd commonly set the screensaver to activate after 15 minutes and have the monitor shut off (to kill the backlight) after 30 minutes.

I probably just haven't kept up enough on the changes in gnome3 so any comments are welcome :)

---

### Post by cariboo on 2011-07-04
Gnome-screensaver is fairly broken in my opinion, ti doesn't pay attention to any settings I've made, and this morning I was watching a movie using vlc, and the screen saver kept starting on it's own. We seem to be back where we were in Hardy with it misbehaving.

---

### Post by kansasnoob on 2011-07-05
> **cariboo907 said:**
> Gnome-screensaver is fairly broken in my opinion, ti doesn't pay attention to any settings I've made, and this morning I was watching a movie using vlc, and the screen saver kept starting on it's own. We seem to be back where we were in Hardy with it misbehaving.

That's the same behavior I'm seeing, and it's not just limited to Ubuntu. I'm fairly sure it's a gnome3 problem.

I've not had time to try yet but I wonder if we could make xscreensaver overide the new gnome-screensaver?

And it's not dependent on how you're playing videos. It's messed up with some flash, some totem, some mplayer, some VLC, etc.

IMHO the Gnome devs really crapped the bed :(

I can see why the Ubuntu devs went a different direction.

---

### Post by kansasnoob on 2011-08-17
I thought I'd bump this because something may have changed that I'm not aware of. I have been able to use caffeine in Natty if desired:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

But I've not found a decent way of inhibiting/controlling the screensaver/sleep in gnome 3 regardless of what UI is used.

---

### Post by seeker5528 on 2011-08-17
I posted my solution to the screensaver situation in an earlier thread....

[http://ubuntuforums.org/showpost.php?p=11003326&postcount=3](http://ubuntuforums.org/showpost.php?p=11003326&postcount=3)

Later, Seeker

---

### Post by kansasnoob on 2011-08-18
> **seeker5528 said:**
> I posted my solution to the screensaver situation in an earlier thread....

[http://ubuntuforums.org/showpost.php?p=11003326&postcount=3](http://ubuntuforums.org/showpost.php?p=11003326&postcount=3)

Later, Seeker

Thanks, that's just what I needed :D

I'm quite used to xscreensaver anyway from having played around in Lubuntu so this is a fantastic solution.

I just don't see how the gnome devs could overlook something so basic. What good is an OS if you can't watch a video w/o the screensaver/power-saver activating :confused:

OTOH I'm finding Unity-2D almost bearable to use with a few minor tweaks, but it's still more time consuming than a more "mouse-centric" old school approach IMHO.

---

### Post by cariboo on 2011-08-18
In my opinion screensavers are pretty redundant, with most people using LCD/LED monitors, there is no need for something to keep an image from burning into the tube, as with a CRT. Also with the price of utilities, you'd think that the need to cut down on power usage would be the main reason for shutting a monitor down, when not in use, rather than displaying a screensaver.

The current app in system settings allows you to set the amount of time the monitor is idle before before going into power saving mode as well as how long to wait before locking the screen. What more do you need?

---

### Post by kansasnoob on 2011-08-18
> **cariboo907 said:**
> In my opinion screensavers are pretty redundant, with most people using LCD/LED monitors, there is no need for something to keep an image from burning into the tube, as with a CRT. Also with the price of utilities, you'd think that the need to cut down on power usage would be the main reason for shutting a monitor down, when not in use, rather than displaying a screensaver.

The current app in system settings allows you to set the amount of time the monitor is idle before before going into power saving mode as well as how long to wait before locking the screen. What more do you need?

Well, what options do you see? I see this:

[ATTACH]200286[/ATTACH]

I recently had to shut off my local cable so I get one channel on the TV if the weather is good :( So my main computer is now my TV sort of :)

I certainly watch movies that are longer than an hour, and I set Hulu to auto-play so I just have some sound in the house other than my dogs and myself ;)

Is that enough reason to add "never" or make the "inhibit-applet" work :confused:

---

### Post by cariboo on 2011-08-18
I still have the same problem as you do, where the screensaver/screen shut-off comes on in the midst of watching a movie.

Back when this happened in I believe it was Hardy, the dev responsible for gnome-screensaver, said he wouldn't fix the problem, as it was up to the individual applications to disable the screensaver while they were running. It looks like we've run into to the same situation again, with the latest version of gnome-screensaver.

Has there been a bug report created for this problem?

This [lpbug]428884[/lpbug] is the only bug I could find on the problem.

---

### Post by kansasnoob on 2011-08-18
> **cariboo907 said:**
> I still have the same problem as you do, where the screensaver/screen shut-off comes on in the midst of watching a movie.

Back when this happened in I believe it was Hardy, the dev responsible for gnome-screensaver, said he wouldn't fix the problem, as it was up to the individual applications to disable the screensaver while they were running. It looks like we've run into to the same situation again, with the latest version of gnome-screensaver.

Has there been a bug report created for this problem?

This [lpbug]428884[/lpbug] is the only bug I could find on the problem.

I don't know about a bug report but from Gutsy through Natty I could just use the inhibit-applet or you could select "never" in gnome-screensaver.

I'll try to search gnome-screensaver bugs later.

This is just one example of the things the gnome devs did wrong IMHO. I realize some of it's purely opinion but when things you used to do no longer work, or take much longer to do, that is in itself a bug :)

That aside I think Canonical did the best they could at easing us into this transition, and I like that SABDFL accepted Lubuntu just when he did.

I also realize that no two people use their computer(s) the same way so opinions vary and at times of immense change people get really emotional.

---

### Post by cariboo on 2011-08-18
I haven't had to set the screensaver to never, recently. I run XBMC on top of Natty on my media center pc, I haven't done anything to set the screensver/lock screen, XBMC disables it as far as I can see, and uses its own screen dimmer when paused.

I have to say that I find the screensaver on Lubuntu fairly annoying on a default setup. It seems to start up at the most inopportune moment, and doesn't seem to be very consistent.

---

### Post by kansasnoob on 2011-08-18
> **cariboo907 said:**
> I haven't had to set the screensaver to never, recently. I run XBMC on top of Natty on my media center pc, I haven't done anything to set the screensver/lock screen, XBMC disables it as far as I can see, and uses its own screen dimmer when paused.

I have to say that I find the screensaver on Lubuntu fairly annoying on a default setup. It seems to start up at the most inopportune moment, and doesn't seem to be very consistent.

I'd never seen that, but now I need to try it :D

BTW at some point it would be cool if someone could talk to the "caffeine" dev(s) and see what challenges they're facing with this.

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

My plate is beyond full :)

---

### Post by mc4man on 2011-08-18
> **kansasnoob said:**
> 

Is that enough reason to add "never" or make the "inhibit-applet" work :confused:
The max presented of 1 hr. does seem a bit presumptuous of gnome, nothing new for gnome3

Whether your typical inhibit <whatevers> of various media players work on this I don't know, haven't had chance to try.
 
Would be interested if anyone knows where the per user choice of time frame till dimmed  is written to, possibly it could be perverted to last longer than 60 min.'s

Edit : writes to ~/.config/dconf/user, nothing to be had there

---

### Post by seeker5528 on 2011-08-18
> **mc4man said:**
> Would be interested if anyone knows where the per user choice of time frame till dimmed  is written to, possibly it could be perverted to last longer than 60 min.'s

In dconf-editor at 'org --> gnome --> screensaver --> power-management-delay' would be my guess.

I see that there is a 'org --> gnome --> desktop --> screensaver --> idle-activation-enabled' option as well that could perhaps disable the screensaver completely by unchecing the box?

Later, Seeker

---

### Post by mc4man on 2011-08-18
A slight possible hack around - 
```
gksudo gedit /usr/share/gnome-control-center/ui/screen.ui
```

Take maybe the 2 entries for 1 min and change the value (the 2nd entry is most likely, around line 65
So here changed 60 to 60000

<col id="0" translatable="yes">1 minute</col>
        <col id="1">60000</col>

Seems to have worked here, ill effects...?

---

### Post by seeker5528 on 2011-08-19
**Note to self:** When copy/pasting settings off the web that need to be in quotes, make sure the quote characters are actually quote characters and not something that just look kinda like quote characters that cause X.org the choke. 

I removed xscreensaver, install gnome-screensaver, set the blank time to 3 minutes, then ran dconf editor and went to 'org --> gnome --> desktop --> screensaver and unchecked the box next to 'idle-activation-enabled' and that seemed to work. Rebooted and it still seemed to work, but the screen still did blank after a while, so I'm guessing it reverts to the X.org setting if that box is not checked?

Next up I added this to my xorg.conf file 
```

Section "ServerFlags"
     Option "blank time" "0"
     Option "standby time" "0"
     Option "suspend time" "0"
     Option "off time" "0"
     Option "dpms" "false"
EndSection 

```

Seems to be working.

Later, Seeker

---

### Post by dsfitzpat on 2011-08-20
Good to know it's possible to disable the screensaver with a bit of work, but in my case I still want to know that the monitor shuts off if I'm away from the computer for a bit.  I'm hoping that Ubuntu builds on past precedent and works on (eventually) providing users with easy ways of managing settings like this.
BTW, in Natty I've been using the following (admittedly kludgey solution) when watching Hulu - when I see the screen start to fade (there's about a 5 second fade before the screensaver kicks in) I hit a button on my bluetooth remote.
I wouldn't suggest investing in this solution if stopping the screensaver is the only reason for doing so - I can also use the remote to control the Hulu desktop program - no need to get up to select a new show :-)

---

### Post by cariboo on 2011-08-21
It seems to me that seeker5528's solution just disables the screensaver/lock screen altogether. I usually forget to lock the screen when leaving the system, so I depend on it starting automatically.

---

### Post by mc4man on 2011-08-21
At least here there has always been 2 separate things - 
The display will blank or sleep based on something independent of gnome or available power settings. (hardware or bios based?

So for example on this laptop it's around 10 min. and has nothing to do with the current 'time to dim'

While there used to be a way around that with 'time to idle' & power settings, in recent times an xorg section similar to what was posted above works the best. (I only use the 1st 4 lines.

Again here the xorg has no effect on the 'time to dim' other than allowing one longer than the 10 min to blank or sleep.
So with the xorg section I can set the 'time to dim' to 1 min. & it will dim after a min or so. If set to 1 hr. it will dim after 1 hr.

Without the xorg then any dim time over the 10 min blank/sleep time obviously doesn't have a chance to happen

For a 'time to dim' over 1 hr. adjusting the screen.ui works fine here though it may require deleting the user file in dconf first

---

### Post by seeker5528 on 2011-08-22
> **cariboo907 said:**
> It seems to me that seeker5528's solution just disables the screensaver/lock screen altogether.

If you want to disable it temporarily, you can issue the command ```
gnome-screensaver-command --exit
``` then issue the comand ```
gnome-screensaver
``` to start it again. Or browse for it in the file browser at '/usr/bin/'.

Later, Seeker

---

### Post by azurehi on 2011-09-08
> **cariboo907 said:**
> In my opinion screensavers are pretty redundant, with most people using LCD/LED monitors, there is no need for something to keep an image from burning into the tube, as with a CRT. Also with the price of utilities, you'd think that the need to cut down on power usage would be the main reason for shutting a monitor down, when not in use, rather than displaying a screensaver.

The current app in system settings allows you to set the amount of time the monitor is idle before before going into power saving mode as well as how long to wait before locking the screen. What more do you need?

Ever tried Noof?  Screensavers add beauty to my desktop.

---

