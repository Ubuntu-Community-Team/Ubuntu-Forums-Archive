---
title: "PycTacToe: a project for Python mid-starters"
date: 2008-10-25
forum: Programming Talk
---

### Post by nvteighen on 2008-10-25
Hi there!

It's quite common to see people here asking for some inspiration after they've managed to learn their first language or asking where to find a project to train their skills.

LaRoza created the [SysRes]("https://launchpad.net/sysres") project (of which I'm also part), but in my opinion that's a project suitable for people with some experience.

So I decided to create a Launchpad project called [PycTacToe]("https://launchpad.net/pyctactoe") written in Python. Don't expect something spectacular: it's just a TicTacToe but aimed to be spiced-up (made to be flexible so we can get similar games easily, like Connect-Four or a Tic-Tac-Toe in a N x N board, etc.).

No, this won't be a killer application... but it can become an interesting way to help people learn how to program.

You'll quickly notice that the codebase is taken from my Tic-Tac-Toe engine I posted [here some time ago]("http://ubuntuforums.org/showthread.php?t=894509"). And you'll notice that the engine is working well enough... so, you may be asking yourself "What could I do for this program that seems to be finished?". Well, it's far from finished... Some ideas:

0. **A better interface:** I'm really bad at coding interfaces and the current one is just crap. If you know some GUI toolkit, it will be really fine.
1. **Derivatives (d(tic-tac-toe)/dx = ... :)):** The current "engine" is quite flexible enough, so if you're creative, why don't you share (and code) your idea?
2. **Improve the "engine":** Well, mine is good, but maybe yours can be better!
3. **An AI:** This is possibly the most interesting part. The "engine" lacks an Artificial Intelligence... so only human player games are allowed currently.
4. **Not-so-auxiliary work:** Bug catching, ideas, documentation, translations may seem "useless" or "secondary" tasks, but are also very important to keep things going.

Launchpad uses the Bazaar version control system. Install the 'bzr' package from the Ubuntu repos to get it... The documentation for Bazaar ([http://bazaar-vcs.org](http://bazaar-vcs.org)) and Launchpad ([https://help.launchpad.net](https://help.launchpad.net)) are very easy to follow, but if you have any question about them, just ask here.

Hope this attracts people and help them to develop their (and also mine, why not?) skills.

---

### Post by OutOfReach on 2008-10-25
Cool, this will help me kill some time.

---

### Post by nvteighen on 2008-10-25
> **OutOfReach said:**
> Cool, this will help me kill some time.
Welcome!

Something I forgot: I'll try to have an API documentation for the "engine" written in the less possible time. Meanwhile, you'll have to read the docstrings from the source code.

---

### Post by LaRoza on 2008-10-25
I probably won't be in for coding, but I'll help test it. After the few sysres bugs we had, I think you could use a tester who doesn't "know" the code.

---

### Post by CptPicard on 2008-10-25
Okay, I will contribute in the AI part if I have the time. Seems like a good way to demonstrate an alpha-beta pruned search instead of the naive full search.

---

### Post by LaRoza on 2008-10-25
> **CptPicard said:**
> Okay, I will contribute in the AI part if I have the time. Seems like a good way to demonstrate an alpha-beta pruned search instead of the naive full search.

Great, a bunch of lisp fanboys jump in and really do a number on the code...

It happened to sysres, it can happen to anyone.

---

### Post by LaRoza on 2008-10-25
Oh, if the OP wants a forum, I can make one on the sysres board. It may be neat to have a bunch of forum projects on that board (I'd change the title to reflect that if it happens)

---

### Post by snova on 2008-10-25
Ugh.

I once tried writing a program that could play chess- it didn't have to be good. If it could pick a random legal move without being ignorant of any rules I'd have been happy. But *[FONT=Arial]noooo[/FONT]*. I didn't even get representation down.

Then it was checkers. That didn't last long, I couldn't think up a good board representation.

So I settled for Tic Tac Toe. But *noooo*, I couldn't get even that to work right.

Memoirs aside, good idea. But won't there eventually be nothing left to do? There's only so many features you can pile on a Tic Tac Toe application...

---

### Post by LaRoza on 2008-10-25
> **snova said:**
> There's only so many features you can pile on a Tic Tac Toe application...

Read the description of the app ;)

It takes that into account.

---

### Post by bobbocanfly on 2008-10-25
Great idea. Already hacking away.

---

### Post by nvteighen on 2008-10-26
Wow, thanks for your input. I've pushed the API documentation to make things easier for you guys/gals.

But, before you start hacking interfaces, please take a look at the Engine first to have a better API... otherwise, we can suffer a Sysres-itis... :p

@LaRoza: A forum would be great. You could be the admin, if you like.

---

### Post by LaRoza on 2008-10-26
> **nvteighen said:**
> 
But, before you start hacking interfaces, please take a look at the Engine first to have a better API... otherwise, we can suffer a Sysres-itis... :p


Hey! Are you mocking my original code :-)

> 
@LaRoza: A forum would be great. You could be the admin, if you like.
Ok, I'll put it in the works. About being admin, I sort off have no choice as I can't make the forum without being an admin ;)

[http://laroza.19.forumer.com/](http://laroza.19.forumer.com/)

---

### Post by nvteighen on 2008-10-26
> **LaRoza said:**
> Hey! Are you mocking my original code :-)

Of course... As pmasiar always says: learn from other's mistakes not from yours... ;)

I'll try to keep the engine compatible during a release... Breakages should occur only when releasing a major-number version.

> Ok, I'll put it in the works. About being admin, I sort off have no choice as I can't make the forum without being an admin ;)

