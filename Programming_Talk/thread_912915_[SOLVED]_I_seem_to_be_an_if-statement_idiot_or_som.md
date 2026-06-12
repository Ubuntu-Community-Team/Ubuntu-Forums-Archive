---
title: "[SOLVED] I seem to be an if-statement idiot or something (Python)"
date: 2008-09-07
forum: Programming Talk
---

### Post by fiddler616 on 2008-09-07
I'm really sorry that this is my third stupid-question-in-Python thread.
That said, I have the following block of code, which is inspired by my [previous Python thread]("http://ubuntuforums.org/showthread.php?p=5699860#post5699860")
```
while running == True:
	while pos == "go":
		#go = 'g'ame 'over'
		running = False
	#C3
	while pos == "cthree":
		print "There are mountains to the North(8), some decimated buildings to the West(4), and empty, white plains to the South(2) and East(6)"
		aa = int(raw_input("What now?"))
		if aa == 8:
			pos = 'ctwo'
		elif aa == 4:
			pos = 'bthree'
		elif aa == 6:
			pos = 'dthree'
		elif aa == 2:
			pos = 'cfour'
		elif aa == 0:
			print inventory
		elif aa != 8 and aa != 2 and aa != 6 and aa != 4 and aa != 0:
			print "You're a really confusing person. Try again."
	#C4
	while pos == "cfour":
		#prints description of setting
		aa = raw_input("What now?")
		if aa == 8:
			pos = 'cthree'
#Etcetera etcetera etcetera
```
It used to be aa = raw_input("What now?").lower() , if aa == 'north' etcetera, but I changed it to numbers because of the bug I'm about to explain, which is still happening:

When I run it, it'll print the little spiel, say What now?, I type in a number (i. e. 8) hit Enter...and the cursor moves down a line, but nothing else happens. I can type whatever I want, hit enter, etcetera, and it'll all be reflected in the cursor, but nothing else happens at ALL (I even tried stuff like exit() ). I tried this both by running it in Geany, and by just doing "python 0.1b.py" in the console.
I feel like there must be something really easy I'm missing, but for the life of me I can't figure out what. Previous builds of the program with a similar structure worked fine in that regard...
Thanks in advance

---

### Post by fiddler616 on 2008-09-07
I guess this is actually more about raw_input, not if statements. Sorry. I can't edit the thread title though.

---

### Post by crazyfuturamanoob on 2008-09-07
> **fiddler616 said:**
> I guess this is actually more about raw_input, not if statements. Sorry. I can't edit the thread title though.
Yes, you can edit the title if you press the "Go Advanced" button next to "Save" button.

---

### Post by fiddler616 on 2008-09-07
> **crazyfuturamanoob said:**
> Yes, you can edit the title if you press the "Go Advanced" button next to "Save" button.
Thanks

---

### Post by constrictor on 2008-09-07
> **fiddler616 said:**
> I'm really sorry that this is my third stupid-question-in-Python thread.
That said, I have the following block of code, which is inspired by my [previous Python thread]("http://ubuntuforums.org/showthread.php?p=5699860#post5699860")
```
while running == True:
	while pos == "go":
		#go = 'g'ame 'over'
		running = False
	#C3
	while pos == "cthree":
		print "There are mountains to the North(8), some decimated buildings to the West(4), and empty, white plains to the South(2) and East(6)"
		aa = int(raw_input("What now?"))
		if aa == 8:
			pos = 'ctwo'
		elif aa == 4:
			pos = 'bthree'
		elif aa == 6:
			pos = 'dthree'
		elif aa == 2:
			pos = 'cfour'
		elif aa == 0:
			print inventory
		elif aa != 8 and aa != 2 and aa != 6 and aa != 4 and aa != 0:
			print "You're a really confusing person. Try again."
	#C4
	while pos == "cfour":
		#prints description of setting
		aa = raw_input("What now?")
		if aa == 8:
			pos = 'cthree'
#Etcetera etcetera etcetera
```
It used to be aa = raw_input("What now?").lower() , if aa == 'north' etcetera, but I changed it to numbers because of the bug I'm about to explain, which is still happening:

