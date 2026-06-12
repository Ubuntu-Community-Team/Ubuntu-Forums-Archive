---
title: "Learning Ruby: Am after step 2 ideas"
date: 2009-02-14
forum: Programming Talk
---

### Post by timClicks on 2009-02-14
Hi all,

I am at that awkward stage of learning to program where the basic tutorials seem easy and the quizzes seem to require lots of knowledge about the language. Can anyone recommend a project, ideally a series of projects that could build me up?

I am attracted to Ruby because of its readable syntax. I plan to learn lower-level languages once flow control and conditionals become second nature.

Thanks for your suggestions,

-Tim

---

### Post by nvteighen on 2009-02-14
Well, try something you're interested in... Is there some (somewhat simple) program you need?

An idea: a simple, text-based Tic-Tac-Toe. It's not that simple as you think, but it's not difficult. The trick is, as almost in all cases, in creating proper data structures/classes, something you have to learn only by practice.

Another idea, from a past challenge we had here, may be to create a program that takes a file like this:
```

0,9
1,9
3,8
0,3

```

Each number is a node in a tree and the pairs tell you what nodes are connected with each. The root node is the smallest number in the file. The goal is to print the tree correctly to screen from any file of that format. Again, think on the data structures. (I wrote this in Python in just 121 lines... In C, well, I needed a lot more... :p)

---

### Post by jimi_hendrix on 2009-02-14
@nvteighen

whats with you and tic tac toe games? :)

you could also try my snowball game (requires knowledge of OOP):

two players, one you control one computer one (controlled by an AI as complex as you want (it can be random numbers for all i care))

on your turn you can 1) make a snowball 2) throw it 3) move closer 4) move farther back

AI can do the same, for the AI i advise using inheritence and polymorphism

---

### Post by ajackson on 2009-02-14
> **jimi_hendrix said:**
> whats with you and tic tac toe games? :)
Because you have to start with that before moving on to Global Thermonuclear War*****?

Probably more because it is a simple to implement game that allows programmers to learn Python with an actual project in mind rather than simple example chunks of code.

***** see [http://www.imdb.com/title/tt0086567/](http://www.imdb.com/title/tt0086567/)

---

### Post by nvteighen on 2009-02-14
> **jimi_hendrix said:**
> @nvteighen

whats with you and tic tac toe games? :)

Because I want the OP to leave Ruby and join my Python project, which is a secret plan to rule the world!! :twisted:

No, seriously: it's because Tic-Tac-Toe is a good starting project as it needs you to design good classes and because the game rules are very simple. I wasn't thinking on PycTacToe (maybe my subconscious did): as you know which is not only a Tic-Tac-Toe game, but an attempt to have a framework for similar games... as you know.

> 
you could also try my snowball game (requires knowledge of OOP):

two players, one you control one computer one (controlled by an AI as complex as you want (it can be random numbers for all i care))

on your turn you can 1) make a snowball 2) throw it 3) move closer 4) move farther back

Also a great suggestion. +1

> AI can do the same, for the AI i advise using inheritence and polymorphism

Sincerely... what does polymorphism has to do with this?

---

### Post by jimi_hendrix on 2009-02-14
> **nvteighen said:**
> 
Sincerely... what does polymorphism has to do with this?

i ment for the computer controlled player, just inherit the player class and ad an AI method...

---

### Post by nvteighen on 2009-02-14
> **jimi_hendrix said:**
> i ment for the computer controlled player, just inherit the player class and ad an AI method...
Hm. I see what you mean... Well, it depends on the design whether you need that or not.

---

### Post by timClicks on 2009-02-14
Thanks all for your posts, and the discussion! As I've discovered by lurking on a few open source project mailing lists - there's many ways to achieve a single result. This discussion brings that out.

Without looking into too much detail, the playing field is most naturally represented as a nested hashes (associative arrays/dictionaries).

[FONT="Courier New"]
"key" => "value"
"position" => "1|0" # where 1 == x, 0 == O
[/FONT]

So far, I've sketched up a bit of a framework for a Naughts and Crosses app:

```

# Pseudo-esque code. 


class SetUp
# configures the game
    player_name
    select_naughts_or_crosses
    number_of_human_players

class Render
# methods might include:
    draw_field
    plot_cross(num, alpha)
    plot_naught(num, alpha)
    draw_sucess_line
    print_winning_sequence
    print_losing_sequence

class Turn
# Receive input from the player. Passes input to:
    print_prompt
    gets
    convert_input 
      #regexp to interpret result, then feed to render and AI

class TurnProcessing
# This class assesses what to do, and whether a new turn is required
    can_parse?
     # tests whether input was correctly entered, e.g. "1a" and 
    valid_move?
     # tests whether the move was within the field of play, and whether
     # the space is aleady occupied
    is_win?

class Data
# holds information on the field of play, and feeds this information
# to the other classes.

class ComputerPlayer
# 'Decision making' class. Am slightly at a loss about how to achieve
# this, without being formulaic. 
    

```

Will let you know how I get on. I can sense that getting all of the information between the classes will take some thought.

---

