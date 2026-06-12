---
title: "Is good bash scripting knowledge considered as a &quot;must have&quot; for system admin?"
date: 2013-06-25
forum: Programming Talk
---

### Post by pmu on 2013-06-25
Hi,

I have been playing with bash for a few days now. Must say its fun :)

However, today, with so many alternatives available such as Ruby/Python etc, does knowing bash still help?

Also, from the job point of view, does it help to know bash scripting well? 

Or is it something that I am supposed to be well versed with anyways? In other words, is bash scripting considered an added advantage or a must have?

---

### Post by SeijiSensei on 2013-06-25
I'd say learning bash is a pretty important tool for system administrators.  I've written a lot of bash scripts over the years to handle specific admin tasks.   

Languages like PHP or Perl are useful for tasks like parsing logs.  They can also come in handy when you need to have the script interact with other services like an SQL database where you can take advantage of the built-in functions to simplify the task.

However a lot of scripting just consists of putting a bunch of shell commands together in a useful way.  I run bash scripts for tasks like managing backups with rsync, constructing and applying iptables rulesets, or checking to make sure none of the critical daemons on my servers have died.  Sometimes I'll write a "wrapper" script in bash that gathers some data, puts them in environment variables, then invokes a PHP or Perl script to read those variables and proceed accordingly.  

Give yourself a simple task to start with like nightly backups.  It's usually much easier to learn a language in the context of trying to solve a problem than learning it in the abstract.

---

### Post by ofnuts on 2013-06-25
It doesn't help getting the job(*),  but if you don't and can't learn it fast, you are dead:)

(*) Nobody will ask if you apply for a sysadmin job... but when you buy an ornamental fish, the merchant doesn't ask if you have a fish tank either. There are things that are somewhat implicit.

---

### Post by CharlesA on 2013-06-25
> **SeijiSensei said:**
> I'd say learning bash is a pretty important tool for system administrators.  I've written a lot of bash scripts over the years to handle specific admin tasks.   

Languages like PHP or Perl are useful for tasks like parsing logs.  They can also come in handy when you need to have the script interact with other services like an SQL database where you can take advantage of the built-in functions to simplify the task.

However a lot of scripting just consists of putting a bunch of shell commands together in a useful way.  I run bash scripts for tasks like managing backups with rsync, constructing and applying iptables rulesets, or checking to make sure none of the critical daemons on my servers have died.  Sometimes I'll write a "wrapper" script in bash that gathers some data, puts them in environment variables, then invokes a PHP or Perl script to read those variables and proceed accordingly.  

Give yourself a simple task to start with like nightly backups.  It's usually much easier to learn a language in the context of trying to solve a problem than learning it in the abstract.

Good example.

It might not be super necessary, but it is a good thing to know. I have written BASH scripts to do mysqldumps and backups off a wiki server at work so I have the data if the VM they are on hoses itself. I have also written scripts for my home server and VPS and it really is a good thing to have.

---

### Post by Vaphell on 2013-06-25
bash is very useful. If you need to slap few commands together for a quick and dirty solution or manage few files or automatically transform some text on a level that doesn't require perl power, bash and a handful of cli tools are plenty fine. Yes you can write more or less the same thing in python or other general purpose language and call the same cli tools if you have to but their generality comes at a price - you need to write a bit of boilerplate code just to get the features that bash tailored for its use case scenarios offers for free.
**for f in *** to iterate over all files? you can't beat that and if that's exactly what you need to do, bash is leaps and bounds above everything else.

---

### Post by drmrgd on 2013-06-25
Being nimble in bash (or equivalent shell) when using a Linux is about as helpful as being nimble with a mouse when using Linux!  As Vaphell said, things that take full scripts to do can be done very quickly with a simple bash one-liner.  

