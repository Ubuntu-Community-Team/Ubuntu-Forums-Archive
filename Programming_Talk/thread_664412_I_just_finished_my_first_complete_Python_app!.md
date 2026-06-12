---
title: "I just finished my first complete Python app!"
date: 2008-01-11
forum: Programming Talk
---

### Post by NovaAesa on 2008-01-11
Okay, I've been working on this for a few days now, and it's finally done. It's a game where you play Tic Tac Toe, also known as Naughts and Crosses in some countries.

It's written in Python and I've released it under the GPL so anyone can modify etc etc if they want to.

Constructive criticism is welcome, if you see any thing that I have done that is in any way un-pythonic please tell me. Also, could you mention whether you found the instructions within the app easy to understand?

So to run the programme, just change directories to the file, and type: (but I'm sure you all knew that :P)

```
python tic_tac_toe.py
```

---

### Post by b0rka7a on 2008-01-11
Hehe :D You can't beat the computer :lolflag:

---

### Post by NovaAesa on 2008-01-11
I know :P It's an unbeatable algorithm. I didn't tell my brother that for a while (he tested it) and he got really frustrated at it!

---

### Post by Kadrus on 2008-01-11
Nice..I really suck at the game though:p..lol.

---

### Post by Majorix on 2008-01-11
Why don't you paste your code on a pastebin so that we can see it without downloading?

---

### Post by Kadrus on 2008-01-11
Here's the code..it's the same thing.. created by **NovaAesa**
[php]
#!/usr/bin/python

import random

class TicTacToe(object):
    """A TicTacTow class
    """
    
    MID  = ((1, 1),)  #middle square
    SIDE = ((0, 1), (1, 0), (1, 2), (2, 1))  #side squares
    CORN = ((0, 0), (0, 2), (2, 0), (2, 2))  #corner squares
    
    def __init__(self, comp_first, comp_chr='X', player_chr='O'):
        """Starts up the class
        Parameters: comp_first - Decides who goes first, True for the computer
                                 or False for the player.
                    comp_chr   - The symbol used for the computer. Should be a
                                 single length string.
                    player_chr - The symbol used for the player. Should be a
                                 single length string.
        """
        self._grid = {}  #keys: 2-tuple coords, values: comp_chr or player_chr
        self._computer = comp_chr
        self._player = player_chr
        self._branch = ""  #the branch that that is being played
                           #(corner='a', edge='b', center='c')
        self._last_move = 0  #The last move played by the computer. Values are
                             #0, 1, 2, 3, and 5
        self._comp_first = comp_first  #Records who went first. True is
                                       #computer went first, False is player
                                       #went first.
        
    def get_first_move(self):
        """Returns: The playing field grid with the computer's first move.
        This method should only be called if the object was created with
        comp_first=True, and then only once at the start"""
        if self._last_move == 0 and self._comp_first:
            first_move = self._comp_move()[0]
            self._last_computer_move = first_move
            self._grid[first_move] = self._computer
            return self._grid
        else:
            print "RAISE ERROR"
        
    def submit(self, move):
        """Submits a move.
        
        Returns: A tuple containing the _grid dictionary (including the
        computer's new move) and a string value indicating a win-tie situation.
        Values for the string are 'win', and 'tie' (there is no lose value
        since the computer never loses :P).
        """
        self._grid[move] = self._player
        self._last_player_move = move
        if self._comp_first:  #computer went first
            new_move, win_tie_value = self._comp_move()
            self._last_computer_move = new_move
            self._grid[new_move] = self._computer
        else:  #player went first
            if self._last_move == 4:
                #On the last move, the computer shouldn't generate a response
                #If the player is able to make a last move, it will always be
                #a tie, because the computer cannot lose.
                win_tie_value = "tie"
            else:
                new_move, win_tie_value = self._player_move()
                self._last_computer_move = new_move
                self._grid[new_move] = self._computer
        return (self._grid, win_tie_value)
        
    def _win(self):
        """Checks to see if the computer can win on the next turn.
        Returns: The coordinates in a tuple if the win can take place.
        Otherwise, None is returned.
        """
        pass
    
    def _two_line(self, win_or_block):
        """Checks to see if the computer should block or take a win. This
        happens if there is two of the same piece in a line and the other
        spot in the line is blank.
        
        Parameters: win_or_block - Decides if the algorithm looks for a
                                   possible win or a block that needs to take
                                   place. 'win' and 'block' are the only
                                   possible values.
        
        Returns: The coordinates in a tuple if the block should take place or
        the win can take place. Otherwise, None is returned.
        """
        seq = [(((0,0),(1,0),(2,0)), ((0,1),(1,1),(2,1)), ((0,2),(1,2),(2,2))), 
               (((0,0),(0,1),(0,2)), ((1,0),(1,1),(1,2)), ((2,0),(2,1),(2,2))),
               (((0,2),(1,1),(2,0)), ((0,0),(1,1),(2,2)))] #line 1 - rows
                                                           #line 2 - column
        for line_type in seq:                              #line 3 - diagonals
            for member in line_type:
                piece_counter = 0  #counts the pieces in the row/column/diag
                empty_counter = 0  #counts the empty places
                for x, y in member:
                    if (x, y) not in self._grid.keys():
                        empty_counter += 1
                        return_x = x
                        return_y = y
                    else:
                        if win_or_block == 'win':
                            if self._grid[x, y] == self._computer:
                                piece_counter += 1
                        elif win_or_block == 'block':
                            if self._grid[x, y] == self._player:
                                piece_counter += 1
                    if piece_counter == 2 and empty_counter == 1:
                        return (return_x, return_y)

        return None  #returns None if no blocks have been found
        
    def _comp_move(self):
        """Returns the best move for the computer to make next if the compter
        went first initially.
        The moves are done according to the logic tree. In the tree X is the
        computer and O is the player.
                                      |
        1                         X-corner
                 _____________________|__________________________ 
                |                     |                          |
            O-corner               O-edge                    O-center   
                |                     |                          |
        2   X-corner(a)           X-center(b)            X-caddy_corner(c)
                |                     |                   _______|________ 
                |                     |                  |                |
             O-block               O-block           O-corner          O-edge   
                |                _____|_____             |                |
                |               |           |            |            ....|....
        3   X-corner      X-block     X-corner       X-corner         .X-block.
                                      not_bordered                    .........
        """
        
        status = None  #default value for status
        #first checks if there are any winning moves
        if self._two_line("win") != None:
            square = self._two_line("win")
            status = "win"
        else:
        
            #this is the first move
            if self._last_move == 0:
                square = self._rnd_corner()
                self._last_move = 1
                
            #this is the second move
            elif self._last_move == 1:
                if self._last_player_move in self.CORN:
                    self._branch = 'a'
                    square = self._rnd_corner()
                elif self._last_player_move in self.SIDE:
                    self._branch = 'b'
                    square, = self.MID
                elif self._last_player_move in self.MID:
                    self._branch = 'c'
                    x, y = self._last_computer_move
                    square = (2 - x, 2 - y)  
                self._last_move = 2
            
            #this is the third move      
            elif self._last_move == 2:  
                if self._branch == 'a':
                    square = self._rnd_corner()
                elif self._branch == 'b':
                    if self._two_line("block") != None:
                        square = self._two_line("block")    
                    else:
                        possible_corners = []
                        for corner in self.CORN:
                            if corner not in self._grid.keys():
                                possible_corners.append(corner)
                        for x, y in possible_corners: 
                            if (x, 1) not in self._grid.keys() and \
                               (1, y) not in self._grid.keys():
                                square = x, y
                elif self._branch == 'c':
                    if self._last_player_move in self.CORN:
                        square = self._rnd_corner()
                    elif self._last_player_move in self.SIDE:
                        square = self._two_line("block") 
                self._last_move = 3
            
            #This is move 4 & 5. It is only executed in response to a c-branch
            else:                                                        #draw
                square = self._two_line("block")
                if self._last_move == 4:
                    status = "tie"
                self._last_move += 1
            
        return (square, status)
        
    def _player_move(self):
        """Returns the best move for the computer to make next if the player
        went first initially.
        The moves are done according to the logic tree. In the tree X is the
        computer and O is the player. Dotted lines indicates repition after
        the first run through.
        
                 __________________________|_______
                |(a)                               |(b)
            O-center                          O-not_center
                |                                  |
    1       X-corner                            X-center
                |                 _________________|__________________      
       .........|........        |                 |                  |
       .   O-any-move   . O-1edge,1corner     O-both-edge       O-both-corner
       .    ____|___    .     ___|____          ___|____          ____|___
       .   |        |   .    |        |        |        |        |        |
       .   |        |   .    |        |  both-edges  one-edge    |        |
       .   |        |   .    |        |brder-corner  brder-corner|        |
       .   |        |   .    |(ba)    |(bb)    |(bc)    |(bd)    |(be)    |(bf)
    2  .X-block X-corner. X-block  X-caddy X-cornered X-edge  X-block  X-edge
       ..................    |     corner    square     |        |        |
                         ....|... ....|...  ...|....    |     ...|.... ...|....
                         .block/. .block/.  .block/. O-block  .block/. .block/.
                         .random. .random.  .random.    |     .random. .random.
                         ........ ........  ........    |     ........ ........
    3                                             X-corner-next
                                                    to-X-edge
        """
        status = None  #default value of status is None
        #first checks if there are any winning moves
        if self._two_line("win") != None:
            square = self._two_line("win")
            status = "win"
        else:
            
            #this is the first move
            if self._last_move == 0:
                if self._last_player_move in self.MID:
                    square = self._rnd_corner()
                    self._branch = 'a'
                else:
                    square, = self.MID
                    self._branch = 'b'
                self._last_move = 1
                    
            #this is the second move
            elif self._last_move == 1:
                if self._branch == 'a':
                    if self._two_line("block") != None:
                        square = self._two_line("block")
                    else:
                        square = self._rnd_corner()
                elif self._branch == 'b':
                    side_count = 0
                    corner_count = 0
                    for x, y in self._grid.keys():
                        if self._grid[x, y] == self._player:
                            if (x, y) in self.SIDE:
                                side_count += 1
                            elif (x, y) in self.CORN:
                                corner_count += 1
                    if side_count == 1 and corner_count == 1:
                        if self._two_line("block") != None:
                            square = self._two_line("block")
                            self._branch = "ba"
                        else:
                            for x, y in self.CORN:
                                if (x, y) in self._grid.keys():
                                    if self._grid[x, y] == self._player:
                                        square = (2 - x, 2 - y)
                                        self._branch = "bb"
                    elif side_count == 2:
                        side_pieces = []
                        for x, y in self.SIDE:
                            if (x, y) in self._grid.keys():
                                side_pieces.append((x, y))
                        x1, y1 = side_pieces[0]
                        x2, y2 = side_pieces[1]
                        if abs(x1 - x2) == 1:
                            if x1 != 1:
                                new_x = x1
                            else:
                                new_x = x2
                            if y1 != 1:
                                new_y = y1
                            else:
                                new_y = y2
                            square = (new_x, new_y)
                            self._branch = "bc"
                        else:
                            square = self._rnd_side()
                            self._branch = "bd"
                    elif corner_count == 2:
                        if self._two_line("block") != None:
                            square = self._two_line("block")
                            self._branch = "be"
                        else:
                            square = self._rnd_side()
                            self._branch = "bf"
                self._last_move = 2
                                
            #this is the third move
            elif self._last_move == 2:
                #branch 'a'
                if self._branch == 'a':
                    if self._two_line("block") != None:
                        square = self._two_line("block")
                    else:
                        square = self._rnd_corner()
                #all other branches
                elif self._branch in ("ba", "bb", "bc", "be", "bf"):
                    if self._two_line("block") != None:
                        square = self._two_line("block")
                    else:
                        square = self._rnd_square()
                #branch "bd"
                elif self._branch == "bd":
                    possible = []
                    last_x, last_y = self._last_computer_move
                    for x, y in self.CORN:
                        if x == last_x or y == last_y:
                            possible.append((x, y))
                    square = random.choice(possible)
                self._last_move = 3
                
            #this is the fourth move
            elif self._last_move == 3:
                if self._two_line("block") != None:
                    square = self._two_line("block")
                else:
                    square = self._rnd_square()
                self._last_move = 4        
                
        return (square, status)
        
    def _rnd_side(self):
        """Returns: a tuple containing the coordinates to a random side edge
        that has yet to be taken.
        """
        while True:
            x, y = random.choice(self.SIDE)
            if (x, y) not in self._grid.keys(): break
        return (x, y)
  
    def _rnd_corner(self):
        """Returns: a tuple containing the coordinates to a random corner
        that has yet to be taken.
        """
        while True:
            x, y = random.choice(self.CORN)
            if (x, y) not in self._grid.keys(): break
        return (x, y)
        
    def _rnd_square(self):
        """Returns: a tuple containing the coordinates to a random square
        that has yet to be taken.
        """
        possible = []
        for x in range(3):
            for y in range(3):
                if (x, y) not in self._grid.keys():
                    possible.append((x, y))
        return random.choice(possible)
        
def string_grid(grid):
    """Creates a string version of a 3x3 Tic Tac Toe grid.
    
    Parameters: grid - the grid that is to be created
    
    Returns: a string representation of grid.
    """
    output_string = "\n"
    for y in range(3):
        for x in range(3):
            if (x, y) in grid.keys():
                output_string += grid[x, y] + " "
            else:
                output_string += '- '
        output_string += '\n'
    return output_string
    
def get_input(tictactoe_obj):
    """Gets input from the user about which position they wish to put their
    piece. Entered corespond with the following positions: 7 8 9
                                                           4 5 6
    tictactoe_obj is the current game being played.        1 2 3

    Returns: A tuple containing the coordinates of the piece.
    """
    
    while True:
    
        #Gets a set of coordinates
        while True:
            valid_num = False
            user_input = raw_input("Please enter a number between 1 and 9:\n")
            if user_input in ('1', '2', '3', '4', '5', '6', '7', '8', '9'):
                valid_num = True
                x = (int(user_input) - 1) % 3
                y = 2 - (int(user_input) - 1) // 3
                coord = (x, y)
            else:
                print "Invalid answer"
            if valid_num: break
        
        #makes sure the coordinates aren't already taken
        if coord not in tictactoe_obj._grid.keys():
            taken = False
        else:
            taken = True
            print "That place is already taken"
            
        if not taken: break

    return coord
        
if __name__ == '__main__':

    #initialises score counters (there is no player_wins because
    computer_wins = 0  #the player cannot win)
    ties = 0
    
    #prints instructions
    print "****************************************"
    print "*                                      *"
    print "*         Tic Tac Toe 1.0.0            *"
    print "*                                      *"
    print "****************************************"
    print "                                        "
    print "Tic Tac Toe is released under the       "
    print "GPL (c) 2008 Peter Stace.               "
    print "                                        "
    print "Instructions:                           "
    print "When entering a place to put a piece,   "
    print "use the number pad to enter a number    "
    print "between 1 and 9. The position on the    "
    print "number on the number pad coresponds to  "
    print "the square as follows:                  "
    print "                                        "
    print "         7 | 8 | 9                      "
    print "        ---+---+---                     "
    print "         4 | 5 | 6                      "
    print "        ---+---+---                     "
    print "         1 | 2 | 3                      "
    print "                                        "
    print "The computer is X and the player is O   "
    print "                                        "
    

    computer_first = False
    while True:
        computer_first = not computer_first
        
        #says who will go first
        current_game = TicTacToe(computer_first)
        if computer_first:
            print "\nComputer goes first"
            print string_grid(current_game.get_first_move())
        else:
            print "\nPlayer goes first"
        
        #plays the game    
        while True:
            grid, status = current_game.submit(get_input(current_game))
            print string_grid(grid)
            if status != None:
                if status == "win":
                    print "The computer has won\n"
                    computer_wins += 1
                elif status == "tie":
                    print "You have tied against the computer\n"
                    ties += 1
                print """Score:\n\nComputer: %s\nPlayer: 0\nTies: %s\n""" \
                                                        % (computer_wins, ties)
            if status != None: break
            
        #finds out if the player wants to play again
        while True:
            answer = raw_input("Would you like to play again? y/n ")
            if answer not in ('y', 'n'):
                print "Please answer y or n"
                valid_answer = False
            else:
                valid_answer = True
            if valid_answer == True: break
        if answer == 'n': break
[/php]

---

### Post by Mr.popo on 2008-01-11
I tied.

---

### Post by Kadrus on 2008-01-11
> **Mr.popo said:**
> I tied.
So did I..twice :p..

---

### Post by NovaAesa on 2008-01-13
So does anyone have any constructive criticism? I'm sure I must have done something wrong.

---

### Post by Jessehk on 2008-01-13
You could try writing a dynamic tree (and use something like a minimax algorithm) instead of hardcoding the possibilities in.

I had fun doing just that in C++. :)

