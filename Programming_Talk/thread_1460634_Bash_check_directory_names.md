---
title: "Bash check directory names"
date: 2010-04-23
forum: Programming Talk
---

### Post by dragos2 on 2010-04-23
I have a folder that contains folders with this name pattern:
ddddd_name

where d is a digit

I want to do a bash script that checks if all the folders have 5 digits in its name.

Any ideas ?

I tryed 
```

ls -l folder | awk '{print $8}'

```

Output is something like:
```

12345_name
12384_name
..

```

But how do I extract the first 5 characters from each line and check if it contains 5 digits 
in bash ?

---

### Post by MadCow108 on 2010-04-23
my ugly solution assuming 5 digits followed by more nondigits
```

if [ `echo "$dirname" | grep -xE "[0-9]{5}[^0-9]+"` ]; then
  echo "ok";
fi

```

"[0-9]{5}_.*" if its 5 digits separated by _ from arbitrary string

if you know it are 5 digits you can extract them with: ${dirname:0:5}

---

### Post by dragos2 on 2010-04-23
> **MadCow108 said:**
> my ugly solution assuming 5 digits followed by more nondigits
```

if [ `echo "$dirname" | grep -xE "[0-9]{5}[^0-9]+"` ]; then
  echo "ok";
fi

```"[0-9]{5}_.*" if its 5 digits separated by _ from arbitrary string

if you know it are 5 digits you can extract them with: ${dirname:0:5}

Thanks, this is what I did so far

```


#!/bin/bash
dirname=$(ls -l /folder | awk '{ print $8}')

if [ `echo "$dirname" | grep -xE "[0-9]{5}[^0-9]+"` ]; then
  echo "ok";
elso
 echo "not ok"
fi

```

How do I make it check for every line and list the lines that are not ok ?

---

### Post by dragos2 on 2010-04-23
I found a solution, I will post it here :)

Also I think that this can be done in pure awk or grep if one knows.

---

### Post by dragos2 on 2010-04-23
This is the script so far, I modified a bit the pattern from [0-9]{5}[^0-9]+ to [0-9]{5}[.]+ to ignore all character after the first 5 numbers:

```

ls -l /folder | awk '{print $8}' | sed -e '/somefolderIwanttoremove/d' | while read line; do
  if [ ! `echo "$line" | grep -xE "[0-9]{5}[.]+"` ]; then
     echo "not ok:"
     echo $line
  fi
done

```

Any idea of why it prints that its not ok even if it is ?

---

### Post by gmargo on 2010-04-23
You can use **find** to get a list of matching directories.
```

find folder -type d -name '[0-9][0-9][0-9][0-9][0-9][^0-9]*' -print

```

---

### Post by stylishpants on 2010-04-23
List all directory names in the current dir that do not match your pattern:

```
ls -d */ | egrep -v '^[0-9]{5}_'
```

---

### Post by geirha on 2010-04-23
Using bash:
```

shopt -s extglob nullglob

dirs=( !([0-9][0-9][0-9][0-9][0-9]_*)/ )
echo "There are ${#dirs[@]} directories that does not start with a five digit number followed by an underscore:"
printf "%s\n" "${dirs[@]}"

```

[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by dragos2 on 2010-04-26
> **geirha said:**
> Using bash:
```

shopt -s extglob nullglob

dirs=( !([0-9][0-9][0-9][0-9][0-9]_*)/ )
echo "There are ${#dirs[@]} directories that does not start with a five digit number followed by an underscore:"
printf "%s\n" "${dirs[@]}"

```[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

Thanks for this :)

But where do I say on which folder to apply ?

---

### Post by geirha on 2010-04-26
> **dragos2 said:**
> Thanks for this :)

But where do I say on which folder to apply ?

Either
```
cd "/path/to/that/directory"
dirs=( !([0-9][0-9][0-9][0-9][0-9]_*)/ )
# or
dirs=( "/path/to/that/directory"/!([0-9][0-9][0-9][0-9][0-9]_*)/ )

```

---

### Post by dragos2 on 2010-04-26
> **geirha said:**
> Either
```
cd "/path/to/that/directory"
dirs=( !([0-9][0-9][0-9][0-9][0-9]_*)/ )
# or
dirs=( "/path/to/that/directory"/!([0-9][0-9][0-9][0-9][0-9]_*)/ )

```

