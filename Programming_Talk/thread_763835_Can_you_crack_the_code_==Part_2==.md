---
title: "Can you crack the code? ==Part 2=="
date: 2008-04-23
forum: Programming Talk
---

### Post by Zugzwang on 2008-04-23
So due to the [overwhelming participation]("http://ubuntuforums.org/showthread.php?t=763545") in the first round :) here's another tricky puzzle. It is a little bit harder than the first one, but still not too hard since it's only the second round. You task is it to decode the following message:

```

10721,4009,2369,11189 
4163,12127 
815,2189,6283,11857,302,3749,5633,3811,23183
7783,10481,7313
12283,2033,1969
4387,1529,8777,8509,206,3587,1991
9991,9353,13213
334,13847,1441
8509,7519,11183,7897,7097,13333,1133,889
9301,5311
2353,2921,6493,1253
417,7519,13561
21631,11327,17593
334,7991,1133
6077,7519,2369,7313,1133
515,3811,4841,6901,1133
7313,4841
6901,4841,3811,8137,2369,4429,1751
7313,1957,1133
5459,7519,10403,10403,3811,1133
```
You should already see how the words are separated. 

Also here's a hint: All the numbers above have something in common! What is it?

---

### Post by Lster on 2008-04-23
This looks hard - but I have an idea!

---

### Post by Lster on 2008-04-23
Wow... I'm close - if you catch my drift!

---

### Post by Siph0n on 2008-04-23
I wrote what I think all the numbers have in common in white below this sentence... Is it true???
[COLOR="White"]Are all the numbers made up of exactly two composite numbers??? :)[/COLOR]

---

### Post by Lster on 2008-04-23
Is there another code within it?

Apart from this:
[COLOR="White"]
this is certainly not the message you are supposed to find but you are quite close to solving the puzzle[/COLOR]

---

### Post by Zugzwang on 2008-04-24
> **Lster said:**
> Is there another code within it?


Indeed, there is. Also Siph0n is quite right, since (in white):
[COLOR="White"]Every number given is obtained by multiplying two prime numbers[/COLOR]

---

### Post by Lster on 2008-04-25
OK. I'll be trying this later tonight - I have college now.

---

### Post by LaRoza on 2008-04-25
> **Lster said:**
> OK. I'll be trying this later tonight - I have college now.

0300? Early morning college?

---

### Post by Balazs_noob on 2008-04-25
> **LaRoza said:**
> 0300? Early morning college?

He is from England...
when he posted it was about 8:00
or somewhere about that :D

---

### Post by LaRoza on 2008-04-25
> **Balazs_noob said:**
> He is from England...
when he posted it was about 8:00
or somewhere about that :D

I know, it is a joke. It is 0443 here. I just find the time zones to be kind of funny. I could be on irc and suddenly someone states they are going to eat breakfast in the middle of (my) night.

---

### Post by Ferrat on 2008-04-25
> **LaRoza said:**
> I know, it is a joke. It is 0443 here. I just find the time zones to be kind of funny. I could be on irc and suddenly someone states they are going to eat breakfast in the middle of (my) night.

Would be funny without them, as long as I get to live on the side that has daytime when the sun is up :D

---

### Post by Lster on 2008-04-25
I'm stuck now! Any hints?

---

### Post by JamesUser on 2008-04-25
Am exploring how those numbers were made. I have only figured out  how one half of them were chosen... With the help of [COLOR="White"]http://britton.disted.camosun.bc.ca/jbprimefactor.htm[/COLOR] 

Disabled automatic link parsing to hide the link.

---

### Post by evymetal on 2008-04-25
Well set problem, I haven't found how Lster got the first plaintext quite yet - expected it to be a simple ceasar cypher when I got to a substitution cypher, but I can't spot the trick quite yet.

Duh!!! I've just spotted the obvious step I missed (it's 2:30 am here and i'm really tired). I've got to the same (1st) message.

...
Haven't worked out the second part, but I think I have it down to a substitution cypher of some kind (i'm assuming there isn't some kind of key that we need, but perhaps I'm wrong). Anyway, I'm off to bed (it's now 2:55 am, and I've got a whole load of important work to get done this weekend rather than trying to crack this... If nobody has solved it I'll try again early next week)

---

### Post by haTem on 2008-04-26
Fun challenge :).

Is this the encoded message, or is there more to it (in white)?:
[COLOR=White]IT@LOOKS@LIKE@(>YOU@MANAGED@TO@SOLVED@THIS@DECODING@PUZZLE@@@@@@@@@@@@@@@@@@@@@@(*@@@@@@@

Is the rest just padding from the 1st message, or is there some trick to it? :-P

[/COLOR]

---

### Post by Lster on 2008-04-26
I think you've done it! :) I'm interested how?

---

### Post by evymetal on 2008-04-26
Should have stayed up another half an hour! I had it already but it looked like nonsense as I was expecting the same word breaks, so I started trying to shift the letters around!

@ Lster: (In White) - you'll kick yourself (like I just have)
[COLOR="White"]It's exactly the same as the first message. The trick is that he's used a 53 character alphabet - the first 26 are the letters for the first message, the next is for spaces in the main cypher, and the final 26 are for the main cypher. the clue that should have given it away was that the final sequence of 103,103,... are all spaces[/COLOR]

---

### Post by haTem on 2008-04-26
@ envymetal (in white):

[COLOR="White"]haha, I did the same thing at first, I was expecting the word breaks to be separated in the same way, so it looked like gibberish. I accidentally discovered it when I wrote a small C program to try different possibilities and forgot to put in the word breaks :D. I probably should have cleaned up the plain-text a bit, the "@s" should be spaces, it just happened to work out like that based on the way I was casting the numbers to char.[/COLOR]

---

### Post by Zugzwang on 2008-04-28
haTem, you really managed to crack this code. It's just like evymetal said. Congratulations! As usual, you've got the honour to post a next challenge (if you want, of course).

---

