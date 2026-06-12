---
title: "Choose (a) word from a wordlist"
date: 2010-03-12
forum: Programming Talk
---

### Post by hakermania on 2010-03-12
Hi, I have a text file with 1500 words. Could it be a script that will keep the words that only have all these letters:
n i o m s c t a
If you could show me the way I would be greatful!

---

### Post by n0dix on 2010-03-12
Is this for homework?

---

### Post by hakermania on 2010-03-13
> **n0dix said:**
> Is this for homework?

No, its a mission for a mission-like site.:)

---

### Post by Some Penguin on 2010-03-13
It's a trivial problem and shouldn't be remotely hard for even a beginner -- a solution in Perl can easily be written which is no longer than the original post!

---

### Post by superarthur on 2010-03-13
> **Some Penguin said:**
> It's a trivial problem and shouldn't be remotely hard for even a beginner -- a solution in Perl can easily be written which is no longer than the original post!

You took my line. lol
Perl is my favourite language so far.

(to the author of this post) Just use regular expression. ;)

---

### Post by hakermania on 2010-03-13
Somebody suggested perl -lane 'print if (grep {/\b[niomscta]+\b/} $_);  ' /home/alex/Desktop/wordlist.txt
But the output was
montana
monica
macintos
action
tomcat
cannon
tinman
nissan
station
samson
tattoo
cccccc
sonics
cosmos
mission
tintin
moomoo
Something like that doesn't suits me. I want to find a word from the wordlist that is developed by the letters "n i o m s c t a"
(Something like unscrumbling the word choosing words only from the wordlist, not globaly)

---

### Post by superarthur on 2010-03-13
> **hakermania said:**
> Somebody suggested perl -lane 'print if (grep {/\b[niomscta]+\b/} $_);  ' /home/alex/Desktop/wordlist.txt
But the output was
montana
monica
macintos
action
tomcat
cannon
tinman
nissan
station
samson
tattoo
cccccc
sonics
cosmos
mission
tintin
moomoo
Something like that doesn't suits me. I want to find a word from the wordlist that is developed by the letters "n i o m s c t a"
(Something like unscrumbling the word choosing words only from the wordlist, not globaly)

Can you give an example of the text you are searching from, and the output you expect?

---

### Post by Some Penguin on 2010-03-13
*shrug*

There's the regex approach, but that really needs sorting first, unless you either want to use one regex per letter, or one monster regex that has every permutation essentially.

Using a table to track which letters you want to see but haven't yet is faster for longer strings.  The worst case will be linear in the string size, which scales at least as well as any sort and much better than any comparison-based sort.  It also lets you 'abort' easily if the condition is not only that the term *contains* such letters but that it contains no others.

---

### Post by Lux Perpetua on 2010-03-13
You know, I think this would have made a decent "beginner's programming challenge" for this forum. :-D It seems like a fun little throwaway problem that might be useful in learning the ins & outs of a programming language.

---

### Post by kaibob on 2010-03-14
I'm learning and wanted to give this a try. I suspect there is an easier or better way to do this and would appreciate any suggestions. 

The thought occurred to me that the OP may want to match words that contain all of the specified letters but no others. If that's the case, my script doesn't work.

```
#!/bin/bash

while read -a word ; do
   for i in ${!word[@]} ; do
      match=$(awk '{IGNORECASE=1} /e/ && /n/ && /o/' <<<${word[$i]})
      [[ $match ]] && echo ${word[$i]}
   done
done < file
```

> $ cat file
One red fox
is done with dinner
but was alone and did not have enough to eat.
$ 
$ wordscript
One
done
alone
enough

After completing the above, I decided to see if I could use awk without bash. My knowledge of awk is extremely limited, but I cobbled together the following, which does appear to work. 

```
awk '{IGNORECASE=1} { for (i=1;i<=NF;i++) { if ($(i) ~ /o/ && $(i) ~ /n/ && $(i) ~ /e/) print $i }}' file
```

> $ cat file
One red fox
is done with dinner
but was alone and did not have enough to eat.
$
$ awk '{IGNORECASE=1} { for (i=1;i<=NF;i++) { if ($(i) ~ /o/ && $(i) ~ /n/ && $(i) ~ /e/) print $i }}' file
One
done
alone
enough

---

