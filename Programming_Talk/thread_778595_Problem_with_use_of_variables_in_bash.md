---
title: "Problem with use of variables in bash"
date: 2008-05-02
forum: Programming Talk
---

### Post by qrwe on 2008-05-02
Hello,

I've created a simple bash script which makes gzipped tar dumps of specified directories. A snippet looks like this:

HOMEDIR="/mnt/backup"
BACKUPTYPE="daily"
SOURCE_LIST="/etc /var /usr"

tar cfz $HOMEDIR/$BACKUPTYPE_`date \+\%y\%m\%d`.tgz $SOURCE_LIST

The problem is that the dump has only been named with date afterwards, e.g. "080502.tgz". What am I doing wrong?
Thanks for any help!

---

### Post by tseliot on 2008-05-02
try this:
```
tar cfz $HOMEDIR/"$BACKUPTYPE"_$(date \+\%y\%m\%d).tgz $SOURCE_LIST
```

---

### Post by qrwe on 2008-05-05
That made the trick, thank you! Will bash get the point if I nestle qoutes? E.g:

"tar cfz $HOMEDIR/"$BACKUPTYPE"_$(date \+\%y\%m\%d).tgz $SOURCE_LIST"

---

### Post by tseliot on 2008-05-05
If you do this:
```
"tar cfz $HOMEDIR/"$BACKUPTYPE"_$(date \+\%y\%m\%d).tgz $SOURCE_LIST"
```

you're not telling bash to execute a command.

I added quotation marks so as to prevent bash from looking for $BACKUPTYPE_ instead of $BACKUPTYPE. Quotation marks helped for this reason.

---

### Post by grepster on 2008-05-05
> tar cfz $HOMEDIR/"$BACKUPTYPE"_$(date \+\%y\%m\%d).tgz $SOURCE_LIST

tar cfz "$HOMEDIR/${BACKUPTYPE}_$(date +%y%m%d).tgz"

grepster

---

### Post by omrsafetyo on 2008-05-05
^ That was going to be my reccomendation - I think this is the best way to do it.
```

tar cfz "${HOMEDIR}/${BACKUPTYPE}_$(date +%y%m%d).tgz"

```

---

### Post by qrwe on 2008-05-08
I never quit learning new things in Linux environments :-) Thanks all!

---

