---
title: "Python list of my custom class- strange behaviour"
date: 2011-03-16
forum: Programming Talk
---

### Post by TheMinister on 2011-03-16
Hi all, first time posting here,

I'm playing around with python (relatively new to programming but not completely) and trying to make a sudoku solver.

I'm creating a custom class Square to represent each little cell- it has a value (0-9, with 0 representing an empty square) as well as 9 boolean values to show which numbers it could possibly be- for negative elimination.

Anyway, I use list of lists (called sudoku below) to give the 9x9 sudoku grid (ie sudoku[0][8] is top left), making each slot in the second list an instance of my class Square.

This is generated with the code:

```
class Square:
    #one number type for defining the value of the square (digit can be 1-9, 0 will be null value)
    squareValue = 0
    #and then 10 bool types for representing what values it may or may not be. NB these are actually integers, but whatever. Same difference.
    canbe1 = 1
    canbe2 = 1
    canbe3 = 1
    canbe4 = 1
    canbe5 = 1
    canbe6 = 1
    canbe7 = 1
    canbe8 = 1
    canbe9 = 1
```

And the actual grid sudoku itself:

```
sudoku = [[Square for i in range(9)] for j in range(9)]
```

The strange behaviour I'm having is when I attempt to modify one of the squares, it does it to all of them. I'm fairly certain this is not me being incompetent and changing them all with a poorly written loop (I have checked pretty thoroughly).

Anyway code used to modify a single square:

```
sudoku[i][j].squareValue = int(foo)
```

What the hell is going on? Have I created just one instance of Square with every bit in the grid sudoku just being a pointer back to it? Or something else?

I'm running Pydev on eclipse 3.6.2, this is python 3.1.

Full code here- it's not finished, and the error is occuring in the function getSudoku. Unless I'm wildly wrong and it's in the printSudoku function- but I've checked the f*** out of it, and cannot understand where it is going wrong.

Cheers for any help or pointers- sorry if it's a retarded question, and yes I have had a google for answers.

And before you suggest it, yes I know I should be using Tkinter or curses for the user interface, but as the code says, I'm too lazy.

```
'''
Created on 16 Mar 2011

@author: tom
'''

class Square:
    #one number type for defining the value of the square (digit can be 1-9, 0 will be null value)
    squareValue = 0
    #and then 10 bool types for representing what values it may or may not be. NB these are actually integers, but whatever. Same difference.
    canbe1 = 1
    canbe2 = 1
    canbe3 = 1
    canbe4 = 1
    canbe5 = 1
    canbe6 = 1
    canbe7 = 1
    canbe8 = 1
    canbe9 = 1

def is_number(s):
    try:
        int(s)
        return True
    except ValueError:
        return False

#A function to print the existing sudoku
def printSudoku(sudoku):

    for j in range(8,-1,-1):
        for i in range(0,9):
            print ('',sudoku[i][j].squareValue,end=' ')
            #print('',i,j,end=' ')    
            if (i==2) or (i==5):
                print (end='|')
        
        print()
                           
        if (j==3) or (j==6):
            print ('-----------------------------')
            
#A function to get the initial sudoku from the user
def getSudoku(sudoku):
    print('Hi there. I heard you wanted me to solve some **** for you.')
    print('Because Tom is a lazy ****, we are going to go through position by position - that\'s row by row, starting in the top left.')
    print('If the cell is blank, enter 0')
    
    for j in range(8,-1,-1):
        for i in range(0,9):
            foo = input ('Gimme a number:')
            if (is_number(foo)==1):
                sudoku[i][j].squareValue = int(foo)
                print ('Set postition ',i,' ',j,'to ',foo)
                printSudoku(sudoku)
            else:
                print('That is not how sudoku works retardface.')


    
#Here's the main grid definition. Should be pretty damn sexy
sudoku = [[Square for i in range(9)] for j in range(9)]

print('Program start')


printSudoku(sudoku)


getSudoku(sudoku)

printSudoku(sudoku)

print('Program end')


```

---

### Post by johnl on 2011-03-16
In python, variables declared at class scope like you have done are roughly equivalent to 'static' class variables in C++ -- they are shared between all instances. 

Try changing your square code to this:

```

class Square:
    def __init__(self):
        self.squareValue = 0

        self.canbe1 = 1
        self.canbe2 = 1
        self.canbe3 = 1
        self.canbe4 = 1
        self.canbe5 = 1
        self.canbe6 = 1
        self.canbe7 = 1
        self.canbe8 = 1
        self.canbe9 = 1

```

or something more succinct like:

```

class Square:
    def __init__(self):
        self.squareValue = 0

        # e.g, x = self.canbe[4]
        self.canbe = [False, True, True, True, True,
                      True, True, True, True, True] 
        # or even 
        # self.canbe = [False] + [True] * 9

```

Hope this helps.

---

### Post by andrew1992 on 2011-03-16
I didn't read through your all your code, so I don't know entirely if this is causing your problem, but in your class definition all of your "canbex" variables are class variables - that is, each instance won't have their own copies of these variables. That means when one instance knocks out a possibility (sets one of the "canbes" to 0), it does so for all instances.

EDIT: Beaten to it :)

---

### Post by TheMinister on 2011-03-16
Aha, thanks ever so much guys. For a minute there I was worried that I'd gotten the nature of reality completely confused.

And cheers for the idea to list the booleans like that- now realise that will make life much easier when it comes to the logiccy bit.

---

