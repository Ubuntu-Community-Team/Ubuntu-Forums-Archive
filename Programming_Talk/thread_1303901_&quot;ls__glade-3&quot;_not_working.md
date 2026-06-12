---
title: "&quot;ls | glade-3&quot; not working"
date: 2009-10-28
forum: Programming Talk
---

### Post by J V on 2009-10-28
If I'm correct the following script should open up all of my glade files for me... it works if I type them in by hand...
```
ls | glade-3
```

---

### Post by geirha on 2009-10-28
In the [glade-3 man-page](http://manpages.ubuntu.com/manpages/jaunty/en/man1/glade-3.1.html) there's no mention of it accepting a filelist from standard input. Secondly it only accepts one file as argument according to the synopsis, so you'll probably have to run a loop to start it once for each file.
```
for file in *.glade; do
  glade-3 "$file"
done

```

If it doesn't automatically background itself (i.e. stops at the first invocation of glade-3), you can add an & at the end.
```

for file in *.glade; do 
  glade-3 "$file" & 
done

```

Oh and you can do that all on one line, which is handy for interactive shells
```

for file in *.glade; do glade-3 "$file"; done
# or
for file in *.glade; do glade-3 "$file" & done

```

---

### Post by J V on 2009-10-28
Well using this Glade opens multiple files correctly... I don't know why the pipe won't work...
```
glade-3 file1.glade file2.glade
```And when I run the second one glade pops open a ton of seperate windows, which is no good either...
```
for file in *.glade; do glade-3 "$file" & done
```

---

### Post by geirha on 2009-10-28
I see, the man-page doesn't match the actual command then.
```
glade-3 *.glade
```

---

### Post by J V on 2009-10-28
Wow, so simple, and it works! Thanks :P

[SOLVED]

---

