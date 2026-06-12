---
title: "Another newbie Python question"
date: 2008-12-19
forum: Programming Talk
---

### Post by abraxas_swa on 2008-12-19
Thanks for taking the time to have a look!

I'm having some strange output from this script:

```
import random

responses = {"hi":["Hello.", "Howdy!", "Whussup?"],
	     "hello":["Hey!", "Hi there!", "How are you?"]}
			
user_says = raw_input("Please enter text to chat.\nEnter \"quit\" at any time to exit.\n: ")

while user_says != "quit":
	user_says = user_says.lower()
	user_list = user_says.split()
	format_list = []
	for word in user_list:
		if word[-1].isalpha() == False:
			format_list.append(word[0:-1])
		else:
			format_list.append(word)
	for word in format_list:
		if word in responses:
			user_says = raw_input(random.choice(responses[word]) + "\n: ")
		else:
			user_says = raw_input("Sorry, I don't understand.\n: ")
			
print "It's been nice talking to you."
```


It seems that at random intervals, the script fails to recognise a word which is in the responses dictionary. Any pointers as to what I'm doing wrong would be appreciated. In addition, any time a word present in responses is entered with punctuation, the script fails to recognise it. Would there be a better way of removing nonalpha characters?


Sample output:

```
Please enter text to chat.
Enter "quit" at any time to exit.
: Hi there.
Hello.
: Hi there.
Sorry, I don't understand.
: Hello
How are you?
: Hello
Hey!
: Hello there.
Hey!
: Hello, how are you?
Sorry, I don't understand.
: 
```

Thanks in advance for your help.

---

### Post by digitalvectorz on 2008-12-19
To debug something like this, i'd recommend printing out at each step the variables your referring to, i.e. word, word[-1], word[0:-1] etc. to see exactly what is being evaluated in your script.

Good debugging techniques are useful for getting stuff to work like this :-)

---

### Post by fiddler616 on 2008-12-19
> **digitalvectorz said:**
> To debug something like this, i'd recommend printing out at each step the variables your referring to, i.e. word, word[-1], word[0:-1] etc. to see exactly what is being evaluated in your script.

Good debugging techniques are useful for getting stuff to work like this :-)
I've found that it's sometimes helpful using the interactive shell to accomplish this.

---

### Post by Martin Witte on 2008-12-19
I also would add 
```
for i in responses:
	print i

```
right after you define dictionary responses to help you see why something else happens than what you probably expect to happen

---

### Post by mssever on 2008-12-19
> **Martin Witte said:**
> ```
for i in responses:
    print i

```
Or just ```
print responses
```

---

### Post by Martin Witte on 2008-12-19
> **mssever said:**
> Or just ```
print responses
```
This is a differenent approach, the command I suggested prints the keys of the dictionary, where you print the whole dictionary.

---

### Post by pmasiar on 2008-12-19
pretty-print : [http://docs.python.org/library/pprint.html](http://docs.python.org/library/pprint.html) is excellent for debug prints - even of whole structures. Batteries included! :-)

---

### Post by Strike4!! on 2008-12-21
but it would be no fun there for you. I think you will learn much more discovering what's going on by yourself -and you will have much more fun too!!

So here it is you code with just two strategically placed print orders:

```
import random

responses = {"hi":["Hello.", "Howdy!", "Whussup?"],
	     "hello":["Hey!", "Hi there!", "How are you?"]}
			
user_says = raw_input("Fuerza! Please enter text to chat.\nEnter \"quit\" at any time to exit.\n: ")


while user_says != "quit":
	user_says = user_says.lower()
	user_list = user_says.split()
	format_list = []
	for word in user_list:
		if word[-1].isalpha() == False:
			format_list.append(word[0:-1])
		else:
			format_list.append(word)
	**print 'format_list is:',format_list**
	for word in format_list:
		**print 'word    out of   user_list:',word**
		if word in responses:
			user_says = raw_input(random.choice(responses[word]) + "\n: ")
		else:
			user_says = raw_input("Sorry, I don't understand.\n: ")
			
print "It's been nice talking to you."
```


Go and run it, using your input that worked at random:
First input ---> Hi there.
Second input --> Hi there.
You will spot the problem easily, i guess.

Programming is fun!!!! Learning too!!!!:)

---

### Post by nvteighen on 2008-12-21
There's a logic problem in your program, consequence of bad design. Hint: try printing what words are being analyzed each time and never mix implementation and interface ;)

---

### Post by abraxas_swa on 2008-12-21
Hey folks, thanks for your responses and your patience with a newcomer!

I think I've pretty much got it. Kicked myself when I saw what I'd done. Please correct me if I'm wrong, but:

When the user entered a string, for example, "Hi, how are you" the for loop would proceed to proceed to user_formatted[0] (i.e. "hi") and I'd get a positive result. If the user then entered "Hello." the word checked would actually be "how" - right?

I now have:

