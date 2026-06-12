---
title: "Some sed help please"
date: 2008-03-05
forum: Programming Talk
---

### Post by elpaw on 2008-03-05
I'm trying to edit a file which contains entries like:
```
string1
..
boring stuff
..
string2
string1
..
boring stuff
..
string2
string1
..
interesting stuff
..
string1
..
boring stuff
..
string 2
```
trying to remove all instances of 
```
string1
..
boring stuff
..
string2
```

However, nothing I have tried with sed ("sed '/string1/,/string2/d' filename" + derivatives, even trying some complicated expressions with labels and branching) seems to be able to leave the interesting stuff in, because it too is enclosed in string1/string2, even though string2 belongs to the next boring block. I've been scouring the web for hours trying to do this. I know you probably get asked this all the time, but I've reached the end of my tether in looking for the solution (what exactly do you google for, for this problem?).

Cheers.

---

### Post by shawnhcorey on 2008-03-05
Is your heart set on sed?  Other scripting languages can do the same thing easier.

```
perl -nle '$f=1 if/string1/;print if!$f;$f=0 if/string2/;'
```

---

### Post by elpaw on 2008-03-06
> **shawnhcorey said:**
> Is your heart set on sed?  Other scripting languages can do the same thing easier.

```
perl -nle '$f=1 if/string1/;print if!$f;$f=0 if/string2/;'
```

I've done it in bash now.

Here is the code (usage: $prompt> scriptname filename string1 string2) for future reference

```
#!/bin/bash

FILE="$1"; shift;
STRSTART="$1"; shift;
STREND="$1";

DELETING=0;
BUFFER="";


#if come accross string1, start storing in buffer.
#if come accross string2, delete buffer.
#but if come accross string1 again, print buffer, delete buffer and start again

while read LINE; do
    case $LINE in
      *"$STRSTART"*)
        if [ $DELETING -gt 0 ]; then
          echo -e "$BUFFER";
          BUFFER=""
        else
          DELETING=1;
        fi;
        ;;
    esac
    if [ $DELETING -gt 0 ]; then
      if [ "$BUFFER" = "" ]; then
        BUFFER="$LINE"
      else
        BUFFER="$BUFFER\n$LINE";
      fi
    else
      BUFFER="";
      echo "$LINE"
    fi;
    case $LINE in
      *"$STREND"*)
       DELETING=0;
       BUFFER="";
       ;;
    esac
done < $FILE;
```

---

