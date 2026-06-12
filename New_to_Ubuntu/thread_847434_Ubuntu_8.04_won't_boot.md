---
title: "Ubuntu 8.04 won't boot"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by oncable on 2008-07-02
I have downloaded and burned to cd v8.04. I am unable to get it to go through the install process as dual-boot with XP. When I try to boot from cd it does the following:
- select "TRY" with no changes
- select "normal"
- loading linux kernel
- orange rectangle bounces back and forth for a long time. I finally get message "Ubuntu is running in low graphics mode. Your screen and graphics card could not be detected correctly. To use higher resolutions, you have to configure the display yourself"
- I clicked on "continue"
- "starting deferred execution scheduler - OK"
- "starting periodic command scheduler - OK"
- "checking battery state - OK"
- "running local boot scripts /etc/rc.local - OK"
then I get flashing cursor on black screen and nothing happens.
I can type and the letters appear. If I hit return it moves down one line. It seems to be waiting for me to enter some text, but what should I enter? 

hardware:
mboard - Asus P4P800SE 1gb ram
P4 - 3.2
Asus AX800
Samsung 193P monitor
Auzentech X-Meridian 7.1
Pioneer DVR- 110D DVD burner

When I try to install as dual-boot it also semi-crashes at similar point. Control-alt-del works to reboot system after message asking me to remove the cd.

Any ideas?

---

### Post by hyper_ch on 2008-07-02
try to install it from the alternate install cd... that one generally has less problems for installation

---

### Post by prshah on 2008-07-02
> **oncable said:**
> 

- select "TRY" with no changes

message "Ubuntu is running in low graphics mode. Your screen and graphics card could not be detected correctly. To use higher resolutions, you have to configure the display yourself"
- I clicked on "continue"

then I get flashing cursor on black screen and nothing happens.



Here's a number of things you can try: 

1) The simplest, and one that you should try first; press Ctrl+Alt+F7, if the GUI is running it should show up instantly. If nothing happens, the GUI is not running.

2) When the CD boots up, press F4 to go to the alternate/advanced menu. From there, choose "Safe Graphics Mode" and continue as you have done before.

3) Choose "configure" instead of continue, then use your best guess 

4) If none of the above work, when you reach the prompt where it seems to be waiting for you, press Ctrl+Z, then give the command ```
bg
``` You should get a prompt, probably something like "ubuntu@ubuntu ~$". Here, give the command ```
xinit
``` That should load a GUI (Use Ctrl_At_F7 if nothing seems to happen), and in the white command box, give the command ```
sudo displayconfig-gtk
``` then setup suitable to your graphics card/monitor.

Post back if you have any difficulties.

---

### Post by oncable on 2008-07-02
Thanks for your response. When I try to install as "alternate" it gets to a different black screen with a different prompt. The screen is 3/4 full of text (too much to type here) ending with "See Man Sudo_root for details."
the prompt is "ubuntu@ubuntu:~$
and again, it seems to be waiting for me to enter some text, but what should I enter? Only ctrl-alt-del gets me out of there.
I have scanned cd for errors and done memory scan. no probs in either.

---

### Post by hyper_ch on 2008-07-02
if even the alternate cd has issues getting installed then I'd advice against using ubuntu... maybe you have better luck with debian/mepis/fedora core/....

---

### Post by oncable on 2008-07-03
The problem is solved, thanks to your help. It seems Ubuntu doesn't like my graphics card (Asus AX-800, a standard ATI clone) and couldn't load the gui for some reason and would semi-crash in text-only mode. Thanks again for your help. It was 3 days of trial and error. Now on to configuration.

---

