---
title: "No Applications, No access to terminal"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by llamaboy on 2013-03-20
HELP!
I am running 12.04 and have recently lost all my applications when I click the ubuntu symbol in the upper left hand side of the screen. I am not all that savvy, so I'm not sure how else to access them. I am able to look at recent documents and such, just no applications, and no terminal. I'm at a loss. I was able to access them until a few weeks ago.

---

### Post by usegnu on 2013-03-20
Do the keys Alt+F2 still work?
You can try to go to settings, then "Main Menu" and make sure the sections you want are checked/enabled.

---

### Post by RobZ51 on 2013-03-21
If you need terminal you could try ctrl+alt+f1 Press ctrl+alt+f7 to get back to the default.

---

### Post by llamaboy on 2013-03-22
Yes, Alt+F2 still works, but Dash still pops up, but other than documents, there is nothing in there. One thing I forgot about as well, not sure if it's related, but Ubuntu Software Center freezes every single time I open it.

---

### Post by Krytarik on 2013-03-22
> **llamaboy said:**
> ...Dash still pops up, but other than documents, there is nothing in there. One thing I forgot about as well, not sure if it's related, but Ubuntu Software Center freezes every single time I open it.
From my recent post here:

[http://ubuntuforums.org/showthread.php?t=2120921&p=12534505#post12534505](http://ubuntuforums.org/showthread.php?t=2120921&p=12534505#post12534505)
> **Krytarik said:**
> Try clearing Software Center's cache, it should fix both:
```
rm -rf ~/.cache/software-center
```If you wonder why the Unity Dash is affected by that too, please see [here]("http://ubuntuforums.org/showthread.php?p=11636422#post11636422").

Regards.

---

### Post by llamaboy on 2013-03-22
I found a similar thread, not sure what finally did the trick. I tried the code you offered and it didn't appear to do anything. Then I used:

unity --replace
This seemed to work for me. Anyways, everything now works. THANKS FOR THE HELP!!:popcorn:
[http://ubuntuforums.org/showthread.php?t=1911109&page=2&p=11636422#post11636422](http://ubuntuforums.org/showthread.php?t=1911109&page=2&p=11636422#post11636422)

---

### Post by Krytarik on 2013-03-22
> **llamaboy said:**
> I tried the code you offered and it didn't appear to do anything. Then I used:

unity --replace

This seemed to work for me.
Yeah, restarting of Unity is indeed necessary (or at least of the daemon underlying the Applications Lens), or alternatively a relogin, to make the change affect the Dash.

Glad that it worked out.

---

