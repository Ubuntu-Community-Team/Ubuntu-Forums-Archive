---
title: "find and rm"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by 1234 on 2008-05-03
i am a newbie i wanted to give a command that would search and delete files i tried rm $(find / -name "filename") but doesnt help what should i do

---

### Post by bsharp on 2008-05-03
First find the file:
```
locate *filename*
```

then:
```
rm *path/to/file*
```

---

### Post by noynac on 2008-05-03
> **1234 said:**
> i am a newbie i wanted to give a command that would search and delete files i tried rm $(find / -name "filename") but doesnt help what should i do

The following might help. I'd be really careful with this. 

[I]Another use of xargs is illustrated below.  This command will efficiently remove all files named core from your system (provided you run the command as root of course):

find / -name core | xargs /bin/rm -f
find / -name core -exec /bin/rm -f '{}' \; # same thing
find / -name core -delete                  # same if using Gnu find

(The last two forms run the rm command once per file, and are not as efficient as the first form.)[/I]

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

---

### Post by 1234 on 2008-05-04
thank you  my intention was automatically removing multiple files found on search as in noynac

---

