---
title: "[SOLVED] Java: Convert a string to 2D char array"
date: 2008-11-26
forum: Programming Talk
---

### Post by Igniteflow on 2008-11-26
Hi peeps,
I have a string array of 25 chars I want to put into a 2D array, five chars on each line to form a matrix of 5x5.  I know to put a string into a 1D array you just run:

char[] cArray = string.toCharArray();

But could anyone tell me how to put the string into the mentioned 2D array?  I'm thinking splitting it into blocks of five chars?  Other than though it has got e stumped.

Any guidance would be much appreciated

---

### Post by Idefix82 on 2008-11-26
You just go through the string and put each character into the correct cell in your 2d array. To compute the correct position is easy. The number of the row will be row=Math.floor(position/5), i.e. divide the number of the character by 5 and then round down. To compute the column you simply take the remainder modulo 5: col=position%5. So you loop the index pos from 0 to 24 and do
```
my2darray[Math.floor(pos/5)][pos%5]=cArray[pos];
```

---

### Post by CptPicard on 2008-11-26
Yeah, just create the index pairs for the beginning and end of each 5-character block, use the substring method of String and use toCharArray() on that...

---

### Post by Igniteflow on 2008-11-26
Thanks for your advice.  I understand what you're saying, but as a programming noob I'm having trouble putting this into a working loop to populate the array.  I have this so far

[php]
int k = 0;
int r = 5;
int c = 5;


for(int i = 0; i <= 24; i++) 
	{
	if (c<=5)
	{
	cArray[k];
		for(int i = 0; i <= 4; i++)
		{
		my2darray[Math.floor(r/5)][c%5]=cArray[k];
		k++
		c++
		}
	} else {
		r = (r + 5)
		for(int i = 0; i <= 4; i++)
		{
		my2darray[Math.floor(r/5)][c%5]=cArray[k];
		k++
		c++
		} 
[/php]

Apologies, I know this is way off, but is the closest I can get right now.  Any advice on the "pos" variable???

---

### Post by Idefix82 on 2008-11-26
```

int[][] my2darray = new int[5][5];
for(int pos=0;pos<=24;pos++)
  my2darray[Math.floor(pos/5)][pos%5]=cArray[pos];

```

---

### Post by Igniteflow on 2008-11-26
Thanks Idefix82, appreciate your patience.
I couldn't get Math to work as it gave me the "possible loss of precision" at compile.  I did come up with this less graceful code which almost achieves the same thing, although I think it should only fill the first row.  Does anyone know where I've gone wrong?  (It compiles and runs okay, but no output)

[php]
class PopulateArray
{
public static void main(String[] args)  
{
    try
    {
    int k = 0;
   	int r = 0;
	int c = 0;
	char[][] matrix = null;
	String alphabet;
    alphabet = "ABDEFGHIJKLMNOPQRSTUVWXYZ";
	char[] cArray = alphabet.toCharArray();
	

    for(int i = 0; i <= 24; i++) 
	{
	if (c<=4)
	{
	for(i = 0; i <= 4; i++)
		{
		matrix[r][c]=cArray[k];
		k++;
		c++;
		}
	} 
    }
	
	// For loop prints the contents of the array
	for(int i = 0; i <= 4; i++) 
		{
       		System.out.print("[");
       		for(int j = 0; j <= 4; j++) 
       		{
        	 	System.out.print(" " + matrix[i][j]);
       		}
       	System.out.println(" ]");
     	}
    System.out.println();
	}
	
	
	catch (ArrayIndexOutOfBoundsException e)
	{
	}
	catch (NullPointerException e)
	{
	}
}
}
[/php]

---

### Post by dwhitney67 on 2008-11-26
An alternative solution:
```

...
char[][] array = new char[5][5];

for (int i = 0; i < 5; ++i)
{
  str.getChars(i*5, (i*5)+5, array[i], 0);    // str is the 25-char string
}
...

```


For info on [,%20int)"]getChars]("http://java.sun.com/javase/6/docs/api/java/lang/String.html#getChars(int,%20int,%20char[).

---

### Post by Idefix82 on 2008-11-26
> **Igniteflow said:**
> Thanks Idefix82, appreciate your patience.
I couldn't get Math to work as it gave me the "possible loss of precision" at compile. 

In that case try
```
int[][] my2darray = new int[5][5];
for(int pos=0;pos<=24;pos++)
  my2darray[Math.floor((double)pos/5.0)][pos%5]=cArray[pos];
```

---

### Post by dwhitney67 on 2008-11-26
> **Idefix82 said:**
> In that case try
```
int[][] my2darray = new int[5][5];
for(int pos=0;pos<=24;pos++)
  my2darray[Math.floor((double)pos/5.0)][pos%5]=cArray[pos];
```

Why are you converting pos to a double, and then dividing by 5.0?

If you leave pos as an int and divide by 5, the result will be an int.  This would also obviate the need for the Math.floor().

P.S.  Refer to my previous post for (IMO) a simpler solution.

---

### Post by Idefix82 on 2008-11-26
> **dwhitney67 said:**
> Why are you converting pos to a double, and then dividing by 5.0?

If you leave pos as an int and divide by 5, the result will be an int.  This would also obviate the need for the Math.floor().

P.S.  Refer to my previous post for (IMO) a simpler solution.

Thanks for pointing that out. I just wanted to make sure that it really rounds down rather than leaving it to the implementation. I don't really know Java. My solution works in any decent programming language.

I actually fail to see why your solution is simpler but I don't feel like going into this argument.

---

### Post by geirha on 2008-11-26
Alternatively, you can use the 1D-array as a matrix too by calculating the index with row * width + column. E.g.:

```

char[] cArray= string.toCharArray();
int w= 5, h= 5;     // width and height

System.out.println("row 2, col 3: " + cArray[2*w+3]);

System.out.print("row 1: ");
for (int j= 0; j < w; j++)
    System.out.print(cArray[1*w+j] + " ");
System.out.println();

System.out.print("col 0: ");
for (int i= 0; i < h; i++)
    System.out.print(cArray[i*w+0] + " ");
System.out.println();

```

I find it easier to do it that way.

---

### Post by Igniteflow on 2008-11-26
Thank you to all that helped, here is the solution with a second for loop to print the resulting matrix which appears as:

[ A B C D E ]
[ F G H I J ]
[ K L M N O ]
[ P Q R S T ]
[ U V W X Y ]

[php]
class Matrix
{
public static void main(String[] args)  
{
String alphabet = "ABCDEFGHIJKLMNOPQRSTUVWXY";  // Minus Z
char[][] matrix = new char[5][5];

for (int i = 0; i < 5; ++i)
  {
  alphabet.getChars(i*5, (i*5)+5, matrix[i], 0); 
  }    


for(int i = 0; i <= 4; i++) 
{
  	System.out.print("[");
  	for(int j = 0; j <= 4; j++) 
  	{
  	System.out.print(" " + matrix[i][j]);
  	}
  	System.out.println(" ]");
  	}
	System.out.println();
}
}
[/php]

---

### Post by CptPicard on 2008-11-27
> **Idefix82 said:**
> My solution works in any decent programming language.

IMO integer division producing integers is far more standard in any "decent programming language" than "Math.floor".. ;)

---

