---
title: "question about awk and columns"
date: 2011-11-10
forum: Programming Talk
---

### Post by Jumper11550 on 2011-11-10
So I have a script I'm trying to write that takes a three file column:
```

#0    temperature    resistance
1    77.8382        0.000620609
2    77.8551        0.00063785
3    77.8467        0.000626168
4    77.8636        0.00063785
5    77.8636        0.000615925
6    77.8636        0.000628505
7    77.8721        0.000649533
8    77.8806        0.000588785
9    77.889        0.000628505
10    77.8636        0.000571096

```

and computes a for each line in each column delta using data points two lines away (I can deal with the end points seperately once I have the awk syntax correct to do it in general)

so I want to compute deltaR in the file at line 5 by computing the difference in the R values for lines 2 and 6
deltaR(line4) = R(line2)-R(line6)

here is my script I've been working with:

```

#!/bin/sh
length=`wc -l < $1.std | awk '{print ($1-1) }'`
minus1=`wc -l < $1.std | awk '{ print ($1-2) }'`
minus2=`wc -l < $1.std | awk '{ print ($1-3) }'`

awk '
NR > 1{ resist[$1]=$3 }
NR > 1 { temper[$1]=$2 }
NR == 1 { print $1"\t"$2"\t"$3"\tdeltaR\tdeltaT" }
NR == 2 { print NR-1"\t"$2"\t"resist[$(NR-1)]-resist[$(NR+1)]"\t"temper[$(NR-1)]-temper[$(NR+1)] }
NR == 3 { print NR-1"\t"$2"\t"resist[$(NR-2)]-resist[$(NR+1)]"\t"temper[$(NR-2)]-temper[$(NR+1)] }
NR > 3 && NR < '"$minus2"' { print NR-1"\t"$2"\t"(resist[(NR-3)]-resist[(NR+1)])"\t"(temper[(NR-3)]-temper[(NR+1)]) }
NR == '"$minus1"' { print NR-1"\t"$2"\t"(resist[(NR-3)]-resist[NR])"\t"(temper[(NR-3)]-temper[NR]) }
NR == '"$length"' { print NR-1"\t"$2"\t"(resist[(NR-3)]-resist[(NR-1)])"\t"(temper[(NR-3)]-temper[(NR-1)]) }' $1.std > $1.test

```

The output file should contain the original three columns as well as add a fourth and fifth column for the delta R and delta T at each point. I've filled in a few lines of the output where R(x) represents the value of resistance on line x.

```

#0    temperature    resistance        deltaR        delta T
1    77.8382        0.000620609        special case    special case
2    77.8551        0.00063785        special case    special case
3    77.8467        0.000626168        R(1)-R(5)    T(1)-T(5)
4    77.8636        0.00063785        R(2)-R(6)    T(2)-t(6)
5    77.8636        0.000615925        ....        ...
6    77.8636        0.000628505
7    77.8721        0.000649533
8    77.8806        0.000588785
9    77.889        0.000628505
10    77.8636        0.000571096

```

I would love to be able to calculate this difference for an arbitrary pair of lines

---

### Post by SeijiSensei on 2011-11-10
Just a suggestion.... This would be much easier to accomplish using a spreadsheet.

---

### Post by Jumper11550 on 2011-11-10
> **SeijiSensei said:**
> Just a suggestion.... This would be much easier to accomplish using a spreadsheet.
To do once, but with a large number of data files it will be much easier to hand it to a script on the command line. So I'd rather get this working.  Thanks.

---

### Post by papibe on 2011-11-10
In your case, I would attempt to solve the problem in 2 steps, first calculating the Rs and then the Ts. That is 2 scripts, and 2 pass.

Just a thought,
Regards.

---

### Post by Jumper11550 on 2011-11-10
I had thought of that, and I guess I should have posted my output that's my bad.

the subtraction isn't being posted all the output gives me is:
```

#0    temperature    resistance    deltaR    deltaT
1    77.8382    0.000620609    77.8382
2    77.8551    0.00063785    77.8551
3    77.8467    0.000620609    77.8382
4    77.8636    0.00063785    77.8551
5    77.8636    0.000626168    77.8467
6    77.8636    0.00063785    77.8636
7    77.8721    0.000615925    77.8636
8    77.8806    0.000628505    77.8636
9    77.889    0.000649533    77.8721
10    77.8636    0.000588785    77.8806

```

first I'm only getting 4 columns instead of the 5 columns in the print statements. second its not calculating the differences. it prints the first three columns and then posts the second column again instead of the delta R like its supposed to.  the delta T column isn't even there.

It's the syntax for doing the array element subtraction in awk not the flow/logic of the script I need help with.

---

### Post by erind on 2011-11-10
> **Jumper11550 said:**
> So I have a script I'm trying to write that takes a three file column:
```

#0    temperature    resistance
1    77.8382        0.000620609
2    77.8551        0.00063785
3    77.8467        0.000626168
4    77.8636        0.00063785
5    77.8636        0.000615925
6    77.8636        0.000628505
7    77.8721        0.000649533
8    77.8806        0.000588785
9    77.889        0.000628505
10    77.8636        0.000571096

```and computes a for each line in each column delta using data points two lines away (I can deal with the end points seperately once I have the awk syntax correct to do it in general)

so I want to compute deltaR in the file at line 5 by computing the difference in the R values for lines 2 and 6
deltaR(line4) = R(line2)-R(line6)
...
The output file should contain the original three columns as well as add a fourth and fifth column for the delta R and delta T at each point. I've filled in a few lines of the output where R(x) represents the value of resistance on line x.

```

#0    temperature    resistance        deltaR        delta T
1    77.8382        0.000620609        special case    special case
2    77.8551        0.00063785        special case    special case
3    77.8467        0.000626168        R(1)-R(5)    T(1)-T(5)
4    77.8636        0.00063785        R(2)-R(6)    T(2)-t(6)
5    77.8636        0.000615925        ....        ...
6    77.8636        0.000628505
7    77.8721        0.000649533
8    77.8806        0.000588785
9    77.889        0.000628505
10    77.8636        0.000571096

```I would love to be able to calculate this difference for an arbitrary pair of lines
This might be something to start with,


calc.sh
```
#!/bin/bash
# set -x

 awk -v d="$1" '
      NR==1 { print $0, "deltaR deltaT"; next }
      NR<=d+1 { print $0, s=" special_case special_case" }
      { a[$1]=$0; temp[$1]=$2; res[$1]=$3 }
      ++c > d*2 { print a[c-d], sprintf(" %.4f", temp[c-d*2]-temp[c]), sprintf(" %.9f", res[c-d*2]-res[c]) }
      END { for(i=NR-d; i<NR; i++) print a[i] s }
     ' filename

```Run it like:

  ```
./calc.sh 2
```For an arbitrary pair of lines, change *2* to any desired number. Note that the last 2 lines are *"special case"* too.

---

### Post by Jumper11550 on 2011-11-11
Thank you so much, this worked perfectly!!

---

