---
title: "is there a way to . . . .  in C ??"
date: 2011-11-07
forum: Programming Talk
---

### Post by ClientAlive on 2011-11-07
I was wondering if there's a way for the user create a variable with C language. I don't really mean that the value of the variable is defined by user input, I mean more like a word or a name that they specify. It would be printed at the end of the program as a way to label the players but would also need to be used internally in the program to control the program itself (probably with if and if else statements). You don't know what they are going to type in for a names until they do it and there shouldn't be much constraint on what they can enter.

Does anyone know if this can be done?
---------------

Edit:

Arrays??

---

### Post by schauerlich on 2011-11-07
I'm not really sure what your goal is here, but it sounds like what you're describing is an [associative array](http://en.wikipedia.org/wiki/Associative_array) with strings for keys. To answer your question: no, C does not have anything like this built in. However, it's not terribly hard to implement yourself, and I'm sure good open source implementations exist out there that you could use instead.

---

### Post by Bachstelze on 2011-11-07
If I understand you correctly, you want a variable whose name depends on data entered by the user. You can do that (or something close enough) using a data structure caled a [hash table](http://en.wikipedia.org/wiki/Hash_table). However, C does not provide hash tables (or any advanced data structure, for that matter), so you will have to implement it yourself, or use an implementation written by someone else. If you don't absolutely need to use C, you can use other languages that provide them, like Python or PHP (they are called "dictionaries" in Python and "associative arrays" in PHP).

---

### Post by ClientAlive on 2011-11-07
Oh, well, about two weeks ago we did a project for my programming class where we wrote a program that keeps track of the scores in a basketball game. Last night, playing cards at my friends house we got to talking about programming (well I did anyway) and she suggested I write a program that keeps track of the points in a card game (so you don't have to use a pen and paper you know). Well that sounded kinda cool to me and I thought I could modify that class project easy enough to do it --which I began to do today. What I hadn't really thought about until I saw the code again was the additional elements that might have to go into something like that.

To begin with I knew I would want to let the user label the players however they want. If they want to enter the persons name or whatever. Thing about it is, in my original program (the one from the class project) it used the values the person selected for team choice to determine which of the two calculations to run (and thus which of the two scores was being added to). In that original program the user was constrained to choosinge either 1 or 2. In the case of modifying the program though, it would have to use whatever the user entered to label the players as part of the program control.

Then, between writing that original post and now, I got to thinking it would be cool if they could choose the number of players first thing off and whatever that number is would determine how many poeple to keep score of. I also hadn't thought of it until recently but some card games you subtract from the score as well as add. I wondered if that was not already possible though by simply entering the score with a negative sign out front (since in algebra adding the opposite is the same as subtracting). I guess I figured I'd find that last part out when I tried to do it in the program.

So yeah, not very experienced in programming. Just thought it would be neat to take some dumb thing we created in class and really make something useful out of it.  :D

---

### Post by schauerlich on 2011-11-07
Sounds like it's time to learn about structs and dynamically allocated memory. Make a struct that has two fields, a string containing the player's name, and their score. Find out how many players you'll be keeping track of, and allocate an array of that many structs. Fill in each struct with the right name and score. Iterate through the array to find the right player each time you need to change their score. For a simple program with a small amount of players, that should be sufficient.

---

### Post by ClientAlive on 2011-11-07
> **schauerlich said:**
> Sounds like it's time to learn about structs and dynamically allocated memory. Make a struct that has two fields, a string containing the player's name, and their score. Find out how many players you'll be keeping track of, and allocate an array of that many structs. Fill in each struct with the right name and score. Iterate through the array to find the right player each time you need to change their score. For a simple program with a small amount of players, that should be sufficient.


Wow. That'd be cool! I'd feel awfully proud of myself if I could pull that off. Thank's for giving me some stuff to go off of. Bet there's lots of info on those things out there for me.

:D

---

