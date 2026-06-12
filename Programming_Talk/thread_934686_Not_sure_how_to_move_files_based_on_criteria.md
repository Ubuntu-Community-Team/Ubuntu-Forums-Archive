---
title: "Not sure how to move files based on criteria"
date: 2008-09-30
forum: Programming Talk
---

### Post by Jengu on 2008-09-30
I have a ton of text files, some of which start with the text "0@0@0@0@". I'd like to move all the files starting with that to a separate folder (but not move any files that start with different text). I'm sure bash can do this but I can't figure out how to pipe it all together. Anyone know?

Thanks,

Jengu

---

### Post by ghostdog74 on 2008-09-30
```

grep -l "^0@0@0@0@" file* | xargs -i mv "{}" /tmp 

```

---

