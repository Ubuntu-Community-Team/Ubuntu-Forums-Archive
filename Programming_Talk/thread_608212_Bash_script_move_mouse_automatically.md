---
title: "Bash script: move mouse automatically"
date: 2007-11-09
forum: Programming Talk
---

### Post by hazica on 2007-11-09
Hello.

I configured my infra-red remote control to power off my monitor using this little script I found somewhere
```
#!/bin/bash

STATUS=`xset -q | grep "Monitor is" | awk '{print $3}'`

if [ "${STATUS}" = "On" ]
then
   xset dpms force off
else
   xset dpms force on
fi
exit 0

```
It works just swell if I want to turn the monitor off . If I press the power button on my remote again, the monitor turns on (it returns from sleep mode) but remains blank. In order to see my desktop again, I have to either move the mouse or press a key on the keyboard.

So I was thinking of writing a script that automatically moves the mouse just a tiny little bit and running this script right after *xset dpms force on*, in the else branch. The problem is that I am clueless when it comes to writing scripts that simulate mouse movements.

Bottom line: I'm either looking for a script that can move the mouse or some  alternative(less goofy) solution to my problem.

I'd appreciate your help.

Thanks.

---

### Post by stylishpants on 2007-11-09
It would be easier to send a button press event.

```
xsendkeys Shift_L
```

---

### Post by hazica on 2007-11-09
Thanks for your simple solution, mate!

Works like a charm.

---

### Post by dwhitney67 on 2007-11-10
Thanks for the post... it gave me a good chuckle.

It would be awesome to write some code that could move the mouse!  I knew what you meant... the mouse "pointer" or "cursor", but to physically move the mouse, that would have been something to see.

Anyhow, I'm glad you resolved your little problem.

---

### Post by hazica on 2007-11-10
Actually, the idea for moving the mouse *pointer/cursor* in order to keep the monitor on, comes from an older xkcd comic:

[http://xkcd.com/196/]("http://xkcd.com/196/")

---

### Post by fatalerr on 2008-05-03
if anyone's interested

```
xte 'mousermove 1 1'
```

---

### Post by omrsafetyo on 2008-05-03
What do you need installed for the xte and xsendkeys?

---

### Post by y-lee on 2008-05-03
> What do you need installed for the xte and xsendkeys?

xte is found in the [xautomation package]("http://packages.ubuntu.com/hardy/xautomation")

And I am not sure but  I think xsendkeys is found in the [lineakd package]("http://packages.ubuntu.com/hardy/lineakd").

---

### Post by debbuntu on 2011-09-09
This is quite wonderful. Thanks guys. :-)

---

### Post by lodp on 2011-10-25
I'd like to use this xte thing to combat a screen saver that resists all attempts to be switched off. And it works from the terminal - the mouse moves one pixel to the right and one down. But on a cronjob the mouse pointer won't move. 

Here's the crontab line, with an additional command for debugging:
> 
*/1 * * * * /usr/bin/xte 'mousermove 1 1' && echo 'mouse wiggled!' >> /tmp/mousecron.log

The cronjob's working, I get the log entry every minute, but the mouse won't move like it does when entering the command in a terminal. Tried root crontab too, to no avail. Anyone?

---

### Post by erind on 2011-10-26
> **lodp said:**
> ...
The cronjob's working, I get the log entry every minute, but the mouse won't move like it does when entering the command in a terminal. Tried root crontab too, to no avail. Anyone?
That's because cron doesn't have a tty assigned, try this instead:

```
*/1 * * * * export DISPLAY=:0 && /usr/bin/xte 'mousermove 1 1' && echo 'mouse wiggled!' >> /tmp/mousecron.log 
```Also, an infinite loop with *xte* command inside, can be used and placed in the Startup Applications for the same purpose.

---

### Post by lodp on 2011-10-26
thanks so much erind, works like a charm now. I'm going to stick to the cronjob until I've figured out how to turn off screen blanking.

---

