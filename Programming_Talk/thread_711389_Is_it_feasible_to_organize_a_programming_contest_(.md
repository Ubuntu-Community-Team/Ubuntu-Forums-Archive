---
title: "Is it feasible to organize a programming *contest* (!= challenge)?"
date: 2008-02-29
forum: Programming Talk
---

### Post by aks44 on 2008-02-29
Hi there,


Following a discussion on IRC where hod139 suggested that, I decided to bring this to the forum's attention.


As interesting as they are, the weekly challenges don't leave much space for more complex problems (mainly because of the short delay).
I agreed to hod139's suggestion that it could be interesting to have more "in-depth" challenges, where each participant's code would *contest* against the others'. Which means interaction between the programs. Or at least, even if the submissions don't interact with each other, some criterion (number of "rounds" needed to solve a problem, ...) to designate the winner(s).


We identified several problematic points, but they are mainly organizational problems that can (IMO) be solved:
[LIST]
[*]It takes time to run everyone's submission against the others => we'd need several persons running them
[*]Noone uses the same language => the persons running the contest must be able to (globally) run every submitted language.
[*]Interaction: again, due to languages' heterogeneity, we need to find a least common denominator that can be used by everyone to interact with other people's submissions. => restrict ourselves to files or console redirections?
[/LIST]


EDIT: looks like this post is not as clear as I thought... so here's a bit of explanation (from IRC):
> [21:16] <LaRoza> Could you explain it?
[21:17] <aks44> well, eg. a rubik-cube solver (hard question if it were not for the solution on Wikipedia), the criterion would be (1) least number of moves (2) least number of rounds (from the algo POV)
[21:17] <LaRoza> I see.
[21:18] <aks44> or things like "robotic contests" but only software
[21:18] <LaRoza> Interesting.
[21:18] <aks44> you know, when unis build robots that have to catch balls etc ;)


Discuss. :)

---

### Post by ruy_lopez on 2008-02-29
Restricting the challenge to one language would ensure a level playing field. But not everyone knows every language equally. 

Personally, I'd be reluctant to enter into a prolonged challenge just for vanity. I'd much prefer it if the challenge was meaningful, ie the challenge involved developing part of a usable application.

Maybe we could come up with a layered package which would use different languages. People could chose their own layer. Multiple implementations would arise for every layer. People could then choose which implementations are adopted, without being able to choose their own.

Just some ideas.

---

### Post by Wybiral on 2008-02-29
> **ruy_lopez said:**
> Restricting the challenge to one language would ensure a level playing field. But not everyone knows every language equally. 

Personally, I'd be reluctant to enter into a prolonged challenge just for vanity. I'd much prefer it if the challenge was meaningful, ie the challenge involved developing part of a usable application.

Everyone is on a level playing field if they can use any language. Also, the challenge doesn't have to be for vanity, you could always challenge yourself just for self improvement, right?

---

### Post by ruy_lopez on 2008-02-29
> **Wybiral said:**
> you could always challenge yourself just for self improvement, right?

Of course. If I've learned anything, it's that there's always more to learn.

---

### Post by aks44 on 2008-02-29
> **ruy_lopez said:**
> Personally, I'd be reluctant to enter into a prolonged challenge just for vanity. I'd much prefer it if the challenge was meaningful, ie the challenge involved developing part of a usable application.

Well, "vanity" is not the adequate word here, I'd rather say "fun". The primary goal would be to solve interesting problems, involving (if possible) reacting to opponent algorithms.

But I get your point anyway. What kind of application would you suggest?


> **ruy_lopez said:**
> Maybe we could come up with a layered package which would use different languages. People could chose their own layer. Multiple implementations would arise for every layer. People could then choose which implementations are adopted, without being able to choose their own.

Now that I think of it, things like DBUS / CORBA etc could come in handy. I don't know about DBUS, but CORBA is quite complex, so why not kill two birds with one stone: make "simplified", homogenous DBUS or CORBA bindings for each language (useful) and build the contests over that? :D

---

### Post by Lster on 2008-02-29
I like the idea. Count me in!

Maybe a panel of judges or a community voting thread for each solution could determine the winner. We would also need some organizers to oversee the competition...

If you allow all languages, everyone can pick the best tool for the job. However, I do think that, unlike the challenge, in the competition picking the best language for the job should be counted for or against a person's ranking. Following that, we could have a "shortest code award", "fastest code award", "most elegant code award" etc...

