---
title: "Simple Bash Question"
date: 2010-07-09
forum: Programming Talk
---

### Post by stormchaser on 2010-07-09
Hi all! 

I've been a lurker on these forums for a little over a year and a half now, and have always been able to find useful information. This time, I'm having difficulty finding an answer and so I figured I would finally post here!

Is there any meaningful difference between the two following lines of code (assuming $path is a defined valid system path)?
```
cat ${path}foo.txt
cat ${path}"foo.txt"
```

---

### Post by sisco311 on 2010-07-09
Quoting  is  used  to  remove the special meaning of certain characters or words to the shell. e.g.:
```
cat "file with spaces in the name.txt"
```
or
```
cat 'file with a $ symbol in the name.txt'
```
See:
```
man bash | less +/^QUOTING
```

---

### Post by stormchaser on 2010-07-09
Thanks!  That less trick is nice.

---

### Post by geirha on 2010-07-09
> **stormchaser said:**
> 
Is there any meaningful difference between the two following lines of code (assuming $path is a defined valid system path)?
```
cat ${path}foo.txt
cat ${path}"foo.txt"
```

For this particular case, there is absolutely no difference. As sisco311 mentions, quoting is needed to prevent special characters, or combinations there of, from being expanded by the shell. None of the characters in "foo.txt" are special to the shell, so the quoting is not needed for that part.

The variable expansion, however, should be quoted in case it may contain whitespace or glob characters.
```

cat "$path"foo.txt
# or
cat "${path]foo.txt"

```

If you'd like to learn shell scripting, I recommend reading [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by DaithiF on 2010-07-09
> **geirha said:**
> ```

cat "${path]foo.txt"

```
small typo, should be:
```
cat "${path}foo.txt"
```
can't let an opportunity to correct geirha pass by, as i don't think I'll get another! :)

---

### Post by geirha on 2010-07-09
Damnit! I also wrote {/code], though I spotted that one fairly quickly myself. :)

---

