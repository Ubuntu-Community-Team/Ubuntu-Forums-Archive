---
title: "Simple shell scripting problem: spaces in filenames..."
date: 2007-07-28
forum: Programming Talk
---

### Post by mahy on 2007-07-28
Hello,

i'd like to run a certain action for every file named "Root" within a defined directory tree. This is the stub:

```
#! /bin/tcsh

foreach filename (`find /mnt/win2/work/CVS/ETB_CRM_sources -name Root`)
        echo $filename
end
```

The trouble is that some of the files've got spaces in their paths. Naturally, foreach breaks such paths into two (or more). How do i prevent it? THX for any help.

---

### Post by ssam on 2007-07-28
there are some tips on [http://wooledge.org/mywiki/BashPitfalls](http://wooledge.org/mywiki/BashPitfalls) for similar problems. but i don't know if it will help when using find

---

### Post by girishv on 2007-07-28
Hi,

why to write a script for it, why not just use the exec of find itself ?

find /mnt/win2/work/CVS/ETB_CRM_sources -name Root -exec echo {} \;

Do not forget the "{}" in the above command

Girish

---

### Post by mahy on 2007-07-28
Ok, i fixed some problems this way:

```
#! /bin/tcsh

foreach filename (`find /mnt/win2/work/CVS/ETB_CRM_sources -name Root | tr \  \*`)
          set newname = `echo $filename | tr \* \ `
          echo "certain string" > $newname
end
```

But but the last echo is giving me an error output, due to some ambiguity (wtf?!). How do i fill every "Root" file with a desired content?

---

### Post by angustia on 2007-07-28
try with:

echo "$filename"

---

### Post by mahy on 2007-07-28
> **angustia said:**
> try with:

echo "$filename"

Thanks! The quotation marks fixed it!

---

