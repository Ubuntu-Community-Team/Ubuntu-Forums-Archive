---
title: "I need some advice on how to make a database/dictionary"
date: 2009-06-27
forum: Programming Talk
---

### Post by offchance on 2009-06-27
Hey Everybody!

I have 430+ words and definitions that I have compiled by hand from book sources that I need to organize into an alphabetized dictionary/glossary. Condict look promising, but the depencies are a mess due to the flux inherent in nonprofit, opensource projects.

So. What I want to learn to do is create a searchable database. I want to enter a word and its definition once and, if I have the same word with another definition, add to the original. I want to be able to show whole categories of records (i.e. display all the A words, etc.). 

I am looking for advice on how to approach this project. I have experience with html/css and that's about it. I know my way around the command line to an extent. All I'm really asking for is for someone to point me in a useful direction.

Any takers?

---

### Post by slavik on 2009-06-27
I think you answered your own question when you said database.

---

### Post by MadViper on 2009-06-27
if you have office pro, or heck even open office can do this, use access its pretty simple but im sure there are guides online if you need help

---

### Post by ghostdog74 on 2009-06-27
> **offchance said:**
> HAny takers?
if you foresee your dictionary is going to increase in the future, consider using database such as mysql etc. that said, a file is also a simple "database". you can "structure" you dictionary file in a special way, such that by using programming language, you can parse the file and extract the necessary information. also, there are simple database modules in languages such as Python (dbm, pickle,shelve, sqlite etc) that you can also use. 

here's a very simple example using just plain text file as "database". the language used is awk
```

BEGIN{
    ####    -------- Amateur dictionary editor (ghostdog74) ------------- ###
    IGNORECASE=1
    # name of dictionary
    dictionary="file" 
    while ( ( getline line < dictionary )>0 ){
        #get all lines into array for easier manipulation
        dict[++d]=line
    }
    while (1){
        # do forever until quit
        system("clear")
        print "1) Look for word"
        print "2) Insert definition"
        print "3) Search word using definition"
        print "4) Insert new word and definition"
        print "5) Quit"
        printf "Select your choice:"
        getline choice <"-"
        if ( choice == 5 ) exit
        if ( choice == 1 ) {
            # enter word and search for definitions
            printf "Enter word: "
            getline word < "-"
            for (i=1;i<=d;i++){
                m=split(dict[i],l,":")
                if ( l[1] == word ){
                    #if found word
                    print "Word: " word
                    print "Definition: " 
                    print "-------------------------"
                    n=split(l[2],def,"|")
                    for(i in def){
                        print def[i]
                    }                    
                    break
                }
            }    #end reading dictionary file                    
            getline <"-"
            system("clear")
        }else if ( choice == 2 ){
            #insert new definition
            print "insert new definition"
            printf "Enter word to insert new defintion: "
            getline word < "-"
            for (i=1;i<=d;i++){
                m=split(dict[i],l,":")
                if ( l[1] == word ){
                    printf "Enter new defintion: "
                    getline newdef < "-"
                    print  newdef
                    l[2] = l[2]"|"newdef
                    dict[i] = l[1]":"l[2]
                    f=1 
                }                
            }
            if(f){
                #write new data to file if there are changes
                for (i=1;i<=d;i++){
                    print dict[i] > dictionary
                }
                print "New definition for "word" updated"
            }
            printf "Press enter to continue..."
            getline <"-"        
        }else if (choice == 3){
            #search word using defintion key words
            printf "Enter key word: "
            getline keyword <"-"
            for (i=1;i<=d;i++){
                m=split(dict[i],l,":")
                if ( l[2] ~ keyword){
                    print dict[i]
                }            
                print "--------------------------"
            }
            printf "Press enter to continue..."
            getline <"-"
        }else if ( choice == 4){
            #insert new word and definition
            printf "Enter new word: "
            getline newword <"-"
            printf "Enter new definition(s) (separated by |): "
            getline newdef < "-"
            newitem = newword":"newdef
            dict[++d]=newitem
            #sort the dictionary
            b=asort(dict, dict1)            
            printf "Press enter to continue..."
            getline <"-"            
            for (i=1;i<=b;i++){
                    print dict1[i] > dictionary
            }            
        }
    }
}

```