```

import random

responses = {"hi":["Hello.", "Howdy!", "Whussup?"],
	     "hello":["Hey!", "Hi there!", "How are you?"]}
			
user_says = raw_input("Please enter text to chat.\nEnter \"quit\" at any time to exit.\n: ")

while user_says != "quit":
	user_says = user_says.lower()
	user_list = user_says.split()
	format_list = []
	for word in user_list:
		print word[-1], "- Last char in word."
		if word[-1].isalpha() == False:
			format_list.append(word[0:-1])
			print format_list, " - The current list"
		else:
			format_list.append(word)
	for word in format_list:
		if word in responses:
			user_says = raw_input(random.choice(responses[word]) + "\n: ")
		else:
			user_says = raw_input("Sorry, I don't understand.\n: ")
			
print "It's been nice talking to you."
```

Any better?

---

### Post by nvteighen on 2008-12-21
Another hint: what's the program's state when asking the user for input?

---

### Post by Strike4!! on 2008-12-21
but you didn't solve it!!

still, with the new code you're posting, you will have the problem:

> : hi, man
, - Last char in word.
['hi']  - The current list
n - Last char in word.
Hello.
: hi
Sorry, I don't understand.


As you said, in your FOR loop, **for word in format_list:**, there is a problem. I'll make you this question: When is the program out of that loop?
And then, what happens if my first input is "Hi Space fighter" and then "hi" and "hi"? Why does the program answer that both "hi" are not understood? Is it checking against those Hi or against something else?

We can help you, but use the hints! ***_Take the code i wrote for you in my previous post_***, and use it to understand what's going on. You're almost there!!

---

### Post by abraxas_swa on 2008-12-21
Ah, crap! I had the previous version open along with the modified one and, having had a couple of beers with dinner, copied and pasted the wrong one.

Strike4!!, thanks for your help. I used your code and changed things accordingly:

```

import random

responses = {"hi":["Hello.", "Howdy!", "Whussup?"],
	     "hello":["Hey!", "Hi there!", "How are you?"],
	     "glider":["Sugar gliders are sooo cute!", "I'd love some gliders!"]}
			
user_says = raw_input("Please enter text to chat.\nEnter \"quit\" at any time to exit.\n: ")

while user_says != "quit":
	user_says = user_says.lower()
	user_list = user_says.split()
	format_list = []
	for word in user_list:
		if word[-1].isalpha() == False:
			format_list.append(word[0:-1])
		else:
			format_list.append(word)

	word_hit = False
	for word in format_list:
		if word_hit == False:
			if word in responses:
				word_hit == True
				user_says = raw_input(random.choice(responses[word]) + "\n: ")
				break
			else:
				continue
		else:
			user_says = raw_input("Sorry, I don't understand.\n: ")
			
print "It's been nice talking to you."

```

Apologies for the confusion!

---

### Post by Strike4!! on 2008-12-21
Ok. We have some problems here.

First, the program does not work. I mean, if you input some wrong expression like "DWade", you fall into an infinite loop. 

That said, you still have the problem of not recognizing when someone types "Hi!!", because of the double exclamation point.

But the worst thing that just happened to you are those break/continue...
Please, please, for your own good, avoid them!! The infinite loop you're creating is due to those devil creations. Because the continue will, as supposed, continue, but will re-enter the FOR loop without changing the word, so you will run endlessly that piece of code analyzing the same word...


So, a couple of hints:

For the problem of checking if there is an occurrence of your words/expressions into the string, look here:
[http://docs.python.org/whatsnew/2.3.html#string-changes](http://docs.python.org/whatsnew/2.3.html#string-changes)
See? Get used to Documentation. It saves lives!!!
Specially in python. Remember, batteries included!!!!

Of course, you will run into some other problems ('China' will be a false positive). You can, you should make some other checking. But it's a start.


Now, make a version that works with "Hi!!" and with "Sir, hello, sir!", and WITHOUT USING break and continue, and we can improve from there.

Come on, just a couple of yards to a working dialogs program!!!!:P

---

### Post by nvteighen on 2008-12-22
> **Strike4!! said:**
> 
But the worst thing that just happened to you are those break/continue...
Please, please, for your own good, avoid them!! The infinite loop you're creating is due to those devil creations. Because the continue will, as supposed, continue, but will re-enter the FOR loop without changing the word, so you will run endlessly that piece of code analyzing the same word...


What? Ok, break and continue are in fact camouflaged goto's, but restricted to a block and therefore, are structured programming. I don't get why you should avoid them.

----
@OP:
The mistake is what I advanced in a post: OP, you're mixing interface and implementation. In real programs, you'd have at least two different functions: one that analyzes the user's input and generates the response and another that takes the input and outputs the response (moreover, I'd separate this one in two and make everything called from a flow-control function called "main()", à la C).

The idea: one task : one function; one function : one task. You must never have the same task be done in two separate places; you must never have the same function do two different tasks.

