---
title: "&quot;De-Jumble&quot; Python script: how can I make it more efficient?"
date: 2008-01-01
forum: Programming Talk
---

### Post by martinw89 on 2008-01-01
Hello all,
I've been doing the [Python Challenge]("http://www.pythonchallenge.com"), which by the way is an awesome way to get familiar with Python [/plug].  I decided to whip up a quick Python script to solve those "jumble" puzzles in the newspaper.  Following is the code.  The dictionary file referenced in the file is from "12dicts" at [http://wordlist.sourceforge.net/](http://wordlist.sourceforge.net/).  I didn't include it in this post.```
#!/usr/bin/env python
'''Solves Jumble puzzles.

Uses regexes to find possible letter arrangements by matching them with
a dictionary file.
Made with Vim and Python 2.5.'''

import re
import sys

def string_to_list(string):
    '''Takes a string and appends each character to a list.'''
    letter_list = []
    for char_num in range(len(string)):
        letter_list.append(string[char_num])
    letter_list.sort()
    return letter_list

def dejumble(word):
    '''Solves "jumble" puzzles.
    
    "word" is the letters to be "de-jumbled.'''
#The regular expression to match any order of the letter in the word.
    regex = re.compile("([" + word + "]{" + repr(len(word)) + "})")
#Save the dictionary file to a variable."
    dictionary = open("12dicts/5desk.txt", "r").read()
#Find all matches.  Does not match EACH character though.
    possible_match_list = regex.findall(dictionary)
    word_letters = string_to_list(word)
    match_list = []
#Now only save matches that are the same characters as the original.
    for word_num in range(len(possible_match_list)):
        match_letters = string_to_list(possible_match_list[word_num])
        if match_letters == word_letters:
            match_list.append(possible_match_list[word_num])
    match_list.sort()
#Remove duplicates.
    for match in match_list:
        match_num = match_list.index(match)
        try:
            while match == match_list[match_num + 1]:
                del match_list[match_num + 1]
        except IndexError:
            pass
#Print the matches if there are any.
    if len(match_list) != 0:
        print ""
        print "*****Possible matches:*****"
        for match_num in range(len(match_list)):
            print repr(match_num + 1) + ":", match_list[match_num]
        print "*****End of Possible Matches*****"
        print ""
    else:
        print "Sorry, no matches found.\n"

def main():
    print "Enter the word to dejumble (type 'quit' to exit)"
    word = raw_input("Word: ")
    if word != "quit":
        dejumble(word)
        main()
    else:
        sys.exit(0)

if __name__ == "__main__":
    main()

```So, what I'm wondering is how can I make the code more efficient?  This is just the most basic version that put the logic in code, I'm sure I could make this go a lot faster.  Thanks for any suggestions, I bet this will get interesting to see how efficient it can get (without just porting to C :))

**Edit:**  Thanks for the help so far everyone, this is why learning Python is great, everyone is nice!  Also, most recent code will be in each post in which I change something.

---

### Post by ghostdog74 on 2008-01-01
> 
```

def string_to_list(string):
    '''Takes a string and appends each character to a list.'''
    letter_list = []
    for char_num in range(len(string)):
        letter_list.append(string[char_num])
    letter_list.sort()
    return letter_list

```

this is a long winded way of saying 
```

a=list(string_to_list)
a.sort()

```

---