When I run it, it'll print the little spiel, say What now?, I type in a number (i. e. 8) hit Enter...and the cursor moves down a line, but nothing else happens. I can type whatever I want, hit enter, etcetera, and it'll all be reflected in the cursor, but nothing else happens at ALL (I even tried stuff like exit() ). I tried this both by running it in Geany, and by just doing "python 0.1b.py" in the console.
I feel like there must be something really easy I'm missing, but for the life of me I can't figure out what. Previous builds of the program with a similar structure worked fine in that regard...
Thanks in advance

Don't you have to put a break after the while statements completed?

---

### Post by fiddler616 on 2008-09-07
> **constrictor said:**
> Don't you have to put a break after the while statements completed?
No, not according to the tutorial I use, which has the following sample for while:
```
number = 23
running = True

while running:
	guess = int(raw_input('Enter an integer : '))

	if guess == number:
		print 'Congratulations, you guessed it.'
		running = False # this causes the while loop to stop
	elif guess < number:
		print 'No, it is a little higher than that.'
	else:
		print 'No, it is a little lower than that.'
else:
	print 'The while loop is over.'
	# Do anything else you want to do here

print 'Done'

```
Maybe I need an else though...I'll go try that.

---

### Post by fiddler616 on 2008-09-07
Adding an else did nothing.

I think the problem is with the input, not the if-statement. Sorry for the title.

---

### Post by nvteighen on 2008-09-07
I believe you're still thinking in BASIC... though a little less than the last time.

While loops are while loops (:)), i.e. they're used to control flow with respect to some defined circumstance... you're using them to create subroutines and that, although it's possible, is not the best thing to do: at the end, you'll be "hacking" flow constantly the same way you would in BASIC with labeled GOTO's.

Maybe, you should break the whole thing into functions and control function calls with those loops, defining return values for different situations (error, input, whatever). But also, try to design a better way to represent the map in your program.

An idea: use dictionaries that use some ID ("cthree", "C3", "3.3", whatever, but I highly recommend you using numbers... see below) as key and as value, a list of all items contained in that cell. That will allow you to have more than an item in the same place or easily change one place's contents according to a condition.

So, for a 3x3 map:
[PHP]
map = {0 : ["home", "heal"], 1 : [], 2 : [],
       3 : ["me"], 4 : ["dragon"], 5 : ["princess"]
       6 : ["heal", "treasure"], 7 : [], 8 : ["black hole"]}
[/PHP]

To show, say, slot 7:
[PHP]
print map[7]
[/PHP]

Then, if you want to move down, you move the "me" 3 places (to 6). Notice that moving left is moving -1, right +1, up -m, down +m for a mxn map... yes, even if it's not a square!... You could move the character by extending (read about the extend() method for list's) the target list and removing the "me" from the source, for example. Of course, any attempt to move to a place located at < 0 or > (m * n) (for mxn map) should be considered illegal (unless you might want to have some "secret areas" outside the regular map... see how improving the data structure makes your possibilities grow?)

You should write functions that are as more general as possible: a function that moves stuff from one place to another, no matter what that stuff is, whether your character or enemies that travel through the map, for example. Other function for "collecting", another for "fighting", etc. Observe the general patterns involved in the game and give them a function. The particular cases will be decided according to the parameters passed to the function.

---

### Post by DaymItzJack on 2008-09-07
If you have tons of those loops, a better thing would be to have a 'x' and 'y' variable for the user.

```
x = 3
y = 3

while running:
    # for item collection or whatever
    if isItemAtPos(x, y):
        print "you found an item!"
    pos = int(raw_input("Direction?"))
    
    if pos == 8:
        y -= 1
    elif pos == 2:
        y += 1
    elif pos == 4:
        x -= 1
    elif pos == 6:
        x += 1
    elif pos == 0:
        print 'inventory'
    else:
        print 'wrong direction'
```

Something like that.

---

