---
title: "tic-tac-toe pattern recognition in python"
date: 2009-07-22
forum: Programming Talk
---

### Post by Azrael on 2009-07-22
I wrote some python code to create a list of all 138 unique (i.e. excluding rotations and reflections) endstates (i.e. the state of the board right after a winning move is made) of tic-tac-toe. Every state is represented as a list of 3 lists (rows from top to bottom) of 3 integers (0 for an empty field, 1 for an 'X', and -1 for an 'O'). Here it is:
```
[[[-1, -1, 1], [1, -1, 1], [0, 1, -1]], [[1, -1, 1], [-1, 1, 1], [-1, 1, -1]], [[1, -1, 0], [1, -1, -1], [1, 1, 0]], [[-1, 1, -1], [1, 1, -1], [-1, 1, 1]], [[-1, 1, 1], [-1, 0, 0], [-1, 0, 1]], [[-1, 1, -1], [1, 1, 1], [-1, 1, -1]], [[1, 1, 1], [-1, 1, -1], [0, -1, 0]], [[-1, -1, -1], [1, 1, 0], [1, -1, 1]], [[-1, 1, -1], [1, -1, -1], [1, 1, 1]], [[0, 1, -1], [0, 1, 0], [-1, 1, 0]], [[-1, 1, 1], [-1, 1, 0], [1, 0, -1]], [[0, 1, 1], [-1, 0, 1], [-1, -1, 1]], [[1, -1, -1], [0, -1, 1], [1, -1, 1]], [[0, -1, 1], [1, -1, 0], [1, -1, 0]], [[1, 0, -1], [1, -1, 0], [1, 1, -1]], [[1, 0, 1], [-1, 1, 1], [-1, -1, -1]], [[-1, 1, 1], [1, -1, 0], [1, -1, -1]], [[1, 0, 1], [0, -1, 1], [-1, -1, 1]], [[1, 1, 1], [0, -1, -1], [1, -1, 0]], [[1, -1, 1], [1, -1, 1], [-1, 1, -1]], [[-1, 1, 1], [0, -1, 1], [1, -1, -1]], [[0, -1, 1], [0, 1, 0], [1, 0, -1]], [[1, 1, -1], [1, -1, 1], [-1, -1, 0]], [[-1, 1, -1], [1, -1, 1], [-1, 1, 0]], [[1, 1, 1], [-1, -1, 1], [1, -1, -1]], [[1, 1, 0], [1, -1, 0], [1, -1, -1]], [[1, 1, 1], [-1, 0, -1], [0, 0, 0]], [[1, 1, 1], [0, -1, 0], [0, -1, 0]], [[1, -1, -1], [1, 1, -1], [0, 1, -1]], [[-1, 1, 0], [-1, 1, 0], [-1, 0, 1]], [[-1, 0, -1], [1, 1, 1], [-1, 1, 0]], [[1, 1, -1], [-1, -1, 0], [-1, 1, 1]], [[0, -1, 0], [1, 1, 1], [0, 0, -1]], [[-1, 0, 1], [0, 1, 1], [-1, -1, 1]], [[1, 1, -1], [1, 0, -1], [-1, 1, -1]], [[1, -1, 1], [1, -1, -1], [-1, 1, 1]], [[-1, -1, 1], [-1, 1, -1], [1, 1, 1]], [[1, 1, 1], [0, 1, -1], [0, -1, -1]], [[0, 0, 1], [-1, -1, 1], [-1, 1, 1]], [[-1, 1, 1], [-1, -1, 1], [-1, 1, 0]], [[0, 1, -1], [1, 1, 1], [-1, -1, 0]], [[1, 0, -1], [1, 1, 1], [-1, -1, 0]], [[-1, 0, -1], [1, 1, 1], [-1, 0, 1]], [[0, 1, 1], [-1, -1, -1], [-1, 1, 1]], [[1, 1, 1], [-1, -1, 1], [-1, -1, 1]], [[-1, 0, 1], [-1, 1, -1], [1, 0, 1]], [[0, -1, -1], [0, 0, 0], [1, 1, 1]], [[1, 1, -1], [-1, 1, -1], [0, 0, 1]], [[1, 1, 1], [0, -1, 0], [-1, -1, 1]], [[-1, -1, -1], [0, 1, 1], [-1, 1, 1]], [[1, -1, 0], [1, 1, 0], [1, -1, -1]], [[1, 0, -1], [1, 0, -1], [0, 1, -1]], [[1, -1, -1], [0, 1, 0], [-1, 1, 1]], [[1, -1, -1], [1, 1, -1], [-1, 1, 1]], [[0, -1, 1], [1, 1, -1], [1, 0, -1]], [[0, 1, 1], [-1, -1, -1], [0, 1, 0]], [[1, -1, 1], [0, -1, 0], [0, -1, 1]], [[1, -1, -1], [-1, 1, 1], [0, 0, 1]], [[-1, 1, 1], [0, -1, 1], [-1, 1, -1]], [[1, 0, 0], [-1, 1, -1], [0, 0, 1]], [[1, -1, 1], [-1, 1, 1], [1, -1, -1]], [[-1, 0, 1], [-1, 1, 0], [1, 0, 0]], [[1, 1, -1], [-1, 1, 0], [-1, 1, 0]], [[-1, 1, -1], [-1, 1, 1], [0, 1, 0]], [[-1, 1, 1], [-1, 1, 1], [1, -1, -1]], [[1, -1, 1], [1, 0, -1], [1, 0, -1]], [[-1, 0, -1], [-1, 0, 1], [1, 1, 1]], [[1, -1, 0], [1, 1, 1], [-1, 0, -1]], [[1, -1, 0], [1, 0, -1], [1, 0, 0]], [[-1, -1, -1], [1, 1, 0], [0, 1, 0]], [[-1, 0, 1], [1, -1, 1], [-1, 1, -1]], [[-1, 1, -1], [1, 1, -1], [1, 0, -1]], [[-1, 0, 0], [0, -1, 0], [1, 1, 1]], [[1, -1, -1], [1, 1, 1], [0, 0, -1]], [[1, -1, 0], [0, -1, 1], [1, -1, 0]], [[0, 0, 0], [-1, -1, 0], [1, 1, 1]], [[0, 0, 1], [1, 0, 1], [-1, -1, -1]], [[-1, 0, 1], [-1, 1, 0], [1, 1, -1]], [[1, 1, -1], [-1, 1, -1], [0, 1, 0]], [[-1, 1, 0], [-1, 1, -1], [1, 1, 0]], [[-1, -1, 1], [1, 1, 1], [1, -1, -1]], [[1, 0, -1], [1, -1, -1], [1, 1, 0]], [[1, -1, 1], [-1, -1, 1], [1, -1, 0]], [[0, 0, -1], [1, 0, -1], [1, 1, -1]], [[1, 0, 0], [1, 1, 0], [-1, -1, -1]], [[1, -1, -1], [-1, 1, 0], [1, 0, 1]], [[1, 1, 1], [-1, -1, 1], [0, 0, -1]], [[1, -1, 1], [0, -1, 1], [0, -1, 0]], [[1, 1, 0], [0, 1, -1], [-1, 1, -1]], [[-1, 1, -1], [-1, 0, 0], [1, 1, 1]], [[1, 1, 1], [-1, 0, 0], [-1, -1, 1]], [[0, 1, 0], [-1, 1, 0], [-1, 1, 0]], [[-1, -1, -1], [1, 1, -1], [1, 1, 0]], [[-1, 1, -1], [1, 1, 1], [0, -1, 0]], [[1, 0, -1], [1, 1, -1], [1, -1, 0]], [[1, 0, -1], [0, 1, 0], [-1, 0, 1]], [[0, -1, 1], [-1, 1, -1], [1, 1, 0]], [[-1, 0, 0], [-1, 1, 1], [-1, 0, 1]], [[1, -1, -1], [1, 1, 0], [0, -1, 1]], [[-1, 0, 1], [1, -1, 1], [0, 0, -1]], [[1, -1, 0], [-1, 1, 0], [1, -1, 1]], [[0, 0, -1], [-1, 0, 0], [1, 1, 1]], [[1, 1, -1], [0, -1, 1], [-1, 0, 0]], [[1, -1, 1], [-1, 1, -1], [1, -1, 1]], [[1, -1, 0], [1, -1, 1], [-1, -1, 1]], [[1, 0, 1], [1, -1, 1], [-1, -1, -1]], [[-1, -1, 1], [-1, 1, 1], [1, 0, 0]], [[-1, 1, -1], [1, 1, 1], [-1, 0, 0]], [[0, -1, 0], [1, 1, 1], [0, -1, 0]], [[0, 0, -1], [1, -1, 1], [-1, 1, 0]], [[-1, 1, 0], [-1, -1, 0], [1, 1, 1]], [[1, 1, 1], [0, -1, -1], [-1, 0, 1]], [[1, 1, -1], [0, -1, 0], [-1, 0, 1]], [[1, -1, -1], [1, 1, 1], [1, -1, -1]], [[1, -1, 0], [-1, 1, -1], [1, 0, 1]], [[0, 1, -1], [1, 0, -1], [0, 1, -1]], [[1, 0, 1], [-1, -1, -1], [1, -1, 1]], [[-1, 1, 0], [-1, 0, -1], [1, 1, 1]], [[-1, 0, 1], [1, -1, 0], [0, 1, -1]], [[-1, -1, -1], [1, 0, 1], [1, -1, 1]], [[0, -1, 1], [-1, 0, -1], [1, 1, 1]], [[1, 1, 1], [-1, 0, -1], [-1, 0, 1]], [[-1, 0, 0], [1, 1, 1], [-1, 0, 0]], [[1, -1, 0], [1, 1, 1], [0, -1, -1]], [[1, -1, 0], [1, 1, -1], [-1, 0, 1]], [[0, -1, 1], [0, 1, -1], [1, 0, 0]], [[1, 0, -1], [1, 0, 0], [1, 0, -1]], [[1, -1, -1], [1, 0, 0], [1, 0, 0]], [[-1, 1, 0], [0, -1, -1], [1, 1, 1]], [[1, 1, 1], [0, -1, -1], [0, -1, 1]], [[0, 1, -1], [0, 1, 0], [0, 1, -1]], [[-1, 0, 1], [-1, 1, 0], [-1, 0, 1]], [[1, -1, 0], [0, 1, -1], [0, 0, 1]], [[-1, 0, 0], [1, -1, 0], [1, 1, -1]], [[1, 0, -1], [1, -1, 1], [1, 0, -1]], [[1, -1, 1], [-1, 1, 0], [1, 0, -1]], [[1, 0, 1], [0, 1, -1], [1, -1, -1]], [[-1, 1, 1], [-1, 0, 1], [0, -1, 1]]]
```Now I want to write some code to statistically analyze this list (i.e. perform pattern recognition on it) and (hopefully) have it detect the "unrandomness" of the winning conditions (i.e. the three-in-a-rows). However, I don't know what to write. Help me.:KS

