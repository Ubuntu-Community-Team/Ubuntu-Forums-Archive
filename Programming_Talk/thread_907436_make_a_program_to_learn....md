---
title: "make a program to learn..."
date: 2008-09-01
forum: Programming Talk
---

### Post by hockey97 on 2008-09-01
Hi I saw a couple of hacking movies like one called wargames ect. Old movies.

I saw a program on it that would learn the passwords by trial and error.

it would try every letter and number.

Is this possible to program or is this just a movie stunt??

kinda interesting because you could make a smart AI program.

---

### Post by Wybiral on 2008-09-01
Trial and error would only work if you had a hash (a brute-force attack), and is exactly why you should always make your password long enough and with a mix of characters. The number of permutations with a large enough alphabet and enough digits makes it almost impossible without a large farm of computers churning away.

But what does this have to do with AI?

---

### Post by crazyfuturamanoob on 2008-09-01
Why not? The program would just try out every possible combination.
String variables don't take too much memory, don't they?

---

### Post by Can+~ on 2008-09-01
Read: [Rainbow tables](http://en.wikipedia.org/wiki/Rainbow_table)

> **crazyfuturamanoob said:**
> Why not? The program would just try out every possible combination.
String variables don't take too much memory, don't they?

Think about permutations (order counts, repeatable characters).

Let's say you got [Extended ASCII](http://www.asciitable.com/), (255 characters - 32 restricted characters = 223 (this might not be accurate, nor real))

Now, for each letter you got:

223 * 223 * 223 ... (nth character) 223 = 223^n.

You got 223^n combinations to try out. Let's say you have a 10 character password, that is equivalent to 304122555034158459939649 possible combinations.

And that's why you also add salt to a password hash.

---

### Post by CptPicard on 2008-09-01
I seem to recall Wargames had a wardialler that just went through phone numbers by brute force... nothing to do with AI whatsoever :)

---

### Post by Reiger on 2008-09-01
Let's assume completely unrealistically that we have passwords of a fixed length; of an alphabet alpha-numeric characters which is to say 62 unique characters.

Consider the case the fixed length is 10 characters -> 62 to the power of 10 possible things to try, of which only 1 matches the given (indeed, given?!) username.

Now 10 characters barely stands out from the usual absolute minima of 8 characters; let's relax this constraint, but maintain an upper bound of 10 characters:
Then the total permutations amounts to the sum of the terms: [0<=k<=10]*62^k

Or in simple English:
62^0 + 62^1 + 62^2 ... + 62^10.

That adds up. And we still maintain our program needs to cope with up to 10 chars only; not exactly realistic. (Having seen forms that would allow up to 20 chars easily.) And then think about the fact that we still get the Username for free.

---

### Post by hockey97 on 2008-09-01
> **CptPicard said:**
> I seem to recall Wargames had a wardialler that just went through phone numbers by brute force... nothing to do with AI whatsoever :)

I know it didn't have any AI. I am saying couldn't you make a program to have an AI that learns from it's errors.

I mean in war games I saw where the computer tries to find a match with the nuke launch code so it tries every letter and numbers that is on a keyboard.
Then it find the first part of the code and then tries the second part until it finds it.

I wanted to know if this can be a true program. Like you said I know of a brute force tool where it just uses a password lists and tries each password in the txt file.

but I am saying can you really make a program with if can learn the password.

like it would try every letter in a keyboard and find each letter one by one of the password.

this would also be a good AI concept of trial and error.

I mean if you were to make a computer game and created an AI for the enemy that would learn from evetns like if you attack the guy in certain areas on the game map and it has been done frequently then the AI of the enemy would then adjust if it's in the same situation again.

---

### Post by jimi_hendrix on 2008-09-01
possible: 99.9% sure but i would have no clue how to make it know what text box to put the answer in to and how it would know if it was right

---

### Post by rogeriopvl on 2008-09-01
You have no way to know if one character is part of the password or not. You can only try complete set of characters at once, and you also need to have the password hash or feed the password and user name to the login prompt. But in this last case, you would be making allot of "noise".

---

### Post by hockey97 on 2008-09-01
Well I am going to try to learn AI  so I can made good computer games.


would you know how to code cleanly?? Like what is the industry standard in computer programming.

I want to start to learn how to code cleanly and easily... meaning using less code to do a task.

---

