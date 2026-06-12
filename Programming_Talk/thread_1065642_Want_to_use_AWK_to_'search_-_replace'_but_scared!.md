---
title: "Want to use AWK to 'search - replace' but scared!"
date: 2009-02-10
forum: Programming Talk
---

### Post by theDaveTheRave on 2009-02-10
hi all,

I have a question regarding <awk> file maniputlation.

I have a file that I need to "adjust"

here is the first line of the file

> 
a	gi|170295850|ref|NM_018764.2|	100	14	0	0	1	14	5068	5055	1.4	28.2	


As can be seen it contains a combination of field separators, bot the '|' and a '\t' (tab) character.

I am wanting to import this into a MySQL table, but to make my life easier I would like to change either the tab's to bars (or vice versa).

for now I can happily open up a text editor and do a <search - replace> as the current "experminental" file is only 10 lines long.

but in the future it could be upto 900,000 lines! obviously the change will still work with this, but I would like a more "elegant" solution.

so I figure i could programe this in Java (but it would take a while for me to get it to work) and I'm sure that I can do it in the bash terminal! 

Quick investigations have lead me to awk programing, so I seem to be correct.

But I'm not convinced I understand the syntax so here is what I plan to do, at the command line

myOutputFile.txt < awk 'begin { gsub (/\\t/, '\|'); print} myInputFile.txt'

am I correct in thinking this will take the <myInputfile.txt> perform the substitution of tabs to bar delimiter and will send the result to my new file <myOutputfile.txt>??

I guess that I could just try it, but I don't fancy to bugger up my file!

thanks in advance.

David

---

### Post by ajackson on 2009-02-10
> **theDaveTheRave said:**
> I guess that I could just try it, but I don't fancy to bugger up my file!
I'm no good at AWK so can't help with the specifics but why not create a copy of the file for testing purposes, if it gets screwed just recopy the original and try again.

---

### Post by geirha on 2009-02-10
Close, but not quite. Try with
```
awk '{gsub (/\t/,"|"); print}' myInputFile.txt >myOutputFile.txt
```
myInputFile.txt will not be touched. If you're paranoid, you can always make the file read-only. Then you'll know for certain that it has not been altered
```
chmod -w myInputFile.txt
```
(replacing -w with +w will make it writable again)

---

### Post by theDaveTheRave on 2009-02-10
ajackson and geirha

thanks to both for the suggestions.

I must admit that after i posted the call for some assistance I thought to myself 

"I could just make a copy"

geirha,

I like your idea of making the file read only, I'll do that definately.

and I'm pleased that I am as close as I was, this is my first "trip" into playing with AWK, and I suspect that this is the only sort of simple task I will ever want to do.

a question, whilst you are both around...

do you think that there is a size limit on these types of functions?

I have another table / file that I import into MySQL that contains over 4 million records, although I probably don't want to play around using AWK on it - I may need to at some point!

thanks for the help so far.

David

---

### Post by theDaveTheRave on 2009-02-10
geirha

You are one superstar.

I owe you a major sized drink.

it works a treat.

David

---

### Post by theDaveTheRave on 2009-02-10
OK I know it is getting silly now but....

can I call these sort of functions from a java programe?

either to run them on the local machine (if it is runing linux/ unix) or run awk on the server (if I determine that the user isn't running linux/unix)?

thanks in advance.

in fact I'm going to have a quick look in the java.doc

David.

---

### Post by ghostdog74 on 2009-02-10
awk treats tabs and spaces the same. therefore you just need to change the OFS (Output Field separator) variable.
```

# awk '{$1=$1}1' OFS="|" file
a|gi|170295850|ref|NM_018764.2||100|14|0|0|1|14|5068|5055|1.4|28.2


```

---

### Post by theDaveTheRave on 2009-02-11
> **ghostdog74 said:**
> awk treats tabs and spaces the same. therefore you just need to change the OFS (Output Field separator) variable.
```

# awk '{$1=$1}1' OFS="|" file
a|gi|170295850|ref|NM_018764.2||100|14|0|0|1|14|5068|5055|1.4|28.2


```

ERR !!! this is where i loose the plot with AWK so much of the time, and the reason for my original post (before trying the code).

can you help me understand??

I assume the  < $1=$1 > is some sort of user variable handiling??
and I assume the line
[quote]a|gi|170295850|ref|NM_018764.2||100|14|0|0|1|14|5068|5055|1.4|28.2[/quote
is the expected output??

I must admit that I am writting help files and stuff for my team, and I am being much more "verbose" in the explanations of the variables etc.

thanks for the help

David

---

### Post by ghostdog74 on 2009-02-11
$1=$1 means to "reformat". Please refer to [Effective Awk](http://www.gnu.org/software/gawk/manual/). If you read it, you will come across an explanation of what it means.

---

### Post by theDaveTheRave on 2009-02-11
Thanks I've tagged the page.

i don't know if i have time to go all the way through it thoug!

David

---

### Post by The Cog on 2009-02-11
How about (changing | to <tab>):
**cat inputFile | tr '|' '\t' > outputFile**
or
**tr '|' '\t' < inputFile > outputFile**
or 
**cat inputFile | sed 's/|/\t/g' > outputFile**
or
**sed 's/|/\t/g' > outputFile < inputFile > outputFile**

---

### Post by theDaveTheRave on 2009-02-12
> **The Cog said:**
> How about (changing | to <tab>):


I did try this one as well, but the nature of the position of the tabs meant that I had 2 tab spaces after one another. Then whilst using the MySQL <load data infile...> command I found that I had "seen" one tab space when in fact there was 2!

Which was temporarily confusing!

so now I have just changed my default... find tabs and change them to a "tab then a |" made it easier to count the actual true number of column.

Again this is all due to the NCBI sending the file to a combined "tab spaced" and "bar delimited" file!

I guess the part that is "bar delimited" is actually an <enum> data type in the original database??

Who knows... who cares (well actually maybe I do!) but I know that with AWK I can alter the file to a more consistent method for delimiting.

David

---

