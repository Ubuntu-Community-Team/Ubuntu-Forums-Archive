---
title: "Threaded timer"
date: 2009-07-02
forum: Programming Talk
---

### Post by Nevon on 2009-07-02
Can anyone tell what I'm doing wrong?

```
import threading

def timedActivation():
    print "Activating in 5 seconds..."
    timer = threading.Timer(5.0, activation)
    timer.start()
    print "from now!"

def activation():
    print "5 seconds have passed"
```

As I run the function timedActivation, everything seems to work. Both statements are being printed. However, the function activation is never run.

---

### Post by smartbei on 2009-07-02
Works for me. Maybe try again and get back to us?

---

### Post by Nevon on 2009-07-02
> **smartbei said:**
> Works for me. Maybe try again and get back to us?

Hmm. This is strange. It works, kind of. But it doesn't run the function until I run something else. I've attached the program so you'll see what I mean. The functions I posted above are at line 120. They're supposed to be run when "Activate in..." in the right-click menu is selected.

---

### Post by smartbei on 2009-07-02
Really? this sounds like the output is being buffered. The function is run at the correct time, it's just that the output to the screen is not necessarily printed immediately. If you really want it immediately, use:
```

import sys
print "a"
sys.stdout.flush()

```
Or, instead of printing to the screen, make the computer beep... :-)
First install beep - 'sudo aptitude install beep'
```

import os
os.system('beep')

```
Hope that works for you!

---

### Post by Nevon on 2009-07-02
> **smartbei said:**
> Really? this sounds like the output is being buffered. The function is run at the correct time, it's just that the output to the screen is not necessarily printed immediately.

Well, the icon is supposed to change as well, to give a visual indication for the user that the program is keeping the computer from going into sleep mode (or the other way around). The function for that should be run once right away (as long as the screensaver is not already being disabled), then it should be run again after the 5 seconds (the delay will of course be longer in the final version).

---

### Post by smartbei on 2009-07-02
Yes, I understand. My point was that the function is actually running on time, it is just that your stdout output is being buffered. Therefore, in the real application this won't be a problem, since you won't be printing anyway. I mentioned beep just for debug purposes.

---

### Post by Nevon on 2009-07-02
> **smartbei said:**
> Yes, I understand. My point was that the function is actually running on time, it is just that your stdout output is being buffered. Therefore, in the real application this won't be a problem, since you won't be printing anyway. I mentioned beep just for debug purposes.

I'm trying it out in the real application, and it's not working. If it was, the icon would change.

Here's how it should work. 

1. As the application starts, it's not blocking the screensaver (sleepPrevented == False). 

2. The user clicks on "Activate for...", which currently means activate for five seconds and then turn off. The function timedActivation() is run. That function in turn runs the function sleepPreventionPressed(), which toggles the icon from empty to full (it's a coffee cup, keeping the computer awake), it also runs the function toggleSleepPrevention() which does it's magic to keep the computer awake, and sets sleepPrevented to True.

3. Five seconds pass and sleepPreventionPressed() is run again, this time it toggles the icon from full to empty. As it runs toggleSleepPrevention() again, the screensaver is no longer blocked and sleepPrevented is once again set to false.

Currently it fills up the cup like it's supposed to, but it never empties it again.

---

### Post by smartbei on 2009-07-02
Hmmm... Could you post the whole source code? I would love to take a look at it. I am actually interested in how you prevent the screensaver as well.

Anyway, without more of the source I have no idea right now what the problem could be, since the small source you posted does work.

---

### Post by Nevon on 2009-07-02
> **smartbei said:**
> Hmmm... Could you post the whole source code? I would love to take a look at it. I am actually interested in how you prevent the screensaver as well.

Anyway, without more of the source I have no idea right now what the problem could be, since the small source you posted does work.

I posted the whole source code in one of my previous posts. Here it is again, I'm sure there are some minor updates in this one. 

By the way, this is not really my project. I'm just helping out with [this project.](https://launchpad.net/caffeine)

---

### Post by smartbei on 2009-07-02
Interesting - after reading around, I found that if you use threads with PyGTK, you are supposed to add:
```

gtk.gdk.threads_init()

```
Right before the call to gtk.main()

From my testing this fixes the problem.

For more information: [http://www.pardon-sleeuwaegen.be/antoon/python/page0.html](http://www.pardon-sleeuwaegen.be/antoon/python/page0.html)

Nice project anyway - good idea!

---

### Post by Nevon on 2009-07-03
> **smartbei said:**
> From my testing this fixes the problem.

Hey, yeah! That works great! Thank you very much for your help.

---

