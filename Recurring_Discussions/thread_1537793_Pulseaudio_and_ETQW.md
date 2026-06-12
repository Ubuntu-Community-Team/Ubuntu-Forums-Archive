---
title: "Pulseaudio and ETQW"
date: 2010-07-24
forum: Recurring Discussions
---

### Post by MichiganMan on 2010-07-24
Enemy Territory:Quake Wars is one of the FEW retail games that supported Linux almost from the word go.  And its one of the few games that maintains a substantial base of linux users that are able to play, cross platform with users on other OS's...

So wouldn't it be great if Pulseaudio, the sound architecture that Ubuntu just *has* to have, didn't *break* this retail game that has been so good to us?  (Unless you consider a 30 second lag on sound acceptable for when playing a linux game) I mean its not like sound with Pulseaudio didn't work with ETQW with the release of 10.4.  And its not like the Pulseaudio/ETQW bug hasn't been reported and active for months now...

To answer your question, No, I'm not a programmer.  No, I can't code an open source solution.  I can only imagine:

What would it be like if Pulseaudio didn't break ETQW?

[SOLVED]11 May, 2011 Installed Debian Stable.  All Pulseaudio issue resolved.

---

### Post by Elfy on 2010-07-24
Moved to recurring.

---

### Post by YuiDaoren on 2010-07-24
> **MichiganMan said:**
> Enemy Territory:Quake Wars is one of the FEW retail games that supported Linux almost from the word go.  And its one of the few games that maintains a substantial base of linux users that are able to play, cross platform with users on other OS's...

So wouldn't it be great if Pulseaudio, the sound architecture that Ubuntu just *has* to have, didn't *break* this retail game that has been so good to us?  (Unless you consider a 30 second lag on sound acceptable for when playing a linux game) I mean its not like sound with Pulseaudio didn't work with ETQW with the release of 10.4.  And its not like the Pulseaudio/ETQW bug hasn't been reported and active for months now...

To answer your question, No, I'm not a programmer.  No, I can't code an open source solution.  I can only imagine:

What would it be like if Pulseaudio didn't break ETQW?

```
pasuspender /path/to/etqw
```

That will suspend Pulseaudio and let you play ETQW with ALSA. When you quit ETQW, Pulseaudio then resumes.

---

### Post by MichiganMan on 2010-07-25
> **YuiDaoren said:**
> ```
pasuspender /path/to/etqw
```

That will suspend Pulseaudio and let you play ETQW with ALSA. When you quit ETQW, Pulseaudio then resumes.

Thanks for the response.  I did try pasuender buy the technique was unsuccessful, although I don't remember why at this point since it was over a month ago and in the midst of several other attempt to work around the problem.  I think it left me with no mic, or no sound...  In any event, I ended up ripping out Pulseaudio and returning to alsa.  All is well.  I'll try Pulseaudio again if the bug is ever addressed.

---

