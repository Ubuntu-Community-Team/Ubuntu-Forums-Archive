---
title: "Reverse an input sequence using bash script"
date: 2010-04-04
forum: Programming Talk
---

### Post by Winos on 2010-04-04
Hi, i have very little knowledge of bash but would like to make a script to output the words i input into the script but in reverse order; for example i input  " I like cheese" i would like it to output " cheese like I"

Thanks in advance for any helpful responses

---

### Post by croto on 2010-04-04
Write a script that outputs the words you enter in normal order:
```

$./reverser.sh I like cheese
I like cheese

```

and then I'll help you modify it to reverse the words. I recommend trying to use a loop over the positional parameters and print them out one at a time.

---

### Post by lostinxlation on 2010-04-05
> echo  "1 2 3 4" | rev
> 4 3 2 1

---

### Post by Some Penguin on 2010-04-05
Something that's not entirely clear is whether the OP wants to be able to identify the words in something like:

``Oh bother''', said Pooh as Eeyore devoured his soul for the 5th time even before he'd prepared breakfast.

or

"Hydra's heads' terrible teeth masticated menacingly", thought the hero Herakles.


Would '5th', "he'd" and "heads'" be considered words?
Would the output need to be stripped of punctuation, such as the `` and ''?

---

### Post by Winos on 2010-04-05
I am guessing the "words" would be defined by spaces inbetween. So the punctuation can stay in it's place ?

I Figured out how to do what i wanted. If anyone is interested this is how simple i needed it to be:

> [I]echo "Input 4 more words "
read word1
echo "Input 3 more words"
read word2
echo "Input 2 more words"
read word3
echo "Input 1 more word"
read word4
clear
echo $word4
echo $word3
echo $word2
echo $word1[/I]

---

### Post by Yuzem on 2010-04-05
```
for (( i = ${#*}; i > 0; i-- ))
{
	echo ${!i}
}
```

Run it like this:
script hello and good bye

---

### Post by Winos on 2010-04-05
Thank you for the reply Yuzem, however could you please explain your script because i am just learning bash and i have almost no knowledge of it at the moment.

---

### Post by Yuzem on 2010-04-05
Ofcourse:

I will assume that you understand the next for loop that counts from 0 to 10:
```
for (( i = 0; i < 10; i++ ))
{
	echo $i
}
```

Now, the other loop:
```
for (( i = ${#*}; i > 0; i-- ))
{
	echo ${!i}
}
```

And the example:
script hello and good bye


${#*} is the number of arguments passed to the script in this example is equal to 4. (the loop counts from 4 to 1)

${!i} is an indirect variable references that means that it will resolve to the variable named $i. If $i = 4 then ${!i} will be $4 (the last parameter).

Check [this]("http://tldp.org/LDP/abs/html/refcards.html") link. It has helped me lot.

---

### Post by Winos on 2010-04-05
Thanks for all the help!

---

