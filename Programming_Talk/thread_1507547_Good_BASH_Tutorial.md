---
title: "Good BASH Tutorial"
date: 2010-06-11
forum: Programming Talk
---

### Post by Jahocolips on 2010-06-11
I'm looking for an eloquent and comprehensive tutorial of scripting with BASH. Any suggestions?

---

### Post by K.Mandla on 2010-06-13
Moved to Programming Talk.

---

### Post by geirha on 2010-06-14
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) along with BashFAQ on the same wiki.

---

### Post by Compyx on 2010-06-14
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

### Post by geirha on 2010-06-14
> **Compyx said:**
> [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

I recommend one stay AWAY from the abs guide. It teaches you to write bugs, not scripts.

---

### Post by Compyx on 2010-06-14
> **geirha said:**
> I recommend one stay AWAY from the abs guide. It teaches you to write bugs, not scripts.

Any particular reasons for this? I know it tends to experiment a lot and isn't very clearly written, but I found it to be quite useful as a reference. It does often fail to mention portability issues, but then again, it's a Bash guide, not a general shell-scripting guide.

I'll look into the guide you mentioned and see if it's any better.

---

### Post by geirha on 2010-06-14
I can mention a few I noticed while taking a quick perusing of random chapters

For one, it is very inconsistent, using the [ command vs the [[ and (( keywords interchangably, even in the same scripts. that's bad practice. [ should not be used at all in bash-scripts. Same with `` vs $().

There's lack of quoting all over the place, so a ton of the scripts and snippets you find there will fail on filenames containing spaces or globs.

In some cases it gets laughably silly. Take for instance this snippet from [http://tldp.org/LDP/abs/html/loops1.html](http://tldp.org/LDP/abs/html/loops1.html)
```

for file in "$( find $directory -type l )"   # -type l = symbolic links
do
  echo "$file"
done | sort                                  # Otherwise file list is unsorted.
#  Strictly speaking, a loop isn't really necessary here,
#+ since the output of the "find" command is expanded into a single word.
#  However, it's easy to understand and illustrative this way.

```
The point is to show that you can pipe a loop, but does the example need to be so absurdely useless?

The page on regular expressions fail to fully distinguish what regular expression syntax bash uses compared to grep, sed, awk, etc., and which are GNU-extensions.

It CAN be used as a reference, but only if you know how to filter the junk.

EDIT: Oh, and another point worth mentioning. It uses the external expr command to do math in a lot of places. Bash can itself do all that expr can do, and much better. You only need to use expr if you have to write a script to run on ancient shells like the bourne shell, which lacks arithmetics and posix parameter expansions.

---

### Post by Compyx on 2010-06-14
Thanks for taking the time to explain your views. The abs guide is indeed very inconsistent in its examples, perhaps because many people contributed code snippets. (it should be the authors job to filter those snippets and edit them if needed, but no such effort was made) 

The lack of quoting is one thing that bothered me a lot, I myself quote every expansion, but I can see that people starting out might get into the wrong habit when reading the abs guide. The guide you mentioned tells us to always quote expansions, in bold, so that's a big plus.

As for the regular expressions, a missed opportunity indeed. Regular expressions aren't the easiest things to explain, especially when considering the different 'flavors' of regexes, but a mention of some pitfalls and perhaps a few tables listing some differences would have been nice.

I've read a few pages of the guide you mentioned, and it seems to be a lot more concise and actually tries to teach good coding practises, which is something I've missed from the abs guide and a lot of other online material.
I won't be recommending the abs guide anymore, I think I'll stick to the guide you linked to, once I've read all of it and found no serious flaws.

Anyway, thanks for the insight.

---

