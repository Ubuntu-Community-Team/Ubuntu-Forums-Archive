---
title: "Need help coping matrix in python"
date: 2010-10-27
forum: Programming Talk
---

### Post by Nergar on 2010-10-27
Ok, i'm trying to write a Simplex algorithm but I'm having a HUGE problem with my code, I'm using two matrices to store the values, so I have matrix and matrixNew

I'm using matrixNew to store all new values and matrix to store the old ones but every time I modify matrixNew, matrix also gets modified

I've tried with:

[PHP]
matrixNew = matrix
matrixNew = list(matrix)
matrixNew = matrix[:]
[/PHP]

non of them work

here's the complete code:

[PHP]

matrix = [10,6,1,0,0,2500],[5,10,0,1,0,2000],[1,2,0,0,1,500]
matrixNew = matrix[:]
basicVars = [0,0,0]
C_j = [23,32,0,0,0]
numVars = 2
constraints = 3

"""
Don't change anything here
"""

Z_j = []
C_jZ_j = []
ratio = []
pivX = 0
pivY = 0


def calZ_jCol(col):
  size = len(matrix)
  sum = 0
  for i in range(size):
    sum += (matrix[i][col] * basicVars[i])
  return sum

def calZ_j():
  size = len(matrix[0]) - 1
  for i in range(size):
    Z_j.append(calZ_jCol(i))
  return

def calC_jZ_j():
  if len(C_j) != len(Z_j):
    print "Cj and Zj have different sizes"
    exit(0)
  for i,j in zip(C_j, Z_j):
    C_jZ_j.append(i - j)

def isSolved():
  for i in C_jZ_j:
    if i >= 0:
      return False
  return True;

def getBiggerC_jZ_j():
  bigger = 0
  for i in C_jZ_j:
    if i > bigger:
      bigger = i
  return C_jZ_j.index(bigger)

def getRatio():
  x = len(matrix[0]) - 1
  y = getBiggerC_jZ_j()
  for i in matrix:
    ratio.append(float(i[x]) / i[y])
  smaller = ratio[0]
  for i in ratio:
    if i < smaller:
      smaller = i
  return ratio.index(smaller)

def printMatrix():
  print "Start Table----"
  for i in range(len(matrix)):
    print "[",
    for j in range(len(matrix[0])):
      print matrixNew[i][j],
    print "]"
  print "End Table-----"


#def pivotRule(i, j):
#  matrixNew[i][j] = matrix[i][j] - ((matrix[i][pivX] * matrix[j][pivY])/pivot)

calZ_j()
calC_jZ_j()
isSolved()
pivY = getBiggerC_jZ_j()
pivX = getRatio()
pivot = matrix[pivX][pivY]
basicVars[pivX] = C_j[pivY]
printMatrix()
for i in range(len(matrix[pivX])):                    #divide pivot row / pivot
  matrixNew[pivX][i] = float(matrix[pivX][i]) / pivot
printMatrix()
for i in range(len(matrix)):                          #zeros in pivot col
  if i != pivX:
    matrixNew[i][pivY] = 0
printMatrix()
for i in range(len(matrix)):                          #pivot rule in non basic cols
  for j in range(numVars):
    if j != pivY:
      matrixNew[i][j] = matrix[i][j] - ((matrix[i][pivX] * matrix[j][pivY]) / float(pivot))
#     pivotRule(i, j)
printMatrix()

[/PHP]

---

### Post by Vox754 on 2010-10-28
> **Nergar said:**
> Ok, i'm trying to write a Simplex algorithm but I'm having a HUGE problem with my code, I'm using two matrices to store the values, so I have matrix and matrixNew

I'm using matrixNew to store all new values and matrix to store the old ones but every time I modify matrixNew, matrix also gets modified

I've tried with:

[PHP]
matrixNew = matrix
matrixNew = list(matrix)
matrixNew = matrix[:]
[/PHP]


Several issues.

1. Make sure you are using brackets "[ ]" to create a list of lists. Otherwise it will create a tuple of lists.
[php]
matrix_1 = [10,6,1,0,0,2500],[5,10,0,1,0,2000],[1,2,0,0,1,500]
matrixNew_1 = matrix_1[:]

id(matrix_1)
id(matrixNew_1)

matrix_2 = [ [10,6,1,0,0,2500],[5,10,0,1,0,2000],[1,2,0,0,1,500] ]
matrixNew_2 = matrix_2[:]

id(matrix_2)
id(matrixNew_2)
[/php]

2. You are using global variables. In this procedural code, it's better to pass the variables to the functions, and return values from them. Although it may seem simple now, it will help you greatly as your code grows, and you need to debug how values are being passed around.
3. Leave horizontal and vertical whitespace.
4. Use 4 spaces for indentation.
4. Use 4 spaces for indentation.
4. Use 4 spaces for indentation.
5. Use underscores for names.

