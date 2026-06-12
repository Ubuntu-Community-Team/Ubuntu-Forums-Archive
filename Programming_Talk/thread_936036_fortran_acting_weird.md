---
title: "fortran acting weird"
date: 2008-10-02
forum: Programming Talk
---

### Post by alejaaandro on 2008-10-02
hi everybody..

i m trying to write a program to get the windspeed of every turbine in a wind park for a thesis in my uni...

anyway, i get this really weird effect:

when commenting a "write" command, all the results change...
if i uncomment it, everything goes back to normal...
if i delete the line, everything goes back to wrong...

I really can't explain it..

i use f77 to compile it, tried to use f95 but gives me errors while compiling it (may the syntax is different, and i don't want to have to go through the whole code changing it)

plus, i was talking with a friend and he said he once had the same problem (he runs windows) so i guess it's not a compiler problem... 

any ideas? did you ever get this problem?

---

### Post by LaRoza on 2008-10-02
You should give some code.

---

### Post by DrMega on 2008-10-02
First, let me start by pointing out that Fortran is evil. It is the spawn of Satan, sent to melt the brains of mortals.

Now that we've got that out of the way, as LaRoza says, post up the code so we can have a look.

Is your write statement evaluating a function that changes some global variables which are used further down the code?

---

### Post by alejaaandro on 2008-10-02
thnx for the imediate response guys...

there's no point in making you go through the whole code, it's 600 lines of math and greek comments... it would look like greek to you! (hmmm, bad self-sarcasm)..

anyway,the line giving me the proplem was just a typical 

write(90,*) i

i tried it on my bros laptop which has windows with force2.0 and it ran ok...

then i tried g77 and fort77 instead of f77... they run ok too...
now i have a different problem....

g77 and fort77  give me different results... force2.0 matches one of those results (i think g77 but i don't remember... not at home right now to check)..
i haven't had time to search it thouroughly, but i did find a forum mentioning it does happen...

any idea why that is? any idea which results i should trust?
cause some give me an efficiency greater than 1 which is obviously unacceptable an the other gives me about .75 which is kinda low but acceptable.. so how can i be sure if my progam is correct or not?

if you still want to take a look at the code tell me and i ll attach it when i get home

---