### Post by fiddler616 on 2008-09-07
I understand:
The brilliance of using a dictionary
How to 'play' with dictionaries (As much as was said [here]("http://www.ibiblio.org/g2swap/byteofpython/read/dictionary.html"), at least.
The +1, -1 of map dictionary*
How to make functions, and use them
I don't understand:
The -m +m of map dictionary, but I'll take your word for it, and assume that it's used the same way as the +/- 1.
* Why 2+1 wouldn't go to map[3], but again I'll take your word for it
-------
I suddenly feel the lenght of the program being reduced tenfold :)
-------
It's always nicer checking on an active thread than making a FOURTH "Help!" thread, so:
Once I make the (rather large) dictionary (I wrote out a map on paper and it's 5x5), and make a list for the inventory, all there needs to be is a while running == True: loop that has a function running that provides the UI for playing with the dictionary--moving 'me' around, if statements about life/death depending on what's in the inventory list, etc.
pseudo-pseudo-pseudo code (not even BASIC!)
> while running == True
print contents of the 'position' cell in dictionary
var = input("What now?")
use ifs to call a function to move things around in dictionary based on var
#once running == False, this while loop won't happen, and the rest of the program is just defining functions/variables/dictionaries/lists, so the program will end.
THANK YOU!!

---

### Post by fiddler616 on 2008-09-07
> **DaymItzJack said:**
> If you have tons of those loops, a better thing would be to have a 'x' and 'y' variable for the user.

```
x = 3
y = 3

while running:
    # for item collection or whatever
    if isItemAtPos(x, y):
        print "you found an item!"
    pos = int(raw_input("Direction?"))
    
    if pos == 8:
        y -= 1
    elif pos == 2:
        y += 1
    elif pos == 4:
        x -= 1
    elif pos == 6:
        x += 1
    elif pos == 0:
        print 'inventory'
    else:
        print 'wrong direction'
```

Something like that.
Defining isItemAt will be just as long and complicated as having 25 different possibilities for the 'pos' variable, methinks. Especially since the contents of the cell need to be said. Well, I guess it's cleaner/neater. But making a dictionary for map is downright sweet.
Thanks anyway

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> ```

    while pos == "go":
        #go = 'g'ame 'over'
        running = False
```
I recommend following nvteighen's advice, but here's a note regarding your while loops: Make sure that they terminate when appropriate. This loop that I'm quoting is an infinite loop, and will never terminate under any condition short of exiting the program.

---

### Post by fiddler616 on 2008-09-07
> **mssever said:**
> This loop that I'm quoting is an infinite loop, and will never terminate under any condition short of exiting the program.
Good call...I guess it should be an if instead of a while?

---

### Post by nvteighen on 2008-09-07
> **fiddler616 said:**
> 
I don't understand:
The -m +m of map dictionary, but I'll take your word for it, and assume that it's used the same way as the +/- 1.


Ok, I'll try to explain it you so you can see there's no magic :)

Think we have this 3x5 matrix* representing the map:
```

0  1  2  3  4
5  6  7  8  9
10 11 12 13 14

```

(*) I noticed in my last post I used the unusual notation cols x rows... Though I was coherent throughout that post and therefore everything was correct, I believe it's better I use the standard rows x cols notation.

If you were in 2 and you moved down, you'd end in 7. But, the Python dictionary data type is 1D, not 2D as our matrix, so you have to simulate moving down somehow in a linear world. If you observe the matrix, you'll see that the first row starts at 0, the next at 5, the last at 10, so the "offset" due to a new line is 5... the amount of cols the matrix has. So, if you are in position x, the position right below will be x + 5 in this particular case (and x - 5, the position above). Playing around with different sizes, you'll see this is true for any dimensions you give to a rectangular grid (remember that squares are a subset of rectangles :)).

And look that you could start counting from 1 or whatever instead from 0 and this would be also valid. Just that counting from 0 makes it more evident.

> 
* Why 2+1 wouldn't go to map[3], but again I'll take your word for it


Smart guy, you hit the "flaw" in this design: if you go pass the row (2 + 1), you get into the next one... or when going backwards (5 - 1), you go back to the previous. 

