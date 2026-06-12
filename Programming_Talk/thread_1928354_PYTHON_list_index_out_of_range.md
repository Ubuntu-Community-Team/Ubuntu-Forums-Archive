---
title: "PYTHON: list index out of range"
date: 2012-02-19
forum: Programming Talk
---

### Post by nischalinn on 2012-02-19
I want to explain my code to you.

1. this code is to search for the given number whether it is present in the list or not.
2. first if statement returns the value of row if the i/p number is in the first column 

3. if the given number is not in the first column, the second if statement compares the i/p number with the values in the first column of different rows.

4. if the i/p number is less than the value of matrixM[row+1][0], it goes to 
matrixM[row][0] i.e. previous row to search the i/p number and return index.

Suppose the i/p number is 22, since it is not in the first column, the second if statement is executed. 

when row = 2, row+1 = 3 =>matrixM[3][0] == 28, since 22<28, it should go to the third row and search for 22 & return the value of row and column.

Why this code is showing error in main()? 

```

def checkvalue(number,matrixM):
	
	for row in range(len(matrixM)):
		if (matrixM[row][0] == number):
			return row,0
		
		elif(matrixM[row+1][0] < number):
			for column in range(len(matrixM)):
				if(matrixM[row][column] == number):
					return row, column
			  
					
				
def main():
	matrix = [[2,4,6,8],[10,12,14,16],[20,22,24,26],[28,30,32,34]]
	row1=0
	column1=0	
	n = int(input(('provide the value of n: ')))
	row1,column1 = checkvalue(n,matrix)
	print('\n')
	print(row1,column1)
	return 0

if __name__ == '__main__':
	main()


```

> 
provide the value of n: 22
Traceback (most recent call last):
  File "check.py", line 48, in <module>
    main()
  File "check.py", line 42, in main
    row1,column1 = checkvalue(n,matrix)
  File "check.py", line 30, in checkvalue
    elif(matrixM[row+1][0] < number):
IndexError: list index out of range


---

### Post by The Cog on 2012-02-20
Moved to programming talk.

On the last row (row=3), then row+1 is 4, so that matrixM[row+1] is out of range. You are searching past the end of the array.

---

### Post by StephenF on 2012-02-20
This program performs a binary search. If the data is not perfectly in order it can fail.
```

#!/usr/bin/python3

import itertools

def checkvalue(val, matrix):
    """Perform a binary search on a sorted matrix."""

    def linear(r, c):
        """Reduce the coordinates of the matrix to a single value."""

        return r * len(matrix[0]) + c
        
    def coord(l):
        """Given an offset compute the row and column coordinates."""
        
        return divmod(l, len(matrix[0]))
        
    bot = 0
    # Calculate top from the index of the bottom right value.
    top = linear(len(matrix) - 1, len(matrix[0]) - 1)

    while bot <= top:
        # Bisect the matrix and compare the value.
        mid = (top - bot) // 2 + bot
        row, col = coord(mid)
        comparison = cmp(val, matrix[row][col])

        # Disregard the incorrect half or return the result.
        if comparison < 0:
            top = mid - 1
        elif comparison > 0:
            bot = mid + 1
        else:
            return row, col

    raise ValueError("value %d could not be found in the matrix" % val)


def main():
    matrix = [[2,4,6,8],[10,12,14,16],[20,22,24,26],[28,30,32,34]]
    n = int(input(('provide the value of n: ')))
    try:
        row, col = checkvalue(n, matrix)
    except ValueError as e:
        print(e)
    else:
        print(row, col)


if __name__ == '__main__':
    main()

```

---

