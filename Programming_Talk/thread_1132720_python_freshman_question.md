---
title: "python freshman question"
date: 2009-04-22
forum: Programming Talk
---

### Post by Ohmaley on 2009-04-22
i have a liste of letters called "text" and a liste of tuples called "key" in python. I need to assign the "keys" to the letters of the "text" into a variable "phrase" in order to be able to spit out the magic word or sentence , how do i proceed? How would the function "self" be useful?

Exemple:
               text = 'huzteizuocutz' 
                             key = [(0,1),(4,5),(9,10)] 
               .........
                             .....
                             ......
                             >>> print phrase 
                             'hec'

---

### Post by Arndt on 2009-04-22
> **Ohmaley said:**
> i have a liste of letters called "text" and a liste of tuples called "key" in python. I need to assign the "keys" to the letters of the "text" into a variable "phrase" in order to be able to spit out the magic word or sentence , how do i proceed? How would the function "self" be useful?

Exemple:
               text = 'huzteizuocutz' 
                             key = [(0,1),(4,5),(9,10)] 
               .........
                             .....
                             ......
                             >>> print phrase 
                             'hec'

If you tell us the steps you want to perform on the input data, we can help you choose the right Python constructs. Construct an algorithm first, in English.

I'll test your understanding of the problem: what would the output be if you input

```
text = 'huzteizuocutz' 
key = [(4,5),(0,1),(9,10)]
```

and

```
text = 'huzteizuocutz' 
key = [(1,4),(2,3),(9,10)]
```

?

---

### Post by stumbleUpon on 2009-04-22
You need to define a mapping from one list to another list to achieve what you are asking. For the example that you have given, the code below works

```

text = 'huzteizuocutz'

key = [(0,1),(4,5),(9,10)] 

phrase='' # init phrase to empty string

for i in range(len(key)):
  phrase = phrase + text[ key[i][0] ]

print phrase

```

---

### Post by Ohmaley on 2009-04-22
How about this one? Tried it on my own and failed; this forum's my easy way out!
text = 'huzteizuocutz'
key = [(0,1),(4,5),(9,12)] 
...
....
..
>>>print phrase
hecut

---

### Post by stumbleUpon on 2009-04-22
> **Ohmaley said:**
> How about this one? Tried it on my own and failed; this forum's my easy way out!
text = 'huzteizuocutz'
key = [(0,1),(4,5),(9,12)] 
...
....
..
>>>print phrase
hecut

Sorry but who are referring to...??

If you used the code i gave above and changed the key to what you have shown, mine still gives the phrase as 'hec'. Basically the second element of each of the tuple in key plays no role in the piece of code i suggested. 

You have to tell us more about what kind of a mapping you want between the elements of the tuples in 'key' and the characters of the string 'text'.

---

### Post by Ohmaley on 2009-04-22
Yes i was referring to your code.
The seconde element of each of the tuple in key is supposed to play a role. for instance if I had 

text = '[COLOR=Lime]h[/COLOR]uzt[COLOR=Orange]e[/COLOR]izuo[COLOR=Red]cut[COLOR=Black]z[/COLOR][/COLOR]'
key = [([COLOR=Lime]0,1[/COLOR]),([COLOR=Orange]4,5[/COLOR]),[COLOR=Black]([/COLOR][COLOR=Black][COLOR=Red]9,12[/COLOR])[/COLOR]] 

9 to 12 would represent that whole sequence of letters. So how should i modify your coding as to take this into account?
I should have made this clear from beginning. i have set aside my IT class aside thinking i could catch it up in no time... turns out im now being swallowed by this wave of excel python sql. thanks for your help

---

### Post by stumbleUpon on 2009-04-22
ah....i get the point..!
you want the second element of the tuple to represent how many characters you want to extract starting from the position given by the first element of the tuple.

Code is easily modified. 
```

text = 'huzteizuocutz'

key = [(0,1),(4,5),(9,12)] 

phrase='' # init phrase to empty string

for i in range(len(key)):
  phrase = phrase + text[ key[i][0] : key[i][1] ]

print phrase

```

gives phrase as 'hecut' as you wanted.


You just need to be explicit when explaining your problem.

---

### Post by lykwydchykyn on 2009-04-22
Python can do something called "slicing", in which you specify a start and end ordinal for a string or list.  For instance:
```

text="blah"
print text[1:3]

```
Prints out "la".  Your keys are basically slices, so it's just a matter of iterating through the key list and adding together each slice:
```

text='huzteizuocutz'
key = [(0,1),(4,5), (9,12)]
result = ""
for x in key:
    result += text[x[0]:x[1]]
print result

```

Ah! beaten by mere seconds...

---

### Post by imdano on 2009-04-22
A list comprehension would work here as well:
```
text='huzteizuocutz'
key = [(0,1),(4,5), (9,12)]
result = ''.join([text[k[0]:k[1]] for k in key])
print result
```I was testing this out on a machine running Python 2.4 and was a little surprised to find that using a for loop is actually faster than the join/list comprehension until you get up to about 40 keys.  I guess string concatenation for small strings is pretty efficient?

---

### Post by dmizer on 2009-04-22
> **Ohmaley said:**
> this forum's my easy way out!

Closed for review.

---

### Post by dmizer on 2009-04-23
Not homework. Carry on! :)

---

### Post by JK3mp on 2009-04-23
> **dmizer said:**
> Closed for review.

I guess it was opened back up?. LoL

---

