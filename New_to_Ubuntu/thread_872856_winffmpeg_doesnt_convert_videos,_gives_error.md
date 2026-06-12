---
title: "winff/mpeg doesnt convert videos, gives error"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by thebestofall007 on 2008-07-28
hello, i am having a problem with winff/ffmpeg not encoding files from flv to avi (but it does convert to ms compatible avi's). when i click convert, i get a terminal output that says that ffmpeg cant find the file/directory, and get a 0 byte file on the desktop (or wherever i save the converted files).


i have included a screenshot if this helps.

---

### Post by FakeOutdoorsman on 2008-07-28
This is a problem with the two-pass XVID preset in WinFF.  The first pass is telling FFmpeg that the output file is /dev/null, which is fine and what I usually do, but FFmpeg gets confused because it doesn't know what format /dev/null is supposed to be.  You can add "-f avi" to "Additional Command Line Parameters (Advanced)" in WinFF and it should encode fine.

---

### Post by thebestofall007 on 2008-07-28
gotcha. i disabled this and it worked fine. thanks for the advice.

---

