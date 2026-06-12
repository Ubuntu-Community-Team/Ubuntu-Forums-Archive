---
title: "[SOLVED] ctrl+alt+f1 not working in hardy!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by philphil on 2008-05-29
here we go again:

I can't use Ctrl+Alt+F[1..6].  When I press them, nothing happens.  

If I'm already in a terminal, however, I CAN switch between other tty windows and I can get to the GUI by pressing Ctrl+Alt+F7.  Once in the GUI though I'm stuck and can't get back to a tty.

Any ideas?

---

### Post by viljun on 2008-05-29
Your window manager (Gnome / Kde / ...) is not configured right. It may also be problem with general X settings.

Check that you keyboard is configured to use its actual layout goint to settings > keyboard on Gnome. If it's right, there's button you should press to change settings for special keys.

Also you might try to generate a new user to see if problems are only with this user.

---

### Post by mali2297 on 2008-05-29
Try moving **.gconf** in your home directory to a backup folder.

---

### Post by Joeb454 on 2008-05-29
Odd, it works for me (it asks me to log in again on the tty :))

Funnily enough, I had issues with it on Gutsy on the very same machine :)

---

### Post by philphil on 2008-05-29
thanks to all for the replies...

tried moving .gconf and it rest my whole desktop to the default as expected, tried ctrl+alt+f[1..6] and nothing happened

tried creating a new user which probably amounts to the same as above but still nothing....

My Ctrl, Alt and F1 keys definitely work, I've tested them.

Hm, any other ideas?

Edit: oh, and I tried looking in Keyboard settings but there was nothing about special keys...

---

### Post by mali2297 on 2008-05-29
I'm trying to find a common denominator here:
[http://ubuntuforums.org/showthread.php?p=4671032](http://ubuntuforums.org/showthread.php?p=4671032)
[http://ubuntuforums.org/showthread.php?t=472647?post=#11](http://ubuntuforums.org/showthread.php?t=472647?post=#11)
[http://ubuntuforums.org/showthread.php?t=804788](http://ubuntuforums.org/showthread.php?t=804788)

You don't have a UK keyboard, do you?

---

### Post by philphil on 2008-05-30
don't have time to check those links now but yes I do have a UK keyboard...

---

### Post by philphil on 2008-05-30
ok, now I kinda have it working...if I comment out this line from my xorg.conf file:

Option		"XkbLayout"	"uk"

then it works fine and I can Ctrl+Alt+F* to a terminal window BUT if I do this then I lose my uk keyboard layout (obviously) and the keys no longer match up with what they're supposed to match up with...(e.g. pressing the # key doesn't give me a #) so I'm in a bit of a bind....but much closer than I was, any further ideas?

---

### Post by philphil on 2008-05-30
ok after much huffing and puffing I've got it working

step 1: In Xorg.conf, comment out the line that reads:	Option		"XkbLayout"	"uk
step 2: Go to preferences-->keyboard- ->Layouts
step 3: select default united kingdom layout
step 4: (this is what clinched it for me) untick the box that says "Separate layout for each window" 

logout then log back in and everything should be working

---

### Post by Joeb454 on 2008-05-30
Glad to hear you finally got it solved :)

You can mark the thread as solved by choosing Thread Tools at the top of this page and clicking "Mark Thread as Solved"

---

### Post by mali2297 on 2008-05-30
Thanks for providing a solution, it may prove to be useful for your countrymen.

Interestingly, I just found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/231888") on the issue. Perhaps an alternative solution is to change
```

Option "XkbLayout" "uk"

```
to
```

Option "XkbLayout" "gb"

```
in /etc/X11/xorg.conf.

---

### Post by lobner on 2008-08-18
Thank you! - This helped :)

---

