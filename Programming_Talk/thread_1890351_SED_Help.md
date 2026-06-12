---
title: "SED Help"
date: 2011-12-03
forum: Programming Talk
---

### Post by tdyboc on 2011-12-03
Need help with SED.  I'm trying to join lines in a file, foo.  I've been able to do that, but, I also need to do a couple other edits.  Given the following example file:
 
this is line1
next line2
line3
next line4
then line5
last ;
 
using SED to join the above lines would yield:
 
this is line1 next line2 line3 next line4 then line5 last ;
 
However, I need to also remove blank lines and|or lines that begin with two dashes.  For example:
 
this is line1
next line2
line3
 
--next line4
then line5
last ;
 
When I attempt to perform other edits they don't work as I would expect and I'm not understanding it completely.  I get the concept just am missing something logically here.  I thought by adding:
 
/^$/ d
/^--/ d
 
to the SED below it would remove blank lines and lines that begin with two dashes but I cannot get it to work for me.  I've tried placing them before and after the 'branch' with no success.
 
sed '
:a
$!N
s/\n/ /
ta
' foo
 
:confused:  Any suggestions appreciated.

---

### Post by The Cog on 2011-12-03
```
cat myfile | tr -s '\n' ' '
```
translate newlines to spaces and squeeze repeats. This is OK unless you have lines with multiple spaces that you need to keep. In that case, this should do:
```
cat myfile | tr -s '\n' '\n' | tr '\n' ' '
```
There are probably better ways. Actually, I'd like to see a solution using sed but I can't think of a way.

---

### Post by SevenMachines on 2011-12-03
How about

```
$ cat test.txt 
this is line1
next line2
      
line3
-- Comment line

next line4
then line5
last ;

$ cat test.txt |sed '/^ *--/d'|sed '/^ *$/d'|sed ':a;N;$!ba;s/\n/ /g' 

this is line1 next line2 line3 next line4 then line5 last ;

```

---

### Post by tdyboc on 2011-12-03
Thanks for the replies.  I see that it works using multiple inline SEDs.  For the life of me I can't understand why I can't do that in one SED.  My original thought seemed straightforward enough to me.  Must have something to do with "greediness" on behalf of the reqex then.

---

### Post by McNils on 2011-12-06
This problem has been like a bad itch for me. I just had to find a solution with one sed expression. With this page [http://www.thegeekstuff.com/2009/12/unix-sed-tutorial-7-examples-for-sed-hold-and-pattern-buffer-operations/](http://www.thegeekstuff.com/2009/12/unix-sed-tutorial-7-examples-for-sed-hold-and-pattern-buffer-operations/) and the sed manpage I managed to put this together ;)

```
sed -n '/^--/d;H;1!x;s/\n/ /;h;${s/ \{1,\}/ /g;p}' test.txt
```

---

### Post by DaithiF on 2011-12-07
another variation:
```
$ sed -n '/^\s*$/d;/^\s*--/d;1h;1!H;${x;s/\n/ /g;p}' test
this is line1 next line2 line3 then line5 last ;
```

@tdyboc, the reason you had trouble doing this in one sed invocation once you added the lines to match & delete blank lines and lines beginning with -- was that your approach was to build up a single long pattern space by reading in & appending (N) the next lines.  Once you do that, your pattern space starts to look something like:

this is line1 next line2 line3 -- Comment line etc.

your delete expressions are trying to delete a pattern anchored at the beginning of a line (^) ... well since your line has become one big long one there is no such pattern.

Thats why McNils & my solutions use the 'hold' space as a staging area where the content you're keeping gets built up, and the pattern space is only used for the current line being examined.  That way a delete expression gets to do its thing on the current line, and only non-deleted content gets kept.  The last clause ${x;s/n/ /g;p} says at the last line of the file, swap back in the hold space contents, remove newlines and print.

hope this helps

---