---

### Post by soltanis on 2009-07-23
Are you trying to teach a neural network or something?

Otherwise it's pretty obvious -- code a rule that recognizes contiguous lines of three boxes in length. No pattern recognition required.

---

### Post by Azrael on 2009-07-23
> **soltanis said:**
> Are you trying to teach a neural network or something?
Possibly.

> **soltanis said:**
> Otherwise it's pretty obvious -- code a rule that recognizes contiguous lines of three boxes in length. No pattern recognition required.
Obviously. No, I want to write code that can derive in-game rules (or at least output some kind of approximation thereof) by giving it data of played games (by other software/humans). Providing it code describing supposedly "universal truths" is allowed, but providing code containing in-game rules is not. If a human watches two other humans play tic-tac-toe in silence for a long period of time, the observing human will come to understand the rules and patterns of the game. I suppose I wish to emulate that process. The problem in the first post would be my first proof of concept.

I figure this will probably not be a simple feat, but I'm curious what approaches people might contribute here. When I have my own code developed more I will update this thread.

---

### Post by nvteighen on 2009-07-23
Interesting project... And maybe my PycTacToe project may be a good platform to test this on. Using the tictactoe plugin (stripped from the UI code) + the PycTacToe Engine inside of some program that collects and interprets the games could work.

Look at my sig if interested!

