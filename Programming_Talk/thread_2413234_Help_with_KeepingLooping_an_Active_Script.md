---
title: "Help with Keeping/Looping an Active Script"
date: 2019-02-22
forum: Programming Talk
---

### Post by jakfish on 2019-02-22
Hello, All,

Running Mate 18.3 on a 7" GPD Pocket 1, I'm trying to remove the text of Chromium's window title bar. I've gotten pretty far, but I'm stuck on executing a pkill command upon closing Chromium:

```

[COLOR=#000000][FONT=Verdana]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]if [[ $(pgrep chromium-browse) ]][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]then[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]mate-terminal --command /home/jake/Scripts_Icons/chro_watch3 ##chro_watch3 is script running only one command: watch --exec bash -c 'wmctrl -r Chromium -T " "'##[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]else[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo pkill -INT watch[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]fi[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]exit 0[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Verdana]Successful tests:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]a) script starts watch command if chromium-browse is running in processes[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]b) script will not start watch command if chromium-browse is not running in processes

The rub is that the script ends once chromium and watch command are started, and I need it to keep running so that when I close chromium, a [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]pkill -INT watch command will be sent.

I've looked hard, but I haven't figured out how to do this, and I'd be appreciative of any help.
Jake[/FONT][/COLOR]

---

### Post by freemedia2018 on 2019-02-22
Like this?

```
while [[ 1 ]] 
do echo you can say that again
sleep .5
done

```

---

### Post by jakfish on 2019-02-22
Many thanks for your post/help.

I had already tried: 

w[COLOR=#000000][FONT=Verdana]hile [ 1 ]; do wmctrl -r chromium -T " "  ; done[/FONT]

[FONT=Verdana]but it gives a 30% spike in cpu usage and I've yet to figure out why. That's why I turned to the watch command, since it was less aggressive.

[/FONT]Jake
[/COLOR][COLOR=#000000][FONT=Verdana]

[/FONT][/COLOR]

---

### Post by spjackson on 2019-02-23
> **jakfish said:**
> 
I had already tried: 

w[COLOR=#000000][FONT=Verdana]hile [ 1 ]; do wmctrl -r chromium -T " "  ; done[/FONT]

[FONT=Verdana]but it gives a 30% spike in cpu usage and I've yet to figure out why. That's why I turned to the watch command, since it was less aggressive.
[/FONT][/COLOR]
What you are missing from freemedia2018's example is a sleep.

---

