---
title: "Rename All Files in a Folder Numerically"
date: 2013-04-20
forum: Programming Talk
---

### Post by _user on 2013-04-20
I have about 13000 files in a folder with names following this pattern: newaaaapmr, newaaaapms, newaaaapmt.  No extensions.

I'd like to rename all the files numerically from 1-13000.  How would I go about doing this?

---

### Post by cybergalvez on 2013-04-20
I'm sure there is a quick bash script that can do this, but considering im not that good with bash I would write a quick python script to do it. something like this:

```
import os, sys

files = os.listdir(sys.argv[1]) # use the full path to the folder as an arugument to the script
files.sort()
n=1
for f in files:
    os.rename(f, n)
    n += 1
```

---

### Post by Vaphell on 2013-04-20
do you need fixed width (0-padded) as in 00001-13000? *printf %05d *will do that, if you don't need it you can replace whole *$( printf ... $i )* with *$i* alone

```
i=1; for f in *; do **echo** mv "$f" "$( printf "%05d" $i )"; ((i++)); done
```

if the printout is ok remove echo to actually rename files.

---

### Post by steeldriver on 2013-04-20
Might it be worth adding a 'plain file' test - in case the directory contains subdirectories that are not to be included in the sequential rename?

```
i=1; for f in *; do [COLOR=#0000ff]**if [ -f "$f" ]; then**[/COLOR] echo mv "$f" "$( printf "%05d" $i )"; ((i++)); [COLOR=#0000ff]**fi;**[/COLOR] done
```

Or if the target files all have the "new" prefix we could be even more specific

```
i=1; for f in [COLOR=#0000ff]**new**[/COLOR]*; do [COLOR=#0000ff]**if [ -f "$f" ]; then**[/COLOR] echo mv "$f" "$( printf "%05d" $i )"; ((i++)); [COLOR=#0000ff]**fi;**[/COLOR] done
```

---

### Post by Vaphell on 2013-04-20
good point, better safe than sorry
one could also write the condition as *[ -f "$f" ] || continue;*

---

### Post by uc50_ic4more on 2013-04-20
I think both the (GTK-based) "pyrenamer" and "gprename" applications, available through the Software Centre, could assist you.

---

### Post by _user on 2013-04-20
Great answers - always informative to get input from different people.  Much appreciated.

I used the answer from Vaphell and it worked perfectly for my use case.

---

