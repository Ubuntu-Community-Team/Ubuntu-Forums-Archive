---
title: "cron and gnome-screensaver"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by PinkFloyd102489 on 2008-05-21
Ive been trying to get this script to work forever. It works for the most part except for the bit about killing off the screensaver.

```

#!/bin/bash

# WSTP stream with VLC
export DISPLAY=:0 && vlc mms://wma1.viastreaming.net/wstp --volume 500 &

# Set Pidgin status available
/usr/bin/purple-remote "setstatus?status=available&message="

# Turn monitor on and unlock screensaver
export DISPLAY=:0 && xset dpms force on
export DISPLAY=:0 && gnome-screensaver-command -dp

# Turning on lamp
/usr/local/bin/heyu flightson A

```

As you can see, everything looks in order. Got the variable exported so that everything should run on the GUI, but the screensaver command does nothing at all. It executes fine from the terminal but not from cron. Is there anything I can do to fix this?

---

### Post by sdennie on 2008-05-21
Do you have your screensaver setup to lock the screen with a password?  If so, gnome-screensaver-command -dp will not be able to unlock it without user interaction.

---

### Post by sdennie on 2008-05-21
Wow, I was completely wrong about gnome-screensaver-command -dp not being able to unlock the screen:

```

gnome-screensaver-command -l ; sleep 5 ; gnome-screensaver-command -dp

```

Works just fine.  I have no idea if this will help but, you only need to export DISPLAY once and, in reality, it should be a single:

```

export DISPLAY=:0.0

```

Other than that, I can't think of anything that would prevent it from working.  Unless of course, something in your environment needs to be included in the script.  If the above doesn't work, maybe try adding the following to the top of your script:

```

export XAUTHORITY=/home/your_user_name/.Xauthority

```

---

### Post by PinkFloyd102489 on 2008-05-21
After poking around a bit, I found out that gnome-screensaver-command has a bug that wont allow cron to interact with it.

I "fixed" it by switching to xscreensaver, mainly because it has Flurry also and I love my Flurry. :-)

---

