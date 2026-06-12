---
title: "Dictionaries and the formatting function: Python basics"
date: 2017-08-07
forum: Programming Talk
---

### Post by Drone4four on 2017-08-07
Take a look at the python script (code copied at the end of this post). I got it from a learn-to-program magazine. The rock-paper-scissors game code is intended to teach basic python programming.  

I can follow along line by line in the script and mostly understand what is going on.  The two areas which I don&#8217;t really understand are lines 40 and 76.

At line 39, the names variable creates a dictionary distinguishing the previously declared variable &#8220;rock&#8221; to be printed as the string &#8220;Rock&#8221;.  Same is true for paper and scissors.  I think I understand that much. But in the next line, line 40, the rules variable is declared as a dictionary containing rock: scissors, paper: rock, scissors: paper.  Here I&#8217;m confused.  What is happening at this line? I understand the relationship at least.  Like, I get that rock *beats* scissors, paper *beats* rock, scissors *beats* paper.  Those are the rules.  But how does the colon bind that relationship of &#8216;beat&#8217; between the three sets of two corresponding variables?

The documentation found in the magazine explaining lines 39 and 40 read: > 
Here we specify the rules for the game, and the text representations of each move for the rest of the code. When called upon, our script will print the names of any of the three moves, mainly to tell the player how the computer moved. These names are only equated to these variables when they are needed &#8211; this way, the number assigned to each of them is maintained while it&#8217;s needed.
I get the first sentence there.  But the final sentence escapes me. Can anyone shed some light here or lend a helping hand? How would you explain what is happening on line 40?

With respect to the other line which I don&#8217;t understand, it's line 76, which reads: 

```
 print "Computer threw {0}!".format(names[computer])

```

It&#8217;s a string printed with a variable which will change every time you run the script, indicated by the {0}.  What is the formatting function doing? I Google &#8216;format function python&#8217; which turned up the official python doc on the subject. It reads:

> 
Perform a string formatting operation. The string on which this method is called can contain literal text or replacement fields delimited by braces*{}. Each replacement field contains either the numeric index of a positional argument, or the name of a keyword argument. Returns a copy of the string where each replacement field is replaced with the string value of the corresponding argument.


...which completely escapes me as well. Any thoughts?

Thanks for your attention. 

I kept the line numbers in the code sample below to enhance readability here on this forum.  Attached is the raw code so you can try it out yourself if you are so inclined.  

