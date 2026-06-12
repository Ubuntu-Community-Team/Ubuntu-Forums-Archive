---
title: "HOWTO: Self-defined filename-patterns in Sound-Juicer"
date: 2005-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Mauleye on 2005-06-20
Sound-Juicer is a nice simple and well intigrated tool for ripping audio-CD's ... but one thing I always hated with it was the fact that I could not use my own filename-patterns (i.e. <tracknumer> <trackname>). I just found out how to get a work-around here:

Start the configuration-editor* (Menu->Systemtools->Configuration Editor)
browse to apps->soundjuicer
change the string in file_pattern (in my case it should be %tN %tt - see key-documentation in the lower right of the configuration editor) ... snd you are done  :)

---

### Post by bestiarosa on 2007-01-20
Thanks, it works!

---

### Post by blackpuma on 2007-10-20
It works here too... :)
Not always! Only if you don't open the Edit->Preferences window in the sound-juicer process. For some reason the values are overwritten.

There's no ``Year'' parameter support also :(
I think it's critical for naming profiles

---

### Post by wormser on 2007-11-28
> **blackpuma said:**
> It works here too... :)
Not always! Only if you don't open the Edit->Preferences window in the sound-juicer process. For some reason the values are overwritten.

There's no ``Year'' parameter support also :(
I think it's critical for naming profiles

Mine gets over written too.  Sound Juicer is a nice little app but it would be nice if they added more default options for file name.  I want to have my out put like this: Artist - Album - Track # - Tittle.  How do I do that and not have it over written.

Thanks

---

### Post by BigGuyWhoKills on 2010-12-24
> **wormser said:**
> Mine gets over written too.  Sound Juicer is a nice little app but it would be nice if they added more default options for file name.  I want to have my out put like this: Artist - Album - Track # - Tittle.  How do I do that and not have it over written.

Thanks

Wormser, I was listening to Roll The Bones (your forum avatar pic) when I found this post, and I want to use "Artist - Album - Track # - Tittle" (%aa - %at - %tn - %tt) for my naming convention as well.

"Menu->Systemtools->Configuration Editor" does not exist in the default Ubuntu 10.10 menu, but can be launched from a terminal with "gconf-editor".  This seems to only get overwritten when you open the SJ prefs and select a new naming scheme from the drop-down list.

---

