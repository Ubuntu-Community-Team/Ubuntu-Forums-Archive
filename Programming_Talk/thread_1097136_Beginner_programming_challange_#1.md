---
title: "Beginner programming challange #1"
date: 2009-03-15
forum: Programming Talk
---

### Post by Bodsda on 2009-03-15
[Challenge #2]("http://ubuntuforums.org/showthread.php?t=1109152")

Hi, 

I have decided to bring back the beginner programming challenges, since many of the non-beginner ones are way to over my head i thought maybe other people may feel the same way, and when the old beginners challenges were about, i really enjoyed them (even though i never submitted anything). So these challenges should be simple enough for someone with a few months programming behind them. The submitted entries will be judged next weekend. All languages are allowed, but if its something obscure or not majorly used please provide a link to a tutorial on how to get it runnning, thanks :) Enjoy

[SIZE="4"]Challenge[/SIZE]
Write a guess the number game.

You must use a random number generator to obtain the number.

The number must be between 1 and 100

The game should not crash if an invalid entry is made, e.g. if i enter the string "OMG give me the answer!!" the program should catch the error and tell me that only integers are valid entries.

[SIZE="3"]Extra credit[/SIZE]
Allow the use of words for the values, e.g. "Twenty six" should be recognized as 26 and no error should be raised.

Allow the use of an external text file for higher lower prompts.

(I realise i have just said dont allow words, then allow them, but you know what i mean)



Please refrain from uploading obfuscated code, as im likely to dismiss it. The code should be readable by a beginner programmer. 

NOTE: To experienced programmers. Whilst your entries will be accepted, they will not be judged, instead I encourage you to help newer programmers with this challenge (obviously not giving them the answer) and any help you do give will be greatly appreciated im sure.

So, without further ado, Begin. 

Oh, and have fun!

Thanks, 

Bodsda

---

### Post by sujoy on 2009-03-15
here's a quick python solution :)

[PHP]#!/usr/bin/env python

import random

num = random.randint(0,100)
while 1:
	try:
		input=int(raw_input("Guess a number within 0-100 :: "))
		if input<0 or input>100:
			raise ValueError
		elif input == num:
			print "you guessed it right :)"
			break
		elif input < num:
			print "guess higher next time ...\n"
		else:
			print "guess lower next time ...\n"
	except ValueError:
		print "only integers within 0-100 are accepted\nplease try again ...\n"[/PHP]

---

### Post by Bodsda on 2009-03-15
An addition to the Extra credit section has been added:

> Allow the use of an external text file for higher lower prompts.

---

### Post by run1206 on 2009-03-15
i made my program in c++
```

#include <iostream>
#include <cstdlib>
#include <time.h>

using namespace std;

int main()
{
	//initialize random seed 
	srand ( time(NULL) );
	
	int randomNumber = 0;
	randomNumber = (rand()%100)+1;	//create a random number b/w 1 & 100
	int numGuess = 0;	
	cout << "Guess a number between 1 and 100." << endl;
	
	cin >> numGuess;

	while (numGuess != randomNumber)
	{
	
			cout << "Wrong number. Try again." << endl;	//signify wrong number
			cin >> numGuess;				//guess again...
	}

		cout << "You guessed the correct number!! Great Job!" << endl;	//signify right number
		cout << "Program Terminated." << endl;			//end random number game
		

    return 0;
}//end main

```

in the following code, i put the random number in the output to try to verify that it's (somewhat) random.
edit: found out what my problem was, i forgot to include the initializer itself! :oops: :oops: :lol: :lol:

```

run1206@run1206-laptop:~$ g++ -o randomNumber randomNumber.cpp
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
83
83
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
64
64
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
58
58
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
83
83
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
99
99
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
70
78
Wrong number. Try again.
70
You guessed the correct number!! Great Job!
Program Terminated.

```

i'll try with words as numbers as well... :)

---

### Post by Bodsda on 2009-03-16
> **run1206 said:**
> i made my program in c++
```

#include <iostream>
#include <cstdlib>
#include <time.h>

using namespace std;

int main()
{
	//initialize random seed 
	srand ( time(NULL) );
	
	int randomNumber = 0;
	randomNumber = (rand()%100)+1;	//create a random number b/w 1 & 100
	int numGuess = 0;	
	cout << "Guess a number between 1 and 100." << endl;
	
	cin >> numGuess;

	while (numGuess != randomNumber)
	{
	
			cout << "Wrong number. Try again." << endl;	//signify wrong number
			cin >> numGuess;				//guess again...
	}

		cout << "You guessed the correct number!! Great Job!" << endl;	//signify right number
		cout << "Program Terminated." << endl;			//end random number game
		

    return 0;
}//end main

```

in the following code, i put the random number in the output to try to verify that it's (somewhat) random.
edit: found out what my problem was, i forgot to include the initializer itself! :oops: :oops: :lol: :lol:

```

run1206@run1206-laptop:~$ g++ -o randomNumber randomNumber.cpp
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
83
83
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
64
64
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
58
58
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
83
83
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
99
99
You guessed the correct number!! Great Job!
Program Terminated.
run1206@run1206-laptop:~$ ./randomNumber 
Guess a number between 1 and 100.
70
78
Wrong number. Try again.
70
You guessed the correct number!! Great Job!
Program Terminated.

```

i'll try with words as numbers as well... :)

Good job, nice to see an entry other then python :) I remember in the old beginners challenges 90% of the entries were python.

---

### Post by hessiess on 2009-03-16
Common Lisp:

```

; Function to prompt the user and return the entered value
(defun prompt-read (prompt)
  (format *query-io* "~a : " prompt)
  (force-output *query-io*)
  (read-line *query-io*))

;Function to repeatedly prompt the user until a valid
;number is entered
(defun get-number (prompt)
  (let ((val 0))
    (loop
      (setf val (parse-integer
        (prompt-read prompt) :junk-allowed t))
      (if val
        (return val)
        (format t "Only integers are allowed.~%")))))

(defun correct() 
  (format t "~%You guessed correctly.~%")
  (bye))

;Main game function
(defun game ()
  (format t "Guess the number game.~%")
  (let ((rndnum nil)(answer nil))
    (setf rndnum (random 100))
    (loop
      (setf answer (get-number "number > "))
      (if (= answer rndnum)
        (correct)
        (format t "~%Your answer is wrong.~%")))))

(game)

```

I am not new to porgramming, but I am new to Lisp ;).

---

### Post by ufis on 2009-03-16
> **Bodsda said:**
> [SIZE="3"]Extra credit[/SIZE]
Allow the use of words for the values, e.g. "Twenty six" should be recognized as 26 and no error should be raised.

I'll just go for the extra credit part in java. 

Edit: Caters for "twentysix" and "twenty six" but not "twenty-six";

[PHP]import java.util.HashMap;

public class StrToNum {
	private HashMap<String, Integer> postnumbers;
	private HashMap<String, Integer> numbers;
	private HashMap<String, Integer> teenpre;
	private HashMap<String, Integer> pre;

	private String ten = "teen";
	private String decade = "ty";

	{
		postnumbers = new HashMap<String, Integer>();
		postnumbers.put("one", 1);
		postnumbers.put("two", 2);
		postnumbers.put("three", 3);
		postnumbers.put("four", 4);
		postnumbers.put("five", 5);
		postnumbers.put("six", 6);
		postnumbers.put("seven", 7);
		postnumbers.put("eight", 8);
		postnumbers.put("nine", 9);

		numbers = new HashMap<String, Integer>();
		numbers.putAll(postnumbers);
		numbers.put("ten", 10);
		numbers.put("eleven", 11);
		numbers.put("twelve", 12);
		numbers.put("hundred", 100);

		teenpre = new HashMap<String, Integer>();
		teenpre.put("thir", 3);
		teenpre.put("four", 4);
		teenpre.put("fif", 5);
		teenpre.put("six", 6);
		teenpre.put("seven", 7);
		teenpre.put("eigh", 8);
		teenpre.put("nine", 9);

		pre = new HashMap<String, Integer>();
		pre.put("twen", 2);
		pre.putAll(teenpre);
	}

	public int convert(String str) throws NumberFormatException {
		str = str.toLowerCase();
		int indexD = str.indexOf(decade);
		int indexT = str.indexOf(ten);
		String sub, post;
		try {
			if ( indexT != -1) { //String contains "teen"
				sub = str.substring(0, indexT);
				if (ten.equals(str.substring(indexT))) {
					return teenpre.get(sub) + 10;
				}
			} else if ( indexD != -1) { //String contains ty
				sub = str.substring(0, indexD);
				if (decade.equals(str.substring(indexD))) { //Dividable by 10
					return pre.get(sub) * 10;
				} else {
					post = str.substring(indexD + decade.length()).trim();
					return (pre.get(sub) * 10) + postnumbers.get(post);
				}
			} else {
				return numbers.get(str);
			}
			throw new Exception();
		} catch (Exception e) {
			throw new NumberFormatException(str + " is not a valid number"); 
		}
	}
}[/PHP]

---

### Post by run1206 on 2009-03-16
thanks much :)
i'm trying to learn Python and script languages, kinda broaden my horizons on programming languages.

---

### Post by namegame on 2009-03-16
I might throw something together in Ruby. (which I currently know NOTHING about, it could be fun.)

---