But there's a little solution to that: notice that such situation (only if you start counting from 0) will only occur when you are either in the last or first element of a row. All last elements are multiples of the amount of cols minus 1 (in other words, the modulo is (cols - 1)), and all first elements are multiples of the amount of cols (the modulo is 0). In Python (and in many programming languages), you take the modulo of x in y by using x % y, so, before moving, you'd have to check if the (current position % cols) is either (cols - 1) or 0 in order to detect whether you're in the border or not.

The *very best* way to design this would be using matrices. So, you'd just use x,y coordinate pairs. The problem is that constructing a matrix in Python from lists consists in making a big list of lists... a bit like the way you do it in C with arrays. The issue you get there is that you loss the "direct access" through keys you have in dictionaries: To do any move, you'll need two coordinates instead of a single "ID" for the slot... (Programming is much related to dealing with those trade-offs).

---

### Post by fiddler616 on 2008-09-07
Yay! The world is starting to make sense!
Thank you

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> Good call...I guess it should be an if instead of a while?
That would help.

---

### Post by fiddler616 on 2008-09-07
> **mssever said:**
> That would help.
Would it help or would it solve?
(Well, it's a moot point after everything that nvteighen said, but I'm trying to learn as much per post as possible)

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> Would it help or would it solve?
(Well, it's a moot point after everything that nvteighen said, but I'm trying to learn as much per post as possible)
I agree that it's a moot point, but here's the principle: Loops are for when something should be repeated. Conditionals, such as if, are for testing a condition. So yes, changing the while to an if would remove the infinite loop, because there's no loop with if.

---

### Post by fiddler616 on 2008-09-07
> **mssever said:**
> I agree that it's a moot point, but here's the principle: Loops are for when something should be repeated. Conditionals, such as if, are for testing a condition. So yes, changing the while to an if would remove the infinite loop, because there's no loop with if.
(Re: Moot point--we should both really quite while we're ahead :) )
I [mostly]  understand the theory, I was just checking, since stranger things have happened to me in Python.
("Python is not BASIC, Python is not BASIC, Python is not BASIC...")

---

### Post by imdano on 2008-09-07
> [php]		if aa == 8:
			pos = 'ctwo'
		elif aa == 4:
			pos = 'bthree'
		elif aa == 6:
			pos = 'dthree'
		elif aa == 2:
			pos = 'cfour'
		elif aa == 0:
			print inventory
		elif aa != 8 and aa != 2 and aa != 6 and aa != 4 and aa != 0:
			print "You're a really confusing person. Try again."
[/php]That last elif really isn't necessary.  You've already tested aa for equality to each of those numbers, so there's no reason to do it again.  You could just do [php]		if aa == 8:
			pos = 'ctwo'
		elif aa == 4:
			pos = 'bthree'
		elif aa == 6:
			pos = 'dthree'
		elif aa == 2:
			pos = 'cfour'
		elif aa == 0:
			print inventory
		else:
			print "You're a really confusing person. Try again."[/php]

---

### Post by fiddler616 on 2008-09-07
> **imdano said:**
> That last elif really isn't necessary.  You've already tested aa for equality to each of those numbers, so there's no reason to do it again.  You could just do [php]		if aa == 8:
			pos = 'ctwo'
		elif aa == 4:
			pos = 'bthree'
		elif aa == 6:
			pos = 'dthree'
		elif aa == 2:
			pos = 'cfour'
		elif aa == 0:
			print inventory
		else:
			print "You're a really confusing person. Try again."[/php]
True/Good point
It still doesn't solve the error though.
And now it's a moot point (though I'm still kind of interested in why it doesn't work, even though the workaround is superior to the thing being worked around)

---

### Post by pmasiar on 2008-09-07
> **fiddler616 said:**
> II suddenly feel the lenght of the program being reduced tenfold :)

Big part of learning programming is to learn using flexible data structures. Python is substantially more flexible than ie Basic, so is easier to model your data.

As a rule of thumb, hacking Python means using dictionaries, the more the merrier :-) When you have list of dictionaries whose values are list of dictionaries, stop 8-)

