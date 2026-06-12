---
title: "bash script to iterate through files and add a line"
date: 2010-06-11
forum: Programming Talk
---

### Post by tarahmarie on 2010-06-11
#!/bin/bash
FILES="*"
for f in "$FILES"
do
     sed -n 'l i Subject: Your Daily Book Part' $f
     cat $f
done

What am I doing wrong here? I go to the directory I want to iterate through, and run this script. Nothing happens. I want to add that line, "Subject: Your Daily Book Part", as the first line in each of the text files in that directory.

---

### Post by lostinxlation on 2010-06-11
what do you mean by nothing happens ?
if you mean the contents of the files didn't get changed, it's because you didn't redirect the result from sed to new files.

---

### Post by tarahmarie on 2010-06-11
I thought that's what I was doing with $f. Is that not supposed to be the name of the new file?

---

### Post by lostinxlation on 2010-06-11
Sed doesn't modify the contents of input files. It just outputs the modified result to the STDOUT and you need to redirect the result to new files.
 
Try this
 
```

sed -e '1s/^/Whatever comments\n/' $f > newfile
cat newfile

```

---

### Post by disabledaccount on 2010-06-11
> **lostinxlation said:**
> Sed doesn't modify the contents of input files.Sed has -i option, that overrides its normal behavior (in-place editing) see manpages.

---

### Post by tarahmarie on 2010-06-11
#!/bin/bash
FILES="*"
for f in "$FILES"
do
sed -e '1s/^/Subject:Your Daily Book Part, Tarah.\n/' $f > $f
cat $f
done

It's still not working. I understand that I need to redirect the output, but I want the output to have the same name. Why doesn't this work?

---

### Post by Compyx on 2010-06-11
As tomazzi already mentioned, sed has the -i/--in-place option:

```

for f in * ; do
    sed -i '1s/^/Subject:Your Daily Book Part, Tarah.\n/' "$f"
    cat "$f"
done

```

The -i option tells sed to do its work `in-place', in other words, to modify the file(s) it is given. The -i option takes an optional argument that specifies a backup file suffix, for example -i.bak would tell sed to backup its input file(s) with a .bak suffix.

Redirecting the output to the same file used as sed's input most likely doesn't work because the input file is opened read-only by sed (when not using -i), so writing to the file fails.

You could simulate the behaviour of -i by using a temporary file:
```

for f in * ; do
    sed -e '1s/Blabla/' "$f" > "$f.$$"
    if [ "$?" -eq "0" ]; then
        mv -f "$f.$$" "$f"
    fi
done

```

---

### Post by geirha on 2010-06-11
globs are not expanded when you quote them. E.g. try: ```
echo '*' "*" *
```

So your for-loop should look like
```
for f in *; do ...; done
```

The second problem is this:
```
sed -e '1s/^/Subject:Your Daily Book Part, Tarah.\n/' $f > $f
``` 
Ok, bash sees you want to redirect output from some command to a file $f, so it opens the file for writing, which truncates it (empties it), then starts the sed program with at least 3 arguments. Sed now tries to read the same file $f which is empty, so it completes. You must use a temporary file.

Now, that is of course if $f happens to be one filename that does not contain any special characters like spaces or globs (in your case it contains *, which is expanded to all files in the current dir). Always quote parameter expansions; "$f", not $f.

To prepend a line to a file see this:
[http://mywiki.wooledge.org/BashFAQ/090](http://mywiki.wooledge.org/BashFAQ/090)

---

