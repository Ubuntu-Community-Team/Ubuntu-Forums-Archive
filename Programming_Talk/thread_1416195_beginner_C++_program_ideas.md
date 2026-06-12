---
title: "beginner C++ program ideas"
date: 2010-02-25
forum: Programming Talk
---

### Post by smdawson on 2010-02-25
I am quite new to c++ and I was looking for basic program ideas. I saw the "beginner c++ challenges", but I am more beginner than those.... 

In class we are going through repetition statements. So my practice project was making a calculator-like application that performs basic mathematical operations.

Next we go through functions, arrays and cStrings, then file I/O and data manipulation. Any ideas to help me learn or practice these elements?

---

### Post by Queue29 on 2010-02-25
[http://javabat.com/](http://javabat.com/)

is awesome for going from beginner to intermediate problems. Even though it's in java, the syntax is very similar to C and C++ at this level.

---

### Post by dwhitney67 on 2010-02-25
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by smdawson on 2010-02-25
these both look very good, thanks!

---

### Post by n0dix on 2010-02-25
1. Do a palindrome program, alucard = dracula
2. Do your own version of Quick Sort.

---

### Post by Neezer on 2010-02-25
Some easy things and fun things that I did was cards and dice...I did craps, blackjack, and even the basics of risk. I had a program work out risk scenarios based on how many men the attacker and defender had, and the probabilities of who would win...quite interesting I though....think of something that you might like to try and get to work...I made a small text based role playing game back in college. anything to get you used to the syntax and experience with all sorts of different aspects..reading and writing to files, working with arrays and vectors, creating classes to make things a bit easier, and functions to make things prettier....

Anything that gets you on the keyboard writing code will help.

---

### Post by smdawson on 2010-02-26
@n0dix. The palindrome sounds like fun and a good idea (Going to start that tonight ), and the same goes for a quick-sort program.  

@Neezer. I have made a small interactive RPG and that was fun. Games involving AI like a good challenge, but I wouldn't even know where to start. I will look into it though, and thank you for the great suggestions.

---

### Post by lavinog on 2010-02-26
> **smdawson said:**
> I am quite new to c++ and I was looking for basic program ideas. I saw the "beginner c++ challenges", but I am more beginner than those.... 

In class we are going through repetition statements. So my practice project was making a calculator-like application that performs basic mathematical operations.

Next we go through functions, arrays and cStrings, then file I/O and data manipulation. Any ideas to help me learn or practice these elements?

Make a simple game.  Don't focus on graphics or even a gui.  Start with a console based game.  As you learn more, expand that game.
A fun project is to make a mastermind type game.  One that I made was a simple bulls and cows game that I played in the military. [Bulls and cows](http://en.wikipedia.org/wiki/Bulls_and_cows)

---

### Post by nvteighen on 2010-02-27
Hm... a Tic-Tac-Toe game with AI is a nice idea... :)

---

### Post by smdawson on 2010-02-27
I cannot find this anywhere online or in my textbook. Can you have a person input a word and then set each character as a value into an array? I tried it a bajillion different ways but I have to initialize the array, and if I do that then the size of the word cannot vary....(this is for a palindrome program. so please don't give away any more of the logic or code than just this question. thank you.)

---

### Post by n0dix on 2010-02-27
I forget to tell you that for the palindrome program the idea is to give a string and said if is palindrome, for example, arepera, for more info read the [wiki]("http://en.wikipedia.org/wiki/Palindrome")

If you want a clue, just post it.

---

### Post by smdawson on 2010-02-27
Is there an "inverse" or "reverse" function that will make a string, array, etc, backwards? If I could do that then I could check the regular and inverse input from the front and increment up until they reach half of the length of the word...

---

### Post by n0dix on 2010-02-27
supposed the function doesn't exists, what you need to compare if the word is palindrome. 

Btw, the function inverse could help you. This problem probably have more than one solution, using inverse/reverse or doing step by step.

---

### Post by Tony Flury on 2010-02-28
smdawson - in C you would use malloc and realloc to dynamically created and resize your array - in C++ there are similar methods - but I have to admit that C++ is not my strong point.

in C I would use malloc to create say a 10 character array, and use getc() to read the input at a time, and once you get to the 9th character (since you know you have to store the NULL character, I would use realloc to increase the size of the array - say to 20 characters.

---

### Post by lavinog on 2010-02-28
> **Tony Flury said:**
> smdawson - in C you would use malloc and realloc to dynamically created and resize your array - in C++ there are similar methods - but I have to admit that C++ is not my strong point.

in C I would use malloc to create say a 10 character array, and use getc() to read the input at a time, and once you get to the 9th character (since you know you have to store the NULL character, I would use realloc to increase the size of the array - say to 20 characters.

Could a linked list work?

---

### Post by smdawson on 2010-02-28
The only other language I have had experience in is Java, and not that much. Therefore, I haven't used the 'malloc' or 'realloc' functions you described for C, and I don't know what their counterparts in C++ would be...I will look into it though.

---

### Post by nvteighen on 2010-03-01
> **smdawson said:**
> The only other language I have had experience in is Java, and not that much. Therefore, I haven't used the 'malloc' or 'realloc' functions you described for C, and I don't know what their counterparts in C++ would be...I will look into it though.

There's not too much difference between Java and C++. The required mindset is quite almost the same, as opposed for example to the one required for Perl or the one for Lisp.

C 'malloc' = C++ 'new'; C 'free' = C++ 'delete'. C 'realloc' has no direct counterpart in C++.

---

### Post by Jonas thomas on 2010-03-01
> **smdawson said:**
> Is there an "inverse" or "reverse" function that will make a string, array, etc, backwards? If I could do that then I could check the regular and inverse input from the front and increment up until they reach half of the length of the word...

There is something in the Vector class to do that.
(Just did it the other day on a homework assignment).

---

### Post by smdawson on 2010-03-01
> **Jonas thomas said:**
> There is something in the Vector class to do that.
(Just did it the other day on a homework assignment).

Sounds good. I'll scour my book and the internet for vector functions. Thanks.

---

### Post by lavinog on 2010-03-01
Where is a good place to get a dictionary of words?
I am thinking you could read a file with a list of words and output which words are palindromes

---

### Post by smdawson on 2010-03-01
> **lavinog said:**
> Where is a good place to get a dictionary of words?
I am thinking you could read a file with a list of words and output which words are palindromes

I thought of that, and it seems like a great idea. However, I haven't learned how to open, read and then apply information from files into my programs yet. So, unless anyone has a good link for that in c++ or can quote a short tutorial, that's on my things-I-need-to-learn list. :)

---

### Post by lavinog on 2010-03-01
> **smdawson said:**
> I thought of that, and it seems like a great idea. However, I haven't learned how to open, read and then apply information from files into my programs yet. So, unless anyone has a good link for that in c++ or can quote a short tutorial, that's on my things-I-need-to-learn list. :)

It could be something to work up to.
I think fopen is where you would start.

also I found some word lists if you are interested:
[http://www.outpost9.com/files/WordLists.html](http://www.outpost9.com/files/WordLists.html)

---

### Post by lavinog on 2010-03-01
I decided to brush up on c.  I have been spending a lot of time with python lately.
Attached is my palindrome program written in c.
I found out that there is a word dictionary located at /usr/share/dict/words
I used a fixed length for the character array instead of using malloc. I couldn't think of any words larger than 100 characters.

Feel free to look at it and ask questions.

---

### Post by smdawson on 2010-03-02
Your palindrome.c looks good to me (although I'm a beginner so I now that doesn't mean anything). However, I understand the logic of the program and will can this as a reference for my palindrome.c++. I thought the 'real word check' function was a good idea that I hadn't previously thought of. Thanks for posting that.

---

### Post by Jonas thomas on 2010-03-02
> **smdawson said:**
> Your palindrome.c looks good to me (although I'm a beginner so I now that doesn't mean anything). However, I understand the logic of the program and will can this as a reference for my palindrome.c++. I thought the 'real word check' function was a good idea that I hadn't previously thought of. Thanks for posting that.

Just thinking loud. I'm a scrabble player.. Wouldn't it be cool to be able to take the letters you have,and have a application rip through a dictionary to figure out the which word combinations you could make. (sorry... don't mean to hi-jack a thread here.. I'm going to need to take a look at the dictionary when I get home.)

---

