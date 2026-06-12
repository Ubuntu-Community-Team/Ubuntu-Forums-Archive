---
title: "Sorting a list by two variables"
date: 2013-12-03
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-12-03
Hi Guys,

I have a script (that I did not write) that sorts tasks by priority.
Each task can have a priority rating of A - E or none.
The name of the text file that is being sorted is todo.txt

The script is below:

```

#!/bin/bash
$HOME/scripts/todo.sh -p ls | awk 'BEGIN{
HEADING="${color grey}\n";A="${color yellow}";B="${color 6892C6}";C="${color green}";D="${color grey}";N="${color white}"
}
{if ($2~/\(A\)/) PRI_A=PRI_A $0"\n"}
{if ($2~/\(B\)/) PRI_B=PRI_B $0"\n"}
{if ($2~/\(C\)/) PRI_C=PRI_C $0"\n"}
{if ($2~/\([D-Z]\)/) PRI_D=PRI_D $0"\n"}
{if ($2!~/\([A-Z]\)/&&$1!~/(--|TODO:)/) NOPRI=NOPRI $0"\n"}
END{
{if (PRI_A!~/^$/) {OUTPUT=HEADING A PRI_A;HEADING=""}}
{if (PRI_B!~/^$/) {OUTPUT=OUTPUT HEADING B PRI_B;HEADING=""}}
{if (PRI_C!~/^$/) {OUTPUT=OUTPUT HEADING C PRI_C;HEADING=""}}
{if (PRI_D!~/^$/) {OUTPUT=OUTPUT HEADING D PRI_D;HEADING=""}}
{if (NOPRI!~/^$/) {OUTPUT=OUTPUT HEADING N NOPRI}}
{if (OUTPUT!~/^$/) printf OUTPUT}
}'

```

Here is an example of the todo.txt file _prior_ to being sorted:
```

(B) A Task Due:2013-12-09
(B) Another task Due 2013-12-20
(D) Put out Christmas presents Due:2013-12-24
(A) Due some stuff Due:2013-12-03
(A) More stuff but not as important Due 2014-1-3
(B) Do this today Due:2013-12-03
(A) Do this tomorrow Due:2013-12-04

```

The script above does a good job of sorting all the A tasks first followed by the B tasks and then the C tasks and so on.

My question is, how could I sort the tasks by due date  and then priority level (A-E) so the tasks due soonest with priority A come before a task due the same day with priority B?

Example:
```

(A) Due some stuff Due:2013-12-03
(A) Do this tomorrow Due:2013-12-04
(A) More stuff but not as important Due 2014-1-3
(B) Do this today Due:2013-12-03
(B) A Task Due:2013-12-09
(B) Another task Due 2013-12-20
(D) Put out Christmas presents Due:2013-12-24

```
I appreciate the help!

---

### Post by ofnuts on 2013-12-03
You have to transform the file so that the due date is in an identifiable column... then sort on two columns, then restore the original format.

---

### Post by r-senior on 2013-12-03
It's pretty ugly and fragile, and it does modify the data, but ...

```
 sed -e 's/Due:/Due /' todo.txt | awk '{split($NF, d, "-"); printf "%4d-%02d-%02d\t%s\n", d[1], d[2], d[3], $0}' | sort | cut -f2-
```

Breaking it down:

1. Sed tidies up the mixture of Due with colon and Due without colon, but more importantly makes a space before the date
```
 $ sed -e 's/Due:/Due /' todo.txt
(A) Due some stuff Due 2013-12-03
(A) Do this tomorrow Due 2013-12-04
(A) More stuff but not as important Due 2014-1-3
(B) Do this today Due 2013-12-03
(B) A Task Due 2013-12-09
(B) Another task Due 2013-12-20
(D) Put out Christmas presents Due 2013-12-24
```

2. Awk splits the date in the last field (NF) into an array 'd' and reformats the month and day with leading zeroes, printing it at the front of the row. There is a reason for the tab (\t).

```
 $ sed -e 's/Due:/Due /' todo.txt | awk '{split($NF, d, "-"); printf "%4d-%02d-%02d\t%s\n", d[1], d[2], d[3], $0}'
2013-12-03    (A) Due some stuff Due 2013-12-03
2013-12-04    (A) Do this tomorrow Due 2013-12-04
2014-01-03    (A) More stuff but not as important Due 2014-1-3
2013-12-03    (B) Do this today Due 2013-12-03
2013-12-09    (B) A Task Due 2013-12-09
2013-12-20    (B) Another task Due 2013-12-20
2013-12-24    (D) Put out Christmas presents Due 2013-12-24

```

3. It's easy now, just sort it

```
 $ sed -e 's/Due:/Due /' todo.txt | awk '{split($NF, d, "-"); printf "%4d-%02d-%02d\t%s\n", d[1], d[2], d[3], $0}' | sort
2013-12-03     (A) Due some stuff Due 2013-12-03
2013-12-03     (B) Do this today Due 2013-12-03
2013-12-04     (A) Do this tomorrow Due 2013-12-04
2013-12-09     (B) A Task Due 2013-12-09
2013-12-20     (B) Another task Due 2013-12-20
2013-12-24     (D) Put out Christmas presents Due 2013-12-24
2014-01-03     (A) More stuff but not as important Due 2014-1-3

```

4. Cut chops the formatted date off the front of the line by printing field 2 to the EOL. Default delimiter for cut is tab, hence the tab.

```
 $ sed -e 's/Due:/Due /' todo.txt | awk '{split($NF, d, "-"); printf "%4d-%02d-%02d\t%s\n", d[1], d[2], d[3], $0}' | sort | cut -f2-
(A) Due some stuff Due 2013-12-03
(B) Do this today Due 2013-12-03
(A) Do this tomorrow Due 2013-12-04
(B) A Task Due 2013-12-09
(B) Another task Due 2013-12-20
(D) Put out Christmas presents Due 2013-12-24
(A) More stuff but not as important Due 2014-1-3
```

It should go without saying that this data file is a very fragile format that doesn't really lend itself to automated processing.

---

### Post by GrouchyGaijin on 2013-12-04
Thank you!

I realized when I read your reply that I had a typo in my example list.
Due some stuff should be Do some stuff.

Would it make it easier if I gave every task a priority and a due date? 

```
Due:yyyy-mm-dd
```

After looking at your solution I realized it would be better (and maybe easier to program?), if the tasks were sorted first by priority then by due date.
So that all of the (A) tasks come first with the one due soonest at the top and one due latest at the bottom, followed by the (B) tasks with the one due soonest at the top and one due latest at the bottom, then the (C) (D) (E) tasks the same way.

Sorry to be so flaky, I should have thought this through better

---

### Post by r-senior on 2013-12-04
The easiest format would be that shown in step 2 but without the date at the end:

```
2013-12-03 (A) Do some stuff 
2013-12-04 (A) Do this tomorrow 
2014-01-03 (A) More stuff but not as important 
2013-12-03 (B) Do this today 
2013-12-09 (B) A Task 
2013-12-20 (B) Another task 
2013-12-24 (D) Put out Christmas presents
```

If you want to sort by date then priority, you just sort it

```
sort todo.txt
```

If you want to sort by priority only, you just sort it by that key

```
sort -k2 todo.txt
```

In Sweden, you have a locale date format that lends itself to this. ;)

---

### Post by GrouchyGaijin on 2013-12-04
Thanks man!!

---

