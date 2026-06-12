---
title: "logic error"
date: 2007-05-03
forum: Programming Talk
---

### Post by theorem_hunter on 2007-05-03
i am trying to implement something in Java, but the logic should be language specific... i have spent the past few days thinking about this & just cant get it right, but i know i have been very close...

i want a 2D array to have a output was follows...

let int x = n; let me just say 4
let int y = n-1; so this will be 3

when i have

for (int a=0; a<x; a++)
   for (int b=0; b<y; b++)
       print arr[a][b]

----------------------

0 1 2
0 1 3
0 2 3
1 2 3

then if x was 5 & y was 4, the output would look like this...

0 1 2 3
0 1 2 4
0 1 3 4
0 2 3 4
1 2 3 4

if x was 6 & y was 5 then

0 1 2 3 4 
0 1 2 3 5
0 1 2 4 5
0 1 3 4 5
0 2 3 4 5
1 2 3 4 5

& so the pattern continues...
any help is appreciated... thanks

---

### Post by b1g4L on 2007-05-03
In your second example with x = 5 and y = 3, I believe you only meant for there to be 3 columns, correct?

---

### Post by theorem_hunter on 2007-05-03
sorry, that was a typo.. y was supposed to be 4, i have updated it.

---

### Post by b1g4L on 2007-05-03
Are you just trying to traverse a 2d array and print the contents of each index?


If not, what data is in the arrray....the code you have assumes there is some data already stored.

---

### Post by theorem_hunter on 2007-05-03
i have tried this a number of ways. with 2D & 1D arrays... the arrays are created but not initialized, well they are initialized to NULL... 

i want to give them those values... 

so that when i do traverse through the array, the output would look like that.

---

### Post by b1g4L on 2007-05-03
Ok I think I got it.....You have it reversed.

```
for (b = 0; b < y; b++)
   for (a = 0; a < x; a++)
   //Here you insert b into array[a][b]
```

** Make sure the second for loop and the insert is inside the first for loop **


Then it's simply a matter of traversing the 2d array and printing the contents of each index. Good luck.  \\:D/

---

### Post by theorem_hunter on 2007-05-03
thanks, i think i have done what you suggested but i get 0's & 1's as a output...

```

public class pat {
    
    private int sets = 3;
    private int arr[][];
   
    public pat() {
        arr = new int[sets][sets-1];
    }
    
    public void initialize() {
        for (int y=0; y<(sets-1); y++) {
            for (int x=0; x<sets; x++) {
                arr[x][y] = y;
            }
        }
    }
    
    public void print() {
        for (int x=0; x<sets; x++) {
            for (int y=0; y<sets-1; y++) {
                System.out.print(arr[x][y]);
            }
            System.out.println();
        }
    }
}

```

```

public class Main {
    public static void main(String[] args) {
        pat p = new pat();
        p.initialize();
        p.print();   
    }
}

```

when i run this i get

```

01
01
01

```

---

### Post by theorem_hunter on 2007-05-03
well 1 of the two methods i thought about doing this was...

```

public class pat {
    
    private int sets = 3;
    private int arr[];
   
    public pat() {
        arr = new int[sets*(sets-1)];
    }
    
    public void initialize() {
        int count =0;
        int num = 0;
        
        for (int i=0; i<(sets*(sets-1)); i++)
        {
            arr[i] = num;
            count++;
            if (count == (sets-1))
            {
                num++;
                count=0;
            }
        }
        
    }
    
    public void print() {
        for (int i=0; i<(sets*(sets-1)); i++)
        {
            System.out.print(arr[i]);
            if (i%(sets-1)==0)
                System.out.println();
        }
    }
}

```

which gives a output so close to what i want...

```

0
01
12
2

```

some were in the above code is a small logic error... probably in the print method ;)

the other way i thought about doing this is a lot more complicated, it involves y amount of arrays to count the number of times a number appears. it also used polymorphism...

---

### Post by theorem_hunter on 2007-05-03
maybe this will make it easier to understand what i want...

if a=4 & b = 3

these will be what i want to be stored in the array positions...

```

[0,0] = 0; [0,1] = 1; [0,2] = 2;
[1,0] = 0; [1,1] = 1; [1,2] = 3;
[2,0] = 0; [2,1] = 2; [2,2] = 3;
[3,0] = 1; [3,1] = 2; [3,2] = 3;

```

so that when i run,

```

for (int x=0; x<a; x++)
   {
   for (int y=0; y<b; y++)
   {
      System.out.print(arr[x][y]);
   }
   System.out.println();
}

```

i will get the following output...

```

012
013
023
123

```

if you read the output form left to right, but read form top to bottom before moving to the next column, it reads...

000111222333

it would read

00001111222233334444

if a were 5 & b was 4...

---

### Post by theorem_hunter on 2007-05-03
i am getting a little bit closer...

```

public class pat {
    
    private int sets = 4;
    private int arr[][];
    
    public pat() {
        arr = new int[sets][(sets-1)];
    }
    
    public void initialize() {
        
        int skip = sets-1; //3
        
        for (int x=0; x<sets; x++) {
            for (int y=0; y<(sets-1); y++) {
                if (y != skip)
                    arr[x][y] = y;
                if (y == skip)
                    arr[x][y] = y+1;
            }
            skip--;
        }
    }
    
    public void print() {
        
        for (int x=0; x<sets; x++) {
            for (int y=0; y<(sets-1); y++) {
                System.out.print(arr[x][y]);
            }
            System.out.println();
        }
    }
}

```

