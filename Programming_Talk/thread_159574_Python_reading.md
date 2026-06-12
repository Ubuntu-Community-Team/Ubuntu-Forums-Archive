---
title: "Python reading"
date: 2006-04-13
forum: Programming Talk
---

### Post by Ubuntuud on 2006-04-13
Hi, I am making a program with python to help me learn  my words for my languages. I have already written it, but I would like to store the questions and answers in an other file.

This (an example):

```
questions = ['apple', 'cow', 'cows', 'pigs']
answers = ['appel', 'koe', 'koeien', 'varkens']
```

is in the second file should be readable in the first file.
I think I need to do something with pickle but I don't seem to figure it out...

If you would like to see the rest of the code, just ask. I thought it might just anoy you.
Thanks in advance!

---

### Post by gord on 2006-04-13
if you just want it to be quick and simple, you might as well just store the questios and answers in that format, in a second file called QA.py, then simply import it at the start of your code, just make sure its on your import path (put it in the same directory as the rest of the code, or one of the places in sys.path)
```
import QA
```
then you can access the data by prefixing it with "QA."
```
QA.questions[2]
```


you could go through the hastle of pickling the data but it doesn't seem nessasesy for a small home project :)

---

### Post by thumper on 2006-04-13
I'd suggest using a dictionary though.  You might find that lining up the questions and answers gets a bit tough once there are more than just a few.

```
words = { 'apple':'appel', 'cow':'koe', 'cows':'koeien', 'pigs':'varkens' }

```

Imported the same way as above.

---

### Post by Ubuntuud on 2006-04-13
I did that as well, but it is harder to random that. Or do you know a way to shuffle it? Thanks!

---

### Post by thumper on 2006-04-13
Use the same randomisation technique on the keys to the dictionary.
```
>>> words = { 'apple':'appel', 'cow':'koe', 'cows':'koeien', 'pigs':'varkens' }
>>> words.keys()
['cows', 'pigs', 'apple', 'cow']
>>>

```

---

### Post by Ubuntuud on 2006-04-13
OK. Thanks! I'll go and try that out now.

---

### Post by Ubuntuud on 2006-04-13
Uhm... I'm having a little problem with random.shuffle([x, y, z])

this:

```
print random.shuffle(QA2.words.keys())
```

outputs "None"

What should I do?

For your information:
QA2 is the file I stored:
```
words = {'apple': 'appel',...,'pigs': 'varkens'}
```

---

### Post by dabear on 2006-04-13
random.shuffle sorts the keys directly, so try this:
```

import random
#here, get from file instead
words = {'apple': 'appel','pigs': 'varkens'}
keys = words.keys()
print keys
random.shuffle(keys)
print keys

```

---

### Post by Ubuntuud on 2006-04-14
OK. Thanks, I'll do so.

---

### Post by Ubuntuud on 2006-04-14
Erhm... when I do that I loose all conection with the iteritems and dictionary. So when I do:
```
for q, a in words.iteritems:
...
```
They are still in the same sequence.
But maybe it works if I make an always the same seed and shuffle both, keys and iteritems.

---

### Post by Ubuntuud on 2006-04-14
Uhh, I have a little update. The dictionary seems to shuffle itself. This:
```
words = {'le gardien': 'de oppasser', 'la naissance': 'de geboorte', 'durer': 'duren', 'le vol': 'de diefstal', 'alerter': 'waarschuwen', 'le bruit': 'het geluid'}
```
comes in the following sequence:  5 1 2 6 4 3.
It isn't alfabetical: al - le - la - le - le - la - du
nor the sequence I made. Is there a explanation and maybe a way to make it really random, because it gives the same sequence all the time.

---

### Post by fng on 2006-04-14
i use this for a random shuffle : 

```

import random

    def __init__(self):
        '''Initializes a new deck of cards.'''

        self.cards = []

    def countCards(self):
        '''Counts the amount of cards in the deck.'''

        return len(self.cards)

    def shuffle(self):
        '''This shuffles the cards in the deck in random order.'''

        nCards = self.countCards()

        for i in range(nCards):
            j = random.randrange(nCards)

            self.cards[i], self.cards[j] = self.cards[j], self.cards[i]

```

note the above is a copy/paste from a couple of functions from an actual source.  It won't work out of the box like this. You'll have to rewrite some parts :)  But you'll get the idea.

---

### Post by Ubuntuud on 2006-04-14
OK. I'll try that, thanks! But does this work for a dictionary? (I haven't tried it yet)

---

### Post by llonesmiz on 2006-04-14
```
import random
#here, get from file instead
dictionary = {'apple': 'appel','pigs': 'varkens'}
keys = dictionary.keys()
random.shuffle(keys)
for word in keys:
    print ("How do you say "+word+" in Dutch?")
    raw_input("Press any key to see the answer...")
    print "The answer is "+dictionary[word]

```

A dictionary can't be ordered because they have no order. To access the entries randomly you have to get the "keys" (a list, that can be ordered) and then shuffle them. Then, with the for loop you can get the pairs question-answer using word-dictionary[word].

---

### Post by Ubuntuud on 2006-04-15
OK. Thanks, that shouldn't be to hard to implent. Thanks for all the trouble!

---

### Post by Ubuntuud on 2006-04-15
I have another question, is there a way to write dictionaries to another file, or the file itself. So that when I enter something with this code:

```
def enter(words):
   g = 'hello' # Doesn't matter what this is
   while g != 'quit':
      q = (raw_input('What word would you like to add? '))
      a = (raw_input('What does that mean? '))
      words[q] = a
```

that that will be saved when I exit. Since it isn't a string, I don't think it'll be easy, or can this be done in a similar way as the random?

---

### Post by llonesmiz on 2006-04-15
If you do "repr(words)" you'll get a string with the contents of the dictionary. You could then save that string to a file.

---

### Post by Ubuntuud on 2006-04-16
Thanks, you make me feel stupid...

---

