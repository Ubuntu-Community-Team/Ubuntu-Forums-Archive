---
title: "SED/Replace"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Warpnow on 2008-05-24
I have a CRAPLOAD of html files (like over a hundred) where I need every instance (100 or so a file) of <TH> to turn into <TH><FONT COLOR ="FF000" SIZE=3>.

Can someone give me the command to do this?

I've been trying it for an hour now with no luck.

---

### Post by sdennie on 2008-05-24
I think:

```

cat some_file | sed -e 's/<TH>/<TH><FONT COLOR ="FF000" SIZE=3>/g' > output

```

---

### Post by Warpnow on 2008-05-24
When I use that command it makes the files blank.

---

### Post by sdennie on 2008-05-24
Not the exact same command but:

```

sdennie@zorba:~$ cat index.html | sed -e 's/<head>/<TH><FONT COLOR ="FF000" SIZE=3>/g' > output
sdennie@zorba:~$ diff index.html output 
4c4
<   <head>
---
>   <TH><FONT COLOR ="FF000" SIZE=3>

```

---

### Post by barnex on 2008-05-24
In the example of vor, if 'some_file' and 'output' are the same file, this will blank the file. This is because linux first clears ('clobbers') a file before writing to it. Maybe this is why you blank your files.

---

### Post by sdennie on 2008-05-24
Yes, that's very true.  Check the -i option of sed if you are using it in this way.

Edit:
To clarify:

```

sed -i -e 's/<TH>/<TH><FONT COLOR ="FF000" SIZE=3>/g' some_file.html

```

---

