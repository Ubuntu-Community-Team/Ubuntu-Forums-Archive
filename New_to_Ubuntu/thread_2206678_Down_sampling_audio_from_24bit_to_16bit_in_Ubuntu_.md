---
title: "Down sampling audio from 24bit to 16bit in Ubuntu 12.4??"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by paulgre2000 on 2014-02-20
Could anyone please tell me how to do this in Ubuntu 12.4?
I currently have a bunch of 24bit flac files that I want to down sample and burn to cd with K3b 
is there an easy way???

Thanks

---

### Post by Don_Stahl on 2014-02-20
Do you have Audacity installed?

---

### Post by paulgre2000 on 2014-02-20
Yes

---

### Post by Don_Stahl on 2014-02-20
OK, I'm not on my Ubuntu machine right now. However, if you open your flac file in Audacity and then use the "Export File" menu you should be able to choose "flac" as the export type. Then in the Options sub-menu, choose 16-bit.

I've not had a need to do this before, but there are probably some batch conversion utilities -- someone else may know a good one?

Late edit: running SoX from the command line would probably do batch resampling. I haven't tried it so I won't venture to give specific guidance. The manpage is at [http://manpages.ubuntu.com/manpages/saucy/man1/sox.1.html](http://manpages.ubuntu.com/manpages/saucy/man1/sox.1.html)

---

### Post by paulgre2000 on 2014-02-20
thanks Don I'll give it a go

---

