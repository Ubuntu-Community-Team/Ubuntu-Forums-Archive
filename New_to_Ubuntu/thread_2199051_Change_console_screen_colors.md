---
title: "Change console screen colors"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by bobmct on 2014-01-11
:confused:  I'm running Ubuntu 13.10 Server so there is no GUI console.  Its ALL CLI.  But the grey on black is hard to see (for me anyway).  Could someone please advise how/where I can modify the definition so when the console is displayed it will appear with the newly defined color scheme?

Thanks

---

### Post by egeezer on 2014-01-11
Is there an Edit tab on the upper border?  If so, click it and choose Preferences.  You'll find a Color tab in there.

---

### Post by bobmct on 2014-01-12
Thanks egeezer but I see no tab anywhere.  I'm running this install as a guest OS under Virtualbox.  And seeing how its a server edition, there is nothing but a square border and a black screen with the light-gray prompt.

I was thinking maybe something could be placed in the users .profile but don't know what.

Any other ideas?

---

### Post by egeezer on 2014-01-12
Sorry, I'm about tapped out.  I did do a server install once, but just to use it as the core for a cobbled-up sort of Xfce desktop.  I think it was probably the Xterm terminal I was using that gave me the tabbed title bar.  Might try it by apt-get?

---

### Post by steeldriver on 2014-01-12
If the terminal (screen) supports it, you should be able to use setterm e.g. to set the text color to green-on-black

```
setterm -foreground green -background black -store
```

IIRC there is limited support for changing the actual screen background color via inverting the screen

```
setterm -foreground green -background black -inversescreen -store
```

You may also find that changing the console font helps significantly with readability as well - you should be able to do that by installing the console-setup package and running

```
sudo dpkg-reconfigure console-setup
```

I find that terminus 14pt works pretty well

---

### Post by bobmct on 2014-01-13
Thank you steeldriver.  I tried both the setterm and the console-setup.  The former worked but only until a program and/or utility was run that output to the terminal then the section of display reverted back to the white on black.

I'll keep looking but thanks for the suggestions.

---

### Post by steeldriver on 2014-01-13
Hmm... that's really strange

There's a known bug with the 'dpkg-reconfigure console-setup' font changes not persisting after reboot --> [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/632382](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/632382)

but the 'setterm' part for the text color should work. Could you give some examples of commands that appear to reset it?

---

### Post by bobmct on 2014-01-13
Steeldriver -

Additional research showed a -store switch to be used with the setterm command.   I used it and it seems to be holding across all logins and programs/utilities.

So let's consider this SOLVED!  Thank you very much (a happy 'buntu user). :smile:

---

