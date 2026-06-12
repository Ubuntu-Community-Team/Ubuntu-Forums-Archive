---
title: "Frozen or something else"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by hansmax on 2012-11-28
I installed 12.10 today, not a dual boot, just Ubuntu. Everything seemed to go all right, got a wireless connection to the internet. It told me to restart, and on restart it went out and got updates. That was the last interaction I was able to have. I have a desktop now, but with no icons on it. The mouse works. When I press ctrl+alt+delete I get a message that I am logged in as so and so, do I want to log out. Log out takes me to a login screen, where I enter my login, which puts me back at the empty screen. It's been a few years since I dealt with Ubuntu (last was 8.??), so I'm back at the beginning of the learning curve. This is an older system. Any thoughts or ideas would be appreciated.

---

### Post by audiomick on 2012-11-28
> I love cats, but I can't eat a whole one. 

Neither can I. ;)

Anyway...

Log out is not shut down. It just stops the user session, so the fact that you are getting back to the log-in screen with that does not mean that anything is broken. Do you not get offered a "shut down" or "switch off" option there? I do on this 10.04 install.

If you do ctrl+shift+t , you should get a terminal. One thing you can do from there is
```
shutdown -P now
```
which should turn the computer of cleanly.

As far as your desktop goes, that sounds like a problem with video drivers. Can you post here what your video card is? That will make it easier for people to help you.

If you can get a terminal open, do
```
sudo lshw -C video
```
to list what your video card is if you don't know off the top of your head.

---

### Post by hansmax on 2012-11-28
I do also get the shut-down option. As for video card, it's an N-Vidia, very old, probably bought around 2000. I don't seem to be able to get a command prompt at all. Come to think of it, the card brand is a Siluro - G-Force 430 or 440. Like I said, it's quite an antique.

---

### Post by hansmax on 2012-11-28
I will try to get a command prompt up tomorrow, but so far have not had much luck with any hotkey compbinations. I'm a little hazy on just how the whole driver thing works in Ubuntu. Since my miraculous memory recall of the card model I've done some googling, but am fairly confused as to what I would be looking to replace or how I would go about it. Thanks for the reply, audiomick.

---

### Post by newb85 on 2012-11-28
I think the Ctrl+Alt+T key combination is dependent on Unity, so if graphics issues are preventing Unity from loading, it would explain why you can't even call up a terminal.

Someone more proficient might be able to tell you how to get your graphics issues fixed from a fullscreen CLI.  I can't.

However, I can suggest you try to log in to a Gnome Classic session.  At the login screen (I'm assuming you can still get that far), beside your name is a little Ubuntu icon.  If you click it, it will give you a few session options.  Look for one with "Classic" or "Fallback" in the name and select it.  Then log in.  With any luck, you'll have a functional DE that looks a lot like Gnome 2 (which you'll remember from 8.10).

From there, you can bring up Software Sources and go to the tab for drivers and make sure you have the Nvidia drivers installed and enabled.


By they way am I understanding right that for a while, you had a working system with 12.10 and a ten-year-old Nvidia card?

---

### Post by audiomick on 2012-11-29
> **newb85 said:**
> I think the Ctrl+Alt+T key combination is dependent on Unity,...

works on 10.04. I think it is Gnome rather than Unity. I don't know, though, how keyboard shortcuts react if the desktop is having trouble.

---

### Post by hansmax on 2012-11-29
I don't get a small Ubuntu icon next to my name on the login screen, so I can't get to any of these sessions. Also no terminal with ctrl+alt+t. I do have a small toolbar, upper right for a few functions. Onscreen keyboard gives me a white bar across the bottom of the screen. It says wireless is enabled.

---

### Post by dannyboy79 on 2012-11-29
can you hit ctrl-alt-F2? then within that box type, gnome-terminal

---

### Post by hansmax on 2012-11-29
This takes me to a command prompt asking for a login and password. I recall my password, but do not recall creating a login name. I will have to play some more with this later. Have appointments right now. I also have downloaded 12.04 which I might install if all else fails and start the process all over again. Thanks for the input, people. I will be posting.

---

