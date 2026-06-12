---
title: "help make code shorter?"
date: 2012-10-19
forum: Programming Talk
---

### Post by snowlizard31 on 2012-10-19
I'm trying to make a simple cli app to help me learn my kanji but I they way I'm doing it right now is just to long and boring and I can't come up with any code that will work to make it shorter. 

```

kanji_set1 = ['&#20061;', '&#21476;', '&#20882;', '&#26379;', '&#26126;', '&#21809;', '&#26230;', '&#21697;', '&#21570;', '&#26124;', '&#26089;', '&#26093;',\
            '&#19990;', '&#32963;', '&#26086;', '&#32966;', '&#20120;', '&#20985;', '&#20984;']

#kanji set one kanji reading only here so I can remember the readings for each kanji
#also failed attempt to make code shorter
kanji1_onread = ['&#12365;&#12421;&#12358;','&#12405;&#12427;&#12356;', '&#12412;&#12358;', '&#12411;&#12358;', '&#12417;&#12356;', '&#12375;&#12423;&#12358;', '&#12375;&#12423;&#12358;',\
                '&#12375;&#12394;', '&#12426;&#12423;', '&#12375;&#12423;&#12358;', '&#12381;&#12358;', '&#12365;&#12423;&#12367;', '&#12379;&#12356;', '&#12356;', '&#12383;&#12435;', '&#12383;&#12435;',\
                '&#12371;&#12358;', '&#12362;&#12358;', '&#12392;&#12388;']

# kanji set one english meaning
kanji1_e = ['nine', 'old', 'risk', 'companion', 'bright', 'chant', 'sparkle',\
            'goods', 'spine/ come together', 'prosperous','early' , 'rising sun',\
            'generation', 'stomach', 'nightbreak', 'gall bladder', 'span', \
            'concave', 'convex']

def check_exit(input):
    if input.lower() == 'quit' or  input.lower() == 'exit':
        sys.exit()
    
print "&#12393;&#12358;&#12375;&#12390;&#12427;? This is an exercise based on RTF lessons 1 though 2 to get\
    to guess the meaning of the kanji and the on reading."
print "First guess the meaning of the kanji in english if you get it right\
    you'll be able to guess it's on reading."
print "Type any on reading in either hiragana or romanji. Type quit or exit to quit."


while True:
    kanji = random.choice(kanji_set1)
    print kanji
    guess = raw_input('>>')
    check_exit(guess)
    
    if kanji == '&#20061;':
        if guess == 'nine':
            print "Correct!"
            on_guess = raw_input('>')
            if on_guess == '&#12365;&#12421;&#12358;' or on_guess == 'kyuu':
                print "correct!"
            else:
                print "incorrect!"
        else:
            print "&#12385;&#12364;&#12358;&#65281;that's wrong"
    
    elif kanji == '&#21476;':
        if guess == 'old':
            print "correct!"
            on_guess = raw_input('>')
            if on_guess == '&#12405;&#12427;' or on_guess == 'furu':
                print "Correct!"
            else:
                print "Incorrect!"
        else:
            print "Incorrect"

```also Is there any way I can make the kanji font size any bigger?

P.S is there any way I can make kanji1_e a dict and make the value of a kanji in kanji_set1 equal to the key in kanji1_e and make it print the value of the key.

---

### Post by PatrickD-52761 on 2012-10-19
> **snowlizard31 said:**
> I'm trying to make a simple cli app to help me learn my kanji but I they way I'm doing it right now is just to long and boring and I can't come up with any code that will work to make it shorter. 

```

kanji_set1 = ['&#20061;', '&#21476;', '&#20882;', '&#26379;', '&#26126;', '&#21809;', '&#26230;', '&#21697;', '&#21570;', '&#26124;', '&#26089;', '&#26093;',\
            '&#19990;', '&#32963;', '&#26086;', '&#32966;', '&#20120;', '&#20985;', '&#20984;']

#kanji set one kanji reading only here so I can remember the readings for each kanji
#also failed attempt to make code shorter
kanji1_onread = ['&#12365;&#12421;&#12358;','&#12405;&#12427;&#12356;', '&#12412;&#12358;', '&#12411;&#12358;', '&#12417;&#12356;', '&#12375;&#12423;&#12358;', '&#12375;&#12423;&#12358;',\
                '&#12375;&#12394;', '&#12426;&#12423;', '&#12375;&#12423;&#12358;', '&#12381;&#12358;', '&#12365;&#12423;&#12367;', '&#12379;&#12356;', '&#12356;', '&#12383;&#12435;', '&#12383;&#12435;',\
                '&#12371;&#12358;', '&#12362;&#12358;', '&#12392;&#12388;']

# kanji set one english meaning
kanji1_e = ['nine', 'old', 'risk', 'companion', 'bright', 'chant', 'sparkle',\
            'goods', 'spine/ come together', 'prosperous','early' , 'rising sun',\
            'generation', 'stomach', 'nightbreak', 'gall bladder', 'span', \
            'concave', 'convex']

def check_exit(input):
    if input.lower() == 'quit' or  input.lower() == 'exit':
        sys.exit()
    
print "&#12393;&#12358;&#12375;&#12390;&#12427;? This is an exercise based on RTF lessons 1 though 2 to get\
    to guess the meaning of the kanji and the on reading."
print "First guess the meaning of the kanji in english if you get it right\
    you'll be able to guess it's on reading."
print "Type any on reading in either hiragana or romanji. Type quit or exit to quit."


while True:
    kanji = random.choice(kanji_set1)
    print kanji
    guess = raw_input('>>')
    check_exit(guess)
    
    if kanji == '&#20061;':
        if guess == 'nine':
            print "Correct!"
            on_guess = raw_input('>')
            if on_guess == '&#12365;&#12421;&#12358;' or on_guess == 'kyuu':
                print "correct!"
            else:
                print "incorrect!"
        else:
            print "&#12385;&#12364;&#12358;&#65281;that's wrong"
    
    elif kanji == '&#21476;':
        if guess == 'old':
            print "correct!"
            on_guess = raw_input('>')
            if on_guess == '&#12405;&#12427;' or on_guess == 'furu':
                print "Correct!"
            else:
                print "Incorrect!"
        else:
            print "Incorrect"

```also Is there any way I can make the kanji font size any bigger?

