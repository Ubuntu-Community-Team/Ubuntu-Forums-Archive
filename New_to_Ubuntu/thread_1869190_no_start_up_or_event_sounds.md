---
title: "no start up or event sounds"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by bob brazie on 2011-10-25
Fresh install of 11.10

When the machine starts there is no start up sounds and the event sounds do not play either.

In sounds I have the default alert selected and can hear the sounds as I click on each selection. Nothing is muted or turned all the way down.

I log onto the computer as root as I am the only one who comes near the machine,

Thanks in advance if you can help. Bob.

---

### Post by blade4 on 2011-10-25
Hi bob , quick question - are you getting sound in the normal user mode ? If so then that rules out any driver/hardware issues . 

Anyways , try installing sysv-rc-conf and run it in root 

sudo apt-get install sysv-rc-conf 

See if there is a check on the 'S' column in the 'pulseaudio' row 
If not , check it and log in again . 

Hope this helps :) 

Cheers

---

### Post by Frogs Hair on 2011-10-25
Nice little tool blade4 .

---

### Post by bob brazie on 2011-10-28
OK, I'm back for a couple of hours.

I can log out as root and back in as a guest and the sounds play but when I log out as guest and back in as root they do not play.

---

### Post by MrLeek on 2011-10-28
A very similar problem for me as well. 

