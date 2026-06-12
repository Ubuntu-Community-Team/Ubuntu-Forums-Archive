---
title: "Using a video on your lock screen"
date: 2014-12-23
forum: New to Ubuntu
---

### Post by pyth0n2 on 2014-12-23
Hey there ubuntuforums community.

I am new to Ubuntu and would like to ask an random question that you can probably already guess from the title.

I have a 10 second video clip and I would like it to play on a loop whenever I leave my computer alone.
Is this possible?

Thanks for any solutions

---

### Post by CantankRus on 2014-12-23
The only way I know how would be to use a different screenlocker
and run a fullscreen totem window.
Open the Videos application(totem) and in the Edit Menu, choose "Repeat mode" to loop.
eg...
```
xtrlock & totem --fullscreen "[COLOR="#FF0000"]**/path/to/video**[/COLOR]"
```
xtrlock replaces the mouse cursor with a small blue lock when the screen is locked.
(You can compile a version that removes the blue lock symbol)
Type in password and press enter to unlock. See **man xtrlock** before using.
You could bind this to a shortcut key using as the command...
```
sh -c 'xtrlock & totem --fullscreen "[COLOR="#FF0000"]**/path/to/video**[/COLOR]"'
```
[COLOR="#FF0000"]**Use your path to a video**[/COLOR]

If you want the vid to play after a set screen idle time you can use **xautolock**.
> Xautolock monitors input devices under the X Window System, and launches a
program of your choice if there is no activity after a user-configurable
period of time.
The minimum idle time you can set is 1 minute.
The normal screensaver settings still run.
See "man xautolock"

This command can be used in startup applications.
Test in terminal using [COLOR="#FF0000"]**your path to a video**[/COLOR].
After 1 minute of inactivity the screen should lock and you video start playing.
```
xautolock -notify 10 -notifier 'notify-send "Screen will lock in 10 seconds"' -time 1 -locker 'xtrlock & totem --fullscreen "[COLOR="#FF0000"]**/path/to/video**[/COLOR]"'
```
Need to install xautolock and xtrlock.

---

### Post by David_Camp on 2014-12-23
Oh, it's great tuts to do. Just change it.

---

### Post by pyth0n2 on 2014-12-24
> **CantankRus said:**
> The only way I know how would be to use a different screenlocker
and run a fullscreen totem window.
Open the Videos application(totem) and in the Edit Menu, choose "Repeat mode" to loop.
eg...
```
xtrlock & totem --fullscreen "[COLOR=#FF0000]**/path/to/video**[/COLOR]"
```
xtrlock replaces the mouse cursor with a small blue lock when the screen is locked.
(You can compile a version that removes the blue lock symbol)
Type in password and press enter to unlock. See **man xtrlock** before using.
You could bind this to a shortcut key using as the command...
```
sh -c 'xtrlock & totem --fullscreen "[COLOR=#FF0000]**/path/to/video**[/COLOR]"'
```
[COLOR=#FF0000]**Use your path to a video**[/COLOR]

If you want the vid to play after a set screen idle time you can use **xautolock**.

The minimum idle time you can set is 1 minute.
The normal screensaver settings still run.
See "man xautolock"

This command can be used in startup applications.
Test in terminal using [COLOR=#FF0000]**your path to a video**[/COLOR].
After 1 minute of inactivity the screen should lock and you video start playing.
```
xautolock -notify 10 -notifier 'notify-send "Screen will lock in 10 seconds"' -time 1 -locker 'xtrlock & totem --fullscreen "[COLOR=#FF0000]**/path/to/video**[/COLOR]"'
```
Need to install xautolock and xtrlock.


That worked perfectly, thank you very much :)

---

