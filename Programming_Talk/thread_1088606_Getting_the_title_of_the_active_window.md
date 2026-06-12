---
title: "Getting the title of the active window"
date: 2009-03-06
forum: Programming Talk
---

### Post by Arancaytar on 2009-03-06
(I'm not sure if this is the right forum for a gnome/metacity specific question, but it is a programming issue after all.)

I would like to run a program as a background process on my computer that keeps track of which window was active at what time. The log output would be something like:

```
2009-03-06 13:54:34 VLC Media Player
2009-03-06 13:57:02 Ubuntu Forums - Post New Thread - Firefox
```

 I'd prefer to make a script that listens for something like a "window change" event.

```
# pseudo-code

bind MyHandler to WindowChangeEvent

def MyHandler
  title = getActiveWindow().title
  logfile << getCurrentTime + " " + title
end
```

If that doesn't exist I could also write a program that polls and sleeps a few times per second (I'd have to test that interval for a compromise between performance and granularity).

```
title = getActiveWindow().title

while(true)
  if (title != getActiveWindow().title)
    logfile << getCurrentTime + " " + title
    title = getActiveWindow().title
  end
  sleep(a while)
end
```

Unfortunately, I have no idea how to interface with the gnome window manager, and a cursory Google search didn't bring up a documentation site. Can I find an API somewhere?

---

### Post by canchete on 2009-04-23
> **Arancaytar said:**
> (I'm not sure if this is the right forum for a gnome/metacity specific question, but it is a programming issue after all.)

I would like to run a program as a background process on my computer that keeps track of which window was active at what time. The log output would be something like:

```
2009-03-06 13:54:34 VLC Media Player
2009-03-06 13:57:02 Ubuntu Forums - Post New Thread - Firefox
```

 I'd prefer to make a script that listens for something like a "window change" event.

```
# pseudo-code

bind MyHandler to WindowChangeEvent

def MyHandler
  title = getActiveWindow().title
  logfile << getCurrentTime + " " + title
end
```

If that doesn't exist I could also write a program that polls and sleeps a few times per second (I'd have to test that interval for a compromise between performance and granularity).

```
title = getActiveWindow().title

while(true)
  if (title != getActiveWindow().title)
    logfile << getCurrentTime + " " + title
    title = getActiveWindow().title
  end
  sleep(a while)
end
```

Unfortunately, I have no idea how to interface with the gnome window manager, and a cursory Google search didn't bring up a documentation site. Can I find an API somewhere?


Hi,
I was looking for the same functionality and I found the libwnck gnome library. It has wnck_screen_get_active_window() function, which seems to return an object with info about the current window. I haven't tested this, you could try to install libwnck-dev package and test it.

Tell me if it works and good luck!
Ruben.

---

### Post by emmiesix on 2009-07-29
Did you ever get this working?

I am looking to do the EXACT same thing as yet another tactic to combat my severe ADD. 

All the "time tracking" software out there seems geared towards billable hours and requires manual entry - not gonna work.

I want to track how often and how long I get derailed, particularly, by browsing when I should be getting back to coding.  Tracking the active window should do what I want.

I'm a scientific programmer (read: next to useless for practical programming) but I do have some knowledge of scripting, so I might work on this if you even got some parts of it done (or, you know, a whole script that I could steal! :) :) )

---

### Post by stroyan on 2009-07-29
You could use xprop to look for the properties set by the window manager and the current active application.
```

#!/bin/bash
read D1 D2 D3 D4 ID <<<$(xprop -root _NET_ACTIVE_WINDOW); xprop -id $ID WM_NAME

```
It is also possible to request notification of property changes.
The "xprop -spy" option shows how that can work.
But using the output of "xprop -spy" would be delayed by stdio buffering unless you used something like expect to send its output to a tty device to get line buffering.

---