### Post by Taidgh on 2009-03-16
Could anyone tell me why this doesn't work? 
```

#!/usr/bin/env python
import random

guess = raw_input("Please enter a number between 1 and 100: ")
guess = int(guess)
try:
	if guess == random.randint(1,100):
		print "You guessed correct!"
	else:
		print "Incorrect number."
except ValueError:
	print "Please enter an integer (whole number)."

```
I get this output:
```

taidgh@ephedra:~/Desktop$ python guess.py
Please enter a number between 1 and 100: notanint
Traceback (most recent call last):
  File "guess.py", line 5, in <module>
    guess = int(guess)
ValueError: invalid literal for int() with base 10: 'notanint'

```

---

### Post by sujoy on 2009-03-16
> **Taidgh said:**
> Could anyone tell me why this doesn't work? 
```

#!/usr/bin/env python
import random

guess = raw_input("Please enter a number between 1 and 100: ")
guess = int(guess)
try:
	if guess == random.randint(1,100):
		print "You guessed correct!"
	else:
		print "Incorrect number."
except ValueError:
	print "Please enter an integer (whole number)."

```
I get this output:
```

taidgh@ephedra:~/Desktop$ python guess.py
Please enter a number between 1 and 100: notanint
Traceback (most recent call last):
  File "guess.py", line 5, in <module>
    guess = int(guess)
ValueError: invalid literal for int() with base 10: 'notanint'

```


the exception is thrown in this line,
guess = int(guess)
as it tried to make an int out of a string.
hence, put it inside the try block :)

---

### Post by simeon87 on 2009-03-16
> **Taidgh said:**
> Could anyone tell me why this doesn't work? 

The conversion to integer is outside the try...

---

### Post by Taidgh on 2009-03-16
> **sujoy said:**
> the exception is thrown in this line,
guess = int(guess)
as it tried to make an int out of a string.
hence, put it inside the try block :)
Lol, thanks for pointing that out for me. I feel like an idiot now. :D

---

### Post by Sinkingships7 on 2009-03-16
Here's a quick Python hack. I'll add the extra credit when I have more time, as well as implement a C++ version.
```
[color=#008000]**import**[/color] [color=#0000FF]**random**[/color]

random_number [color=#666666]=[/color] random[color=#666666].[/color]randint([color=#666666]1[/color], [color=#666666]100[/color])

[color=#008000]**while**[/color] [color=#008000]True[/color]:
	[color=#008000]**try**[/color]:
		guess [color=#666666]=[/color] [color=#008000]int[/color]([color=#008000]raw_input[/color]([color=#BA2121]"Take a guess: "[/color]))
	[color=#008000]**except**[/color] [color=#D2413A]**ValueError**[/color]:
		[color=#008000]**print**[/color] [color=#BA2121]"Please choose a positive integer between 1 and 100."[/color]
		[color=#008000]**continue**[/color]
		
	[color=#008000]**if**[/color] guess [color=#666666]<[/color] random_number:
		[color=#008000]**print**[/color] [color=#BA2121]"Guess higher!"[/color]
	[color=#008000]**elif**[/color] guess [color=#666666]>[/color] random_number:
		[color=#008000]**print**[/color] [color=#BA2121]"Guess lower!"[/color]
	[color=#008000]**else**[/color]:
		[color=#008000]**print**[/color] [color=#BA2121]"You guessed it!"[/color]
		[color=#008000]**break**[/color]

```

---

### Post by Taidgh on 2009-03-16
Okay here's my finished effort:
[PHP]
#!/usr/bin/env python
import random, sys

try:
    file = open(sys.argv[1],"r")
    guesses = file.readlines()
    for guess in range(0,len(guesses)):
        guesses[guess] = int(guesses[guess].strip())
    if random.randint(1,100) in guesses: print "You guessed correct!"
    else: print "Incorrect number."
except IOError:
    print "Sorry, that file does not appear to exist."
    print "Are you sure it is in the current directory?"
except IndexError:
    while True:
        try:
            guess = raw_input("Please enter a number between 1 and 100: ")
            guess = int(guess)
            if guess == random.randint(1,100):
                print "You guessed correct!"
                break
            elif guess < 0 or guess > 100:
                print "That number is not between 1 and 100."
            else:
                print "Incorrect number."
        except ValueError:
	        print "Please enter an integer (whole number)."
[/PHP]
You supply a file (containing a list of numbers) to be opened as the first argument. It's a bit sloppy/inelegant, but it appears to do the job.

---

### Post by snova on 2009-03-16
> **Bodsda said:**
> Good job, nice to see an entry other then python :) I remember in the old beginners challenges 90% of the entries were python.

What's wrong with that? :D

I wrote most of this yesterday, but finished it after it was too late to submit, so here's mine.

It implements everything except using an external file for messages. And I should probably make NaturalToInteger() raise more specific exceptions, so I can print out a particular parse error...

[PHP]
#!/usr/bin/python
# -*- coding: utf-8 -*-

import optparse
import random
import time

# A mapping of numbers less than ten to their numerical equivalents, one
# through ten. Valid on their own or paired with one of the next series.
Ones = {'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5,
        'six': 6, 'seven': 7, 'eight': 8, 'nine': 9}

# Multiples of ten, starting from twenty. These are only valid with another
# number from the first series coming after it.
Tens = {'twenty': 20, 'thirty': 30, 'forty': 40, 'fifty': 50,
        'sixty': 60, 'seventy': 70, 'eighty': 80, 'ninety': 90}

# Numbers only valid on their own. Includes ten through nineteen, each of the
# other series, and zero.
Singles = {'zero': 0, 'ten': 10, 'eleven': 11, 'twelve': 12, 'thirteen': 13,
           'fourteen': 14, 'fifteen': 15, 'sixteen': 16, 'seventeen': 17,
           'eighteen': 18, 'nineteen': 19}
Singles.update(Ones)
Singles.update(Tens)

def NaturalToInteger(line):
    words = [word.lower() for word in line.split()]

    if len(words) == 1:
        if words[0] in Singles:
            return Singles[words[0]]
        else:
            raise ValueError
    elif len(words) == 2:
        try:
            return Tens[words[0]] + Ones[words[1]]
        except KeyError:
            raise ValueError

# Initialize random number generator and choose an answer.
random.seed(time.time())
answer = random.randint(1, 100)

# Parse options.
parser = optparse.OptionParser()
parser.add_option("-a", "--answer", action="store", type="int",
                  help="Set the answer to the game.")
parser.add_option("-m", "--max", action="store", type="int", default=8,
                  help="Set the maximum number of guesses you are allowed. If 0, unlimited.")
options, args = parser.parse_args()

if args:
    parser.error("This script does not take any arguments.")
if options.answer:
    answer = options.answer
if options.max:
    if options.max == 0:
        # Somewhat hackish, but the comparison "guesses < MAX_GUESSES" will
        # always be True, so it works.
        MAX_GUESSES = -1
    else:
        MAX_GUESSES = options.max

guesses = 0

try:
    while guesses < MAX_GUESSES:
        line = raw_input("What is your guess? ")
        try:
            guess = int(line)
            natural = False
        except ValueError:
            try:
                guess = NaturalToInteger(line)
                natural = True
            except ValueError:
                print "Invalid input. Please enter either an integer or a natural expression."
                continue

        if guess == answer:
            print "You win!"
            exit()
        elif guess < answer:
            # Numbers inputted in "natural" form are echoed back, in case it
            # was parsed incorrectly.
            if natural:
                print "%i is too small." % guess
            else:
                print("Too small.")
        elif guess > answer:
            if natural:
                print "%i is too large." % guess
            else:
                print "Too large."

        guesses += 1
    print "Too many guesses. Answer was:", answer
except (EOFError, KeyboardInterrupt):
    # On Ctrl-D or Ctrl-C
    print
    print "Quitting. Answer was:", answer
[/PHP]

---

### Post by jimi_hendrix on 2009-03-16
> **snova said:**
> What's wrong with that? :D

white space hurts my eyes?

---

### Post by Bodsda on 2009-03-16
> **snova said:**
> What's wrong with that? :D

I wrote most of this yesterday, but finished it after it was too late to submit, so here's mine.

It implements everything except using an external file for messages. And I should probably make NaturalToInteger() raise more specific exceptions, so I can print out a particular parse error...

Loving the enthusiasm, perhaps you would be kind enough to give a detailed explanation of your code, line by line type of thing so that beginners can benefit.

Thanks,

Bodsda

> **Taidgh said:**
> Okay here's my finished effort:
[PHP]
#!/usr/bin/env python
import random, sys

try:
    file = open(sys.argv[1],"r")
    guesses = file.readlines()
    for guess in range(0,len(guesses)):
        guesses[guess] = int(guesses[guess].strip())
    if random.randint(1,100) in guesses: print "You guessed correct!"
    else: print "Incorrect number."
except IOError:
    print "Sorry, that file does not appear to exist."
    print "Are you sure it is in the current directory?"
except IndexError:
    while True:
        try:
            guess = raw_input("Please enter a number between 1 and 100: ")
            guess = int(guess)
            if guess == random.randint(1,100):
                print "You guessed correct!"
                break
            elif guess < 0 or guess > 100:
                print "That number is not between 1 and 100."
            else:
                print "Incorrect number."
        except ValueError:
	        print "Please enter an integer (whole number)."
[/PHP]
You supply a file (containing a list of numbers) to be opened as the first argument. It's a bit sloppy/inelegant, but it appears to do the job.

Ok, i think you may have slightly misunderstood. The number must be randomly generated, which you have achieved, however your program randomly generates the number 'every' time you guess. I edited your code to print the answer for the purpose of showing you this output. 

```

Please enter a number between 1 and 100: 50
Incorrect number.
Correct number. 90
Please enter a number between 1 and 100: 90
Incorrect number.
Correct number. 72

```

