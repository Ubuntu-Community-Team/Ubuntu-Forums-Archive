---
title: "Renaming directories?"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by liferules on 2012-06-29
I need help renaming directories to be more windows friendly... I need to remove : from all directory names that it might appear. Need to search : and replace with _ ... this is really beyond my paygrade... need some help...

---

### Post by oldos2er on 2012-06-29
Post moved to its own thread.

---

### Post by sisco311 on 2012-06-29
Are you looking for a GUI tool or a CLI command for this? Do you want to rename the directories recursively?

---

### Post by David Andersson on 2012-06-29
If you want a GUI tool, pyRenamer (package **pyrenamer**) or GPrename (package **gprename**)

**GUI**

In **GPrename**, select tab *Files* or *Directories*, navigate to the directory that contain the files or dirs of interest, select tab *Replace/Remove*, check *Regular Expression*, enter from expression **[\\?*<>:|"^]** enter to expression **_**, press *Preview* to see what it will do before doing it, then press *Rename*.

(If you see a sad face in the regular expression above, it is a colon ":" and a vertical bar "|".)

Similar procedure with **pyRenamer**, but Ifind no Regular Expression so you have to replace one illegal character at a time, e.g. ":" to "_", then "?" to "_", etc. On the other hand, in pyRenamer you can rename files and/or dirs recursively (that is in all subdirs of the specified dir).

**CLI**

If you want a CLI command, prename (package **perl**)

General syntax of **prename**

```
prename PERL_EXPRESSION FILENAMES...
```

Syntax with regexp and substitution

```
prename 's/FROM/TO/g' FILENAMES...
```

Example: replace characters forbidden in FAT and NTFS (/,\,?,*,<,>,:,|,",^) with underscore, for all dir names in current directory

```
prename 's/[\\?*<>:|"^]/_/g' */
```

---

### Post by sisco311 on 2012-06-29
prename has a -n option which is useful for testing. Invoked with this option prename will show what files would have been renamed:

```
prename **-n** PERL_EXPRESSION FILENAMES...
```

If you have to rename the directories recursively, then I'd suggest you to use GNU/find & bash:
```
find [COLOR="Red"]/path/to/dir[/COLOR] -depth  -name '*:*' -type d -execdir bash -c '**echo "Working directory: $PWD"; echo** mv -b -- "$1" "${1//:/_}"' _ {} \;
```
You have to replace [COLOR="Red"]/path/to/dir[/COLOR] with the actual relative or absolute path to the directory.

The above command will only print the working directory and the mv (move) command which should rename the directories. To actually rename them delete the **bold** part (**echo "Working...**).

---

### Post by sisco311 on 2012-06-29
> **David Andersson said:**
> 
(If you see a sad face in the regular expression above, it is a colon ":" and a vertical bar "|".)


The [noparse][noparse][/noparse] tag allows you to stop the parsing of BB code.

[noparse][noparse]:|[/noparse][/noparse] --> [noparse]:|[/noparse]

---

### Post by David Andersson on 2012-06-29
> **sisco311 said:**
> 
If you have to rename the directories recursively, then I'd suggest you to use GNU/find & bash:
```
find [COLOR="Red"]/path/to/dir[/COLOR] -depth  -name '*:*' -type d -execdir bash -c '**echo "Working directory: $PWD"; echo** mv -b -- "$1" "${1//:/_}"' _ {} \;
```


1) **Or** you can use *prename* in *find*
```
find . -depth -type d -exec prename -n 's/:/_/g' {} \;
```
With -n to preview, as before. Remove -n when you are ready to go. (The -depth option is needed to rename inner dirs before outer dirs. The "." is for current dir. Replace with "/path/to/dir" for any dir.)

2) Remember that Windows filesystems **ignore case** in filenames. If there are filenames like "AnUmberGame.txt" and "aNumberGame.txt" in the same directory, it won't work even when characters are fixed. (Same with "ThePopEssay.txt" / "ThePopesSay.txt", "cc" / "CC", etc.)

You can find out if there are filenames that will clash when ignoring case with this command
```
find | tr A-Z a-z | sort | uniq -d
```

---

