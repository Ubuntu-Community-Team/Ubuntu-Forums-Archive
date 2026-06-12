---
title: "how to .tar.gz for more than one file in single attempt."
date: 2009-11-29
forum: Programming Talk
---

### Post by tushar.hiwse on 2009-11-29
[COLOR=navy]Hi Guys,[/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy]Thanks in advance !![/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy]Actually, I want to list 10 big size files from directory (say /logs) and do the .tar.gz in single attempt on Redhat Linux, AIX and Solaris.[/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy][/COLOR] 
[COLOR=navy]Regards,[/COLOR]
[COLOR=navy]Tushar[/COLOR]
 
 :popcorn:

---

### Post by Barriehie on 2009-11-29
> **tushar.hiwse said:**
> [COLOR=navy]Hi Guys,[/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy]Thanks in advance !![/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy]Actually, I want to list 10 big size files from directory (say /logs) and do the .tar.gz in single attempt on Redhat Linux, AIX and Solaris.[/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy][/COLOR] 
[COLOR=navy]Regards,[/COLOR]
[COLOR=navy]Tushar[/COLOR]
 
 :popcorn:

Do you mean to make a .tgz file from 10 files only in a specific directory?  Like ```
tar -cvpzf *somefilename.tgz* file1 file2 file3 ...
```

Barrie

---

### Post by tushar.hiwse on 2009-11-30
But, By using abovesaid command it will create complete .tgz file for 10 big files. I have to create .tgz file for each one in a single shot.

---

### Post by M4rotku on 2009-11-30
just do one file, using the example above but with only one file, then put an & symbol, and then type the same thing for the next file, then another & symbol and so on.  Easiest way that I can think of.

---

### Post by tushar.hiwse on 2009-11-30
[COLOR=blue]Hi M4rotku,[/COLOR]
[COLOR=blue][/COLOR] 
[COLOR=blue]Is there any another way for that ?[/COLOR]
[COLOR=blue]Can u give me it in command ?[/COLOR]

---

### Post by Rinzwind on 2009-11-30
You can do that with a bash script:
```

        #!/bin/bash
        for i in $( ls ); do
            echo item: $i
        done

```

Change the "ls" to search for the files you need.
Change the "echo item: $i" to a tar command.

---