Also, you might want to consider not running the main section of your program only when an IndexError is raised

Im also unsure what this file with a list of numbers is supposed to do -- the extra credit section for an external file was so that you could have multiple prompts for "Go higher" / "Go lower"

A valiant effort, keep going, if you need help, just ask.

---

### Post by Slayeragb2 on 2009-03-16
Don't know how good the code itself is, bu it works.

[PHP][CODE
]#!/usr/bin/env python

import random

def game():
	winNum = random.randrange(1, 101)
	while True:
		try:
			guess = int(raw_input("What do you think the number is? "))
			if guess > winNum:
				print "Guess was to high. Try agian."
			elif guess < winNum:
				print "Guess was to low. Try agian."
			elif guess == winNum:
				print "Correct!"
				playagian()
				return False
		except ValueError, NameError:
			print "Not a valid entry!"
			

def playagian():
	playquestion = raw_input("Would you like to play agian?(Yes/No)")
	while True:
		if playquestion == "yes":
			game()
		elif playquestion == "no":
			print "Goodbye!"
			return False
		else:
			print "Please enter yes or no!"
			playagian()
			return False
			
game()
[/CODE][/PHP]

---

### Post by eightmillion on 2009-03-17
I may have gone a bit overboard here. I wrote my own random number generator.

[PHP]
#!/usr/bin/env python        

class spellwords:
    def __init__(self):
        self.words = [ (1,'one',''),(2,'two',''),(3,'three',''),(4,'four',''),(5,'five',''),(6,'six',''),(7,'seven',''),
                      (8,'eight',''),(9,'nine',''),(10,'ten',''),(11,'eleven',''),(12,'twelve',''),(13,'thirteen',''),  
                      (14,'fourteen',''),(15,'fifteen',''),(16,'sixteen',''),(17,'seventeen',''),(18,'eighteen',''),    
                      (19,'nineteen',''),(20,'twenty',''),(30,'thirty',''),(40,'forty',''),(50,'fifty',''),(60,'sixty',''),
                      (70,'seventy',''),(80,'eighty',''),(90,'ninety',''),(100,'hundred','and'),(1000,'thousand','and'),]  
        self.words.reverse()                                                                                               

    def spell(self,n):
        if n == 0: return ['zero']
        word = []                 
        while n > 0:              
            for num in self.words:
                if num[0] <= n:   
                    div,n = divmod(n,num[0])
                    if num[2]: word.append(' '.join(self.spell(div)))
                    word.append(num[1])                              
                    if num[2] and n: word.append(num[2])             
                    break                                            
        return word                                                  

    def num2word(self,n): return " ".join(self.spell(n))

    def getWorddict(self,start,finish):
        self.worddict = {}             
        for x in range(start,finish+1):
            y = self.num2word(x)       
            self.worddict[y] = x       
            self.worddict['-'.join(y.split())] = x
            if 'and ' in y:                       
                y = ''.join(y.split('and '))      
                self.worddict[y] = x              
                self.worddict['-'.join(y.split())] = x
        return self.worddict                          

class random:
    def __init__(self):
        from time import strftime
        self.mt = [0]*624        
        self.index = 0           
        self.initializeGenerator(int(strftime('%s')))

    def reseed(self,seed):
        self.index = 0    
        self.initializeGenerator(seed)

    def initializeGenerator(self,seed):
        self.mt[0] = seed              
        for i in range(1,624):         
            self.mt[i] = (1812433253 * (self.mt[i-1] ^ ((self.mt[i-1]>>30)+i))) & 4294967295L

    def extractNumber(self):
        if self.index == 0: 
            self.generateNumbers()
        y = self.mt[self.index]   
        y = y ^ (y>>11)           
        y = y ^ ((y<<7) & 2636928640)
        y = y ^ ((y<<15) & (4022730752))
        y = y ^ (y>>18)                 
        self.index = (self.index + 1) % 624
        return y                           

    def generateNumbers(self):
        for i in range(624):  
            y = (self.mt[i]%2) + ((self.mt[(i+1) % 624])>>1)
            self.mt[i] = self.mt[(i + 397) % 624] ^ (y>>1)  
            if y % 2 == 1:                                  
                self.mt[i] = self.mt[i] ^ 2567483615        

    def randrange(self,start,finish):
        y = self.extractNumber()%finish
        while not start <= y <= finish:
            y = self.extractNumber()%finish
        return y                           


class game:
    def __init__(self):
        self.rand = random()
        self.limit = 100    
        self.words = spellwords().getWorddict(0,self.limit)
        self.cheat = False                                 

    def setlimit(self,limit):
        self.limit = limit   
        self.words = spellwords().getWorddict(0,self.limit)

    def setcheat(self):
        self.cheat = True

    def new(self):
        number = self.rand.randrange(1,self.limit)        
        tries = 0                                         
        if self.cheat: print number                       
        while True:                                       
            try:                                          
                guess = raw_input("Enter your guess: ")   
            except (EOFError, KeyboardInterrupt):         
                print "\nGoodbye."                        
                exit()                                    
            try:                                          
                guess = int(guess)                        
            except:                                       
                if self.words.has_key(guess.lower()):     
                    guess = self.words[guess.lower()]     
                else:                                     
                    print "Guess not recognized. Try again."
                    continue
            tries += 1
            if guess < number:
                print "Higher"
            elif guess > number:
                print "Lower"
            else:
                print "You guessed it in %d %s!" % (tries,'try' if tries==1 else 'tries')
                break

if __name__ == '__main__':
    from optparse import OptionParser, SUPPRESS_HELP
    import sys

    usage = "%s [-l|--limit] limit" % sys.argv[0]
    guess = game()
    parser = OptionParser(usage=usage, version="%prog 1")
    parser.add_option("-l", "--limit", dest="limit", action="store",type="int", default=False, help="Set the upper limit for the game.")
    parser.add_option("--cheat", action="store_true", dest="cheat", default=False, help=SUPPRESS_HELP)
    (options, args) = parser.parse_args()
    if options.limit: guess.setlimit(options.limit)
    if options.cheat: guess.setcheat()
    guess.new()
    while True:
        yesno = raw_input("Would you like to play again? [y/n] ").strip().lower()
        if yesno in ["yes","y"]:
            guess.new()
        if yesno in ["no","n","quit","q","exit"]:
            print "Goodbye."
            exit()
        else:
            print "Option not recognized. Try again."
[/PHP]

and here's my obfuscated version just for fun:

[PHP]
import sys,random;guess=lambda x,num=random.randint(1,100),f=[1]:(lambda y,g=lambda t:sys.stdout.write(t):map(
eval,["g(\"Lower\\n\")","f.append(f.pop()+1)","guess(int(raw_input(\"Guess: \")))"]) if y>num else map(eval,["g(\"Higher\\n\")",
"f.append(f.pop()+1)","guess(int(raw_input(\"Guess: \")))"]) if y<num else g("You guessed it in %d %s!\n" %(f[0],["tries",
"try"][f[0]==1])))(x);guess(int(raw_input("Guess: ")))
[/PHP]

---

### Post by Frank Kotler on 2009-03-17
Do we want an assembly language (Nasm) version? I have such a beast - written a while ago, and just modified slightly to fit the "specs" better. (no "extra credit", as yet) I'll be glad to post it, but if any real "beginners" are going to give it a shot, I'll hang back... Spudgunner? Anybody?

(how *do* I post code??? one of those hieroglyphics on the top???)

Best,
Frank

---

### Post by run1206 on 2009-03-17
> **Frank Kotler said:**
> Do we want an assembly language (Nasm) version? I have such a beast - written a while ago, and just modified slightly to fit the "specs" better. (no "extra credit", as yet) I'll be glad to post it, but if any real "beginners" are going to give it a shot, I'll hang back... Spudgunner? Anybody?

(how *do* I post code??? one of those hieroglyphics on the top???)

Best,
Frank

type code (in brackets) then post some code....

then type /code (in brackets)
```
like this
```


i'd be interested to see it in assembly :)

---

### Post by Frank Kotler on 2009-03-17
Okay, lemme give it a shot. Like this, huh?

