---
title: "Linux regular expressions"
date: 2014-08-06
forum: Programming Talk
---

### Post by rogersma on 2014-08-06
Ok, I feel like a complete idiot, but I can't figure this out.

I had a directory that contained a bunch of files.  Many had names like c1.out, c2.out, ... but there were also some named AS32.out, BT12.out, ...

I didn't need any of these latter files.  Since they were all characterized by upper-case letters, I attempted to remove them using:
```
rm [A-Z]*.out
```
This removed everything in the directory, which I didn't want.  Fortunately I could run the same program to generate the files.

I thought perhaps "[A-Z]*" meant "0 or more", so I tried this instead:
```
rm [A-Z][A-Z]*.out
```

This also removed all the files.  Now I really feel like an idiot.  Can someone spot my error (which I'm sure is painfully obvious)?  How do I remove the [A-Z][A-Z]*.out files without also removing the c*.out files?  I should mention my shell is bash.

---

### Post by Bucky Ball on 2014-08-06
*Thread moved to **Programming Talk**.*

I can't help, and I realise you're relatively new here, but this could be the best place for this support request. 

Any commands involving 'rm' should be treated with caution, particularly if proceeded by becoming root, as I'm sure you're aware. ;)

Good luck.

---

### Post by ofnuts on 2014-08-06
> **rogersma said:**
> Ok, I feel like a complete idiot, but I can't figure this out.

I had a directory that contained a bunch of files.  Many had names like c1.out, c2.out, ... but there were also some named AS32.out, BT12.out, ...

I didn't need any of these latter files.  Since they were all characterized by upper-case letters, I attempted to remove them using:
```
rm [A-Z]*.out
```
This removed everything in the directory, which I didn't want.  Fortunately I could run the same program to generate the files.

I thought perhaps "[A-Z]*" meant "0 or more", so I tried this instead:
```
rm [A-Z][A-Z]*.out
```

This also removed all the files.  Now I really feel like an idiot.  Can someone spot my error (which I'm sure is painfully obvious)?  How do I remove the [A-Z][A-Z]*.out files without also removing the c*.out files?  I should mention my shell is bash.

These aren't regular expressions. These are [filename expansions]("https://www.gnu.org/software/bash/manual/html_node/Filename-Expansion.html") (that are done by the shell, before calling the command, so you can try with "ls" before using them with "rm"). They use a [different syntax]("https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html#Pattern-Matching"). You can also use [brace expansion]("https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html") to enumerate the files.

---

### Post by steeldriver on 2014-08-06
I think the issue here is that the shell interprets commands using *glob* *syntax* rather than *regex* *syntax*. TBH I'm not sure the right way to do what you want with globs - perhaps

```

rm +([[:upper:]])*.out

```

(one or more upper-case letters followed by anything, followed by .out) - but test it first with something innocuous like

```

ls +([[:upper:]])*.out

```

or even just

```

echo +([[:upper:]])*.out

```

---

### Post by sisco311 on 2014-08-06
> **steeldriver said:**
> I think the issue here is that the shell interprets commands using *glob* *syntax* rather than *regex* *syntax*. TBH I'm not sure the right way to do what you want with globs - perhaps

```

rm +([[:upper:]])*.out

```

(one or more upper-case letters followed by anything, followed by .out) - but test it first with something innocuous like

```

ls +([[:upper:]])*.out

```

or even just

```

echo +([[:upper:]])*.out

```


+(pattern-list) is an extglob in bash. extglobs aren't enabled by default.

@OP check out:
```
man 7 glob
```
[http://mywiki.wooledge.org/locale](http://mywiki.wooledge.org/locale)
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)


 In bash the LC_COLLATE variable defines the order in which names are sorted.

---

### Post by Vaphell on 2014-08-06
[A-Z] is not foolproof because it depends on locale, LC_COLLATE to be exact. In some locales chars are ordered aAbBcC so the range catches pretty much everything.

[[:upper:]]* should always match only names with 1st uppercase char.

---

### Post by steeldriver on 2014-08-06
I didn't want to complicate things by mentioning extglob - afaik it *is* enabled by the default for interactive shells

---

### Post by sisco311 on 2014-08-06
> **steeldriver said:**
> I didn't want to complicate things by mentioning extglob - afaik it *is* enabled by the default for interactive shells


You  are right,  steeldriver. I stand corrected. 

Thanks!

---

### Post by rogersma on 2014-08-07
> **Vaphell said:**
> [A-Z] is not foolproof because it depends on locale, LC_COLLATE to be exact. In some locales chars are ordered aAbBcC so the range catches pretty much everything.

[[:upper:]]* should always match only names with 1st uppercase char.


I think this may be it.  I just tried the exact same same rm [A-Z]*.out on a different machine and it worked just fine. Oddly they both have the exact same Ubuntu installed, but different people set them up.

Thanks for your fast replies -- the answer wasn't quite as obvious as I'd thought!

---

### Post by gray380 on 2014-08-07
Hi,

Try to put before rm:
$ export LC_ALL=POSIX

should work.

brg,
Serhiy.

---

