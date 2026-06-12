---
title: "Cut text between 2 delimiters and paste in the previous line provided..."
date: 2012-07-06
forum: Programming Talk
---

### Post by hihihi100 on 2012-07-06
Cut text between 2 delimiters and paste in the previous line provided that the text before the first delimiter is the same:

I dont even know if bash or sed are up for the thing, or is it that I must create a script, which by now is out of my capabilities

Hello:

Sample of plain text edited with geany, its for a goldendict file:

Mêdog county, Tibetan: Me tog rdzong, in Nyingchi prefecture &#26519;&#33437;&#22320;&#21312; [Lin2 zhi1 di4 qu1], Tibet»	&#22696;&#33067; [Mo4 tuo1]$
Mêdog county, Tibetan: Me tog rdzong, in Nyingchi prefecture &#26519;&#33437;&#22320;&#21312; [Lin2 zhi1 di4 qu1], Tibet»	&#22696;&#33067;&#32291; [Mo4 tuo1 xian4]$

I need to edit those 2 lines to:

Mêdog county, Tibetan: Me tog rdzong, in Nyingchi prefecture &#26519;&#33437;&#22320;&#21312; [Lin2 zhi1 di4 qu1], Tibet»	&#22696;&#33067; [Mo4 tuo1], &#22696;&#33067;&#32291; [Mo4 tuo1 xian4]$

for an unknown number of lines, presumed to be in the 8,000-10,000 range

Rule: cut text in between delimiters »	(there is a tab) and $ for each line that repeats the text before delimiter »TAB (thats between beginning of line and delimiter »TAB) and paste selected text to the end of the first line, if possible, before the final $ of each line and at the same time, getting rid of the redundant text (between beginning of line and »TAB)

Most of the lines are paired, some are not. is this relevant?

I've been told awk would do the thing. If so, at least tell me what options should I look for

---

### Post by e36freak on 2012-07-06
I answered this in #awk on freenode, but I'll put it here as well in case someone else has a similar problem...

```

awk -F '»' '{sub(/\$$/, ""); v[$1,++c[$1]]=$2} END {for (s in c) {printf("%s»", s); for (i=1; i<=c[s]; i++) printf("%s%s", v[s,i], i==c[s] ? "$\n" : ",")}}' file

```Put in a script:
```

#!/usr/bin/awk -f
BEGIN {
  FS = "»";
}

{
  # remove the '$' from the end of the line
  sub(/\$$/, "");

  # store in matrix, mapping the second field to the first. this way, lines with
  # the same first field will be grouped together
  vals[$1,++counts[$1]] = $2;
}

# after all input is read...
END {
  # loop over each unique first field
  for (str in counts) {
    # print the first field, followed by the delimiter
    printf("%s%s", str, FS);

    # loop over each second field mapped to the first
    for (i=1; i<=counts[str]; i++) {
      # print each second field. if it's the last one mapped to the first, use
      # a "$" and newline at the end. otherwise, use a comma
      printf("%s%s", vals[str,i], (i == counts[str]) ? "$\n" : ",");
    }
  }
}

```This has the advantage of being able to deal with non-sequential pairings, and up to N lines with the same first field. The only real drawback is that it has to store all of the data in memory.

Another option, if storing in memory is an issue, is to instead use a one-line buffer. This next solution DOES, however, require lines to be joined to be sequential.

```

#!/usr/bin/awk -f

BEGIN {
  FS = "»";
}
 
# remove the "$" from the end of each line
{
  sub(/\$$/, "");
}

# treat the first line of the file differently
NR == 1 {
  # print the line, but without a newline at the end
  printf("%s", $0);

  # store the first field in "prev" so the next line can be compared to it
  prev = $1;

  # skip to the next line of input
  next;
}

{
  # if the first field is the same as the previous line's...
  if ($1 == prev) {
    # print a comma, and the second field
    printf(",%s", $2);

  # first field is new
  } else {
    # finish the previous line with a "$" and a newline, and print the whole
    # line, but without a newline
    printf("$\n%s", $0);
  }

  # store the first field in "prev" so the next line can be compared to it
  prev = $1;
}

# print the final '$\n' for the last line
END {
  printf("$\n");
}


```Written as a one-liner:
```

awk -F '»' '{sub(/\$$/, "")} NR==1 {printf("%s", $0); p=$1; next} {if ($1 == p) printf(",%s", $2); else printf("$\n%s", $0); p=$1} END {print "$"}' file

```

---

### Post by hihihi100 on 2012-07-06
There's more:

For a sample line: 

&#40845;&#39706;&#33756;	»[long2 xu1 cai4] asparagus, (Taiwan) young shoots of the chayote vine &#20315;&#25163;&#29916;	»[fo2 shou3 gua1]$

I need to change the second "TAB»" to a ",space" so it reads:

&#40845;&#39706;&#33756;	»[long2 xu1 cai4] asparagus, (Taiwan) young shoots of the chayote vine &#20315;&#25163;&#29916;, [fo2 shou3 gua1]$

Rule: dont touch the first TAB», but for the second, make it into a ",space"

---

### Post by Vaphell on 2012-07-06
```
awk -F$'\t»' '{ printf("%s\t»%s, %s\n", $1, $2, $3 ) }' file
```

test:
```
$ echo $'&#40845;&#39706;&#33756;\t»[long2 xu1 cai4] asparagus, (Taiwan) young shoots of the chayote vine &#20315;&#25163;&#29916;\t»[fo2 shou3 gua1]$' | awk -F$'\t»' '{ printf("%s\t»%s, %s\n", $1, $2, $3 ) }'
&#40845;&#39706;&#33756;	»[long2 xu1 cai4] asparagus, (Taiwan) young shoots of the chayote vine &#20315;&#25163;&#29916;, [fo2 shou3 gua1]$
```

---

### Post by hihihi100 on 2012-07-09
Thanks for the previous answers:

I still need to edit another glossary of 95,000 entries to get rid of redundant tabs. For each of the lines I must have the first one, but remove any other one and transform it to ",space":

For a sample line:


Namling county, Tibetan: Rnam gling rdzong, in Shigatse prefecture, Tibet	&#21335;&#26408;&#26519; [Nan2 mu4 lin2],	&#21335;&#26408;&#26519;&#32291; [Nan2 mu4 lin2 xian4]$

that includes 2 tabs:


Namling county, Tibetan: Rnam gling rdzong, in Shigatse prefecture, Tibet	<--TAB&#21335;&#26408;&#26519; [Nan2 mu4 lin2],	<--TAB&#21335;&#26408;&#26519;&#32291; [Nan2 mu4 lin2 xian4]$

I need to obtain:


Namling county, Tibetan: Rnam gling rdzong, in Shigatse prefecture, Tibet	<--TAB&#21335;&#26408;&#26519; [Nan2 mu4 lin2], &#21335;&#26408;&#26519;&#32291; [Nan2 mu4 lin2 xian4]$

SOLVED: like the previous one, without the guillemet

---

### Post by hihihi100 on 2012-07-09
for a 103,000 lines glossary, how do I locate ALL lines that do not include chinese characters? I believe that somehow I am deleting some content, or the source of the info is not complete...

thx

---

### Post by Vaphell on 2012-07-10
try this
```
sed 's/»/>>/g' file | LANG=C grep -vn $'[\u4e00-\u9fcc]'
```

u4e00-u9fcc is the main CJK unicode block, but there are few more

i added sed because grep seemed to trigger at » with the specified range o.O i also had to add LANG=C because my locale apparently crapped out at the specified range (invalid range or sorted char or something)
i have to say the standard linux tools support unicode poorly -_-

---

