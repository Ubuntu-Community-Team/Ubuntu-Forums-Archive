---
title: "cannot launch terminal and much more"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by timidly.leery on 2013-12-09
13.10. Screen black, no panel, no launcher, just cursor. keyring login came up and was able to enter password successfully but that is all. cannot access terminal with ctrl+alt+t. right click does not give access to settings. ctrl+alt+F1 does bring up tty but unable to comply with request for username (I have not been asked for it since installation long ago and I don't remember, hell, I don't well remember what I was exactly doing this morning to initiate these troubles...mucking around with Ubuntu Tweaks trying to lighten the panel changing opacity? Don't think I found the setting... 

Have broken Unity before, if that's what I've done here, but managed to get back by copying and pasting corrections into terminal but I am stuck. Help would be much appreciated.

---

### Post by philinux on 2013-12-09
If u got a terminal reset unity and compiz.

dconf reset -f /org/compiz/

Then

setsid unity

---

### Post by timidly.leery on 2013-12-09
[COLOR=#000000]thanks but 

"cannot access terminal with ctrl+alt+t", is there some other way?

[/COLOR][COLOR=#000000]"ctrl+alt+F1 does bring up tty but unable to comply with request for username..." failure to know name is restricting access to tty[/COLOR]

---

### Post by deadflowr on 2013-12-09
Can you boot into recovery mode?

If you can, open the root shell(or whatever it's called)
and run
```
ls /home
```

This should at least give you the username in that listing.
then try the above commands to reset unity and compiz.

---

### Post by Impavidus on 2013-12-09
In case you lost your password too, see [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). This tells how to reach a recovery console or root shell too. With that you should be able to login to tty1.

---

### Post by timidly.leery on 2013-12-09
[COLOR=#000000]retrieved username via instructions, thank you.

dconf reset -f /org/compiz/ yields

[/COLOR][COLOR=#000000]error: Error spawning command line 'dbus-launch --autolaunch=f5585e9d6560af91d536c9fe50c68573 --binary-syntac --close-stderr ': Child process exited with code[/COLOR]

[COLOR=#000000]Usage:[/COLOR]
[COLOR=#000000]dconf reset [-f] PATH[/COLOR]

[COLOR=#000000]Reset a key or dir. -f is required for dirs.[/COLOR]

[COLOR=#000000]Arguments:[/COLOR]
[COLOR=#000000]PATH Either a KEY or DIR[/COLOR]
[COLOR=#000000]KEY A key path (starting, but not ending with '/')[/COLOR]
[COLOR=#000000]DIR A directory path (starting and ending with '/')

entered 
[/COLOR][COLOR=#000000]setsid unity
anyway but still no panel, launcher, terminal via ctrl+alt+t.

unity command in terminal yields 

[/COLOR]*WARNING*[COLOR=#444444][FONT=arial]: [/FONT][/COLOR]*no DISPLAY variable*[COLOR=#444444][FONT=arial] set, setting it to :0

[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]GLib-WARNING **: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). Most likely the process is ignoring SIGCHLD, or some other thread is invoking waitpid() with a nonpositive first argument; either behavior can break applications that use g_child_watch_add()/g_spawn_sync() either directly or indirectly.
[/FONT][/COLOR][COLOR=#444444][FONT=arial]
compiz (open gl) Error FBO is incomplete: GL:: FRAMEBUFFER_UNSUPPORTED (0x8cdd)
[/FONT][/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by steeldriver on 2013-12-09
Usually you can only run the dconf compiz reset from inside the desktop session - you may be able to get it to attach to the running dbus instance from your virtual console by setting the DISPLAY environment variable appropriately e.g.

```
**DISPLAY=:0** dconf reset -f /org/compiz/
```

```
**DISPLAY=:0** setsid unity
```

or just export the variable first

```

[B]export DISPLAY=:0
[/B]dconf reset -f /org/compiz/
setsid unity

```

In case the X server didn't start on display :0 (sometimes happens if you also run headless sessions) then you can check the output of ps e.g.

```
ps -ef | grep vt[7]
```

---

### Post by timidly.leery on 2013-12-09
Yes, that brought back panel and launcher. Wish I understood what transpired. Any simple explanation? Why cursor visible, why login keyring but nothing else? Why is it so easy to break unity and why not so easy to regain? 

More importantly... thank you all, especially [[COLOR=#000000]deadflowr[/COLOR]]("http://ubuntuforums.org/member.php?u=1276577")[COLOR=#000000]  and [/COLOR][COLOR=#DD4814][COLOR=#000000][steeldriver]("http://ubuntuforums.org/member.php?u=1627500").  [/COLOR][/COLOR]

---

