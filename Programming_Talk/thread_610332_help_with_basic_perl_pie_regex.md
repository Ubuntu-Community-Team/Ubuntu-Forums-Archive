---
title: "help with basic perl pie regex"
date: 2007-11-11
forum: Programming Talk
---

### Post by syxbit on 2007-11-11
i have a script that i run after a fresh install that makes everything the way i like it (installs stuff, copies over my Xorg, bashrc etc..
i can't just copy over my grub though, as that will change with each release

i'm learning perl regex, and wanted to do something basic.
change the default timeout from 10 to 3 seconds, and make it have a hidden menu.
should be easy right?
i had a few problems. first, after timeout there's a TAB, which i'm not sure how to get across, so i tried just replacing the '10' i figured, the regex should just replace the first instance, so it shouldn't destroy stuff.
i tried the following
```

sudo perl -p -i -e 's/10/3' /boot/grub/menu.lst
```

i keep getting the error
```
Substitution replacement not terminated at -e line 1.
```
putting a '/' after the 3 seems to fix this, but then it changes ALL '10' to '3' (i thought you needed '/g' to be global.)
```

sudo perl -p -i -e 's/10/3/' /boot/grub/menu.lst
```
any ideas?

ideally there should be a way to get around the TAB, so I'd like to know both approaches :)

---

### Post by PaulFr on 2007-11-12
Does this work ?```
sudo perl -p -i -e 's/timeout\t+10/timeout\t\t3/' /boot/grub/menu.lst
```/g is for changing all the instances on a single line, otherwise your (s)ubstitute command changes the first instance of 10 to 3 on each and every line.

---

### Post by syxbit on 2007-11-12
yep, that works
thanks a lot
a question. I figure the '\t' means tab, but why do you need a '+' before the 10
and why does the replacement timeout have two tabs?

EDIT:
by the way, i've been trying other stuff, and doing the command with '/' at the end, like in yours (the '/' after 't3' does it for the whole file.)
i did the following command
sudo perl -p -i -e 's/#hiddenmenu/hiddenmenu/' menu.lst
and it replaces ALL '#hiddenmenu' with 'hiddenmenu'
any idea why that's the case?

---

### Post by slavik on 2007-11-12
\t+ means match 1 or more tabs :)

someone hasn't been reading their perldocs ;)

for hidden menu you can also do

s/^#hiddenmenu/hiddenmenu/ (^ means beginning of line in this context)

---

### Post by stylishpants on 2007-11-12
> **syxbit said:**
> 
by the way, i've been trying other stuff, and doing the command with '/' at the end, like in yours (the '/' after 't3' does it for the whole file.)
i did the following command
sudo perl -p -i -e 's/#hiddenmenu/hiddenmenu/' menu.lst
and it replaces ALL '#hiddenmenu' with 'hiddenmenu'
any idea why that's the case?

The perl substitution command always requires three delimiters (s///).  The trailing one is not optional, this is the only valid form of the command.

PaulFR already answered your question.  Here's a more long-winded explanation.

The way that the -p flags works is to effectively put a line-reading loop around whatever code you provide, So, your substitution is applied to every line in the file, every time.

The meaning of the g flag is not what you seem to think.  Normally the s/// operator substitutes only the first match in the string it is applied to.  The g flag does mean 'global', but that means global to the string which s/// is operating on.  In your case, you are applying the s/// operator many times , once for each line of the file.

If you want to read the entire file into one single perl scalar variable and apply the s/// operator to that, then it will replace only the first match in the entire file.  That would look like this:

```
 perl -e '$/=undef; $_ = <>; s/10/3/; print' file
```

You don't need that though. Slavik's solution is better.

---

### Post by syxbit on 2007-11-12
i did a 'man perl' and then installed perl-doc
but it's not intuitive. didn't know how to get a regular man page.

so, from my understanding, the 'g' means global to that line, so if there were more than one instance in the same line, it would do it.
but what if i wanted to do it just once, to the first instance, (or maybe the second)

---

### Post by tr333 on 2007-11-14
You can view the perl documentation (perldoc) online at [http://perldoc.perl.org/](http://perldoc.perl.org/)

---

