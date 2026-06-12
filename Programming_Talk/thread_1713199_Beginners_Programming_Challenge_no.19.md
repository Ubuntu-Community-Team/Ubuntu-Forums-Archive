---
title: "Beginners Programming Challenge no.19"
date: 2011-03-23
forum: Programming Talk
---

### Post by red_Marvin on 2011-03-23
[SIZE="6"]Beginners Programming Challenge no.19[/SIZE]
Since I won the 18th challenge I have tried to come up with the next one,
hoping it will be challenging without being insurmountable:

[SIZE="5"]Crossword creator helper[/SIZE]
[SIZE="4"]Description[/SIZE]
Creating crosswords (crossword example in post 3) is a difficult task, and a program to help out can speed up the process. It is your task to write the program following the specifications:

The program will read data from a file with the following format:

[LIST]
[*]One line with one number denoting the width in cells of the crossword
[*]One line with one number denoting the height in cells of the crossword
[*]Multiple lines containing X,Y,D,W where
[list]
[*]X and Y are numbers signifying the position where the 'question cell' responsible for the word is placed (0,0 is the upper left corner)
[*]D is the direction of the word--signified by one letter, either h (horizontal) or v (vertical)
[*]W is a word (containing only lowercaze a-z)
[/list]
[/LIST]
So the input 0,0,h,foobar means that #foobar is placed in the upper left corner of the crossword, where # is the little question box hinting at the word foobar.

[size="4"]Constraints[/size]
[list]
[*]A cell may contain a single letter or a '#' signifying that it is used by a question box, or be unused '.'
[*]A question cell (#) may be overlapped by another question cell (eg for a word in a different direction)
[*]The resulting crossword should be printed
[*]Upon discovering an impossible word placement the input parsing should stop and the crossword so far should be printed. The impossible word cells should be marked with '$' and the word and position should be printed. (see example 2)
[*]If the placement coordinate of the word is outside the crossword this should be printed (see example 3) but no dollar signs are needed,
[*]If the placement coordinate is inside the crossword, but the word would stick out, this should be printed, but the parts inside should be marked with $ (see example 4)
[/list]

[size="4"]Example Input/Output[/size]
[size="3"]1) Valid[/size]
Input:
```

8
6
1,2,h,car
3,0,v,bar
4,1,v,rose
2,3,h,robot
1,2,v,dog

```
Output:
```

...#....
...b#...
.#car...
.d#robot
.o..s...
.g..e...

```

[size="3"]2) Invalid word[/size]
Input:
```

8
6
1,2,h,car
3,0,v,bar
4,1,v,rose
2,3,h,fruit
1,2,v,dog

```
Output:
```

...#....
...b#...
.#car...
.#$ro$$.
....s...
....e...
Horizontal word 'fruit' can not start from cell 3,2 (letter mismatch)

```
[size="3"]3) Invalid word placement[/size]
Input:
```

8
6
1,2,h,car
3,0,v,bar
4,100,v,rose
2,3,h,fruit
1,2,v,dog

```
Output:
```

...#....
...b....
.#car...
...r....
........
........
Vertical word 'rose' can not start from cell 4,100 (out of bounds)

```

[size="3"]4) Invalid word size[/size]
Input:
```

8
6
1,2,h,car
3,0,v,bar
4,1,v,rosebud
2,3,h,robot
1,2,v,dog

```
Output:
```

...#....
...b#...
.#car...
...r$...
....$...
....$...
Vertical word 'rosebud' can not start from 4,1 (size mismatch)

```

[SIZE="5"]Judgement criteria[/SIZE]
The judgement criteria pretty standard, the program has to work,
code should be readable, it has to be your code, etc. etc...

Entries accepted until and including 2011-04-24

Best of luck.

---

### Post by schauerlich on 2011-03-23
Just a thought - the type of crosswords they do in sweden is different from what's common in most other places. Most American and British people are used to having the clues numbered and appear off the board. I was a bit confused by this until I did some [wikipedia research](http://en.wikipedia.org/wiki/Crossword#Types_of_grid).

---

### Post by red_Marvin on 2011-03-23
I see, well we have these numbered ones here in Sweden too, but the one linked below is the most common.

