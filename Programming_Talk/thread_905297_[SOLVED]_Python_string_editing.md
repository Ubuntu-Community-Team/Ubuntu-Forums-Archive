---
title: "[SOLVED] Python string editing"
date: 2008-08-30
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-30
I have a list, framefiles. That list contains the following:
```
['frame0', 'frame1', 'frame2', 'frame3']
```
How can I convert it to string and edit the string so it will be:
```
'frame0, frame1, frame2, frame3'
```

Edit: I managed to make it this:
```
frame0, frame1, frame2, frame3, 
```
With this command:
```
framestring = ''
for x in framefiles:
	framestring += (str(x) + ", ")
```
But how can I remove the last two letter of it?

---

### Post by Def13b on 2008-08-30
I think your after,

', '.join(i for i in ['frame0', 'frame1', 'frame2', 'frame3'])

---

### Post by ghostdog74 on 2008-08-30
> **Def13b said:**
> I think your after,

', '.join(i for i in ['frame0', 'frame1', 'frame2', 'frame3'])

```

', '.join(['frame0', 'frame1', 'frame2', 'frame3'])

```

---

### Post by Def13b on 2008-08-30
hehe, that just dawned on me and was on my way back to edit my post, your just to fast : )

---

### Post by crazyfuturamanoob on 2008-08-30
But I already have string "frame0, frame1, frame2, frame3, ".
**I need to remove the last two letters from it, how can I do that?**
Is that jointhing the answer? What does that join do?

---

### Post by LaRoza on 2008-08-30
> **crazyfuturamanoob said:**
> But I already have string "frame0, frame1, frame2, frame3, ".
**I need to remove the last two letters from it, how can I do that?**
Is that jointhing the answer? What does that join do?

Like this?

```

>>> "string"[:-2]
'stri'
>>> 

```

---

### Post by ghostdog74 on 2008-08-30
the join() converts a list to a string for you. if you want to remove the last 2 then, you can do it during the join using index slicing.
```

','.join(yourlist[:-2])

```
looks like you haven't got your fundamentals right yet.

---

### Post by Bachstelze on 2008-08-30
> **ghostdog74 said:**
> 
looks like you haven't got your fundamentals right yet.

You neither. He wants to remove the last two characters of the final string, so the answer would be as LaRoza suggested :

```
', '.join(list)[:-2]
```

---

### Post by crazyfuturamanoob on 2008-08-30
Thanks. Problem solved.

---

### Post by ghostdog74 on 2008-08-30
> **HymnToLife said:**
> You neither. He wants to remove the last two characters of the final string, so the answer would be as LaRoza suggested :

```
', '.join(list)[:-2]
```
that's a case of mistaken requirements and definitely not my fundamentals. I had thought OP wanted to remove the last 2 elements so I apologize for that. I have known the language for more than 10 yrs so i suggest you don't doubt my knowledge.  string slicing is so basic in Python that its really not an excuse for OP not knowing by now, especially after so many posts.

---

### Post by Wybiral on 2008-08-30
> **HymnToLife said:**
> You neither. He wants to remove the last two characters of the final string, so the answer would be as LaRoza suggested :

```
', '.join(list)[:-2]
```

It seems like they only need to remove the two characters IF they do it the hard way and iterate the list themselves. If they use the join method, they wont have those extra chars on there.

---

### Post by generalguy on 2008-08-30
Join doesn't add the separater after the end element.

[PHP]
In [3]: ", ".join(map(str,range(1,10)))
Out[3]: '1, 2, 3, 4, 5, 6, 7, 8, 9'
[/PHP]


OP:

Use 

[PHP]
", ".join(['frame0', 'frame1', 'frame2', 'frame3'])
[/PHP]

and you will get

[PHP]
'frame0, frame1, frame2, frame3'
[/PHP]

---

### Post by thornmastr on 2008-08-30
> **ghostdog74 said:**
> that's a case of mistaken requirements and definitely not my fundamentals. I had thought OP wanted to remove the last 2 elements so I apologize for that. I have known the language for more than 10 yrs so i suggest you don't doubt my knowledge.  string slicing is so basic in Python that its really not an excuse for OP not knowing by now, especially after so many posts.

Are you saying the total number of posts is indicative of an individuals understanding of 'a specific' programming language? Perhaps Python is the OPS  second language; something on the order of Chinese to English. If you really believe that statement I  think you are acting just a tad pedantic.

---

### Post by pmasiar on 2008-08-30
> **HymnToLife said:**
> You neither. He wants to remove the last two characters of the final string, so the answer would be as LaRoza suggested :

```
', '.join(list)[:-2]
```

You missed something :-)

two last characters ", " to be removed were artifact of the loop, join will add item separator only between items, not at the end. Your suggestion would cut last 2 chars 'e4' of the correct result.

But you can get what you need with loop too:

