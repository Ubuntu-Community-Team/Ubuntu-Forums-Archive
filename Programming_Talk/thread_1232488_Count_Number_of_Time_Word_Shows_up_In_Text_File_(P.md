---
title: "Count Number of Time Word Shows up In Text File (Python)"
date: 2009-08-05
forum: Programming Talk
---

### Post by bren21 on 2009-08-05
I'm trying to create a mad libs program to help me with learning a language using python. So far I am able to get the program to read from a list of nouns, verbs, adverbs, and adjectives and get it to make a somewhat understandable sentence (this is all I'm trying to do). I made a list of formats such as 'The adjective noun verb adverb.' and got python to successfully choose a random word from each list and insert it. The problem I ran into is when I want to use more than one noun or verb, such as 'The noun verb adjective noun adverb.' since python inserts the same noun twice. I figured I would just use a while loop to get around this, however I need to know how many times the word 'noun' is in the document. How would I do this?

I'm not too good at programming, so I'm sure there are a bunch of easier ways to do what I'm doing. Here's my code so far in case you want to see it. 

```
#!/usr/bin/python
from random import choice
from collections import defaultdict

###EMPTY LISTS###
nounl = []
verbl = []
adjl = []
advl = []
forml = []

###LIST FILES###
nouns = open('src/nouns.txt', 'r')
verbs = open('src/verbs.txt', 'r')
adj = open('src/adjectives.txt', 'r')
adv = open('src/adverbs.txt', 'r')
form = open('src/formats.txt', 'r')
###IMPORTS THE LISTS###
for line in nouns:
	nounl.append(line.rstrip('\n'));
for line in verbs:
	verbl.append(line.rstrip('\n'));
for line in adj:
	adjl.append(line.rstrip('\n'));
for line in adv:
	advl.append(line.rstrip('\n'));
for line in form:
	forml.append(line.rstrip('\n'));


dnoun = choice(nounl)
dverb =  choice(verbl)
dadj =  choice(adjl)
dadv =  choice(advl)

print 'The ' + choice(adjl) + ' ' + choice(nounl) + ' ' + choice(verbl) + ' ' + choice(advl) + '.'

###THE FORMATER###
if raw_input('Do you want to make up your own format? [y/N] ') == 'y':
	format = raw_input('What format do you want? ');

else:
	format = choice(forml);


format = format.replace('noun', dnoun)
format = format.replace('verb', dverb)
format = format.replace('adj', dadj)
format = format.replace('adv', dadj)

print format



while True:
	format.replace('noun', dnoun, [1])
	dnoun = choice(nounl)
	if nounnumber == 0:  ###How do I get this number?
		break;
	else:
		format.replace('noun', dnoun, [1])
```

---

### Post by Tony Flury on 2009-08-05
Method 1 
Lateral thinking sort of  - why not take a copy of the string before and compare it with the string after the replace - and if they are the same then the replace has had no impacts and you have run out of things to replace.

Method 2
use the find method to see if there is "noun" available to be replaced before you try to replace it.

Method 3
Use the count method to count how many instances of "noun" exist in the string.


