---
title: "Bash script. Help with 10 digit number"
date: 2013-06-12
forum: Programming Talk
---

### Post by Drenriza on 2013-06-12
Hi guys.

I have a 10 digit number xxxxxx-xxxx, where i would like to calculate the number of different number combinations.
And print each combination in it's full length.

My question is as follows.
What is the most optimal way of doing this in a bash script, _**when**_ i have the following info

[LIST]
[*]Digit 1-7 i already know 
[*]Digit 8-9 is a serial number (Unknown digits) 
[*]Digit 10 i know is a even or odd number based on a inpur variable. 
[/LIST]
  
Hope it makes sense.
Kind regards.

---

### Post by ofnuts on 2013-06-12
If the only digits you don't know are the 7th and 8th, then you have 10x10=100 combinations, and you can generate all the numbers in a loop that counts from 00 to 99:

```

for i in {00..99}
do
   printf "xxxxxx-%dxx\n" $i
done

```

Adding the last two digits to this is left as an exercise to the reader, using an inner loop and the brace expansion with increment: {01..99..2} or {00..98..2}

---

### Post by steeldriver on 2013-06-12
or something like

```
oe=3; echo 123456-7{0..9}{0..9}${oe}
```

```
oe=2; echo 123456-7{0..9}{0..9}${oe} | wc -w
100

```

---

### Post by ofnuts on 2013-06-12
Hmm. Yes. Even simpler:

123456-7{01-99}{0..8..2} for even
123456-7{01-99}{1..9..2} for odd

---

