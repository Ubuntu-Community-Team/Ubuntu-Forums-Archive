---
title: "Bash, Sed &amp; Awk tutorials"
date: 2011-04-08
forum: Programming Talk
---

### Post by Drenriza on 2011-04-08
Hi all.

Anyone know some really good / professional / usefull bash, awk and sed tutorials. That are up to date. I have worked with the 3 "languages" or w/e they are, on and off. But would like to get more in debt with it.

And if anyone know of some good online tutorials, books, nuggets, others. That i'm all ears.

Thanks on advance.
Kind regards.

---

### Post by Grenage on 2011-04-08
I've always found [this]("http://www.grymoire.com/Unix/Sed.html") resource to be very handy:

---

### Post by SeijiSensei on 2011-04-08
For sed and awk, [this is the Bible]("http://oreilly.com/catalog/9781565922259").

---

### Post by Rubi1200 on 2011-04-08
> **Grenage said:**
> I've always found [this]("http://www.grymoire.com/Unix/Sed.html") resource to be very handy:
Excellent link Grenage; thanks :-)

---

### Post by nothingspecial on 2011-04-08
For bash

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Check the faq and pitfalls section as well.

---

### Post by ghostdog74 on 2011-04-08
You only need to learn awk out of sed/awk. Forget about sed. With awk, you can do what sed does , and much more, because Awk is a programming language itself. If you want to get more in depth on awk, look at its manual. (see my sig)

---

### Post by jerome bettis on 2011-04-09
^ i'll agree with that in a genral sense, awk is more powerful and can do everything sed can.  But for a lot of smaller things, sed is far quicker.  my personal favorite is

find /dir/ -iname "fileToSub*.txt" -exec sed -i -e 's/replace/new/g' {} \+  

try to do that with awk. :p

OP, "advanced bash scripting guide" is good

set -x
set -e

---

### Post by ghostdog74 on 2011-04-09
> **jerome bettis said:**
> ^ i'll agree with that in a genral sense, awk is more powerful and can do everything sed can.  But for a lot of smaller things, sed is far quicker.  my personal favorite is

find /dir/ -iname "fileToSub*.txt" -exec sed -i -e 's/replace/new/g' {} \+  

try to do that with awk. :p



don't forget, -exec is an option for the find command
```

find . -type f -name "file" -exec awk '{gsub(/replace/,"new")}1' "{}" > temp \; -exec mv temp "{}" \;

```

true, awk doesn't have in place file editing feature, but i just showed you it can be done with just awk as well... and don't forget, sed -i also creates temp files in the back end.

---

### Post by geirha on 2011-04-09
> **ghostdog74 said:**
> 
```

find . -type f -name "file" -exec awk '{gsub(/replace/,"new")}1' "{}" > temp \; -exec mv temp "{}" \;

```


That will only work if there's at most one matching file. It's equivalent to 
```

find . -type f -name "file" -exec awk '{gsub(/replace/,"new")}1' "{}" \; -exec mv temp "{}" \; > temp

``` 

This'll edit the files using awk.
```
find . -type f -name "file" -exec awk '{gsub(/replace/,"new"); print > FILENAME}' {} +
```

Oh and to the OP, for learning bash, stay away from the bash guides at tldp.org. Read the bash guide that nothingspecial posted. It's the only one that teaches good practice.

---

### Post by jerome bettis on 2011-04-09
> **ghostdog74 said:**
> don't forget, -exec is an option for the find command
```

find . -type f -name "file" -exec awk '{gsub(/replace/,"new")}1' "{}" > temp \; -exec mv temp "{}" \;

```

true, awk doesn't have in place file editing feature, but i just showed you it can be done with just awk as well... and don't forget, sed -i also creates temp files in the back end.

i know it can be done, but look how much more work that was.  thanks for helping me prove my point so well :lolflag:

bash/sed/awk are all worth learning.  i've been meaning to look at some other shells one of these days zsh/ksh/csh .. ive seen some people doing even more powerful stuff over there.  But i'm so used to bash it is a bit weird.

---

### Post by ghostdog74 on 2011-04-09
> **jerome bettis said:**
> i know it can be done, but look how much more work that was.  thanks for helping me prove my point so well :lolflag:

that was just a poor example.. You can see geirha's example. (@geirha's thanks,been dormant for a while and forgot about FILENAME). Sorry what point are you proving again? 

> 
bash/sed/awk are all worth learning.  

when it comes to parsing files, bash (to call awk ) and awk is all you need. The rest of the tools that can read files -> wc, tr, sed, grep, cat, nl, head, etc one can chuck it in his toolbox and never use it. But for some, like tail, is sometimes indispensable due to its purpose. (although you can also use awk to simulate "tail")

---

### Post by Drenriza on 2011-04-12
> **ghostdog74 said:**
> You only need to learn awk out of sed/awk. Forget about sed. With awk, you can do what sed does , and much more, because Awk is a programming language itself. If you want to get more in depth on awk, look at its manual. (see my sig)

If awk is a programming language, what is it designed to program? can it program an entire program, with a gui and such?

---

### Post by ghostdog74 on 2011-04-12
> **Drenriza said:**
> If awk is a programming language, what is it designed to program? can it program an entire program, with a gui and such?
Have you read the link "Effective awk" in my sig? awk is little language that provides you with the basics for programming, arrays, variables, functions, if/else, switch etc. What can it program ? anything that you can produce with those programming features! Except GUI...because it doesn't have that kind of library (not like fully featured ones like Python or Ruby). See [here]("http://awk.info/?awk100") for more on what awk can do

---

### Post by matt_symes on 2011-04-12
Hi

> For bash

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Check the faq and pitfalls section as well.

+1 to this. I liked the site so much i put it in my sig. Well worth reading before any tldp documentation.

Kind regards

---

### Post by graphicsmanx1 on 2012-11-01
awesome glad I ran across this  :popcorn:

---

