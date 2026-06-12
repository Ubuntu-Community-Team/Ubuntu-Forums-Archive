---
title: "Algorithm Analysis"
date: 2011-09-15
forum: Programming Talk
---

### Post by WinterMadness on 2011-09-15
Im struggling a bit with this concept(im taking my first data structures/algorithms class at university.), at least in terms of proving best/worst/avg cases. Admittedly, I have a book that has a reputation for being horrible for first timers with the subject, but im seriously really lost, and im wondering if most people even really go into depth with this stuff?

---

### Post by OlyPerson on 2011-09-15
Algorithm analysis and understanding of data structures is important.  Basically it's how you know if the code you're writing is as efficient as it can be.

---

### Post by WinterMadness on 2011-09-15
> **OlyPerson said:**
> Algorithm analysis and understanding of data structures is important.  Basically it's how you know if the code you're writing is as efficient as it can be.

Im aware of that. I want to know if most people actually prove best,average and worst cases scenarios. By that, I dont mean simply looking up that a specific algorithm is O(n^2) or O (n Log n) etc. I mean, doing all of the math on YOUR OWN to figure out what its big oh is.

Example: [http://en.wikipedia.org/wiki/Algorithm_analysis#Evaluating_run-time_complexity](http://en.wikipedia.org/wiki/Algorithm_analysis#Evaluating_run-time_complexity)

---

### Post by cyberslayer on 2011-09-16
You mean does the "average programmer" do runtime analysis?  Definitely not.  However, the "average programmer" does a lot of bad things so its not really a model for what you should be doing.

Once you code enough and analyze enough algorithms, you'll be able to tell what the runtime is most of the time without actually having to do the analysis.

---

### Post by CptPicard on 2011-09-16
Well, in the real world you don't really do an actual proof. It's just important to have a sense of the overall class of the complexity of the problem you're dealing with, and to be able to do rough arithmetic with the big-Ohs when combining approaches...

---

### Post by karlson on 2011-09-16
> **WinterMadness said:**
> Im struggling a bit with this concept(im taking my first data structures/algorithms class at university.), at least in terms of proving best/worst/avg cases. Admittedly, I have a book that has a reputation for being horrible for first timers with the subject, but im seriously really lost, and im wondering if most people even really go into depth with this stuff?

If you are even remotely writing code that requires performance then absolutely you go in depth with the stuff.

---

### Post by karlson on 2011-09-16
> **WinterMadness said:**
> Im aware of that. I want to know if most people actually prove best,average and worst cases scenarios. By that, I dont mean simply looking up that a specific algorithm is O(n^2) or O (n Log n) etc. I mean, doing all of the math on YOUR OWN to figure out what its big oh is.

Example: [http://en.wikipedia.org/wiki/Algorithm_analysis#Evaluating_run-time_complexity](http://en.wikipedia.org/wiki/Algorithm_analysis#Evaluating_run-time_complexity)

If you come up with a generic algorithm like sorting/searching you will need to do a big O research on your own to prove that your stuff is worth the concept.  Furthermore on quite a few interviews you may be asked to come up with a way to do something like a most common subset search or determine if the set is a subset of another set, etc. and you need to make it in the most efficient manner you will have to do this Big O calculation right then and there.

---

### Post by Off Shore on 2011-09-16
Keep thinking positive is the trick.
Sometimes in education the subject matter makes some students wonder if it 
has any practical use. This is just as true of Computing Science as it is of English language, Biology, History or any other academic subject.
 
The answer, of course, is yes it does always have a practical use. You need to study that material to pass your module or your exam.
In addition you will have gained something valuable albeit intangible from applying yourself to this difficult or dull area.
 
That's part and parcel of your education and the learned ability to deal with dense and dull topics is a highly valuable transferable skill.
 
Dont undervalue it.

---

### Post by cyberslayer on 2011-09-16
> **Off Shore said:**
> 
That's part and parcel of your education and the learned ability to deal with dense and dull topics is a highly valuable transferable skill.
 
Dont undervalue it.

Complexity analysis can be useful in practice; while most of the time its not necessary, it can be useful once in a while if you use a custom algorithm and are not sure how well it performs.  It also doesn't have to be "dense and dull"; it just requires some effort in order to get the hang of things.

---

