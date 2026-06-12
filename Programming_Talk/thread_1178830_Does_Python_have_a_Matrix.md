---
title: "Does Python have a Matrix"
date: 2009-06-04
forum: Programming Talk
---

### Post by M4rotku on 2009-06-04
Hello all,

I'm currently trying to program the game Battleship in Python.  I've done it in C++ before and I mainly just want to do it in Python for learning purposes.  In C++, I used a matrix for the board.  As one can imagine, this made displaying the board really easy.  A simple for statement nested in another for statement could display the whole thing with nice, neat rows and columns.  I'm wondering if there is a matrix module for Python and how I would go about using it.  Basically, I want my board to look like the following.

> [ ][ ][ ][ ][ ][ ][ ][ ]
[ ][O][ ][ ][X][ ][ ][ ]

and so on to form an 8 x 8 grid with the ' ' character representing a spot which has yet to be fired on, the 'O' character representing a miss, and the 'X' character representing a hit.

Any advice is greatly appreciated.

Much thanks,
M4rotku

---

### Post by crdlb on 2009-06-04
There should be a matrix type in numpy, but that's probably not really applicable for this. The two easy solutions that come to my mind are a list of lists:
```
board = [[''] * 8 for i in xrange(8)]
board[0][0] = 'X' 
```
or a dictionary with tuple keys:
```
board = {}
for x in xrange(8):
    for y in xrange(8):
        board[x,y] = ''
board[0,0] = 'X' 
```

The first approach is probably vastly superior overall, but I like the nicer coordinate indexing of the dictionary approach. It would be easy to make an object using the first approach internally and the tuple indexing externally, though.

---

### Post by M4rotku on 2009-06-04
I had considered using a matrix, I might just use it after all.  Thanks for your input. :D

---

### Post by The Cog on 2009-06-05
I think that dict of tuples should be:
```
board = {}
for x in xrange(8):
    for y in xrange(8):
        board[(x,y)] = ''
board[(0,0)] = 'X'
```

---

### Post by Habbit on 2009-06-05
I don't understand... why are you offering the OP solutions based on lists and dictionaries? I think what the post really asks for is the address of the big black guy giving out red and blue pills :popcorn:

---

### Post by delfick on 2009-06-05
> **The Cog said:**
> I think that dict of tuples should be:
```
board = {}
for x in xrange(8):
    for y in xrange(8):
        board[(x,y)] = ''
board[(0,0)] = 'X'
```

The tuples don't have to be enclosed in brackets, it still works without them :)

---

### Post by ssam on 2009-06-05
for a fast compact matrix/array look at the numpy package. however for this case you don't really need it.

---

### Post by The Cog on 2009-06-05
> **delfick said:**
> The tuples don't have to be enclosed in brackets, it still works without them :)

Whoa! You're right of course, and now I think about it I can see why. It just looks wrong to me. It looks too much like a C 2d array to be right in python. Mind you, that's what the OP is looking for anyway.

---

### Post by delfick on 2009-06-05
> **The Cog said:**
> Whoa! You're right of course, and now I think about it I can see why. It just looks wrong to me. It looks too much like a C 2d array to be right in python. Mind you, that's what the OP is looking for anyway.

:)

However, a C 2d array would look more like matrix[0][8] (i.e. like the tuple solution)

also, we can make the tuple solution look like the dict solution :)

[PHP]
class Matrix(object):
    def __init__(self, rows, cols):
        self.data = [[''] * cols for i in xrange(rows)]
    
    def __getitem__(self, key):
        #You'd have a try..catch statement here to ensure this doesn't break the program :p
        x, y = key
        return self.data[x][y]

    def __setitem__(self, key, value):
        #You'd have a try..catch statement here to ensure this doesn't break the program :p
        x, y = key
        self.data[x][y] = value
        
    def __str__(self):
        return '\n'.join([' '.join('[ %-2s]' % value for value in row) for row in self.data])
        
        
if __name__ == '__main__':
    board = Matrix(8, 8)
    board[4, 5] = 'X'
    board[3, 7] = 'o'
    print board
        [/PHP]

---

### Post by M4rotku on 2009-06-05
Lol, I found the solution by using the dictionaries.  But this thread has turned into something rather interesting.  ):P

---

### Post by crdlb on 2009-06-06
> **delfick said:**
> 
However, a C 2d array would look more like matrix[0][8] (i.e. like the tuple solution)

also, we can make the tuple solution look like the dict solution :)


That's pretty much exactly what I had in mind, though there's definitely no reason to use any try: blocks; just let the exception bubble up.

Also, I think you meant "the list solution", not "the tuple solution". The only tuples used are in the dict approach (or in the hybrid you posted).

---

### Post by delfick on 2009-06-06
> **crdlb said:**
> That's pretty much exactly what I had in mind, though there's definitely no reason to use any try: blocks; just let the exception bubble up.

valid observation, however, it depends on what you want to happen when a bad key is given.

> Also, I think you meant "the list solution", not "the tuple solution". The only tuples used are in the dict approach (or in the hybrid you posted).

true, my bad :p

---

### Post by The Cog on 2009-06-06
I really like the dict solution. It allows for many-dimentional data, and should be very efficient for sparse arrays, where most "locations" contain null.

---