---

### Post by NovaAesa on 2008-01-14
> **Jessehk said:**
> You could try writing a dynamic tree (and use something like a minimax algorithm) instead of hardcoding the possibilities in.

I had fun doing just that in C++. :)
I'll do some reasearch into this and see if it will be a viable solution to tic tac toe. From (very) preliminary research, it sounds like using that kind of algorithm would make the entire programme easier to understand.

---

### Post by NovaAesa on 2008-01-14
oops, double post

---

### Post by Mathiasdm on 2008-01-14
Or if you want to make it really complicated without reason, you could create a neural network and train it to solve the Tic Tac Toe game :-D

---

### Post by NovaAesa on 2008-01-14
> **Mathiasdm said:**
> Or if you want to make it really complicated without reason, you could create a neural network and train it to solve the Tic Tac Toe game :-D
Maybe I'll give something like that a try once I've finished my Batchellor of Software Engineering degree (I'm starting in 3 weeks xD). At the moment, even the dynamic tree idea seems a bit advanced for me, but I'm going to give it a go anyway!

---

### Post by CptPicard on 2008-01-14
Actually neural networks are going to suck for tictactoe; they are pretty good for fuzzy pattern matching and function approximation, but not really great for building this sort of an intense state evaluation function which needs to be exact too. Compare to Go or chess...

A minimax-pruning game tree search is the way to go. You wouldn't be explicitly building any game trees of course; it's all implicitly in the recursion. And you wouldn't want to be using a NN as the state evaluator because it's slow and non-exact (it would be an interesting academic exercise of course)... simply give a greater score for states where you have longer ready segments already on the board, that should direct the search well enough.

---

### Post by Wybiral on 2008-01-14
> **CptPicard said:**
> Actually neural networks are going to suck for tictactoe; they are pretty good for fuzzy pattern matching and function approximation, but not really great for building this sort of an intense state evaluation function which needs to be exact too. Compare to Go or chess...

A minimax-pruning game tree search is the way to go. You wouldn't be explicitly building any game trees of course; it's all implicitly in the recursion. And you wouldn't want to be using a NN as the state evaluator because it's slow and non-exact (it would be an interesting academic exercise of course)... simply give a greater score for states where you have longer ready segments already on the board, that should direct the search well enough.

I was thinking the same thing. Not only would it be really difficult to properly train (without simply feeding it every situation, of course) for a situation like this, it would be grossly inefficient compared to conventional methods.

---

### Post by NovaAesa on 2008-01-14
I'm all up for acedemic excersises. At this stage I can't imporve the programme from a user's point appart from adding a GUI because it already does what it's meant to - plays a mean game of tic tac toe.

So yeah, I'll give the minmax algorithm a go, and maybe for something to mess around with later I'll try making a NN just for the heck of it.

---

### Post by CptPicard on 2008-01-14
> **Wybiral said:**
> Not only would it be really difficult to properly train (without simply feeding it every situation, of course) 

If I *had to* train a NN for tictactoe, I would follow Tesauro's lead who wrote a strong backgammon program using

[http://en.wikipedia.org/wiki/Temporal_difference_learning](http://en.wikipedia.org/wiki/Temporal_difference_learning) .

Just make it play a lot of games and then "push back" the values discovered for the model states at various time steps, and correcting for the error.

I wrote my Bachelor's thesis on this years ago... man that was tough for an undergrad. Got to admit I really "got it" a long time after actually turning the thesis in for marks :)

@Aesa, to be more exact, you want to be using "alpha-beta" search for your minimax algorithm.

---

### Post by Mathiasdm on 2008-01-15
> **CptPicard said:**
> Actually neural networks are going to suck for tictactoe; they are pretty good for fuzzy pattern matching and function approximation, but not really great for building this sort of an intense state evaluation function which needs to be exact too. Compare to Go or chess...

A minimax-pruning game tree search is the way to go. You wouldn't be explicitly building any game trees of course; it's all implicitly in the recursion. And you wouldn't want to be using a NN as the state evaluator because it's slow and non-exact **(it would be an interesting academic exercise of course)**... simply give a greater score for states where you have longer ready segments already on the board, that should direct the search well enough.
I know it would suck, especially for something like Tic-Tac-Toe, but I figured the idea would be interesting :)
Maybe I should have mentioned that :oops:

---

### Post by NovaAesa on 2008-01-15
Okay, so I've decided to work on the minimax algorithm. However I've run into a bit of a problem. I want to assign a variable to have a value of negative or positive infinity. I know I could just assign a really big number (say 1000), but I think it would be better (from an instrinsic documentation point of view) if it was infinity. Does anyone know of a way of doing this in python?

---

### Post by RIchard James13 on 2008-01-16
> **NovaAesa said:**
> Okay, so I've decided to work on the minimax algorithm. However I've run into a bit of a problem. I want to assign a variable to have a value of negative or positive infinity. I know I could just assign a really big number (say 1000), but I think it would be better (from an instrinsic documentation point of view) if it was infinity. Does anyone know of a way of doing this in python?

Define the number in a string. That way you can have "+infinity" and "-infinity" and "21". When you need to do any math on the value check for the infinity first and if it is just a normal number convert it from a string to a number.

I had to do that for a program last semester but I don't remember the language. The problem was I had to store the result of x/0 which is Not A Number, so I just used a string for that case and converted to a number for all other cases.

---

### Post by NovaAesa on 2008-01-27
After examining the logic of the algorithm a bit more, I realised that it doesn't really need to be infinity or negative infinity. Rather, it just needs to be a number greater than 1 or less than -1. I just decided to go with 1000 and -1000 made sure to use lots of remarks to document the code.

Thanks for the idea though Rlchard James13

---

### Post by sheto on 2008-10-28
I won!

---

### Post by NovaAesa on 2008-10-28
Sure sure. :P There's not even code in there to register a win because it can't happen :P

---

### Post by wmcbrine on 2008-10-28
I once wrote what I thought was an unbeatable Tic Tac Toe program (this was in Sinclair BASIC), so I didn't put in code to deal with a player win. Then I discovered I was wrong, and it could indeed be beaten. :)

---