### Post by martinw89 on 2008-01-01
](*,) I KNEW there was a string-list function in Python.  Thanks!  That saved a few lines.
OK, the new code:
```
#!/usr/bin/env python
'''Solves Jumble puzzles.

Uses regexes to find possible letter arrangements by matching them with
a dictionary file.
Made with Python 2.5.'''

import re
import sys

def dejumble(word):
    '''Solves "jumble" puzzles.
    
    "word" is the letters to be "de-jumbled.'''
#The regular expression to match any order of the letter in the word.
    regex = re.compile("([" + word + "]{" + repr(len(word)) + "})")
#Save the dictionary file to a variable."
    dictionary = open("12dicts/5desk.txt", "r").read()
#Find all matches.  Does not match EACH character though.
    possible_match_list = regex.findall(dictionary)
    word_letters = list(word)
    word_letters.sort()
    match_list = []
#Now only save matches that are the same characters as the original.
    for word_num in range(len(possible_match_list)):
        match_letters = list(possible_match_list[word_num])
        match_letters.sort()
        if match_letters == word_letters:
            match_list.append(possible_match_list[word_num])
    match_list.sort()
#Remove duplicates.
    for match in match_list:
        match_num = match_list.index(match)
        try:
            while match == match_list[match_num + 1]:
                del match_list[match_num + 1]
        except IndexError:
            pass
#Print the matches if there are any.
    if len(match_list) != 0:
        print ""
        print "*****Possible matches:*****"
        for match_num in range(len(match_list)):
            print repr(match_num + 1) + ":", match_list[match_num]
        print "*****End of Possible Matches*****"
        print ""
    else:
        print "Sorry, no matches found.\n"

def main():
    print "Enter the word to dejumble (type 'quit' to exit)"
    word = raw_input("Word: ")
    if word != "quit":
        dejumble(word)
        main()
    else:
        sys.exit(0)

if __name__ == "__main__":
    main()
```

---

### Post by engla on 2008-01-01
> **martinw89 said:**
> 
```

#Now only save matches that are the same characters as the original.
    for word_num in range(len(possible_match_list)):
        match_letters = string_to_list(possible_match_list[word_num])
        if match_letters == word_letters:
            match_list.append(possible_match_list[word_num])

```

This is quite unpythonic. It is simply more natural to use the real **for** idiom.
```

#Now only save matches that are the same characters as the original.
    for word in possible_match_list:
        match_letters = string_to_list(word)
        if match_letters == word_letters:
            match_list.append(word)
```

or even a list comprehension

```

    match_list = [word for word in possible_match_list if list(sorted(word)) == word_letters]
```

However, this has no big impact on performance. If there are many duplicates, it might be better to use tuples instead of lists and use a set as container, to automatically keep all entries unique.

---

### Post by martinw89 on 2008-01-01
That's a good point, after reading some optimization articles I got it in my head it's faster to use index numbers to manipulate lists than items (which makes sense).  However in this case I'm not doing anything major and the list is very tiny, so the readability is worth it.  Most recent code:```
#!/usr/bin/env python
'''Solves Jumble puzzles.

Uses regexes to find possible letter arrangements by matching them with
a dictionary file.
Made with Vim and Python 2.5.'''

import re
import sys

def dejumble(word):
    '''Solves "jumble" puzzles.
    
    "word" is the letters to be "de-jumbled.'''
#The regular expression to match any order of the letter in the word.
    regex = re.compile("([" + word + "]{" + repr(len(word)) + "})")
#Save the dictionary file to a variable."
    dictionary = open("12dicts/5desk.txt", "r").read()
#Find all matches.  Does not match EACH character though.
    possible_match_list = regex.findall(dictionary)
    word_letters = list(word)
    word_letters.sort()
    match_list = []
#Now only save matches that are the same characters as the original.
    for match in possible_match_list:
        match_letters = list(match)
        match_letters.sort()
        if match_letters == word_letters:
            match_list.append(match)
    match_list.sort()
#Remove duplicates.
    for match in match_list:
        match_num = match_list.index(match)
        try:
            while match == match_list[match_num + 1]:
                del match_list[match_num + 1]
        except IndexError:
            pass
#Print the matches if there are any.
    if len(match_list) != 0:
        print ""
        print "*****Possible matches:*****"
        for match_num in range(len(match_list)):
            print repr(match_num + 1) + ":", match_list[match_num]
        print "*****End of Possible Matches*****"
        print ""
    else:
        print "Sorry, no matches found.\n"

def main():
    print "Enter the word to dejumble (type 'quit' to exit)"
    word = raw_input("Word: ")
    if word != "quit":
        dejumble(word)
        main()
    else:
        sys.exit(0)

