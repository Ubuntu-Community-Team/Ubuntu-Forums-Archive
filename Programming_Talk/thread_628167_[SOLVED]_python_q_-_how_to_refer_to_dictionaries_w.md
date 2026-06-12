---
title: "[SOLVED] python q - how to refer to dictionaries when they are in lists?"
date: 2007-11-30
forum: Programming Talk
---

### Post by NovaAesa on 2007-11-30
In Python, how do you refer to dictionaries if they are within a list?

For example, the data structure that I have constructed is a two dimensional list, with each dimension having 9 members. In each of these 81 members, I have identical dictionaries each with a keys "1", "2", "3"... through to "9". Each value to each key is boolean.

My question is, how do you go about referring to the values?

An example of what I have done is this:
script[3][2]["4"] = False

but what it seems to be doing is in every one of the 81 dictionaries setting the value corresponding to the key "4" to False.

If anyone could help me figure out the correct ways to assign values in dictionaries when the dictionaries themselves are in lists, that would be great!

---

### Post by Dancingwllamas on 2007-12-01
Sounds like a sudoku solver. :)

I was not able to replicate your problem with a smaller example:
```

>>> list=[[{1:True,2:False}, {1:True,2:False}], [{1:True,2:False}, {1:True,2:False}]]
>>> list[0][0]
{1: True, 2: False}
>>> list[0][0][1]=False
>>> list[0][0]
{1: False, 2: False}
>>> list[1][0]
{1: True, 2: False}
>>> list[0][1]
{1: True, 2: False}
```

Maybe you could post some more code?

---

### Post by NovaAesa on 2007-12-01
:) yes it's for a Sudoku solver. I made one about a year ago in Visual Basic and wanted to impliment the algorithms I designed in Python as a learning exercise (I only started learning Python a few days ago).

Anyway, here's the module that I'm having problems with:
The bit I'm having troubles with is in the function _script_erase

