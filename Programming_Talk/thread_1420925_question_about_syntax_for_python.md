---
title: "question about syntax for python"
date: 2010-03-03
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-03
hello :) i just have a question about the basic syntax, being that what im trying to do is exactly this:
```

a = a list object
for x in a[:]:
 if len(x) > 3: a.append(x)

```this is pretty much the stucture of the coding that will do the command i ask it to and for each object in the list of a whos character count is great than 3 make a copy of that to the list of a. however i dont see why this wouldnt work either;
```

for x in a:
 if len(x) > 3: a.append(x)

```the only differnece in the two being the a at top at the start of the code says a[:] instead of a. it doesnt return a syntax error as i would expect it not to but instead hangs up my command window, and i dont understand why. wouldnt the if statement in the first one saying a[:] be the same thing as saying a? in the comment in the tutorial it said #make a slice copy of the entire list. i dont understand what does this mean and how does the code with the a[:] work and the code with just a doesnt? please explain lol. :popcorn:



also on the toturial it has the sections, using lists as stacks, and using lists as queues.  i just have a quesiton as i have tried pretty much the exact same code the tutorial had under a diffreent name, and it worked jsut fine. all it did was still make it a list. the only hting i see the tutorial doing is assigning the word, list, and queue to a list of object. what is so special abotu this? and what if you wanted to use more than one stack or queue? you couldnt use it under the same name so you would obviously have to name it something like queue2 or stack2. so these names apprently arent special in python as you can name queues and stacks under anything. my question is what is so special about these terms and why would you use them as opposed to a list? and stacks still come up under when i type in type(stack) returns the value a list. i mean from what i can understand using them as a queue soley means importing deque from collections library. which apprently doesnt do anythign but fast pops and appends form both ends, i can see where thast useful on large databases..etc.. but creating a database would you really use a list? lol

also the MOD thing aka %. this is bugging the candy bars outta me lol. it took me forever to figure out what it means and i still dont know what it does. lol ive tried various mod problems in python and have had some strange answers, can anyone actually explain what this means and what it does so i can have an idea? lol thank you
EDIT--------------------------------------
also just a small ps while im here lol, if anyone skypes and would liek to have discussions about python, etc.. anythign computer related or just talk or something that would be cool :D my username is tenshi.otoko so please feel free to add me :D

---

### Post by talonmies on 2010-03-03
Actually, it is the second code which is working correctly, and the first which isn't.

The expected result should be an endless loop if the list ever contains an entry of length >3, because you will then be appending to the list at every iteration, so the end of the list will never be reached and the loop never terminated. The reason the first doesn't loop endlessly is because using the slicing operation [:] makes a copy of the list before the loop is entered, so that the loop is iterating over a finite length list.

---

### Post by Tony Flury on 2010-03-03
It could be due to something like 

a[:] is evaluated as an in flight copy of the slice from begining to end of a, which is then looped through - so the loop is effectively constrained to the contents of a - at the time the loop actually begins.

whereas just using "a" actually uses a reference to the real a object - and since you are adding something to "a" as you go round the loop, you have a potential infinite loop - work out what happens when your loop actually adds something to the loop - say - it finds the word "dogs", it will add "dogs" to a (because the len("dogs") > 3), and then you go round the loop again - and you will eventually get to that new copy of "dogs", so it will get added again, and so on.

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-03
> **Tony Flury said:**
> It could be due to something like 

a[:] is evaluated as an in flight copy of the slice from begining to end of a, which is then looped through - so the loop is effectively constrained to the contents of a - at the time the loop actually begins.

whereas just using "a" actually uses a reference to the real a object - and since you are adding something to "a" as you go round the loop, you have a potential infinite loop - work out what happens when your loop actually adds something to the loop - say - it finds the word "dogs", it will add "dogs" to a (because the len("dogs") > 3), and then you go round the loop again - and you will eventually get to that new copy of "dogs", so it will get added again, and so on.



> **talonmies said:**
> Actually, it is the second code which is working correctly, and the first which isn't.

The expected result should be an endless loop, because you are appending to the list at every iteration, so the end of the list will never be reached. The reason the first doesn't loop endlessly is because using the flattening operation [:] makes a copy of the list before the loop is entered, so that the loop is iterating over a finite length list.


this makes so much sense. thank you very much. so by using the a[:] command you are telling x to list over the newly created temporary list of a that is going to be used so as to make sure you dont jump into an infinite loop. it makes so much sense now thank you :D

---

