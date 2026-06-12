---
title: "need help with simple C++ code"
date: 2009-10-23
forum: Programming Talk
---

### Post by jdunn on 2009-10-23
I'm taking an algorithms class and learning C++ on my own.  I've written a simple quicksort algorithm that compiles but I get a segmentation fault when I run the program.  I'm using the standard G++ compiler.  What's wrong with my code?

**edit**
```

// Quicksort example
//
#include <iostream>
using namespace std;

int partition(int a[], int p, int r) {
	int t;
	int x = a[r];
	int i = p - 1;
	for (int j=p; j <= r - 1; j++) {
		if (a[j] <= x) {
			i++;
			t = a[i];
			a[i] = a[j];
			a[j] = t;
		}
	}
	t = a[i + 1];
	a[i + 1] = a[r];
	a[r] = t;
	return (i + 1);
}

void quicksort(int a[], int p, int r) {
	if (p < r) {
		int q = partition(a, p, r);
		quicksort(a, p, q - 1);
		quicksort(a, q + 1, r);
		}
	        for (int k = 0; k < 10; k++)
		cout << a[k] + " ";
}

int main () {
	int a[] = {8, 16, 52, 13, 82, 21, 0, 12, 30, 61};
	int p = 0;
	int r = 9;
	quicksort(a, p, r);
}

```

---

### Post by MadCow108 on 2009-10-23
use a debugger like gdb to debug your code

on a quick glance your loop boundaries seem wrong
your using a[0] and a[9] as boundaries which are 8 and 61
but the array only has 10 entries

