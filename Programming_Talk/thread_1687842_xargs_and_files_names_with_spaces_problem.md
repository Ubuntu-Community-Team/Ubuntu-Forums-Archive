---
title: "xargs and files names with spaces problem"
date: 2011-02-14
forum: Programming Talk
---

### Post by abadr on 2011-02-14
Hi,
I'm trying to figure out a command to move or delete duplicate files from a directory using 'fdupes' and 'xargs'. Here's what I have so far
```
fdupes -f . | xargs mv -t ~/duplicates
```
The problem with this command is that it can't handle file names with spaces in them. Reading xargs's man page there's a --delimiter option which is supposed to accepet /n but when I use it it still splits the file name:
```
fdupes -f . | xargs --delimiter=\n  mv -t ~/duplicates
```
xargs also has -0 option with works with null sperators but fdupes only used \n as a seperator.
Any ideas on how to do this?

Thanks

---

### Post by An Sanct on 2011-02-14
I don't know if this will help, but in Ubuntu, spaces are "escaped" with "\"

example
```
env WINEPREFIX="/home/an/.wine" wine C:\\windows\\command\\start.exe /Unix /home/an/.wine/dosdevices/c:/users/an/Start\ Menu/Programs/Avery\ Dennison/DesignPro\ 5.lnk
```

This is an actual link from WINE.

---

### Post by MadCow108 on 2011-02-14
put the delimiter in quotes:
```
fdupes -f . | xargs --delimiter="\n"  mv -t ~/duplicates
```

---

### Post by Arndt on 2011-02-15
> **abadr said:**
> Hi,
I'm trying to figure out a command to move or delete duplicate files from a directory using 'fdupes' and 'xargs'. Here's what I have so far
```
fdupes -f . | xargs mv -t ~/duplicates
```
The problem with this command is that it can't handle file names with spaces in them. Reading xargs's man page there's a --delimiter option which is supposed to accepet /n but when I use it it still splits the file name:
```
fdupes -f . | xargs --delimiter=\n  mv -t ~/duplicates
```
xargs also has -0 option with works with null sperators but fdupes only used \n as a seperator.
Any ideas on how to do this?

Thanks

I don't know what 'fdupes' is, but 'xargs' has an option -0, which goes well together with the option -print0 of 'find'. Maybe 'fdupes' has something similar.

---

### Post by geirha on 2011-02-15
Assuming none of the filenames contain newlines, you can use a while read loop instead.

```

while IFS= read -r file; do 
  mv "$file" ~/duplicates
done < <(fdupes -f .)

```

See [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001) for more.

---

### Post by The Cog on 2011-02-15
Or this one?
```
IFS=$'\n'; for f in $(fdupes -f .) ; do mv -t ~/duplicates "$f" ; done
```

---

### Post by sisco311 on 2011-02-15
> **The Cog said:**
> Or this one?
```
IFS=$'\n'; for f in $(fdupes -f .) ; do mv -t ~/duplicates "$f" ; done
```

Nope. Check out the link posted by geirha.

If you use a for loop, you should disable pathname expansion:
```
oIFS=$IFS IFS=$'\n' ;set -o noglob; for file in $(fdubes -f ./); do echo "$file"; done; IFS=$oIFS ; set +o noglob
```

---

### Post by abadr on 2011-02-19
Thank you all, the following worked by adding another "\" to the "\n":
```

fdupes -f . | xargs --delimiter=\\n  mv -t ~/duplicates

```

---

