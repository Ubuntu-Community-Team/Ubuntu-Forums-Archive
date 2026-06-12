---
title: "Testing path for inclusion of sub path"
date: 2008-09-03
forum: Programming Talk
---

### Post by MattUK on 2008-09-03
I am trying to find a way of reliably checking a path for a substring. This is what I have at the moment:

```

if [[ ! $destination_dir =~ '\/data\/store\/blarp\/*' ]]; then

```

Basically the only way I want that if statement passing is if the full path contains /data/store/blarp, but the above doesn't seem to be working consistently for me.

Any help appreciated.

---

### Post by stylishpants on 2008-09-03
Perl:

```
fhanson@fhanson:~$ var="/path/good"
fhanson@fhanson:~$ if perl -e 'exit !($ARGV[0] =~ m[/good])' "${var}"; then echo "yes"; else echo "no"; fi
yes

fhanson@fhanson:~$ var="/path/bad"
fhanson@fhanson:~$ if perl -e 'exit !($ARGV[0] =~ m[/good])' "${var}"; then echo "yes"; else echo "no"; fi
no
fhanson@fhanson:~$ 
```

The code needs that weird little inversion because the perl match operator returns true/false as 1/0, but bash return codes map true/false to 0/1.

Of course a nice benefit of using perl is that its match operator lets you use something like m[] for delimiters instead of //, meaning that you don't need to escape all the slashes in your path anymore.

---

### Post by MattUK on 2008-09-03
That does the trick, thanks! Id noticed the weird 0/1 thing with bash, very confusing..

---

### Post by mssever on 2008-09-03
> **MattUK said:**
> That does the trick, thanks! Id noticed the weird 0/1 thing with bash, very confusing..
It's because the exit status of a successful program is 0. Most of what you do in bash is run external programs, so you have to cope with their exit statuses.

---

### Post by ghostdog74 on 2008-09-03
> **MattUK said:**
> I am trying to find a way of reliably checking a path for a substring. This is what I have at the moment:

```

if [[ ! $destination_dir =~ '\/data\/store\/blarp\/*' ]]; then

```

Basically the only way I want that if statement passing is if the full path contains /data/store/blarp, but the above doesn't seem to be working consistently for me.

Any help appreciated.

you do not have to use any external programs to check path in bash
```

case $destination_dir in
  /data/store/blarb* ) echo "yes";;
  * ) echo "no";;
esac


```

---