[php]
frames = ['frame0', 'frame1', 'frame2', 'frame3' ]
joined = frames[0] # to 'prime' resilt

for frame in frames[1:]: 
# skip the first one, already joined
   joined += ', ' + frame
[/php]

Of course ', '.join(alist) is the idiomatic way to do it. And you learned another way :-)

And never ever name variable list (unless you know exactly what you are doing) or any reserved keyword. Strange things might (and will) happen if you do.

---

### Post by ghostdog74 on 2008-08-30
> **thornmastr said:**
> Are you saying the total number of posts is indicative of an individuals understanding of 'a specific' programming language? Perhaps Python is the OPS  second language; something on the order of Chinese to English. If you really believe that statement I  think you are acting just a tad pedantic.
have you really looked at the threads OP started? If you do, you can find one that he says manuals are boring. What impression does this give you?

---

### Post by thornmastr on 2008-08-30
> **ghostdog74 said:**
> have you really looked at the threads OP started? If you do, you can find one that he says manuals are boring. What impression does this give you?

Point taken. As to the impression given.....well, an impression of an inpatient youth, someone too impatient to learn the foundations of one's skills properly; in which case the obvious will out, and it has. Still, people with strong skills are "almost" (notice the quotes) duty bound too help and it is good they do. So I do thank both you and Pmasiar for your many replies.

---

### Post by pmasiar on 2008-08-30
> **thornmastr said:**
> someone too impatient to learn the foundations of one's skills properly; in which case the obvious will out, and it has. Still, people with strong skills are "almost" (notice the quotes) duty bound too help and it is good they do. 

Yes, but I subscribe more to "tough love", aka "don't give fish, give fishing rod". 

If learner will not learn to solve problems by reading and understanding docs and just "figuring it out", she is not gonna be decent hacker. So not forcing such learner to learn the basics, do it right, is not only wasting our time on repeatedly answering trivial questions, it also wastes learner's time, by embarking on a career where success is possible only after changes in attitude - and if such change is required, learner may as well start thinking about it sooner than later.

Learner has no 'right' to our help. We are doing it, paying forward for help we got when we were learning, but "you owe me help" attitude shows not only immaturity but basic misunderstanding how hacker gift culture works. Person with such attitude will not be good member of hacker culture, and need be accultured before including. "Tough love" is about helping to understand the culture learner wants to be part of, not only (trivial) technical matters.

---

### Post by crazyfuturamanoob on 2008-08-31
What does OP mean? Me? I'm just 11, does that explain you anything?

I will only learn by time. I just noticed I have made another similar topic earlier.

I am what I am.

---

### Post by thornmastr on 2008-08-31
> **crazyfuturamanoob said:**
> What does OP mean? Me? I'm just 11, does that explain you anything?

I will only learn by time. I just noticed I have made another similar topic earlier.

I am what I am.

Hi. 

The 'OP' is the first person asking the question. In this case you are the OP.

Your questions quite often can be answered by looking at the manuals you call boring. It is simply a fact that to learn sometimes you have to be bored. It is a part of growing up. Something like learning how to multiply numbers together. That is boring but absolutely necessary. By the time you know Why, you will not even want to ask the question.

If you would take a quick moment to keep in mind that you are not yet "I am what I am." You are wonderfully malleable (look it up in a dictionary) and as easily influenced. Take some time to learn and don't push to understand by osmosis. In another 11 years, you will be more "You are what you are" and hopefully what you are then is an intelligent, gifted, university student who will truly make a contribution of value to both himself/herself and the universe at large.

Best of luck to you,

Robert,

who could easily be your grandfather.

---

### Post by pmasiar on 2008-08-31
For 11 years old, OP, you are pretty adventurous. But as you will soon learn, attitude is not a valid replacement for competence :-) My son was not into 'programming by typing text' at your age, but, using Game Maker, was able to create graphic  games fun enough so his friend wanted to play them.

Even if I consider Python excellent language for beginners, especially young ones like you, you may want to look at Game Maker. You can program games directly, using GUI editor, instead of typing code. The only sad part is that GM is windows only - but we are working to remedy it, see Game Baker project in my sig :-)

---

### Post by crazyfuturamanoob on 2008-08-31
> **pmasiar said:**
> For 11 years old, OP, you are pretty adventurous. But as you will soon learn, attitude is not a valid replacement for competence :-) My son was not into 'programming by typing text' at your age, but, using Game Maker, was able to create graphic  games fun enough so his friend wanted to play them.

Even if I consider Python excellent language for beginners, especially young ones like you, you may want to look at Game Maker. You can program games directly, using GUI editor, instead of typing code. The only sad part is that GM is windows only - but we are working to remedy it, see Game Baker project in my sig :-)
I used to make games with a [SIZE="1"]cracked[/SIZE] Game Maker some time ago, but I didn't like it, because it is so limited.
Pygame is almost the same than GML but I can do a lot more with it. For example, you can't run commands in console with GML, right?

---

