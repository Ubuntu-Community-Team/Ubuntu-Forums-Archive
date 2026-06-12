---
title: "Bash Script: Write everything in one go"
date: 2009-10-01
forum: Programming Talk
---

### Post by Matuku on 2009-10-01
I'm writing a small Bash Script to generate a list of Comics that I'm looking to get and it just seems very clunky that I have to tell it to pass echo to the file for each subtitle, etc; is there anyway just to have all the output written to the file at the end?

I'm also looking for any tips on ways this script seems "clunky" or if there's a much more efficient method.

```

#!/bin/bash
# Making a list of comics I have yet to collect.

if [ ! -f ComicList ]
  then touch ComicList
fi

echo "---Green Lantern---" > ComicList

for number in `seq 1 40`
do
  echo "Green Lantern $number" >> ComicList
done

echo -e "\n---Green Lantern Corps---" >> ComicList

for number in `seq 1 35`
do
  echo "Green Lantern Corps $number" >> ComicList
done

```

---

### Post by ghostdog74 on 2009-10-01
if using bash, you can just omit the use of seq. this just the same thing as seq 1 10
```

for i in {1..10}
do
  # echo $i
done

```

---

### Post by Arndt on 2009-10-01
> **Matuku said:**
> I'm writing a small Bash Script to generate a list of Comics that I'm looking to get and it just seems very clunky that I have to tell it to pass echo to the file for each subtitle, etc; is there anyway just to have all the output written to the file at the end?

I'm also looking for any tips on ways this script seems "clunky" or if there's a much more efficient method.

```

#!/bin/bash
# Making a list of comics I have yet to collect.

if [ ! -f ComicList ]
  then touch ComicList
fi

echo "---Green Lantern---" > ComicList

for number in `seq 1 40`
do
  echo "Green Lantern $number" >> ComicList
done

echo -e "\n---Green Lantern Corps---" >> ComicList

for number in `seq 1 35`
do
  echo "Green Lantern Corps $number" >> ComicList
done

```

You can redirect stdout for the duration of the script:

```

#!/bin/bash

exec > ComicList

echo "---Green Lantern---"

for number in `seq 1 40`
do
  echo "Green Lantern $number"
done

etc.


```

---

### Post by Matuku on 2009-10-01
> **ghostdog74 said:**
> if using bash, you can just omit the use of seq. this just the same thing as seq 1 10
```

for i in {1..10}
do
  # echo $i
done

```

Ah, I did wonder if there was a simpler way to do that; seemed strange that there wasn't! Thanks!

---

### Post by Matuku on 2009-10-01
> **Arndt said:**
> You can redirect stdout for the duration of the script:

```

#!/bin/bash

exec > ComicList

echo "---Green Lantern---"

for number in `seq 1 40`
do
  echo "Green Lantern $number"
done

etc.


```

Will stdout return to normal when the script ends? Or is an additional command needed?

---

### Post by Arndt on 2009-10-01
> **Matuku said:**
> Will stdout return to normal when the script ends? Or is an additional command needed?

It will return to normal. The script can't change things for its parent process.

---

### Post by Matuku on 2009-10-01
> **Arndt said:**
> It will return to normal. The script can't change things for its parent process.

How can I return it to stdout before the end of the program if I want to do that?

---

### Post by Arndt on 2009-10-02
> **Matuku said:**
> How can I return it to stdout before the end of the program if I want to do that?

You will have to make bash remember what the original stdout was. You can pick a file descriptor which is ordinarily not used, like 3, redirect stdout to it, and later redirect back:

```
exec 3>&1

exec >/tmp/aha

echo a
echo b

exec 1>&3

echo c
echo d
```

---

### Post by geirha on 2009-10-02
You can also group together commands with { ; }
```

{
  echo "---Green Lantern---"
  for i in {1..10}; do echo "Green Lantern $i"; done
  echo ...
} > ComicList

```


You can also do stuff like this:
```

for line in "---Green Lantern---" \
            "Green Lantern "{1..40} \
            "" \
            "---Green Lantern Corps---" \
            "Green Lantern Corps "{1..35}
do
    echo "$line"
done > ComicList

```

Or, using arrays; in somewhat obscure ways ...
```

lines=("---Green Lantern---" "Green Lantern "{1..40} "" "---Green Lantern Corps---" "Green Lantern Corps "{1..35})
IFS=$'\n'; echo "${lines[*]}" >ComicList; unset IFS

```

---

