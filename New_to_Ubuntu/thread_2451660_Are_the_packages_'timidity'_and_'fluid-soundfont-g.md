---
title: "Are the packages 'timidity' and 'fluid-soundfont-gm' important?"
date: 2020-10-08
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-10-08
Hello all,

I was reading [this thread]("https://ubuntuforums.org/showthread.php?t=2451405") and ran 'dpkg --list | grep ^rc' out of curiosity to see what packages I hadn't properly purged. A load of kernel stuff came up (which I haven't actually removed myself) and also 'timidity' and 'fluid-soundfont-gm'

Are the latter two important? I re-installed them to try and get the sound working in a game I was having some bother with that is capable of using them, mostly out of curiosity, but nothing changed so I purged them again...

---

### Post by deadflowr on 2020-10-08
Are they important in the overall scheme of things? No.
Are they important for a select few programs to run properly? Yes.

---

### Post by jcdenton1995 on 2020-10-09
Fair enough, I guess if they are needed for anything I'll find out in due course!

---

### Post by CatKiller on 2020-10-09
They're for playing MIDI sounds. Timidity allows you to use MIDI without a hardware synthesiser, and the other is a (one of many possibilities) sound font to say *which* sounds should be played for each MIDI instrument.

---

