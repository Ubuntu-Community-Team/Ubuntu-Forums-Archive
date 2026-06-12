---
title: "random word generator"
date: 2007-08-01
forum: Programming Talk
---

### Post by Mrwasab1 on 2007-08-01
Hi guys,
I am attemting to write a shell script wich when run, it will ask the user 
do you want to create a random sentance

if yes then it will grab one word from 4 different colums of text and put them together in a sentance

for example 
```

Abc    jkl    stu    234

Def    mno    vwx   567

Ghi    pqr    yz1   890


```
And it would come out
```

Abc mno yz1 234

```
im fairly new to scripting so can someone point me in the right direction and tell me what i should be using or if they can show me a script which is already written and i can modify it.

been searching google but cant seem to find much


i am writing this in an HP-UX 11.11 system using ksh

---

### Post by thomasaaron on 2007-08-01
1. Count the number of rows in the file
2. Generate 4 random number (representing columns 1-4)
3. Generate 4 random number between 1 and the result of step 1
4. Count down through the rows, stopping on the rows represented by  the 4 random numbers from step 3.
5. Whenever you stop on one of these rows, use awk to extract the word from the column represented by one of the random numbers from step 2.

__________________________________________________________________________-

That said...

It might be easier to just have a single text file with a long list of words that can be loaded into an array.

Then just generate 4 random numbers ranging between 0 and the length of the array. Use those random numbers as indexes to extract words from the array.

---

### Post by Mrwasab1 on 2007-08-02
The reason the text is split into 4 columns is because each column represents the order which the words have to go in

so any word from column 1 will be the 1st word in the sentance
column 2 the second word...etc...

i thought about using an array to do this but it didnt work because of that technicallity

---

### Post by H264 on 2007-08-03
I have been thinking about doing something kinda like this, only in a more interesting way...
Don't know if anybody else plays this game called mad libs, but I was thinking to have a list of nouns, adverbs, verbs, and the like to auto fill in a mad libs form or something like that.

I did one on [http://www.madlibs.org/](http://www.madlibs.org/) but the ones you buy I think are better right now. It is typically best if done late at night when things tend to get funnier ;)

:lolflag:

---

### Post by smartbei on 2007-08-03
Sure, I used to play mad libs, but the whole point is that the group of friends comes up with the words, with all the connotations that come with it.

If you randomise it, it wouldn't be nearly as funny. Just like filling one out yourself isn't nearly as funny.

About the topic:
Just have four arrays.

---

### Post by alphane on 2007-08-03
> i thought about using an array to do this but it didnt work because of that technicallity

Surely arrays would work if placed the text from each column into the array, it seems you are thinking that you'd put each row into an array?

So array1 = Abc, Def, Ghi
     array2 = Jkl, Mno, Pqr
     array3... so on.

Generate a random number, pull the resulting string from the array, display, repeat?

---

### Post by b1g4L on 2007-08-03
Here is a quick example of what you could do in Python. Simply read from a text file to import the strings into 4 separate arrays.

```
import random

array1 = ["Abc","Def", "Ghi"]
array2 = ["jkl","mno","pqr"]
array3 = ["stu","vwx", "yzl"]
array4 = ["234", "567", "890"]

print array1[random.randrange(0,len(array1))],
print array2[random.randrange(0,len(array2))],
print array3[random.randrange(0,len(array3))],
print array4[random.randrange(0,len(array4))]
```

---

### Post by pmasiar on 2007-08-03
Or even simpler:

```
import random
nouns = [...]
verbs = [...]
for arr in [nouns, verbs, ...]:
    print random.choice(arr) 

```

---

### Post by finer recliner on 2007-08-03
use CSV formatting (comma sepearted value) to denote each column. words have different lengths, and using commas will make it easier for your program to determine which "column" it is looking at

---

### Post by slavik on 2007-08-03
use an array for each column, then pick whatever number of random numbers and pick the proper stuff from the array.

check if HP-UX has /dev/random ... then you can read as many bytes as needed for a random number of proper size and then pick stuff from the array.

---