You'll have a hard time hunting for errors if you don't clean up your code.

[php]
#!/usr/bin/python

#
# Definitions
#
def calZ_jCol(col, matrix, basicVars):
    size = len(matrix)
    sum = 0

    for i in range(size):
        sum += (matrix[i][col] * basicVars[i])

    return sum

def calZ_j(Z_j, matrix, basicVars):
    size = len(matrix[0]) - 1

    for i in range(size):
        Z_j.append(calZ_jCol(i, matrix, basicVars))

    return Z_j

def calC_jZ_j(C_j, Z_j, C_jZ_j):
    if len(C_j) != len(Z_j):
        print "Cj and Zj have different sizes"
        exit(0)

    for i,j in zip(C_j, Z_j):
        C_jZ_j.append(i - j)

    return C_jZ_j

def isSolved(C_jZ_j):
    for i in C_jZ_j:
        if i >= 0:
            return False

    return True

def getBiggerC_jZ_j(C_jZ_j):
    bigger = 0

    for i in C_jZ_j:
        if i > bigger:
            bigger = i

    return C_jZ_j.index(bigger)

def getRatio(matrix, C_jZ_j, ratio):
    x = len(matrix[0]) - 1
    y = getBiggerC_jZ_j(C_jZ_j)

    for i in matrix:
        ratio.append(float(i[x]) / i[y])

    smaller = ratio[0]

    for i in ratio:
        if i < smaller:
            smaller = i

    return ratio, ratio.index(smaller)

def printMatrix(matrix, matrixNew):
    print "Start Table----"

    for i in range(len(matrix)):
        print "[",
        for j in range(len(matrix[0])):
            print matrixNew[i][j],
        print "]"

    print "End Table-----"


#def pivotRule(i, j):
#  matrixNew[i][j] = matrix[i][j] - ((matrix[i][pivX] * matrix[j][pivY])/pivot)


# ===========================================================================
#
# Main program
#
# ===========================================================================
# Starting values
# ===========================================================================
matrix = [ [10,6,1,0,0,2500],[5,10,0,1,0,2000],[1,2,0,0,1,500] ]
matrixNew = matrix[:]
basicVars = [0,0,0]
C_j = [23,32,0,0,0]
numVars = 2
constraints = 3

"""
Don't change anything here
"""

Z_j = []
C_jZ_j = []
ratio = []
pivX = 0
pivY = 0 

# ===========================================================================

Z_j = calZ_j(Z_j, matrix, basicVars)
C_jZ_j = calC_jZ_j(C_j, Z_j, C_jZ_j)
IS_solved = isSolved(C_jZ_j)

pivY = getBiggerC_jZ_j(C_jZ_j)
ratio, pivX = getRatio(matrix, C_jZ_j, ratio)

pivot = matrix[pivX][pivY]
basicVars[pivX] = C_j[pivY]

printMatrix(matrix, matrixNew)

# divide pivot row / pivot
for i in range(len(matrix[pivX])):                    
    matrixNew[pivX][i] = float(matrix[pivX][i]) / pivot

printMatrix(matrix, matrixNew)

# zeros in pivot col
for i in range(len(matrix)):                          
    if i != pivX:
        matrixNew[i][pivY] = 0

printMatrix(matrix, matrixNew)

# pivot rule in non basic cols
for i in range(len(matrix)):
    for j in range(numVars):
        if j != pivY:
            matrixNew[i][j] = matrix[i][j] - ((matrix[i][pivX] * matrix[j][pivY]) / float(pivot))
#           pivotRule(i, j)

printMatrix(matrix, matrixNew)
[/php]

Since you are using matrices, you may like to use "numpy" early on to improve their handling. With numpy some operations are vectorized in a similar way to Matlab/Octave, which may help you as you use bigger matrices.

---

### Post by Nergar on 2010-10-28
hey, thanks a lot! i'll look into it!

---

### Post by Tony Flury on 2010-10-28
When you do things like :
```

matrixNew = matrix

```
Then matrixNew is just another reference to the same list - if you change matrix - i.e. add or remove items, or you change an item in matrix then matrixNew will also change because it is the same object.

```

matrixNew = list(matrix) 
matrixNew = matrix[:]

```
What these do are create a new list which contrain references to the contents of matrix - I think you can add and remove stuff in MatrixNew or matrix without impacting the other (since they are different lists), but you still can't change an existing item in either without changing the other as well.

So as you have found out that using either technique when you change matrix you change your matrixNew too.

You need to use a deep copy - which will copy the contents recursively

[http://docs.python.org/library/copy.html?highlight=deep%20copy](http://docs.python.org/library/copy.html?highlight=deep%20copy)

```

matrixNew = copy.deepcopy(matrix)

```

I think all of the above is right - I don't have a python implementation available that i can check it on.

---