[http://laroza.19.forumer.com/](http://laroza.19.forumer.com/)

Thank you!

---

### Post by BackwardsDown on 2008-10-26
I have made some edit's, created a bazaar. But how do I submit my edits to the bazaar? I'm getting this:

```
niels@inoue:~/python2.5/tictactoe$ ls
ChangeLog  COPYING  COPYRIGHT  doc  pttengine.py  pttengine.pyc  pyctactoe
niels@inoue:~/python2.5/tictactoe$ bzr push lp:~nielsegberts/pyctactoe/niels  
bzr: ERROR: Not a branch: "/home/niels/python2.5/tictactoe/".
niels@inoue:~/python2.5/tictactoe$
```

---

### Post by nvteighen on 2008-10-26
> **BackwardsDown said:**
> I have made some edit's, created a bazaar. But how do I submit my edits to the bazaar? I'm getting this:

```
niels@inoue:~/python2.5/tictactoe$ ls
ChangeLog  COPYING  COPYRIGHT  doc  pttengine.py  pttengine.pyc  pyctactoe
niels@inoue:~/python2.5/tictactoe$ bzr push lp:~nielsegberts/pyctactoe/niels  
bzr: ERROR: Not a branch: "/home/niels/python2.5/tictactoe/".
niels@inoue:~/python2.5/tictactoe$
```

First you need to transform your directory into a branch:
```

bzr init

```

After that, you have to tell Bazaar what files are you including. You want them all, so we just use the recursive adder:
```

bzr add

```

But adding stuff means a change in the branch, so you have to register (commit) that change using:
```

bzr commit -m "some message"

```

("Initial import" is a very widespread log when just creating a branch).

And then upload by using push as you did before.

Whenever you do some change to your code, the process is commit->push. When you want to get changes from elsewhere, the process is merge->commit.

EDIT: When deleting, renaming, adding files ALWAYS use the bzr "shell" functions (bzr rm, bzr mv, bzr add), never bash commands, Nautilus, whatever. Otherwise, weird stuff happens in the source, like resurrecting old code.

---

### Post by fiddler616 on 2008-10-26
Sweet! I'm in.
(The timing of this is perfect: I just entered that awkward moment of "I finished the tutorial...should I learn GUI programming...or work on a project...but I don't have any ideas...hmm...?")

---

### Post by BackwardsDown on 2008-10-26
> **nvteighen said:**
> And then upload by using push as you did before.

Whenever you do some change to your code, the process is commit->push. When you want to get changes from elsewhere, the process is merge->commit.


```
niels@inoue:~/python2.5/tictactoe$ bzr push lp:~nielsegberts/pyctactoe/niels  
bzr: ERROR: Transport operation not possible: http does not support mkdir()
```

After committing it still wont upload my changes to my bazaar.

edit: nvm, I think it has something to do with my username

---

### Post by nvteighen on 2008-10-26
> **BackwardsDown said:**
> ```
niels@inoue:~/python2.5/tictactoe$ bzr push lp:~nielsegberts/pyctactoe/niels  
bzr: ERROR: Transport operation not possible: http does not support mkdir()
```

After committing it still wont upload my changes to my bazaar.

edit: nvm, I think it has something to do with my username
What's the error message? If it's "Name unknown" or similar it's due to some server unstability...

But anyway, I see you've succesfully commited to your branch.

EDIT: How did you get the source from trunk? Did you use the bzr branch command? I ask you that because if you did, you shouldn't have had to 'bzr init'... and your branch revisions start at No. 1...

---

### Post by BackwardsDown on 2008-10-26
> **nvteighen said:**
> What's the error message? If it's "Name unknown" or similar it's due to some server unstability...

But anyway, I see you've succesfully commited to your branch.

EDIT: How did you get the source from trunk? Did you use the bzr branch command? I ask you that because if you did, you shouldn't have had to 'bzr init'... and your branch revisions start at No. 1...

This command needed to be ran, so I could authenticate myself:
```
bzr launchpad-login nielsegberts
```

And yes, now I have just copied (terminal cp) the contents of the official trunk to my bazaar. Should I re-do it?

edit:
I also made another fix, the printing of the board is more Object Orientated now.

---

### Post by nvteighen on 2008-10-26
> **BackwardsDown said:**
> This command needed to be ran, so I could authenticate myself:
```
bzr launchpad-login nielsegberts
```

And yes, now I have just copied (terminal cp) the contents of the official trunk to my bazaar. Should I re-do it?

No, just leave it... but for the next time, you better avoid that and just do 'bzr branch ...'

> edit:
I also made another fix, the printing of the board is more Object Orientated now.

Please, read my review. I disapprove that last fix... I sort-of like the first... But here I'd like to hear some opinions on this. Anyway, I can merge partially if needed.

---

### Post by fiddler616 on 2008-10-26
Hmm. I lose.
I scrupulously followed Bazaar's instructions for creating a branch and uploading files to it, and it seemed like it worked, but when I look at the source code *from Firefox* it's the exact same thing--with none of the modifications I thought I uploaded.
(The branch in question is alicia-tsm)
Help please?
Thanks

---

### Post by nvteighen on 2008-10-26
> **fiddler616 said:**
> Hmm. I lose.
I scrupulously followed Bazaar's instructions for creating a branch and uploading files to it, and it seemed like it worked, but when I look at the source code *from Firefox* it's the exact same thing--with none of the modifications I thought I uploaded.
(The branch in question is alicia-tsm)
Help please?
Thanks

What does 'bzr status' output? Are you sure you committed your changes?

---

### Post by fiddler616 on 2008-10-26
> **nvteighen said:**
> What does 'bzr status' output? Are you sure you committed your changes?

```
$bzr status
modified:
  pttengine.py
$ bzr push lp:~tsmacdonald/pyctactoe/alicia-tsm
No new revisions to push.


```
>commited your changes
That's a new term.
I think I....I forget the term. First, there was a line of code to upload the files, which I did, and then it went form saying there were no files to saying there were, in fact, files.
And I had a nice little song and dance with SSH keys, but that all seemed to go fine.
PS: Is it pronounced pick-tac-toe (to rhyme with tic-tac-toe), or pike-tac-toe (to sound like **Py**thon?)

---

### Post by nvteighen on 2008-10-26
> **fiddler616 said:**
> ```
$bzr status
modified:
  pttengine.py
$ bzr push lp:~tsmacdonald/pyctactoe/alicia-tsm
No new revisions to push.


```
>commited your changes
That's a new term.
I think I....I forget the term. First, there was a line of code to upload the files, which I did, and then it went form saying there were no files to saying there were, in fact, files.

After you've done your coding, you have to do:
```

bzr commit -m "Some informative message"
bzr push lp:(wherever)

```

> PS: Is it pronounced pick-tac-toe (to rhyme with tic-tac-toe), or pike-tac-toe (to sound like **Py**thon?)

Both pronounciations are possible. I'm a Linguistics student and can assure you that I've heard both ;)

---

### Post by fiddler616 on 2008-10-26
> **nvteighen said:**
> After you've done your coding, you have to do:
```

bzr commit -m "Some informative message"
bzr push lp:(wherever)

```

Oooh, thanks.

