---
title: "grep binary windows .lnk"
date: 2009-09-14
forum: Programming Talk
---

### Post by john_spiral on 2009-09-14
Hi,

BACKGROUND - PART OF A NAS(NETWORK ATTACHED STORAGE) MIGRATION
---------------------------------------------------------------

I've got a folder filled with a few thousand sub folders (windows machine names) all containing their own folders ( user accounts on each machine), again containing only .lnk (Windows shortcut files).

I tried the below grep command to ideally print out the location of the file and the UNC path the .lnk is referencing. Unfortunately grep is printing out a mass of rubbish.

grep -Ra '\\\\' .


any idea how I could limit the output to only:

file name (including path) and Windows UNC path contained within file?

thanks in advance

John

---

### Post by Arndt on 2009-09-14
> **john_spiral said:**
> Hi,

BACKGROUND - PART OF A NAS(NETWORK ATTACHED STORAGE) MIGRATION
---------------------------------------------------------------

I've got a folder filled with a few thousand sub folders (windows machine names) all containing their own folders ( user accounts on each machine), again containing only .lnk (Windows shortcut files).

I tried the below grep command to ideally print out the location of the file and the UNC path the .lnk is referencing. Unfortunately grep is printing out a mass of rubbish.

grep -Ra '\\\\' .


any idea how I could limit the output to only:

file name (including path) and Windows UNC path contained within file?

thanks in advance

John

A directory, seen as a file, does contain a lot of rubbish, or rather, a lot of binary information. It's not useful to look at it as a text file.

Does this do what you want?

```
grep '' *
```

If your files contain one line each, it should, if I understood your requirements.

---

### Post by john_spiral on 2009-09-17
> **Arndt said:**
> A directory, seen as a file, does contain a lot of rubbish, or rather, a lot of binary information. It's not useful to look at it as a text file.

Does this do what you want?

```
grep '' *
```

If your files contain one line each, it should, if I understood your requirements.

Sorry for my delayed reply Arndt, work load has got a bit crazy....

I'm looking to search a directory containing a number of binary files (.lnk) for a specific string, but at the same time limiting the display just to the required string. Hope this clarifies what I'm looking for.

---

### Post by lloyd_b on 2009-09-17
> **john_spiral said:**
> Sorry for my delayed reply Arndt, work load has got a bit crazy....

I'm looking to search a directory containing a number of binary files (.lnk) for a specific string, but at the same time limiting the display just to the required string. Hope this clarifies what I'm looking for.

Try this one:```
grep -Eao "\\\\[a-zA-Z0-9. \]+" *.lnk
```

The "E" tells it to use extended regexp
The "a" tells it to process a binary file as a text file
The "o" tells it to output ONLY the matching portion

The "[a-zA-Z0-9. \]" will match any character that is alphanumeric, a period, a space or a backslash (you may or may not need to add some extra punctuation marks into this - depends on how your directories/files are named).  The "+" tells it to match this at least once (this suppresses any stray backslash characters that may be in the file - it has to be a backslash followed by one of the characters in the match).

I tested it on a directory on my machine, and it seems to be working.  If it's not a complete solution for you, at least it's a start.

Lloyd B.

---

### Post by john_spiral on 2009-09-21
thanks for all the responses so far.

I've found a Perl script that fits my needs, hopefully someone else might find it useful:

Perl script to parse a shortcut (LNK) file and retrieve data (H. Carvey).
[http://my.safaribooksonline.com/9781597491730/ch02lev1sec2](http://my.safaribooksonline.com/9781597491730/ch02lev1sec2)

I would have posted the script but it looks like it has a copyright attached.

The script outputs various attributes associated with binary .lnk files.

Thanks

John

---