---

### Post by fiddler616 on 2008-09-07
@nvteighen: Estaba repasando el 'unico (no tengo teclado internacional para tildes, disculpe) lugar donde me agradecieron, y vi que hablas espanol. No lo sabia antes, tienes ingles excelente (ingles es my lengua primaria).
Has pasado a Wybiral como mi persona favorita para ayudarme con Python :)

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> @nvteighen: Estaba repasando el 'unico (no tengo teclado internacional para tildes, disculpe) lugar donde me agradecieron, y vi que hablas espanol. No lo sabia antes, tienes ingles excelente (ingles es my lengua primaria).
Has pasado a Wybiral como mi persona favorita para ayudarme con Python :)
translate.google.com translation for the rest of us: > I was sifting through the 'one and only (I have no keyboard for international accents, sorry) where I appreciated, and I saw you speak Spanish. I do not know before, have excellent English (English is my primary language). 
 You have come to Wybiral as my favorite person to help with Python :)

---

### Post by nvteighen on 2008-09-07
> **fiddler616 said:**
> @nvteighen: Estaba repasando el 'unico (no tengo teclado internacional para tildes, disculpe) lugar donde me agradecieron, y vi que hablas espanol. No lo sabia antes, tienes ingles excelente (ingles es my lengua primaria).
Has pasado a Wybiral como mi persona favorita para ayudarme con Python :)
Muchísimas gracias, ¡pero Python no es mi lenguaje de programación principal! (antes, C y ahora Scheme Lisp). En realidad, ni siquiera soy un programador "profesional", sino un estudiante de filología/lingüística al que le gusta estudiar las características lingüísticas de estos lenguajes... y programar algo de vez en cuando.

(Before someone comes with a bad automated translation, I'll give a real one)
Thank you very much, but Python isn't even my main programming language! (first, C; now Scheme Lisp). Actually, I'm not even "professional" programmer, but a Philology/Linguistics student who likes to study the linguistic features these languages have... and also to program something occasionally.

---

### Post by fiddler616 on 2008-09-07
> **pmasiar said:**
> Big part of learning programming is to learn using flexible data structures. Python is substantially more flexible than ie Basic, so is easier to model your data.

As a rule of thumb, hacking Python means using dictionaries, the more the merrier :-) When you have list of dictionaries whose values are list of dictionaries, stop 8-)
Yeah, it's hard re-training myself to be like "Stop! There's actually an easier, shorter, more-intuitive-in-the-long-run, and more-recommended way of doing this....*data structures!*. Pretty soon I'm going to be incapable of writing good TI-BASIC programs...I guess that's a good thing though :KS

---

### Post by fiddler616 on 2008-09-07
> **nvteighen said:**
> Muchísimas gracias, ¡pero Python no es mi lenguaje de programación principal! (antes, C y ahora Scheme Lisp). En realidad, ni siquiera soy un programador "profesional", sino un estudiante de filología/lingüística al que le gusta estudiar las características lingüísticas de estos lenguajes... y programar algo de vez en cuando.

(Before someone comes with a bad automated translation, I'll give a real one)
Thank you very much, but Python isn't even my main programming language! (first, C; now Scheme Lisp). Actually, I'm not even "professional" programmer, but a Philology/Linguistics student who likes to study the linguistic features these languages have... and also to program something occasionally.
You could've fooled me :)
Before somebody automates what *I* said--never mind, I didn't F5 at the right time. Seeing as somebody has automated what I said, and done it poorly (although that's Google's fault, not the poster's):
@nvteighen: I was reviewing my only [ed: It has an accent in Spanish] (sorry, I don't have an international keyboard) [ed: It's a painful experience to not have accents] thanked post, and saw that you speak Spanish. I didn't know that beforehand--you have excellent English (English is my first language)
You've surpassed Wybiral as my favorite Python guru. :) [ed: See my other threads under Programming Talk, which have been handled masterfully by Wybrial.]

---

