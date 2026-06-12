---
title: "Coding filosophy-strategy"
date: 2008-09-23
forum: Programming Talk
---

### Post by hoboy on 2008-09-23
Hello guys, as a new in the field, as I read the forum they are many gurus here.
Could you guys chair your experiences of getting so far in coding ? the obstacle for a new who want to be good at coding her i am using java, I don't think that makes much of difference.
What is the mental field, the transition from a problem definition to a good code. I have look at many books they all have lots of codes, but not a word about the mental gymnastic of the decision making.
Maybe I am looking for how to acquire a strategy from problem to coding.
tks.

---

### Post by CptPicard on 2008-09-23
The only way to learn it is to actually do it. First, learn one language well enough so that you're comfortable with it. In this phase, don't jump between languages too early on. Advance your learning by doing simple training tasks. Also, read other people's code. I should have done that more when I was learning instead of always trying to figure out everything on my own from scratch.

Java is an OK beginner language but I do have a reservation about the static-typed OOP which forces you to think about object-oriented design too early. A beginning programmer should not be forced to end up stumbling on insufficient object decomposition skills -- that is a separate skill that comes in due time, after seeing enough code and examples.

Then, when you want to move on from simple tasks to more "real" projects, you may want to read some on algorithms and general design principles. Again, books really aren't a replacement to actually getting your hands dirty... the line between actual code and abstract principles and structure of your problem at hand starts to eventually become quite blurred once you're both a competent programmer and a problem analyst :) At about this time you need to expand your horizons by learning different paradigm languages... something like functional programming, to get new perspectives to languages and problem solutions.

---

### Post by dwhitney67 on 2008-09-23
Well for starters, never think of coding as the first step to solving a s/w problem.  I see it too often (and I did it myself in the early stages of my career).

The first thing to consider is the design.  The second thing to consider is the design.  And the third thing... ok, you get it now.

Basically, before you commit yourself to a lot of coding, try experimenting with a design using UML, visio, or whatever (Use Cases?).  You should have a high-level idea of what the s/w application will do and whether it satisfies all of its intended requirements.  You should also question whether it is adaptable to new requirements.

Feel free to prototype program snippets to get a feel for new programming tools (e.g. C++ Boost library) that you may encounter.  These little exercises can be applied towards the bigger project.

Anyhow, once you make it to the coding-phase, it should pretty much be a cake-walk.  The design, which is hopefully in place, will be your guide.

P.S.  As the ol' saying goes... "There's no substitute for experience."

---

### Post by lisati on 2008-09-23
+1 to the previous suggestions, plus learn to break problems into managable chunks

---

### Post by Greyed on 2008-09-23
> **dwhitney67 said:**
> The first thing to consider is the design.  The second thing to consider is the design.  And the third thing... ok, you get it now.

On the flip side, design is not everything.  There is something to be said about organically grown code, especially in a language that makes it fairly easy to refactor.

Coding is like battle.  Just as there has never been a plan that survived battle so too has there never been a design that survived coding.  When you get down into coding you find that your preconceptions in the design stage were flawed.  If the flawed preconceptions are at the core of your design the entire design is flawed.  So, yeah, designing is good.  But don't dwell on design too much and be prepared to scrap it in a heartbeat if it simply doesn't work.

---

### Post by CptPicard on 2008-09-23
The problem with telling a beginner in particular to use UML is that paper designs require pretty much perfect foreknowledge of the language you're using, plus how to apply it to the problem. Once you know those, you might just as well start coding already. This is why I have always considered UML to be mostly a business communication and documentation, not a design, tool.

Especially a beginner just needs to do a lot of exploratory programming to learn "how programming applies to problems". It's more fun too :)

---

### Post by hoboy on 2008-09-23
Lisati.
you have touched something I struggled with when you said
"+1 to the previous suggestions, plus learn to break problems into managable chunk"
it seemed like you are good at it what is your secret ?

---

### Post by hoboy on 2008-09-23
> **lisati said:**
> +1 to the previous suggestions, plus learn to break problems into managable chunks

you have touched a problem i am struggling with
What is your secret of it
"Break problems in manageble chaunks" ?

---

### Post by dwhitney67 on 2008-09-23
> **Greyed said:**
> On the flip side, design is not everything.  There is something to be said about organically grown code, especially in a language that makes it fairly easy to refactor.

Coding is like battle.  Just as there has never been a plan that survived battle so too has there never been a design that survived coding.  When you get down into coding you find that your preconceptions in the design stage were flawed.  If the flawed preconceptions are at the core of your design the entire design is flawed.  So, yeah, designing is good.  But don't dwell on design too much and be prepared to scrap it in a heartbeat if it simply doesn't work.

IMO, you opinion is pure rubbish.