Here's a real world example (maybe more informatics than sys administration) of something I've used a bunch recently (maybe there's a quicker way to do it, but this works like a champ for me).  I wanted to find all files in a directory that don't contain a particular string and list them.  I know I can use grep to find strings, and grep -v will print all lines that don't match (not quite what I want).  However, with a little shell magic, I can search for files that don't contain a string of interest:

```
for f in *; do grep -q -iE 'TP53_ENST[0-9]+' $f && continue || printf "String not found in $f\n"; done
```

That will iterate through every file in the current directory, using grep to quietly find the string "TP53_ENST" followed by any number of digits, and if it finds the string the file, the loop will skip to the next iteration (i.e. file), and if it does not find the string, it will print "String not found in <file>":

```
String not found in 170_genelist.062413.txt
String not found in counts_noENST.txt
String not found in genesVars.pl
String not found in lookup.pl
String not found in old
String not found in variants_noENST_170_genelist.csv
```

Or this one-liner I just used an hour ago to compare a two column list (the "final result") with another list (the original query) to quickly show which elements were missing:

```
cat counts.txt | while read line; do gene=($(echo $line | sed 's/\t+//g')); grep ${gene[0]} 170_genelist.062413.txt && continue || printf "Not found: ${gene[0]}\n"; done
```

If you plan to use Linux, definitely learn bash to make your life easier.  The above tricks can be used to do all kinds of things.

---

### Post by Vaphell on 2013-06-25
> Or this one-liner I just used an hour ago to compare a two column list (the "final result") with another list (the original query) to quickly show which elements were missing:
```

cat counts.txt | while read line; do gene=($(echo $line | sed 's/\t+//g')); grep ${gene[0]} 170_genelist.062413.txt && continue || printf "Not found: ${gene[0]}\n"; done

```

yup, that's the quick and dirty kind of bashing ;-)
unnecessary use of cat
unnecessary continue, || part wont execute either way
shoddy part with array and sed 
- sed does nothing because there are no tabs due to unquoted $line
- is this supposed to be 'at least one \t' or '\t','+'? if it's the former then sed needs -r
- given the above i am not sure what that array is supposed to do :-)

unless i am reading the intent wrong, this would be much nicer
```
while read gene _; do grep $gene 170_genelist.062413.txt || echo "not found: $gene"; done < counts.txt
```
or something utilizing **grep -v -f** where file(s) can be substituted/faked with **<( cmd extracting proper column from file )**

---

### Post by tgalati4 on 2013-06-25
Think of bash as another tool in your toolbox.  If you know how to use it, it will make your life easier when you confront a problem.  Go through some of the advanced bash scripting tutorials (search the web) and you will see the power of knowing bash.

---

### Post by prodigy_ on 2013-06-25
Bash is pretty easy to learn. And even easier to debug. Simply adding **set -x** yields you a complete trace log of your script. I don't think anything in any other language beats that (especially for a newbie).

---

### Post by drmrgd on 2013-06-26
> **Vaphell said:**
> yup, that's the quick and dirty kind of bashing ;-)
unnecessary use of cat
unnecessary continue, || part wont execute either way
shoddy part with array and sed 
- sed does nothing because there are no tabs due to unquoted $line
- is this supposed to be 'at least one \t' or '\t','+'? if it's the former then sed needs -r
- given the above i am not sure what that array is supposed to do :-)

unless i am reading the intent wrong, this would be much nicer
```
while read gene _; do grep $gene 170_genelist.062413.txt || echo "not found: $gene"; done < counts.txt
```
or something utilizing **grep -v -f** where file(s) can be substituted/faked with **<( cmd extracting proper column from file )**


Heh!  I knew Vaphell would have a much better suggestions; I'm still pretty new myself!  What I was trying to do was to compare two files.  The first, counts.txt, is a two column table of gene names and the number of entries associated with them from something I extracted from a massive table.  The second is the original lookup table with just a column of gene names I used to generate the counts.txt file.  My goal was a quick (and apparently more dirty than I thought) way to do a spot check to make sure I got results for every gene in the 170_genelist file.  

My strategy was to split the counts file into a bash array so that ${gene[0]} held the gene name, and ${gene[1]} held the number of times I was found (in other iterations I actually used that data, which is part of the reason why I split it into an array), so that I could do a reverse lookup of the 170_genelist file.  If the current query was found (based on the exit code of the grep query), the loop should skip to the next item in ${gene[0]}, otherwise it should print that the gene was not found in the file.  In my hands it seemed like the 'grep -q <query> && continue || <report something>' worked, but maybe I'm over looking something.

