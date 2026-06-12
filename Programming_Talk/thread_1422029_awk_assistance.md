---
title: "awk assistance"
date: 2010-03-04
forum: Programming Talk
---

### Post by junapp on 2010-03-04
I have a tab delimited source file with a product code, and a sale price or a mix and match code.

Basically it has the pattern:
```

6502082     $4.99
1109815     2/5$

```From that I want to produce a fixed width file like:
```

6502082 000004.99 000000 00000.00 
1109815 000002.50 000002 00005.00

```I've simplified the question somewhat (there are a few dozen other fields involved) to illustrate my dilemma. I'm using combination of sed and awk to get all the other fields formatted correctly, but running into a snag with this mix and match portion.

right now I have:
```
sed 's/ \$//g' sample_source.txt | awk -F"\t" '{printf("%6s %09s %06s %08.2f \n",$1,$2,0,0);}'
```which produces (undesired result):
```

6502082 000004.99 000000 00000.00 
1109815 0000 2/5$ 000000 00000.00 

```Any awk gurus out there that could help me figure out how to catch that existance of a '/' in the $2 column and behave accordingly as shown up above?

Edit: the sed is overcoming a problem where all the dollar signs on prices have a space character preceding which I remove first along with the dollar sign.
Edit 2: might be a bad example. the 00002.50 is $5.00/2 = 2.50. If it was 3/6$, the second line would be 1109815 000002.00 000003 00006.00

---

### Post by DaithiF on 2010-03-05
Hi,
something like this may get you started:
```
$ cat testfile
6502082     $4.99
1109815     2/5$

$ sed 's/ \?\$//g' testfile | awk '{ if(index($2, "/")) {split($2, a, "/"); f1=a[2]/a[1]; f2=a[1]; f3=a[2]; } else { f1=$2; f2=0; f3=0 }; printf ("%6s %09s %06s %08.2f \n", $1, f1, f2, f3);}' 
6502082 000004.99 000000 00000.00 
1109815 0000002.5 000002 00005.00 

```

---

### Post by weresheep on 2010-03-05
A slight variation on what DaithiF posted. No need to use sed when awk can strip $ from the input string just as easily. You can copy the below code into a file e.g. products, make the file executable and then run it directly.

For example...

$ ./products < testfile
6502082 000004.99 000000 00000.00
1109815 000002.50 000002 00005.00
$


```

#!/usr/bin/awk -f

{
  gsub(/\$/, "")

  code = $1
  price = $2
  units = 0
  cost = 0

  if ($2 ~ /\//) {
    split(price, tmp, /\//)
    units = tmp[1]
    cost = tmp[2]
    price = cost / units
  }

  printf("%6s %09.2f %06d %08.2f\n", code, price, units, cost)
}

```

-weresheep

---

### Post by junapp on 2010-03-07
both look like they would work nicely. I'd probably use the one liner, except that I imagine this might be a recurring task, so weresheep, your approach (with all the nice var names) might get used if only to remind myself what I was doing 6 months from now.

Thanks to both.

---

### Post by weresheep on 2010-03-07
> except that I imagine this might be a recurring task, so weresheep, your approach (with all the nice var names) might get used if only to remind myself what I was doing 6 months from now.

Yeah, I do that myself. I've only been writing awk scripts (other than things like awk '{print $2}') for a short while so anything non trivial I tend to stick in a file so I can refer back to it later, even if I don't use that script itself much.

It is really impressive what awk can do in a throw-away command line, once I know it a lot better I'll maybe start throwing them away :D

-weresheep

---

