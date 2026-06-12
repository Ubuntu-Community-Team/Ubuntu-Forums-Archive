---
title: "How to redirect output to grep?"
date: 2015-09-20
forum: Programming Talk
---

### Post by susja on 2015-09-20
Hello,
I'm using 'grep' with multiple patterns. It looks like this
grep -E "abc|def|ghi" dir1/*
The content of patterns that I pass to 'grep' e.g. "abc|def|ghi" is stored in file2.txt

1. Actually initially I have file1.txt
abc|def|ghi|
2. Then I run this:
cat file1.txt | gawk 'BEGIN{printf "\""}{print}' | sed -e '$s/|$/"/' > file2.txt
3. This results in "abc|def|ghi"
4. I open file2.txt, copy it content and paste it on command line for list of patterns for -E
5. I want to avoid step 4. i.e. copy/paste and want to redirect the content of file2.txt to grep -E like this
grep -E < cat file2.txt dir1/*
But it failed with error:
bash: cat: No such file or directory
--
Could someone please advice for correct syntax for redirecting the content of file2.txt to option -E of grep ?
Thanks in advnace

---

### Post by Lars Noodén on 2015-09-20
For step 4 you can do [process substitution](http://tldp.org/LDP/abs/html/process-sub.html) using <( ... )

```

 grep -E -f **<(awk '{ sub( /^[[:space:]]*/, "" ); sub( /\|$/, "" ); print }' file1.txt )** dir1/*

```

But step 2 can be simplified.  awk can do what sed does and more.

---

### Post by susja on 2015-09-20
Thanks so much.
I'm all set now

---

