---
title: "awk help wanted"
date: 2009-04-01
forum: Programming Talk
---

### Post by knattlhuber on 2009-04-01
I have a large text file with a printout of study data that I need to convert into a comma-separated file. After running a series of sed commands, the file looks like this:

```
0003,20070830
4,33740,267.30,1 
4,610,250.00,1 
4,38120,20.00,0 

0005,20070831
4,37080,56.80,0 
4,1210,56.00,0 
4,16230,84.00,0 
4,1440,125.00,1 
4,29330,250.00,1 

0010,20070901
4,40660,70.00,0 
```

The first line of each block contains the 4-digit subject ID and the date, followed by 1 to 6 lines of data for the corresponding subject.
I would like to move the suject ID and the date in front of each line of a subject's data so that it looks like this:

```
0003,20070830,4,33740,267.30,1 
0003,20070830,4,610,250.00,1 
0003,20070830,4,38120,20.00,0 

0005,20070830,4,37080,56.80,0 
0005,20070830,4,1210,56.00,0 
0005,20070830,4,16230,84.00,0 
0005,20070830,4,1440,125.00,1 
0005,20070830,4,29330,250.00,1 

0010,20070830,4,40660,70.00,0 


```

I suspect awk would be the appropriate tool to do that?! Could somebody please tell me if that is feasible in awk and if so, maybe give me a hint on how to do that? You don't have to write the script for me, just pointing in the right direction would be much appreciated. I'm familiar with grep and sed but don't know much about awk (I've got an awk reference book though..). The file has 120,000+ lines, so doing it manually is not really an option ;-)
Thanks...

---

### Post by kpatz on 2009-04-01
This will do it:

```

 awk 'BEGIN {FS=","; OFS="," } !$3 { hdr1=$1; hdr2=$2 }; $3 { print hdr1, hdr2,$0 }; !$0' inputfile >outputfile

```

Here's the awk code broken out to make it clearer.

```

BEGIN {FS=","; OFS="," }
!$3 { hdr1=$1; hdr2=$2 }
$3 { print hdr1,hdr2,$0 }
!$0

```
The BEGIN line executes first, and sets FS (input field delimiter) and OFS (output field delimiter), to a comma.  By default awk treats whitespace as a field delimiter, but since your files are comma delimited, this line takes care of that little task.  You can also use the -F option to awk to set FS on the command line.

The second line executes whenever the 3rd field is blank (meaning you're on one of the header lines).  It stashes the two values $1 and $2 into hdr1 and hdr2.

The third line executes when the 3rd field is not blank (meaning one of the data lines).  It prints the two fields from the header followed by the input line.

The last line executes on a blank input line, and simply writes it to the output, so the breaks are retained in the output file.

Using your sample input, the output is:
```
0003,20070830,4,33740,267.30,1
0003,20070830,4,610,250.00,1
0003,20070830,4,38120,20.00,0

0005,20070831,4,37080,56.80,0
0005,20070831,4,1210,56.00,0
0005,20070831,4,16230,84.00,0
0005,20070831,4,1440,125.00,1
0005,20070831,4,29330,250.00,1

0010,20070901,4,40660,70.00,0

```

---

### Post by knattlhuber on 2009-04-01
AWESOME!!!!
Thank you so much for the solution and for the explanations!

---