With regard to the cat call, I didn't know how to load a file into read.  Cat didn't seem right there, but I didn't know a better way.  That's for pointing out how it should be done!

With regard to the sed statement, you're right, and I forgot to quote the variable, when I re-typed this.  Also, I did want sed to split the line on a tab, and mistakenly wrote the '\t+' here.  I think that should have just been '\t' (I think I was originally splitting with a Perl one-liner and using "\s+" to cover my bases...maybe not any better).  

Thanks as usual for the tips and help Vaphell!

---

### Post by drmrgd on 2013-06-26
OK, after doing some more reading, it looks like I could simplify what I wrote greatly as 'read' has a '-a' option to split lines into array elements based on the IFS variable.  IFS always seems to trip me up, but this seems to work much better.  Also, now that I'm at my work computer, here is the original way (with the improved array building method) that I tried to use that statement, trying to match the number of times a gene was seen in a huge file with the number of counts I have in a table from another source (table reads like "Gene    Counts"):

```
while read -a look; do printf "${look[0]}\t${look[1]}\t"; grep -c -E "^${look[0]}," variants_ENST_170_genelist.csv; done < counts_noENST.txt
```

Here's what I think the oneliner I posted here should have been:

```
while read -a look; do grep -q "${look[0]}" 170_genelist.062413.txt && continue || echo "Not Found: ${look[0]}" ; done < counts_noENST.txt
```

Better?

Anyway, to the OP, learn bash...it's pretty easy, fun, and very, very useful!

---

### Post by CharlesA on 2013-06-26
drmrgd, you'd probably be surprised how badly hacked together some of my bash scripts are. :)

Rewriting a working script can be a bit... time consuming.

---

### Post by Vaphell on 2013-06-26
> **drmrgd said:**
> OK, after doing some more reading, it looks like I could simplify what I wrote greatly as 'read' has a '-a' option to split lines into array elements based on the IFS variable.  IFS always seems to trip me up, but this seems to work much better.
Better?

yes, read -a was my next idea but seeing that only [0] was needed i opted for *read var throwaway_var*
IFS does splitting at [ \t]+ just fine so reading columns is for free (though it would be a pain to read tab delimited data set if null values were to be preserved)

> With regard to the cat call, I didn't know how to load a file into read. Cat didn't seem right there, but I didn't know a better way. That's for pointing out how it should be done!

```
while read; do ...; done < file
while read; do ...; done < <( command )   # space between < <
while read; do ...; done <<< "string"
```
**<( command )** is a file for all intents and purposes, so any time you see 'file name' in --help of some command, you can use this.
eg grep -f can take a list of words from a given file 
```
grep -v** -f <( awk '{ print $1 }' file1.txt )** file2.txt
```
this should find lines of file2 that are not matched by any word from the first column of file1

---

### Post by pmu on 2013-06-26
Whoa,

Thank you all very much for your replies. 

I am super convinced that bash indeed will help.

On to it now.

Thank you very much everyone. This is why Ubuntu rocks. It has amazing community and forum members.

Awesome.

---

### Post by drmrgd on 2013-06-26
> **CharlesA said:**
> drmrgd, you'd probably be surprised how badly hacked together some of my bash scripts are. :)

Rewriting a working script can be a bit... time consuming.

No doubt!  And being OCD doesn't make matters any better.  I guess in the end if you got the answer you needed, even if the script is a bit ugly or not as eloquent as it could be, it's good enough.

> 
```
[COLOR=#000000]
while read; do ...; done < file
while read; do ...; done < <( command )   # space between < <
while read; do ...; done <<< "string"[/COLOR]

```[B]
<( command ) is a file for all intents and purposes, so any time you see 'file name' in --help of some command, you can use this.
eg grep -f can take a list of words from a given file[/B]

Thanks again for clarification and education.  You've really, really simplified this for me very nicely and helped to make some better scripts!

---

