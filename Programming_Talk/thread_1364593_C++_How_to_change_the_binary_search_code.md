---
title: "C++ How to change the binary search code?"
date: 2009-12-26
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-26
I have written a code to binary search the element in array.

But if the element is not found, the search is looped forever.
How to change this so it returns -1 if the element's not found?

Here's the code:

**array[]** - array to search.
**N** - number of elements in array.
**Number** - number to find.

```

int Binary_Search(int array[], int N, int Number)
{
    int Left, Right, Middle;
    Left=0;
    Right=N;
    Middle=(Left+Right)/2;
    for(;;)
    {
        cout << Middle << endl;
        if(array[Middle]==Number)
            return Middle;
        if(array[Middle]<Number)
        {
            Left=Middle;
            Middle=(Middle+Right)/2;
        }
        else
        {
            Right=Middle;
            Middle=(Middle+Left)/2;
        }
    }
    return -1;
}

```

---

### Post by LKjell on 2009-12-26
is the array already sorted?

---

### Post by OVERPOWER8 on 2009-12-26
>> **LKjell**

Sure it is!

---

### Post by Some Penguin on 2009-12-26
When it's looping forever, what is the relationship between Left, Right and Middle?

---

### Post by OVERPOWER8 on 2009-12-26
>> **[Some Penguin]("http://ubuntuforums.org/member.php?u=963358")**

The search area is shrinks from right and left.

Just test the code and you'll c.

---

### Post by LKjell on 2009-12-26
Then if left == right you break it.

```
int Binary_Search(int array[], int N, int Number)
{
    int Left, Right, Middle;
    Left=0;
    Right=N;
    Middle=(Left+Right)/2;
    do
    {
        cout << Middle << endl;
        if(array[Middle]==Number)
            return Middle;
        if(array[Middle]<Number)
        {
            Left=Middle;
            Middle=(Middle+Right)/2;
        }
        else
        {
            Right=Middle;
            Middle=(Middle+Left)/2;
        }
    }while(Right != Left);
    return -1;
}
```

Edit: it is in the morning. So I have not tested the code above. Should work but my gut feeling says something is wrong.

---

### Post by Some Penguin on 2009-12-26
Bingo.  Well, mostly -- there's still a degenerate case that needs to be handled.

Try a two-value array:  0, 1.
Search for 1.

---

### Post by LKjell on 2009-12-26
This one should work. Sorry for using C but that can be easily changed. The function works with C++ though.

```
#include <stdio.h>

int binary_search(int *array, int n, int number)
{
	int left = 0;
	int right = n;
	
	do
	{
		int middle = (right + left)/2;
		int mod = (right + left)%2;
		
		if (array[middle] == number)
			return array[middle];
		
		if (number < array[middle])
			right = middle - mod;
		else
			left = middle + mod;
	}while(right != left);
	
	return -1;
}

int main()
{
	int array[] = {0,1,3,3,5,5,6,7};

	for (int i = 0, k = 0; i < 8; i++) {
		k = binary_search(array, 8, i);
		printf("%d\n", k);
	}
}
```

---

### Post by kwyto on 2009-12-26
you shouldn't declare variables inside a loop, i think you can do better 
 
```

for( middle = ( left + right ) / 2 ; middle <= N && middle >= 0; middle = ( left + right ) / 2 ) 
     if ( array[middle] == number ) return middle;
     else if( array[middle] < number ) right = middle + 1;
            else left = middle - 1;
     
 return -1;

```

---

### Post by Some Penguin on 2009-12-26
Rather than provide a direct answer to what screams "homework question", I'll continue with some notes:

1.  In C, integer division does not round; it truncates.  1/2 = -1/2 = 0.

2.  It is simpler if you think [a,b] rather than [a,b).  Of course, if you do, [a,a] does NOT scream 'end immediately' unless you have already checked a... or a is out of bounds.

3.  If you have already checked a value at index m, and it is not your match, then why would you include m in your new bounds?  Either m+1 or m-1 seems like a better candidate for an inclusive boundary.

---

