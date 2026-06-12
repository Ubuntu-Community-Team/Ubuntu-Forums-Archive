---
title: "Bash script - formating output"
date: 2012-12-09
forum: Programming Talk
---

### Post by matuskap on 2012-12-09
Hello, i have a little problem with correct formatting of my output in ubuntu. It is output from very large log file (100MB - 3GB). My problem is as follows:

Entry in log has from 8 up to xxx lines. First and last line carry always the same information but different parameters. I need to only show those entries(those multiple lines), that have specific parameters in last line. Entries are separated by "--" which is done by previous grep-ing 

Format sample:

--
First line of FIRST ENTRY (contains string "INSERT")
            DATA
                    DATA
                    DATA
            DATA
            DATA
                    DATA
                    DATA
            DATA
                    Last line of FIRST ENTRY (contains string "sample1")
--
First line of SECOND ENTRY (contains string "INSERT")
            DATA
                    DATA
                    DATA
            DATA
            DATA
                    DATA
                    DATA
            DATA
                    Last line of SECOND ENTRY (contains string "sample2")
--
First line of THIRD ENTRY (contains string "INSERT")
            DATA
                    DATA
                    DATA
            DATA
            DATA
                    DATA
                    DATA
            DATA
                    Last line of THIRD ENTRY (contains string "sample1")


In this partial output, only entries FIRST and THIRD contain desired string in last line so those are the only ones i need. Therefore i need to only output those two. Problem is, that in the first line parameters are variable and unpredictable. The first line contains time stamp, session info and so on, which cant be foretold although first line always contains string "INSERT" at the very beginning of line (INSERT,next parameter,next parameter,...).

So right now i have script that returns above described output, and i need to add another pipe and only print specific entries as described above. 

Something like: print lines from string "sample1" upwards up to first occurrence of string "INSERT".

Can anyone help me with this one?

---

### Post by matuskap on 2012-12-09
OK i have found a way :) 
I delete all end lines with tr, then i replace all INSERT with end lines with sed. Now i can grep all relecant data that belongs to specific desired parameter. After im done i just replace all white spaces with end lines to make it readable again. It probably isnt the most ideal way to do this but it works pretty well :).

---

### Post by steeldriver on 2012-12-09
Well you might have been able to do it with a variant of this sed one liner:

**58. Print a paragraph that contains "AAA". (Paragraphs are separated by blank lines).**
 ```
sed -e '/./{H;$!d;}' -e 'x;/AAA/!d;'
```Instead of blank lines your input 'paragraphs' are separated by lines beginning with hyphens; so something like

```
 sed -e '/^[^-]/{H;$!d;}' -e 'x;/sample1/!d' *yourfile*
```[basically it keeps appending lines into the hold space until it encounters a line starting with a '-'; then it swaps the hold space into pattern space and prints it if it contains 'sample1']

Reference here: [http://www.catonmat.net/blog/sed-one-liners-explained-part-two/](http://www.catonmat.net/blog/sed-one-liners-explained-part-two/)

---

### Post by Vaphell on 2012-12-09
maybe something like this
```
awk 'BEGIN { RS="\n?--\n"; FS="\n"; }
     $NF ~ /"sample1"/ { print $0; }'
```
RecordSeparator set to -- + newlines, FieldSeparator set to newline => whole block is a single record and its lines are fields.
test last field (line in block) for "sample1" and print the whole record if it matches.

---