```
  1 # !/usr/bin/env python2
  2 
  3 '''
  4 
  5 Rock, Scissors, Paper: The Video Game
  6 
  7 Copyright (c) 2015 Linux User & Developer
  8 
  9 Permission is hereby granted, free of charge, to any person obtaining a copy
 10 of this software and associated documentation files (the "Software"), to deal
 11 in the Software without restriction, including without limitation the rights
 12 to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
 13 copies of the Software, and to permit persons to whom the Software is
 14 furnished to do so, subject to the following conditions:
 15 
 16 The above copyright notice and this permission notice shall be included in
 17 all copies or substantial portions of the Software.
 18 
 19 THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 20 IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 21 FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 22 AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 23 LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 24 OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
 25 SOFTWARE.
 26 
 27 '''
 28 
 29 import pdb
 30 import random
 31 import time
 32 
 33 # initiation of variables
 34 
 35 rock = 1
 36 paper = 2
 37 scissors = 3
 38 
 39 names = { rock: "Rock", paper: "Paper", scissors: "Scissors" }
 40 rules = { rock: scissors, paper: rock, scissors: paper }
 41 
 42 player_score = 0
 43 computer_score = 0
 44 
 45 def start():
 46         print " "
 47         print "Whaddya say, lets play a game of Rock, Paper, Scissors, shall we?"
 48         while game():
 49                 pass
 50         scores()
 51 
 52 def game():
 53         player = move()
 54         computer = random.randint(1,3)
 55         result(player, computer)
 56         return play_again()
 57 
 58                 print " "  #"[placeholder]"
 59                 player = raw_input("Rock = 1 \nPaper = 2 \nScissors = 3\nChoose a hand >>    ")
 60                 print " "  #"[placeholder]"
 61                 try:
 62                         player = int(player)
 63                         if player in (1,2,3):
 64                                 return player
 65                 except ValueError:
 66                         pass
 67                 print "Ooops! I didn't understand that. Please enter 1, 2 or 3."
 68 
 69 def result(player, computer):
 70         print "Sea..."
 71         time.sleep(0.75)
 72         print "Sum..."
 73         time.sleep(0.75)
 74         print "Sue..."
 75         time.sleep(0.25)
 76         print "Computer threw {0}!".format(names[computer])
 77         global player_score, computer_score
 78         print " "  #"[placeholder]"
 79         if player == computer:
 80                 print "Tie Game"
 81         else:
 82                 if rules[player] == computer:
 83                         print "Your victory has been assured"
 84                         player_score += 1
 85                 else:
 86                         print "The player laughs as you realize you've been defeated"
 87                         computer_score += 1
 88 
 89 def play_again():
 90         answer = raw_input("Would you like to play again? >>    ")
 91         if answer in ("y", "yes", "Yes", "Y", "Of Course"):
 92                 return start()
 93         elif answer in ("n", "no", "No", "N", "Nope"):
 94                 print "Thank you for playing our game. See you next time!"
 95                 return scores()
 96         else:
 97                 print "I didn't quite get that.  Please try again."
 98                 return play_again()
 99 
100 def scores():
101         global player_score, computer_score
102         print "HIGH SCORES"
103         print "Player: ", player_score
104         print "Computer: ", computer_score
105 
106 if __name__ == '__main__':
107         start()

```

---