```

; guess the number
;
; nasm -f elf -Ox guess.asm
; ld -o guess guess.o

global _start	; tell ld about our entrypoint

MAX_INPUT equ 4	; 3 digits and a linefeed

section .data
    start_prompt db "I'm thinking of a number between 1 and 100.", 10
		db "Can you guess it?", 10
    start_prompt_len equ $ - start_prompt		

    high_prompt db "No, that's too high.", 10
    high_prompt_len equ $ - high_prompt
    
    low_prompt db "No, that's too low.", 10
    low_prompt_len equ $ - low_prompt
    
    win_prompt db "You got it!", 10
    win_prompt_len equ $ - win_prompt

    bad_prompt db "Please enter only numbers '0' through '9'!", 10
    bad_prompt_len equ $ - bad_prompt
    
    quit_prompt db 'Giving up? Type "echo $?" to see the number.', 10
    quit_prompt_len equ $ - quit_prompt

section .bss
    the_number resd 1
    guess_buffer resb MAX_INPUT

section .text
_start:
    nop

; a half-asmed PRNG
; "good enough for games"
; don't use it for crypto!
    rdtsc
    mov ecx, 100
    shr eax, 1
    xor edx, edx
    div ecx
    inc edx
    mov [the_number], edx

; instruct the victim
    mov ecx, start_prompt
    mov edx, start_prompt_len
    call write_stdout

; let the battle of wits begin!
get_guess:
    mov ecx, guess_buffer
    mov edx, MAX_INPUT
    call read_stdin
    cmp eax, byte 1
    ja got_guess

; if we didn't get anything back but the linefeed
; they must be quitting. So impatient, kids these days!
    mov ecx, quit_prompt
    mov edx, quit_prompt_len
    call write_stdout
    mov ebx, [the_number]	; give answer as exitcode
    jmp exit

got_guess:
    mov edx, guess_buffer
    call atoi
    jnc good_number

; idiot entered a non-digit!
; (idiot programmer can't handle words)
    mov ecx, bad_prompt
    mov edx, bad_prompt_len
    call write_stdout
    jmp get_guess

good_number:    
    cmp [the_number], eax
    je got_it
    ja too_low
    
    mov ecx, high_prompt
    mov edx, high_prompt_len
    call write_stdout
    jmp get_guess    

too_low:
    mov ecx, low_prompt
    mov edx, low_prompt_len
    call write_stdout
    jmp get_guess

got_it:
    mov ecx, win_prompt
    mov edx, win_prompt_len
    call write_stdout

    xor ebx, ebx	; claim "no error"
exit:
    mov eax, 1
    int 80h
;----------------------

;-------------------
; write_stdout    
; expects: buffer in ecx, length in edx
; returns: length written (or error) in eax
write_stdout:
    push ebx
    mov eax, 4 ; __NR_write
    mov ebx, 1 ; stdout
    int 80h
    pop ebx
    ret
;------------------

;-------------------
; atoi - converts string to (unsigned!) integer
; expects: buffer in edx
; returns: number in eax - carry-flag set
; if a non-digit (except 0 and linefeed) was encountered
atoi:
    push ecx
    push edx
    xor eax, eax        ; clear "result"
.top:
    movzx ecx, byte [edx]
    inc edx

    cmp ecx, byte 0
    jz .done
    cmp ecx, byte 10
    jz .done
    
    cmp ecx, byte '0'
    jb .invalid
    cmp ecx, byte '9'
    ja .invalid
    
    ; we have a valid character - multiply
    ; result-so-far by 10, subtract '0'
    ; from the character to convert it to
    ; a number, and add it to result.
    
    lea eax, [eax + eax * 4]
    lea eax, [eax * 2 + ecx - '0']

    jmp short .top
.invalid:
    stc
.done:
    pop edx
    pop ecx
    ret
;--------------

;--------------
; read_stdin
; expects: buffer in ecx, max to read in edx
; returns: length read in eax
; any excess over max is flushed from OS's buffer
read_stdin:
    push ebx
    push ecx
    push edx
    
    mov eax, 3 ; __NR_read
    mov ebx, 0 ; stdin
    int 80h

    cmp eax, edx
    jb .done

    cmp byte [ecx + eax], 10
    jz .done

; if the pesky user typed more than max,
; it will be picked up by our next read,
; or show up on the command prompt when we exit.
; get rid of it!
    push eax	; save original count
.flush_buffer:
    push eax	; make a buffer
    mov ecx, esp
    mov eax, 3 ; __NR_read
    mov edx, 1
    int 80h
    pop eax	; free the buffer
    cmp al, 10
    jnz .flush_buffer
    pop eax	; restore original count
    
.done:
    pop edx
    pop ecx
    pop ebx
    ret
;-----------------


```


Yeah, I guess that worked. Thanks for the posting tip, run1206!

Best,
Frank

---

### Post by run1206 on 2009-03-17
edit: nvm got it :D

```

run1206@run1206-laptop:~$ nasm -f elf -Ox guess.asm
run1206@run1206-laptop:~$ ld -o guess guess.o
run1206@run1206-laptop:~$ ./guess
I'm thinking of a number between 1 and 100.
Can you guess it?
45
No, that's too low.
88
No, that's too low.
99
No, that's too high.
89
No, that's too low.
95
No, that's too high.
92
No, that's too low.
93
You got it!
run1206@run1206-laptop:~$ 

```
had to compile it the right way :lol:

---

### Post by Bodsda on 2009-03-17
Sweet, I'm gonna have to study that, nice work Frank

---

### Post by gtr32 on 2009-03-17
> **snova said:**
> 
I wrote most of this yesterday, but finished it after it was too late to submit, so here's mine.

You're missing (one) hundred (not 100).

Also when you guess the right number you get type error:

What is your guess? 87
You win!
Traceback (most recent call last):
  File "./p_s.pl", line 82, in ?
    exit()
TypeError: 'str' object is not callable

---

### Post by bobbocanfly on 2009-03-17
Not new to programming, but definately new to lisp. Seems to work mostly. Doesnt crash when you input a string, but doesn't tell you that you're doing it wrong, simply just tells you you are incorrect. 

```
; Creates a random number between 1 and 100
(defun get-random ()
  (+ 1 (random 99))) ;Clisp random starts from 0, so we need to add one to start from one

; Read input from user (no error checking etc)
(defun do-read ()
  (force-output *query-io*)
  (read-line *query-io*))

; Used to get input from user and make sure it is an integer
(defun get-input ()
  (or (parse-integer (do-read) :junk-allowed T) 0))

; Gets a guess from user and checks if it is right
(defun guess (randnum wrong)
  (if (eq T wrong)
    (format t "Incorrect, please try again: "))
  (let ((in (get-input)))
    (if (eql randnum in)
      (format t "Correct!")
      (guess randnum T))))

; Gets the game going
(defun main ()
  (format t "Please guess a number between 1 and 100: ")
  (let ((x (get-random)))
    (guess x NIL)))


```

---

### Post by sujoy on 2009-03-17
here is a basic perl one, will attempt the extra credits later,

```

#!/usr/bin/env perl

use strict;
use warnings;

my $max = 100;
my $number = int(rand($max));
my $guess = -1;

while ($guess != $number) {
	
	print "\nenter an integer between 1 and 100 :: ";
	
	if (eof()) {
		print "\n";
		exit;
	}

	chomp($guess=<>);

	if ($guess !~ m/^-?\d+$/) {
		print "enter an integer number\n";
		$guess = -1;
	}
	elsif ($guess == $number) {
		print "Congrats!\n";
	}
	elsif ($guess > $number) {
		print "Your guess is too high!\n";
	}
	else {
		print "Your guess is too low!\n";
	}
}
```

---

### Post by snova on 2009-03-17
> **gtr32 said:**
> You're missing (one) hundred (not 100).

Bother. So I am.

The parser is rather uncreative, and fairly fixed-form. Adding that would probably be difficult... which is unfortunate, I'd hoped to extend its capabilities a bit by allowing one to change the limits of the answer.

> Also when you guess the right number you get type error:

What is your guess? 87
You win!
Traceback (most recent call last):
  File "./p_s.pl", line 82, in ?
    exit()
TypeError: 'str' object is not callable

Hmm, odd. I can't duplicate it at all, and can't see anything wrong in the source...

---

### Post by ghostdog74 on 2009-03-18
```

awk 'BEGIN{srand();n=int(rand()*100)+1}n==ch{ print "Congrats..";exit}{printf "Guess?: ";getline ch<"-";print n<=ch?"Lower":"Higher"}'  /var/log/messages


```

---

### Post by Frank Kotler on 2009-03-20
I thought the Assembly Language Community (such as it is), ought to have an "extra credit" version, so I tried accepting "words as numbers". I figured if I was going to do it, I ought to shoot for a full 32-bit number, rather than stop at 100. I thought about 64-bit, so we could play "guess the National Debt", but I didn't know what comes after "gazillion" - "politicillion"? I should have stopped at 100!!!

Albert Einstein is quoted as saying, "Things should be as simple as possible... but no simpler." I'm afraid I tried to make my routine too simple. Works okay for small numbers - 100 is fine - but breaks badly up around "one million one hundred thousand" (maybe sooner - I haven't tried all possible values). I think I'm going to have to "stack" or "queue" values... and probably "operators", too. I tried a quick hack at that, but it isn't even close, at present, and I'm running out of ambition.

So back to the broken version... This turns out not to be much of an "enhancement" - much easier to type in numbers than words. (this version accepts either numbers or words, but not mix-and-match... which would have been nice). I'm too lazy at the moment to even lowercase the string (easy) - user must type lowercase - and "space" is the only delimiter allowed (would be easy to accept "twenty-five", but "twentyfive" would be harder... well, "twentyfive" wouldn't be bad, but "sixtysix"? Looks like a problem to me.)

I didn't attempt the "external file". I assume this is for "internationalization" purposes. The prompts shouldn't be too hard, but the "number names" might encounter some gotchas. I speak only English, but I "took" French in HS (long time ago!). IIRC, they do like "vingt et un", which would require special-casing. I'd need to know "all languages" and their numerical idiosyncrasies before even attempting to design the format of the external file... So I left it alone... Cries out for unicode, anyway...

So here's what I've got so far. I guess it's "playable" (not an exciting game!), but don't re-use the "natural_to_int" routine. It really isn't "right" - not even "close" - but works for a "certain subset"...

