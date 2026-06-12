---
title: "getting Opera to play video"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-04
I just downloaded Opera just to give it a whirl.  I like it but I cannot get video to play.  I click on video and M player comes up.  Shows a status bar as playing.  But get blank screen.  I must need to config something.  Any suggestions.  I am really enjoying this part of Linux.  Getting to pick and choose what I want to use is great.

Mark shuman

---

### Post by SunnyRabbiera on 2008-05-04
are you running flash videos?

---

### Post by phread59 on 2008-05-04
yea I guess so.  Firefox can play everything just fine.  opera doesn't display.  I wonder if there is a setting to enable flash in opera.

Mark Shuman

---

### Post by SunnyRabbiera on 2008-05-04
ah there lies your problem, flash doesnt work with opera if you are using opera 9.27.
With opera you may want to try the beta version instead, like when you click on the link on the main page dont choose the options the site gives you and click on the link to the latest beta...
here is a link to the beta's page:
[here]("http://www.opera.com/download/linux/?ver=9.50b2")
and just install the beta, and remove the one you have installed now.
Now take one note though, you see the little pulldown menu that has ubuntu in it?
you may actually want to click on that and select the other/static DEB option as it tends to look a little cleaner, and it will still work with your system

---

### Post by phread59 on 2008-05-04
Yup that's exactly what I did.  I have B2 installed.  I guess flash is still not supported.  Shame I really like Opera.  I guess I'll keep it and hope they add it in the future.

Mark Shuman

---

### Post by TeoBigusGeekus on 2008-05-04
> **SunnyRabbiera said:**
> ah there lies your problem, flash doesnt work with opera if you are using opera 9.27.

Yes it does...
[http://ubuntuforums.org/showthread.php?t=745325]("http://ubuntuforums.org/showthread.php?t=745325")

---

### Post by jviscosi on 2008-05-04
IIRC, the mplayer plugin hangs the Opera plugin framework unless it's compiled with some option or other set in configure.  I did this a while back and it does work for me, so let me go check the directory where I compiled mplayer plugin.  Back in a sec ...

Okay, the option is:

```

./configure --enable-x

```And then you compile mplayer and put the plugin files in the Opera plugin directory.  Given that this is the "Absolute Beginner" forum, though, compiling mplayer plugin is probably not an optimal solution.  So I also found [this post]("http://list.opera.com/pipermail/opera-linux/2007-September/009603.html") purporting to be from the author of mplayerplug-in, who has another suggestion:

> gecko-mediaplayer with gnome-mplayer is the recommended plugin to use
with Opera.

You can get them here

[http://dekorte.homeip.net/download](http://dekorte.homeip.net/download)

I wrote mplayerplug-in and also have written gecko-mediaplayer and have
been having some success with the Opera Alpha and the gecko-mediaplayer
cvs code. I have been working with the Opera plugin team to get any
issues we find worked out. So while not perfect we are making great
progress.

Kevingecko-mediaplayer and gnome-mplayer are both in the Graphics (multiverse) repository so you shouldn't actually have to grab them from the site he mentions.  Anyway, hope this helps.

Incidentally, Hardy seems to have broken mplayerplug-in for me in Firefox and Seamonkey, although my compiled version in Opera still works.  I haven't gotten around to fixing it yet ...

---

### Post by evertsfnic on 2008-05-04
Yeah me too, I like opera, but i can not install in linux the flash stuff, For opera it's the best browser......

---

### Post by dstin1 on 2008-05-04
Try running this line to link flash to opera if you are using the beta version

 sudo ln /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/opera/plugins/

if that doesn't work follow this guide.
[http://sysblogd.wordpress.com/2007/08/01/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/]("http://sysblogd.wordpress.com/2007/08/01/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/")

as a side note I had to remove the current flash and reinstall.

---

### Post by kansasnoob on 2008-05-04
I know it's a matter of preference, but I just can't imagine life without Firefox!

I began looking for Explorer alternatives when Microsoft dropped support for 98 & ME and IMHO Firefox is simply more user friendly and damn secure!

I used Firefox w/ME on one puter until about 3 months ago (until the hardware died) with no problems!

---

### Post by houstonasl on 2008-05-05
> **SunnyRabbiera said:**
> ah there lies your problem, flash doesnt work with opera if you are using opera 9.27.
With opera you may want to try the beta version instead, like when you click on the link on the main page dont choose the options the site gives you and click on the link to the latest beta...
here is a link to the beta's page:
[here]("http://www.opera.com/download/linux/?ver=9.50b2")
and just install the beta, and remove the one you have installed now.
Now take one note though, you see the little pulldown menu that has ubuntu in it?
you may actually want to click on that and select the other/static DEB option as it tends to look a little cleaner, and it will still work with your system

this is my absolute first post to this forum as i am a brand spanking new windows defector so really really look forward to support from this community. i would though like to add that when i had opera 9.27 i couldn't get flash to play to save my life. i'm sure i'm just too noob to have worked out the technical kinks as i'm sure it is possible, but i just installed the beta 9.5 and it works like a charm. already i'm getting help from the community and would like to say a big thank you all.

---

### Post by thiebaude on 2008-05-05
SunnyRabbiera, thanks my flash now works in this beta Opera.before it didn't.

---

