---
title: "Open Programming Challenge - Elevator Simulator"
date: 2009-01-20
forum: Programming Talk
---

### Post by samjh on 2009-01-20
We haven't had a serious challenge for a while, so here's one I've just thought of while tackling my apartment's inefficient elevator.

This challenge is an on-going challenge: there are no time limits.  It is also a non-competitive challenge: I'm not going to declare winners or losers.  It is an open challenge for experienced programmers to critique, and beginners to learn from.

Devise an algorithm to control an elevator system with maximum efficiency.

Assumptions:[list][*]There are ten floors in the building: Ground, 1, 2, 3, 4... 9.
[*]There is only 1 elevator servicing all ten floors.
[*]To traverse one floor level, takes the elevator 1 second.
[*]To embark or disembark passengers, stops the elevator for 3 seconds at a floor (simultaneous embarking and disembarking takes 3 seconds also).[/list]

Requirements:[list][*]Provide each floor with controls to call an elevator UP or DOWN. Ground floor only requires a call button for UP; 9th floor only requires a call button for DOWN.
[*]The elevator needs buttons to travel to all floors, they may be selected at any time, and multiple floors can be selected at once.[/list]

**USER INTERFACE (optional)**

Create a graphical user interface to run the simulation.  The GUI must include:
- A display for the current floor that the elevator is on.
- A group of buttons representing the buttons located within the elevator, and which buttons are selected.
- Call buttons for each floor, and which buttons are selected.
- A display showing whether the elevator is headed up, down, or stationary at any given moment.

**If you do not create a GUI, make sure your console UI is good enough to provide all the necessary controls and feedback, and make sure to post instructions on how to interact with your program.**

=======================================

This may be a good challenge for domain-specific languages.  Intermediate programmers who have just learned a language or GUI library will find this a strong test of their skills.

This challenge requires a thorough understanding of procedural logic.  It also requires you to be able to design a GUI, work with signals and events, and deal with concurrent computing issues.

**Make sure to post instructions on dependencies, compilation, and execution of your implementation.**

Good luck!  May the genius of past programming pioneers be with you! ;)

---

### Post by slavik on 2009-01-20
so, it's a queue that gets rearranged as things come in. :P

---

### Post by CptPicard on 2009-01-20
[http://en.wikipedia.org/wiki/Elevator_algorithm](http://en.wikipedia.org/wiki/Elevator_algorithm)

> **samjh said:**
> 
Devise an algorithm to control an elevator system with maximum efficiency.

An interesting question is how optimal the heuristic given in that article is, compared to some theoretical optimum. Sounds like a homework assignment for online vs. offline competitiveness analysis... I always hated those, never could quite get how to actually prove that some ratio is the worst possible of all possible cases ;)

---

### Post by samjh on 2009-01-20
> **slavik said:**
> so, it's a queue that gets rearranged as things come in. :P

Very basically, yes.  That's what it comes down to.  It's perhaps a good thing the algorithm is not runtime-critical.  The bigger question is how to rearrange the things that are coming in. ;)

> **CptPicard said:**
> [http://en.wikipedia.org/wiki/Elevator_algorithm](http://en.wikipedia.org/wiki/Elevator_algorithm)

An interesting question is how optimal the heuristic given in that article is, compared to some theoretical optimum. Sounds like a homework assignment for online vs. offline competitiveness analysis... I always hated those, never could quite get how to actually prove that some ratio is the worst possible of all possible cases ;)
You are a very mean man. :p

---

### Post by Tomosaur on 2009-01-20
While I was at university, I discovered that the maintenance panel on this elevator in a tower I had to use every day could be jiggled open. It had an override button which would make the elevator ignore every call until it arrived at your floor. Needless to say I never told anybody of my discovery, and abused it at every opportunity :P

---