```

; guess the number - "words" version
;
; nasm -f elf -Ox guess2.asm
; ld -o guess2 guess2.o

global _start	; tell ld about our entrypoint

MAX_INPUT equ 255 ; enough?

section .data
    start_prompt db 10, "I'm thinking of a number between 1 and 100.", 10
		db "Can you guess it?", 10
		db "Numerals '0' through '9' or English numbers", 10
		db '"one" through "one hundred" are acceptable.', 10, 10
    start_prompt_len equ $ - start_prompt		

    high_prompt db " is too high.", 10
    high_prompt_len equ $ - high_prompt
    
    low_prompt db " is too low.", 10
    low_prompt_len equ $ - low_prompt
    
    win_prompt db "! You got it!", 10
    win_prompt_len equ $ - win_prompt

    bad_prompt db "Please enter only numerals '0' through '9',", 10
	db 'OR "English numbers": "one" through "one hundred".', 10
    bad_prompt_len equ $ - bad_prompt
    
    quit_prompt db 'Giving up? Type "echo $?" to see the number.', 10
    quit_prompt_len equ $ - quit_prompt

; numbers we can just add to "result so far"
    n_0 db "zero", 0, 0
    n_1 db "one", 0, 1
    n_2 db "two", 0, 2
    n_3 db "three", 0, 3
    n_4 db "four", 0, 4
    n_5 db "five", 0, 5
    n_6 db "six", 0, 6
    n_7 db "seven", 0, 7
    n_8 db "eight", 0, 8
    n_9 db "nine", 0, 9
    n_10 db "ten", 0, 10
    n_11 db "eleven", 0, 11
    n_12 db "twelve", 0, 12
    n_13 db "thirteen", 0, 13
    n_14 db "fourteen", 0, 14
    n_15 db "fifteen", 0, 15
    n_16 db "sixteen", 0, 16
    n_17 db "seventeen", 0, 17
    n_18 db "eighteen", 0, 18
    n_19 db "nineteen", 0, 19
    n_20 db "twenty", 0, 20
    n_30 db "thirty", 0, 30
    n_40 db "forty", 0, 40
    n_50 db "fifty", 0, 50
    n_60 db "sixty", 0, 60
    n_70 db "seventy", 0, 70
    n_80 db "eighty", 0, 80
    n_90 db "ninety", 0, 90

; numbers we have to multiply
; obviously we don't need 'em all for 1 to 100...
    n_hun db "hundred", 0
    dd 100
    n_tho db "thousand", 0
    dd 1000
    n_mil db "million", 0
    dd 1000000
    n_bil db "billion", 0
    dd 1000000000

; zero-terminated array of pointers to "add-type numbers"
    addtable dd n_0, n_1, n_2, n_3, n_4, n_5, n_6, n_7, n_8, n_9, n_10
         dd n_11, n_12, n_13, n_14, n_15, n_16, n_17, n_18, n_19
	 dd n_20, n_30, n_40, n_50, n_60, n_70, n_80, n_90, 0

; zero-terminated array of pointers to "multiply-type numbers"
    multable dd n_hun, n_tho, n_mil, n_bil, 0

section .bss
    the_number resd 1
; the current "natural_to_int" expects a *double* 0-terminator!
    guess_buffer resb MAX_INPUT + 1

section .text
_start:
    nop

; a half-asmed PRNG
; "good enough for games"
; don't use it for crypto!
    rdtsc
    mov ecx, 100
    shr eax, 1
    xor edx, edx
    div ecx
    inc edx
    mov [the_number], edx

; instruct the victim
    mov ecx, start_prompt
    mov edx, start_prompt_len
    call write_stdout

; let the battle of wits begin!
get_guess:
    mov ecx, guess_buffer
    mov edx, MAX_INPUT
    call read_stdin

; the current "natural_to_int" expects a *double* 0-terminator!
    mov word [eax + ecx - 1], 0
    cmp eax, byte 1
    ja got_guess

; if we didn't get anything back but the linefeed,
; they must be quitting. So impatient, kids these days!
    mov ecx, quit_prompt
    mov edx, quit_prompt_len
    call write_stdout
    mov ebx, [the_number]	; give answer as exitcode
    jmp exit

got_guess:
    mov edx, guess_buffer
    call atoi
    jnc good_number

; try "English numbers"
    mov esi, guess_buffer
    call natural_to_int
    jnc good_number

; idiot entered a non-digit!
; idiot programmer can't handle words...
; not *these* words, anyway!
    mov ecx, bad_prompt
    mov edx, bad_prompt_len
    call write_stdout
    jmp get_guess

good_number:    
    call showeaxd
    cmp [the_number], eax
    je got_it
    ja too_low
    
    mov ecx, high_prompt
    mov edx, high_prompt_len
    call write_stdout
    jmp get_guess    

too_low:
    mov ecx, low_prompt
    mov edx, low_prompt_len
    call write_stdout
    jmp get_guess

got_it:
    mov ecx, win_prompt
    mov edx, win_prompt_len
    call write_stdout

    xor ebx, ebx	; claim "no error"
exit:
    mov eax, 1
    int 80h
;----------------------

;-------------------
; write_stdout    
; expects: buffer in ecx, length in edx
; returns: length written (or error) in eax
write_stdout:
    push ebx
    mov eax, 4 ; __NR_write
    mov ebx, 1 ; stdout
    int 80h
    pop ebx
    ret
;------------------

;--------------
; read_stdin
; expects: buffer in ecx, max to read in edx
; returns: length read in eax
; any excess over max is flushed from OS's buffer
read_stdin:
    push ebx
    push ecx
    push edx
    
    mov eax, 3 ; __NR_read
    mov ebx, 0 ; stdin
    int 80h

    cmp eax, edx
    jb .done

    cmp byte [ecx + eax], 10
    jz .done

; if the pesky user typed more than max,
; it will be picked up by our next read,
; or show up on the command prompt when we exit.
; get rid of it!
    push eax	; save original count
.flush_buffer:
    push eax	; make a buffer
    mov ecx, esp
    mov eax, 3 ; __NR_read
    mov edx, 1
    int 80h
    pop eax	; free the buffer
    cmp al, 10
    jnz .flush_buffer
    pop eax	; restore original count
    
.done:
    pop edx
    pop ecx
    pop ebx
    ret
;-----------------

;-------------------
; atoi - converts string to (unsigned!) integer
; expects: buffer in edx
; returns: number in eax - carry-flag set
; if a non-digit (except 0 and linefeed) was encountered
atoi:
    push ecx
    push edx
    xor eax, eax        ; clear "result"
.top:
    movzx ecx, byte [edx]
    inc edx

    cmp ecx, byte 0
    jz .done
    cmp ecx, byte 10
    jz .done
    
    cmp ecx, byte '0'
    jb .invalid
    cmp ecx, byte '9'
    ja .invalid
    
    ; we have a valid character - multiply
    ; result-so-far by 10, subtract '0'
    ; from the character to convert it to
    ; a number, and add it to result.
    
    lea eax, [eax + eax * 4]
    lea eax, [eax * 2 + ecx - '0']

    jmp short .top
.invalid:
    stc
.done:
    pop edx
    pop ecx
    ret
;--------------

;---------------------------------
; showeaxd - print a decimal representation of eax to stdout
; for "debug purposes only"... mostly
; expects: number in eax
; returns; nothing useful
showeaxd:
    push eax
    push ebx
    push ecx
    push edx
    push esi
    
    sub esp, 10h
    lea ecx, [esp + 12]
    mov ebx, 10
    xor esi, esi
    mov byte [ecx], 0
.top:    
    dec ecx
    xor edx, edx
    div ebx
    add dl, '0'
    mov [ecx], dl
    inc esi
    or eax, eax
    jnz .top
    
    mov edx, esi
    mov ebx, 1
    mov eax, 4
    int 80h
    
    add esp, 10h

    pop esi
    pop edx
    pop ecx
    pop ebx
    pop eax

    ret
;---------------------------------


;-----------------------
; WARNING WARNING WARNING
; broken software ahead!
; this bad boy silently returns wrong answers
; in some cases - works okay for 1 to 100... mostly.
;------------------------
; expects: pointer to string of "number words" in esi
; returns: number in eax - carry-flag set if unreadable.
natural_to_int:
    push ebx
    push ecx
    push edx
    push esi
    push edi

    xor eax, eax	; "result so far"
    xor ebx, ebx	; keeps a copy of last "add-type number"

; in order to do the string-compare, I
; split the input string into 0-terminated
; sub-strings "in place".
; this may not have been the best strategy,
; in that I might want to spit back "blah is
; not a valid number". they got what they typed
; right in front of 'em - I can live with it.
.word_from_string:
    or ecx, -1
.terminate_string:
    inc ecx
    cmp byte [esi + ecx], 0
    jz .end_terminate_string
    cmp byte [esi + ecx], ' '
    jnz .terminate_string
    mov byte [esi + ecx], 0
.end_terminate_string:

; I elected to try the "multiply-type numbers"
; first, since there are fewer of 'em.
; this may not have been the best move(?)
    mov edx, multable - 4
.next_multable:
    add edx, 4
    mov edi, [edx]
    test edi, edi
    jz .end_multable
    call compare_string
    jnz .next_multable

; okay, we've got a "multiply-type number"...
; (the dword number past the terminating zero)
; this nonsense is to "un-add" the
; result-so-far" from the
; "add-type number", multiply it by the
; "multiply type number", and add the
; result back into the "result-so-far".
; it only kinda sorta works sometimes.
; "one hundred thousand" :(

    test ebx, ebx
    jnz .got_add_type
    mul dword [edi + ecx + 1]
    jmp .end_nonsense

; that fixes "one hundred thousand"
; but "one million one hundred thousand"... :(

.got_add_type:
    xchg eax, ebx
    sub ebx, eax
    mul dword [edi + ecx + 1]
    add eax, ebx
    
    xor ebx, ebx
.end_nonsense:

; update the input-string pointer,
; if there's no more, we're done,
; else get next sub-string.
    lea esi, [esi + ecx + 1]
    cmp byte [esi], 0
    jz .end_natural_to_int
    jmp .word_from_string
.end_multable:

; now check for "add-type numbers"
    mov edx, addtable - 4
.next_addtable:
    add edx, 4
    mov edi, [edx]
    test edi, edi
    jz .end_addtable
    call compare_string
    jnz .next_addtable

; get (zero-extend) the byte 1 past the terminating 0.
; add it to "result-so-far"... and keep a copy in ebx!
; with the above, this kinda sorta works...
    movzx ebx, byte [edi + ecx + 1]
    add eax, ebx

; update the input-string pointer,
; if there's no more, we're done,
; else get next sub-string.
    lea esi, [esi + ecx + 1]
    cmp byte [esi], 0
    jz .end_natural_to_int
    jmp .word_from_string
.end_addtable:
; can't make a number out of what you typed. please try again
    stc
.end_natural_to_int:
    pop edi
    pop esi
    pop edx
    pop ecx
    pop ebx
    ret
;----------------

;----------------
; expects: string in esi, string in edi
; returns: flags
compare_string:
    pusha
.top:
    mov al, [esi]
    mov ah, [edi]
    cmp al, ah
    jnz .done
    inc esi
    inc edi
    cmp al, 0
    jnz .top
.done:
    popa
    ret
;-----------------------


```

