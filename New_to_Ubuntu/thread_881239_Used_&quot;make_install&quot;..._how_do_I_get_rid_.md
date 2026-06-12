---
title: "Used &quot;make install&quot;... how do I get rid of it now? (Hardy)"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Chalks on 2008-08-05
I downloaded quodlibet (a music player) and mutagen.  Then, I unpacked the tar.gz files and went into their respective directories and used "sudo make" then "sudo make install".

They installed just fine, but now I want to remove them completely from my computer.  How?  is there a "remove quodlibet" command or some such thing?  Or do I need to manually figure out where all the installed files went to and remove them that way?

Thanks

---

### Post by loell on 2008-08-05
generally you can 

```
sudo make uninstall
```

to remove it.

check out checkinstall if you want a manageable install from source.

---

