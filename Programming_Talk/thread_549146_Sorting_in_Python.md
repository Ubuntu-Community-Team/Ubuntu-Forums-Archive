---
title: "Sorting in Python"
date: 2007-09-12
forum: Programming Talk
---

### Post by Catsworth on 2007-09-12
Hi Guys,

Another Python problem I'm afraid :)

Have the following code:

```

    for word in listIn:
        characters = []
        characters = list(word)
        sortedCharacters = []
        sortedCharacters = characters.sort()
        for letter in sortedCharacters:
            print letter

```

listIn is a list of words.  The idea is that the code should take that list of words, and then iterated through the list.  Each word in the list gets split into it's separate letters, which are then assigned to a list (called characters).

From there the code should then sort that list of characters.  It should then print out the letters.

I have got it splitting the words into letters, and it sorts them just fine.  When I try to iterate through that list with the 'for letter in sortedCharacters' line I get the following error:

```
    for letter in list(sortedCharacters):
TypeError: iteration over non-sequence

```

Anybody able to give me a hint as to what I've done wrong?  Would I be right in thinking that I've used a list where perhaps I shouldn't have?  Or am I totally barking up the wrong tree here?

Thanks.

---

### Post by cwaldbieser on 2007-09-12
The sort method is in-place.  It does not return a new list.

---

### Post by Catsworth on 2007-09-12
Gotcha.....

So, if I use:

```
sortedCharacters = sorted(characters)
```

I should be ok :)

---

### Post by pmasiar on 2007-09-12
[php]
    for word in listIn:
        word.sort()
        for letter in word:
            print letter
[/php]

---

