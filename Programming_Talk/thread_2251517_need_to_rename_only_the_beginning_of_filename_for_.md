---
title: "need to rename only the beginning of filename for all files in a directory"
date: 2014-11-04
forum: Programming Talk
---

### Post by cris7 on 2014-11-04
I'm trying to find the quickest and easiest way to change a portion of all the file names in a directory.  The names all start the same, but have varying parts at the end...[INDENT]
EXAMPLEl.shp
EXAMPLEy.shx
EXAMPLEp.proj
[/INDENT]

I started building a script to do this, but since I'm a novice there and required a lot of banging my head on a wall only to fail, I thought I'd ask here if there's an easy way to do this...

---

### Post by steeldriver on 2014-11-04
Change how? what do you want the names to be?

---

### Post by cris7 on 2014-11-04
Sorry,

These...[INDENT]
EXAMPLEl.shp
EXAMPLEy.shx
EXAMPLEp.proj
[/INDENT]

Need to become these...

[INDENT] FIXEDl.shp
FIXEDy.shx
FIXEDp.proj
[/INDENT]

Thanks!

---

### Post by steeldriver on 2014-11-04
You should be able to use the perl-based 'rename' command e.g.

```

rename -nv -- 's/^EXAMPLE/FIXED/' *

```

Note that the -n switch is for testing only (it will output what the command *would *do) - if it looks OK, remove the 'n' to run the command for real

---

### Post by cris7 on 2014-11-04
Ran perfectly.  Removed the n and my files were fixed.

 	Code:
 	rename -v -- 's/^EXAMPLE/FIXED/' * 
Thanks [**[COLOR=#C61919][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")!

---

### Post by cris7 on 2014-11-04
can you explain these two parts of the command:


      --


      ^


Thanks,

---

### Post by steeldriver on 2014-11-04
The -- marks the end of the command's option list, so that everything afterwards gets treated as an input expression or filename argument - it's to handle the case of filenames that begin with a hyphen (rare, but it does happen). You *probably* don't need it but it's good practice.

The ^ (caret) character in a regular expression is a *line anchor* - it tells the command that you only want to replace the string EXAMPLE when it occurs at the start of the filename (so it won't replace the EXAMPLE in abcEXAMPLE.ext).

---

### Post by andrew.46 on 2014-11-08
I cannot better steeldriver's example but to just use the native shell try:

```

for j in EXAMPLE*
do
  mv -v "$j" "${j/#EXAMPLE/FIXED}"
done

```

Not as cool as rename though... A few more here:


bulk rename files with sed, one-liner
[http://www.commandlinefu.com/commands/view/8368/bulk-rename-files-with-sed-one-liner](http://www.commandlinefu.com/commands/view/8368/bulk-rename-files-with-sed-one-liner)

---

