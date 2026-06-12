---
title: "How do you , , , in C ??"
date: 2011-11-09
forum: Programming Talk
---

### Post by ClientAlive on 2011-11-09
Hi,

Well, a day or so ago I asked about doing something with converting a program I made for a class project (a program that kept the score of a basketball game) into something a little different (a program that keeps the scores of a card game and lets the user define the number and labels of the scores being kept). I'm still going to be messing w/ that and seeing if I can pull it off, but in the mean time I thought I'd try to tweak that same program (the basketball score one) to be a little more fun for the user. Basically taking a smaller learning step in between doing the card game scoring thing (to help me learn).

So, I'll be looking on the internet for information but I wondered if anyone would be interested to comment if I put this out there.

I've attached both files (actually the basketball score one is a second one I did from scratch again just for practice - I have no idea how similar or different it is from the first one, just that it does the same thing).

So, basically, all I was trying to do is define a different thing for the user to enter to end the program, rather than just some specific number. This time I thought they could enter a particular fun phrase to end the program but I'm not certain what data type would be suited to something like that. An array occured to me but I'm not so sure that is suited to what I'm trying to do with it.

If you like, the comments at the beginning of the file indicate the difference in what I was trying to do (if compared to one another). And the second one (the one I was trying to have the user enter a phrase to end the program) I even took a stab at making that work. Only problem is, it doesn't  :P 

So if anyone would like to chime in on a good, simple way to do this I'd love that. It would help me know what to look for to learn about and maybe I can get the program to work that way.

Thanks in advance guys.

Jake

---

### Post by Vaphell on 2011-11-09
Exiting is not exciting ;-)
Explore other, cooler things first.
You better get used to the concept of arrays. You could have made 'total' an array and index it with 'team' - you would get rid of the whole if block and could use universal ```
total[team]=total[team]+score
``` instead.
Also learn to use structs to package the data into functional pieces so you don't have to micromanage all these loose variables.
Try writing something fancy - team is a struct with a team name and with full list of players with their numbers and individual scores.

---

### Post by 11jmb on 2011-11-09
> **ClientAlive said:**
> 
I've attached both files (actually the basketball score one is a second one I did from scratch again just for practice - I have no idea how similar or different it is from the first one, just that it does the same thing).


I'm not sure if re-doing your work is the best use of your time, but you just inadvertently gave a decent explanation of abstraction, which is an extremely important computer science concept. :D


> **ClientAlive said:**
> This time I thought they could enter a particular fun phrase to end the program but I'm not certain what data type would be suited to something like that. An array occured to me but I'm not so sure that is suited to what I'm trying to do with it.


You should not be using an int, though. "peach out home buoye" is a string literal, which is of type **const char*** Pointers and arrays will certainly be covered in future lessons, so this may be a little bit over your head for now. better choices would be a single character such as 'Q' or a negative number to terminate the program.

---

### Post by Arndt on 2011-11-09
> **ClientAlive said:**
> 
So, basically, all I was trying to do is define a different thing for the user to enter to end the program, rather than just some specific number. This time I thought they could enter a particular fun phrase to end the program but I'm not certain what data type would be suited to something like that.

A common practice is to detect end of file.

---

### Post by ClientAlive on 2011-11-09
> **Vaphell said:**
> Exiting is not exciting ;-)
Explore other, cooler things first.
You better get used to the concept of arrays. You could have made 'total' an array and index it with 'team' - you would get rid of the whole if block and could use universal ```
total[team]=total[team]+score
``` instead.
Also learn to use structs to package the data into functional pieces so you don't have to micromanage all these loose variables.
Try writing something fancy - team is a struct with a team name and with full list of players with their numbers and individual scores.


Yeah, structs.  :D  And arrays . . .

I did read some stuff about structs on the internet the other night. Maybe I wasn't looking at the best material on the subject but it seemed pretty complicated, what they were talking about.

I'm not really sure what you just said about 'indexing total with team', but it sounds interesting. I'm looking forward to doing some extra programming projects on the side so I can really get the hang of it. :)


> **11jmb said:**
> I'm not sure if re-doing your work is the best use of your time, but you just inadvertently gave a decent explanation of abstraction, which is an extremely important computer science concept. :D




You should not be using an int, though. "peach out home buoye" is a string literal, which is of type **const char*** Pointers and arrays will certainly be covered in future lessons, so this may be a little bit over your head for now. better choices would be a single character such as 'Q' or a negative number to terminate the program.


Yeah, I mis-spelled that word in the comment area. lol. It was supposed to go: "Peace Out Home Buoye" but ok.

What we had done before was a number (one of them I used -999 and the other I had used 777). I was just trying to figure out something cool I could do that would stretch me a little but not so much it was out of reach, you know?


> **Arndt said:**
> A common practice is to detect end of file.


I just read something on that. That guy was using it bc he needed to scanf something in from an outside file and didn't know how big the file was or where it would end. They told him to make his while loop condition so it kept running the loop until it reached EOF. I wonder what other ways it can be used (we've only worked with a single file so far).


:)

---

### Post by 11jmb on 2011-11-09
Structs are pretty simple. You will get the hang of them right away.

The  wikipedia article gives you some good starting points.

[http://en.wikipedia.org/wiki/Struct_(C_programming_language)](http://en.wikipedia.org/wiki/Struct_(C_programming_language))


You could try making a struct Team that looks something like:

```
struct bballTeam{
    int score;
    int fouls;
    char* name; //This is a string as described earlier
    bool hasPossession;
};

```

Then you would declare them as:
```

struct bballTeam home;
struct bballTeam visitor;

home.name = "Raptors";
home.score = 0;

home.score+=2;

//and so forth

```

---

### Post by Vaphell on 2011-11-09
> **ClientAlive said:**
> I'm not really sure what you just said about 'indexing total with team', but it sounds interesting. I'm looking forward to doing some extra programming projects on the side so I can really get the hang of it. :)


you keep score with 2 loose variables and there is no obvious relation between team that needs its score updated (1 or 2) and total1 and total2 variables. Ok, there is a number in name that indicates that but program doesn't care about that, it treats it as just another identifier. That connection exists only in your head.
What you should do is to explicitly tie the value of total to the value of team and you can do that via array index.

you declare total as an array of 2 elements of type int.
int total[2];
in C indexing starts from 0 so array declared as total[2] consists of 2 elements indexed with 0 (total[0]) and 1 (total[1]).
Let's say you decide that team can only be 1 or 2. you can translate the value of team to the index of array easily (1->total[0], 2->total[1], so universal rule would be team->total[team-1]). To update the score related to the given team you need to use
**total[team-1]+=score;**
using arrays and indexes gives you a way to create physical relations between parts of data and it greatly simplifies managing that data. You can skip that stuff with explicit if team=... then scoreX=... for every allowed case. Just imagine amount of work required when you would want to introduce minor changes in such logic blocks if every relation was to be explicitly coded by hand.
In case of array index you have one simple universal formula.

---

