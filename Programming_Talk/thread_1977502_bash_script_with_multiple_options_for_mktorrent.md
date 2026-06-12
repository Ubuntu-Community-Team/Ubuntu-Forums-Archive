---
title: "bash script with multiple options for mktorrent"
date: 2012-05-10
forum: Programming Talk
---

### Post by snikerzz on 2012-05-10
```
**path**
Please choose desired path:
1) /home/user1
2) /home/user2

**tracker**
Please choose desired tracker:
1) http://www.sometracker.com/announce.php
2) http://www.sometracker.com/announce.php

**flag**
Set the private flag (If yes it will add -p option)?
1) Yes
2) No

**piece**
Set the piece length (Please write number for ex: 21).

**source**
specify source (For ex: War.Movie.Megapack.720p.Part3.of.3 | somemovie.mkv).
```After you done it will call mktorrent and set options based on your choices.

```
cd $path
mktorrent -a '$tracker' $flag -l $piece '$source'
```====================
For ex:

```
cd /home/user1
mktorrent -a 'http://www.sometracker.com/announce.php' -p -l 21 'War.Movie.Megapack.720p.Part3.of.3'
```Possible to do that?

---

### Post by codemaniac on 2012-05-10
A menu driven shell script will serve your purpose .An example to get you started .
[http://bash.cyberciti.biz/decision-making/menu-driven-shell-script/](http://bash.cyberciti.biz/decision-making/menu-driven-shell-script/)

---

### Post by Vaphell on 2012-05-10
*select* makes it ever more convenient

```
$ select x in "a b c" "def" "g h i"; do echo "$x"; break; done
1) a b c
2) def
3) g h i
#? 3
g h i
```

```
mktorrent -a '$tracker' $flag -l $piece '$source'
```
never use single quotes with variables, they won't expand to their value and you will get literal $var instead. Use double quotes.

---

### Post by snikerzz on 2012-05-10
> **Vaphell said:**
> *select* makes it ever more convenient

```
$ select x in "a b c" "def" "g h i"; do echo "$x"; break; done
1) a b c
2) def
3) g h i
#? 3
g h i
``````
mktorrent -a '$tracker' $flag -l $piece '$source'
```never use single quotes with variables, they won't expand to their value and you will get literal $var instead. Use double quotes.

Can u write some example?
I do not understand :(

---

### Post by Vaphell on 2012-05-11
example of what?
select or double quotes?

```
#!/bin/bash

paths=( "/home/user1" "/home/user2" )
trackers=( "http://www.sometracker.com/announce.php" "http://www.someothertracker.com/announce.php" )

echo "Choose desired path"
select path in "${paths[@]}"
do
  break
done

echo "Choose desired tracker:"
select tracker in "${trackers[@]}"
do
  break
done

echo "Set the private flag"
select private in "yes" "no"
do
  case "$private" in
    yes) flag="-p"
         ;;
    no)  flag=""
         ;;  
  esac
  break
done

read -p "Piece length: " piece

read -p "Specify source: " source

cd "$path"
mktorrent -a "$tracker" $flag -l $piece "$source"
```

i typed it in right here, in comment box with no testing so don't expect it to work right off the bat :)

---

### Post by snikerzz on 2012-05-12
Thanks Vaphell. Works like a charm :)

---

