---
title: "lubuntu-rc.xml - stickykeys, brightness, keymaping, voice-command"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-05-18
Hi Guys

I'm still tweaking Lubuntu on my notebook for one-handed use for my upcoming shoulder op. 

My system is:
Presario-CQ57-Notebook-PC 3.2.0-43-generic-pae #68-Ubuntu SMP Wed May 15 03:55:10 UTC 2013 i686 i686 i386 GNU/Linux

I tweaked: 
~/.config/openbox/lubuntu-rc.xml 
to give me the keyboard shortcuts I like. And I've tweaked it to give me the doubleclick speed I can handle.

Now I would like to tweak a little more, but don't know how to.

On startup I want:

1. these two commands to run for stickykeys:
xkbset exp -bell -sticky -twokey -latchlock -accessx -feedback -stickybeep -led 9999
xkbset bell sticky -twokey latchlock feedback led stickybeep

2. my screen brightness key (f3) to be pushed 5 times (Lubuntu always boots up dim for me)

3. my Super Key to remapped as a "page down" key (I do a lot of on-screen reading and it's awkward to lean across the keyboard). 
If I could rig a single voice command for page down that would be awesome.

If anyone can help with any of these 3 I'd be really grateful.

---

### Post by cortman on 2013-05-18
Edit the autostart file for #1. Either Openbox's autostart, or else follow the instructions for LXDE [here]("http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/").
On #2, [this]("http://askubuntu.com/questions/66751/how-do-i-set-default-display-brightness") may be of help.
[Here]("http://askubuntu.com/questions/137172/how-to-remap-superleft-key-to-control-key") is some info on remapping keys.

Hope the surgery goes well!

---

### Post by vasa1 on 2013-05-18
@cortman, is it okay if I PM you re. [http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/](http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/) ?

---

### Post by Kevin McCready on 2013-05-18
Wow. Thank you so much Cortman.
For 1 and 2 I altered
```
sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
```
by putting in:
xkbset exp -bell -sticky -twokey -latchlock -accessx -feedback -stickybeep -led 9999
xkbset bell sticky -twokey latchlock feedback led stickybeep
xbacklight =100

This worked fine!

But for 3 (Super Key to remapped as a "page down" key), I couldn't understand "man xmodmap"

I found when I do
```
xmodmap -pke
```
one of the lines which might have something to do with "page down" reads
keycode  88 = KP_Down KP_2 KP_Down KP_2

---

### Post by cortman on 2013-05-19
> **vasa1 said:**
> @cortman, is it okay if I PM you re. [http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/](http://cortman.wordpress.com/2012/06/06/add-startup-program-to-almost-any-de/) ?

Certainly, vasa1.

---