What is a person (or group of persons) supposed to do when building s/w for the next generation of aircraft or spacecraft?  Go to the farm to grow organic code (whatever that is)??

How can you be serious and say that design does not matter.  How do you propose to earn the privilege to work on a $100+ million contract?  You better show the client that you indeed have a clue about how to go about designing/implementing the project.  Simply telling the client that you have 50 code-monkeys won't do the trick.

If you are talking about developing simple little projects that one spends an hour or a weekend pursuing, then fine, dispense with the design.  But for any serious s/w developer or engineer, the design phase is paramount.  The same applies to any engineering profession; well, with the exception of Sanitation Engineering.

P.S.  Software does not fight back, have independent thoughts, or mood swings like the enemy in a battle situation.  You might as well compare apples and oranges.

---

### Post by Greyed on 2008-09-23
> **dwhitney67 said:**
> IMO, you opinion is pure rubbish.

Likewise.

> What is a person (or group of persons) supposed to do when building s/w for the next generation of aircraft or spacecraft?  Go to the farm to grow organic code (whatever that is)??

Something tells me your hostility is born out of ignorance.  And...

> How can you be serious and say that design does not matter.

...you have horrible comprehension skills.  At what point in my message did I say that design did not matter?  When in my message did I say don't design at all?  

I didn't.

I simply stated that design is not everything and to not dwell on it.  At some point you have to sit down and code.  Design all you want, until you start to code your design is nonfunctional.

> If you are talking about developing simple little projects that one spends an hour or a weekend pursuing, then fine, dispense with the design.  But for any serious s/w developer or engineer, the design phase is paramount.

And yet show me one project that ever went off exactly as design.

> P.S.  Software does not fight back, have independent thoughts, or mood swings like the enemy in a battle situation.  You might as well compare apples and oranges.

Tell Kasperov that... but I digress.

You have trouble with the concept of analogies, don't you?  Of course code doesn't fight back.  The adage that no plan has survived combat isn't about people killing people for whatever reason.  It is about the changing nature of the process and while the beginning condition (pre-battle) and end condition (victory) are known the path between those two points, the battleplan, cannot foresee all possible factors.

My point was that during the process of coding things change.  Those things might be requirements on the code to constraints from where the code will run on through to the preconceived notions of the developer(s) being destroyed by learning a new, more efficient way to do something or, alternatively (and more often) that their ideas simply are inefficient and need to be scrapped.  It is this last part that is most important to the neophyte programmer since by the very nature of their ignorance most of their designs will be inefficient and, after they gained the experience, will need to be scrapped.

Since both battle and programming involves change the analogy fits.  Albeit one is most often external change while the other is most often internal.  But that is why no analogy is perfect.

If you think that the process is a constant which can be controlled by the design stage alone then I invite you to read up on why microkernels have yet to take the world by storm.  The design seems elegant; a tiny kernel to control processes and process communication while all other traditional kernel-space, hardware-level processes moved up a layer.  This would allow for faster development and the ability to swap in and out different implementations of the same subsystem on the fly.  I won't spoil why the design is a prime example on why design only carries you so far.  I'll just say that it would behoove you to go read up it before responding lest another well known adage be attached to your name, "It is better to be considered ignorant by keeping silent rather than open your mouth and prove it."

---

### Post by dwhitney67 on 2008-09-23
> **Greyed said:**
> ...

...you have horrible comprehension skills.  At what point in my message did I say that design did not matter?  When in my message did I say don't design at all?  

I didn't.

I simply stated that design is not everything and to not dwell on it.  At some point you have to sit down and code.  Design all you want, until you start to code your design is nonfunctional.
...
Apparently you are correct.  I must have misread your earlier post.  My apologies for being ignorant in my abilities to comprehend the English language.  To quell my shame, I will resort to drinking another beer.

---

### Post by Greyed on 2008-09-23
Meh, now you're making me feel bad for portions of what I wrote.  How'sabout I buy you that beer and we call it even?

---

### Post by hoboy on 2008-09-23
Thanks guys for all the input,some parts of the answer is been very advanced.
But for new like me,
I am still wandering about your experiences about the point made by Lisati
witch is the following" 
 learn to break problems into managable chunks"
what has been you technics of passing that stage of your learning ?

---

### Post by CptPicard on 2008-09-23
> **hoboy said:**
> 
what has been you technics of passing that stage of your learning ?

Coding and thinking about problems. And reading others' code.

The really is no royal road to philosophy...

---

### Post by lisati on 2008-09-23
> **hoboy said:**
> you have touched a problem i am struggling with
What is your secret of it
"Break problems in manageble chaunks" ?

Apologies for the delay responding, in-laws came over.

