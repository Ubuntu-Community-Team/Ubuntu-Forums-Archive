---
title: "Function keys won't work in Eclipse"
date: 2011-03-13
forum: Programming Talk
---

### Post by Mike Brennan on 2011-03-13
I'm using Eclipse 3.6.2 on Ubuntu Lucid 10.04 and the function keys are not working at all in Eclipse, but work fine in other programs.

This is driving me nuts. I've done google searches but find nothing. Other shortcuts work fine, but Eclipse does not recognize function key presses. Even if I go into the keboard shortcut preferences for Eclipse and try to map anything to any key combination involving a function key, it does not work. Eclipse does not detect the function key being pressed.

Has anyone else experienced this? I use Eclipse at work (on Windows) and am very accustomed to using the keyboard shortcuts. This is very frustrating that I cannot use function keys.

Any help would be very much appreciated.

---

### Post by GregBrannon on 2011-03-14
Any luck?  Did they ever work in Ubuntu for you, or has this been a problem since installing?  You might try creating a new workspace to see if that helps, but I'm doubtful that it'll help, especially if it's been a problem from the start.

Others, very few, have reported keyboard problems with Eclipse, but it's usually related to a specific environment/configuration change or plugin that they could point to because their problems began after making a change.  Your apparent "out of the box" problem is not being reported by others that I could find.

How did you install Eclipse?  You might try reinstalling.  Or if you installed from repos, try reinstalling it manually or vice-versa.

Good luck.

---

### Post by Mike Brennan on 2011-03-14
It used to work for me. I can't remember exactly when it started, but I do remember it being broken in 3.5. I haven't been using Eclipse much on my home machine lately, so I didn't worry about it. But I'm getting back into it, now. I downloaded the latest from the Eclipse site to see if this problem was fixed, but it is still occurring. 

I tried creating a fresh workspace and trying a clean install of Eclipse, but no such luck. Same problem.

I don't install Eclipse from the repos because it lags too far behind what's on the Eclipse website (and because of inability to add plugins from within Eclipse when it is installed from repos).

I'm at a loss.

---

### Post by GregBrannon on 2011-03-14
Eclipse preferences are so complicated with so many possible settings affecting how others work.  Perhaps you innocently changed a setting that disabled function keys and didn't realize it.

Since you have Eclipse running and configured the way you like it on your work machine, you could try exporting your work machine preferences and importing them to your home machine.  If that doesn't work, I'm out of ideas.

---

### Post by ihliedaily on 2011-08-31
Let me push this topic, cause i am experiencing the same problem. Running on 11.04, unity and all the stuff. Open Resource for example (Ctrl+Shift+R) is not working, but after i called that function from the menu its working for a certain time frame.

Whats that? Has anybody any hint? Drives me more than crazy...

edit: also using eclipse 3.6.2

---