### Post by imdano on 2008-09-07
> **fiddler616 said:**
> True/Good point
It still doesn't solve the error though.
And now it's a moot point (though I'm still kind of interested in why it doesn't work, even though the workaround is superior to the thing being worked around)I think your original problem was because you weren't casting the the second raw_input to an int.
[php]	#C4
	while pos == "cfour":
		#prints description of setting
		aa = raw_input("What now?")
		if aa == 8:
			pos = 'cthree'[/php]should be [php]	#C4
	while pos == "cfour":
		#prints description of setting
		aa = int(raw_input("What now?"))
		if aa == 8:
			pos = 'cthree'[/php]

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> (no tengo teclado internacional para tildes, disculpe)
<off-topic>I use the US International (AltGr dead keys) keyboard layout. It lets me type English as normal, but makes characters for most Western European characters easily available. For example, é is <RightAlt>e, and ñ is <RightAlt>n. No Spanish keyboard necessary.</off-topic>

---

### Post by fiddler616 on 2008-09-07
> **imdano said:**
> I think your original problem was because you weren't casting the the second raw_input to an int.
[php]	#C4
	while pos == "cfour":
		#prints description of setting
		aa = raw_input("What now?")
		if aa == 8:
			pos = 'cthree'[/php]should be [php]	#C4
	while pos == "cfour":
		#prints description of setting
		aa = int(raw_input("What now?"))
		if aa == 8:
			pos = 'cthree'[/php]
Good spot, but that shouldn't affect the int(raw_input()) for C3.
(At least, I *think* so, the reason I'm here is that I don't know enough about Python...)

---

### Post by mssever on 2008-09-07
> **nvteighen said:**
> (Before someone comes with a bad automated translation, I'll give a real one)
Actually, Google translate only made one mistake this time, which I was able to recognize as such, even though I don't speak Spanish.

---

### Post by fiddler616 on 2008-09-07
> **mssever said:**
> <off-topic>I use the US International (AltGr dead keys) keyboard layout. It lets me type English as normal, but makes characters for most Western European characters easily available. For example, é is <RightAlt>e, and ñ is <RightAlt>n. No Spanish keyboard necessary.</off-topic>
<Even more off-topic, but I'm the OP so be quiet :)> I saw that in the Keyboard options, and was wondering what it was, but installing Ubuntu is not the time to go off researching keyboard layouts...that's really handy *Goes to System-Preferences-Keyboard and changes layout*
Thanks! (Sorry, but you don't get a real thanks for that, it'd make everybody else I thanked feel slighted :) )

---

### Post by fiddler616 on 2008-09-07
This is the lamest 100th post ever, but it's entirely worth it because I can do tricks like thís! And thát! Wahóó!
(Sorry. Really. I'll try to save myself: )
Wouldn't a 5x5 matrix in Python just be six lists? L1, L2, L3...L6
L6 = [L1, L2, L3, L4, L5]
L1 = ["dragon", "black hole", "etc"...]
L2 = ["etc", "black hole", "dragon"...]
L3 = ...
...
Although that would get sticky hopping about between them...Much easier to use the modulo. Though I'm surprised there isn't some module out there that gives matrices...

---

### Post by imdano on 2008-09-07
Oh sorry, I misread your first post.  The problem is that if you type 8, 6, or 4 the first time, pos gets in a state where no raw_input dialogs will appear.  With the change I suggested the loop works as long as you don't type any of those during the C3 raw_input.

---

### Post by fiddler616 on 2008-09-07
@imdano: OK, thanks (I'm taking your word for it, because I'm not going to open up Geany/gedit to test an obsolete program)
@mssever: I got the following for a translation:
> Thank you very much, but Python is not my main programming language! (formerly C and now Scheme Lisp). Actually, I'm not even a programmer "professional", but a student of philology / linguistics who likes to study the linguistic characteristics of these languages ... and schedule something occasionally.
programmer "professional" is obvious, but "schedule something occasionally" makes it sound like he has a rather strange relationship with his girlfriend, and is definitely not pointed at his programming habits. Maybe Google Translate is temperamental?

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> 
L6 = [L1, L2, L3, L4, L5]
L1 = ["dragon", "black hole", "etc"...]
L2 = ["etc", "black hole", "dragon"...]
L3 = ...
How about a list of lists? ```
the_list = [
    ["dragon", "black hole", "etc"],
    ["Another item", 42, "etc"],
    # and still more
]
```

---

### Post by fiddler616 on 2008-09-07
> **mssever said:**
> How about a list of lists? ```
the_list = [
    ["dragon", "black hole", "etc"],
    ["Another item", 42, "etc"],
    # and still more
]
```
I could put every single variable/string/dictionary/etcetera into a HUGE list, and submit it to an Obfuscated Python contest :)

