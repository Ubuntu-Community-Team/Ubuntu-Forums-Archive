---
title: "Filename Script"
date: 2007-04-17
forum: Programming Talk
---

### Post by I_Failed_C++ on 2007-04-17
I stumped myself in a script.  I'm writing a script to generate a formated playlist from an unformated text file containing filenames (they are entire path filenames) and I need a to strip the path off of the filename.  I'm sure that a single line will probably do this but can't find the command.

Thanks,
Bill

---

### Post by dsl on 2007-04-17
bash? Try basename.

---

### Post by I_Failed_C++ on 2007-04-17
yes, bash script.  Thanks, I will try that.

---

### Post by I_Failed_C++ on 2007-04-20
I could not get basename to work with a pipe or a redirect.  Is it just me or is this a weird command that won't work that way?  Could some try it out with a pipe or a redirect.
I figured out a way to do it on my own ended up just doing that way.  I did:

less $1 | awk -F "/" '{ printf $NF }'

Thanks,
Bill

---

### Post by ghostdog74 on 2007-04-20
in bash,
```

# var="/home/test/test.txt"
# echo ${var##*/}
test.txt

```

---

### Post by cwaldbieser on 2007-04-22
> **I_Failed_C++ said:**
> I could not get basename to work with a pipe or a redirect.  Is it just me or is this a weird command that won't work that way?  Could some try it out with a pipe or a redirect.
I figured out a way to do it on my own ended up just doing that way.  I did:

less $1 | awk -F "/" '{ printf $NF }'

Thanks,
Bill

It does not appear that "basename" reads from standanrd input, so using it in a pipeline means having to use a somewhat awkward while loop.
```

$ less $1 | while read line; do basename "$line"; done

```
This seemed to run a lot slower on my PC than the awk solution you came up with, though.

I think this sed command should also work:
```

less $1 | sed 's;.*/;;'

```

---

### Post by WW on 2007-04-22
You can give a filename as an argument to awk or sed.  This is more efficient than using 'less' (or 'cat') to pipe the file to the command.  So the example given above that uses awk can be changed to
```

awk -F "/" '{ print $NF }' $1

```
and the example that uses sed can be changed to
```

sed 's;.*/;;'  $1

```

---