[http://docs.python.org/library/stdtypes.html#string-methods](http://docs.python.org/library/stdtypes.html#string-methods)

---

### Post by pepperphd on 2009-08-05
I don't know Python, but if you can read C, here is something I made that does exactly what your title says.

[php]#include <iostream>
#include <vector>
#include <string>
#include <sstream>
#include <ctype.h>

using namespace std;

inline string get_file_contents(const string filename);
inline void find_term(const string term, const string file_contents);
inline void print_results(const string term, vector<unsigned int> lines_found_on);

int main(const int argc, const char *argv[])
{
    for(; argc != 3; abort()) cout << "usage: " << argv[0] << " [filename] [search term]" << endl;
    
    find_term(argv[2], get_file_contents(argv[1]));
    return 0;
}

inline string get_file_contents(const string filename)
{
    FILE             *file_to_search = NULL;

    string            file_contents = "";

    register char         ch;

    unsigned register int     current_line = 1;


    for(; !(file_to_search = fopen(filename.c_str(), "rb") ); abort()) cout << "check filename" << endl;

    cout << current_line << '\t';
    while( ( ch = fgetc(file_to_search) ) != EOF )
    {
        file_contents += ch;
        cout << ch;
        if(ch == '\n') cout << ++current_line << '\t';    
    }

    fclose(file_to_search);

    return file_contents;
}

inline void find_term(const string term, const string file_contents) 
{                        
    unsigned static int    i,
                term_length,
                term_compare;
    
    unsigned register int     current_line = 1;

    vector<unsigned int>     lines_found_on;

    
    for(current_line = 1; file_contents[i]; i++)
    {
        if(file_contents[i] == '\n') current_line++;

        if(file_contents[i] == term[0])
        {    
            for(term_length = term_compare = 0; term[term_length]; term_length++)
                if(term[term_length] == file_contents[i + term_length])    term_compare++;                
            
            if(term_compare == term_length)    lines_found_on.push_back(current_line);
        }
    }
    print_results(term, lines_found_on);
}

inline void print_results(const string term, vector<unsigned int> lines_found_on)
{    
    for(; !lines_found_on.size(); exit(0))
        cout << endl <<
        endl <<
        "term not found" << endl;

    stringstream found_on;

    string found_on_s;

    vector<unsigned int>::iterator p;

    cout << endl <<
    endl <<
    term << " was found " << lines_found_on.size() << " time(s)" <<    " on line(s): ";    
    for(p = lines_found_on.begin(); p != lines_found_on.end(); p++) found_on << *p << ", ";
    found_on_s = found_on.str();
    found_on_s.erase(found_on_s.end() - 2);
    cout << found_on_s << endl;
}[/php]

---

### Post by tom66 on 2009-08-05
```

string = "word anyone here word, dude word word www internet python is awesome lorum ipsum word"
key = "word"

def count_words(string, key):
	return float(len(string) - len(string.replace(key, ''))) / float(len(key))

num = count_words(string, key)
print "string '%s' occurs %d times in string '%s'." % (key, num, string)

```

This works by removing all instances of *key* from the *string*, measuring the difference, and then dividing the difference by the length of the *key*.

---

### Post by Can+~ on 2009-08-05
[PHP]#!/usr/bin/env python

import random

class Randict(dict):
	def __getitem__(self, key):
		return random.choice(dict.__getitem__(self, key))

wordlist = Randict()

wordlist["noun"] = ("sandiwch", "dog")
wordlist["adj"] = ("warm", "sad")
wordlist["verb"] = ("jump", "run", "eat")

print "Last time I saw a %(noun)s was when I was %(verb)sing a %(noun)s" % wordlist[/PHP]

Overloaded the __getitem__ method from the Dictionary class to provide random selection from an iterable.

You could also use a set() as the container for your data, as a set is a collection of unique values.

---

### Post by Reiger on 2009-08-05
EDIT: You couldn't simply read the file line by line and split around occurrences of <word> then count how many parts you have left -1 (per line)?
EDIT2: Alternatively and by far the more elegant solution is to use a string tokenizer function.

---

### Post by bren21 on 2009-08-05
> **tom66 said:**
> ```

string = "word anyone here word, dude word word www internet python is awesome lorum ipsum word"
key = "word"

def count_words(string, key):
	return float(len(string) - len(string.replace(key, ''))) / float(len(key))

num = count_words(string, key)
print "string '%s' occurs %d times in string '%s'." % (key, num, string)

```

This works by removing all instances of *key* from the *string*, measuring the difference, and then dividing the difference by the length of the *key*.

This is exactly what I wanted. Thanks for all the suggestions.

---

### Post by tom66 on 2009-08-05
Actually I just noticed there's a python standard method for doing what I posted... it's called str.count. [http://docs.python.org/library/stdtypes.html#str.count](http://docs.python.org/library/stdtypes.html#str.count)

---

### Post by nvteighen on 2009-08-06
> **tom66 said:**
> Actually I just noticed there's a python standard method for doing what I posted... it's called str.count. [http://docs.python.org/library/stdtypes.html#str.count](http://docs.python.org/library/stdtypes.html#str.count)
Which is what Tony Flury already told you about... :p

---

### Post by tom66 on 2009-08-06
Now you point it out I see...

---

### Post by Tony Flury on 2009-08-06
I was going to say - i told you so - but decided that would be churlish.

Actually I like Can+~'s lambda function solution - if only I understood how/why it worked.

Edit : Ignore that - it is not a lambda function at all - misread it.

---

### Post by Bodsda on 2009-08-06
I know this problem has already been answered, but I just wanted to share how I would count the number of 'someword' in a string. I have not looked at the linked string count module btw.

```

string = "I am dude a string dude and dude this dude dude is really starting to dude me dufe off"
num = 0
for i in string.split():
    if i == "dude":
        num += 1
print "There are %s instances of 'dude' in '%s'" % (num, string)

```
That was just the first thing that came to mind.

Thanks,
Bodsda

---

### Post by Can+~ on 2009-08-06
> **Tony Flury said:**
> Actually I like Can+~'s lambda function solution - if only I understood how/why it worked.

Edit : Ignore that - it is not a lambda function at all - misread it.

Correct, it's not lambda function, but method overloading. The "%" operator calls the __getitem__ (by duct typing) from the next object given. 

So, I created a class based on the dictionary type that behaves just like a normal dictionary but when retrieving items, it assumes that the stored object is an iterable and picks randomly from it (delegating the __getitem__ call to it's parent).

---

