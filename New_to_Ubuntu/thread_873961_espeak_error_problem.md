---
title: "espeak error problem"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by t0p on 2008-07-29
When using **espeak**, the command

```
espeak file.txt
```

should result in the computer reading file.txt out loud.

When I was using Gutsy, espeak worked fine.  But now, trying to use it results in the error message

```
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

Can anyone suggest how to rectify this?

---

### Post by t0p on 2008-07-30
Any point bumping this?

Oh, I seem to have bumped it anyway.

*bump*

---

### Post by prinerocks on 2008-08-17
I had the same problem as you.  I found the solution on the following post:

[http://ubuntuforums.org/showthread.php?t=715271&highlight=espeak&page=2](http://ubuntuforums.org/showthread.php?t=715271&highlight=espeak&page=2)

Try disabling software sound mixing (ESD) by going to System>>Preferences>>Sound, then clicking the Sounds tab.

---

