---
title: "Bash: comparing with a minimum difference"
date: 2011-11-11
forum: Programming Talk
---

### Post by brickmasterj on 2011-11-11
In a bash-script, i want to have two files compared using 'cmp' and a 'while':
```
val=0;
while  [ $val -eq 0 ]  ;  do

sleep 200

wget -np -c "$intput_site" --output-document /tmp/new.html

file1=/tmp/old.html
file2=/tmp/new.html

cmp $bestand1 $bestand2 &> /dev/null 
val=$?
done
```
But i want that old.html and new.html are compared with a difference in 5 sentences.
So, if more than 5 sentences are different to that 5 sentences in the other file, close the loop, if there are less than 5 sentences different, do the loop again... And again...
Is there anyway to do that? It's no problem if I have to use another command than 'cmp'.
(Srry for bad Enlish, i'm Dutch)

---

### Post by karlson on 2011-11-11
> **brickmasterj said:**
> In a bash-script, i want to have two files compared using 'cmp' and a 'while':
```
val=0;
while  [ $val -eq 0 ]  ;  do

sleep 200

wget -np -c "$intput_site" --output-document /tmp/new.html

file1=/tmp/old.html
file2=/tmp/new.html

cmp $bestand1 $bestand2 &> /dev/null 
val=$?
done
```
But i want that old.html and new.html are compared with a difference in 5 sentences.
So, if more than 5 sentences are different to that 5 sentences in the other file, close the loop, if there are less than 5 sentences different, do the loop again... And again...
Is there anyway to do that? It's no problem if I have to use another command than 'cmp'.
(Srry for bad Enlish, i'm Dutch)

5 sentences or 5 lines?

---

### Post by brickmasterj on 2011-11-11
> **karlson said:**
> 5 sentences or 5 lines?
5 Lines.

---

### Post by karlson on 2011-11-11
> **brickmasterj said:**
> 5 Lines.

use diff.

---

### Post by brickmasterj on 2011-11-11
> **karlson said:**
> use diff.
Ok, but how? I've never used 'diff' before... Can you give an example?

---

### Post by karlson on 2011-11-11
> **brickmasterj said:**
> Ok, but how? I've never used 'diff' before... Can you give an example?

simplest way:
```

diff <file1> <file2>

```

What I would suggest doing is to download the files and compare the manually.  See what the output looks like and then parse it accordingly.

Even better you can use Perl for this.  Probably will yield much simpler code then Bash would.

---

### Post by brickmasterj on 2011-11-12
> **karlson said:**
> simplest way:
```

diff <file1> <file2>

```

What I would suggest doing is to download the files and compare the manually.  See what the output looks like and then parse it accordingly.

Even better you can use Perl for this.  Probably will yield much simpler code then Bash would.
I know, but this is one piece of a big bash-script.
Ok, but how do you set the minimum difference to 5 different lines?

---

### Post by ofnuts on 2011-11-12
> **brickmasterj said:**
> I know, but this is one piece of a big bash-script.
Ok, but how do you set the minimum difference to 5 different lines?
Maybe do something like in this thread on the diff output:
[http://ubuntuforums.org/showthread.php?t=1875505](http://ubuntuforums.org/showthread.php?t=1875505) (despite the title it's not using awk)

---

### Post by brickmasterj on 2011-11-12
It is also ok if the loop just counts the lines, and and the loop if there are 5 lines more or less:
```
val=0;
while  [ $val -eq 0 ]  ;  do

sleep "$time"

wget -np -c "$site" --output-document /tmp/new.html

file1=/tmp/old.html
file2=/tmp/new.html

diff $file1 $file2 | grep "^---" | wc -l
val=$?
done
```
But this code does not work, so what's the correct form?

---