These are just some ideas but whatever form it takes, I'm sure I'll enjoy it! :)

---

### Post by ruy_lopez on 2008-02-29
Actually, the rubiks cube analogy clarifies what you mean. You mean more of a structured challenge, a specific problem that has a narrow set of requirements, that would clarify the effectiveness of the solutions. Sounds cool.

---

### Post by pmasiar on 2008-02-29
You don't need judges - that is boring task, computers are better at boring tasks. And let's not restrict ourselves to single language at the beginning - where is fun in not letting other people having fun too?

What you may want instead is restrict to languages available on ubuntu, or to 3-5 popular ones, which are easy to install and run for everyone interested.

My suggestions will be to have a website where contestant can upload source code, website will run it providing test input, and checks if output is according to requirements. Any programing language able to read stdin and produce stdout can compete on equal with others. Or we might have different groups for different languages.

And I am sure there should be some opensource projects doing just that. If not, that would be interesting project to start. 

Thinking about that, this could yield whole class of websites, like are "planets" for blog aggregator: language "leagues" for competing to solve tasks! Anyone can start a "league", create a set of tasks, and let other people to compete. 

Of course security needs be maintained, program should run in a jail, very limited and restricted server resources available, no reading server files. But I am sure security experts will know how to set it up.

Sounds like fun!

Grading submission can be automated too, based on:
- who solved task first
- how many other people solved it
- how long (lines of code) solution is (code according to best practices)
- time needed to run

---

### Post by NathanB on 2008-02-29
If you are intent on "re-inventing the wheel," you may wish to do a bit of research on the subject:

[http://en.wikipedia.org/wiki/Core_War](http://en.wikipedia.org/wiki/Core_War)

Up-grading this "retro 60's-era" idea for the 21st century sounds like a good plan!

Nathan.

---

### Post by Lster on 2008-02-29
[QUOTE=pmasiar]Grading submission can be automated too, based on:
- who solved task first
- how many other people solved it
- how long (lines of code) solution is (code according to best practices)
- time needed to run [/QUOTE]

I doubt a computer could properly judge code. And someone still needs to determine an algorithm for marking code - if that method is used.

---

### Post by cb951303 on 2008-02-29
we may build a host program which accepts plugins written in various languages ?

the idea is very common, just google for robot programming challenges. I also remember there was even a game where the contestant programs try to overwrite a vritual machine's memory blocks, I don't remeber the name though :)

---

### Post by slavik on 2008-02-29
ACM Programming Competition rules (or what I remember of them):
5 hours for 9 problems.
scoring is done by calculating the time to submit the solution from the start of the contest to the time the actual solution was submitted. If the answer was wrong, you get penalized that time. Top "team" (teams are 2-3 people) is the one solving the most problems in the shortest time.

some examples:
team a solves 5 problems in 9 hours, team b solves 4 problems in 1 minute, team a wins.
you submit a solution 1 hour after the beginning of the competition, if it is wrong and you submit the correct solution 10 minutes later, you get counter 70minutes for the correct solution and 60 minutes for the incorrect (130 minutes is the time to solve).
the times get added and used as a tie breaker. In the ACM competitions, the top 3 teams usually do not need the tie breaker to place them.

there is a submition system and the language limits are: C, C++, Java, Ada.

EDIT: there is no judgement on who has the better solution ... just whether it is correct. Also, it should not take a solution more than 5 minutes to solve a problem (The fibonacci's fury problem is the type that come from the competition). :)

problems are listed in the increasing order of difficulty, with #1 and #2 being pretty obvious. The fibonacci's fury problem someone listed would be #4-#6.

ACM of the Greater Region of New York site: [http://www.acmgnyr.org/](http://www.acmgnyr.org/) (has rules, past problems, solutions, etc).

---

### Post by aks44 on 2008-02-29
TBH hod139's original idea (which I agree with) was more centered around programs interacting with each other (eg. chase/evade). Which boils down to *very* basic "AI".


Task-solving contests (ie. "Rubik cube"-style) could work too, but IMHO they are way less interesting. YMMV.


"Battles" will of course be easier to judge: define the rules of a 2 vs 2 battle, there is always a winner who gets a score (based on various criterion). Make it a tournament (everyone should play against everyone) and sum up the scores. :)

---

### Post by slavik on 2008-02-29
a tourney style competition ... that would be interesting ... :)

---

