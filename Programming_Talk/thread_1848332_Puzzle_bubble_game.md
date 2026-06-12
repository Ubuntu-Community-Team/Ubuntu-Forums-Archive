---
title: "Puzzle bubble game"
date: 2011-09-22
forum: Programming Talk
---

### Post by Edounl on 2011-09-22
hy,
 I am trying to develop a puzzle game in lua, someone knows some nice  examples, or could someone explain what the best aproach to do this. 
 thks in advance.

---

### Post by DangerOnTheRanger on 2011-09-22
Due to having such a specific goal, you're probably not going to find the kind of help you're looking for. Unfortunately, nobody can just come along and give you step-by-step directions on how to write your game, because they probably have a different goal in mind then you do, not to mention it really wouldn't be "your" game then, anyway. 

I can give you some more general help, though:
[LIST]
[*]LOVE is a good 2D game framework for Lua, you should take a look at it
[*]There are a few puzzle games like what you describe in the Ubuntu package repos (none come to mind at the moment, unfortunately) which might be worth a look
[/LIST]

---

### Post by Edounl on 2011-09-22
hey

i am using the corona sdk.
i am using a 2d array for the bubbles, now i am trying to make the collision and the bubbles pop, already check the collision, but how should i check for all neighborn same colored bubbles ?

---

### Post by DangerOnTheRanger on 2011-09-22
> **Edounl said:**
> hey

i am using the corona sdk.
i am using a 2d array for the bubbles, now i am trying to make the collision and the bubbles pop, already check the collision, but how should i check for all neighborn same colored bubbles ?

Well, I've never used that SDK, so I can't get specific. At a high level, you'd check your 2D array to see if neighboring bubbles are the same color as the bubble in question.

---

### Post by N1GHTS on 2011-09-23
I'm using a 2D array for the bubbles, now I'm trying to make the collision and the bubbles pop.

I'm using a canvas for my painting, now I'm trying to paint some shrubbery and a few people.

I'm using 4 circular plates for locomotion on my vehicle, now I'm trying to allow them to spin freely without flying off the vehicle and move the vehicle forward.

I'm using aluminium for my spacecraft, now I just need it to fly it into space and have a life support system capable of sustaining me up there for a few days.

That's how I'm interpreting your question. I believe you need to read a book instead of ask this general Ubuntu programming forum for advice on how to proceed. At the very least publish your source code so others can give you specific pointers. 

Good luck with your project!

---