---

### Post by lisati on 2009-07-23
Some simplification might be possible. Imagine the tictactoe board as a 3x3 array, where each array position corresponds to a board position. There are 8 "triples" to check when looking for a "win": 3 rows, 3 columns and two diagonals. In each "triple" all the elements you are checking will refer to the same player occupying that position.

---

### Post by jero3n on 2009-07-23
You might use a neural network with 9 input neurons to classify every winning (or loosing) position to +1 (or -1) and any other position to X. X might be evaluated, according to the probability of winning or loosing the game in the range (-1,+1).

- Forgot to mention that you could calculate
X = (TotalGain-TotalLost)/(TotalGain+TotalLost), meaning the total games that gained/lost after this position.

Furthermore this trained neural network could be an evaluation function to a search algorithm like minimax.

---

### Post by Tony Flury on 2009-07-23
I think the first thing i would do is to reduce your data set - take into acount that a lot of your data is reflections and rotations - and maybe find a way of recognising those. Also half of your games are identical to the other half - just with all the Xs and Os swapped - so maybe redefine your data so that you use "Winner" and "loser" (which will reduce the duplication).

Also knowing all the end states, will not neccessarily tell you all the rules (although tic tac toe is simple enough that it might do so). 
I would hazard a guess that some of the end states wont ever actually occur when two "perfect" players play each other - I seem to remember somewhere that a perfect player can always force a stalemate (not matter what the starting position).

What you might need to do is to actually have some games played out, move by move, and for the application to use some fuzzy logic to look at particular game states and how often particular moves are made. and how often they lead to a win. It could then start to build a tree like structure that would enable it to learn - although what it will learn is the most likely set of moves to make to lead to a win - play enough games - and it will learn the best path.

---