the dictionary file must look something like this:
```

word1:definition 1|definition 2
word2:def2
word3:def3|def3a|def3b

```

on command line
```

# gawk -f mydictionary.awk

```

---

### Post by fr4nko on 2009-06-27
As other suggested I think you should use a relational database like MySQL, this would be a good choice and if your project/database grows you will be always confortable with MySQL. You can also use a file based SQL system like sqlite.

Francesco

---

### Post by offchance on 2009-06-27
@ghostdog & fr4nko:
Thank you for your insights. That bit of code to go along with a text file is what I had in mind, I just don't have the coding background to whip it out like that! 

If I go along with your example, Ghostdog, will I have to download awk or is that likely to already be installed on my system?

---

### Post by ghostdog74 on 2009-06-27
> **offchance said:**
> If I go along with your example, Ghostdog, will I have to download awk or is that likely to already be installed on my system?
awk is preinstall on almost all *nix distro. what i have shown can be done with practically any other programming languages. if you are familiar with other language, then use them.

---

### Post by Wim Sturkenboom on 2009-06-27
> **fr4nko said:**
> As other suggested I think you should use a relational database like MySQL, this would be a good choice and if your project/database grows you will be always confortable with MySQL. You can also use a file based SQL system like sqlite.

FrancescoPersonally I think that MySQL is a total overkill (there is probably not even anything relational in the OP's 'design').

I agree on a solution with SQLite but one probably still needs to build a bit of an user-interface around it to make it user-friendly.

Personally I would probably make something in a spreadsheet program (csv file storage).

I would never have thought about the awk solution mentioned above but like the (different) approach.

---

### Post by fr4nko on 2009-06-27
> **Wim Sturkenboom said:**
> Personally I think that MySQL is a total overkill (there is probably not even anything relational in the OP's 'design').
I'm not so sure that MySQL would be an overkill, it depends on the complexity of your dictionary. For example, in a decent dictionary you should allow for multiple definitions, some of the definitions will be related to a particular context and some words can be used as verb or as a name (substantive). You may also want to relate together synonyms and may be to provide multiple words expressions like, for example, if you say 'to speed up something', to speed up is a verb, but only if used with 'up', so you should take into account this case. You may also want to take into account the conjugation of the verbs to recognize for example that 'spoken' is the past of the verb to speak.

So, in my point of view, to build a serious dictionary, a SQL relational database is not an overkill. On the other size I recognize that if you want to implement something very simple you can do the job with some file-based definition, as suggested.

Talking about the awk solutions, my remarks is that if the complexity of your dictionary implementation grows with awk you can be in trouble because this kind on implementation is not flexible enough to accomodate a more complex model. Also, I don't see the need of using awk when you can use perl or python.

Francesco

---

### Post by Can+~ on 2009-06-27
A relational database is perfect for this problem, but you're presentation is very vague to define how the actual database it will be.

For example, let's start with a very basic design with two tables (in entity-relation notation):

Words <------>> Definitions

So you can store multiple definitions for a word, but what if you want to do synonyms too? So for example, each definition can have multiple words associated, thus creating many-to-many relation:

Words <<------>> Definitions

Let's break the many-to-many:

Words <------>> Qualifier <<----> Definitions

Qualifier will determine if the relation is a relation of definition, synonym, antonym, etc. As for the actual physical set-up goes, you could use a sorted file for words, thus improving single selection to log b (b=data blocks), and range selection to log b + [s/Fb] (Fb: Registers per block, s: size of selection in registers). But making insertion really slow, but shouldn't be a problem, as a dictionary is rarely updated.

So all depends on how complex you want to make it.

---

### Post by ghostdog74 on 2009-06-27
dudes, that awk piece i did is firstly, for fun, secondly its just showing to OP the very barebones "database" can be just a file. So at the very minimum, its just reading and editing the dictionary file, that's all. much like what you do when you query/update a real database table. without using any database module, this simple approach can also be done with other languages, not necessarily need to use awk. Like i have told awk is one of the tools i use daily, therefore i just pick it up from my tool box like that. I would have use Python as well.

[quote=fr4nko]
Also, I don't see the need of using awk when you can use perl or python
[/quote]
awk does not come with its own database module, however, if i really want, i can just make use of mysql client command line together with awk to query and update the database. That way, its just the same as using Perl or Python's DB modules..isn't it? 

[quote=fr4nko]
Talking about the awk solutions, my remarks is that if the complexity of your dictionary implementation grows with awk you can be in trouble because this kind on implementation is not flexible enough to accomodate a more complex model
[/quote]
a more complex model like what? also do you have awk experience enough to say that? for your reading pleasure see [here](http://awk.info/?awk100)

---

### Post by soltanis on 2009-06-27
Awk does not need databases (and most likely neither does the OP) -- it has associative arrays.

I don't really understand the engineering problem (or rather the problem is not well-defined). Lay out exactly what the storage system for this dictionary needs to be able to do, and then you will be better able to decide whether built-in language structures suffice, or if you are going to need to step up to something like sqlite (MySQL is totally overkill for this).

---

### Post by offchance on 2009-06-28
This is all very helpful (and eye-opening). 

As far as complexity is concerned, the end result is not intended for an audience any wider than me. I want to use this to organize my work, compare/contrast definitions of jargon and argot words that are specific to a single industry, and then print off the completed, organized glossary. There are some words that are related and that have variable definitions depending on context and tense. It would be nice to have a way to link words in a "see also:" sort of way. 

Thanks for bearing with me. This is my first foray into dictionary making and serious coding.

---

### Post by slavik on 2009-06-28
postgres > mysql IMO.

I believe you can do string[] as a field in postgres ;)

---

### Post by ghostdog74 on 2009-06-28
> **soltanis said:**
> Awk does not need databases (and most likely neither does the OP) -- it has associative arrays..
yes it does, BUT the issue is, data in assoc arrays will be gone when program exits. you will still need a "database" to store information on disk for future processing.

---

### Post by slavik on 2009-06-28
> **ghostdog74 said:**
> yes it does, BUT the issue is, data in assoc arrays will be gone when program exits. you will still need a "database" to store information on disk for future processing.
Hibernate ;)

---

### Post by pelle.k on 2009-06-28
The simplest approach would be python + data in dicts/lists/tuples serialized to json and saved to a flat text file.
Another option would be pysqlite. I wouldn't start with that if i was a beginner though.

---

### Post by offchance on 2009-06-28
ghostdog: I read here ([...]("http://hell.org.ua/Docs/oreilly/nuts/bookshelves/linuxwebserv2/lian/ch13_02.htm")) about a command that can print all lines that contain a certain key word. Would it be possible for me to add a few lines to the code you provided that would allow me to print all the lines that begin with a certain letter?
[I]
example:[/I]
6. display all words beginning with the letter...
enter letter ___
(and then it shows me all the words/def's that begin with the letter A in alphabetical order)

does that make any sense?

---

### Post by soltanis on 2009-06-28
Or dump the array to a file and read it back in later. There's your database.

---

### Post by fr4nko on 2009-06-28
Just for fun, the same code of the dictionary but in python instead of awk:
```

import sys

dictionary = {}

def text_input(msg):
    print msg
    line = sys.stdin.readline()
    return line.replace('\n', '')

def add_def(word, deff):
    try:
        dictionary[word].append(deff)
    except KeyError:
        dictionary[word] = [ deff ]

def word_search ():
    word = text_input('Enter word: ')
    print 'Definitions'
    print '-' * 40
    for definition in dictionary[word]:
        print definition

def insert_def ():
    word = text_input("Enter word to insert new defintion: ")
    definition = text_input("Enter new defintion: ")
    add_def(word, deff)

def search_def ():
    keyword = text_input("Enter key word: ")
    for word, definitions in dictionary.iteritems():
        for d in definitions:
            if d.find(keyword) >= 0:
                print '-' * 40
                print 'Word:', word
                print 'Definition:', d

def insert_word():
    word = text_input("Enter new word: ")
    defs = text_input("Enter new definition(s) (separated by |): ").split('|')
    for d in defs:
        add_def(word, d)

main_menu = [
    {'text': 'Look for word',                  'action': word_search},
    {'text': 'Insert definition',              'action': insert_def},
    {'text': 'Search word using definition',   'action': search_def},
    {'text': 'Insert new word and definition', 'action': insert_word},
    {'text': 'Quit',                           'action': (lambda : exit(0))},
]

while True:
    for i, line in enumerate(main_menu):
        print '%d) %s' % (i+1, line['text'])
    try:
        choice = int(text_input("Enter your choice: ")) - 1
        action = main_menu[choice]['action']
        action()
    except IndexError:
        print 'Invalid selection'

```Of course you can make the database definition by dumping the dictionary into a file.

Francesco

---

### Post by ghostdog74 on 2009-06-28
> **offchance said:**
> example:[/I]
6. display all words beginning with the letter...
enter letter ___
(and then it shows me all the words/def's that begin with the letter A in alphabetical order)

does that make any sense?
you just change the "==" sign to "~"
```

if ( l[1] ~ word )

```

---

### Post by offchance on 2009-06-29
@fr4nko

I ran your version (*py dic.py* in terminal) and got the following when adding a new definition to a word (option 2)

```

Traceback (most recent call last):
  File "dic.py", line 57, in <module>
    action()
  File "dic.py", line 26, in insert_def
    add_def(word, deff)
NameError: global name 'deff' is not defined
```

---

### Post by Can+~ on 2009-06-29
> **fr4nko said:**
> Just for fun, the same code of the dictionary but in python instead of awk:
```

import sys

dictionary = {}

def text_input(msg):
    print msg
    line = sys.stdin.readline()
    return line.replace('\n', '')

def add_def(word, deff):
    try:
        dictionary[word].append(deff)
    except KeyError:
        dictionary[word] = [ deff ]

def word_search ():
    word = text_input('Enter word: ')
    print 'Definitions'
    print '-' * 40
    for definition in dictionary[word]:
        print definition

def insert_def ():
    word = text_input("Enter word to insert new defintion: ")
    **deff** = text_input("Enter new defintion: ")
    add_def(word, deff)

def search_def ():
    keyword = text_input("Enter key word: ")
    for word, definitions in dictionary.iteritems():
        for d in definitions:
            if d.find(keyword) >= 0:
                print '-' * 40
                print 'Word:', word
                print 'Definition:', d

def insert_word():
    word = text_input("Enter new word: ")
    defs = text_input("Enter new definition(s) (separated by |): ").split('|')
    for d in defs:
        add_def(word, d)

main_menu = [
    {'text': 'Look for word',                  'action': word_search},
    {'text': 'Insert definition',              'action': insert_def},
    {'text': 'Search word using definition',   'action': search_def},
    {'text': 'Insert new word and definition', 'action': insert_word},
    {'text': 'Quit',                           'action': (lambda : exit(0))},
]

while True:
    for i, line in enumerate(main_menu):
        print '%d) %s' % (i+1, line['text'])
    try:
        choice = int(text_input("Enter your choice: ")) - 1
        action = main_menu[choice]['action']
        action()
    except IndexError:
        print 'Invalid selection'

```Of course you can make the database definition by dumping the dictionary into a file.

Francesco

Typo there.

---

### Post by offchance on 2009-06-29
> **ghostdog74 said:**
> you just change the "==" sign to "~"
```

if ( l[1] ~ word )

```

I added the following to your awk code:

```
}else if ( choice == 6 ) {
  # enter word and search for definitions
  printf "Enter word: "
  getline word < "-"
  for (i=1;i<=d;i++){
  m=split(dict[i],l,":")
  if ( l[1] ~ word ){
  #if found word
  print "Word: " word
  print "Definition: " 
  print "-------------------------"
  n=split(l[2],def,"|")
  for(i in def){
  print def[i]
  }  
  break
  }
  } #end reading dictionary file  
  getline <"-"
  system("clear")
```

This works, in that it gives me a response and doesn't turn into an error message and a fresh prompt. It only shows me the first D, A, or B entry it comes to, not all of the words/defs that begin with their respective letters. Would it be appropriate to modify this section at   *#if found word* to include all words beginning with a certain letter, or is this not the site of the problem?

---

### Post by ghostdog74 on 2009-06-29
> **offchance said:**
> 

This works, in that it gives me a response and doesn't turn into an error message and a fresh prompt. It only shows me the first D, A, or B entry it comes to, not all of the words/defs that begin with their respective letters. Would it be appropriate to modify this section at   *#if found word* to include all words beginning with a certain letter, or is this not the site of the problem?

```

        if ( choice == 1 ) {
            # enter word and search for definitions
            printf "Enter word: "
            getline word < "-"
            oword=word
            word="^"word  # this will search at start of word
            for (i=1;i<=d;i++){
                m=split(dict[i],l,":")
                if ( l[1] ~ word ){
                    #if found word
                    print "Word: " l[1]
                    print "Definition: " 
                    print "-------------------------"
                    n=split(l[2],def,"|")
                    for(i in def){
                        print def[i]
                    }                    
                    break
                }
            }    #end reading dictionary file                    
            getline <"-"
            #system("clear")

```

this is as far as i will go for your issue. please read and practice with the gawk manual if you are interested, otherwise, you may start to learn a programming language such as Python that comes with good database modules for your needs.

---

### Post by gorilla on 2009-06-29
> **offchance said:**
> Hey Everybody!

I have 430+ words and definitions that I have compiled by hand from book sources that I need to organize into an alphabetized dictionary/glossary. Condict look promising, but the depencies are a mess due to the flux inherent in nonprofit, opensource projects.

So. What I want to learn to do is create a searchable database. I want to enter a word and its definition once and, if I have the same word with another definition, add to the original. I want to be able to show whole categories of records (i.e. display all the A words, etc.). 

I am looking for advice on how to approach this project. I have experience with html/css and that's about it. I know my way around the command line to an extent. All I'm really asking for is for someone to point me in a useful direction.

Any takers?
For so little, private projects, real databases applications are overkill when one has the unix tools at his fingertips :)
I only use plain textfiles + grep for my personal database needs and that actually work pretty well. Sure, it's hackisch, but you can't beat zero development effort \\:D/

---

### Post by tturrisi on 2009-06-29
You could have a look at how the dictionaries are formatted which are used by Gnome Dictionary and OpenOffice.  AFAIK they are text files.  The duplicate the format using your words and definitions and use the graphical Gnome dictionary.

---

### Post by monraaf on 2009-06-29
> **tturrisi said:**
> You could have a look at how the dictionaries are formatted which are used by Gnome Dictionary and OpenOffice.  AFAIK they are text files.  The duplicate the format using your words and definitions and use the graphical Gnome dictionary.

I think that the gnome-dictionary only uses online dictionaries.

---

### Post by offchance on 2009-06-29
> **gorilla said:**
> For so little, private projects, real databases applications are overkill when one has the unix tools at his fingertips :)
I only use plain textfiles + grep for my personal database needs and that actually work pretty well. Sure, it's hackisch, but you can't beat zero development effort \\:D/

I'm reading the output of *grep --help* right now and I'm a little lost. I'm not sure about "regular expressions" and how to use them. This makes sense to me, though. It seems possible to use gedit to create the plain text file and then use grep to display useful chunks of information stored there (i.e. sorting out all the A words).

**edit**: I read a tutorial ([here]("http://www.panix.com/~elflord/unix/grep.html")) and figured out how to use ^ to return all the results that begin with a certain letter. The only problem I encountered is that something like *grep ^a file* does not sort the results, it just returns them in whatever order they occur in the file. This is the heart of my problem, sorting/alphabetizing.

---

### Post by offchance on 2009-06-29
```
grep ^b file | sort
```

This may solve my problem. If I enter all my words by hand into a text file and use these commands I could get the sorted, alphabetized results I need. I could then just cut/paste the terminal results into something fancier if I ever need to. This seems to eliminate the apparent need for a special interface which, thus far, has been most of the problem.

Thanks all who helped out!

*Update*: Here's what I ended up using.
```
grep ^Z file | sort > newfile.txt
```

---

