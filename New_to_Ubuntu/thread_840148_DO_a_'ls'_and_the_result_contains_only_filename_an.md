---
title: "DO a 'ls' and the result contains only filename and not the full path"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by byenary on 2008-06-25
Hello,

Im looking for an instruction like this
ls /home/user/folder/*.pdf
But it should only give a list of the filenames and leave out the path, I could script this but im sure there must be a cleaner method using ls but i can't seem to find it or overlooking it.

THx

---

### Post by _sphinx_ on 2008-06-25
So you want only file name and not the full path. Am I right? and also a simle way?

---

### Post by sdennie on 2008-06-25
This is a crude method but, it should work:

```

find /path/to/location/to/search -exec basename '{}' \;

```

---

### Post by byenary on 2008-06-25
That does the job so its fine with me, THX !

---

### Post by _sphinx_ on 2008-06-25
Yup, 
Good command, "basename", never heard of it before.

---

### Post by ad_267 on 2008-06-25
Just because I like practicing my bash when I should be studying:

```
for file in `ls /home/user/folder/*.pdf`; do basename $file; done
```

---

### Post by sdennie on 2008-06-25
To be a bit more specific to your post, you could also try:

```

find /path/to/location/to/search -type f -name "*.pdf" -exec basename '{}' \;

```

That does the same thing but only gets files with the .pdf extension.

---

