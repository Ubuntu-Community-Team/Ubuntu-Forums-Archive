---
title: "[SOLVED] Python: String Operations: Removing whitespace..."
date: 2008-08-10
forum: Programming Talk
---

### Post by Nebelhom on 2008-08-10
Hi,

as a part of teaching myself python (I have no prior exposure to computer languages), I decided to try and write a little spanish vocabulary tester for me (I worked through Allen Downey's "How to think like a (Python) Programmer" - [http://www.greenteapress.com/thinkpython/html/](http://www.greenteapress.com/thinkpython/html/)

I broke this project up into little parts to work on separately (seemed to be a good idea at the time). The part I am currently working on is to take a list of words copied and pasted into a text file in the format:

english word  -  spanish word (or vice versa doesn't really matter)

(This is my test source:
[http://www.braser.com/spanish-comida/spanish-food-ab.html](http://www.braser.com/spanish-comida/spanish-food-ab.html))

example text:

[list]    * acorn - bellota
    * add - añadir
    * almonds -almendras
    * aubergine - berenjena
    * avocado - aguacate


    * bacon - beicón
    * bake - cocer al horno
    * baking powder - levadura (en polvo)[/list]

I thought this was sensible as most online dictionaries come in this form or similar ;)

I have two problems with this so far, the main one is the whitespace. I will give you first the code and then the output to demonstrate the problem (scroll past code to find the question).

```
def read_vocab_txt(filename):
    """Reads files and gives a list of
    'Word - Word' from any two word line
    removing all special characters in the process"""
    
    openfile = open(filename, 'r')
    vocabulary_list = []
    for crude_line in openfile:
        line = crude_line.strip() # should remove all whitespace before and after the line
        char = []
        for letter in line:
            if letter in string.replace(string.punctuation, '-', ''): # removes all special chars apart from separator
                letter.replace(letter, '')
            else:
                char.append(letter)
                word = string.join(char, '') # creates the word
        vocabulary_list.append(word)
    return vocabulary_list

# See list output below to see what I get there

def vocab_list2dict(filename):
    """Converts a potential vocabulary list into
    a dictionary of corresponding values"""

    startlist = read_vocab_txt(filename) # creating the above list
    vocabulary = {}
    for entry in startlist:
        result = entry.split('-') # This separates the two words at the separator '-' to give a two item list
        if result[0] not in vocabulary:
            vocabulary[result[0]] = result[1]
        else:
            vocabulary[result[0]]+= result[1]
    return vocabulary


```

the output for read_vocab_txt is(an excerpt):

```
[' acorn - bellota', ' add - a\xc3\xb1adir', ' almonds -almendras', ' anchovy - anchoa', ' apple - manzana', ' arrange - poner', ' artichoke -alcachofa', ' asparagus - esp\xc3\xa1rrago', ' aubergine - berenjena', ' avocado - aguacate', ' avocado - aguacate', ' avocado - aguacate', ' bacon - beic\xc3\xb3n', ' bake - cocer al horno', ' baking powder - levadura en polvo']
```

The main points being the space before and after the part of the string (e.g. ' acorn - bellota')  I'm interested in and also the fact that 'avocado - aguacate' occurrs 3 times (probably because it is the last line in A vocabulary and then two free lines and then B starts).

These problems just transfer to the second part as well or occur again when string.split() is used, which makes it annoying since when asking the vocabulary I don't want to always remember to put a whitespace before and after the answer.

How can I remove this whitespace to just give me "the word", i.e. 'acorn' or 'bellota'? No spaces.

string.strip() does not remove it and string.replace(' ', '') doesn't do anything either :(

If anyone could give me tips on this I would be very grateful. Also I know this is far from finished and the code probably is a bit clunky. I focussed on writing the functions first and tackle each small problem before it becomes a big one several steps down the line. I haven't thought about using OOP or anything like that yet (maybe later). So sorry if it is a bit crude.
Oh and also, if you know how to write the same code in a more elegant and readable fashion, please let me know. I'd be more than happy to adapt it as long as it helps me writing better code. 

Thanks already guys.

Nebelhom

P.S. The second problem is more fundamental and concerns separating columns of words without a separator like '-', which I think is for another time and maybe I can think of something about that in the mean time :)

P.P.S. I just realised how long this post has gotten. Sorry :(... and thanks for your patience with my rantings. just wanted to be thorough.

---

### Post by pmasiar on 2008-08-10
Next time, please little less irrelevant background. But you correctly stated your skill level, seems like you did read sticky about how to ask questions :-) 

> **Nebelhom said:**
> 
string.strip() does not remove it and string.replace(' ', '') doesn't do anything either 

Strings are immutable. Characters are not replaced, but new string with replacement is created, you need to assign it to some variable.

Good way to test such functionality is try is in Python shell: results are printed automagically for you.
> I haven't thought about using OOP or anything like that yet (maybe later). 

Don't. OOP can wait until after you mastered basics.

> Oh and also, if you know how to write the same code in a more elegant and readable fashion, please let me know. I'd be more than happy to adapt it as long as it helps me writing better code. 

Read PlanetPython.org , read code of other people, and summary of python mailing list (I read it via LWN.net, linux weekly news). After all years, I will weekly learn neat tricks.

---

### Post by Nebelhom on 2008-08-10
Yea, sorry about that. by the last P.S. one can guess that I wasn't sure if that is too much information or not. I will try and sum it up more next time :oops:

It worked! For some weird and wonderful reason, I must have forgotten about that string immutability thing :(. 

And thanks for the pointers! (planetpython is a bit of an overkill so far but that's the challenge :popcorn:)

---