now this prints...

```

012
013
022
112

```

:) nearly there

---

### Post by WW on 2007-05-03
Try this in initialize():
```

        for (int x=0; x<sets; x++) {
            for (int y=0; y<(sets-1); y++) {
                arr[x][y] = y;
                if (x+y >= sets-1)
                    arr[x][y] = y+1;
            }
        }

```

---

### Post by Blacktalon on 2007-05-03
What exactly are you attempting to do?

---

### Post by b1g4L on 2007-05-03
OK I got it. Sorry my first solution was a little off. I needed to add two variables to keep track of which number to insert and how many times that number had been inserted. There may be a more efficient way, but this works.

pat.java
```
public class pat
{    
    private int SETS = 6;
    private int[][] arr;
    private int count = 0;		//keeps track of how many times a number is inserted into array
    private int number = 0;		//which number to insert into array
   
    public pat()
    {
    	arr = new int[SETS][SETS-1];
    }
    
    public void init()
    {    	
    	for (int b=0; b<(SETS-1); b++)
    	{
            for (int a=0; a<SETS; a++)
            {
                if (count < (SETS-1))
                {
                	arr[a][b] = number;
                	count++;
                }
                else
                {
                	arr[a][b] = number + 1;
                	number++;
                	count = 1;
                }
            }
        }
    }
    
    public void print()
    {
    	for (int i=0; i<SETS; i++)
        {
        	for (int j=0; j<(SETS-1); j++)
        	{
        		System.out.print(arr[i][j]);
        	}
        	System.out.println();
        }
    }
}
```

Main.java
```
public class Main {
    public static void main(String[] args) {
        pat p = new pat();
        p.init();
        p.print();   
    }
}
```

---

### Post by theorem_hunter on 2007-05-03
b1g4L, thanks, thats exactly it :)

---

### Post by theorem_hunter on 2007-05-03
slash2314 also gave a lot of help, thanks...
his post is

```

public class EXPERIMENT{
	public static void main(String[] args){
		int x = 4;
		int y = 3;
		int num = 0;
		int count = 0;
		int[][] arr = new int[x][y];
		for (int column=0; column<y;column++){
			for (int row=0;row<x;row++){
				count+=1;
				arr[row][column] = num;
				System.out.print("["+row+","+column+"] = "+arr[row][column]);
				if (count==3)
				{
					num+=1;
					count=0;
				}
			}
			System.out.println();
			
			
		}
		for (int row=0;row<x;row++){
			for (int column=0;column<y;column++){
				System.out.print(arr[row][column]);
			}
			System.out.println();
		}

	}
}

```

very nice :)

---

### Post by WW on 2007-05-03
Try the version that I posted above.  There is no need for the extra  "count" variable.

---

### Post by WW on 2007-05-03
Here's a short C version:
```

/*
 *  arr.c
 */

#include <stdio.h>

#define MAX_SETS 10

int main(int argc, char *argv[])
    {
    int arr[MAX_SETS][MAX_SETS-1];
    int i,j;
    int sets;

    sets = atoi(argv[1]);
    for (i = 0; i < sets; ++i)
        for (j = 0; j < sets-1; ++j)
            if (i+j >= sets-1)
                arr[i][j] = j+1;
            else
                arr[i][j] = j;

    for (i = 0; i < sets; ++i)
        {
        for (j = 0; j < sets-1; ++j)
            printf("%d",arr[i][j]);
        printf("\n");
        }
    }

```
```

~/tmp$ gcc arr.c -o arr
~/tmp$ ./arr 4
012
013
023
123
~/tmp$ ./arr 5
0123
0124
0134
0234
1234
~/tmp$ ./arr 6
01234
01235
01245
01345
02345
12345
~/tmp$

```

---

### Post by theorem_hunter on 2007-05-03
thats great WW  :) C is nice...

i cant believe i was thinking about it for so long... :)

---

### Post by ghandi69_ on 2007-05-03
I just got done doing a homework assignment in C, where we had to take a an array of any size, and

print it to the screen;
add them together  & pring;
subtract and print;
multiply them and print;
find determient and print;

I figured out how to do that, but I still had no idea what you were trying to do.

---

### Post by twstokes on 2007-05-03
Here's a way to do it in C with a one dimensional array. I'm not sure if you absolutely have to use a two dimensional one, but just in case this might be helpful:

```

#include <stdio.h>

#define X 5

int main()
{
	int array[X];
	int i, j;
	
	for (i=0; i<X; i++)
		array[i] = i;
	
	for (i=0; i<X+1; i++)
	{
		for (j=0; j<X; j++)
			printf ( "%d", array[j] ); 
	printf ( "\n" );
	array[X-i-1]++;
	}
}


```

---

### Post by theorem_hunter on 2007-05-04
twstokes, thanks, thats great,

a 1D array, in my opinion is better because it uses less memory :)

---

