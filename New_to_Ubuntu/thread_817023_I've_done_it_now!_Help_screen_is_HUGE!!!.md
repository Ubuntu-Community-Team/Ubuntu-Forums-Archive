---
title: "I've done it now! Help screen is HUGE!!!"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Indy452 on 2008-06-03
I'm trying to get used to Xubuntu 8.04 and while tinkering around in the setings manager I was checking out the screen resolution and when you click on the various sizes it will go to that size and a dialog box will pop up asking if you want to keep this setting. Well I clicked one that was GIANT and I must have hit the keep button and now its set at this giant size!!

The text is so big I cant read it or navigate through it in any way, so If someone knows how to revert it back to default I could use the help.

Thanks a million.

---

### Post by ChameleonDave on 2008-06-03
> **Indy452 said:**
> I'm trying to get used to Xubuntu 8.04 and while tinkering around in the setings manager I was checking out the screen resolution and when you click on the various sizes it will go to that size and a dialog box will pop up asking if you want to keep this setting. Well I clicked one that was GIANT and I must have hit the keep button and now its set at this giant size!!

The text is so big I cant read it or navigate through it in any way, so If someone knows how to revert it back to default I could use the help.

Thanks a million.

You picked a large size and the text is now large?  Text normally appears to be large when you have picked a small, low-resolution desktop.  Hmm.

If all you have changed is your Xfce settings (Xubuntu is based on Xfce), then you could just log into a different desktop environment.

Try hitting Ctrl + Alt + F1 to switch to a terminal.  Then, enter this:

```
sudo apt-get install fluxbox
```

Once Fluxbox is installed, you should be able to choose it (instead of Xfce) from the menu on the log-in screen.  This will give you a working desktop, and from there you can fiddle with your Xfce settings until they work again.

---

### Post by Indy452 on 2008-06-03
Thanks, I'll try that out later today as I'm obviouslly away from the machine right now.

I'll post the results when I get this accomplished, if I get it accomplished. My Bad:(

If all else fails I'll have to re-install and lose all that I've done in the past couple of days? I hope not but I'm sure I can do it again.

Thanks again.

---

### Post by ChameleonDave on 2008-06-03
> **Indy452 said:**
> Thanks, I'll try that out later today as I'm obviouslly away from the machine right now.
Well, actually you could be using your machine from a live CD.

> **Indy452 said:**
> If all else fails I'll have to re-install and lose all that I've done in the past couple of days?

That definitely should not be necessary.  This is a simple reconfiguration.  I could probably fix it in a minute if I had physical access to your machine.

---

### Post by ChameleonDave on 2008-06-03
OK, I've played with Xfce until I found the exact file.  

Go to the terminal and enter this:

```

mv -T ~/.config/xfce4/mcs_settings/display.xml ~/.config/xfce4/mcs_settings/display.xml.backup

```

or this (on two lines):

```

cd ~/.config/xfce4/mcs_settings
mv -T display.xml display.xml.backup

```

This will reset the display to its default settings (probably best to be logged out of Xfce at the time).

---

### Post by Indy452 on 2008-06-03
> **ChameleonDave said:**
> OK, I've played with Xfce until I found the exact file.  

Go to the terminal and enter this:

```

mv -T ~/.config/xfce4/mcs_settings/display.xml ~/.config/xfce4/mcs_settings/display.xml.backup
```

This will reset the display to its default settings.

Whoa, that would be cool if that works. Like I said, I'm away from my machine now but I will definately try this when I get home.

I'll thank you if if works too!!

Neal

---

### Post by Indy452 on 2008-06-03
Well I can't get to a terminal because everything is too large to even navigate.  I'm not sure what else to tell ya.

I'll wipe it out and start over cause I'm not going to fiddle faddle around with something like this. Sorry.

Neal

---

### Post by uterrorista on 2008-06-03
> **Indy452 said:**
> Well I can't get to a terminal because everything is too large to even navigate.  I'm not sure what else to tell ya.

I'll wipe it out and start over cause I'm not going to fiddle faddle around with something like this. Sorry.

Neal
Have you tried [Ctrl] + [Alt] + [F1] ??

---

### Post by ChameleonDave on 2008-06-03
> **Indy452 said:**
> Well I can't get to a terminal because everything is too large to even navigate.  I'm not sure what else to tell ya.

I'll wipe it out and start over cause I'm not going to fiddle faddle around with something like this. Sorry.

Neal

Arghh!! Noo, noooooo!  Noooooooooooo!

That would mean that all the time I've spent solving this for you is wasted!

By "terminal", I didn't mean one of those terminal emulator programs such as gnome-terminal, xterm, konsole, etc.  I meant the real terminal (also known as "tty") that always underlies a Linux system.  Just hit *Ctrl* + *Alt* + a function key to switch between terminals.  F1 - F6 are assigned to terminals.  F7 is your graphical desktop.

It's really easy.  You go to the terminal and enter your user name and password.  Then type the commands I gave.  It will fix your problem instantly.

---

