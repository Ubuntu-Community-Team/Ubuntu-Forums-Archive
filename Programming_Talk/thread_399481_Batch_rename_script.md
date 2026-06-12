---
title: "Batch rename script"
date: 2007-04-02
forum: Programming Talk
---

### Post by dadevilx on 2007-04-02
I'm trying to rename a lot of files from one format to another. I can just rename them all by hand, but I won't, just because it can be easier and I want to know how.

My files look like this:
*Blablabla [01x23] Blaat.ext*

and I want to convert it to something like this:
*Blablabla - 01x23 - Blaat.ext*


I just can't get it to work in a script (because of the spacing in the names??). My intention was that the script checks for files in the directory with the 'right' filename and then renames them. This is what I thought of, at least something like this:
```

for x in `ls` # doesn't work
do
   #if (${x} == y) then # doesn't work either, doh
      name = `awk '{print $1}'`
      ssn = `awk '{print $2}' | cut -c 2,3`
      ep = `awk '{print $2}' | cut -c 5,6`
      ttl = `awk '{print $3}'`

      echo ${name} - ${ssn}x${ep} - $ttl
      #mv ${x} "{$name} - $.....
   #fi
done

```

Any suggestions?

---

### Post by doonium on 2007-04-02
the spaces in the files are messing you up.  i've gotten around that by setting the field separator to the newline:

IFS=$'\n'

you can also use an `ls -1` to make sure the files are listed one per line.

---

### Post by H3g3m0n on 2007-04-02
For i in 'ls' won't work on files with spaces in the names, the best solution is to use an obscure find command, I actually wrote a thing about it here: [http://h3g3m0n.wordpress.com/2007/03/28/run-a-unix-command-on-each-file-in-a-directroy/](http://h3g3m0n.wordpress.com/2007/03/28/run-a-unix-command-on-each-file-in-a-directroy/)

Wouldn't it be simpler to replace all instances of "[" with "- " and "]" with " -" rather than trying to split the filenames up?

---

### Post by WW on 2007-04-02
Use the **rename** command.

---

### Post by dadevilx on 2007-04-02
Got it working, maybe not perfect, but it'll do:

```
#!/bin/bash
ls -1 *.avi | while read FILE
do
	target=$(echo "$FILE" | sed -e 's/\(.*\ \)\[/\1- /1' | sed -e 's/\]/ -/1')
	mv "$FILE" "$target"
done
```

---

### Post by WW on 2007-04-02
You could also do this:
```
$ rename 's/(.* )\[(.*)\](.*)/$1- $2 -$3/g'  *.avi
```

---

