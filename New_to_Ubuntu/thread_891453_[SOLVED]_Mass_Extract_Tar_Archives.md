---
title: "[SOLVED] Mass Extract Tar Archives"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Sarah L on 2008-08-16
I'm having trouble extracting multiple bz2 archives using the tar command.

The output of ls:```

stardict-cedict-gb-2.4.2.tar.bz2
stardict-gaojihanyudacidian-2.4.2.tar.bz2
stardict-guojibiaozhunhanzidacidian-2.4.2.tar.bz2
stardict-langdao-ce-gb-2.4.2.tar.bz2
stardict-langdao-ec-gb-2.4.2.tar.bz2
stardict-oxford-gb-2.4.2.tar.bz2
stardict-oxford-gb-formated-2.4.2.tar.bz2
```

The output of tar -xvjf *.bz2:```

tar: stardict-gaojihanyudacidian-2.4.2.tar.bz2: Not found in archive
tar: stardict-guojibiaozhunhanzidacidian-2.4.2.tar.bz2: Not found in archive
tar: stardict-langdao-ce-gb-2.4.2.tar.bz2: Not found in archive
tar: stardict-langdao-ec-gb-2.4.2.tar.bz2: Not found in archive
tar: stardict-oxford-gb-2.4.2.tar.bz2: Not found in archive
tar: stardict-oxford-gb-formated-2.4.2.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
```

The output of tar -xvjf stardict-cedict-gb-2.4.2.tar.bz2```

stardict-cedict-gb-2.4.2/
stardict-cedict-gb-2.4.2/cedict-gb.idx
stardict-cedict-gb-2.4.2/cedict-gb.ifo
stardict-cedict-gb-2.4.2/cedict-gb.dict.dz
```

So it seems like tar can't handle extraction of multiple archives, and I have to type in a separate command to extract each archive. Is there some way to do extract them all in bulk?

Thanks,
Sarah

P.S. I've also tried using Konqueror's "Extract to Here" command, but that only seems to extract a single archive when multiple archives are selected, forcing me to process each archive individually....

---

### Post by scragar on 2008-08-16
```
for untarme in `ls`; do tar -xvjf $untarme; done
```

give that a go

---

### Post by Sarah L on 2008-08-16
thanks, it works quickly & efficiently!

---

### Post by scragar on 2008-08-16
Mind me asking if you could make this thread as solved now? It's under thread tools at the top of the page.

---

