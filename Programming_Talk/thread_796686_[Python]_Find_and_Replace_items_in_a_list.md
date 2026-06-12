---
title: "[Python] Find and Replace items in a list"
date: 2008-05-16
forum: Programming Talk
---

### Post by durand on 2008-05-16
How would you find and replace items in a list.

For example:
```

li = ['1','3','7','J']

```
How would you replace the J with, say "11". The context for this is a poker game. I need to check if a list is a straight and it adds the numbers together in order and divides by 5. If it equals the middle number, then this is a straight.
The problem is that jacks/queens/kings/aces aren't currently represented by a number.

---

### Post by LaRoza on 2008-05-16
> **durand said:**
> How would you find and replace items in a list.

For example:
```

li = ['1','3','7','J']

```
How would you replace the J with, say "11". The context for this is a poker game. I need to check if a list is a straight and it adds the numbers together in order and divides by 5. If it equals the middle number, then this is a straight.
The problem is that jacks/queens/kings/aces aren't currently represented by a number.
```

>>> lis = ['one','two','three']
>>> lis[lis.index('one')] = 'replaced!'
>>> print lis
['replaced!', 'two', 'three']
>>> 

```

---

### Post by durand on 2008-05-16
Thanks LaRoza!

---

### Post by durand on 2008-05-16
Also, is there anyway to catch errors like ValueError. Would it be possible to use them in if statements?

if ValueError:
   do something
else:
   do something else..

Thanks in advance.

---

### Post by Jessehk on 2008-05-16
To replace **all** occurances, you could alternatively do something like this:

```

def with_index(seq):
    for i in xrange(len(seq)):
        yield i, seq[i]

def replace_all(seq, obj, replacement):
    for i, elem in with_index(seq):
        if elem == obj:
            seq[i] = replacement

def main():
    li = ['1', '3', '7', 'J']

    replace_all(li, 'J', '11')
    print li

if __name__ == "__main__":
    main()

```

---

### Post by durand on 2008-05-16
Yeah, I'm going to need that sometime later. *Bookmarked*
Thanks!

---

### Post by LaRoza on 2008-05-16
> **durand said:**
> Also, is there anyway to catch errors like ValueError. Would it be possible to use them in if statements?

if ValueError:
   do something
else:
   do something else..

Thanks in advance.

```

try:
    #code
except ValueError:
    #do something on ValueError
except OtherError:
    #do something else on OtherError
finally:
    #do this no matter what

```

Not all are needed, so look into Exception Handling more.

---

### Post by ifross on 2008-05-16
Also not sure about your method of finding a straight, say if you had [1,3,3,3,5] if you add them together and divide by 5 you get 3. By your method this would count as a straight when it clearly isnt...

you could do say:


[PHP]for i, value in enumerate(list):
    if value == list[i+1] - 1 == list[i+2] -2 == #and so on for 5
        straight = True[/PHP]




There is probably a better way, but I think I used this way when I was doing my poker scoring algorithm...

---

### Post by geirha on 2008-05-16
Assuming the list li is sorted, this should tell you if it's a straight.
[php]
if li == range(li[0], li[0]+5):
  print "straight!"  
[/php]
Probably not the most efficient algorithm, but short and nice to write :)

---

### Post by durand on 2008-05-17
> **LaRoza said:**
> ```

try:
    #code
except ValueError:
    #do something on ValueError
except OtherError:
    #do something else on OtherError
finally:
    #do this no matter what

```

Not all are needed, so look into Exception Handling more.

Could I put this within an if statement? I should probably look into error handling. Thanks


> 
Also not sure about your method of finding a straight, say if you had [1,3,3,3,5] if you add them together and divide by 5 you get 3. By your method this would count as a straight when it clearly isnt...

you could do say:



```
for i, value in enumerate(list): 
    if value == list[i+1] - 1 == list[i+2] -2 == #and so on for 5 
        straight = True  

```


There is probably a better way, but I think I used this way when I was doing my poker scoring algorithm...

Damn, I thought there would be a catch to this :( I'll have to look into it cos I'm still new to python and I don't understand whats going on in there. Thanks.


> Assuming the list li is sorted, this should tell you if it's a straight.

```
if li == range(li[0], li[0]+5): 
  print "straight!"  
```
Probably not the most efficient algorithm, but short and nice to write :)

Would this work for a list like 2,3,4,4,5? Thanks for looking at this.

---

### Post by geirha on 2008-05-17
> **durand said:**
> 
Would this work for a list like 2,3,4,4,5? Thanks for looking at this.

Yes. With li=[2,3,4,4,5], li[0] has the value 2. So we compare li with range(2,2+5) which evaluates to [2,3,4,5,6], which is not equal to [2,3,4,4,5] and thus it's not a straight.

---