Sorry for posting such sloppy code. Silently returning a wrong result is an "unacceptable" class of bug! If anyone sees an "elegant" fix, help me out! I'll keep working on it...

(the awk script was a lot shorter, wasn't it?)

Best,
Frank

---

### Post by Eisenwinter on 2009-03-20
Another basic one in Perl:

```
#!/usr/bin/perl -w

use strict;

my $number = int(rand(100));

while (my $guess = <STDIN>) {
 chomp($guess);

 if ($guess !~ /\d+/g) { print("Invalid input - must be a number\n"); }
 elsif ($guess == $number) { printf("Congratulations!\n"); die "finished\n"; }
 elsif ($guess > $number) { print("Lower\n"); }
 elsif ($guess < $number) { print("Higher\n"); }

}

```

---

### Post by jimi_hendrix on 2009-03-20
@frank
you are my hero for trying that in asm

---

### Post by lisati on 2009-03-20
> **jimi_hendrix said:**
> @frank
you are my hero for trying that in asm

Ditto on the appreciation of an effort in ASM (sorry, haven't looked at it closely enough to make suggestions on the "broken" section)

---

### Post by ibuclaw on 2009-03-20
> **Eisenwinter said:**
> Another basic one in Perl:

```
#!/usr/bin/perl -w

use strict;

my $number = int(rand(100));

while (my $guess = <STDIN>) {
 chomp($guess);

 if ($guess !~ /\d+/g) { print("Invalid input - must be a number\n"); }
 elsif ($guess == $number) { printf("Congratulations!\n"); die "finished\n"; }
 elsif ($guess > $number) { print("Lower\n"); }
 elsif ($guess < $number) { print("Higher\n"); }

}

```

C'mon Eisenwinter, at least make it a one-liner:
```
perl -e '$n=int(rand(100));do{chomp;$_=~/^$/?print"Guess the Number:":$_>$n?print"Lower:":$_<$n?print"Higher:":next;}while($_=<STDIN>)!=$n;print"Correct!\n"'
```

Regards
Iain

---

### Post by jimi_hendrix on 2009-03-20
> **tinivole said:**
> C'mon Eisenwinter, at least make it a one-liner:
```
perl -e '$n=int(rand(100));do{chomp;$_==""?print"Guess the Number:\n":$_>$n?print"Lower\n":$_<$n?print"Higher\n":next;}while($_=<STDIN>)!=$n;print"Correct!\n"'
```Regards
Iain

i was going to hack up a 1 liner but i was lazy

good job tinivole

---

### Post by drubin on 2009-03-20
> **jimi_hendrix said:**
> i was going to hack up a 1 liner but i was lazy

good job tinivole

/me dares tinivole to write it with sed and regex reading from /dev/random :)

---

### Post by ibuclaw on 2009-03-20
> **drubin said:**
> /me dares tinivole to write it with sed and regex reading from /dev/random :)

With sed's limited ability (it only has v.basic turing completeness... Can't even store values). It can't be done with a straight-up sed script.

But under the bash shell, you can come close:
```

# Get our random number (No peeking)
random=`sed "s/^.*\([1-9][0-9]\).*$/\1/" /proc/sys/kernel/random/uuid`
# Play game
sed -ne "/$random/"'{s/^.*$/Correct!/;p;q}' -e 's/^.*$/Wrong/;p'

```

It can't tell you whether or not you are higher or lower, but it will tell you if you are wrong/right :)

Regards
Iain

---

### Post by Eisenwinter on 2009-03-21
> **tinivole said:**
> C'mon Eisenwinter, at least make it a one-liner:
```
perl -e '$n=int(rand(100));do{chomp;$_=~/^$/?print"Guess the Number:":$_>$n?print"Lower:":$_<$n?print"Higher:":next;}while($_=<STDIN>)!=$n;print"Correct!\n"'
```

Regards
Iain
Well, didn't the OP request the code to be readable by a beginner?

I myself didn't like my own entry (in the way it's almost too simple), ;x

---

### Post by nvteighen on 2009-03-21
We already had this exact challenge... Here's my Scheme entry for the past one:

[http://ubuntuforums.org/showpost.php?p=5688998&postcount=30](http://ubuntuforums.org/showpost.php?p=5688998&postcount=30)

EDIT: Anyway, I had to review that code... it was broken :p

---

### Post by ibuclaw on 2009-03-21
> **Eisenwinter said:**
> Well, didn't the OP request the code to be readable by a beginner?

I myself didn't like my own entry (in the way it's almost too simple), ;x

Aye... but it my entry isn't **that** unreadable ...

All you have to do is press enter after each semicolon; (an auto indenting text editor usually helps) and the code will become clear in a text editor :)

Also:
tip on the Text -> Number Extra Credit... this is really simple in Perl, so why don't you do it?

```

#!/usr/bin/perl

sub convert($);

while($_=<STDIN>)
{
    my @arr, $num;
    my @toks = split(/\b/, $_);
    push (@arr, convert $_) for(@toks);
    while (scalar @arr)
    {
        $_ = shift @arr;
        if(not defined $num)
        {
            $num = $_;
            $num = "1$num" if($num=~/^0+$/);
        }
        else
        {
            my $len = length $_;
            if($_=~/^0+$/)
            {
                length $num <= length $_ ? $num .= $_ :
                    $num=~/0{$len}$/ ? $num .= $_ :
                    $num=~s/[0-9]{$len}([0-9]{$len})$/$1$_/ ?
                    next : goto error;
            }
            elsif($num!~/10$/ and $num=~/0+$/
                    and $_=~/^[1-9]/)
            {
                $num=~s/0{$len}$/$_/;
            }
            else
            {
                goto error;
            }
        }
    }
    print "$num\n";
    endloop:
    {
        undef $num;
    }
}
    
error:
{
    print "Hmm... either you are being a bit too fancy, or Incorect Input!\n";
    goto endloop;
}

sub convert($)
{
    shift;
    s/^one$/1/gi ? return $_ :
    s/^two$/2/gi ? return $_ :
    s/^three$/3/gi ? return $_ :
    s/^four$/4/gi ? return $_ :
    s/^five$/5/gi ? return $_ :
    s/^six$/6/gi ? return $_ :
    s/^seven$/7/gi ? return $_ :
    s/^eight$/8/gi ? return $_ :
    s/^nine$/9/gi ? return $_ :
    s/^ten$/10/gi ? return $_ :
    s/^eleven$/11/gi ? return $_ :
    s/^twelve$/12/gi ? return $_ :
    s/^thirteen$/13/gi ? return $_ :
    s/^fourteen$/14/gi ? return $_ :
    s/^fifteen$/15/gi ? return $_ :
    s/^sixteen$/16/gi ? return $_ :
    s/^seventeen$/17/gi ? return $_ :
    s/^eighteen$/18/gi ? return $_ :
    s/^nineteen$/19/gi ? return $_ :
    s/^twenty$/20/gi ? return $_ :
    s/^thirty$/30/gi ? return $_ :
    s/^forty$/40/gi ? return $_ :
    s/^fifty$/50/gi ? return $_ :
    s/^sixty$/60/gi ? return $_ :
    s/^seventy/70/gi ? return $_ :
    s/^eighty$/80/gi ? return $_ :
    s/^ninety$/80/gi ? return $_ :
    s/^hundred$/00/gi ? return $_ :
    s/^thousand$/000/gi ? return $_ :
    s/^million$/000000/gi ? return $_ :
    /^[0-9]+$/ ? return $_ :
    return;
}

```
OK, OK ... a wee bit verbose on the **convert** sub, but the rest is logical... :)

Tell me if you find a bug in it (I want to know).

Regards
Iain

---

### Post by Bodsda on 2009-03-22
Hi guys, this thread will be judged TODAY!! The result will most likely be announced at 22:00 UTC.

Any last minute entries will still be judged so get on with it!!

P.S: Tinivole your not a beginner :) wise *** perl monkey

---

### Post by elCabron on 2009-03-22
C#
```
using System;

class NumberGame
{
    public static void Main()
    {
        int rndNumber = new Random().Next(1, 100);
        int inpNumber = 0;

        while (inpNumber != rndNumber)
        {           
            do
            {
                Console.Write("Enter a number [1-100]: ");
               
                while (Int32.TryParse(Console.ReadLine(), out inpNumber) == false)
                {
                    Console.Write("Only numeric values are allowed, please try again [1-100]: ");
                }    
                              
            } while ((inpNumber < 1) || (inpNumber > 100));
           
            if (inpNumber != rndNumber)
            {
                Console.WriteLine("Your guess is too {0}, try again.", (inpNumber < rndNumber) ? "low" : "high");
            }
        }  
        
        Console.WriteLine("You guessed the correct number!");
    }
}
```

