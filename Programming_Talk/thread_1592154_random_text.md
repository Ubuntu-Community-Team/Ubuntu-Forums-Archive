---
title: "random text"
date: 2010-10-10
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-10-10
i recently made a file sorting python program that goes through the text file you input and sorts the words by length, alphabetically, and picks out the sentences. Then, just for the fun of it i made a random text generator to create random text for my other program to sort. 

Im pretty much a programming beginner... can you tell me what i could do more efficiently in this program?its not very precise, and kinda complicated for something like that. i feel like theres a way easier way to do the same task. 
It's interesting to compare what i would naturally think of (since im completely untrained) to what others would think of, so if you would like to you can post your own programs from the same task. 

thanks

---

### Post by ziekfiguur on 2010-10-10
One thing i noticed is that you store a lot of information in the words_sentences list while you could output directly.

Another thing is that you initialize some variables (wps, number and total) twice or more times.

Also, in line 36 you do:
```

words_sentences[x] = ['' for y in range(0,words_sentences[x]-1)] 

```But, range returns [x, y) this means range(0, 10) will return [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] so the -1 is not necessary.

P.S. Great you are learning to program! Don't let it get you down if things don't work right away but keep going. In the end it will totally be worth any frustration you will have while learning.

P.P.S. My version doesn't usually give the exact number of words that were requested. However, I'm sure you can fix that quite easily.

---

### Post by flyingsliverfin on 2010-10-10
my one doesnt give the exact number either. your version is a lot shorter than mine! thanks for showing me the .normalvariate im sure that will come in handy in future programs.

my file sorter also needs improvement, probably more than the text generator. i see that i could have written the stuff directly rather than storing it... i feel like there are better ways to do lines 40-51 and 70-79.

---

### Post by ziekfiguur on 2010-10-11
Regular expressions may seem confusing at first. But, once you understand them, they can really make your life easier. 
I would also advice you to take a good look at the python standard library, lots of functions have very useful optional parameters that can save you a lot of work if you use them.
Some examples:
string.find can take an indices that indicates where to start and stop searching, so you could have done
```

place = 0
while True:
    prevplace = place
    place = w.find('.', prevplace) # will search only after prevplace
    if place == -1:
        break
    # do something

```another example is list.sort() that can take a function it will use to compare the elements in the list, i have used that in my version.

For working with filenames the os.path module usually is not necessary but it may save you some work and it is guaranteed to work cross-platform which is allways nice.

If you have any questions feel free to send me a private message.

---