### Post by durand on 2008-05-17
Ohh, I see what it does now. I thought that it just compares the first and last number. I might use this seeing as its the shortest amount of code. Thank you.

I got one more question. This poker game I'm coding is not normal poker. It's called [BigTwo]("http://en.wikipedia.org/wiki/Bigtwo") and the point is, 2's are high in this game but they can also be low as part of a straight.

Eg: 2,3,4,5,6 and J,Q,K,A,2 should both be possible. Any ideas how this can be done?

---

### Post by geirha on 2008-05-18
> **durand said:**
> Ohh, I see what it does now. I thought that it just compares the first and last number. I might use this seeing as its the shortest amount of code. Thank you.

I got one more question. This poker game I'm coding is not normal poker. It's called [BigTwo]("http://en.wikipedia.org/wiki/Bigtwo") and the point is, 2's are high in this game but they can also be low as part of a straight.

Eg: 2,3,4,5,6 and J,Q,K,A,2 should both be possible. Any ideas how this can be done?

I'd say evaluating twice is easiest. First replace aces and twos with 14 and 15 respectively, if that doesn't give a straight, change the aces and twos to 1 and 2 respectively and check for straight again.

---

### Post by durand on 2008-05-19
Oh ok, Thank you. I just don't seem to think like a programmer :P

---

### Post by naxa on 2010-02-24
# if your version > python 2.5
li = ['1','3','7','J']
li = [11 if a == 'J' else a for a in li]
#['1', '3', '7', 11]

---

### Post by durand on 2010-02-24
> **naxa said:**
> # if your version > python 2.5
li = ['1','3','7','J']
li = [11 if a == 'J' else a for a in li]
#['1', '3', '7', 11]

Hehe, thanks. I started this post when I was still new to programming but I am now a lot more adept with python. I like that method but I personally would separate it onto multiple lines to make it easier to read.

---

### Post by OgreProgrammer on 2010-02-24
The way I would do it is with a dictionary giving each card a hidden value that has a specific prime value which cannot be the sum of two or more other cards. Assuming that the card hand always has the same number of cards, a quick summation will tell you what you have. 

Then you just need a dictionary with the sums as keys that represent a string naming the hand.

I skipped the first few primes. Sum collisions become possible with them.

'2' : 13
'3' : 17
'4' : 19
'5' : 23
'6' : 29
'7' : 31
'8' : 37
'9' : 41
'10' : 43
'J' : 47
'Q' : 53
'K' : 59
'A' : 61

Your minimum value with this scheme is 52 (4 2's) and a 17 (from a 3), for a total of 69. So You can see that none of the combinations can form a value inside the range of our cards, and I am pretty sure that means no combination of cards can have the same value as another combination. 

So then we have our dictionary for combos. You can choose to track every possible combo, or combine them with matching keys in the dictionary. 

"4-of-a-kind-2s" : 69
"Low-House" : 73
"Low-House" : 77
"Two-low-Pairs" : 79

Or something like that. The high combos with 2s would have second entries, and you would look through the dictionary backwards for a match, so that you get the high combos first.

With some additional cleverness you can arrange the scores so that full houses always beat two pairs. And so on.

---

### Post by durand on 2010-02-24
> **OgreProgrammer said:**
> The way I would do it is with a dictionary giving each card a hidden value that has a specific prime value which cannot be the sum of two or more other cards. Assuming that the card hand always has the same number of cards, a quick summation will tell you what you have. 

Then you just need a dictionary with the sums as keys that represent a string naming the hand.

I skipped the first few primes. Sum collisions become possible with them.

'2' : 13
'3' : 17
'4' : 19
'5' : 23
'6' : 29
'7' : 31
'8' : 37
'9' : 41
'10' : 43
'J' : 47
'Q' : 53
'K' : 59
'A' : 61

Your minimum value with this scheme is 52 (4 2's) and a 17 (from a 3), for a total of 69. So You can see that none of the combinations can form a value inside the range of our cards, and I am pretty sure that means no combination of cards can have the same value as another combination. 

So then we have our dictionary for combos. You can choose to track every possible combo, or combine them with matching keys in the dictionary. 

"4-of-a-kind-2s" : 69
"Low-House" : 73
"Low-House" : 77
"Two-low-Pairs" : 79

Or something like that. The high combos with 2s would have second entries, and you would look through the dictionary backwards for a match, so that you get the high combos first.

With some additional cleverness you can arrange the scores so that full houses always beat two pairs. And so on.

Hmm, that sounds like a really good algorithm to use. I put that project on hold while I learnt more python but I think I'll start it up again.

Thanks :)

---

### Post by Sage81 on 2012-02-10
[FONT=&quot]I saw you can do a multiple find and replace a list of items in text online at [[COLOR=blue]http://list-replace.info[/COLOR]]("http://list-replace.info") .  Maybe this can help.[/FONT]

---

