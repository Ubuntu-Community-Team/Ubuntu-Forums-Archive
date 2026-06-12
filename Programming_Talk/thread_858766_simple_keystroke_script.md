---
title: "simple keystroke script"
date: 2008-07-13
forum: Programming Talk
---

### Post by cartisdm on 2008-07-13
I want to run a command from kAlarm.  I need to have the keystrokes "ctrl + R" pressed at a certain time to initial something.  kAlarm allows for scripts so could someone create a simple script that makes the computer think I pressed those keys?

---

### Post by nanotube on 2008-07-14
> **cartisdm said:**
> I want to run a command from kAlarm.  I need to have the keystrokes "ctrl + R" pressed at a certain time to initial something.  kAlarm allows for scripts so could someone create a simple script that makes the computer think I pressed those keys?

the following references may be of use:
[http://search.cpan.org/~ctrondlp/X11-GUITest-0.21/GUITest.pm](http://search.cpan.org/~ctrondlp/X11-GUITest-0.21/GUITest.pm) (perl)

[http://osdir.com/ml/misc.misterhouse.user/2003-07/msg00207.html](http://osdir.com/ml/misc.misterhouse.user/2003-07/msg00207.html) (c)

[http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html#SEC13](http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html#SEC13) (python)

---

### Post by cartisdm on 2008-07-14
Awesome for the info, but my programming knowledge registers about a .5 on the scale.  I don't particularly have the time to invest in learning it right now either.  Anyone wanna help a brother out and put together a simple script?

---

### Post by nanotube on 2008-07-15
> **cartisdm said:**
> Awesome for the info, but my programming knowledge registers about a .5 on the scale.  I don't particularly have the time to invest in learning it right now either.  Anyone wanna help a brother out and put together a simple script?

well ok, here's a little c program to send control-r to the active application:
```
#include <X11/extensions/XTest.h>

#define KEY_DOWN True
#define KEY_UP   False

#define KEYCODE_LCONTROL 37
#define KEYCODE_R 32

int main() {
  Display *dpy = XOpenDisplay(NULL);
  if (!dpy) return 1;
  XTestFakeKeyEvent(dpy, KEYCODE_LCONTROL, KEY_DOWN, CurrentTime);
  XTestFakeKeyEvent(dpy, KEYCODE_R, KEY_DOWN, CurrentTime);
  XTestFakeKeyEvent(dpy, KEYCODE_R, KEY_UP, CurrentTime);
  XTestFakeKeyEvent(dpy, KEYCODE_LCONTROL, KEY_UP, CurrentTime);
  XCloseDisplay(dpy);
  return 0;
}
```

save file as injectkey.c

to compile, install package libxtst-dev:
```
sudo apt-get install libxtst-dev
```

and then run ```
gcc -o injectkey -lXtst injectkey.c
```

for your convenience, i also attach the binary, built on i386 arch. (it's an executable, not a shell script, but the forum wouldn't accept it without an "allowed" extension)

have fun, enjoy. you can use it in any script to trigger a control-r keycombo.

credits: [http://www.thinkwiki.org/wiki/How_to_inject_fake_keystrokes](http://www.thinkwiki.org/wiki/How_to_inject_fake_keystrokes)

---

### Post by cartisdm on 2008-07-15
Hey man thanks for the script.  I tried messing around with it but was unable to get it to work.  I decided to take a [different route]("http://ubuntuforums.org/showthread.php?t=860350") with what I'm trying to accomplish.  Right now it looks like Audacity has a timer recording option but I'm running into problems with audio playback with Audacity

---

### Post by nanotube on 2008-07-15
> **cartisdm said:**
> Hey man thanks for the script.  I tried messing around with it but was unable to get it to work.  I decided to take a [different route]("http://ubuntuforums.org/showthread.php?t=860350") with what I'm trying to accomplish.  Right now it looks like Audacity has a timer recording option but I'm running into problems with audio playback with Audacity

so all you want to do is record audio (from your microphone, e.g.) at a specified time? then you can just use "arecord" program. start it from a cron job with the appropriate arguments, and tada.

```
man arecord
```
for more details.

---

