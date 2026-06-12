---
title: "Intel 946GZ Problems..."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by lillypilly on 2008-11-06
Reference the thread and bug below.
[http://ubuntuforums.org/showthread.php?t=959974&highlight=bug+289883](http://ubuntuforums.org/showthread.php?t=959974&highlight=bug+289883)

I have an almost identical problem, the main difference being that I have a Accer G991 Screen

Does any one know of any way to get around this problem. Everything works fine under 8.04 and earlier but I can only see a 640 screen in 8.10. I am getting the same (EE) error on startup

---

### Post by Mark_in_Hollywood on 2008-11-08
I don't have your equipment, nor have I seen your problem, BUT, reboot:

when the All caps and other leds flash on, press 

esc

that will get you into recovery mode.

Once there, use the arrow keys to move down to the XORG selection. Run that.
As I don't know what you will see, I can't help you with that. Select ordinary or minimum values.

If you get to a prompt that looks like:

yourusername@your-computer-name:~>

type 

shutdown -r now

the system will reboot itself.

if this solves it, come back and mark this thread solved, please.

---

### Post by lillypilly on 2008-11-10
I have found that if I delete the "xorg.conf" file and run the computer without this file the screen display seems to run correctly.

I also found that by deleting the "xorg.conf" file on my notebook as well that that solved a similar display problem on it as well

The suggestion in the 1st reply did not appear to help my initial problem at all.

---

