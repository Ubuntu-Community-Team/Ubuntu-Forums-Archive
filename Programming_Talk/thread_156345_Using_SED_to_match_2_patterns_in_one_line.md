---
title: "Using SED to match 2 patterns in one line"
date: 2006-04-06
forum: Programming Talk
---

### Post by jaykup on 2006-04-06
How would I do this?

For example.

this is a line matching [0090] 0090
this is a non-matching line [1010] 0001

---

### Post by amohanty on 2006-04-07
Why do you want to venture into sed-hell just do and echo/cat on the text and pipe it to grep:

> cat file.txt | grep "matching text"
or
> cat file.txt | grep -v " non matching text"
or 
> fgrep "matching text"
or
> fgrep -v "non matching text"

for raw text input, replace the cats with the string output command.

If you can provide some more details as to what you are mathing, where are you getting the content from etc. it would be more helpful

---

### Post by jaykup on 2006-04-07
Ok, that won't work for what I wanted it for.  Here is the actual list.

[K-F]_ONE_PIECE_001_[44899E42].AVI  44899E42
[K-F]_ONE_PIECE_002_[DC2AFB03].AVI  DC2AFB03
[K-F]_ONE_PIECE_003_[E8C81815].AVI  E8C81815
[K-F]_ONE_PIECE_004_[35E8EC6F].AVI  35E8EC6F
[K-F]_ONE_PIECE_005_[89BA23B1].AVI  89BA23B1
[K-F]_ONE_PIECE_006_[84AB1A9C].AVI  84AB1A9C
[K-F]_ONE_PIECE_007_[CFA2D23E].AVI  CFA2D23E
[K-F]_ONE_PIECE_008_[F6B7A11A].AVI  F6B7A11A
[K-F]_ONE_PIECE_009_[4984356F].AVI  4984356F
[K-F]_ONE_PIECE_010_[9A20CC38].AVI  9A20CC38
[K-F]_ONE_PIECE_011_[9B1CBA8A].AVI  9B1CBA8A
[K-F]_ONE_PIECE_012_[F2C49D5D].AVI  F2C49D5D
[K-F]_ONE_PIECE_013_[F25BF818].AVI  F25BF818
[K-F]_ONE_PIECE_014_[CAA389AD].AVI  CAA389AD
[K-F]_ONE_PIECE_015_[F028A4B7].AVI  F028A4B7
[K-F]_ONE_PIECE_016_[9EC1A011].AVI  9EC1A011
[K-F]_ONE_PIECE_017_[C0A06DDE].AVI  C0A06DDE
[K-F]_ONE_PIECE_018_[2B3A4FC1].AVI  3G9Q5ZC2

I'd like something that would be able to pick out the lines that are the same (they are crc32 checksums) 1-17 all match up, but 18 does not.  How could I pick out just 18?

This is why I wouldn't like to use grep, because I don't want to specify what I am searching for, just a pattern of 8 characters inside the [ ] that match the last column.

---

### Post by amohanty on 2006-04-07
[QUOTE=jaykup]Ok, that won't work for what I wanted it for.  Here is the actual list.

[K-F]_ONE_PIECE_001_[44899E42].AVI  44899E42
[K-F]_ONE_PIECE_002_[DC2AFB03].AVI  DC2AFB03
[K-F]_ONE_PIECE_003_[E8C81815].AVI  E8C81815
[K-F]_ONE_PIECE_004_[35E8EC6F].AVI  35E8EC6F
[K-F]_ONE_PIECE_005_[89BA23B1].AVI  89BA23B1
[K-F]_ONE_PIECE_006_[84AB1A9C].AVI  84AB1A9C
[K-F]_ONE_PIECE_007_[CFA2D23E].AVI  CFA2D23E
[K-F]_ONE_PIECE_008_[F6B7A11A].AVI  F6B7A11A
[K-F]_ONE_PIECE_009_[4984356F].AVI  4984356F
[K-F]_ONE_PIECE_010_[9A20CC38].AVI  9A20CC38
[K-F]_ONE_PIECE_011_[9B1CBA8A].AVI  9B1CBA8A
[K-F]_ONE_PIECE_012_[F2C49D5D].AVI  F2C49D5D
[K-F]_ONE_PIECE_013_[F25BF818].AVI  F25BF818
[K-F]_ONE_PIECE_014_[CAA389AD].AVI  CAA389AD
[K-F]_ONE_PIECE_015_[F028A4B7].AVI  F028A4B7
[K-F]_ONE_PIECE_016_[9EC1A011].AVI  9EC1A011
[K-F]_ONE_PIECE_017_[C0A06DDE].AVI  C0A06DDE
[K-F]_ONE_PIECE_018_[2B3A4FC1].AVI  3G9Q5ZC2

I'd like something that would be able to pick out the lines that are the same (they are crc32 checksums) 1-17 all match up, but 18 does not.  How could I pick out just 18?

This is why I wouldn't like to use grep, because I don't want to specify what I am searching for, just a pattern of 8 characters inside the [ ] that match the last column.[/QUOTE]


Ok since your file columns match up you can do the following brute force way:
Put the abive contents into a file. THen create a shell script called test.sh with:
```

OFS=$IFS
export IFS='
'

for l in $(cat file)
do
  x1=$(echo $l | cut -c22-29)
  x2=$(echo $l | cut -c36-43)
  if [ "$x1" != "$x2" ]
  then
    echo $l
  fi
done

export IFS=$OFS

```

Then do a:
> chmod +x sh
./test

You can probably use awk and parse out parts do the same, but this is a quick and dirty way to do it.

Before you descend into bash programming hell, I would suggest checking out some python. Far more easier with fancy regex too.

HTH
AM

---

