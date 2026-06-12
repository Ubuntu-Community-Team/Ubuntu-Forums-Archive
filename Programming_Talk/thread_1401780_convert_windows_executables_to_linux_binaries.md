---
title: "convert windows executables to linux binaries?"
date: 2010-02-08
forum: Programming Talk
---

### Post by Vahagn_IV on 2010-02-08
Hi all.

May be the question will seem stupid, but can anyone explain me why there is no windows executables to linux binaries converter. Some program that will open exe file and replace all windows specific things with corresponding linux ones. Is it impossible to do(if so, why??) or is it forbidden for of some license problems.

Thanks in davance.

---

### Post by Zugzwang on 2010-02-08
First of all, analysing binary executables is an extremely difficult task as they often do not contain enough meta-data to do this task.

Then, relative code jump addresses, that happen a lot in assembly will fail if instruction A is replaced by A' with a different length. Unfortunately, binary code is full of explicit and implicit such values that need to be changed. The implicit ones are very hard to detect.

Finally, often there is no equivalence in Linux. Consider for example some piece of code listing all available drive letters. What would you change it to?

---

### Post by doas777 on 2010-02-08
the binary is not the problem, since we are all on x86/64, but what the binary does, is another matter all together.

a win32 binary will call a number of windows system interfaces to perform it;s tasks. they have names like GetUnsafeWindowHandle() or whatever. 
there is no function in the linux system libraries that is called that, or that will perform the same tasks in the same fashion.

wine attempts to present a set of windows system interfaces to act as an environment for windows code to run. it sits in the middle and translates GetUnsafeWindowHandle to calls that linux can support. 

ok, to directly answer your question, yes it is a breach of most closed source licenses to decompile, disassemble, or otherwise reverse engineer packaged executables, as you suggest. additionally the process of "porting" (moving an app from one platform to another) is far from simple.

just remember, you can do almost nothing with binary, unless you have some kind of source (even assembler) to work with. otherwise, it's just a blob.

---

### Post by pirate_tux on 2010-02-08
> **Vahagn_IV said:**
> Hi all.

May be the question will seem stupid, but can anyone explain me why there is no windows executables to linux binaries converter. Some program that will open exe file and replace all windows specific things with corresponding linux ones. Is it impossible to do(if so, why??) or is it forbidden for of some license problems.

Thanks in davance.

Ask Micro&oft to make a program which converts windows executables to linux binaries.
Then post here the Micro$oft reply ;)

---

### Post by Bachstelze on 2010-02-08
> **Vahagn_IV said:**
> Some program that will open exe file and replace all windows specific things with corresponding linux ones.

That's what WINE does (or at least attempts to do, with varying success depending on the "windows specific things" the program in question uses).

---

### Post by Vahagn_IV on 2010-02-08
Thank you guys  for your answers.

> **pirate_tux said:**
> Ask Micro&oft to make a program which converts windows executables to linux binaries.
Then post here the Micro$oft reply ;)
What do you expect from them? If I were from Microsoft I would ignore that question and IMHO would be right.

> **Zugzwang said:**
> First of all, analysing binary executables is an extremely difficult task as they often do not contain enough meta-data to do this task.
...



> **doas777 said:**
> the binary is not the problem, since we are all on x86/64, but what the binary does, is another matter all together.
...



As far as I understand this just mean that it is extremely hard but not principally unsolvable problem. At least, there is no exact proof. Right??


> **Zugzwang said:**
> 
 Consider for example some piece of code listing all available drive letters. What would you change it to?

May be that's the case when program should ask user what to do??:-k

---

### Post by Vahagn_IV on 2010-02-08
> **Bachstelze said:**
> That's what WINE does (or at least attempts to do, with varying success depending on the "windows specific things" the program in question uses).

In fact, I want to play windows games under Ubuntu and Wine fails to make them work properly. :)

---

### Post by Ferrat on 2010-02-08
> **Bachstelze said:**
> That's what WINE does (or at least attempts to do, with varying success depending on the "windows specific things" the program in question uses).

No, WINE does nothing like that, WINE is simply an API sandbox, like an interpreter, while the result might be seen as similar it's two completely different things actually changing Windows programs to Linux programs and putting a translator in between the program and the system. 

