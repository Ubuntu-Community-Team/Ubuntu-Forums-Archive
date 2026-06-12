---
title: "formatting as csv"
date: 2014-04-23
forum: Programming Talk
---

### Post by peter_brickles on 2014-04-23
I have a rather large file as below 

> 
 Richard Smith
Mr Roger Jones
Mrs maria jones 
 Stephen Smith
 Kathryn Hogwarts 



I would like to have it in the following format so i can open in libre office 

 > 

,Richard,Smith
Mr,Roger,Jones
Mrs,maria,jones 
,Stephen,Smith
,Kathryn,Hogwarts



any one have any ideas how i can accomplish this ? 


Cheers Pete

---

### Post by SeijiSensei on 2014-04-23
```

sed 's/^/,/g' < file | sed 's/\ /,/g' > newfile

```
The first sed command adds a comma to the beginning of the line, represented by "^" in [regular expressions](). It then "pipes" the result to a second instance of sed that replaces the spaces with commas.  The result is then saved as newfile.

If I apply that to the list above I get
```

,Richard,Smith
,Mr,Roger,Jones
,Mrs,maria,jones
,Stephen,Smith
,Kathryn,Hogwarts,

```
Notice the problem with Kathryn.  In the text you posted, her entry ends with two spaces.  If you're reading this into LO Calc, you'd just get an empty column, but if you want a clean input file, you can modify the command above like this:
```
sed 's/^/,/g' < file | sed 's/\ /,/g' | sed 's/,$//g' > newfile
```
The last sed deletes trailing commas using the "$" special character in regular expressions that denotes the end of the line.

---

### Post by steeldriver on 2014-04-23
I'm surmising you want the leading comma only when the title field (Mr/Mrs) is empty? 

How about awk?

```

$ awk -vOFS=, '{print (NF>2?$(NF-2):""),$(NF-1),$NF}' addresses.txt 
,Richard,Smith
Mr,Roger,Jones
Mrs,maria,jones
,Stephen,Smith
,Kathryn,Hogwarts

```

---

### Post by Vaphell on 2014-04-23
```
sed -r 's/\s+/,/g; /Mrs?/! s/^/,/'
```

what about double-barrelled names? In such a case using , instead of whitespace would be rather wrong.

---