if __name__ == "__main__":
    main()

```

---

### Post by Nekiruhs on 2008-01-01
> **engla said:**
> 
or even a list comprehension

```

    match_list = [word for word in possible_match_list if list(sorted(word)) == word_letters]
```

Can you explain how a list comprehension works, I've heard a lot about Python's list comprehensions but have no idea what one is and how to make/use one. Thank you.

---

### Post by pmasiar on 2008-01-02
Google knows all about [http://www.google.com/search?q=python+list+comprehension:](http://www.google.com/search?q=python+list+comprehension:)
- [http://www.python.org/dev/peps/pep-0202/](http://www.python.org/dev/peps/pep-0202/)
- [http://www.secnetix.de/olli/Python/list_comprehensions.hawk](http://www.secnetix.de/olli/Python/list_comprehensions.hawk)
- [http://www.network-theory.co.uk/docs/pytut/ListComprehensions.html](http://www.network-theory.co.uk/docs/pytut/ListComprehensions.html)
- [http://en.wikipedia.org/wiki/List_comprehension](http://en.wikipedia.org/wiki/List_comprehension)

---

### Post by ghostdog74 on 2008-01-02
> **Nekiruhs said:**
> Can you explain how a list comprehension works, I've heard a lot about Python's list comprehensions but have no idea what one is and how to make/use one. Thank you.

Read the tutorial please. Its [there ]("http://docs.python.org/tut/node7.html"). Read from start till the end, and then carry on reading the library reference plus the tons of documents at the official doc site.

---

### Post by engla on 2008-01-02
> **martinw89 said:**
> That's a good point, after reading some optimization articles I got it in my head it's faster to use index numbers to manipulate lists than items (which makes sense).  However in this case I'm not doing anything major and the list is very tiny, so the readability is worth it.  Most recent code:

One thing I've seen on the mailing list is that they generally work for making the  natural use the fastest! Still I don't think it should matter. Anyhow you have to traverse the whole list, and it's been optimized for that, it's a very common case.

Anyway, use xrange instead of range for long iterations.. Range creates a list as long as the number of iteration steps. Otoh xrange just returns an iterator to do the same job (when using it for iteration), so it has no memory overhead or time to precompute the list. This again has no impact for normal small ranges..

---

### Post by popch on 2008-01-02
You could transform the word list into a mapping sorted_letters->list_of_words 

where sorted_letters is a string containing all the letters in a word in ascending order 

and list_of_words is a list of all words the letters of which yield the same sorted_letter

In order to unjumble a word, sort its letters, look up sorted_letters

Transforming the straight word list into the mapping would take some time. So does, however, matching regexp with each word in the list. Preparing the original word list also took time which is not taken into account for measuring the unjumbling speed.

---

### Post by evymetal on 2008-01-03
* Using C would not speed this up much, I assume most of the time is being spent in the regular expression, and once it's compiled you're not going to get it any faster no matter what language you're calling it in. This is a perfect example of why it's often not worth writing something in C.

* if you are doing this with loads of jumbled words per program execution then it would by much faster to load the dictionary into RAM earlier (in the main loop) and just pass it to the function (the data is sent by reference so it's barely any overhead)

* BTW, I would solve this problem by building an inverted index on unigrams within a word (similarly to what popch suggested). 

e.g.
"ate" would become:
[1,0,0,0,1,..... ]
(1 "a", 1 "e" etc)

Then store these as keys for a "dict" or similar (perhaps a [cleverly?] written tree to save memory), which would have the list of words as it's data.

Once this is done the function just has to look down 26 levels for each jumbled word, and return the list it finds. 

(it should be possible to optimise the suggestion above to take less than 26 levels on average by using a better tree like structure - but I'm not sure if it's faster to use a python dict, they're well optimised internally - at least in the standard (C) Python)

initialisation will take much longer though. (I'm normally doing server based stuff so I don't really care about initialisation)

---