Thank you, it seems that bash is pretty useful by itself. 

As I promised this is the solution I build:
```


ls -l /folder | awk 'NR>1{print $8}' | sed -e '/someDirIExclude/d' | while read line;
do
  if [ ! `echo "$line" | grep -xE "[0-9]{5}[0-9a-zA-Z_-]+"` ]; then
     echo "Not ok: $line"
  fi
done

```

I am pretty sure that everything can be compacted in a awk or grep except for the ls.

---

### Post by geirha on 2010-04-26
> **dragos2 said:**
> Thank you, it seems that bash is pretty useful by itself. 

As I promised this is the solution I build:
```


ls -l /folder | awk 'NR>1{print $8}' | sed -e '/someDirIExclude/d' | while read line;
do
  if [ ! `echo "$line" | grep -xE "[0-9]{5}[0-9a-zA-Z_-]+"` ]; then
     echo "Not ok: $line"
  fi
done

```

I am pretty sure that everything can be compacted in a awk or grep except for the ls.
... or done safely, in bash.

```
#!/bin/bash

cd /folder || exit
for dir in */; do
  if [[ $dir = *someDirIExclude* ]]; then
    echo "Skipping: $dir"
    continue
  elif [[ $dir != [0-9][0-9][0-9][0-9][0-9]_* ]]; then
    echo "Not ok: $dir"
    continue
  fi
  echo "Ok: $dir"
done

```

[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by dragos2 on 2010-04-26
> **geirha said:**
> ... or done safely, in bash.

```
#!/bin/bash

cd /folder || exit
for dir in */; do
  if [[ $dir = *someDirIExclude* ]]; then
    echo "Skipping: $dir"
    continue
  elif [[ $dir != [0-9][0-9][0-9][0-9][0-9]_* ]]; then
    echo "Not ok: $dir"
    continue
  fi
  echo "Ok: $dir"
done

```[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

Thanks, interesting link. I am using ls -l so I think I am safer than using simpler ls.
Your script misses [a-zA-Z_-]+ can I add it the same way as you did with numbers ?

Thanks again :)

---

### Post by geirha on 2010-04-26
> **dragos2 said:**
> Thanks, interesting link. I am using ls -l so I think I am safer than using simpler ls.
Your script misses [a-zA-Z_-]+ can I add it the same way as you did with numbers ?

Thanks again :)

The ere  "[0-9]{5}[0-9a-zA-Z_-]+"  will match for instance "1234567890foo", I thought you wanted to match a five-digit number followed by an underscore?

Maybe show some example filenames, and which of them you want to be matched and which not.

---

### Post by dragos2 on 2010-04-27
> **geirha said:**
> The ere  "[0-9]{5}[0-9a-zA-Z_-]+"  will match for instance "1234567890foo", I thought you wanted to match a five-digit number followed by an underscore?

Maybe show some example filenames, and which of them you want to be matched and which not.

It seems that I have an error: I want to match 12345_name where name can be [a-zA-Z_-].

---

### Post by geirha on 2010-04-27
The ERE that'll match that is «^[0-9]{5}_[a-zA-Z_-]+/$» then.

You can match the same with extglob

```

shopt -s extglob
...

[[ $dir = [0-9][0-9][0-9][0-9][0-9]_+([a-zA-Z_-])/ ]] && echo match
# or if you also want to match non-ascii alphabetical characters (depending on your locale)
[[ $dir = [0-9][0-9][0-9][0-9][0-9]_+([[:alpha:]_-])/ ]] && echo match

```

---

### Post by dragos2 on 2010-04-27
> **geirha said:**
> The ERE that'll match that is «^[0-9]{5}_[a-zA-Z_-]+/$» then.

You can match the same with extglob

```

shopt -s extglob
...

[[ $dir = [0-9][0-9][0-9][0-9][0-9]_+([a-zA-Z_-])/ ]] && echo match
# or if you also want to match non-ascii alphabetical characters (depending on your locale)
[[ $dir = [0-9][0-9][0-9][0-9][0-9]_+([[:alpha:]_-])/ ]] && echo match

```

Great, thank you :)

But this ^[0-9]{5}_[a-zA-Z_-]+/$ does not work as expected in my grep -xE, any idea of why ?

---

