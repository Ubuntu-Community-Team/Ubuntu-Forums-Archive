---
title: "HOWTO disable screensaver and powermanager while mplayer or other apps are running"
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by crazy___cow on 2006-10-26
I have written a small python daemon to disable gnome-screensaver and gnome-powermanager while certain specified apps are running.
It works quite well on Ubuntu Edgy. It requires dbus (>= 0.93), python-dbus, and obviously gnome-screensaver and gnome-powermanager (on gnome 2.16).
The idea is simple: I have seen how Totem is working, and I emulate its behavior with a small python daemon.
To install it just copy "disablegss.py" in /usr/local/bin, fix its execute permissions and create a simple config file in your homedir "~/.disablegss". In this config file add every application name that could stop gnome-screensaver, one for each line. Example:

```
mplayer
gmplayer
vlc
wxvlc
xine
gxine
```

Please notice you must insert the name of the app how you can see it on 'ps aux': for example if you want to add firefox, you must write a line with "/usr/lib/firefox/firefox-bin".
Now just launch disablegss.py on a terminal or simply add it on your session!
You can change the config file on fly (I check if someone modify it), adding or removing apps without restarting it.


**HOW IT WORKS**
Unfortunately the dbus and gnome development documentation are a bit outdated, so I have read totem sources to view which methods are called to stop gnome-screensaver and gnome-powermanager. The idea is if you call the *Inhibit* method of gnome-screensaver, you disable the screensaver AND the powermanager. To enable them again you must call the *UnInhibit* method. There is a small terminal app, dbus-send, to comunicate with dbus but it doesn't work well with these methods, so I decide to use the python dbus interface. This is my first program in python so please tell me if something is wrong or not well coded!
Every 60 secs the daemon check if there are apps running that are also present in the config file. If it's true, the screensaver is disabled. If someone change the config file, the daemon read it again.
I don't think that this small daemon could run on Dapper: the dbus and gnome API change on every release. But you can modify it to fix things. There are only two lines that could be problematic:

Line 38:    cookie = dev.Inhibit(myprogram, 'Disabled by DisableGSS Daemon')
Line 49:    dev.UnInhibit(cookie)

These two methos are different on gnome 2.14 on Dapper. Also dbus has radically changed. If you want to use disablegss.py on Dapper, find the right methods (try to see dapper totem sources) and feel free to change what you want!
To do debug, I suggest you to launch disablegss.py on a terminal and dbus-monitor on another one (you can see all messages from and to dbus daemon). Also change the sleep time value in seconds (line 121) to debug it faster.
Happy coding!

---

### Post by wolf202 on 2006-10-26
great, will try it after I update, this problem has plagued me under windows and the vlc devs have ignored the bugs I have submitted.

-wolf

---

### Post by nyarla33 on 2006-10-29
Thank you very much. Works fine for me.

---

### Post by iggee85 on 2006-10-31
Wow, thanks a lot for this. Solves a really annoying problem with mplayer.

---

### Post by phoqueyoo on 2006-10-31
Good job. :)

---

### Post by 23meg on 2006-10-31
Thanks for the effort, appreciated.

---

### Post by hikaricore on 2006-10-31
> **iggee85 said:**
> Wow, thanks a lot for this. Solves a really annoying problem with mplayer.

Yay now mplayer + screensaver can't break my damn monitor again (for the third time).  Screensaver faded, I attempted to stop it... now that monitor looks like it got coated with 4 coats of clear black no matter what I do, and gamma adjust looks like hell.  Broke a monitor at work a similar way, really weird.  But enough ranting.  Thanks.  :)

---

### Post by neymac on 2007-04-03
Now, in Feisty Fawn Beta we have in the version MPlayer 2:1.0~rc1-0ubuntu8, the option to Stop XScreenSaver, in Preferences=>Misc of the gmplayer.
It works, but when you press the stop button (of mplayer) appears a error message(of mplayer) in a small window that says: "gnome_screensaver_control" .
Does anyone knows if is possible avoid this message (only occurs when I press the Stop Button of MPlayer, if I close it by pressing the "q" there is no error message)?

---

