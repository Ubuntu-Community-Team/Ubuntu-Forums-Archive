---
title: "How can I search for all subfolders but excluding hidden ones? (bash)"
date: 2007-08-30
forum: Programming Talk
---

### Post by Yuzem on 2007-08-30
Something like:
```
find . -type d
```
But excluding hidden folders.
I tried to use grep but I don't know how to use the dot:
```
find . -type d | egrep  -v '/home/user/.*./.*'
```
or
```
find . -type d | egrep  -v '/home/user/.*\./.*'
```
:(

---

### Post by Mr. C. on 2007-08-30
How about 

```
find . -type d | egrep -v '/\..*$|^.$'
```

MrC

---

### Post by bashologist on 2007-08-30
I've never done something like this before but these seem to work.

For one pattern:
```
find . ! -path './.*'
```

For two patterns:
```
find . !  \( -path '*pattern*' -o -path './.*' \)
```

With sed maybe something like this:
```
find | sed '/.*\/\./d'
```

---

### Post by Yuzem on 2007-08-30
Ok, the command that I need is:
```
find . -type d ! -path ".*/.*"
```
Thanks a lot! :)

---

### Post by bashologist on 2007-08-30
After some more thought maybe '*/.*' would be better for matching hidden paths.

Try these both separately and you'll see the difference.
```
find ~ ! -path '.*/.*'
find ~ ! -path '*/.*'
```

---

### Post by Yuzem on 2007-08-30
Yes, but in the script that I am making I need to start the search from a specified path:

```
find "$path" -type d ! -path "$path*/.*"
```

If the specified path is a hidden folder maybe the following will give me no result:
```

path=~/.hidden/something
find "$path" -type d ! -path "*/.*"
```

I don't know... but the first example works great.

---

### Post by bashologist on 2007-08-30
That should work good. Easy stuff isn't it?! Gj.

---

### Post by Yuzem on 2007-08-30
Yes, it is easy if you know how to do it.
Thanks again for your help!

---

