---
title: "executing bash scripts does not work"
date: 2013-08-15
forum: Programming Talk
---

### Post by jairoh_ on 2013-08-15
i'm currently new to bash and i have a tr1.sh script in a folder in the Desktop. but when i tried** bash tr1.sh **, **sh tr1.sh **, **. tr1.sh** or **./tr1.sh**, and error will show 
[COLOR=#ff0000]"li: command not found" [/COLOR] . anyone can help. tnx

---

### Post by DarkAmbient on 2013-08-15
The script are trying to run a command named li, but you no app/tool installed with that name.

What's the content of the script?

---

### Post by jairoh_ on 2013-08-15
> **DarkAmbient said:**
> The script are trying to run a command named li, but you no app/tool installed with that name.

What's the content of the script?

this is the content of the script 
```

for i in `li -A`
do
    newname=`echo $i | tr A-Z a-z`
    mv $i $newname
done


```

i am trying to replace the names of the files ( **FILE1  FILE2  FILE3  FILE4  FILES** ) into lowecase as ( file1 file2 file3 file4 files)

---

### Post by Vaphell on 2013-08-15
you probably wanted *ls* but you shouldn't use *ls* for anything in scripts.

```
for f in *; do [ -f "$f" ] && mv -- "$f" "${f,,}"; done
``` should do the trick

[ -f "$f" ] is a test for being a file, just in case there are dirs you don't want to touch. If not, mv alone will do.

---

### Post by jairoh_ on 2013-08-17
i solved it. i just mistyped **ls** into **li**

---

### Post by sisco311 on 2013-08-17
As Vaphell already mentioned it, you shouldn't use *for i in $(ls)*. See BashPitfalls 01 (link in my signature). Also check out BashPitfalls 02 and 30 and [http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution) .
  
Vaphell's solution should do the trick, but it can be improved. You only have to rename the files which have at least one uppercase letter:
```
for f in *[[:upper:]]*; do ...
```

For more examples you can check out BashFAQ 030.

---

