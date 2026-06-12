---
title: "Cannot execute binary file"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by kingrat89 on 2011-12-15
Hi there,

I'm trying to install a .bin file on my Ubuntu 10.04 LTS Lucid and the Terminal shows me this message. I look in google for guide but i didn't understand it all. Can you explain me something about this problem?

Thanks a lot

---

### Post by lechien73 on 2011-12-15
From the directory where your .bin file is downloaded, please run:

```
file ./name-of-file
```

Replace *name-of-file* with the name of your .bin file. Please copy and paste the output here.

---

### Post by spcwingo on 2011-12-15
It might also not be marked as executable.  To do that: in a terminal "cd" to the directory holding your binary file.  Then just:

```
chmod +x ./name-of-file.bin
```

---