P.S is there any way I can make kanji1_e a dict and make the value of a kanji in kanji_set1 equal to the key in kanji1_e and make it print the value of the key.

It appears that you're using an array for the kanji, and english translations. So, you should be able to do something like this:

```
index = random(10)
print kanji_set1(index)
guess = raw_input('>>')
while guess != "exit" OR guess !="quit":
    if guess == kanji_e(index):
        print "Correct! Now, guess the on reading of the kanji"
        on_guess = raw_input('>')
        if on_guess == kanji1_onread(index):
                print "correct!"
        else:
                print "incorrect!"
    else:
        print "Incorrect."
    index = random(10)
    print kanji_set1(index)
    guess = raw_input('>>')

```

Some things to note. The actual format for each statement will vary based on whatever language you're using. Also the number in the random statement will vary depending on the language and how many items you have in the array.

You won't need the check_exit() portion of your code at all, since it will be checked in the while loop.

Also, I left off the top portion of the code. So you'll need to create each array like you did, then print the instructions, and start with the code that I put in.

As for your PS, that's exactly what you should be doing with the arrays. You won't need to compare each element in the array separately. You'll just use one line to get the index, one line to print the kanji from that array at that index location, and one line to compare the guess to each corresponding array at that index location.

Also, in case you're not familiar with this, the first position in the array is 0 NOT 1. So, if you have 10 items, you'll be looking for 0 through 9 (not 1 through 10). You'll have to adjust your random for that.

Hope this helps. Have a great day:)
Patrick.

---

### Post by Vaphell on 2012-10-20
separate arrays are a pain in terms of maintenance.

i'd create a file where all related values are together, read the file into array of dict structures and then pick one
```
#!/usr/bin/env python

import codecs
import random

class KanjiDictElem():
  def __init__( self, kanji, read, english ):
    self.kanji = kanji
    self.read = read
    self.english = english

f = codecs.open( "kanji_dict.txt", "r", encoding="utf-8" )
kanjidict = []

# populate dict
for ln in f:
  col = ln.split( "|" )
  kanjidict.append( KanjiDictElem( col[0].strip(), col[1].strip(), col[2].strip() ) )

# print dict  
for elem in kanjidict:
  print "%s (%s): %s" % ( elem.kanji, elem.read, elem.english )

# pick random elem
rnd = kanjidict[ random.randint( 0, len(kanjidict)-1 ) ]

# Q&A
print "%s (%s): " % ( rnd.kanji,rnd.read )
answer = raw_input()
if answer == rnd.english:
  print "correct!"
else:
  print "you get an F!"
```
kanji_dict.txt:
```
&#20061;       |&#12365;&#12421;&#12358;        |nine
&#21476;       |&#12405;&#12427;&#12356;        |old
&#20882;       |&#12412;&#12358;          |risk
&#26379;       |&#12411;&#12358;          |companion
&#26126;       |&#12417;&#12356;          |bright
&#21809;       |&#12375;&#12423;&#12358;        |chant
&#26230;       |&#12375;&#12423;&#12358;        |sparkle
&#21697;       |&#12375;&#12394;          |goods
&#21570;       |&#12426;&#12423;          |spine/ come together
&#26124;       |&#12375;&#12423;&#12358;        |prosperous
&#26089;       |&#12381;&#12358;          |early
&#26093;       |&#12365;&#12423;&#12367;        |rising sun
&#19990;       |&#12379;&#12356;          |generation
&#32963;       |&#12356;            |stomach
&#26086;       |&#12383;&#12435;          |nightbreak
&#32966;       |&#12383;&#12435;          |gall bladder
&#20120;       |&#12371;&#12358;          |span
&#20985;       |&#12362;&#12358;          |concave
&#20984;       |&#12392;&#12388;          |convex
```

output:
```
$ python -V
Python 2.6.5
$ ./kanji.py 
&#20061; (&#12365;&#12421;&#12358;): nine
&#21476; (&#12405;&#12427;&#12356;): old
&#20882; (&#12412;&#12358;): risk
&#26379; (&#12411;&#12358;): companion
&#26126; (&#12417;&#12356;): bright
&#21809; (&#12375;&#12423;&#12358;): chant
&#26230; (&#12375;&#12423;&#12358;): sparkle
&#21697; (&#12375;&#12394;): goods
&#21570; (&#12426;&#12423;): spine/ come together
&#26124; (&#12375;&#12423;&#12358;): prosperous
&#26089; (&#12381;&#12358;): early
&#26093; (&#12365;&#12423;&#12367;): rising sun
&#19990; (&#12379;&#12356;): generation
&#32963; (&#12356;): stomach
&#26086; (&#12383;&#12435;): nightbreak
&#32966; (&#12383;&#12435;): gall bladder
&#20120; (&#12371;&#12358;): span
&#20985; (&#12362;&#12358;): concave
&#20984; (&#12392;&#12388;): convex
&#21570; (&#12426;&#12423;): 
spine/ come together
correct!

```

---

### Post by snowlizard31 on 2012-10-20
thanks for the help guys! Just reading you're code make me wish I was as good as you guys I guess I'm going to have to practice a lot more!:D

---

