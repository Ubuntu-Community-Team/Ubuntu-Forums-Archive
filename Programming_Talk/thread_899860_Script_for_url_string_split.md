---
title: "Script for url string split"
date: 2008-08-24
forum: Programming Talk
---

### Post by vasquez on 2008-08-24
Hi people I'm in desperate need for a script that does the following.

Read an url address from a file
ex: [http://www.url.com/page12/search.php?string=](http://www.url.com/page12/search.php?string=)

Save the url root address in another file (url.txt)
ex: [http://www.url.com](http://www.url.com)

Save everything that's after the root address (after .com) in another file (stuff.txt)
ex: /page12/search.php?string=

So basically I end up with 2 text files.

Any ideas/scripts would be highly welcomed.

---

### Post by ghostdog74 on 2008-08-24
depending on how your data file really looks like
```

awk -F "/" '/http/ {
  print $1,$2,$3 > "after.com"
  $1=$2=$3=""
  gsub(/^\/+/,"")
  print $0 > "stuff.txt"
}
' OFS="/"  file

```

---

### Post by lswb on 2008-08-24
look up the "cut" command. Say you have read the URL into a variable named URL, then something like

echo $URL|cut -d / -f1-3
should output everything up to but not including the third slash in the string, and
echo $URL|cut -d / -f4- 
will echo everything after the 3rd slash. If you need more complicated filtering check out sed or awk.

---

### Post by vasquez on 2008-08-24
thank you very much!

---

