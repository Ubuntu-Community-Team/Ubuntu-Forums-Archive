---
title: "gAWK: record separator bugged?"
date: 2012-03-28
forum: Programming Talk
---

### Post by GerritHiemstra on 2012-03-28
Hello,

i was wondering if anyone has an explanation for a problem i ran into with AWK...

I will use the following simple awk script to explain myself:

```
BEGIN{RS=""}
END{print "num_rows: " NR}
```I assumed that by using an empty record separator, AWK would consider all incoming fields to be on 1 record. 

Using the following example text, all seems good:

> 
<abc>
<def>
</def>
</abc>
**Output**: num_rows: 1

However, using the following text (containing a situation where there's 2 or more newline characters in a row):


> 
<abc>
<def>



</def>
</abc>
**Output: **num_rows: 2

How could it be?

Do i have my definitions wrong? (what precisely IS a record separator?)

Many thanks in advance!

---

### Post by r-senior on 2012-03-28
The manual page for gawk explains "Records":

```
 Records
       Normally, records are separated by newline characters.  You can control
       how records are separated by assigning values to the built-in  variable
       RS.   If  RS is any single character, that character separates records.
       Otherwise, RS is a regular expression.  Text in the input that  matches
       this  regular expression separates the record.  However, in compatibil&#8208;
       ity mode, only the first character of its string value is used for sep&#8208;
       arating  records.   [B]If  RS  is set to the null string, then records are
       separated by blank lines.[/B]  When RS is set to the null string, the  new&#8208;
       line  character  always acts as a field separator, in addition to what&#8208;
       ever value FS may have.

```

Use 'man gawk' for further information.

---

### Post by GerritHiemstra on 2012-03-28
Thank you sir!

---

### Post by GerritHiemstra on 2012-03-28
Hollld up, i was a bit too quick in that one...

If i use 10 consecutive blank lines in my example text, the output is still "num_rows: 2" :confused:

---

### Post by r-senior on 2012-03-28
It means the separator is one or more blank lines, not that each record is separated by a single blank line. The man page is slightly ambiguous, I'd agree, but the complete manual is quite clear:

[http://www.gnu.org/software/gawk/manual/html_node/Multiple-Line.html](http://www.gnu.org/software/gawk/manual/html_node/Multiple-Line.html)

---

### Post by GerritHiemstra on 2012-03-29
Thanks!

My xml pretty print script is working again; i used "/a" as record separator, as I need the text to be read on one record :p

---

