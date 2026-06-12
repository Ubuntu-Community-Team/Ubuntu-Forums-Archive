---
title: "After grep -B1, how to merge the two lines into one please"
date: 2010-11-22
forum: Programming Talk
---

### Post by amylase on 2010-11-22
I grepped infile for the line containing greptext, plus the line just before it, and I saved both lines to outfile.

grep -B1 'greptext' infile > outfile

So now outfile has two lines, for example

LineB1LineB1LineB1LineB1LineB1
greptextgreptextgreptextgreptextgreptext

How do I merge the two lines so I get only one line that looks like:

LineB1LineB1LineB1LineB1LineB1greptextgreptextgreptextgreptextgreptext

I tried so many different ways including:
sed -e :a -e '$!N; s/\n/ /; ta' outfile
cat outfile | tr -d '\n' > newfile
sed -i -e 's/$/\r/' outfile

None of these listed above work.

Any suggestions please? Thanks very much.

---

### Post by Arndt on 2010-11-22
> **amylase said:**
> I grepped infile for the line containing greptext, plus the line just before it, and I saved both lines to outfile.

grep -B1 'greptext' infile > outfile

So now outfile has two lines, for example

LineB1LineB1LineB1LineB1LineB1
greptextgreptextgreptextgreptextgreptext

How do I merge the two lines so I get only one line that looks like:

LineB1LineB1LineB1LineB1LineB1greptextgreptextgreptextgreptextgreptext

I tried so many different ways including:
sed -e :a -e '$!N; s/\n/ /; ta' outfile
cat outfile | tr -d '\n' > newfile
sed -i -e 's/$/\r/' outfile

None of these listed above work.

Any suggestions please? Thanks very much.

I didn't look at your other attempts, but this one works for me:

```
cat outfile | tr -d '\n' > newfile
```

(although I would just write

```
tr -d '\n' <outfile > newfile
```
)

Are you sure it didn't work?

---

### Post by SlugSlug on 2010-11-22
I've had this prob a few times,

I bang the text in google search then copy it back :)

---

