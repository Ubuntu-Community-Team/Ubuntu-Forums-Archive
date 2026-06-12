---
title: "Flash, etc.etc, avm2"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by earthshakergb on 2012-05-17
Ubuntu 12.04

I am really coming to believe that if you want to watch embedded video in Ubuntu...use Windows. I know this had been beaten to death and then some.

I have the latest gnash, the latest VLC player, have tried all the supposed fixes on here, all the plugins are up to date, for firefox. 
So I tried chromium, I have read it works, well not really. You Tube videos play fine if they are AVM1, according to the gnash properties.

What is with the AVM2 format that nothing likes to play. I have the latest FFMPEG installed from the software center, still nothing works, well I can't really say nothing...I see the play button and the "circle of circles" spinning for about 10 milliseconds, then nothing.
This is really just an annoyance for me, I do have Windows, two versions, up and running.

---

### Post by jtarin on 2012-05-17
[Try adding Medibuntu repository]("http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/"):a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons,

---

### Post by earthshakergb on 2012-05-17
Tried and failed. No change. Still no embedded video on sites other than YouTube.

---

### Post by anewguy on 2012-05-18
I think I remember reading on the web somewhere that starting with Flash 9 for Linux, they were moving away from actionscript and going to something they call flex2.  I have no idea if that messed things up for avm2 (actionscript) or not.  If it did, perhaps the Windows versions of Flash still have some sort of support built in.

Dave ;)

---

### Post by anewguy on 2012-05-18
There is also an open bug report on launchpad for this - the latest posting there was 4/2012: [https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/202391]("https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/202391")

Throughout the things I have found on the net, one post indicated they were moving away from actionscript, which is what avm2 is.  Others claim that they moved TO avm2 in flash 9.  There are many posts on using gnash and lightspark to get avm2 support.  So, it's a little confusing out there.

What I would try, and this is just me:
[LIST]
[*]completely remove all existing flash player(s)
[*]install gnash with the package manager and try it.  If that doesn't work:
[*]install lightspark with the package manager and try it again.
[*]If the above steps don't improve things, then use the package manager to remove them and reinstall the flashplayer-plugin from the package manager (or you could try flashaid).
[/LIST]
Some of us have no luck with videos and flash player (the default when you install now is something like flash 11.2xxxxxx).  Let us know what your results are from the above steps.

Dave ;)

---

### Post by earthshakergb on 2012-05-18
Did that already, not a big deal. But this little PITA, needs fixed. It could be enough to really turn new Ubuntu users off. 
When you are trying to do convert users from Windows to Ubuntu, and these people like watching embedded videos. They will find out they can't watch all the videos they want to, they will probably dump Ubuntu  altogether, and stay with what works.
I will not waste any more time trying things, for now, and coast for a few months, see if a master solution appears.

---

### Post by anewguy on 2012-05-18
Don't count on it.  I've had problems with flash since before 12.04.  Top that off with what people have been posting:  Adobe won't be supporting the Linux port after the current release.  Rumor also has it they aren't putting any more work into the current release for Linux - in other words, no patches.  If anything is to come of this and "fix" many of our problems, it's going to need to be an open-source solution.  I wonder if we can get Adobe to release the code for the Linux flash player so it can be further debugged and enhanced in the open-source community.

---

### Post by jtarin on 2012-05-18
Can you give a link(s) to these files your having problems with?

---

### Post by earthshakergb on 2012-05-18
I can try, it might take a bit, I am running two different profiles, two computers, they are not set up the same (on purpose).
[http://qrznow.com/?p=3147](http://qrznow.com/?p=3147)
Try this one, works in windows not in Ubuntu I am using Gnash, I right click on the black square, select file>properties>stage properties and next to root VM version it reads AVM2(unsupported)

---

### Post by jtarin on 2012-05-18
> root VM version
Your running Ubuntu in a VM?

---

### Post by earthshakergb on 2012-05-18
Don't think so, I didn't select that option when installing, should be straight up.


Not that kind of VM, this is from the Gnash project wiki
**  What is AVM2? **

 The latest Adobe ActionScript Virtual Machine, the standards-based  scripting language engine in Adobe Flash Player 9. It executes  ActionScript 3.0.

---

### Post by earthshakergb on 2012-05-18
Just noticed this also, I played a video on Ubuntu, the audio was good, the video, however not so much. It stuttered real bad, looked more  like a stop motion animation than a video..
The exact same video played on the same computer on XP was perfect (well as perfect as a YouTube video could be.
It takes me just a couple of minutes to switch from XP to Ubuntu, so if I can do some comparisons from one to the other let me know. I also have a video camera that I can record the screens with, for a side by side, not sure how to do a side by side, but I bet I could figure something out.

---

### Post by jtarin on 2012-05-19
I'll check that link on my Ubuntu machine when I get home and get back to you. If you have any other links it would be helpful.

---

### Post by jtarin on 2012-05-19
> **earthshakergb said:**
> I can try, it might take a bit, I am running two different profiles, two computers, they are not set up the same (on purpose).
[http://qrznow.com/?p=3147](http://qrznow.com/?p=3147)
Try this one, works in windows not in Ubuntu I am using Gnash, I right click on the black square, select file>properties>stage properties and next to root VM version it reads AVM2(unsupported)
OK...tried that one and runs fine in my browser with Flash 11.

---

### Post by earthshakergb on 2012-05-19
[twit.tv/shows]("http://ubuntuforums.org/twit.tv/shows")
I grabbed a couple of random shows from here.
There are still images at the start, after clicking the play button there is the ever popular black rectangle, no audio no video.

---

### Post by jtarin on 2012-05-19
> **earthshakergb said:**
> [twit.tv/shows]("http://ubuntuforums.org/twit.tv/shows")
I grabbed a couple of random shows from here.
There are still images at the start, after clicking the play button there is the ever popular black rectangle, no audio no video.
Bad URL.:mad:

---

### Post by earthshakergb on 2012-05-19
[http://twit.tv/shows](http://twit.tv/shows)
My bad try this

---

### Post by fooman on 2012-05-19
tried your links here and they all play fine for me (12.04, 64bit).  i have the *flashplugin-installer 11.2* which (i assume) was installed along with the *ubuntu-restricted-extras* package that i added after installing ubuntu and running all available updates.

i personally,  have never used gnash or any other flash alternatives....the flash from the repositories, although flakey at best...usually works fine on all my machines.  when i do have any issues,  i install flash-aid from the firefox add-ons:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=search)

i would try that if you have not already done so.  it will clean up gnash and any other things that may be affecting your playback,  then install flash + a few tweaks to help it work a little better (hopefully).

good luck

---

### Post by jtarin on 2012-05-19
Links play fine here also.Flash plugin in my /.mozilla/plugins folder. I downloaded it and extracted the plugin and manually placed it.

---

### Post by earthshakergb on 2012-05-19
Fooman, flash-aid was installed- flash installed no change.

jtarin, pm me a step by step I will try your approach.

---