But, obviously, for such a small code, using that much functions would be overkill. So, let's reduce it to your program. For example, why are you asking the user for input in three separate places? You can reduce them into a single raw_input() call.

This will simplify your code **a lot**. And will make everything much clearer for further debugging/development. And you'll catch the bugs much more easily...

---

### Post by Strike4!! on 2008-12-22
> What? Ok, break and continue are in fact camouflaged goto's, but restricted to a block and therefore, are structured programming. I don't get why you should avoid them.

;)Break and continue are always, by definition, "restricted into a block". So using your reasoning you can always say that goto is part of structured programming. Uh oh.

He's learning programming, and he's trying to write actual code. You think it's ok for him to use break and continue? 
By the way, reading his code you will notice that he had an infinite loop, and that was because of those break and continue. So telling him to put them aside and to try to write code without them is the best way to go. Instead of telling him to rewrite almost the whole thing, let him learn and understand. So, I think, the way to go is to give him some idea on when his program does not work, and eventually some hint for him to do the work of discovering why. We can really help, not just in a particular problem, but in his programming skills as a whole, if we let him chose, make mistakes, etc. That's why I was trying to help him make the program  work. Once that stage is achieved, well, we can tell him about the convenience of functions or about using logical blocks and constants, and so many other things to make his code look and behave better.

OP
Of course, with my heart I advice you not to use break and continue; you should make it always with the usual loops. Once you have really programmed a lot maybe, just maybe you will find some things that can be done slightly better with the goto family.../and that depends on what 'better' means to you-... but at any beginner/intermediate stage, you should avoid them, period. They tend -strongly- to make you think in just the way your program is written -and that nv rightly points as the biggest problem-: messy, without a plan on what things have to be done and how to write a few functionalities that get executed over and over using the right structures to flow.
I can go on and on, but there are whole threads about the argument. The point is that i've never seen a defense on the use of gotoisms in a beginner/intermediate level, well, not until today. However, whatever my position on this matter is, those are the reasons why your program does not work properly in this case. So, changing your program a little bit into the looping part will do the magic. You can always use our hints; my advice is to first make it work. After that, explore that command for checking for a substring into another. Play a little bit with it, and use it in your program. That will lead to a redesign of the program -you will do it by your own, your code shows you're capable of doing it-, and you will also have used the online documentation, which is a great thing to learn. And then, go and see if you can change your code to use just one raw_input. There, you will do some redesigning of your code again, but you will get the idea by your own. And, after that, the most important lesson of all, go and check your first code. You will be amazed.
Btw, the whole tour should take a few hours. 
Go, and have fun!!!

---

### Post by nvteighen on 2008-12-22
> **Strike4!! said:**
> 
He's learning programming, and he's trying to write actual code. You think it's ok for him to use break and continue? 
By the way, reading his code you will notice that he had an infinite loop, and that was because of those break and continue. So telling him to put them aside and to try to write code without them is the best way to go. Instead of telling him to rewrite almost the whole thing, let him learn and understand. So, I think, the way to go is to give him some idea on when his program does not work, and eventually some hint for him to do the work of discovering why. We can really help, not just in a particular problem, but in his programming skills as a whole, if we let him chose, make mistakes, etc. That's why I was trying to help him make the program  work. Once that stage is achieved, well, we can tell him about the convenience of functions or about using logical blocks and constants, and so many other things to make his code look and behave better.

What? How can a break yield an infinite loop? The break is needed. The bug is not how the OP is using them but actually a step back... an unneeded condition check that's forcing him to misuse one of these keywords (I'm trying hard to not spoil the answer). Plus, the interface/implementation issue that's messing the whole code over.

Break is an interrupt, so it's semantically the same as a return. Continue is more like a goto, but there's a critical difference: a continue's outcome is always predictable from the elements inside the loop. A goto, instead, is not easily predictable, as you may jump to any place in the code... therefore, suddenly changing context and well... everything.

Of course, instead of break/continue you can start using control flags that "deviate" the program's flow... Yes, it's feasible, but it needs lots of nested if's that will make this program a lot more complex. Such an approach is better for other situations, e.g. short functions that will return something anyway, so you just return once and set the returning variable before.

---

### Post by pmasiar on 2008-12-22
> **Strike4!! said:**
> ;)Break and continue are always, by definition, "restricted into a block". So using your reasoning you can always say that goto is part of structured programming. Uh oh.

BS. GOTO is very different from break/continue, it is unstructured and jumps out of context. break/continue are just shortcuts, more convenient than using if/then/else. If you cannot see this, i wonder what else you are missing.

Strike4!!> He's learning programming, and he's trying to write actual code. You think it's ok for him to use break and continue? 

Yes, definitely, when appropriate.

Strike4!!> By the way, reading his code you will notice that he had an infinite loop, and that was because of those break and continue. 

that's theoretically impossible. block condition take care of that (or not), but no break/continue.

---