### Post by tamoneya on 2008-09-01
> **hockey97 said:**
> I know it didn't have any AI. I am saying couldn't you make a program to have an AI that learns from it's errors.

I mean in war games I saw where the computer tries to find a match with the nuke launch code so it tries every letter and numbers that is on a keyboard.
Then it find the first part of the code and then tries the second part until it finds it.

I wanted to know if this can be a true program. Like you said I know of a brute force tool where it just uses a password lists and tries each password in the txt file.

but I am saying can you really make a program with if can learn the password.

like it would try every letter in a keyboard and find each letter one by one of the password.

this would also be a good AI concept of trial and error.

I mean if you were to make a computer game and created an AI for the enemy that would learn from evetns like if you attack the guy in certain areas on the game map and it has been done frequently then the AI of the enemy would then adjust if it's in the same situation again.

There isnt anything to learn from guessing passwords.  Say I guess "aaaaaaaaaa".  The only thing I gain from that is knowing whether or not "aaaaaaaaaa" is or isnt the password.  It tells me nothing about any other passwords so I have to continue trying passwords like "aaaaaaaaab".

---

### Post by Wybiral on 2008-09-01
Not unless your hash function sucked really bad :) But REAL hash functions make that impossible... That's why we use them ;)

---

### Post by loganwm on 2008-09-01
The more characters that you could have "blacklisted" then your number of possibilities also shrinks drastically.

Just For example:

On a 10 digit keypad for example, in a password of 6 characters in length with no "blacklisted" characters then your number of total possibilities is massive, it shrinks by a power of 10, which is a decent chunk of your incorrect solutions gone per each blacklisted char.

This example implies malicious intent, but it's the best way I can phrase it:

If you've seen someone enter their key and you know for a fact that the zero key and the 3 key are not used at all in the password then here's the comparison:

No Blacklisted:
6^10 = 60,466,176

2 Keys Blacklisted:
6^8 = 1,679,616

The more keys that you know are not included in the password, then the smaller number of possibilities there are that need to be tried.

---

### Post by rogeriopvl on 2008-09-01
> **loganwm said:**
> The more characters that you could have "blacklisted" then your number of possibilities also shrinks drastically.

Just For example:

On a 10 digit keypad for example, in a password of 6 characters in length with no "blacklisted" characters then your number of total possibilities is massive, it shrinks by a power of 10, which is a decent chunk of your incorrect solutions gone per each blacklisted char.

This example implies malicious intent, but it's the best way I can phrase it:

If you've seen someone enter their key and you know for a fact that the zero key and the 3 key are not used at all in the password then here's the comparison:

No Blacklisted:
6^10 = 60,466,176

2 Keys Blacklisted:
6^8 = 1,679,616

The more keys that you know are not included in the password, then the smaller number of possibilities there are that need to be tried.

That's a nice approach.

---

### Post by rogeriopvl on 2008-09-01
> **hockey97 said:**
> Well I am going to try to learn AI  so I can made good computer games.


would you know how to code cleanly?? Like what is the industry standard in computer programming.

I want to start to learn how to code cleanly and easily... meaning using less code to do a task.

The best way is reading books about it, and practice the examples, then start implementing your own ideas, etc. The books part is very important to understand the ways to make your code clean.

---

### Post by CptPicard on 2008-09-01
> **loganwm said:**
> 
The more keys that you know are not included in the password, then the smaller number of possibilities there are that need to be tried.

... which is why any half-decent password system will not allow you to guess individual characters.

---

### Post by loganwm on 2008-09-01
> **CptPicard said:**
> ... which is why any half-decent password system will not allow you to guess individual characters.

The algorithm I referenced doesn't guess individual characters at all, it just doesn't include "blacklisted" characters when running through the different possible complete strings to pass on.


And about the AI regarding the password generation:

An AI could possibly serve to prioritize which combinations are "more likely" to be passwords than others, mainly, passwords that resemble words and phrases in a "dictionary" could be tested before obscure combinations for the password such as "aaaaaabaa".

AI could also receive input on optional related information that could potentially help with solving a password such as birthdate and other personal information (provided that you would have this information).

Although much of AI discussion is theoretical.

---

### Post by rogeriopvl on 2008-09-01
> **loganwm said:**
> The algorithm I referenced doesn't guess individual characters at all, it just doesn't include "blacklisted" characters when running through the different possible complete strings to pass on.


