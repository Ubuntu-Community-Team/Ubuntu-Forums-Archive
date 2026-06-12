---
title: "sed align in columns upper case insert new column"
date: 2010-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Paul S on 2010-06-16
I've been searching for this specific sed howto and decided to post the results here to make it easier for someone in the future.

I'm starting with a file that has two columns that are not aligned and want to add a third column, change words to caps and get the columns aligned:

this is my start.txt:
 
zones                         z ow n z
zoning                                   z ow n ih ng
zoo                     z uw
__str__                       ah n d er s k ao r d s t r
what_can_i_say           w ah t k ae n ay s ey

this is what I want it to look like (note that the normal web page html shows these columns misaligned, but if you copy tham to a local text, you'll see they're aligned:
 
ZONES                   [ZONES]                 z ow n z
ZONING                  [ZONING]                z ow n ih ng
ZOO                     [ZOO]                   z uw
__STR__                 [__STR__]               ah n d er s k ao r d s t r
WHAT_CAN_I_SAY          [WHAT_CAN_I_SAY]        w ah t k ae n ay s ey

here's the sed / expand statement that works:

cat start.txt | sed -e 's/\(^[^ ]*\) *\([^ ].*$\)/\U\1\t[\1]\E\t\2/g' | expand -t 24 > done.txt

here's the actions taken by the various parts of the sed statement, check the documentation for more info:
1.  \(\) saves to 1 stuff between them
2.  ^ line beginning 
3.  [^ ] not a space * repeated 0 or more times
4.  * <space char> repeated 0 or more
5.  \(\) saves to 2 stuff between
6.  [^ ] not a space
7. . any char * repeated 0 or more $ to end of line
8.  \U start output in upper case   (if you had wanted lowercase, you'd use \L)
9.  \1 print first saved \(\)
10.  \t print tab
11.  [ print left bracket char
12.  \1 print first saved \(\)
13.  ] left bracket char
14.  \E end upper case
15. \t print tab
16.  \2 print 2nd saved \(\)
17.  expand replaces tabs with spaces and "-t 24" pads at tab width of 24 

hth others looking for a similar sed

---

