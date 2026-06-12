---
title: "Find command with GPG"
date: 2007-12-17
forum: Programming Talk
---

### Post by oneadvent on 2007-12-17
Ok, so I have a group of files that I want to encrypt when I leave my computer, but the problem is that there is 10 to 15 of them, and it is inconvenient to have to type 
```
gpg -e filename
``` 
each time. so I decided to make a script to do it for me. I got this:
```
find * -exec gpg -e {} \;
```
the problem is it still asks for the user each time.

How can I do this where I just type the script name and it is all encrypted?

I know its an easy answer, but I am missing it somewhere.

---

### Post by oneadvent on 2007-12-17
nevermind, I got it...

```

find * -exec gpg -e -r USERID {} / ;

```

does it fine.

---