Sound does work (playing youtube videos, games using wine, etc) - but I don't get any alert sounds (or the cool startup tune when you log in). I'm guessing either something has been turned off (so that 11.10 thinks I don't want event sounds) or it's a config glitch that's appeared since the upgrade from 11.04.

Thoughts?

---

### Post by FokkerCharlie on 2011-10-30
Yeah, this is a funny little one- the notification sounds from Skype are controlled via the 'Sound Settings' dialog.

So:  System settings > sound > Sound Effects tab > make sure it's un-muted and the volume is up.

No need for sysv-rc-conf as far as I can tell.

Charlie

---

### Post by m.riz on 2011-10-30
:oops::oops:
i too face similar problem,in the guest account sound is OK,but other user account didnt play startup sound.in the Sound Effects tab its un-muted and the volume is up.
is it a bug?

---

### Post by pierreyy on 2011-10-30
same problem here too... it had the same problem in 11.04...
 when i first installed ubuntu the event sounds were there... once or twice i muted the starup sound and now it just doesnt come up... i would really like to get the sounds back....

---

### Post by pierreyy on 2011-10-30
i just went into " sound" and turns out it muted 


" sound settings"-> "sound effects" and untick the "mute" checkbox... thats what i just did and it works fine ...

---

### Post by bob brazie on 2011-10-30
First thing I checked and it was not muted. Problem continues.

---

### Post by bob brazie on 2011-10-30
I find no place to turn on/off start up sounds in 11.10.

Bob.

---

### Post by m.riz on 2011-10-30
> **bob brazie said:**
> First thing I checked and it was not muted. Problem continues.

me too:(

---

### Post by blade4 on 2011-10-31
Hi bob , referring to my earlier post , did you try out sysv-rc-conf ? Because by now I'm pretty sure that pulseaudio is not granted access in root . ( It's the same for me too ) .

---

### Post by bob brazie on 2011-10-31
It was not checked, I checked it and it did not help.

Funny thing is that I have another clean install on another machine with the S unchecked and it works just fine with no check in the s column.

---

### Post by yoramdavid on 2011-11-01
I am having the same problem since upgrading to buntu 11.10
No login sound.
I do not use the root account, only the normal user account.

Here is what solved my problem: 
Download dconf editor if you haven't already. Then open it and go to "org -> gnome -> desktop -> sound". Once in sound, click on the theme name there (it says freedesktop) and change it to ubuntu (lowercase!) and exit. Log out and log back in, Login sound should now work.

---

### Post by Frogs Hair on 2011-11-01
Login to the guest session  and see if you have sound , turn down the volume or you may get a surprise .

This happened to my friend with Wubi after installing the gnome shell . We tested the  sounds using test speakers under the hardware tab in sound settings and all worked , but she had no login sound .

The system sounds worked when tested also . Because she just plays with Ubuntu via Wubi she reinstalled and added the shell again with no problems. 

:confused:

---

### Post by tedrogers on 2011-11-01
> **yoramdavid said:**
> I am having the same problem since upgrading to buntu 11.10
No login sound.
I do not use the root account, only the normal user account.

Here is what solved my problem: 
Download dconf editor if you haven't already. Then open it and go to "org -> gnome -> desktop -> sound". Once in sound, click on the theme name there (it says freedesktop) and change it to ubuntu (lowercase!) and exit. Log out and log back in, Login sound should now work.

Hi, whilst this does help a little, it does not bring back the "login ready" bonks at the start before logging in to X.

It is worth noting though, that before I edited the dconf as you suggest, my alert sounds were gray and ghosted-out...so this must be helping in some way as I can now select different sound themes for alerts.

But I do not have my beloved ubuntu login bonks/congas, or whatever they are called. :(

This has never been a problem before (and I've properly been on ubuntu since 6.06) and only happened on upgrade to 11.10 from 11.04.

I too have nothing muted or disabled, and yet the guest account works "better" as many of your have eluded, although still no login bonks.

In short, I want my login bonks back :P !

Can anyone help us/me get our login bonks working?

Thanks in advance all.

---

### Post by Electronicman on 2011-11-01
Hello, another newbie here.

I liked the startup sound for 10.04, this was my first encounter with Ubuntu. I tried to upgrade to 11.10 and had all kinds of error messages, so I did a reinstall and everything appears to be alright, except for the startup sound. Tried all the suggestions in the thread... nothing!. All the other audio works so it's not the sound card. Any Ideas?

---

### Post by bob brazie on 2011-11-01
> **yoramdavid said:**
> I am having the same problem since upgrading to buntu 11.10
No login sound.
I do not use the root account, only the normal user account.

Here is what solved my problem: 
Download dconf editor if you haven't already. Then open it and go to "org -> gnome -> desktop -> sound". Once in sound, click on the theme name there (it says freedesktop) and change it to ubuntu (lowercase!) and exit. Log out and log back in, Login sound should now work.

After installing dconf editor I found that my sounds were set at "Custom" I reset the defaults to the "freedesktop" and everything is working fine now.

Thanks for the tip on the nifty utility. I even found a setting to turn off my touch pad which got in the way with my wild typing style and landed the cursor in unknown positions. <g>

Do you know of any documentation for the editor that would lead me to new and fun hacks?

---

### Post by MrLeek on 2011-11-01
> **yoramdavid said:**
> 
Here is what solved my problem: 
Download dconf editor if you haven't already. Then open it and go to "org -> gnome -> desktop -> sound". Once in sound, click on the theme name there (it says freedesktop) and change it to ubuntu (lowercase!) and exit. Log out and log back in, Login sound should now work.

Another success with this method. Worth mentioning that dconf crashed for me a couple of times whilst trying to make the edit - just stick with it and the solution will work..

Oh - and when you click on the theme name (where it says freedesktop) you're looking for a cursor. Delete "freedesktop" and type in "ubuntu". I was expecting a drop-down menu...:p

---

### Post by MrLeek on 2011-11-01
> **bob brazie said:**
> 
Thanks for the tip on the nifty utility. I even found a setting to turn off my touch pad which got in the way with my wild typing style and landed the cursor in unknown positions. <g>

Do you know of any documentation for the editor that would lead me to new and fun hacks?

2nd this - dconf is a neat utility that can be really useful in the right hands...but confusing to the newbie (wait, that's me!! :))

---

### Post by yoramdavid on 2011-11-01
> **bob brazie said:**
> After installing dconf editor I found that my sounds were set at "Custom" I reset the defaults to the "freedesktop" and everything is working fine now.

Thanks for the tip on the nifty utility. I even found a setting to turn off my touch pad which got in the way with my wild typing style and landed the cursor in unknown positions. <g>

Do you know of any documentation for the editor that would lead me to new and fun hacks?

I found this: [http://developer.gnome.org/dconf/unstable](http://developer.gnome.org/dconf/unstable)
And this: [http://developer.gnome.org/dconf](http://developer.gnome.org/dconf)

I have not tried these myself, good luck. :)

---

### Post by m.riz on 2011-11-02
> **yoramdavid said:**
> I am having the same problem since upgrading to buntu 11.10
No login sound.
I do not use the root account, only the normal user account.

Here is what solved my problem: 
Download dconf editor if you haven't already. Then open it and go to "org -> gnome -> desktop -> sound". Once in sound, click on the theme name there (it says freedesktop) and change it to ubuntu (lowercase!) and exit. Log out and log back in, Login sound should now work.

it was work for me :guitar:
I set theme to freedesktop in dconf editor

---

### Post by tedrogers on 2011-11-03
The dconf tweak sorted out my system sounds, e.g. volume control buttons now generate feedback sound events, but my login bonks/congas/drum sound is still nowhere to be heard. :(

Any ideas?

---

### Post by Barney-R on 2011-11-03
I don't know whether this will help, but it worked for me when I lost all sounds from my main "user account", but everything worked normally when I switched to a different "user".

Videos didn't work either, whether on the internet or my hard drive. Sometimes I'd get a blank screen, occasionally an error message, and if the video did show, it was silent, jerky and seriously speeded up.

In System > Preferences > Sound, check that the Hardware and Output tabs point to the same thing. I hadn't knowingly changed anything, but once I'd fixed this, everything was back to normal.

---

### Post by bob brazie on 2011-11-03
I just noticed that the log on sound works but the event sounds don't.

Bob.

---

### Post by tedrogers on 2011-11-03
> **Barney-R said:**
> I don't know whether this will help, but it worked for me when I lost all sounds from my main "user account", but everything worked normally when I switched to a different "user".

Videos didn't work either, whether on the internet or my hard drive. Sometimes I'd get a blank screen, occasionally an error message, and if the video did show, it was silent, jerky and seriously speeded up.

In System > Preferences > Sound, check that the Hardware and Output tabs point to the same thing. I hadn't knowingly changed anything, but once I'd fixed this, everything was back to normal.

Hi.

All of that checks out for me.

The curious thing is that for a Guest account, the login sound works, but doesn't on my User account. But on neither do the Ubuntu Conga Drum login prompt sounds work.

The Ubuntu conga drum sound when presented with the login dialogue should play this file:

/usr/share/sounds/ubuntu/stereo/system-ready.ogg

The login success sound (long choral angelic one) should play this file:

/usr/share/sounds/ubuntu/stereo/desktop-login.ogg

I'm not bothered about 'desktop-login.ogg' - I always disable this anyway, but I miss the 'system-ready.ogg' (Conga Drum) which tells me the computer is ready to login.

Nothing I've tried works, including editing the gconf and dconf in the relevant areas to do with Gnome and Sounds, unless I'm missing something of course.

Any more ideas peeps?

Thanks.

---

### Post by bob brazie on 2011-11-05
I set the default theme as "ubuntu" and checked the event sounds and all is working now.

Thanks for the help!

Bob.

---

### Post by tedrogers on 2011-11-05
> **bob brazie said:**
> I set the default theme as "ubuntu" and checked the event sounds and all is working now.

Thanks for the help!

Bob.

When you say 'all is working now', is your 'system-ready' conga drum sound playing before you login with your password??

---

### Post by bob brazie on 2011-11-06
I use automatic log-on as I am the only one who uses this machine and it is working.

Although if I log on as guest the sound will play too at start-up.

Bob.

---

### Post by Electronicman on 2011-11-06
Try as a may, I cannot get the login sound to work. I went to Startup Apps and set the sound to > /usr/share/sounds/ubuntu/stereo/desktop-login.ogg and .....Nothing. Guess I will have to login as a Guest

Why is this thread [Solved]??

---

### Post by bob brazie on 2011-11-06
I started the thread and fond a solution that worked for me. Sorry. So since it was my question and I found a solution I marked it as solved.

You might start a new thread to work on your situation.

Good luck.

Bob.

---

### Post by bob brazie on 2011-11-06
BTW I checked and the line in mine is:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

You might try replacing yours with this?

Bob.

---

### Post by Electronicman on 2011-11-07
> I started the thread and fond a solution that worked for me I'm sorry, I did not know that the person who starts a thread is the one that has to close it as well. Makes sense.
 
Anyway I tried your suggestion and still no sound. So I'll forget about it for the time being.

---