also the loop is an infinite loop:
for (int j=p; **r - 1**; j++) {
r-1 always evaluates to true (as long r > 1), because r is never changed in the loop body

normally loops look like this:
for (int j=somestart; j<someend; j++) {

---

### Post by jdunn on 2009-10-23
> **MadCow108 said:**
> use a debugger like gdb to debug your code

on a quick glance your loop boundaries seem wrong
your using a[0] and a[9] as boundaries which are 8 and 61
but the array only has 10 entries {

I'm passing the pointer to the array, as well as the 1st and last elements of the array to the quicksort function.  That's how its supposed to work.

---

### Post by januzi on 2009-10-23
> int a[] = {8, 16, 52, 13, 82, 21, 0, 12, 30, 61};
int p = a[0];[FONT=monospace] [/FONT]
int r = a[9];
p = 8; r = 61;

> [FONT=monospace]
[/FONT]int partition(int a[], int p, int r) {[FONT=monospace] 
 // ...
 [/FONT]int x = a[r];
[FONT=monospace] [/FONT]//...
  for (int j=p;[FONT=monospace]
[/FONT]      if (a[j]

x = a[61] ; 
"a" has got size 10: a[0] ... a[9]

j = 8 ; if (a[8]  
j = 9 ; if (a[9] 
next step and there will be a[10]

---

### Post by dwhitney67 on 2009-10-23
@ OP

I believe the quicksort algorithm specifies that the first and last indexes of the array are to be passed to the function, not the actual values within the array.

In most algorithms I've seen, the indexes are 1-based, not zero.  Hence the reason there is a statement such as:
```

	int i = p - 1;

```

---

### Post by MadCow108 on 2009-10-23
> **jdunn said:**
> I'm passing the pointer to the array, as well as the 1st and last elements of the array to the quicksort function.  That's how its supposed to work.
maybe, but you still can't use the values of certain array elements as loop conditions
you have to loop on the array itself and not on the values of the array when using the loop variables as array indices.

your loop looks something like this:
for i from 8 to 61:
a[i] ...

now a is only defined from 0 to 9, when the loop reaches 10:
a[10] -> bam! segmentation fault, your trying to access memory which does is not defined

you probably want to pass the pointer to the first and last element of the array instead of the value. Those you can use in the loop
```

partition(int array[], int * first, int * last);

main() {
partition(ar,&ar[0],&ar[9]);
}

```

---

### Post by jdunn on 2009-10-23
Oops.  Now I see what people mean.  I changed it so p=0 and r=9 now but I still get the seg fault.

---

### Post by Zugzwang on 2009-10-23
> **jdunn said:**
> Oops.  Now I see what people mean.  I changed it so p=0 and r=9 now but I still get the seg fault.

Look at what MadCow wrote in his first post (in bold letters). The solution is there. Your for-loop is in fact is equivalent to:
```

{
  int j=p;
  while (r-1!=0) {
    [ loop body ]
    j++;
  }
}

```
This is not what you meant.

---

### Post by jdunn on 2009-10-23
I sort of understand what you're saying but I don't know how to do it.  This is not a homework assignment.  Can someone please modify the code so it works?  That way, I'll have a better understanding.

---

### Post by Dougie187 on 2009-10-23
I'm not sure, but I think this is what you are looking for.
```
// Quicksort example
// //
#include <iostream>
using namespace std;

int partition(int a[], int p, int r) {
	int t;
	int x = a[r];
	int i = p - 1;
	for (int j=p; j <= r - 1; j++) {
		if (a[j] <= x) {
			i++;
			t = a[i];
			a[i] = a[j];
			a[j] = t;
		}
	}
	t = a[i + 1];
	a[i + 1] = a[r];
	a[r] = t;
	return (i + 1);
}

void quicksort(int a[], int p, int r) {
	if (p < r) {
		int q = partition(a, p, r);
		quicksort(a, p, q - 1);
		quicksort(a, q + 1, r);
	}
	//	for (int k = 0; k < 10; k++)
	//		cout << A[k] + " ";
}

int main () {
	int a[] = {8, 16, 52, 13, 82, 21, 0, 12, 30, 61};
	int p = 0;
	int r = 9;
	quicksort(a, p, r);
}
```

---

### Post by jdunn on 2009-10-23
> **Zugzwang said:**
> Look at what MadCow wrote in his first post (in bold letters). The solution is there. Your for-loop is in fact is equivalent to:
```

while (r-1!=0) {
  [ loop body ]
  j++;
}

```
This is not what you meant.

Looks more to me like For (j = 0 to 8, j++) for the first recursion.  I don't see where you get While (r-1 != 0)

---

### Post by jdunn on 2009-10-23
> **Dougie187 said:**
> I'm not sure, but I think this is what you are looking for.


It looks like you just fixed the r and p in the main function.  I already fixed that but I still get the segmentation fault.

---

### Post by Zugzwang on 2009-10-23
> **jdunn said:**
> Looks more to me like For (j = 0 to 8, j++) for the first recursion.  I don't see where you get While (r-1 != 0)

Because if you want "for i=1 to 8" in C or C++, you must do:
```

for (int i=1;i<=8;i++) { .. }

```

Doing
```

for (int i=1;8;i++) { .. }

```
lets the for loop run while "8", which in this case means forever.

---

### Post by jdunn on 2009-10-23
> **Zugzwang said:**
> Because if you want "for i=1 to 8" in C or C++, you must do:
```

for (int i=1;i<=8;i++) { .. }

```

Doing
```

for (int i=1;8;i++) { .. }

```
lets the for loop run while "8", which in this case means forever.

I don't want the loop to go from 1 to 8 on the first recursion.  On the first recursion, p = 0, r = 9 and there are 10 elements in the array.  0..9 = 10 elements.

The loop is For (j = p; r - 1; j++) which is the equivalent of j = 0 to 8.  The loop should execute 9 times before  i + 1 is returned.

---

### Post by jdunn on 2009-10-23
nm.  I see the next problem.  I think you were trying to tell me the the 2nd condition in my loop statement was incomplete.

I'm changing the loop header to For (j = 0; j <= r - 1; j++)
Sorry, that was a dumb mistake.  I compiled it and it runs.  Now, I just need to uncomment the printf statfement to see if it sorted properly.

**Edit**

Sementation fault is gone but the code still doesn't work right.  It prints out what looks like address information.

---

### Post by dwhitney67 on 2009-10-23
Here's some code I tinkered with once before:
```

#include <vector>
#include <iostream>
#include <iterator>
#include <ctime>
#include <cstdlib>


const int SMALL_ENOUGH = 15;


template <typename T>
void selectionsort(T& array, const int left, const int right)
{
  for (int i = left; i < right; ++i)
  {
    int min = i;

    for (int j = i+1; j <= right; ++j)
    {
      if (array[j] < array[min])
        min = j;
    }
    typename T::value_type temp = array[min];
    array[min] = array[i];
    array[i] = temp;
  }
}


template <typename T>
int partition(T& array, const int left, const int right)
{
  typename T::value_type val = array[left];
  int                    lm  = left-1;
  int                    rm  = right+1;

  for(;;)
  {
    do
    {
      rm--;
    } while (array[rm] > val);

    do
    {
      lm++;
    } while(array[lm] < val);

    if (lm < rm)
    {
      typename T::value_type temp = array[rm];
      array[rm] = array[lm];
      array[lm] = temp;
    }
    else
    {
      return rm;
    }
  }
}


template <typename T>
void quicksort(T& array, const int left, const int right)
{
  if (left < (right - SMALL_ENOUGH))
  {
    int split = partition(array, left, right);
    quicksort(array, left, split);
    quicksort(array, split+1, right);
  }
  else
  {
    selectionsort(array, left, right);
  }
}


int main()
{
   srand(time(0));

   std::vector<int> array;

   while (array.size() < 40)
   {
      int val = rand() % 100;

      array.push_back(val);
   }

   std::copy(array.begin(), array.end(), std::ostream_iterator<int>(std::cout, " "));
   std::cout << std::endl;

   quicksort(array, 0, array.size() - 1);

   std::copy(array.begin(), array.end(), std::ostream_iterator<int>(std::cout, " "));
   std::cout << std::endl;
}

```

---

### Post by jdunn on 2009-10-23
dwhitney,
Since I'm not yet very proficient at writing or understanding C++, I don't understand some of your code.

---

### Post by dwhitney67 on 2009-10-23
> **jdunn said:**
> dwhitney,
Since I'm not yet very proficient at writing or understanding C++, I don't understand some of your code.

Don't pay too much attention to the "fluff" around my function declarations.  Just focus on the "meat" of the functions (ie. quicksort() and partition()), which you will find is very similar to your own.

---

### Post by jdunn on 2009-10-23
result of running my code:

 D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533;
Press ENTER to continue.

---

### Post by dwhitney67 on 2009-10-23
> **jdunn said:**
> result of running my code:

 D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533; D&#65533;&#65533;&#65533;h&#65533;
Press ENTER to continue.

Is this from the same code that you posted earlier?

If not, please post the updated code.

EDIT:  I just ran the code posted by 'dougie'; it works fine.  Thus focus your attention there.

---

### Post by jdunn on 2009-10-23
My code is updated in my first post.  this is the output I get.

I understand how quicksort works but I don't know C++ very well.  From what I can tell, your code chooses the midpoint of the array (val) as the pivot, then compares values from the left subarray to val and the right subarray to val and then to each other.  Then swaps left with right if left < right.  I have no idea why you are using a selection sort function.

Understanding the "fluff" is key to getting something other than garbage on the screen, like I get now.

---

### Post by jdunn on 2009-10-23
> EDIT:  I just ran the code posted by 'dougie'; it works fine.  Thus focus your attention there.

That can't be right.  His code is identical to mine, except he commented the two lines that print out the array.  In fact, I copied his code to a file, uncommented the two lines, saved it, compiled and ran it and got the same garbage on my screen.

---

### Post by MadCow108 on 2009-10-23
the reason you get garbage is that your output line is wrong:
you can't concatenate basic integers and cstrings with '+' in c++
change it to this:
cout << a[k] << " ";

the << operator adds a[k] to the stream and returns the stream again, so you can chain these operators to print as much as you want in one line

with that change your code seems to work fine

dwhitney's fluff is mostly just stuff to generalize the algorithm to any datatype (the template stuff) and he probably uses selectionsort at a certain point because it is faster than quicksort for small arrays

---

### Post by dwhitney67 on 2009-10-23
> **jdunn said:**
> My code is updated in my first post.  this is the output I get.

I understand how quicksort works but I don't know C++ very well.  From what I can tell, your code chooses the midpoint of the array (val) as the pivot, then compares values from the left subarray to val and the right subarray to val and then to each other.  Then swaps left with right if left < right.  I have no idea why you are using a selection sort function.

Understanding the "fluff" is key to getting something other than garbage on the screen, like I get now.

I read somewhere that for a small pool of data, that the selection sort is more efficient than the quick sort.  But hey, what do I know!  :)

Anyhow, the point of the quick sort is to create smaller, more manageable lists of data.  The initial midpoint, as obtained by calling partition, is used for divvying the original list.  The rest involves recursion, so that each sub-list is made even smaller until the values are sorted.

---

### Post by jdunn on 2009-10-23
> **MadCow108 said:**
> the reason you get garbage is that your output line is wrong:
you can't concatenate basic integers and cstrings with '+' c++
change it to this:
cout << a[k] << " ";

the << operator adds a[k] to the stream and returns the stream again, so you can chain these operators to print as much as you want in one line

Thanks.  that helps.  Now I'm getting the numbers and the sort seems to work.

---

### Post by dwhitney67 on 2009-10-23
> **jdunn said:**
> That can't be right.  His code is identical to mine, except he commented the two lines that print out the array.  In fact, I copied his code to a file, uncommented the two lines, saved it, compiled and ran it and got the same garbage on my screen.

Right... I did not uncomment those line; I merely deleted them (since I knew that they were in an inappropriate place).

I substituted them with calls in the main() function to print the array before and after calling quicksort.  Here's how:
```

#include <iostream>
#include <iterator>

...

int main () {
        int a[] = {8, 16, 52, 13, 82, 21, 0, 12, 30, 61};
        int p = 0;
        int r = 9;

        std::copy(a, a+10, std::ostream_iterator<int>(std::cout, " "));
        std::cout << std::endl;
        
        quicksort(a, p, r);
        
        std::copy(a, a+10, std::ostream_iterator<int>(std::cout, " "));
        std::cout << std::endl;
}

```

---