To clarify, the kind of crossword I think of is a simplified version of
the one shown here [http://en.wikipedia.org/wiki/File:Schwedenr%C3%A4tsel.jpg](http://en.wikipedia.org/wiki/File:Schwedenr%C3%A4tsel.jpg) and here [http://www.ordkultur.se/happydivers/2010/04/12/happydivers-intar-svds-korsord/](http://www.ordkultur.se/happydivers/2010/04/12/happydivers-intar-svds-korsord/)
(ignore the arrows, in the contest version here, goes straightly east or south from the clue box)

Not analyzing too hard, I think you can think of the numbered kind too but i.e. one where all words begin with a #.

---

### Post by schauerlich on 2011-03-23
> **red_Marvin said:**
> Not analyzing too hard, I think you can think of the numbered kind too but i.e. one where all words begin with a #.

Alright... does that mean this is a typo?

```
 012345
0...#....
1...b#...
2.#car...
3.d#robot
4.o..s...
 .g..e...
```

"bar" appears to start at (3, 0) and "robot" is at (2, 3) instead of (3, 2). Also, are words allowed to span off the edge of the board? You specified the dimensions as 6x5, but are allowing words to go out to 8x6.

---

### Post by red_Marvin on 2011-03-23
You are correct, they are errors.
Only words fitting inside the predefined rectangle are allowed.
I will update original post.

...updated, new rules and examples added.

---

### Post by schauerlich on 2011-03-25
The error reporting isn't quite the same, but I believe it works.

[php]import copy
import sys

class PlacementError(Exception):
    pass


# from http://code.activestate.com/recipes/410687-transposing-a-list-of-lists-with-different-lengths/
def transposed(lists):
    if not lists:
        return []
    return map(lambda *row: list(row), *lists)


class Board(object):
    def __init__(self, x, y):
        self.blank = "."
        self.board = [[self.blank for i in range(x)] for j in range(y)]


    def place(self, x, y, direction, word):
        if x >= len(self.board[0]) or y >= len(self.board):
            raise PlacementError("Cannot place '%s' at (%d, %d) - out of bounds" % (word, x, y))

        word = "#" + word
        if direction == "h":
            self.board = self._place_horizontal(x, y, word)
        elif direction == "v":
            self.board = self._place_vertical(x, y, word)
        else:
            raise ValueError("direction is not 'h' or 'v'")


    def _place_horizontal(self, x, y, word, board=None):
        if board is None:
            board = copy.deepcopy(self.board)
       
        edge = x + len(word)

        if edge > len(board[0]):
            raise PlacementError("word goes off board: '%s'" % (word))
        
        for i in range(x, edge):
            try:
                if board[y][i] == self.blank:
                    board[y][i] = word[i - x]
                elif board[y][i] == word[i - x]:
                    pass
                else:
                    raise PlacementError("something's in the way ('%s', y=%d, i=%d)" % (word, y, i))
            except IndexError:
                raise PlacementError("off the edge ('%s', y=%d, i=%d)" % (word, y, i))
        
        return board


    def _place_vertical(self, x, y, word):
        return transposed(self._place_horizontal(y, x, word, transposed(self.board)))


    def __repr__(self):
        return "\n".join("".join(self.board[j][i] for i in range(len(self.board[0])))  for j in range(len(self.board)))


if __name__ == "__main__":
    inf = open(sys.argv[1], "r")

    lines = inf.readlines()

    board = Board(int(lines[0]), int(lines[1]))

    for line in lines[2:]:
        args = map(lambda x: x.strip(), line.split(","))
        args = [int(args[0]), int(args[1])] + args[2:]

        try:
            board.place(*args)
        except PlacementError as e:
            print board
            print e
            sys.exit(1)

    print board
[/php]

---

### Post by simeon87 on 2011-03-25
Fortunately you're already giving the word placements. Composing a crossword given a word list and a grid is an NP-complete problem so I wouldn't wanna try that as a beginner :)

---

### Post by schauerlich on 2011-03-25
> **simeon87 said:**
> Fortunately you're already giving the word placements. Composing a crossword given a word list and a grid is an NP-complete problem so I wouldn't wanna try that as a beginner :)

Not too hard if you've got a nondeterministic Turing machine laying around. :)

---

### Post by krazyd on 2011-03-27
> **simeon87 said:**
> Fortunately you're already giving the word placements. Composing a crossword given a word list and a grid is an NP-complete problem so I wouldn't wanna try that as a beginner :)

I thought the same thing when I saw the title of the challenge!

---

### Post by schauerlich on 2011-04-23
Well, looks like I've got some stiff competition.

---

### Post by red_Marvin on 2011-04-24
Indeed, I'm halfway through a forth implementation 'just because', but I won't finish it on time, if at all, and it would be outside the competition anyway.

Five hours and thirtyseven minutes left of the competition people!

It would be good to know if the abundance of competitors are caused by lack of time, or if the challenge was too hard. "Beginner" can mean a lot of things.

---

### Post by red_Marvin on 2011-04-24
As the time for submissions are now over, I can now declare **schauerlich** to be the winner of this contest.

Congratulations, and hoping that your no.20 Challenge to be will attract more participants. :popcorn:

---

### Post by schauerlich on 2011-04-24
> **red_Marvin said:**
> As the time for submissions are now over, I can now declare **schauerlich** to be the winner of this contest.

Congratulations, and hoping that your no.20 Challenge to be will attract more participants. :popcorn:

Woot! Victory by default!

I should have the next challenge up in a day or two, once I think of it. :)

---

