---
title: "making window open in specific spot"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-21
when I open a terminal I'd like it to open in a particular spot.  How do I arrange this?

---

### Post by MemoryDump on 2008-07-21
I don't believe it remembers the last position after you close an application. I've always wondered why this feature was never setup.

---

### Post by adamogardner on 2008-07-21
so does it need a script?

---

### Post by drs305 on 2008-07-21
There is an app called *devilspie* that puts specific apps in specific locations on specific workspaces. But be warned: you will probably tear most of your hair out trying to set it up!

It's in the universe repository if you want to spend the time and effort to get it working. (Once you have it set up, you don't have to mess with it again.)

---

### Post by tjwoosta on 2008-07-21
i may be wrong, but i think you can achieve this with compiz fusion also


there is a a setting in CCSM called Place Windows way down by the bottom (just click the fixed windows tab)

---

### Post by brian_p on 2008-07-21
> **adamogardner said:**
> when I open a terminal I'd like it to open in a particular spot.  How do I arrange this?

man gnome-terminal has a geometry option. The command

```
gnome-terminal --geometry=80x30+0+0
```

should open an 80x30 sized terminal in the top left hand corner of the screen.

---

### Post by drs305 on 2008-07-21
> **tjwoosta said:**
> i may be wrong, but i think you can achieve this with compiz fusion also


there is a a setting in CCSM called Place Windows way down by the bottom (just click the fixed windows tab)

Yes! That asks for the same information devilspie does so it looks like it does the same thing as far as positioning goes. It doesn't seem to have quite the options but would be much simpler to set up.

---

### Post by adamogardner on 2008-07-21
And the ccsm is what?  I know the advanced desk top settings under system>preferences.

---

### Post by tjwoosta on 2008-07-21
CCSM = compiz config settings manager   (system-Preferences-Advanced Desktop Effects Settings)

---

