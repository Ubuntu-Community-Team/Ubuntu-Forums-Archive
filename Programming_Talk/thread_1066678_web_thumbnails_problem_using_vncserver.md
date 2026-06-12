---
title: "web thumbnails: problem using vncserver"
date: 2009-02-11
forum: Programming Talk
---

### Post by stuair on 2009-02-11
Hi,

I'm been looking all over the net but can't seem to find an answer to my problem. I'm trying to create a screenshot of a website using a vncserver and imagemagick.

Here is what I run to achieve this...

```
vncserver :1 -geometry 1024x768 -depth 24
```

I have created a script to run to create the screenshot:

```

#!/bin/bash
export DISPLAY=":1"
/usr/bin/firefox --display :1 "$1" > /dev/null 2> /dev/null &
/bin/sleep 10
/usr/bin/import -window root -display :1 "$2"
killall firefox

```

The script is run like:

```
sh screenshot.sh http://www.google.com/ /test.jpg
```

However I currently only get a small [640x480 firefox window.]("http://www.stuhol.com/test.jpg") 

I'm guessing it is something to do with my vncserver conf but not sure what it could be, any ideas?

---

### Post by stuair on 2009-02-11
Solved:

I needed to edit my ~/.vnc/xstartup.

On the last line replaced
```
twm &
```

With
[HTML]x-window-manager &[/HTML]

Solved

---