It's like the difference of getting a translated book and having someone reading the book in it's original language but reading out loud in your native language, say that this book is an instruction book, in a translation it would take in to account your way of putting things and reference things in a more "logical" way (from your point of view) but when told back to you then you just get the "idea" of what you need to do and try and go from there, you can see it as a language with different grammar.
From German to English for ex. much will be almost the same but there will be differences both in wording and phrasing as well as maybe cultural references etc that doesn't really match up, in a translation these would be taken in to account and corrected and re-edited for to better suite English, but someone just translating word for word on the fly more or less while reading these corrections aren't always present since the reader might not know what is going to be said later and have no real way of compensating for that like a fully translated work would have.

> **Vahagn_IV said:**
> In fact, I want to play windows games under Ubuntu and Wine fails to make them work properly. :)

What games, that would make helping you easier if it's possible :)

---

### Post by Vahagn_IV on 2010-02-08
> **Ferrat said:**
> 
What games, that would make helping you easier if it's possible :)
Empire Total War and Civillization IV

---

### Post by doas777 on 2010-02-08
civ 4 is definetly doable in wine, but you will have to apply several native overrides for msxml and a few others. check winedb and google arround for instructions.

---

### Post by Bachstelze on 2010-02-08
> **Ferrat said:**
> No, WINE does nothing like that, WINE is simply an API sandbox, like an interpreter, while the result might be seen as similar it's two completely different things actually changing Windows programs to Linux programs and putting a translator in between the program and the system. 

It's like the difference of getting a translated book and having someone reading the book in it's original language but reading out loud in your native language, say that this book is an instruction book, in a translation it would take in to account your way of putting things and reference things in a more "logical" way (from your point of view) but when told back to you then you just get the "idea" of what you need to do and try and go from there, you can see it as a language with different grammar.
From German to English for ex. much will be almost the same but there will be differences both in wording and phrasing as well as maybe cultural references etc that doesn't really match up, in a translation these would be taken in to account and corrected and re-edited for to better suite English, but someone just translating word for word on the fly more or less while reading these corrections aren't always present since the reader might not know what is going to be said later and have no real way of compensating for that like a fully translated work would have.

Pedantic much? Plus your analogy doesn't work, you're comparing apples and oranges. A computer program is just a sequence of instructions, it doesn't have "cultural references", either it produces the intended result, or it does not. If it does, you have successfully converted it.

---

### Post by doas777 on 2010-02-08
> **Vahagn_IV said:**
> Thank you guys  for your answers.
As far as I understand this just mean that it is extremely hard but not principally unsolvable problem. At least, there is no exact proof. Right??


almost impossible. if it were possible then there would be far more decompilers on the market that actually work.

the bigger problem than figuring out what the binary says, is converting the instructions to work with the system. the wine team has been at that for years and years and still haven't perfected it.

---

### Post by ubername on 2010-02-08
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15915](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15915)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514)

for the two games you mention.

---

### Post by Vahagn_IV on 2010-02-08
> **doas777 said:**
> civ 4 is definetly doable in wine, but you will have to apply several native overrides for msxml and a few others. check winedb and google arround for instructions.

That's not a solution. :( Moreover if you have only 1Gb of RAM...

---

### Post by djbushido on 2010-02-08
Since there doesn't seem to be a good description of WINE - What happens is Wine translates calls from windows programs to calls for linux programs - when a windows application calls a directX function, wine tries to get the same thing to run with linux. Wine is a binary layer, not a recompiler.
Also, if you're trying to do gaming, recompiling is not where you should be at. : )
On a side note, UNDER NO CIRCUMSTANCES SHOULD YOU ATTEMPT TO PROGRAM IN BINARY!!!! It's next to impossible.
My shpeal is done.

---

### Post by doas777 on 2010-02-08
> **Vahagn_IV said:**
> That's not a solution. :( Moreover if you have only 1Gb of RAM...
neither is dynamically porting binaries.

---

### Post by pirate_tux on 2010-02-08
> **Vahagn_IV said:**
> Thank you guys  for your answers.


What do you expect from them? If I were from Microsoft I would ignore that question and IMHO would be right.



If I were from Linux I would ignore that question and IMHO would be right.

LOL You're so funny.

---

### Post by Vahagn_IV on 2010-02-08
2pirate_tux
I guess you mixed the place to have a fun. I assure you, there was nothing funny neither in the question nor in Micro$oft's policy. But if you really laghed, moreover laughed out loud then I suggest you to go outside and play with a ground. That is much more funny. If you don't like playing with ground try to eat it! Tell me when you have done.

---

### Post by djbushido on 2010-02-08
Chill out.
Point is there is no way to dynamically change windows to linux at run time. Programs can be re-compiled, re-interpreted (both Python and WINE), but there is technically nothing that exists according to your question.
If you are doing gaming though, check out wine.

---