---

### Post by mssever on 2008-09-07
> **fiddler616 said:**
> programmer "professional" is obviousI missed that one.

---

### Post by fiddler616 on 2008-09-07
> **mssever said:**
> I missed that one.
It's your destiny reminding you that you need to learn Spanish :)
Word order is actually harder to pay attention to if you're reading quickly.
Tguhoh it plaes in cmriopaosn to tihs.

---

### Post by jimi_hendrix on 2008-09-07
> **mssever said:**
> Actually, Google translate only made one mistake this time, which I was able to recognize as such, even though I don't speak Spanish.

found no errors with ubiquity but i read it fast

---

### Post by fiddler616 on 2008-09-07
Wahoo! Solved!

---

### Post by nvteighen on 2008-09-07
> **fiddler616 said:**
> 
programmer "professional" is obvious, but "schedule something occasionally" makes it sound like he has a rather strange relationship with his girlfriend, and is definitely not pointed at his programming habits. Maybe Google Translate is temperamental?

LOL... That was funny!

---

### Post by fiddler616 on 2008-09-07
@nvteighen: I try
@Everyone: Darn, I feel kind of sad now, with a solved thread. That is *not* an oxy-moron, I promise. (I can't believe we filled up five pages to say: "Try using a dictionary")

---

### Post by DaymItzJack on 2008-09-07
You also cut down your program a lot by removing tons of loops (hopefully you did).

---

### Post by fiddler616 on 2008-09-08
Yes, and throw in a function or two and it'll be downright smallish.

---

### Post by Wybiral on 2008-09-08
> **fiddler616 said:**
> Yes, and throw in a function or two and it'll be downright smallish.

A game like this is also a good excuse to utilize some OOP (having to group values and actions together into a useful class). For instance you can make a 'tile' class to that will handle the items in that tile and the dialog using some simple methods to do all of the action for things. Naturally you don't want to think too much like a Java programming and MakeAClassForEverything, but it would help organize things a bit.

---

### Post by fiddler616 on 2008-09-08
My 'technology' elective started today at school, where we're learning Java (which the teacher doesn't really know, we're basically reading a tutorial together. Lame.) So maybe by the end of it I'll understand OOP, but when I got there in my Python tutorial (Google byte of python swaroop), I realized I should reinforce all the other stuff I think I know.
Version 2 should include OOP, to make sure I understand that...which'll be about Christmas break :|
Good suggestion though, I can see how it would make sense.
(I also really like how the Ubuntu community is cool enough to keep helping me even after the thread is 'solved')

---

### Post by mssever on 2008-09-08
> **fiddler616 said:**
> So maybe by the end of it I'll understand OOP
My first programming experience was in Java, but I didn't understand OOP until I learned Ruby, where OOP is just so natural without feeling forced.

---

### Post by fiddler616 on 2008-09-08
> **mssever said:**
> My first programming experience was in Java, but I didn't understand OOP until I learned Ruby, where OOP is just so natural without feeling forced.
*Adds it to list of programs to learn, after Python, Java (for AP Comp. Sci.), CSS (for website, already know HTML), PHP (website again)....*So many languages, so little time! Though mastering Python will probably make 90% of that worthless. So Python 1st.

---

### Post by fiddler616 on 2008-09-12
In this class, apparently we're going to be using a--a *thing* (I guess the term is program...or IDE...or IDLE or something) called Karel J Robot...feedback?

---