> 
Both pronounciations are possible. I'm a Linguistics student and can assure you that I've heard both ;)
OK :)
(I'd always assumed your Filología major was in Spanish, but I guess I was wrong (?))

---

### Post by nvteighen on 2008-10-26
> **fiddler616 said:**
> 
(I'd always assumed your Filología major was in Spanish, but I guess I was wrong (?))

Yes, it is (U. de Navarra, Pamplona), but I'm not interested on Literature at all.

---

### Post by fiddler616 on 2008-10-26
> **nvteighen said:**
> Yes, it is (U. de Navarra, Pamplona), but I'm not interested on Literature at all.
I've always found Spanish (as in: language, not: from Spain) literature to be a bit too morbidly creepy (courtesy of Quiroga, Cortázar and friends), IMHO
But we digress :) .
In order to justify this post, could somebody explain, in 5 sentences or less, this (which seems to be standard fare) :
```

def __init__(self, n, players = ["O", "X"]):
    '''Docstring omitted for clarity'''
    self.size = n 
```
All right, that's a terribly ambiguous question. Take two:
Why declare self.size, if n is the same value?
What's the difference between self.size and size? They're both local variables....right?
I think the the biggest missing piece in my grokking of OOP is the correct use of self...because when I think about OOP abstractedly, it makes perfect sense, it's the nitty-gritty that gets me.
```
reasons_to_work_on_project += 1
```
Thanks y'all.

---

### Post by nvteighen on 2008-10-27
Well, you need the self.size = n line to make the object's attribute size to be n. The idea of OOP is to have everything referred to the same thing in the same place, so you can express an class of objects with its attributes and actions defined together. The n variable is just a variable that could come from anywhere; by assign that value to the size attribute, we're "binding" that value to be a significant part of the object.

"self" is a Python-specific thing. If you want a variable to be an attribute of an object created from that class, you use "self". Otherwise, you'll create a local variable that can't be accessed from outside its natural scope.

---

### Post by fiddler616 on 2008-10-27
> **nvteighen said:**
> Well, you need the self.size = n line to make the object's attribute size to be n. The idea of OOP is to have everything referred to the same thing in the same place, so you can express an class of objects with its attributes and actions defined together. The n variable is just a variable that could come from anywhere; by assign that value to the size attribute, we're "binding" that value to be a significant part of the object.

"self" is a Python-specific thing. If you want a variable to be an attribute of an object created from that class, you use "self". Otherwise, you'll create a local variable that can't be accessed from outside its natural scope.
Thank you very much.

I learn better through talking, so in summary:
* self makes variables global, tidily. (since making a 'real' global variable could lead to conflicts)
* Therefore, self.size = n is necessary, to make the value of n available everywhere.

---

### Post by nvteighen on 2008-10-27
Btw, I've been looking at your Alicia code. I know it's still a draft, but please try to keep it as more generic as you can, so the same AI works in differently sized boards, not only the 3 x 3 one.

---

### Post by fiddler616 on 2008-10-27
> **nvteighen said:**
> Btw, I've been looking at your Alicia code. I know it's still a draft, but please try to keep it as more generic as you can, so the same AI works in differently sized boards, not only the 3 x 3 one.
Refresh my memory: on a 5x5 board, do you need to connect 3 or 5?
Regardless, I think the strategy for a 3x3 game is different enough from an NxN game that trying to write one AI to cover both would be problematic.
I have a plan to write a function 'legal_move()' that will have Alicia do a random legal move (in part as an escape clause for the current Alicia). I'm afraid that the only thing I can really contribute just now for an NxN AI script is:
```

check_opp_winning()
check_alicia_winning()
legal_move()
```

I think part of my trouble might stem from the fact that I'm *terrible* at playing NxN tic-tac-toe in real life--never mind Python.

All of that said, if somebody loosely describes a good strategy in English, I'd be perfectly happy to do my best in converting it to Python.

---

### Post by BackwardsDown on 2008-10-27
> **fiddler616 said:**
> Refresh my memory: on a 5x5 board, do you need to connect 3 or 5?
Regardless, I think the strategy for a 3x3 game is different enough from an NxN game that trying to write one AI to cover both would be problematic.

The idea of this program is to write everything as generic as possible. So writing your AI so that it can easily be converted to 4-in-a-row, checker, etc.

You can achieve that by creating a function that can analyse the board, and acts upon a score that is being returned. If the game changes, you only need to rewrite those functions.

But I don't think its handy to walk that path for an AI. Writing a more-or-less generic AI is not a project for a "mid-starter" I think. And the problem is with generic AI's is that they are either to easy to beat, or to hard.

When writing a AI it's not about how to write the best one (because with tic-tac-toe you will create a bot that always draws) but to create one that is fun to play against. It has to be able to make little mistakes etc. The nature for a mistake is different for a different type (eg 5x5 board) than for tic-tac-toe.

I think the best way is to create several AI-objects, eg, alice, bob, paul, etc. For every game 1. So you can make every game-type challenging.

---

### Post by CptPicard on 2008-10-27
Just a note... I am currently writing an alpha-beta pruned search for the AI in this... it handles two-player games, at least, not sure about multiplayer ones.

The search itself is pretty general, and the evaluation function I am applying at the moment is really simple -- it just scores continuous segments, and scores higher the longer the segment is. There's probably room to integrate whatever you're doing into my search, because simple heuristics is not going to take you far.... but let's get the search off the ground first.

---

### Post by bobbocanfly on 2008-10-27
> **BackwardsDown said:**
> The idea of this program is to write everything as generic as possible. So writing your AI so that it can easily be converted to 4-in-a-row, checker, etc.

You can achieve that by creating a function that can analyse the board, and acts upon a score that is being returned. If the game changes, you only need to rewrite those functions.

But I don't think its handy to walk that path for an AI. Writing a more-or-less generic AI is not a project for a "mid-starter" I think. And the problem is with generic AI's is that they are either to easy to beat, or to hard.

When writing a AI it's not about how to write the best one (because with tic-tac-toe you will create a bot that always draws) but to create one that is fun to play against. It has to be able to make little mistakes etc. The nature for a mistake is different for a different type (eg 5x5 board) than for tic-tac-toe.

I think the best way is to create several AI-objects, eg, alice, bob, paul, etc. For every game 1. So you can make every game-type challenging.

I think this architecture is the best for making this game:

- Game "types" are defined by rules in their own classes. Each one has a check() function that checks to see if anyone has won, then returns the current players "mark" if someone has won. 
- The AI is all based on a single generic AI engine, that each GameType class passes its rules to. 

then this kind of code could be the main game loop:

```

game = TicTacToe(...<here is the game stuff>)
ai = Alicia(game.ai_rules)
front = Frontend(get_frontend())
game.using_ai = True

while not game.check():
    input = front.get_input()
    game.update(input)

    if game.using_ai:
       game.update(ai.take_turn())

    front.update(game) # Update the frontend

frontend.winner(game.current_player)

```

I dont know if frontends can work like that (getting pinged for input, then responding when told to update)(ive never really done any GUI programming_, but that makes sense in my head

---

### Post by fiddler616 on 2008-10-27
> **BackwardsDown said:**
> 

But I don't think its handy to walk that path for an AI. Writing a more-or-less generic AI is not a project for a "mid-starter" I think. And the problem is with generic AI's is that they are either to easy to beat, or to hard.

If somebody offers to 'mentor' me on this, I'd be happy to join. But you're right--it's definitely beyond my current skills.
> 
When writing a AI it's not about how to write the best one (because with tic-tac-toe you will create a bot that always draws) but to create one that is fun to play against. It has to be able to make little mistakes etc. The nature for a mistake is different for a different type (eg 5x5 board) than for tic-tac-toe.

I think the best way is to create several AI-objects, eg, alice, bob, paul, etc. For every game 1. So you can make every game-type challenging.
Unless sombeody has a problem with this..:
The Alicia I just made is now Brian, the brainy 3x3 bot. As soon as I find time, I'll also write Bob, the not-brainy 3x3 bot. It shouldn't be hard:
```
check_opp_winning
check_alicia_winning
legal_move
```
I know that's the same code block as before, but on a 3x3 board, due to the limited number of available moves (especially after filtering out winning/losing ones) is small enough that it would look like a "kinda dumb" move, not a "random" one.

@CptPicard: While writing this, I saw that you posted something. Reply coming.

---

### Post by fiddler616 on 2008-10-27
> **bobbocanfly said:**
> I think this architecture is the best for making this game:

- Game "types" are defined by rules in their own classes. Each one has a check() function that checks to see if anyone has won, then returns the current players "mark" if someone has won. 
- The AI is all based on a single generic AI engine, that each GameType class passes its rules to. 

then this kind of code could be the main game loop:

```

game = TicTacToe(...<here is the game stuff>)
ai = Alicia(game.ai_rules)
front = Frontend(get_frontend())
game.using_ai = True

while not game.check():
    input = front.get_input()
    game.update(input)

    if game.using_ai:
       game.update(ai.take_turn())

    front.update(game) # Update the frontend

frontend.winner(game.current_player)

```

I dont know if frontends can work like that (getting pinged for input, then responding when told to update)(ive never really done any GUI programming_, but that makes sense in my head

+1, please delete any statements I made in the previous post which do not agree with this.

---

### Post by fiddler616 on 2008-10-27
> **CptPicard said:**
> Just a note... I am currently writing an alpha-beta pruned search for the AI in this... it handles two-player games, at least, not sure about multiplayer ones.

The search itself is pretty general, and the evaluation function I am applying at the moment is really simple -- it just scores continuous segments, and scores higher the longer the segment is. There's probably room to integrate whatever you're doing into my search, because simple heuristics is not going to take you far.... but let's get the search off the ground first.
"Multiplayer"...in tic-tac-toe? Oh, I guess for NxN boards where N>3. Never mind.
If there's a way I can help, let me know. I'm currently lamenting the fact that my only knowledge of alpha-beta pruned searches/heuristics came from a cursory read of the Wikipedia article.
(Woot! Moved up a bean level!)

---

### Post by nvteighen on 2008-10-27
> **bobbocanfly said:**
> I think this architecture is the best for making this game:

- Game "types" are defined by rules in their own classes. Each one has a check() function that checks to see if anyone has won, then returns the current players "mark" if someone has won. 
- The AI is all based on a single generic AI engine, that each GameType class passes its rules to. 



I like that... And it should be quite easier than you believe: Python allows us to pass whole functions, so you could create your rules and store it as the board's check() method (and the AI).

But just want you to note that the AI is rather an afterthought... It would be nice, of course, but I'm still more concerned on how the API works. I'm working on some changes, but I'll be committing them to my personal branch (lp:~evigo/pyctactoe/evigo) and only merge those changes upstream when reasonable.

---

### Post by CptPicard on 2008-10-27
> **nvteighen said:**
> I like that... And it should be quite easier than you believe: Python allows us to pass whole functions, so you could create your rules and store it as the board's check() method (and the AI).

For example my own AI module does not really make any assumptions about any representations or designs you may have outside of it. What it wants is a board representation which is essentially a function or object that takes (i,j) and returns a symbol -- this can be done by either wrapping your Board object getter in a lambda and passing that, or implementing __call__ on Board itself.

Then it needs a function that recognizes a win condition, and maybe the symbol you want a best move for... it is possible that you could even externalize the evaluation function, but it is easy to take the module apart in that case.

The implementation itself is pure functional in the sense that it does not produce any side effects to the board state that you ask a move for. This is probably suboptimal in performance sense but I hold out hope that a linear-time seek into an altered board state to find board(i,j) is going to be made negligible by the speed of the actual search... but we'll see. Creating a stateful board state for the search can be an exercise for someone adventurous if my system proves too slow :)

---

### Post by sheto on 2008-10-28
I am willing to code if someone could please teach me how.

---

### Post by BackwardsDown on 2008-10-28
You can start by learning python :) .

It's not that hard. I found this book very handy:
[http://www.greenteapress.com/thinkpython/thinkCSpy/](http://www.greenteapress.com/thinkpython/thinkCSpy/)

And there is off course the official documentation/tutorials:
[http://docs.python.org/](http://docs.python.org/)

---

### Post by fiddler616 on 2008-10-28
[http://www.swaroopch.com/notes/Python](http://www.swaroopch.com/notes/Python)
has a really nice mix of being concise but clear

---

### Post by sheto on 2008-10-28
Thank you for your swift reply, BackwardsDown and fiddler616. Your help is appreciated. The thing is that I know Python. I'm just new to this Launchpad/Bazaar/Pygame thing. An easy-to-understand Pygame documentation would be nice.

---

### Post by fiddler616 on 2008-10-28
> **sheto said:**
> Thank you for your swift reply, BackwardsDown and fiddler616. Your help is appreciated. The thing is that I know Python. I'm just new to this Launchpad/Bazaar/Pygame thing. An easy-to-understand Pygame documentation would be nice.
As far as I know, PycTacToe isn't using Pygame (yet(?)). Pygame is just a module frequently used for easy Python game programming.
To do Bazaar right, you need to install the Bazaar package, and then everything else should be more or less apparent. The launchpad site will have lines of code for the Terminal to download 'branches' of the source.
Launchpad, in this case, is just a really handy CMS for dealing with the logistics of a multi-person project.

In terms of actual coding, read the first post in this thread, and have a look at the source code, and then decide where you want to help.

If you choose to help out with AI, you should probably read through the rest of this thread too--a few important decisions have been made.

Also check out other people's branches, to make sure you're not duplicating an effort.

---

### Post by nvteighen on 2008-10-28
> **sheto said:**
> Thank you for your swift reply, BackwardsDown and fiddler616. Your help is appreciated. The thing is that I know Python. I'm just new to this Launchpad/Bazaar/Pygame thing. An easy-to-understand Pygame documentation would be nice.
As you've been told, you have to install the 'bzr' package from the repos and also register an account at Launchpad ([https://launchpad.net](https://launchpad.net)). The latter is also useful when you find a bug in Ubuntu, for example. Please refer to both's documentation [http://bazaar-vcs.org/Documentation](http://bazaar-vcs.org/Documentation) (for Bazaar) and [http://help.launchpad.net](http://help.launchpad.net) (Launchpad).

After you've set your account up and roughly understood what's Bazaar and how it works, do the following:

1. Open a Terminal and type:
```

bzr branch lp:pyctactoe

```

That will download the latest trunk of Pyctactoe's main branch.

2. Do your stuff...

3. After you've done some coding, in a Terminal type:
```

bzr commit -m "Some informative log here"

```

That creates a new revision.

4. Then, go to [https://code.launchpad.net/pyctactoe](https://code.launchpad.net/pyctactoe) and register a new branch. Make it be of the "Hosted" type.

5. To upload your local code to your Launchpad branch or update your Launchpad branch type:
```

bzr push (your branch name)

```

Bazaar remembers the last place you've pushed to, so the next time you want to push to the same place, 'bzr push' will be enough.

6. To get the latest changes from some other branch (usually the trunk), use:
```

bzr merge (source branch)
bzr commit -m "Merge from wherever..."

```

The commit command is just good practice; it's nice to know what changes were due a merge and which not. And also, Bazaar remembers the last branch you have merged from, so the next time you merge from the same place, just use 'bzr merge'.

Hope this helps.

---

### Post by LaRoza on 2008-10-28
[http://laroza.19.forumer.com/](http://laroza.19.forumer.com/)

I redid the forum, and now it should be good for discussions on this project, sysres, and bzr/programming in general.

---

### Post by bobbocanfly on 2008-10-28
@Anyone struggling with bzr:

As part of Ubuntu Open Week next week there are two, one hour sessions teaching you how to use bzr from 20:00 UTC in #ubuntu-classroom on Freenode. The first hour (presented by the lovely Emma Jane Hogbin) goes over the basics, while the second hour (my session) goes into some more complicated features of bzr. Highly recommended if you are struggling to grasp bzr.

Meanwhile, back at the point: Is anyone wanting to mess about with the engine/ai so that it works like that code snippet i posted the other day, or should I do it?

---

### Post by fiddler616 on 2008-10-28
> **bobbocanfly said:**
> 
Meanwhile, back at the point: Is anyone wanting to mess about with the engine/ai so that it works like that code snippet i posted the other day, or should I do it?
Well, I think nvteighen is busy with the actual engine, and sheto and I don't know enough to do it, which leaves CptPicard and you.
I've made and AI thread over at [str]LaRoza's[/str], er, the UF Projects forum, so it might be prudent to move discussion over there...Edit: No I haven't--my terminology is weak enough that I don't know if it classifies better as 'Interface' or 'Core'
(Rats, no beancount though :) )

---

### Post by nvteighen on 2008-10-28
> **bobbocanfly said:**
> @Anyone struggling with bzr:

As part of Ubuntu Open Week next week there are two, one hour sessions teaching you how to use bzr from 20:00 UTC in #ubuntu-classroom on Freenode. The first hour (presented by the lovely Emma Jane Hogbin) goes over the basics, while the second hour (my session) goes into some more complicated features of bzr. Highly recommended if you are struggling to grasp bzr.

Meanwhile, back at the point: Is anyone wanting to mess about with the engine/ai so that it works like that code snippet i posted the other day, or should I do it?
Take a look at lp:~evigo/pyctactoe/evigo, but be careful: I still have to update the docstrings and the API doc.

Basically, I moved your changes to a new Tracker class and have created a Player class which has a play() method that connects to the board's update(). It's a Tracker object which decides what Player object is next to execute its play() method.

This design, IMO, gives a great advantage, as we can have the AI class to inherit the Player class and use the same interface for it. The problem is that having a Player class meant to create the Tracker one as, otherwise we'd have an awful circle-definition situation (boards needing players in order to be initialized and players needing a board in order to be initialized...).

I'm sure it can be improved and I'll only merge it to the trunk if people agree on it; it's a radical API change and I just don't want people to be scared or frustrated.

---

### Post by LaRoza on 2008-10-28
> **fiddler616 said:**
> Well, I think nvteighen is busy with the actual engine, and sheto and I don't know enough to do it, which leaves CptPicard and you.
I've made and AI thread over at [str]LaRoza's[/str], er, the UF Projects forum, so it might be prudent to move dis(Rats, no beancount though :) )cussion over there..

When we did work on sysres, we used a single thread for communication for much of the time, which was someone less optimal.

Now we have the forum, and it is much easier (these threads are good for announcements and getting new people involved.) 

Y'all can use #sysres also on irc.freenode.net.

---

### Post by zoke on 2008-10-28
The problem I currently see with the engine is that it is primarily made for boards that are square. Connect Four for example is usually played on a 6*7 board. This requires some re-working of the engine which I'll try to do. 

The other thing is if I were to modify the engine I don't think having a dictionary as the data structure for the board is then ideal. When I attempted to do this in java, I was better off using a 2d-array and using coordinates to transverse the board for wins but looking at the elegance of nvteighen's implementation I don't think it's ideal.

Edit: I just want to say that I want to contribute a connect four interface to the engine. If you think I can do so without making the changes please do say so.

---

### Post by nvteighen on 2008-10-29
> **zoke said:**
> The problem I currently see with the engine is that it is primarily made for boards that are square. Connect Four for example is usually played on a 6*7 board. This requires some re-working of the engine which I'll try to do. 

The other thing is if I were to modify the engine I don't think having a dictionary as the data structure for the board is then ideal. When I attempted to do this in java, I was better off using a 2d-array and using coordinates to transverse the board for wins but looking at the elegance of nvteighen's implementation I don't think it's ideal.

Edit: I just want to say that I want to contribute a connect four interface to the engine. If you think I can do so without making the changes please do say so.
Yeah, the "n x m" board was something I wanted to address... Let's try it!

---

### Post by zoke on 2008-10-29
> **nvteighen said:**
> Yeah, the "n x m" board was something I wanted to address... Let's try it!

I have created a very rough version at my branch at: [https://code.launchpad.net/~zmanji/pyctactoe/dev](https://code.launchpad.net/~zmanji/pyctactoe/dev)

It currently allows the m x n board creation but the checking for diagonal in rectangular boards does not work and will cause an error. I also removed the pyctactoe file because it relied heavily on the dictionary data type for everything to work. I plan to fixing the check method and re creating the pytactoe file soon.

This is my first contribution to a project ever so please be gentle!

---

### Post by sheto on 2008-10-30
I have a branch now thanks to all you lovely people. But I can't seem to update my branch(kshitij-dev). I get something strange like this:
```

kshitij@kshitij-laptop:~$ bzr branch lp:pyctactoe
bzr: ERROR: Target directory "pyctactoe" already exists.

```:(

Anybody have an idea? I checked out Bazaar's official documentation but that did not seem to help.

---

### Post by BackwardsDown on 2008-10-30
You should use "bzr merge" for updating.

---

### Post by sheto on 2008-10-30
BackwardsDown, could you be a little more specific please?

---

### Post by bobbocanfly on 2008-10-30
> **sheto said:**
> BackwardsDown, could you be a little more specific please?


If you have already downloaded the branch, want to update and have made code changes use:

```
bzr merge lp:pyctactoe
```

If you have already downloaded the branch, want to update and have *not* made any code changes run:

```
bzr pull lp:pyctactoe
```

---

### Post by nvteighen on 2008-10-30
> **zoke said:**
> I have created a very rough version at my branch at: [https://code.launchpad.net/~zmanji/pyctactoe/dev](https://code.launchpad.net/~zmanji/pyctactoe/dev)

It currently allows the m x n board creation but the checking for diagonal in rectangular boards does not work and will cause an error. I also removed the pyctactoe file because it relied heavily on the dictionary data type for everything to work. I plan to fixing the check method and re creating the pytactoe file soon.

This is my first contribution to a project ever so please be gentle!
Great, but how did you remove the file? I hope you used 'bzr rm' (otherwise, it will lead to a dissaster).

---

### Post by Majorix on 2008-10-30
I got excited first and bzr'ed the code. But then, after looking a bit around it; I came to remember that I am a lonewolf. I can't "edit" code, I must "write" it myself from the scratch.

I hope you guys learn a few things from this project, have fun :)

---

### Post by zoke on 2008-10-30
> **nvteighen said:**
> Great, but how did you remove the file? I hope you used 'bzr rm' (otherwise, it will lead to a dissaster).

I am 99% sure I used bzr rm.

---

### Post by zoke on 2008-10-30
> **Majorix said:**
> I got excited first and bzr'ed the code. But then, after looking a bit around it; I came to remember that I am a lonewolf. I can't "edit" code, I must "write" it myself from the scratch.

I hope you guys learn a few things from this project, have fun :)

I had this same problem too when I grabbed the source. If you can't edit the code make it a challenge to understand how it works to the smallest detail. Reading other people's code is a very important asset. Maybe after you understand the code, it will be a lot easier to contribute code.

---

### Post by sheto on 2008-10-31
Can I upload my source code without Bazaar?

---

### Post by bobbocanfly on 2008-10-31
Send me a tar.gz (or even better a patch against the latest trunk) of it ( bobbo  [at]  ubuntu [dot] **NOSPAM** com ) and I will upload it to bzr for you?

---

### Post by LaRoza on 2008-10-31
> **sheto said:**
> Can I upload my source code without Bazaar?

"Can you"? Probably.

Why don't you use bzr though?

---

### Post by Taidgh on 2008-10-31
I've been learning python/programming over the past few months, and would love to contribute to a project. I'm not sure where to start, as the A.I. stuff seems too advanced for me. Is there anything left for a newbie to do?
-Taidgh

---

### Post by LaRoza on 2008-10-31
> **Taidgh said:**
> I've been learning python/programming over the past few months, and would love to contribute to a project. I'm not sure where to start, as the A.I. stuff seems too advanced for me. Is there anything left for a newbie to do?
-Taidgh

Oh yes. Every project needs testers and bug reporters.

---

### Post by Canis familiaris on 2008-10-31
Great. I have practically no experience with Python, so maybe I'll not manage to contribute but it would be interesting to see the source.
I will test it anyways.

---

### Post by Taidgh on 2008-10-31
> **LaRoza said:**
> Oh yes. Every project needs testers and bug reporters.
I think I found a bug, but the problem might be on my end. Should I report it anyway? Sorry for the noob questions, I won't bother the thread anymore after this one.
-Taidgh

---

### Post by LaRoza on 2008-10-31
> **Taidgh said:**
> I think I found a bug, but the problem might be on my end. Should I report it anyway? Sorry for the noob questions, I won't bother the thread anymore after this one.
-Taidgh

Sure, you can post it here. Post what happened, and how to replicate it.

---

### Post by artir on 2008-10-31
It's me or the code is far more complicated than it should ?
I'll open a simple-ptt branch  with my code :)

---

### Post by Taidgh on 2008-10-31
Well when I start the game up and leave a blank input, it gives me a NameError. Apparently this should have been resolved by 'InputError' in this:
[PHP]
except ValueError:
    raise InputError(key)

if key not in myboard.slots.keys(): #If number input toobig/small.
    raise InputError(key)[/PHP]
But I get this error message:
[PHP]Traceback (most recent call last):
  File "pyctactoe", line 91, in <module>
    main()
  File "pyctactoe", line 75, in main
    slot = get_input(myboard)
  File "pyctactoe", line 45, in get_input
    raise InputError(key)
NameError: global name 'InputError' is not defined
[/PHP]
Perhaps I am missing a file where the error code is written?
-Taidgh

---

### Post by bobbocanfly on 2008-10-31
> **Taidgh said:**
> Well when I start the game up and leave a blank input, it gives me a NameError. Apparently this should have been resolved by 'InputError' in this:
[PHP]
except ValueError:
    raise InputError(key)

if key not in myboard.slots.keys(): #If number input toobig/small.
    raise InputError(key)[/PHP]
But I get this error message:
[PHP]Traceback (most recent call last):
  File "pyctactoe", line 91, in <module>
    main()
  File "pyctactoe", line 75, in main
    slot = get_input(myboard)
  File "pyctactoe", line 45, in get_input
    raise InputError(key)
NameError: global name 'InputError' is not defined
[/PHP]
Perhaps I am missing a file where the error code is written?
-Taidgh

I could swear I fixed that bug in my first commit to this project. You sure you have the latest bzr trunk?

---

### Post by Taidgh on 2008-10-31
No, I can't get Bazaar to install, so I used the source off of the site. That's probably my problem.
-Taidgh

---

### Post by nvteighen on 2008-10-31
> **zoke said:**
> I am 99% sure I used bzr rm.

Perfect!

> **sheto said:**
> Can I upload my source code without Bazaar?

Yeah... but it will harden things a bit.

> **Taidgh said:**
> I've been learning python/programming over the past few months, and would love to contribute to a project. I'm not sure where to start, as the A.I. stuff seems too advanced for me. Is there anything left for a newbie to do?
-Taidgh

Yes, for example. Reviewing the engine, proposing ideas, catching bugs, test, whatever you believe can be useful.

> **bobbocanfly said:**
> I could swear I fixed that bug in my first commit to this project. You sure you have the latest bzr trunk?

It was also merged upstream. What I did was to change the bug report status back to "Fix commited". I guess we should only change bug reports to "Fix released" when actually releasing a version.

> **Taidgh said:**
> No, I can't get Bazaar to install, so I used the source off of the site. That's probably my problem.
-Taidgh

From what branch did you get the code? There are several branches that have old code... Look at the "Last modified" info at each branch to get an idea. Anyway, the code targeted for the next release will always be placed at the trunk, so if you want to contribute directly for release, you better use that one.

Also, from where are you trying to install Bazaar. There's the 'bzr' package at the repos!

---

### Post by nvteighen on 2008-10-31
**Very important review request**: Please, developers, comment on this proposal of mine to modify the PTTEngine's API. [https://code.launchpad.net/~evigo/pyctactoe/evigo/+merge/1480](https://code.launchpad.net/~evigo/pyctactoe/evigo/+merge/1480)

---

### Post by nvteighen on 2008-11-04
Bobbo, I've been violating GPL for some time, but now I'm complying...

(I added you at the copyright notices for the trunk branch... well, the Tracker class code is yours... ;))

---

### Post by bobbocanfly on 2008-11-04
> **nvteighen said:**
> Bobbo, I've been violating GPL for some time, but now I'm complying...

(I added you at the copyright notices for the trunk branch... well, the Tracker class code is yours... ;))

Hehe 'tis all good. I have pushed some code into my branch that changes the way the Engine handles checking whether someone has won etc. The new architecture relies on each "game" (tictactoe, connect4 etc.) having its own class specifying its check() function (implements the game rules). The board stores this as self.game_instance and calls self.game_instance.check() when it needs to check if someone has won.

The code is a little rough (and undocumented) but it is going to make having game-specific rules (things like maximum number of players) much easier to implement because they can just be added to the games rules class.


[https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev/+merge/1535](https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev/+merge/1535)
[https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev](https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev)

---

### Post by nvteighen on 2008-11-04
> **bobbocanfly said:**
> Hehe 'tis all good. I have pushed some code into my branch that changes the way the Engine handles checking whether someone has won etc. The new architecture relies on each "game" (tictactoe, connect4 etc.) having its own class specifying its check() function (implements the game rules). The board stores this as self.game_instance and calls self.game_instance.check() when it needs to check if someone has won.

The code is a little rough (and undocumented) but it is going to make having game-specific rules (things like maximum number of players) much easier to implement because they can just be added to the games rules class.


[https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev/+merge/1535](https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev/+merge/1535)
[https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev](https://code.edge.launchpad.net/~bobbo/pyctactoe/bobbo-dev)
Great to see movement.

I'll "officially" review the code on Tuesday to give people a chance to place their opinions (and because I'm a bit busy right now). Also, to give you enough time to document... I just don't like putting undocumented API changes into trunk.

---

### Post by bobbocanfly on 2008-11-06
OK, thanks for your feedback on my code! I've changed it around to address your concerns. There is now a simple function that interfaces the game class "repository" and loads the module into the Board class (you just have to pass it the name of the module, which will be easy to do on the frontend). I have also created a base game type class and implemented a tictactoe class (basically just the old check() code from the Engine). Another review would be appreciated!

---

### Post by nvteighen on 2008-11-06
> **bobbocanfly said:**
> OK, thanks for your feedback on my code! I've changed it around to address your concerns. There is now a simple function that interfaces the game class "repository" and loads the module into the Board class (you just have to pass it the name of the module, which will be easy to do on the frontend). I have also created a base game type class and implemented a tictactoe class (basically just the old check() code from the Engine). Another review would be appreciated!
I've merged it (Launchpad is a bit slow on updating branch info, but if you look at the trunk's source code you'll see it's correctly merged)... If nobody else commits Engine code after this being set and tested, we'll step into "Engine Freeze".

I hope to have this milestone done in less than two months. Milestone 0.0.2 will probably be the AI... Then alpha, beta, rc1 and release version 0.0! (a weird numbering scheme, but we're geeks and start counting from zero)

---

### Post by bobbocanfly on 2008-11-06
> **nvteighen said:**
> I've merged it (Launchpad is a bit slow on updating branch info, but if you look at the trunk's source code you'll see it's correctly merged)... If nobody else commits Engine code after this being set and tested, we'll step into "Engine Freeze".

I hope to have this milestone done in less than two months. Milestone 0.0.2 will probably be the AI... Then alpha, beta, rc1 and release version 0.0! (a weird numbering scheme, but we're geeks and start counting from zero)

I can only think of a few changes to the Engine that I still want to make (moving the AI class into the game class (Tic tac toe AI wont be of much use to a game of conect 4), maybe extending the base game class a bit) but that wont take too long. Other than that, I cant think of anything else I would want to change.

---

### Post by nvteighen on 2008-11-16
Ok, some stuff is happening and I'd like to have input on this.

bobbocanfly cleverly introduced a plugin architecture for PycTacToe... But, the main module is still to text-interface Tic-Tac-Toe centric, so it was nearly impossible to sanely develop plugins for PycTacToe and make them work without manipulating the whole source code.

Well, now this is possible... (or nearly possible as Tic-Tac-Toe is hardcoded to start as default).

I've proposed my changes for merging into trunk. Again, I don't want to break anyone's work. [https://code.launchpad.net/~evigo/pyctactoe/evigo/+merge/1734](https://code.launchpad.net/~evigo/pyctactoe/evigo/+merge/1734)

Thanks! And everyone's invited to participate!

---

### Post by tiachopvutru on 2008-11-18
What's the level of experience required to participate in this project (beside testing and bug-catching)?

... being able to read the code?

---

### Post by nvteighen on 2008-11-18
> **tiachopvutru said:**
> What's the level of experience required to participate in this project (beside testing and bug-catching)?

... being able to read the code?
The code is a bunch of files long, but the code itself (maybe except the function that checks the Tic-Tac-Toe board for wins) is not complex (not plainly easy, though) and any mid-beginner (someone who knows Std. Python well) should be able to read it.

Of course, it'll be difficult to understand it first as it's not your own code, but in little time you get used to it.

What is growing more complex is the program's architecture, how modules relate to eachother. The idea, basically is that there's a pttengine.py module which gives you an API for Tic-Tac-Toe like games, then the modules at games/ are the games' rules and pyctactoe is the main module that calls and controls flow. My merge proposal is aimed to make the design more coherent and move control flow to be game-specific (I'm the maintainer and could just push changes directly to the trunk, but well...).

The current trunk: [https://code.launchpad.net/~evigo/pyctactoe/trunk](https://code.launchpad.net/~evigo/pyctactoe/trunk)
My branch: [https://code.launchpad.net/~evigo/pyctactoe/dev](https://code.launchpad.net/~evigo/pyctactoe/dev)

---

### Post by bobbocanfly on 2008-11-20
Hi nvteighen, dont worry I haven't disappeared. I am a little worried at the current plugin architecutre (calling an executable main() for a game). So far I cant see how interfaces are going to work (without each game class repeating a whole bunch of UI code, that can probably be modularised). DId you have any thoughts on this?

---

### Post by nvteighen on 2008-11-21
> **bobbocanfly said:**
> Hi nvteighen, dont worry I haven't disappeared. I am a little worried at the current plugin architecutre (calling an executable main() for a game). So far I cant see how interfaces are going to work (without each game class repeating a whole bunch of UI code, that can probably be modularised). DId you have any thoughts on this?
Don't worry!

Hmm... The issue could lie on several implementations for similar/the same games (e.g. Tic-Tac-Toe on Tkinter and GTK+), but if we include Connect Four, the interface will change significantly (e.g. you have "gravity": pieces are piled one over the other). That's the reason behind my changes... Thoughts?

---

### Post by bobbocanfly on 2008-11-22
> **nvteighen said:**
> Don't worry!

Hmm... The issue could lie on several implementations for similar/the same games (e.g. Tic-Tac-Toe on Tkinter and GTK+), but if we include Connect Four, the interface will change significantly (e.g. you have "gravity": pieces are piled one over the other). That's the reason behind my changes... Thoughts?

OK, makes sense to me. If we write some reusable base classes for getting most of the frontend going, it should be fine.

---

### Post by nvteighen on 2008-11-22
> **bobbocanfly said:**
> OK, makes sense to me. If we write some reusable base classes for getting most of the frontend going, it should be fine.

You say, like a specialized "widgets" library that is optional and used just for convenience?

---

### Post by bobbocanfly on 2008-11-22
> **nvteighen said:**
> You say, like a specialized "widgets" library that is optional and used just for convenience?

Yeah that would make sense. Anything that we thing will be reused in multiple games we could put into a "widgets" class. For example a text based grid can be used for tic tac toe and connect4. It wouldnt make much sense for us to have to write out a grid system twice, when we could make a reusable "widget". Time to write a spec perhaps?

---

### Post by nvteighen on 2008-11-23
Perfect. I 100% agree with you.

But, let's keep this organized. Currently, we have to finish [Milestone 1 specs]("https://launchpad.net/pyctactoe/+milestone/0.1m1") (we've got 1/3 marked as implemented). 

Milestone 2 is also there but hidden... I put some ideas on its whiteboard (AI + Debian package), but I'm not sure whether they are a good plan, so ignore them. Maybe it could be a good idea to drop the Debianizing and replace it for this. A Connect Four could also be a good idea for Milestone 2 as an example (and also a test of PTTEngine's power)...

After Milestone 2, possibly we could go to Alpha (if an Alpha is necessary at all... but I doubt it), Beta and finally release. GUI and such IMO should be planned for further releases... Release 0.1 should be really simple, though providing the mechanisms for further development.

Anyway, feel free to write a blueprint; any idea on how to schedule stuff is welcome (actually, needed! :p)

---

### Post by nvteighen on 2008-11-29
Ok, we're almost at finishing PycTacToe 0.1 Milestone 1... the last thing needed is to review Tic-Tac-Toe's text interface and tweak it. I'll be working on this next week, but anybody feel free to propose changes.

---

### Post by bobbocanfly on 2008-11-29
I am working on some widgets for the games. I have been looking at writing GTK widgets in Python and it doesnt look like it would be too hard to make a grid widget for GTK. 

The widgets stuff has required some changes to the directory structure (need to add a setup.py for distribution/packaging, which needed the pttengine stuff to be in its own subdir) and some minor changes to the engine. I dont want to ask for a merge at the moment (not tested it enough or documented it), but it would be handy if you had a look and gave some comments?

---

### Post by nvteighen on 2008-11-29
> **bobbocanfly said:**
> I am working on some widgets for the games. I have been looking at writing GTK widgets in Python and it doesnt look like it would be too hard to make a grid widget for GTK. 

The widgets stuff has required some changes to the directory structure (need to add a setup.py for distribution/packaging, which needed the pttengine stuff to be in its own subdir) and some minor changes to the engine. I dont want to ask for a merge at the moment (not tested it enough or documented it), but it would be handy if you had a look and gave some comments?
Of course, I will look at it closer during next week (Latin Exam on Monday :(), but I really like the idea. Possibly this won't get into 0.1 but, as far as I've seen, we could import the TextGrid to the Tic-Tac-Toe plugin.

What I don't like too much is to see games/ inside pttengine/. Is there any way to have games/ again at toplevel?

The rest seems fine.

---

### Post by bobbocanfly on 2008-11-29
> **nvteighen said:**
> What I don't like too much is to see games/ inside pttengine/. Is there any way to have games/ again at toplevel?

We could, and have the game modules installed to /usr/share/pyctactoe or /usr/share/pttengine, but it would make importing them more difficult and less likely to Just Work. Ah well, we have a while until 0.2, so we can work something out!

---

### Post by nvteighen on 2008-11-30
> **bobbocanfly said:**
> We could, and have the game modules installed to /usr/share/pyctactoe or /usr/share/pttengine, but it would make importing them more difficult and less likely to Just Work. Ah well, we have a while until 0.2, so we can work something out!
Hmm... deployment will be bit difficult... At least for 0.1, we should have a Debian pakage working. Anyway, I'm planning to release snapshots for each milestone (à la Supertux). 0.1m1 will have to be a plain .tar.gz archive, but hopefully we can get a .deb as soon as possible; I'm trying to learn how to package one and it's a bit tough...

---

### Post by bobbocanfly on 2008-11-30
> **nvteighen said:**
> Hmm... deployment will be bit difficult... At least for 0.1, we should have a Debian pakage working. Anyway, I'm planning to release snapshots for each milestone (à la Supertux). 0.1m1 will have to be a plain .tar.gz archive, but hopefully we can get a .deb as soon as possible; I'm trying to learn how to package one and it's a bit tough...

Hehe, I am an Ubuntu packager, so I could do the debs if you would like?

Also, we will need the setup.py for packaging it up, which requires the new directory structure.

---

### Post by nvteighen on 2008-11-30
> **bobbocanfly said:**
> Hehe, I am an Ubuntu packager, so I could do the debs if you would like?

Also, we will need the setup.py for packaging it up, which requires the new directory structure.
Great! :)

---

### Post by bobbocanfly on 2008-12-01
Right, I have been busy with this project for the last couple of days. I have a basic grid class that can load data, then a TextGrid class that can show it in text form at pretty much BETA stage and integrated with the basic pyctactoe game. I have also been working on a GTK port, which has meant writing an entire game grid widget from scratch (using Cairo), which is at an alpha stage right now. I am now working on integrating GTKGrid with a GTK version of the game (using the same rules as the text version, maybe it would make sense to have a base tictactoe class with shared data that tictactoe-text and tictactoe-gtk both inherit?). 

Anyone wants a look its at [https://code.edge.launchpad.net/~bobbo/pyctactoe/ui-widgets](https://code.edge.launchpad.net/~bobbo/pyctactoe/ui-widgets) (WARNING: currently very dodgy, but (kind of) functional. Not too much documentation, except some comments from me getting pissed off at cairo).

---

### Post by nvteighen on 2008-12-02
Hmm... so you say we could have the TextGrid into 0.1? That way we could improve the text interface and move on to Milestone 2...

If not, I've been looking at the ncurses... I had a little experience on it in C and I guess I can transfer that knowledge into Python for the basic tic-tac-toe.

---

### Post by bobbocanfly on 2008-12-02
> **nvteighen said:**
> Hmm... so you say we could have the TextGrid into 0.1? That way we could improve the text interface and move on to Milestone 2...

If not, I've been looking at the ncurses... I had a little experience on it in C and I guess I can transfer that knowledge into Python for the basic tic-tac-toe.

If we put TextGrid into the tictactoe game file, we can have it (quite cleanly and with few bugs) in milestone 1. I wouldnt recommend grabbing anything straight out of my branch right at the moment as it is pretty experimental. TextGrid on the other hand is fairly stable (it isnt very complex at all) so I think it should be safe to have it in 0.1m1. I am wanting to get TextGrid and GTKGrid into milestone 2 (if possible), so I'll keep working on that. A curses one would be great.

---

### Post by nvteighen on 2008-12-03
ok, I'll try writing the curses one for Milestone 1. Hopefully I'll be soon pushing changes into my branch.

---

### Post by bobbocanfly on 2008-12-04
Out of sheer boredom I have written a python3.0 patch against current trunk. Porting to python 3.0 when the time is right or making the current codebase future proof wont take much work (2to3 tool will probably take care of it anyway).

[http://bobbo.me.uk/pyctactoe-python3.patch](http://bobbo.me.uk/pyctactoe-python3.patch)

---

### Post by nvteighen on 2008-12-05
Hmm... When running the patched code I get a syntax error:
```

Traceback (most recent call last):
  File "./pyctactoe", line 42, in <module>
    main()
  File "./pyctactoe", line 34, in main
    factory = pttengine.GameFactory(game)    
  File "/home/ugi/prog/pyctactoe/trunk/pttengine.py", line 193, in __init__
    exec("from %s import %s" % (game_type, module_name))
  File "<string>", line 1, in <module>
  File "/home/ugi/prog/pyctactoe/trunk/games/tictactoe.py", line 50
    print(output, end=" ")
                     ^
SyntaxError: invalid syntax

```

I'm on Python 2.5.2 @ Debian Lenny.

---

### Post by fluteflute on 2008-12-06
> **nvteighen said:**
> Hmm... When running the patched code I get a syntax error:
```

Traceback (most recent call last):
  File "./pyctactoe", line 42, in <module>
    main()
  File "./pyctactoe", line 34, in main
    factory = pttengine.GameFactory(game)    
  File "/home/ugi/prog/pyctactoe/trunk/pttengine.py", line 193, in __init__
    exec("from %s import %s" % (game_type, module_name))
  File "<string>", line 1, in <module>
  File "/home/ugi/prog/pyctactoe/trunk/games/tictactoe.py", line 50
    print(output, end=" ")
                     ^
SyntaxError: invalid syntax

```

I'm on Python 2.5.2 @ Debian Lenny.
The patch is for Python 3. :)

---

### Post by nvteighen on 2008-12-06
> **fluteflute said:**
> The patch is for Python 3. :)
:p

---

### Post by nvteighen on 2008-12-14
Colors! :D (thanks to ncurses "magic")

I have pushed some fancy-colored play now to my personal branch at PycTacToe. Also proposed a merge into trunk. Take a look at: [https://code.launchpad.net/~evigo/pyctactoe/evigo/+merge/2328](https://code.launchpad.net/~evigo/pyctactoe/evigo/+merge/2328)

---

### Post by scourge on 2008-12-14
PycTacToe should support Gomoku with custom board sizes. Then coding an AI would actually make sense and be interesting. Tic-tac-toe can be solved heuristically, which isn't much of a challenge.

---

### Post by nvteighen on 2008-12-14
> **scourge said:**
> PycTacToe should support Gomoku with custom board sizes. Then coding an AI would actually make sense and be interesting. Tic-tac-toe can be solved heuristically, which isn't much of a challenge.
PycTacToe is a plugin-based system, so if you know how to do this, you're invited to participate!

It's true that for 0.1 milestone 1 we'll only have the classic Tic-Tac-Toe, but this is just because of order. 0.1 milestone 2 goals aren't actually defined, so a Gomoku could be possible...

---

