---
title: "Comment on/critique my code please!"
date: 2009-11-06
forum: Programming Talk
---

### Post by DanielJackins on 2009-11-06
So I'm taking a linear algebra course in university, and I thought it would be cool/good practice to create a program to perform various matrix operations (ie. determinants, inverses, etc.). This will probably be the first actually useful program I've ever made, so it has been a lot of fun making (just started tonight). So here's what I've got so far:

```

def det2(x1,x2,y1,y2):
    matrix = [[x1,x2],[y1,y2]]
    det = (matrix[0][0]*matrix[1][1])-(matrix[0][1]*matrix[1][0])
    return det


def det3(x1,x2,x3,y1,y2,y3,z1,z2,z3):
    matrix = [[x1,x2,x3],[y1,y2,y3],[z1,z2,z3]]
    det = (matrix[0][0]*det2(y2,y3,z2,z3))-(matrix[1][0]*det2(x2,x3,z2,z3))+(matrix[2][0]*det2(x2,x3,y2,y3))
    return det


print 'Please enter the size of the matrix:'

print

m = input('m = ')
n = input('n = ')

print

matrix = {}
choice = 1

for element in range(1,(m*n)+1):
    matrix.update({element:input('Please enter element ' + str(element) + ': ')})

print

while choice != 0:
    print 'What would you like to determine?: '
    print
    print '1) Determinant'
    print '2) Inverse'
    print '3) Eigenvalues and Eigenvectors'
    print '0) Exit'
    print
    choice = input('Please enter your choice: ')
    print
    if choice == 1:
        if m*n == 4:
            print 'The determinant is', det2(matrix[1],matrix[2],matrix[3],matrix[4])
            print
        elif m*n == 9:
            print 'The determinant is', det3(matrix[1],matrix[2],matrix[3],matrix[4],matrix[5],matrix[6],matrix[7],matrix[8],matrix[9])
            print

```

I know that it correctly computes the determinants. Any comment on the structure/efficiency or other such things? (I'm also aware that at the moment you could enter, for example, a 1x9 matrix and it would still calculate a determinant, which it shouldn't)

Thanks for any comment/suggestions :)

---

### Post by nvteighen on 2009-11-06
Try creating a single general function that calculates the determinant of any matrix. In programming, you should always point to the "**most general as possible**" solution (that's a simple way to talk about abstraction :)). Also, I don't get why you destructure the matrix when calling det2() or det3()... The ideal would be to have those functions accept a single matrix object, since you're using a dictionary as data structure and you can easily access its contents.

---

### Post by DanielJackins on 2009-11-06
Thanks for the input, it helped :) does this look better?

```
def det2(elements):
    matrix = [[elements[1],elements[2]],[elements[3],elements[4]]]
    det = (matrix[0][0]*matrix[1][1])-(matrix[0][1]*matrix[1][0])
    return det


def det3(elements):
    matrix = [[elements[1],elements[2],elements[3]],[elements[4],elements[5],elements[6]],[elements[7],elements[8],elements[9]]]
    matrix1 = {1:elements[5],2:elements[6],3:elements[8],4:elements[9]}
    matrix2 = {1:elements[2],2:elements[3],3:elements[8],4:elements[9]}
    matrix3 = {1:elements[2],2:elements[3],3:elements[5],4:elements[6]}
    det = (matrix[0][0]*det2(matrix1))-(matrix[1][0]*det2(matrix2))+(matrix[2][0]*det2(matrix3))
    return det

def det(elements):
    if len(elements) == 4:
        print det2(elements)
    elif len(elements) == 9:
        print det3(elements)


print 'Please enter the size of the matrix:'

print

m = input('m = ')
n = input('n = ')

print

matrix = {}
choice = 1

for element in range(1,(m*n)+1):
    matrix.update({element:input('Please enter element ' + str(element) + ': ')})

print

while choice != 0:
    print 'What would you like to determine?: '
    print
    print '1) Determinant'
    print '2) Inverse'
    print '3) Eigenvalues and Eigenvectors'
    print '0) Exit'
    print
    choice = input('Please enter your choice: ')
    print
    if choice == 1:
        print 'The determinant is: ', det(matrix)
        print
```

Seems cleaner, I don't know if there would have been a better way to define det3 without all the matrix1,matrix2,matrix3 stuff?

And it still evaluates correctly, but it's printing None underneath the answer.

---

### Post by nvteighen on 2009-11-06
Looks better, but you are still using different functions for something that is essentially the same just because you're not abstracting the code enough.

The weird thing is that you have it almost there. Your code is using Laplace expansion, right? ([http://en.wikipedia.org/wiki/Laplace_expansion](http://en.wikipedia.org/wiki/Laplace_expansion)) Well, you can use recursion to define a Laplace expansion for nxn matrices and whenever you find a 2x2 matrix in the course of expansion, you return that partial determinant... If you find something that's not a 2x2 matrix, you ask the program to return the result of the expected expansion.

Of course, you'll have to think in a general law on how row-column elimination is done when picking each element. Possibly, the "submatrix creation" part should be another function by itself.

Take a real close look to how you take the determinant using Laplace expansion and you'll see that it works for every dimension because it steps reducing matrices to smaller dimensions.

No idea what happens with that 'None'. I haven't run your code, but that's a inor issue compared to transforming your code into a general nxn determinant solver ;) (of course, only if you want to do that... I'm just giving you an idea on how to make it better :P)

---

