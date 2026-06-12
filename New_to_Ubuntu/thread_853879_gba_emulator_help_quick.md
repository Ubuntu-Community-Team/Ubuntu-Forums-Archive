---
title: "gba emulator help quick"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by coolman121 on 2008-07-09
ok im trying to get a gba emulator to work any thoughts

---

### Post by RiceMonster on 2008-07-09
You mean visualboy advance? What exactly is the problem you're having?

---

### Post by original_jamingrit on 2008-07-09
OP: There's several gba emulators.  I only know how mednafen works.  What's the name of yours?

---

### Post by coolman121 on 2008-07-09
i cant load visual boy advance even through wine and cant get any others to work either

---

### Post by original_jamingrit on 2008-07-09
try mednafen.  you should be able to download it with apt-get or synaptic package manager.

Read about it here: [http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

---

### Post by RiceMonster on 2008-07-09
Did you try running it from a terminal? I think there's a frontend available in the repos, but the default package has no GUI (as far as I know).

Did you try doing this from a terminal?

```
VisualBoyAdvance /path/to/rom
```

if that returns "command not found", try changing "VisualBoyAdvance" to "vba" or "visualboyadvance"

---

### Post by Korpocalypse on 2008-07-10
are there any other ways?  I did that terminal(konsole) 'VisualBoyAdvance /path/to/rom' thing but it returned this:
VisualBoyAdvance version 1.8.0 [SDL]
Searching for file VisualBoyAdvance.cfg
Searching current directory: /home/chris
Reading configuration file.
Empty value for key captureDir
Empty value for key batteryDir
Unknown file type /home/chris/Visualboy

any ideas?  already tried rightclicking the rom file and selecting vba from the app menu, but after hitting ok, nothing happens.

---

### Post by coolman121 on 2008-07-13
i have been using vba and no$gba mednafen sucks asss for two reasons it only supports 45 roms and does not support DS

---

### Post by Detox06 on 2008-07-29
Any emulators that allow gameshark? VBA for windows will, but when I open the 'cheats' menu, the game freezes. None of the others I've used even have an option.

---