### Post by jero3n on 2009-07-23
> Some simplification might be possible.

First make it run, then make simplifications :)

By the way
> I suppose I wish to emulate that process.

Your approach with pattern recognition is very correct. In fact, studies has shown that an amateur chess player and a grandmaster can actual 'see' the same amount of moves in the same period of time. The difference is that a grandmaster is experienced, so to recognize some board positions as good, so he can search deeper in them, or to avoid them.

It seems much easier to implement this in tic-tac-toe, as the search space is very small and 'straightforward', meaning that each move simplifies the search space and makes it even smaller. So a recognition algorithm as one I mentioned earlier is possible, by assuming that the result of the game is some function of the board position.

However in chess this approach is impossible, as search space is huge and definitely not 'straightforward' so game result is rarely a function of the current position, but a function to some heuristic rules like "control of the central squares" etc. I dont know if an algorithm could recognize these heuristics without any external knowledge.

Anyway , I would love to see your results :)

---

### Post by soltanis on 2009-07-23
How many layers does your neural net have (I think a linear one is good enough in this case)? If you have hidden layers, how are you doing error propagation? If you are using a simple network with backpropagation I think you should be able to simply supervise the learning of the network; train it to differentiate the basic winning states from the losing states, then show it some test state and see if it recognizes it.

You don't directly program pattern recognition into these networks -- I think the idea is they're suppose to reconfigure themselves to do it.

---

### Post by jero3n on 2009-07-23
> **soltanis said:**
> How many layers does your neural net have (I think a linear one is good enough in this case)? If you have hidden layers, how are you doing error propagation? 

More than one hidden layer is rarely needed, however a linear layer do not seem a pretty good idea in this case. It seems training cases are nonlinear separated. I may be wrong. I would recommend tanh units in the hidden and output layer due to the range of the input [-1,+1] and the desired output [-1,+1] so no normalization is needed and generally perform better when all network signals are in the same range.

> If you are using a simple network with backpropagation I think you should be able to simply supervise the learning of the network; train it to differentiate the basic winning states from the losing states, then show it some test state and see if it recognizes it.

That's what I said. But I think it is better if it is trained also with intermediate board positions by calculating the probability of win/lose. This might improve generalization.

> You don't directly program pattern recognition into these networks -- I think the idea is they're suppose to reconfigure themselves to do it.

Indeed.

---

### Post by soltanis on 2009-07-23
Good call on the non-linear separability -- that whole concept always went over my head when I read about it.

---

### Post by jero3n on 2009-07-23
> **soltanis said:**
> Good call on the non-linear separability -- that whole concept always went over my head when I read about it.
By the way, a network with one or more linear hidden layers is equivalent to a linear network with no hidden layers.

---

### Post by soltanis on 2009-07-23
I thought that was only true when the inputs were linearly separable.

---

### Post by jero3n on 2009-07-23
> **soltanis said:**
> I thought that was only true when the inputs were linearly separable.
No, it is always true :)

[http://en.wikipedia.org/wiki/Multilayer_perceptron](http://en.wikipedia.org/wiki/Multilayer_perceptron)

---

### Post by Azrael on 2009-07-24
Thanks for all your responses.
@nvteighen: Looks good. That code should save me some time at least.
@jero3n: The approach you suggested seems like a good start and similar to what I had in mind.

However, I've come to realize I want/need to brush up on my AI knowledge a bit more first. I'm now reviewing various parts of *Artificial Intelligence: A Modern Approach* (highly recommended by the way - and I hear a 3rd edition will be released later this year), so this project is going to be delayed for a few more days at least... unless someone else wants to start stabbing at it first.

---

### Post by jero3n on 2009-07-24
> **Azrael said:**
> However, I've come to realize I want/need to brush up on my AI knowledge a bit more first. I'm now reviewing various parts of *Artificial Intelligence: A Modern Approach* (highly recommended by the way - and I hear a 3rd edition will be released later this year),

Excellent book. When it comes to neural networks I would definitely recommend "Neural Networks-A comprehensive foundation" by Simon Haykin

---

### Post by nvteighen on 2009-07-24
> **Azrael said:**
> Thanks for all your responses.
@nvteighen: Looks good. That code should save me some time at least.


Thanks. If you have any doubt on PycTacToe's code, contact me via PM.

---

### Post by mulacabu on 2011-02-25
You are on the right track you and  the nearest i have seen to a soloution 
a hint add a one to each cell and you have ie  -1+1=0, 1+1=2 , and 0+1=1 so you have 0 ,1, 2 
for each ROW
so what 

well if you pack those three numbers together you have a base 3 number system 
then convert it to base 10 and pack those three numbers together and you have 
the whole envoirement
And that is only the beging AI==AI
mulacabu
:lolflag:

---

