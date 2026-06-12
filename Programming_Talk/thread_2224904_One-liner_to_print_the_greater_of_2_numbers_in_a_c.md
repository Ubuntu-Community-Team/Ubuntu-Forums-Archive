---
title: "One-liner to print the greater of 2 numbers in a column?"
date: 2014-05-18
forum: Programming Talk
---

### Post by lethalfang on 2014-05-18
Hi guys, 

This tasks seems simple enough that it should be done with awk, but I don't know how to do it. I'm trying not to bother with python or perl for something like this. 

Basically, I have a bunch of lines with overlaps, and I want to print out two extra columns the overlap regions. 
For instance, I have this:

```

START_A	END_A	FEATURES	START_B	END_B	FEATURES	OVERLAP
1	500	FeatureA1	100	600	FeatureB1	400
1000	2000	FeatureA2	1100	2200	FeatureB2	900


```


```

Comm_i	Comm_j START_A	END_A	FEATURES	START_B	END_B	FEATURES	OVERLAP
100	500	1	500	FeatureA1	100	600	FeatureB1	400
1100	2000	1000	2000	FeatureA2	1100	2200	FeatureB2	900


```


Basically, the Comm_i is the greater of Start_A (Column #1) and Start_B (Column #4). The Comm_j is the less of End_A (Column #2) and End_B (Column #5). 

Any idea how to do this?

Thanks in advance.

---

### Post by Vaphell on 2014-05-19
```
awk 'NR==1 { print "Comm_i\tComm_j\t" $0 } NR>1 { print ($1>$4?$1:$4) "\t" ($2<$5?$2:$5) "\t" $0 }' cols.txt
```

---

