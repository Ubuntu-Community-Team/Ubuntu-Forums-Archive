---
title: "Nautilus Copy Files"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by chris062689 on 2008-07-18
I was copying files from my ipod, that serves as a backup.
Of course the power went out when it was about halfway done :lolflag:
Is there anyway I can tell it to only copy the pieces it doesn't have so I don't waste time recopying things I already have?  (I told it to copy all of the files into one folder.)  I think some files are fragmented though (meaning; only half of them copied)

Should I just delete the entire folder and try again?

---

### Post by iaculallad on 2008-07-18
> **chris062689 said:**
> I was copying files from my ipod, that serves as a backup.
Of course the power went out when it was about halfway done :lolflag:
Is there anyway I can tell it to only copy the pieces it doesn't have so I don't waste time recopying things I already have?  (I told it to copy all of the files into one folder.)  I think some files are fragmented though (meaning; only half of them copied)

Should I just delete the entire folder and try again?

It would be better to re-copy the entire folder. And, use the **cp** terminal command instead of Nautilus to copy the files, cp is much faster.

---

### Post by coffeecat on 2008-07-18
Simply highlight all files in the folder you are copying from. Drag and drop them over to the destination folder. You are then given four (iirc) choices - skip, replace, etc. Choose 'Skip all' and only those files you haven't copied yet will be copied.

Be careful with 'cp'. If you don't use the appropriate flags, the time date will be reset to the copy time. And, in my experience of copying several hundred files, I haven't noticed much difference in speed, if any.

---

