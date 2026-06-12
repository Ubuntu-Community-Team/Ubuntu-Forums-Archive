---
title: "Grep a number in a file according to some values in other columns"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by Muriel_Gros-Baltha on 2014-06-11
Hello !

I have this file :

```
K1_run10.log:Cross-Entropy (masked data):     0.890767
K1_run1.log:Cross-Entropy (masked data):     0.900289
K1_run2.log:Cross-Entropy (masked data):     0.88847
K1_run3.log:Cross-Entropy (masked data):     0.884207
K1_run4.log:Cross-Entropy (masked data):     0.897922
K1_run5.log:Cross-Entropy (masked data):     0.892557
K1_run6.log:Cross-Entropy (masked data):     0.899812
K1_run7.log:Cross-Entropy (masked data):     0.897378
K1_run8.log:Cross-Entropy (masked data):     0.886765
K1_run9.log:Cross-Entropy (masked data):     0.889575
```

I would like to obtain the number following the word "run" where the value in the last column is the minimum of all the values.
For instance here, the minimal value is "0.884207" so I would like a script returning the number 3.

Thank you for your help !

Mu

---

### Post by steeldriver on 2014-06-11
I don't think you can do that directly with grep - you would need to find the line containing the maximum value first, for example by sorting and taking the top line

```

sort -nk4,4 *file* | head -n 1 | grep -Po '(?<=run).*(?=\.log)'

```
or with sed instead of head + grep
```

sort -nk4,4 *file* | sed -nr '1s/.*run([0-9]+)[.]log.*/\1/p'

```

---

### Post by Muriel_Gros-Baltha on 2014-06-11
Hi !
Thank you steeldriver for your answer, it's working well !!
I have several of these files called CrossEntropy_Ki with i between 1 and 10 so I wanted to run a loop to obtain the value of run associated with each K.
Here is my code :
for K in 1 2 3 4 5 6 7 8 9 10
    do
        echo K$K; sort -nk4,4 CrossEntropy_K$K | sed -nr '1s/.*run([0-9]+)[.]log.*/\1/p'
    done

It's working well, I obtain this :
K1
3
K2
6
K3
9
K4
5
K5
4
K6
5
K7
10
K8
2
K9
8
K10
2
However, how can I obtain rather one row with two columns like that :
K1 3
K2 6
K3 9
K4 5
K5 4
K6 5
K7 10
K8 2
K9 8
K10 2

Thank you for your help ;)

---

### Post by steeldriver on 2014-06-11
I can't really test this but something like

```

for k in {1..10}; do
  printf 'K%d %d\n' "$k" "$(sort -nk4,4 "CrossEntropy_K$k" | sed -nr '1s/.*run([0-9]+)[.]log.*/\1/p')"
done

```

You can replace the literal space between the %d format specifiers with a \t if you want tabbed columns

---

### Post by Muriel_Gros-Baltha on 2014-06-11
Great, this is working well !

However, in the mean time, I decided to add a third columns, containing the number that was checked to be the minimum.

Here is my code : 
for K in {1..10}
    do
        echo K$K
        sort -nk4,4 CrossEntropy_K$K | sed -nr '1s/.*run([0-9]+)[.]log.*/\1/p'
        sort -nk4,4 CrossEntropy_K$K | awk '{ print $4 }' | head -n1
    done

It works well as I obtain 
K1
3
0.884207
K2
6
0.902681
K3
9
0.951103
K4
5
1.01528
K5
4
1.04045
K6
5
1.16646
K7
10
1.14083
K8
2
1.26172
K9
8
1.34388
K10
2
1.44061


I tried to change it using your answer in order to have
K1 3 0.884207
K2 6 0.902681
...

I tried this :
for K in {1..10}; do
printf 'K%d %d\n' "$K" "$(sort -nk4,4 "CrossEntropy_K$K" | sed -nr '1s/.*run([0-9]+)[.]log.*/\1/p')" "$(sort -nk4,4 "CrossEntropy_K$K" | awk '{ print $4 }' | head -n1)"
done

But it's not working.

Can you tell me where is the error ?

---

### Post by steeldriver on 2014-06-11
You need to add a third format conversion specifier to the print statement - since the 3rd value is floating point, you can use %f i.e.

```

$ for k in {1..2}; do   
  printf 'K%d %d [COLOR=#0000cd]**%f**[/COLOR]\n' "$k" "$(sort -nk4,4 "CrossEntropy_K$k" | sed -nr '1s/.*run([0-9]+)[.]log.*/\1/p')" "$(sort -nk4,4 "CrossEntropy_K$k" | awk '{ print $4 }' | head -n1)"
done

```

(also note I changed your upper-case K to a lower-case k). 

However it would be more efficient and neater if you could find a way to extract both numbers without re-sorting and re-processing the file each time - I don't have time to work on that right now.

---

### Post by Muriel_Gros-Baltha on 2014-06-11
OK it's working well, thanks a lot for your help !!

---

