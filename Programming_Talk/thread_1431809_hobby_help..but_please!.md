---
title: "hobby help..but please!"
date: 2010-03-17
forum: Programming Talk
---

### Post by manyu29 on 2010-03-17
i have been trying to write a program which reverses a text entered,but i havent had any luck so far..could anybody give me a sample program or even a pseudocode?

---

### Post by derekeverett on 2010-03-17
I'm no programming genius, but seems to me you could parse the string into a char array. Then count threw the array assigning the count value to an int.

Then loop through the array backwards using the array value of your int, decrementing the int by one at every loop iteration. This would print out the string backwards one char at a time.

---

### Post by manyu29 on 2010-03-17
how do i do the char array in nasm?im already having trouble using the [ebx]..it seems that im not doing it right..

---

### Post by derekeverett on 2010-03-17
> **manyu29 said:**
> how do i do the char array in nasm?im already having trouble using the [ebx]..it seems that im not doing it right..

You got me there.

---

### Post by manyu29 on 2010-03-17
stil uve helpd me a lot..thx man

---

### Post by JoeWheeler on 2010-03-17
What language are you using, this is reallly easy in python I'm not sure about other languages though

---

### Post by superarthur on 2010-03-17
In Perl:
[PHP]my $string = 'word';
$string = reverse $string;
print $string; #prints: drow[/PHP]
(even though the thread is [SOLVED], I couldn't resist. :P)

---

### Post by nvteighen on 2010-03-17
> **manyu29 said:**
> how do i do the char array in nasm?im already having trouble using the [ebx]..it seems that im not doing it right..

Er... Why are you using NASM? Assembly is a language not meant for beginners... If you're a beginner, there are plenty of better languages to choose from; I recommend you Python, but look at the stickies and the lots of discussion about the topic in these forums.

---

### Post by schauerlich on 2010-03-17
> **nvteighen said:**
> Er... Why are you using NASM? Assembly is a language not meant for beginners... If you're a beginner, there are plenty of better languages to choose from; I recommend you Python, but look at the stickies and the lots of discussion about the topic in these forums.

I'm guessing it's homework.

---

### Post by kaibob on 2010-03-19
> **superarthur said:**
> 
(even though the thread is [SOLVED], I couldn't resist. :P)

Me too!

```
#!/bin/bash

word=kaibob

i=${#word}

for ((j=1 ; j<=${i} ; j++)) ; do
   echo -n ${word:(-${j}):1}
done

echo
```

Just for the record, the easiest solution is the rev utility:

> $ rev <<< kaibob
bobiak

---