[PHP]class Sudoku: 
    """

    Entire grid: coord numbers at the sides and region numbers in the squares.             

        012 345 678                      
        ___ ___ ___                  
     0 |   |   |   |     
     1 | 0 | 1 | 2 |         
     2 |___|___|___|                     
     3 |   |   |   | 
     4 | 3 | 4 | 5 |                     
     5 |___|___|___|         
     6 |   |   |   |         
     7 | 6 | 7 | 8 |                   
     8 |___|___|___|                   
        

    """

    def __init__(self):

        #initialises the script array
        #script: 2 dimensional list of dictionaries each with a sinle length
        #key and a boolean value. True indicates the square *could* have a
        #value equal to the key, and false indicates that it cannot.
        self.script = []
        new = {"1":True, "2":True, "3":True, "4":True, "5":True, \
               "6":True, "7":True, "8":True, "9":True}
        for n in range(9):
            self.script.append([])
            for i in range(9):
                self.script[n].append(new)

        #initialises the answer array
        #answer: 2 dimensional list of strings of length 1. If a string is
        #present, this indicates a final answer. None indicates no answer has
        #been found as of yet.
        self.answer = []
        for n in range(9):
            self.answer.append([])
            for i in range(9):
                self.answer[n].append(None)

    def _sequ(self, x, y):
        """converts the x, y coordinate into a sequencial number from 0 to 80"""
        return x + 9*y
        
    def _coord(self, sequence_num):
        """converts the sequence number into a tuple of coords (x, y)"""
        x = sequence_num % 9
        y = sequence_num // 9
        return (x, y)

    def _region(self, seq_num):
        """returns the region number based on on sequence_num"""
        return (self._coord(seq_num)[0] // 3) + \
               3 * (self._coord(seq_num)[1] // 3)
               
    def _n_region(self, r, n):
        """returns the sequence number of a square based on the square's
        position (n) in a region (r)"""
        return n%3 + 3*(r%3) + 9*(n//3) + 27*(r//3)
        
    def _script_erase(self, x, y): #NEEDS TESTING!
        """deduces which scripts can be set to false depending the vales in
        the script list and the answer array and sets the accordingly"""
        if self.answer[x][y] != None:
            script_to_erase = str(self.answer[x][y])
            r = self._region(self._sequ(x, y))
            for n in range(9):
                #erases scripts in the row        
                self.script[n][y][script_to_erase] = False
                #erases scripts in the column
                self.script[x][n][script_to_erase] = False                
                #erases scripts in the region
                new_x = self._coord(self._n_region(r, n))[0]
                new_y = self._coord(self._n_region(r, n))[1]
                self.script[new_x][new_y][script_to_erase] = False
                #erases all scripts in the square
                self.script[x][y][str(n + 1)] = False
    
    def _only_in_column(self, x):
        """solves squares in the sudoku by seeing if there only one of a
        certain script in the column given by x"""
        pass
        
    def _only_in_row(self, y):
        """solves squares in the sudoku by seeing if there only one of a
        certain script in the row given by y"""
        pass
        
    def _only_in_region(self, r):
        """solves squares in the sudoku by seeing if there only one of a
        certain script in the region given by r"""
        pass
        
    def _only_in_square(self, sequ_num):
        """solves squares in the sudoku by seeing if there only one of a
        certain script in the square given by sequ_num"""
        pass
        
    def _unsolved(self):
        """returns the number of squares that are unsolved i.e.
        the number of times 'none' occurs in the answer list"""
        pass
        
    def _print_answer(self):
        """THIS IS FOR TESTING"""
        output_string = ""
        for n in range(9):
            for i in range(9):
                if self.answer[i][n] == None:
                    output_string += "0"
                else:
                    output_string += self.answer[i][n]
                output_string += " "
            output_string += "\n"
        print output_string
    
    def _print_script(self):
        """THIS IS FOR TESING"""
        output_string = ""
        for y in range(9):
            for x in range(9):
                for k in range(9):            
                    if self.script[x][y][str(k+1)] == True:
                        output_string += "1"
                    else:
                        output_string += "0"
                output_string += "\n"
            output_string += "\n"
        print output_string

    def return_solution(self):
        none

    def submit_givens(self, givens):
        none

[/PHP]

---

### Post by Dancingwllamas on 2007-12-01
Ah, I found your problem.

In your init, you initialize your array by appending with a variable. To aid in efficiency, python is appending the exact same object to each cell in the array. When you change the object in one cell, you are changing it in all the cells because all the cells contain the exact same object.

Check this by printing script[0][0].values and script[0][1].values
Notice that they have the same memory address.

To fix this, just append the contents of your "new" variable instead of using the variable. ie: 

```
self.script[n].append({"1":True, "2":True, "3":True, "4":True, "5":True, "6":True, "7":True, "8":True, "9":True} )
```

---

### Post by slavik on 2007-12-01
so it appends the reference of new instead of a new.copy() (in Java terms).

---

### Post by NovaAesa on 2007-12-01
Thankyou, its working now!

I just have two short questions about this though:

I know that lists and dictionaries are objects, and was wondering about variable names used to refer to the objects. Does it work similar to the way things work in Java? i.e. the variable name doesn't contain the object itself but rather points to a location in memory where the object is located. Is this right, or way off?

Also, is how I have set up the array the best way of doing it (most efficient, smallest amount of code)? I seems kind of arduous to go through loops like I have, so I was wondering if there was an easier way.

Thank you.

---

### Post by smartbei on 2007-12-01
In python, all types are objects (Everything Is An Object) - but only lists and dictionaries are passed by reference. This means:
```

lis = [1,2,3,4]
lis2 = lis
lis2[3] = 8
print lis[3] # -> 8

```
The way around this is in the copy module. For a shallow object copy (normal lists of strings, integers and tuples) use copy.copy. If you have a list of lists you should use copy.deepcopy.

BTW - To me it seems simpler for the structure to have a list for every cell instead of a dictionary. Then you would use lis[Row][Column][Value-1] = True. Seems simpler to me - YMMV.

---

### Post by NovaAesa on 2007-12-01
Having everything as an objects makes sense, and now that you say that, I do remember reading that somewhere.

And after reading the docs for the copy module, using the copy module seems like another alternative I could use. 

The reason that I have used a dictionary for each cell is probably from the way that I think about Sudokus when I solve them myself. I don't think of the numbers that are put in as numbers as such, but rather as 'symbols'. So strings seemed more appropriate rather than integer indexes. Hence the use of dictionaries. It may sound odd, but that's just the way I think of it when I am solving them myself.

---

### Post by pmasiar on 2007-12-01
instead of list of list, you can have a dictionary, which key is a tupple:

sudoku = {}
sudoku[1,2,3] = x

Looks nicer :-)

---

### Post by NovaAesa on 2007-12-02
> **pmasiar said:**
> instead of list of list, you can have a dictionary, which key is a tupple:

sudoku = {}
sudoku[1,2,3] = x

Looks nicer :-)

Ah yes, that would work as well. Just curious though, what is the standard way that most programmers use multidimensional arrays in Python? Are they lists within lists, or dictionaries with tuples as the keys, or does it change from programmer to programmer?

---

### Post by pmasiar on 2007-12-02
It depends on applications, of course, but dictionaries are used all over Python for system purposes (objects, namespaces etc are dictionaries), so they are implemented in a very efficient way. Thre is no reason to avoid using them, if it makes code simpler (like in your case). Also, it would be trivial to add one or more dimensions to a dictionary if needed.

---

### Post by NovaAesa on 2007-12-03
Okay, I think I will change my programme to use dictionaries then, seeings that they are efficient. I somehow got into my mind that they were terribley inefficient compared to lists because they are a more complex data structure.

I also read that its much better to have code as readable as possible, so it's lucky you guys could help me with this before my class got too long and involved much code rewriting. Lesson leaned though - make sure to plan things before jumping in front of a code editor. :)

---