And about the AI regarding the password generation:

An AI could possibly serve to prioritize which combinations are "more likely" to be passwords than others, mainly, passwords that resemble words and phrases in a "dictionary" could be tested before obscure combinations for the password such as "aaaaaabaa".


For that you have GPW, a program that generates "pronouncable" words.

[http://linuxappfinder.com/package/gpw](http://linuxappfinder.com/package/gpw)

---

### Post by loganwm on 2008-09-01
> **rogeriopvl said:**
> For that you have GPW, a program that generates "pronouncable" words.

[http://linuxappfinder.com/package/gpw](http://linuxappfinder.com/package/gpw)

With the right combination of sequencers and combination generation you could have a decent brute password generator :), but there are plenty of things preventing a decent password cracker from being fast enough to be useful.

Anything internet based requires a query to the server to check each password and each password would need to be checked until the correct one is found.

(number of possibilities) * (amount of time to query) = (an unreasonable amount of total time)

Local password cracking is a bit more practical, but it's still a highly inefficient way of doing things.

Put best:
[http://xkcd.com/463/](http://xkcd.com/463/)

---

### Post by mssever on 2008-09-01
> **loganwm said:**
> Anything internet based requires a query to the server to check each password and each password would need to be checked until the correct one is found.

(number of possibilities) * (amount of time to query) = (an unreasonable amount of total time)

Local password cracking is a bit more practical, but it's still a highly inefficient way of doing things.
Ideally, any system that checks passwords should sleep for, say, 5 seconds (especially if it isn't operating over the Internet) before rejecting a bad password. That would make a brute force attack impractical. It would also likely make a dictionary attack much more difficult, if not impractical.

---

### Post by loganwm on 2008-09-01
> **mssever said:**
> Ideally, any system that checks passwords should sleep for, say, 5 seconds (especially if it isn't operating over the Internet) before rejecting a bad password. That would make a brute force attack impractical. It would also likely make a dictionary attack much more difficult, if not impractical.

The less feedback that a system gives the brute force attack the better, but, Brute Force still is a very interesting process.

---

### Post by slavik on 2008-09-01
> **loganwm said:**
> With the right combination of sequencers and combination generation you could have a decent brute password generator :), but there are plenty of things preventing a decent password cracker from being fast enough to be useful.

Anything internet based requires a query to the server to check each password and each password would need to be checked until the correct one is found.

(number of possibilities) * (amount of time to query) = (an unreasonable amount of total time)

Local password cracking is a bit more practical, but it's still a highly inefficient way of doing things.

Put best:
[http://xkcd.com/463/](http://xkcd.com/463/)

try opening a login shell and see how many wrong passwords you enter to get the system to not respond for a minute.

if the system goes into a hard sleep for 1 second on the first failed try and doubles that every failure ... you will start waiting for hours within 20 passwords. (I have not done the math)

there are 1000 combinations of numbers 0-9 if the password is length 3.

---

### Post by hariputtar on 2008-09-01
[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by loganwm on 2008-09-01
> **slavik said:**
> try opening a login shell and see how many wrong passwords you enter to get the system to not respond for a minute.

if the system goes into a hard sleep for 1 second on the first failed try and doubles that every failure ... you will start waiting for hours within 20 passwords. (I have not done the math)

there are 1000 combinations of numbers 0-9 if the password is length 3.

Which is why it's incredibly impractical.

---

### Post by lordhaworth on 2008-09-03
If your interested in AI, why not try... AI!

Make a real simple game that the computer has to learn to play.

For example I recently had a go at my first AI for a naughts and crosses game ([http://ubuntuforums.org/showthread.php?t=876022](http://ubuntuforums.org/showthread.php?t=876022))

In the end I stored the board layout, the move made and the previous success of every move the computer makes in a file. If it doesnt have a move for a particular board layout stored (or it is a rubbish move) in its memory file it will play randomly. Otherwise it plays the most successful move for that situation. At the end of the game it records all the moves it made to the file and amends the success depending on whether it won or lost.

Such a style means you have to teach the computer to play coherently, a process i intend to make easier by making it "watch" the human players moves too and recording those moves in the file. 

You could probably implement something like this in most basic games.

I dont think what your proposing as a code cracker would be worth using AI for, in fact I dont think a non - systematic approach would be a help at all.

---