---

### Post by fixitdude on 2009-03-23
10 PRINT "GUESS THE NUMBER";
20 INPUT A
30 PRINT "WRONG NUMBER, TRY AGAIN"
40 GOTO 10

50 REM The never ending guessing game :)


(sorry, I couldn't resist)

---

### Post by lisati on 2009-03-23
> **fixitdude said:**
> 10 PRINT "GUESS THE NUMBER";
20 INPUT A
30 PRINT "WRONG NUMBER, TRY AGAIN"
40 GOTO 10

50 REM The never ending guessing game :)


(sorry, I couldn't resist)
:o I nearly missed part of the joke, most of the BASICs I've used in recent years don't need the line numbners :)

---

### Post by Bodsda on 2009-03-23
First of all, allow me to apologize for the late judge. My internet wasn't working yesterday so I couldn't post, however I have sorted that out and I have judged the entries.

"Drum roll please........"

*Drum roll*

The winner is......

run1206

Congratulations!

Your C++ implementation of this guess the number game was second to none. The simplicity of this program shows the delights of his chosen language, the most difficult part was probably working out how to set the random seed but after that its just a simple loop. The comments in the code is greatly appreciated to help people understand the program.

Although none of the extra credit was attempted, the clean, structured, organized code wins me over. Once again, congratulations run1206.

I invite you to choose the next Beginners programming challenge. Just create a thread titled 'Beginners programming challenge #2'. 

Well done to all that entered the challenge, although you may not have won, your efforts were still greatly appreciated and I spent just as much time looking over your code as i did run1206's. Please continue to submit entries to the next challenge.

Thank you,

Bodsda

P.S: Tinivole wins the obfuscation award, the prize is, a [link]("http://www.thinkgeek.com/tshirts-apparel/unisex/generic/a69c/")

P.S.S: The award for going well over the top goes to eightmillion, congratulations, and here is you [link]("http://www.thinkgeek.com/tshirts-apparel/unisex/frustrations/374d/?cpg=ab")

---

### Post by sujoy on 2009-03-23
congrats run1206 :)

waiting for the next challenge :D

---

### Post by Frank Kotler on 2009-03-24
Congratulations run1206! And thanks for the judgin', Bodsda!

Nice clean, easy to follow code... but I have a small "issue" with it. If I type, "Help! Give me the answer!", it tells me I'm wrong in an apparently infinite loop (haven't waited it out to see... some day when I have more time, perhaps...). I don't see why it's doing that. Is it "just me"? Maybe I compiled it wrong? Something about "cin" I don't get?  (I'm clueless in C++)

Best,
Frank

---

### Post by Froodolt on 2009-03-24
I know that I'm way to late...
But lacking a new challenge, want to give it a go anyway...

Please comment my code as much as possible!
I'm learning Java, so if anyone has hint or tips...
I know it throws an exception when you don't put an int in.
Tied to catch the exception, but couldn't get it running.
Whats the best way to do this??...

```
import javax.swing.JOptionPane;

public class TheGuessGame {
	private String result= "wrong";
	int count= 0;
	int answer= 1;
	
	public TheGuessGame(){
		answer = (int) (Math.random()*99)+1;
		
		while (getResult().equals("wrong")){
			int input = UserInput();
			String theResult = Check(input);
			setResult(theResult);
			count++;
			Output(theResult, input, count);
		}
		System.exit(0);
	}

	public void setResult(String theResult) {
		result=theResult;
		
	}

	public String getResult() {
		return result;
	}

	private int UserInput() {
		String guess=JOptionPane.showInputDialog(null, "Pick a number between 1 and 100","GuessTheNumberGame", JOptionPane.QUESTION_MESSAGE);
		int intGuess = Integer.parseInt(guess);
		return intGuess;
	}

	private String Check(int input) {
		String check;
		if(input==answer){
			check="hit";
		}else{
			check="wrong";
		}
		return check;
	}

	private void Output(String result2, int input, int count) {
		if (result.equals("hit")){
			JOptionPane.showMessageDialog(null, "Congratulations\n "+input+" is the correct number!\n It took you "+count+" guesses","Right!!" , JOptionPane.INFORMATION_MESSAGE);
		} else {
			JOptionPane.showMessageDialog(null, "Sorry\n"+input+" is not the winning number", "WRONG!", JOptionPane.INFORMATION_MESSAGE);
		}
		
	}

	public static void main(String[] args) {
		TheGuessGame theGuessGame=new TheGuessGame();

	}

}
```

Thanks \\:D/

EDIT:
Comment on myself:
Why do you input "theResult" in method "Output" if you don't use it?... :o

---

### Post by sujoy on 2009-03-24
> **Froodolt said:**
> I know that I'm way to late...
But lacking a new challenge, want to give it a go anyway...

Please comment my code as much as possible!
I'm learning Java, so if anyone has hint or tips...
I know it throws an exception when you don't put an int in.
Tied to catch the exception, but couldn't get it running.
Whats the best way to do this??...

<snip>


atleast give some hint like the number is higher or lower. otherwise its wild guessing :P also when the number is wrong, it'd be better if you could keep the first window visible IMO, now its looks kinda jumpy.

other than that, the interface looks cool :) well done


EDIT: exceptions are handled via try-catch block

```

return-type function name (params, ...) throws someException {
    other code as needed
    try {
        do something that might throw exception, like divide by 0
    } catch (someException exception-variable) {
        handle the error, or ignore it
    }
    other code as needed....
}
```

---

### Post by Chokkan on 2009-03-24
Thanks to all who entered. A very entertaining and educational read so far.

---

### Post by Froodolt on 2009-03-24
> **sujoy said:**
> atleast give some hint like the number is higher or lower. otherwise its wild guessing :P.....

Yes your right... :p
Changed it a bit:
```
import javax.swing.JOptionPane;

public class TheGuessGame {
	private String result= "wrong";
	int count= 0;
	int answer= 1;
	
	public TheGuessGame(){
		answer = (int) (Math.random()*99)+1;
		
		**while (!(getResult().equals("hit"))){**
			int input = UserInput();
			String theResult = Check(input);
			setResult(theResult);
			count++;
			Output(theResult, input, count);
		}
		System.exit(0);
	}

	public void setResult(String theResult) {
		result=theResult;
		
	}

	public String getResult() {
		return result;
	}

	private int UserInput() {
		String guess=JOptionPane.showInputDialog(null, "Pick a number between 1 and 100","GuessTheNumberGame", JOptionPane.QUESTION_MESSAGE);
		int intGuess = Integer.parseInt(guess);
		return intGuess;
	}

	private String Check(int input) {
		String check="wrong";
		if(input==answer){
			check="hit";
		}
		[B]if(input>answer){
			check="lower";
		}
		if(input<answer){
			check="higher";
		}
		[/B]
		return check;
	}

	private void Output(String check, int input, int count) {
		if (result.equals("hit")){
			JOptionPane.showMessageDialog(null, "Congratulations\n "+input+" is the correct number!\n It took you "+count+" guesses","Right!!" , JOptionPane.INFORMATION_MESSAGE);
		} else {
			JOptionPane.showMessageDialog(null, "Sorry\n"+input+" is not the winning number\n **Hint: "+check**, "WRONG!", JOptionPane.INFORMATION_MESSAGE);
		}
		
	}

	public static void main(String[] args) {
		TheGuessGame theGuessGame=new TheGuessGame();

	}

}

```
Above code should be better, when it comes to the guessing, it gives "higher" and "lower" hints... 


> **sujoy said:**
> ....also when the number is wrong, it'd be better if you could keep the first window visible IMO, now its looks kinda jumpy.

Hmmm... your right again... :p
Should keep it a question screen till its the right guess... I guess...:-k

**EDIT:**
[I]To (!(make)) it jumpy... I should draw a frame and draw the rest in that same frame, I think...
Should have a look at that chapter... haven't done that chapter yet... :o
[/I]

> **sujoy said:**
> 
EDIT: exceptions are handled via try-catch block

```

return-type function name (params, ...) throws someException {
    other code as needed
    try {
        do something that might throw exception, like divide by 0
    } catch (someException exception-variable) {
        handle the error, or ignore it
    }
    other code as needed....
}
```
Gave it a try but I couldn't get it working. Must be something I overlooked or something...:-k

Thanks for the review!! :-D

---

### Post by FireFoxer on 2009-03-24
I know that the contest is over, but I wanted to post my code anyway.  The code is C++. It would be really great if any of you more experienced programmers could go over it and give me some pointers.
```

#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main()
{
  srand(time(0));
  int numRand = (rand() % 100) + 1;
  int numGuess = 0;
  
  while(numGuess != numRand)
  {
    cout << "Guess an integer from 1-100: ";
    cin >> numGuess;
    if(numGuess > numRand)
    {
      cout << "Guess lower next time\n";
    }
    else if(numGuess < numRand)
    {
      cout << "Guess higher next time\n";
    }
    else
    {
      cout << "You got it!\n";
    }
  }
  return 0;
}

```
P.S. Does anyone know how to validate the input for this program?  Whenever I tried, it went into a never-ending loop.

---

### Post by run1206 on 2009-03-24
Thanks All!!!  
didn't know my code would win :lol: 