### Post by nvteighen on 2009-01-20
> **Tomosaur said:**
> While I was at university, I discovered that the maintenance panel on this elevator in a tower I had to use every day could be jiggled open. It had an override button which would make the elevator ignore every call until it arrived at your floor. Needless to say I never told anybody of my discovery, and abused it at every opportunity :P
Maybe implementing that button could be a bonus for this challenge? ;)

---

### Post by TreeFinger on 2009-01-20
> **Tomosaur said:**
> While I was at university, I discovered that the maintenance panel on this elevator in a tower I had to use every day could be jiggled open. It had an override button which would make the elevator ignore every call until it arrived at your floor. Needless to say I never told anybody of my discovery, and abused it at every opportunity :P

Nice hack :)

---

### Post by aj_ on 2009-01-21
I'm working on this, but I'm a novice so it might take some time ;).

---

### Post by stevescripts on 2009-01-21
A little something to get folks started perhaps.  This script doesn't fulfill all of the requirements of the challenge, but, as I knew it already existed, (and I probably wont be able to make time to write something ... :( ), I will attach it (due to its size, ~7k).

This script is shamelessly harvested from the Tclers Wiki:
[http://wiki.tcl.tk/12505](http://wiki.tcl.tk/12505)
(that page being originated by a great tcler and friend)

Steve
PS: rename the file to elevsim.tcl

---

### Post by jimi_hendrix on 2009-01-21
i dont get it...why must there be controls and no user interface...also does the computer determine who is getting on and off the elevator?

---

### Post by myrtle1908 on 2009-01-21
This may prove useful to those undertaking the challenge [http://www.elevatorchallenge.com/](http://www.elevatorchallenge.com/) (Java)

---

### Post by samjh on 2009-01-21
> **jimi_hendrix said:**
> i dont get it...why must there be controls and no user interface...also does the computer determine who is getting on and off the elevator?

You can implement the controls using a command-line interface (using prompts) or via a GUI.  A GUI would be most efficient, but that's up to you, depending on how much time or commitment you have.

As for who is getting on or off the elevator, obviously if someone pushes level 5 within the elevator, they will be getting off there.  If someone calls the elevator from level 2, they will be getting on.  You'll need to figure this into your code.

---

### Post by cb951303 on 2009-01-21
I would like to see someone try this with PLC ladder diagrams :D

---

### Post by jimi_hendrix on 2009-01-21
> **samjh said:**
> As for who is getting on or off the elevator, obviously if someone pushes level 5 within the elevator, they will be getting off there.  If someone calls the elevator from level 2, they will be getting on.  You'll need to figure this into your code.

but who decides who gets on or off?

---

### Post by WitchCraft on 2009-01-21
> **jimi_hendrix said:**
> but who decides who gets on or off?

sigsegv decides who gets off :p

do I get a bonus if I write a program that can hack the elevator algorithm to only server my floor (nr. 5)?

---

### Post by jmartrican on 2009-01-21
How is maximum efficiency tested?

I think there needs to be a program that tests it out.  The testing program can simulate various people trying to access the elevator from different floors and destined to various floors.  Similar to the game Sim Building.  The efficiency will come in when the testing program checks how many sims still waiting, how long they waited for, avg wait time across all sims, and so on.

---

### Post by samjh on 2009-01-21
> **jimi_hendrix said:**
> but who decides who gets on or off?

It's self-regulating.

If an elevator is called from Level 5, then it's obvious that the elevator will stop and pause for 3 seconds at Level 5 when it gets there.  Who gets on or how many are irrelevant for simplicity's sake.  The elevator just stops and pauses for 3 seconds when it gets to a level it has been called from or ordered to go to.

> **jmartrican said:**
> How is maximum efficiency tested?There will be a sequence of events a simulator will be put through, hence the design of the user interface needs to be effective and efficient, especially in obtaining the correct user inputs.

---

### Post by stevescripts on 2009-01-22
> **cb951303 said:**
> I would like to see someone try this with PLC ladder diagrams :D

Egad!  (IOW, I would like to see it too, not however, would I want to be the one to *DO* it!)

Steve

---

### Post by aj_ on 2009-01-23
edit: oops, found a little bug. At line 175, change DOWN to UP.
edit2: errr, line 171, not 175. Sorry about that.
edit3: see my next post for a new version, now with 50% less suck.

Well guys, here it is, a newbie's shot at tackling this problem. It would seem I bit off more than I could chew, so in the interest of getting something posted, I went for the easiest possible solution (doesn't even take time into consideration). The lift is reasonably intelligent, but nowhere near optimal. In fact, I wonder if there is such a thing as a perfect elevator system. Maybe one which collects statistics based on usage patterns could approach this.

The elevator doesn't operate in real time because that is way beyond my abilities, so you'll have to manually run it by entering '1'. You can operate the lift and floor panels at any time. The error-catching is crude, so be careful (do not enter anything that isn't a number). Other than that, it seems to work great.

The lift has 3 modes: ascend, descend, and idle. The weakest is idle, because I haven't worked on it much. If you push a bunch of buttons while the lift is in idle mode (ie. no buttons pushed anywhere), and then run it, it'll do a very poor job of selecting which of the other two modes it should engage. Still, I think the worst possible wait time is around 50ish seconds, if you know how to exploit it.

I learned a great deal writing this little program :). I hope you poke a lot of holes in it so I can learn more.

g++ -o splatt splatt.cpp to compile it. If you want to run this in Windows, changing line 280 to system("cls"); should do the trick.

---

### Post by jimi_hendrix on 2009-01-23
> **samjh said:**
> It's self-regulating.

If an elevator is called from Level 5, then it's obvious that the elevator will stop and pause for 3 seconds at Level 5 when it gets there.  Who gets on or how many are irrelevant for simplicity's sake.  The elevator just stops and pauses for 3 seconds when it gets to a level it has been called from or ordered to go to.

well who sends the calls?

---

### Post by JupiterV2 on 2009-01-23
> **jimi_hendrix said:**
> well who sends the calls?

I was wondering the same thing you are!

Perhaps it's better worded:

If those who want to get on the elevator call it, and those who are riding the elevator request one or more floors to go to, whom or what decides what those passengers want? Make some bots to similate randomness or do you have to design some kind of a client-server program to accommodate virtual passengers?

We create the INTERFACE but who controls the USER(S)? Where do(es) the source(s) of input come from?

---

### Post by aj_ on 2009-01-27
Here is my new and much improved version. Hope you enjoy my "object-disoriented" C++ ;). I did manage to cut the algorithm to less than a page, down from whatever ungodly size it was before, and iit's contained mostly in one function (Run). Makes it easier to go in and plug in your own logic.

New things:
[ ] = empty lift.
[&] = occupied lift (note that servicing a floor request does not imply that a user stepped inside. Only by pushing a lift panel button will the program consider the lift occupied.
<- = open lift door.

I'm now studying virtual functions so I will probably rewrite this program once I'm done reading the whole book (or I'd have to rewrite it every time I learned something cool).

Is anyone else working on this?

> **JupiterV2 said:**
> I was wondering the same thing you are!
We create the INTERFACE but who controls the USER(S)? Where do(es) the source(s) of input come from?

You control them, by keeping a mental tab of where they are, because you have access to all the panels. For example, if you select UP  on the 3rd floor, when the lift stops there, it's your responsibility to push a button on the lift panel (which could very well be in the opposite direction), or not go inside the lift at all (in case the user forgot his briefcase :) ).

---

### Post by nvteighen on 2009-01-27
> **aj_ said:**
> Here is my new and much improved version. Hope you enjoy my "object-disoriented" C++ ;). I did manage to cut the algorithm to less than a page, down from whatever ungodly size it was before, and iit's contained mostly in one function (Run). Makes it easier to go in and plug in your own logic.

...


Great one!

---

