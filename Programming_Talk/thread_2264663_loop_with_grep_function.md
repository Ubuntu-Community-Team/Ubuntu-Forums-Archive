---
title: "loop with grep function"
date: 2015-02-09
forum: Programming Talk
---

### Post by tho4 on 2015-02-09
Hi Ubuntu users,

I struggle to define a loop taking name in a first file (Bureau/taxa, each line of the file is a species name) and retrieving the line with the corresponding name and the DNA sequence associated in a second file (Bureau/conc_5genes.fas). The file Bureau/conc_5genes.fas is as follows:

>species1 ATTGTCTAT
>species2 TTGCATATC
...

Here is the loop:

for line in Bureau/taxa ; 
     do 
     grep '$line' Bureau/conc_5genes.fas >> Bureau/moldata_hostrecords; 
done

Thank you for your help!

---

### Post by Lars Noodén on 2015-02-09
The part '$line' uses single quotes. That means the contents will be literal.  If you use double quotes instead "$line" then the contents will be processed and in this case the contents of the variable are used instead.  That is probably what you meant to do with grep.

---

### Post by schragge on 2015-02-09
Try
```
sort -k1,1 Bureau/taxa | join <(sort -k1,1 Bureau/conc_5genes.fas) -
```
or, if both files are already sorted on the common field, just
```
join Bureau/{taxa,conc_5genes.fas}
```

---

### Post by tho4 on 2015-02-10
Thank you for the answers, but I found it by myself. I did as follows:

taxa=Bureau/taxa
moldata=Bureau/conc_5genes.fas

for line in $taxa
    do
    awk 'Begin
    {RS=">"}
    /'$line'/ {print ">"$0}' $moldata >> Bureau/moldata_hostplanttaxa.fas
done

exit

The awk command allows me here to read the format of my DNA sequences (">" separate the sequences)

---

### Post by Vaphell on 2015-02-10
Not that i understand the logic but what is the for loop supposed to do in the first place? It iterates over a single element with value = 'Bureau/taxa' and that's it.
in other words there is nothing that mandates a loop because you access only 1 unique value there.

---

