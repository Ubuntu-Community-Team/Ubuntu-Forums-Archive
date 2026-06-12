---
title: "HOWTO: Stop RhythmBox frrom hanging when you try to load songs"
date: 2004-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by .altan on 2004-10-27
If RhythmBox (after you install whatever decoder you may need to play your audio files) hangs on Loading Songs, check to see that there are no other files other than audio in the source directory. The files that were bugging me were JPG and INI files from Windows and Windows Media Player, but I assume any other kind of file could cause it as well.

This is a bit of a less elegant method I used to solve it, and you should make sure that none of the JPG (or any other file types you will plug in) files you want, or if you do to back them up.

find -name "*.jpg" -type f -print0 | xargs -0 rm

Alternatively, move the MP3 (or JPG/other files for that matter) to another directory where it won't hamper/be hampered:


find -name "*.jpg" -type f -print0 | xargs -0 mv --target-directory=/directorygoeshere/

Thanks to Keybul for helping me out with the last one, and a helpful guy in #ubuntu who had his name cleared from my X-Chat buffer since I logged off.

---