### Post by norobro on 2017-08-09
I think that the definition of a dict is clearer in the Python3 docs [https://docs.python.org/3/tutorial/datastructures.html#dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries).> It is best to think of a dictionary as an unordered set of key: value pairs, with the requirement that the keys are unique (within one dictionary). ...
...
The main operations on a dictionary are storing a value with some key and extracting the value given the key. ...



You shouldn't get too wrapped around the axle over line 40. The actual logic is in the result() function. The only call to rules is on line 82```

 76         print "Computer threw {0}!".format(names[computer])
 77         global player_score, computer_score
 78         print " "  #"[placeholder]"
 79         if player == computer: 
 80                 print "Tie Game"
 81         else:
 82                 if rules[player] == computer:    
 83                         print "Your victory has been assured"
 84                         player_score += 1
 85                 else:
 86                         print "The player laughs as you realize you've been defeated"
 87                         computer_score += 1
```If the player picks rock (1) and the computer picks scissors (3) line 79 is false so the else is executed. On line 82 rules[player] "rules[1]" returns 3, which is the value for key 1. The if statment is true (3==3) therefore "Your victory has been assured" and one point is added to your score. 

Follow the logic if the player had picked paper.

Regarding your question about the format function, maybe this link will help:  [https://docs.python.org/2/library/string.html#format-string-syntax](https://docs.python.org/2/library/string.html#format-string-syntax)

Some alternatives:```
>>> print "Computer threw ", names[computer], "!"
Computer threw Scissors ! # notice the space before the exclamation point? [https://docs.python.org/2/reference/simple_stmts.html?highlight=print%20statement#the-print-statement](https://docs.python.org/2/reference/simple_stmts.html?highlight=print%20statement#the-print-statement)
>>> print "Computer threw " + names[computer] + "!"  # can get messy 
Computer threw Scissors!

```

---

### Post by Drone4four on 2017-08-12
Thank you, **@norobro**, for your help.  The Python3 doc is instructive.

One way of I’m now thinking about dictionaries (like in the context of this script for example) is that they are like a declaration of one variable's association with other variables.  In this case, 1 “becomes” 3. 

In the result function at lines 69-87, the rules declared intially are only true for a winning player. The losing positions could conceiveably be scissors loses to rock (3 vs. 1), but such a relationship is an "Other" possibility (and unnessary one for this script) becasue in this script, the Other potential assoications are going to be automatically wrong (the false ones).

At line 82, let's say player previosuly picked 3 and the computer picked 2.  According to the rules dictionary, 3 becomes (or is converted) to a 2.  AND since the new player value, 2, is equal to the computer's value, the conditional result at line 82 is TRUE, so Python then prints victory for the player.  I think I get it.

When the rules variable is called, Python at line 82 will ‘test’ the variable’s relationship: is it going to be equivalent to the computer’s choice? If yes (true), then the player wins and gets a point.  If not (false), then the computer wins and gets the point.

The “break out” key lesson I applied here is that at line 82, there are three variables at play (rules, player and computer).  Python doesn’t understand the names of rules, player and computers *by themselves*.  The only thing Python registers or sees are *the numbers* assigned to those variables.  If the player chose Rock, Python only sees ‘1’, as was described and initiated at the beginning of the script.  Likewise I declared that 1 (rock) is associated or ‘becomes’ a 3 (scissors) in the dictionary.  So at line 82, the player’s new value is 3. And if the computer picked  3 as well, the two values are equivalent and therefore the player wins.  If the two values are not equivalent, the computer wins.

Let’s take a closer look at line 82:
```
  if rules[player] == computer: 
```
Here Python sees, 'rules[1] == 3’ where the rules dictionary specifies that ‘1 becomes 3’.  And since 3 == 3, the player wins and proceeds to get one more point.

Do I get it now, or what? ):P

---

### Post by The Cog on 2017-08-12
That's showing a good understanding, but to put it in my words as well:

The dict rules provides a lookup (e.g. 'rock':'scissors'). The fact that the relationship is "beats" as in rock beats scissors is not embodied in the contents of the dict, but in how the dict is used in lines 82-87.
You could add an intermediate variable that might make the code logic more readable:```

 82                 beatable = rules[player]    # look up which shape can be beaten by the player's shape
 83                 if computer == beatable:
 84                         print "Your victory has been assured"
 85                         player_score += 1
 86                 else:
 87                         print "The player laughs as you realize you've been defeated"
 88                         computer_score += 1
```

The print string formatting is a little hard to get used to. The easiest one to understand is an ordered list of arguments:
```
>>> print "{1} before {2} but after {0}".format("red", "green", "blue")
green before blue but after red
```
Or you can name the format arguments:
```
>>> print "Roses are {x}, violets are {y}".format(y="blue", x="red")
Roses are red, violets are blue
```
or you can use a dict:
```
>>> colourmap = {"blood":"red", "grass":"green", "sky":"blue"}
>>> print "blood is {x[blood]}, grass is {x[grass]} and the sea is {x[sky]}".format(x=colourmap)
blood is red, grass is green and the sea is blue
```

---

### Post by Drone4four on 2017-08-12
Thanks, **@The Cog** .  I think using the beatable variable is more readable.

From this same magazine is some more sample code, this time for a &#8220;hanged man&#8221; game instead of "rock-paper-scissors".   

I copied each line for hangedman. When I ran my transcribed script, it paused at a few lines giving me traceback indicating errors.  I made some changes.  Now the script executes but it stops at other points and I can&#8217;t figure out why.  Here is the traceback:

```

$ python hangedman.py                          
Let's play a game of Linux Hangman

Take a guess at the mystery word.1

Traceback (most recent call last):
  File "hangedman.py", line 89, in <module>
    start()
  File "hangedman.py", line 15, in start
    while game():
  File "hangedman.py", line 33, in game
    if len(letter)==1 and letter.isalpha():
NameError: global name 'letter' is not defined
$
```

I am looking at lines 88-89, and as far as I can tell, they are perfect transcriptions of what I see in the magazine. Same for line 15.  I am at a loss here. Would any of you care to please take a look at the code below and provide a little advice?

Here is [my public GitHub project]("https://github.com/Angeles4four/PyMag-games-with-tkinter") based on the code so far.  There are two more scripts which I intend on transcribing, one is a game and the other is a tkinter front end.  For now I am working with hangedman.  If you don't have GitHub, please find attached a copy of this hangedman script.  You can also view it [here in a pastebin]("https://pastebin.com/WpGiHsLT"). Here is the code with line numbers:

```

  1 #!/usr/bin/env python2
  2 
  3 from random import *
  4 
  5 player_score = 0
  6 computer_score = 0
  7 
  8 def hangedman(hangman):
  9         graphic =[ """ base""","""first attempt made""", """ second attempt""","""third attempt ""","""fourth attempt """,""" fifth attempt """,""" make your sixth and final attempt!"""]
 10         print graphic[hangman]
 11         return
 12 
 13 def start():
 14         print "Let's play a game of Linux Hangman"
 15         while game():
 16                 pass
 17         scores()
 18 
 19 def game():
 20         dictionary=["gentoo", "ubuntu", "arch", "slackware", "fedora", "suse"]
 21         word = choice(dictionary)
 22         word_length = len(word)
 23         clue = word_length * ["_"]
 24         tries = 6
 25         letters_tried = ""
 26         guesses = 0
 27         letters_right = 0
 28         letters_wrong = 0
 29         global computer_score, player_score
 30 
 31         while (letters_wrong != tries) and ("".join(clue) != word):
 32                 letters=guess_letter()
 33                 if len(letter)==1 and letter.isalpha():
 34                         if letters_tried.find(letter) != -1:
 35                                 print "You've already picked", letter
 36                         else:
 37                                 letters_tried = letters_tried + letter # what about using letters_tried += 1 instead ???
 38                                 first_index=word.find(letter)
 39                                 if first_index == -1:
 40                                         letters_wrong += 1
 41                                         print "Sorry,", letter, "isn't what we're looking for."
 42                                         # what about swapping lines 40 with 41  - - would that behave the same way? 
 43                                 else:
 44                                         print "Congratulations", letter, "is correct."
 45                                         for i in range(word_length):
 46                                                 if letter == word[i]:
 47                                                         clue[i] = letter
 48                 else:
 49                         print "Go ahead, choose another."
 50 
 51                 hangedman(letters_wrong)
 52                 print " ".join(clue)
 53                 print "Guesses: ", letters_tried
 54 
 55                 if letters_wrong == tries:
 56                         print "Game Over"
 57                         print "The word was, ", word
 58                         computer_score += 1
 59                         break
 60                 if "".join(clue) == word:
 61                         print "You Win!"
 62                         print "The word was, ", word
 63                         player_score += 1
 64                         break
 65         return play_again()
 66 
 67 def guess_letter():
 68         print
 69         letter = raw_input("Take a guess at the mystery word.")
 70         letter.strip()
 71         letter.lower()
 72         print
 73         return letter
 74 
 75 def play_again():
 76         answer = raw_input("Would you like to play again? y/n:")
 77         if answer in ("y", "Y", "yes", "Yes", "Of course!"):
 78                 return answer
 79         else:
 80                 print "Thank you very much for playing our game. See you next time!"
 81 
 82 def scores():
 83         global player_score, computer_score
 84         print "HIGH SCORES"
 85         print "Player: ", player_score
 86         print "Computer: ", computer_score
 87 
 88 if __name__ == '__main__':
 89         start()

```

Thanks in advance.

---

### Post by norobro on 2017-08-12
> **Drone4four said:**
> Thank you, **@norobro**, for your help. You're welcome.

Regarding the error in post #5 the last line number listed (33) is where the error occurs. Looks like a typo:```
[COLOR=#000000][FONT=&amp] 32                 [/FONT][/COLOR][COLOR=#ff0000][FONT=&amp]letters[/FONT][/COLOR][COLOR=#000000][FONT=&amp]=guess_letter()
[/FONT][/COLOR][COLOR=#000000][FONT=&amp] 33                 if len([/FONT][/COLOR][COLOR=#ff0000][FONT=&amp]letter[/FONT][/COLOR][COLOR=#000000][FONT=&amp])==1 and [/FONT][/COLOR][COLOR=#ff0000][FONT=&amp]letter[/FONT][/COLOR][COLOR=#000000][FONT=&amp].isalpha():[/FONT][/COLOR]
```

---

### Post by Drone4four on 2017-08-12
Thanks again, **@norobro**. After replacing letters with letter at line 32, the script runs flawlessly.

So the script runs well, now I am going to spend some time trying to explain the syntax and semantics line by line.  If I have any questions I will return to this thread.

---

### Post by Drone4four on 2017-08-15
Have a look at lines 45-47: ```
 45             for i in range(word_length):
 46                     if letter == word[i]:
 47                           clue[i] = letter
```

I'm really struggling with this loop.

Let's say the word chosen by the computer is 'fedora' (terrific distro) and the letter the player chose was, 'e'.

In my confused, humble understanding, beginning at line 45, the python code says that for every iteration in the number of characters in the word_length (6), then execute the following nested conditional: if the 'e' is equal to one of the characters in 'fedora', then proceed to clue (which is 6 * ["_"]) now assigned to e.  

I'm sorry but that is my best attempt  at explaining lines 45-47 and I know I am way off, especially the last line. 

Can anyone here please lend a helping hand if you can?

Thanks for your attention.

---

### Post by Drone4four on 2017-08-16
One of my programmer friends in RL replied via email.  This is enormously helpful.  Here is what my friend has to say: > What is happening is each "iteration" (each pass) of the loop i becomes an integer starting at **0** all the way up to the length of the word minus 1, in this case fedora is 6 characters long so i becomes **0..1..2..3..4..5**  Remember in programing we start counting at 0.
 
With that out of the way, because word becomes one of the strings in the dictionary, that string being "**fedora**" and strings are not only objects but an array of characters.  The next line is able to **[COLOR="#FF8C00"]test each letter of[/COLOR]** "**fedora**" starting at **position 0** which becomes "**f**" and ending at position 5 which becomes "a" the last character of the string.  In this case the variable **[COLOR="#FF8C00"]i is being used as a index, a pointer[/COLOR]** to where in the string we are testing.  We compare each character of "**fedora**" with the guessed letter in your example "**e**"
 
word = "fedora";
 
if we play the role of the loop, the loop sees
 ```

if 'e' == word[0]:
 do stuff
...
if 'e' == word[1]:
 do stuff
...
if 'e' == word[2]:
 do stuff 
```
 
and so on, so
 
 ```
word[0] becomes f (is 'e' equal to 'f'?)
...
word[1] becomes e (is 'e' equal to 'e'?)
...
word[2] becomes d (is 'e' equal to 'd') 
```
 
In essence we are "iterating" through each character of the word, comparing it to the guessed character.
 
This pattern of programming is very common, once you begin to understand it and what is happening, you will gain more experience with it as you review other example programs and eventually you will just understand it.  Right now this is all new territory for you, don't feel that your not born to be a programmer, it's an  acquired skill you gain through practice and exposure.

To paraphrase, at lines 45 and 46, for every iteration or pass in the loop (the number of passes are as many as indicated in the word_length variable - - 6 in the case of &#8216;fedora&#8217;), then if the letter (&#8216;e&#8217;) is equal to each sequence in the string or array of characters named &#8216;word&#8217; (&#8216;fedora&#8217;), then: clue (**word_length * &#8220;_&#8221; **, now: **_ _ _ _ _ _** ).  I get that far.  The next sequence in this algorithm is i again, which is a pointer or index like last time I suppose. Is this where Python knows to put &#8216;e&#8217; in the second place of the six underscores?  So it now looks like: **_ e _ _ _ _**.  Can someone please try to explain the code at line 47?

---

### Post by backwardsbyte on 2017-08-16
when the if statement becomes true, i.e. when the guessed character matches one of the characters in the word, it then goes to that position inside clue "______" and replaces the existing _ with that letter, so in the case that you guessed e, the loop was at the second position of the word fedora when that matched, so it puts "_e____" does that make any sense?

---

