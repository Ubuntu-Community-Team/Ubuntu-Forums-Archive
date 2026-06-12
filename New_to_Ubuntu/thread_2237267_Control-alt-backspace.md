---
title: "Control-alt-backspace"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by UncleMonty on 2014-07-31
How can I enable control-alt-backspace in ubuntu 14.04, in order to force a logout?

---

### Post by cwmoser on 2014-07-31
Using the Tweak Tool located under Applications -> System Tools -> Preferences, go down to Typing.
Change Key sequence to kill the X server to Ctrl + Alt + Backspace

---

### Post by 3rdalbum on 2014-08-01
Control-Alt-Backspace has been depreciated from Xorg for a number of years as it only works when X is listening to keystrokes. Instead you should use Alt-Printscreen-K, which is actually captured by the kernel and therefore is acted on a lot more reliably.

Here's a post that describes how to enable Alt-Printscreen-K: [http://ubuntuforums.org/showthread.php?t=2220356&p=13007809#post13007809](http://ubuntuforums.org/showthread.php?t=2220356&p=13007809#post13007809)

---

### Post by mcduck on 2014-08-01
Yep, I agree with the above, although it should be clarified that the shortcut is *SysRq+K*

(it just happens that many keyboards place SysRq under the Printscreen key, but not all of them do that and trying to Alt-Printscreen would of course fail if your keybaord had SysRq as it's own key or placed in different location. So it's better to just look at where the SysRq is on your keyboard than to rely on it being under Printscreen key... ;))

---

