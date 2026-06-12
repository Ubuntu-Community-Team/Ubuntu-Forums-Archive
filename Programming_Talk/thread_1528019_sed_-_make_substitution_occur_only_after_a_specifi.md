---
title: "sed - make substitution occur only after a specified string"
date: 2010-07-10
forum: Programming Talk
---

### Post by yc2 on 2010-07-10
Hi guys,

This problem can be solved with a workaround so I don't need urgent help this time, but if someone knows the answer I am very curious :)

I was preparing a commandfile to substitute blanks by underscore in filenames.

When I had come to this point I ran into a problem
```
ren c:\this is a foldername\this is a   filename %%%% c:\this is a foldername\this is a    filname
```

I had put %%%% just to separate input and output filenames.

Let's say I first want to change all blanks after %%%% to _

I never found a command for that. Maybe just not thinking hard enough. I therefore cut the line in two at %%%% and worked on two lines and then joined them again. It took several commands. (Esp. since sed 's/\n//' does not seem to work. I had to remove ALL new lines and then replace every second one. I later learnt in another thread (thanks) that 'perl -pe s/\n//' would have done it)

Is there a sed command replacing every blank with _ AFTER %%%%?

I guess I could do the following repeatedly, but *one *command would be better, of course

```
$ echo 'ren c:\this is a foldername\this is a   filename %%%% c:\this is a foldername\this is a    filname' | sed 's/%%%% \([^ ]*\) /%%%% \1_/'
ren c:\this is a foldername\this is a   filename %%%% c:\this_is a foldername\this is a    filname
```

Thanks

EDIT: corrected an error in the last sed argument

---

### Post by DaithiF on 2010-07-10
Hi,
yes you can do this using the conditional branch operator 't'.  this allows you to keep repeating a substitution as long as it keeps succeeding (replacing).  One no more matches, the script can exit.

e.g.:
```
$ echo $test
ren c:\this is a foldername\this is a filename %%%% c:\this is a foldername\this is a filname

$ sed -r ':a;s/^(.*% [^ ]*) /\1_/;ta'  testfile
ren c:\this is a foldername\this is a filename %%%% c:\this_is_a_foldername\this_is_a_filname
```

---

### Post by yc2 on 2010-07-10
That was exactly what I wanted and also very cool. :smile:

Thanks a lot DaithiF !

---

### Post by cfjrocha on 2012-02-23
In this case this solution dont work
Remove all <br> after MARK 2

MARK 1 text<br> text <br> text MARK 2<br> text<br> text <br> text.<br>

The expected result is:
MARK 1 text<br> text <br> text MARK 2<br> text text text.

I trying sed -r ':a;s/^(.*MAKR 2.[^ ]*.)<br>/\1/;ta'

But without sucessefull ... :(

---

### Post by DaithiF on 2012-02-23
Hi,
> **cfjrocha said:**
> 
Remove all <br> after MARK 2

```
$ x="MARK 1 text<br> text <br> text MARK 2<br> text<br> text <br> text.<br>"
$ echo "$x" | sed -r ':a;s/^(.*MARK 2.*)<br>/\1/;ta'
MARK 1 text<br> text <br> text MARK 2 text text  text.

```> 
The expected result is:
MARK 1 text<br> text <br> text MARK 2<br> text text text.
not really, the expected result of 'remove all <br> after MARK 2' is as above.
if you want to remove all <br> after MARK 2 except for the first trailing <br> then:
```
$ echo "$x" | sed -r ':a;s/^(.*MARK 2<br>.*)<br>/\1/;ta'
MARK 1 text<br> text <br> text MARK 2<br> text text  text.

```> 
I trying sed -r ':a;s/^(.*MAKR 2.[^ ]*.)<br>/\1/;ta'
But without sucessefull ... :(Apart from the typo (MAKR != MARK), I'm not sure what you're trying for, maybe this?:
```
$ echo "$x" | sed -r ':a;s/^(.*MARK 2.[^ ]+.*)<br>/\1/;ta'
MARK 1 text<br> text <br> text MARK 2<br> text text  text.

```

---