### Post by gtr225 on 2007-04-09
Thanks a lot for this. This problem was frustrating me for ages and for some time I was forced to use totem. Now I can use VLC all the time and not have to worry about the screen saver popping up. I hope the gnome-screensaver developers will integrate this into the next version of gnome-screensaver or perhaps let users choose what programs need to run in order to halt gss. I would have thought the gss developers would have thought of this already but I guess they want everyone using totem :-(

---

### Post by Snapper187 on 2007-05-20
> **neymac said:**
> Now, in Feisty Fawn Beta we have in the version MPlayer 2:1.0~rc1-0ubuntu8, the option to Stop XScreenSaver, in Preferences=>Misc of the gmplayer.
Does Ubuntu use XScreenSaver by default?

I'm still on Edgy and not sure if I changed things, but right now I don't think I use XSS: If I start mplayer with that option (it's already available in Edgy's mplayer package), I get:

*xscreensaver_disable: Could not find XScreenSaver window.*

---

### Post by weaver4 on 2007-06-04
Has anyone tried this with Fawn?  Does it work?

---

### Post by gtr225 on 2007-06-04
When I upgraded from 6.10 to 7.04, I made no changes to disable gss and it seems to still be working without any trouble.

---

### Post by rapiddl on 2007-09-04
great script work fine in feisty no modification needed. Like the mplayer function which allows you to stop gnome-screensaver this should be in all the video players.
Thx great script real handy

---

### Post by serzz on 2007-10-01
Not working for me in gutsy gives this:

disablegss.py: 23: import: not found
disablegss.py: 24: import: not found
disablegss.py: 25: import: not found
disablegss.py: 26: import: not found
disablegss.py: 27: import: not found
disablegss.py: 28: import: not found
from: can't read /var/mail/stat
disablegss.py: 33: Syntax error: "(" unexpected

---

### Post by crazy___cow on 2007-10-21
I upgrade to gutsy and it works perfectly. Try to check you python configuration....

---

### Post by rpglover64 on 2007-10-27
My only comment on the script is that it stops the screensaver when mplayer plays audio only.

As for mplayer's stop-xscreensaver option, it works, but it has a weird pause before playing the movie.  it pauses after the following output:

VIDEO:  [DX50]  720x540  24bpp  23.976 fps  948.0 kbps (115.7 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.1.1a (build 1155/release)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled

I'm using feisty with no screensaver but the default (at least to my knowledge).

---

### Post by lckdanny on 2007-11-22
Thanks.
I just to looking a method to disable the screensaver when playing mplayer.

Thanks.

---

### Post by MozartlovesUbun2 on 2007-11-23
**how come this isnt already implanted as default in the various players?**

when watching a movie the screen goes black every 15 minutes, how silly

i cant find  any option in Gutsy power management that allows me change that either

---

### Post by DasCrushinator on 2008-06-06
Does anyone know exactly what ALL of the packages I would need to download and install for Hardy to get this to work are?

---

### Post by ha.fernando on 2008-07-10
Thanks

---

### Post by xen-uno on 2008-08-24
Crazy's list of necessary packages: dbus (>= 0.93), python-dbus, gnome-screensaver, and gnome-powermanager (on gnome 2.16) is all you need.

So I've tried his script on Hardy 8.04 x64 and it works with the following exceptions:

1) Will not work on programs that can't be minimized to the taskbar. OpenArena is classic example and the main reason I went searching for a disabler in the 1st place.

2) Will not work on programs that are in system tray, but not present as running program in taskbar. Example: Amarok (amarokapp to system). >> not so sure about this one now ... works as intended ATM <<

3) The disabler list is not re-entrant. Changes to the list must be accompanied by logoff - login. The script does not autoload but will if placed as new item in System>Preferences>Sessions

... the search continues ...

---

### Post by ffixcollector on 2009-03-21
i get this error in intrepid:

```
DisableGSS: config file ~/.disablegss doesn't exist! Write it by hand. 
Add applications name that could disable gnome screensaver: 
one app name for every line of file.

```

I'm not sure if the permissions are wrong, or what. I have the config file in /home/username/.disablegss

---

### Post by Lockheed on 2009-09-13
Is it possible to mod this patch so that screensaved doesn't kick in only if mplayer(smplayer) is playing the movie? 
That mean if the movie is paused, the power manager/screensaver would work normally.

---

### Post by bako on 2009-11-27
what about the 9.10?
i'd the same problem.
it might works?

---

### Post by DracoMoye on 2009-12-03
I confirm it working with 9.10

---

### Post by reddox on 2009-12-12
The inhibitor applet in the gnome-panel does the same thing right?

---

### Post by sisco311 on 2009-12-12
It seems that this application is no longer actively developed/maintained.

You may want to try Caffeine.

*[Caffeine]("http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page") is a system applet that allows the user to temporarily inhibit both the screensaver and the sleep power saving mode, simply by clicking on it. This could be useful for example when watching long flash videos or playing certain full screen games that don't inhibit the screensaver by themselves.*

---

### Post by meklu on 2009-12-18
Works like a charm in Karmic 64-bit with self-compiled MPlayer and FFmpeg and the repo-SMPlayer (added line "smplayer" to config file, just for sure). Well done.

---

### Post by &gt;:3 on 2009-12-20
> **sisco311 said:**
> It seems that this application is no longer actively developed/maintained.

You may want to try Caffeine.

*[Caffeine]("http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page") is a system applet that allows the user to temporarily inhibit both the screensaver and the sleep power saving mode, simply by clicking on it. This could be useful for example when watching long flash videos or playing certain full screen games that don't inhibit the screensaver by themselves.*
Dude, I've been looking for an applet that does *precisely* this for almost 2 years now. 

You've made my day.

---

