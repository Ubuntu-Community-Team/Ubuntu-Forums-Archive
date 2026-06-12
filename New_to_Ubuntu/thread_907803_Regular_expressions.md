---
title: "Regular expressions"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by dash86no on 2008-09-01
Morning chaps,

I am currently studying for the LPI exams and have come up to regular expressions. 

I have found studying these to be interesting and highly useful. However, I find 2 things a little strange:

1) lack of an AND boolean metacharacter. I would have expected to be able to link parts of a regexp using something like & or + (although I reliaze that these have different meanings) to perform AND operations. So for example (assuming # will become our AND metacharacter):

Look for text with cat AND dog on the same line:

'cat#dog'

At first I thought I could work around this with the following:

'.*cat.*dog.*'

but this will only search out lines on which the characters cat appear before the dog characters; i.e. the search is word order sensitive, which I don't want.

So then I thought of a workaround using 2 greps, so:

grep 'cat' file | grep 'dog' file

Which works but feels to me like a bit of a hack. I just don't understand why there is no AND metachar.

2. More of a mystery to me, however, is the apparent lack of a NOT metachar.

I understand there is the ^ metachar which can me used is conjunction with square brackets to negate the appearance of certain character combinations in search strings:

'[^dog]'

but the frustrating thing about this is that the literal characters "d" "o" and "g" are individually considered and not "dog" as a whole.

So then I thought of adding -v (in the case of grep) to negate the entire regexp. This works great for this kind of search:

find all sentences that do not have dog OR cat in the sentence

grep -v '.*dog|cat.* 

but if I want to do this kind of thing I am completely stuck: 

find all sentences that do NOT have dog OR do have cat in the sentence

This is where i'd really like to have a ! metachar to negate things: eg:

'!(dog)|cat'

but this doesn't seem to exist!

If anyone could help (especially with point 2) I would be very grateful.

Cheers!

---

### Post by sardion on 2008-09-01
I think you are misunderstanding the purpose of regexes.

They are not a programming language in and of themselves.  Both conjunction and negation are logical operators (as is disjunction).  Regexes do not perform logical processing, they perform expression matching.

To accomplish what you are trying to do, you need to combine regexes with some sort of logical processing (the most commonly used is probably perl or possibly awk).

The reasons for why regexes are the way they are go back to the theory of logic that predated computer science entirely (the * in regexes is the Kleene star which he invented before Turing and Church had done their work).

I believe that if you read more about them, you will start to understand why it is desirable to separate the pattern matching from the logic.

I would also encourage you to look into using perl and awk with regexes.  That is a very common programming technique for quick little scripts.

---

### Post by dash86no on 2008-09-01
> **sardion said:**
> I think you are misunderstanding the purpose of regexes.

They are not a programming language in and of themselves.  Both conjunction and negation are logical operators (as is disjunction).  Regexes do not perform logical processing, they perform expression matching.

To accomplish what you are trying to do, you need to combine regexes with some sort of logical processing (the most commonly used is probably perl or possibly awk).

The reasons for why regexes are the way they are go back to the theory of logic that predated computer science entirely (the * in regexes is the Kleene star which he invented before Turing and Church had done their work).

I believe that if you read more about them, you will start to understand why it is desirable to separate the pattern matching from the logic.

I would also encourage you to look into using perl and awk with regexes.  That is a very common programming technique for quick little scripts.

sardion,

Many thanks for your reply, that makes a lot of sense. 

I will take your advice and look into pearl/awk etc. 

One slightly confusing thing for me though, does the existence of the OR metachar | not contradict the idea of the pattern matching being separate from the logic?

Thanks,

---

### Post by ghostdog74 on 2008-09-02
you can use awk to perform AND function
```

awk '/pattern1/ && /pattern2/' file

```

---