The basic idea (pun not intended) is a kind of "divide and conquer" approach. You might want to separate a program into different tasks, e.g. design of the user interface, source(s) of data, the step(s) needed to process or otherwise do something useful with the data, and the step(s) needed to save the results and/or keep the person running the program informed. Each of these can be further refined as required into a number of smaller sub-tasks that are easily managable.

---

### Post by dwhitney67 on 2008-09-23
> **Greyed said:**
> Meh, now you're making me feel bad for portions of what I wrote.  How'sabout I buy you that beer and we call it even?
Don't feel bad... you were right, and I was wrong.  Thanks for the beer offer, but I think I am a tad far away from "everyone" at this moment.  (I'm in BFE Thailand, at the in-laws house).

---

### Post by hoboy on 2008-09-23
> **lisati said:**
> Apologies for the delay responding, in-laws came over.

The basic idea (pun not intended) is a kind of "divide and conquer" approach. You might want to separate a program into different tasks, e.g. design of the user interface, source(s) of data, the step(s) needed to process or otherwise do something useful with the data, and the step(s) needed to save the results and/or keep the person running the program informed. Each of these can be further refined as required into a number of smaller sub-tasks that are easily managable.

thanks a lot for your help, I have copied/pasted your answer to a file that I will consult time to time.
In laws ? I am 16 and learning programming.

---

### Post by DrMega on 2008-09-23
> **hoboy said:**
> Hello guys, as a new in the field, as I read the forum they are many gurus here.
Could you guys chair your experiences of getting so far in coding ? the obstacle for a new who want to be good at coding her i am using java, I don't think that makes much of difference.
What is the mental field, the transition from a problem definition to a good code. I have look at many books they all have lots of codes, but not a word about the mental gymnastic of the decision making.
Maybe I am looking for how to acquire a strategy from problem to coding.
tks.

Follow these steps EVERY TIME. When you gain some experience you will be able to do some of the steps in your head, but it is best to start by writing/drawing stuff to get it clear first:

1. Analyse: Define the objective. What is the requirement? Who will use your program? Why will they use it? How skilled are they? When does it need to be ready? Can you realistically do it in that time?

2. Break it down: If you are writing, say for example, a new forum application, you won't sit down and start rattling out code. Work out what data you will need to store and manipulate. The best written front end will die a horrible death if you get your data requirements wrong. Write down each individual function (function in the sense of something it does, not in the programming sense of a subroutine that does something). Break everything down into little chunks.

3. Work out a test plan: Ok, you haven't built it yet so why worry about this at this point? Because your test plan serves many purposes. It helps clarify the requirement, it serves as a double check that you've broke down the requirement properly, and it stops you going off on a tangent and losing sight of the original plan.

4. Develop it. By now you have a clear understanding of the requirement, you've broken it down into manageable chunks, and you know how you are going to test it. You have everything you need. It is a good idea to test each module, each function, class etc individually as you build them. It will be easier to identify bugs at that stage than once the whole app is built. Use your test plan to help focus you in that activity.

5. Test the whole app. Not haphazardly, but against your test plan that you made before you wrote a single line of code.

Incidentally, testing is an often neglected process. It is a whole subject in its self but suffice to say, don't just prove that something *does* work when it *should work*. You need to test that it gives the required result when the user has done something unexpected. Consider the following over simplified requirement. Consider that I have to have at least 100 GBP in my bank account before your function will authorise a transaction. You might code this as follows:

balance > 100.00

When testing the function, you try balance = 200, and it authorise, balance = 50, and it doesn't authorise. Great. What happens if you try balance = 100.00?

---

### Post by pmasiar on 2008-09-23
> **dwhitney67 said:**
> IMO, you opinion is pure rubbish.

What is a person (or group of persons) supposed to do when building s/w for the next generation of aircraft or spacecraft?  Go to the farm to grow organic code (whatever that is)??

IMO, you opinion is pure rubbish. 8-)

OP's problem is how to gain skills from beginner to intermediate, not how to secure contract with NASA :-)

"Exploratory programming" is perfect fit for that phase. You need to "get the feeling" what design decisions have what consequences. And there is no other way to learn that skill but make decisions, implement them in code, and learn from the mistakes you did (and reimplement the code according to lessons learned). Rinse, repeat. 8-)

Although Java is decent language, and language-hopping does not do you any good, Java is IMHO not very good fit for exploratory programming, because static typing and checked exception annoys you and slow your progress with irrelevant minor details.

Consider learning flexible dynamically typed language (Python would be my pick, Ruby or Perl are other options) which allows you to program in a more free and flexible way. If you are past beginner Java, learning basic Python should not take more than a week.

Then: program, program, program. See wiki in my sig for Python links and training tasks (you can solve them in Java, too). After you are able to write 200 lines of Python code (or 1000 in more verbose Java) which runs, reading books about software design would make much more sense than it does now, when you lack of frame of reference about problems described.

---

