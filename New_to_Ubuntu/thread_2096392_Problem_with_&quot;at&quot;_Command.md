---
title: "Problem with &quot;at&quot; Command"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by bobayoga on 2012-12-19
The at command doesn't work when I try to use it. I wish to run transmission-gtk at 20:03.

This is what happens:

$ at 20:03
warning: all commands will be executed using /bin/sh
at> transmission-gtk
at> <EOT>
job 6 at Wed Dec 19 20:03:00 2012

But then, when 20:03 comes by, nothing happens. So next time, I tried to press (ctrl+D) before I press enter. This is what happens:

$ at 20:03
warning: all commands will be executed using /bin/sh
at> transmission-gtk<EOT>
bash: syntax error unexpected token '<'
job 6 at Wed Dec 19 20:03:00 2012

And again, nothing happens when 20:03 comes by.

---

### Post by ubudog on 2012-12-19
This might not be the problem, but try replacing 20:03 with 8:03pm, like so:

```
at 8:03pm
```
```
at> transmission-gtk
```
```
CTRL+D
```

---

### Post by bobayoga on 2012-12-19
Still doesn't work

$ at 9:12pm
warning: commands will be executed using /bin/sh
at> vlc<EOT>
job 10 at Wed Dec 19 21:12:00 2012


Nothing happens

---

### Post by papibe on 2012-12-19
Hi bobayoga.

The DISPLAY variable is not pass to the at's command, which is necessary to load a GUI application:

Try this:
```
$ at 20:30
warning: commands will be executed using /bin/sh
at> [COLOR="Red"]**DISPLAY=:0.0  vlc**[/COLOR]
at> <EOT>

```
Let us know how it goes.
Regards.

EDIT: I have 2 monitors so I have :0.0 and :0.1  if you only have one monitor you should try just :0

---

### Post by bobayoga on 2012-12-22
It worked!

Please accept my sincere gratitude.

May you be well.

---

### Post by papibe on 2012-12-22
:D Glad it worked!

Please mark this thread as SOLVED, when you have the chance ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

