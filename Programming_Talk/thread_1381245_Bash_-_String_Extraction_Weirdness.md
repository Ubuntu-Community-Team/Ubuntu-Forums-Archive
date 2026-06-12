---
title: "Bash - String Extraction Weirdness?"
date: 2010-01-14
forum: Programming Talk
---

### Post by tgeer43 on 2010-01-14
I've been using a very simple snippet of code for many months now without incident. Today it starts giving an error every time.
Here's the code:
```
for a in *.mp3
do 
   b="${a:5}"
   mv "$a" "$b"
done
```This should strip the first five characters from each mp3 file name in the current working directory. It's always worked before but now gives a 'Bad Substitution' error on line #3.
I though it might have something to do with the fact that I've moved to 9.10 since I last used it, like some obscure missing package or something. So I booted back in to 9.04 but got the same result.
I just know it's going to turn out to be something stupid but I'm really scratching my head at the moment.

Someone want to save me from a brain aneurysm? ;)

tgeer

---

### Post by lavinog on 2010-01-14
I don't see anything wrong with it at first, but maybe it would help to echo $a and $b
Maybe there is a file with an illegal character.

---

### Post by falconindy on 2010-01-14
Why not use rename?

```
rename 's/^(.){5}//' *.mp3
```
Add the -n flag for "no act" to see the results before you go through with it.

---