i enjoy doing these kind of challenges, keeps me on my toes with programming :D
i'll post up the next challenge tomorrow evening. ;)

@Frank Kotler: i'll try to write up another version to recognize a worded response and catch the exception a lil later this week.

---

### Post by Frank Kotler on 2009-03-24
Okay... sounds like FireFoxer is having the same(?) problem. Just telling me it's "wrong" is okay, but going into a loop sounds like "six-legged misbehavior" to me. No idea how to fix it.

Looking forward to the next challenge!

Best,
Frank

---

### Post by FireFoxer on 2009-03-25
Frank,

I had been trying to solve the input validation issues by using an **if ... else **statement to control when the input was actually accepted.  It worked as intended in that the input was only accepted when the value was an integer from 1-100 but did not work as intended in that the **else** section of the loop repeated indefinitely when a string or invalid input was used.

---

### Post by NathanB on 2009-03-25
> **FireFoxer said:**
> Frank,

I had been trying to solve the input validation issues by using an **if ... else **statement to control when the input was actually accepted.  It worked as intended in that the input was only accepted when the value was an integer from 1-100 but did not work as intended in that the **else** section of the loop repeated indefinitely when a string or invalid input was used.

I think the reason you and *run1206* are having this problem is because numGuess is **typed** as an int.  The compiler inserts conversion mechanics between "cin >>" and your variable.  This conversion function will always choke on data that it isn't **expecting** to be there.

I think a better route would be to type numGuess as a *char array* and then try to convert that string to a number *after* you have determined that it contains only valid numeral characters.

Nathan.

---

### Post by FireFoxer on 2009-03-26
Finally got a solution to the input validation, thanks to nathan's tip about using a **char array** to store the input in before validation. Here is the code:
```

#include <iostream>
#include <cstdlib>
#include <ctime>
#include <cctype>
using namespace std;

int main()
{
  srand(time(NULL));
  int numRand = (rand() % 100) + 1;
  char guess[50];
  int numGuess = 0;
  
  while(numGuess != numRand)
  {
    cout << "Guess an integer from 1-100: ";
    cin >> guess;
    if(isdigit(guess[0]))
    {
      numGuess = atoi(guess);
      if(numGuess > 0 && numGuess <=100)
      {
	if(numGuess > numRand)
	{
	  cout << "Guess lower next time\n";
	}
	else if(numGuess < numRand)
	{
	  cout << "Guess higher next time\n";
	}
	else
	{
	  cout << "You got it!\n";
	}
      }
      else
      {
	goto tryagain;
      }
    }
    else
    {
      tryagain:
      cout << "Please enter an integer from 1-100\n";
    }
  }
  return 0;
}

```

---

### Post by sujoy on 2009-03-26
well i found this to be a more accepted manner of taking number inputs

```

#include <iostream>
#include <limits>

using namespace std;

int main ()
{
    int number;
    cout << "enter an integer :: ";
    while (!(cin >> number)) {
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
        cout << "enter an integer :: ";
    }
    cout << "the number you entered is, " << number << endl;
    return 0;
}

```

---

### Post by kk0sse54 on 2009-04-28
Thanks bodsa for rejuvinating the Beginner Challenges, after not having programmed in months here's yet again another python entry. I had some troubles with variables and it seems unnecesarrily long but it should (hopefully :p) work with a super simple config file.

[PHP]#!/usr/bin/env python
import sys
import os
import random
choice = 0
num = 0
score = 20
menuChoice = 0

def config():
    if len(sys.argv) == 1:
        print "!: No config_file, using default settings\n" 
    else:
        try:
            config_file = os.path.basename(sys.argv[1])
            if config_file[-3:] == ".py":
                config_file = config_file[:-3]
            data_config = __import__(config_file, globals(), locals(), [])
            global bottom
            global top
            bottom =  data_config.BottomNum
            top =  data_config.TopNum
        except:
            print "[W]: Invalid config_file, using default settings. \n[W]: Syntax for using config file: %s config_file\n" % os.path.basename(sys.argv[0])
        
def rand(bottom,top,score):
    while score != 0:
        num = random.randint(bottom,top)
        choice = raw_input("Guess a number--> ")
        if choice == "quit": 
            print "Goodbye!"
            sys.exit()
        try: 
            choice = int(choice)
            if choice == num: 
                print "Correct"
                score += 5 
                print "Your score: %s \n" % score
            else: 
                print "Wrong, the correct number was ", num
                score -= 5
                print "Your score: %s \n" % score
        except: 
            print "Invalid option, please type a number."
    print '''
__   __            _                   _ 
\ \ / /__  _   _  | |    ___  ___  ___| |
 \ V / _ \| | | | | |   / _ \/ __|/ _ \ |
  | | (_) | |_| | | |__| (_) \__ \  __/_|
  |_|\___/ \__,_| |_____\___/|___/\___(_) \n'''

    
def GetMenu(menu):
    print menu 
    global menuChoice
    while 1:
        try:
            menuChoice = raw_input("Select a menu option: ")
            menuChoice = int(menuChoice)
            if menuChoice  not in range(1,3):
                print "Invalid Option"
            else:   
                break
        except:
            print "Invalid Option"

            
            
def main():
    global top
    global bottom
    bottom = 1
    top = 100
    config()
    print "Welcome to the number guessing game.\nYou start out with 20 points and with every right or wrong answer 5 points is either deducted or added. \n\nThe range for guessing is currently set at %s to %s. Restart the program with a config file to change the default values \n" % (bottom,top)
    menu = "[1] Start Game \n[2] Quit "                  
    GetMenu(menu)
    while menuChoice == 1:
        rand(bottom,top,score)
        GetMenu(menu)
    sys.exit()
   
if __name__ == "__main__":
    main()[/PHP]

And the horribly abstract config file :D
```

BottomNum = 2
TopNum = 22
```

---

### Post by soltanis on 2009-04-29
Yet Another Common Lisp Solution (YACLS):

```

(defvar *number* (random 101 (make-random-state)))

; Ask for input
(defun get-answer nil
	(format t "what is your guess? ")
	(force-output)
	(parse-integer (read-line)))

; Finish
(defun finish nil
	(format t "that is correct!~%")
	(quit))

; Check the input
(defun is-answer (x)
	(cond ((= x *number*) (finish))
			((< x *number*) (format t "guess higher!~%"))
			((> x *number*) (format t "guess lower!~%"))))

; Loop, querying
(defun ask-until-something-happens nil
	(is-answer (get-answer))
	(ask-until-something-happens))
	
(defun start nil (ask-until-something-happens))

(format t "type (start) to begin!~%")

```

EDIT.
Aww over already?

---

### Post by bgs100 on 2009-07-26
My humble C solution:
:)

[PHP]#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
     int guess, answer;

     srand(time(NULL));
     answer = (rand() % 100) + 1;
     do {
          printf("Guess the number: ");
          scanf("%d", &guess);
          if (guess < answer)
               puts("Too low.");
          if (guess > answer)
               puts("Too high.");
     } while (guess != answer);
     puts("You Won!");
     return 0;
}[/PHP]

New to C, but not programming.
**However,** this doesn't fully satisfy requirements as it won't handle bad input.
I'll (probably) be adding that later

---

### Post by dandaman0061 on 2009-08-07
I also am improving my C language-fu

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

int main(void)
{
        int num;
        int guess;
        char guess_buffer[20];

        printf("I'm thinking of a number between 1 and 100\n");

        /* initialize random seed */
        srand(time(NULL));
        /* get random number between 1-100 */
        num = (rand() % 100) + 1;

        fputs("... alright I'm ready, guess it!\n", stdout);
        fflush(stdout);

        while (1) {
                /* get the user input from the stdin */
                if (fgets(guess_buffer, sizeof guess_buffer, stdin) != NULL) {
                        /* search for newline character */
                        char *newline = strchr(guess_buffer, '\n');
                        if (newline != NULL) {
                                /* overwrite newline with NULL */
                                *newline = '\0';
                        }
                }

                /* attempt to convert to a decimal */
                if (sscanf(guess_buffer, "%d", &guess) != 1) {
                        /* here is where we would call func to parse words */
                        printf("Invalid input... must be an integer!\n");
                        continue;
                }

                if (guess < num) {
                        printf("Too low, try again...\n");
                        continue;
                } else if ( guess > num) {
                        printf("Too high, try again...\n");
                        continue;
                } else {
                        printf("You got it!\n");
                        break;
                }
        }

        return 0;
}

```

Thank you [http://www.daniweb.com/tutorials/tutorial45806.html#](http://www.daniweb.com/tutorials/tutorial45806.html#)

---

### Post by hakermania on 2010-03-14
My C code:
```

#include <iostream>
#include <cstdlib>
#include <time.h>

using namespace std;

int main()
{
        //initialize random seed
        srand ( time(NULL) );

        int randomNumber = 0;
        randomNumber = (rand()%100)+1;
        int numGuess = 0;
        cout << "Guess a number between 1 and 100." << endl;

        cin >> numGuess;

        while (numGuess < randomNumber)
        {
                        cout << "Wrong. Guess higher!!!" <<endl;
                        cin >> numGuess;

        }
        while (numGuess > randomNumber)
        {
                        cout << "Wrong.Guess lower!!!" << endl;
                        cin >> numGuess;

        }

                cout << "Correct!" << endl;


    return 0;
}
```

---

### Post by Elfy on 2010-03-14
Thread closed - current challenge is here [http://ubuntuforums.org/showthread.php?t=1424102](http://ubuntuforums.org/showthread.php?t=1424102)

---

