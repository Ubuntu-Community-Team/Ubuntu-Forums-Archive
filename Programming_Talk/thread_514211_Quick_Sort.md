---
title: "Quick Sort"
date: 2007-07-29
forum: Programming Talk
---

### Post by ashvala on 2007-07-29
Post a C code for:
Quick Sort

---

### Post by init1 on 2007-07-29
There are several examples here. 
[http://alienryderflex.com/quicksort/](http://alienryderflex.com/quicksort/)

---

### Post by ashvala on 2007-07-31
All right.. How many of you can solve this problem?

Write a quick sort program in C & post it

---

### Post by tszanon on 2007-07-31
Is that your homework?

---

### Post by LaRoza on 2007-07-31
[http://ubuntuforums.org/showthread.php?p=3098942#post3098942](http://ubuntuforums.org/showthread.php?p=3098942#post3098942)

This is a duplicate post.

-EDIT Posts were merged

---

### Post by trwww on 2007-07-31
Here is my QuickSort implementation from Introduction to Computer Science. Please dont turn it in as your work.

```
// PROGRAM	pa5a.cpp
// PROGRAMMER	Todd Wade
//
// SIGNATURE    __________________________________________________
//     
//  - I have not used source code obtained from another student,
//    or any other unauthorized source, either modified or unmodified. 
//     
//  - All source code and documentation used in my program
//    is either my original work, or was derived, by me, from the source
//    code published in the textbook for this course or presented in class.
//     
//  - I have not discussed coding details about this project with anyone
//    other than my instructor. I understand that I may discuss the
//    concepts of this program with other students, and that another
//    student may help me debug my program so long as neither of us
//    writes anything during the discussion or modifies any computer
//    file during the discussion.  I have violated neither the spirit
//    nor letter of this restriction.
//
// DESCRIPTION	exercise 5.24 p 380
// EXTERNAL FILES: n/a
// INPUT	n/a
// OUTPUT	a sorted integer array
// WARNINGS	see below
// SYSTEM	Microsoft Visual C++ 6.0/Windows 2000
// DATE	4.14.02
// MODIFICATION date of modification, programmer (lines added as needed)
//	description of modifications

#include <iostream>

using std::cout;
using std::cin;
using std::endl;
using std::flush;

#include <iomanip>

using std::setw;

void makeCopy(int[], const int[], int); 
void printArray( const int[], const int[], int );

void quickSort(int [], int, int);
int myPartition(int [], int, int);

void swap(int &, int &);

int main() {

	int ary[] = {37, 2, 6, 4, 89, 8, 10, 12, 68, 45};

	int arSz = (sizeof(ary)/sizeof(int)) - 1;

	int copy[100] = { 0 };
	makeCopy( copy, ary, arSz );
	
	quickSort( ary, 0, arSz );

	printArray( copy, ary, arSz );

	return(0);

}

void quickSort( int a[], int l, int r) {

	int p = 0;
	
	if (l < r ) { // if not, im done
		p = myPartition(a, l, r);
		quickSort(a, l, p - 1);
		quickSort(a, p + 1, r);
	}

	return;
}

int myPartition( int a[], int lmepos, int nsp) {

	// lmepos -- LeftMostElementPosition
	// nsp -- NextStartPosition

	int lme = a[lmepos]; // LeftMostElement
	int sentinel = 1, i = 0;

	while (sentinel) {
		if (sentinel % 2) {
			// starting from right
			// looking for fist element lt <
			for (i = nsp; ; i--) {
				if (a[i] < lme) {
					swap(a[i], a[lmepos]);
					nsp = lmepos + 1;
					lmepos = i;
					sentinel++;
					break;
				} else if (a[i] == lme) {
					// found myself. Im done.
					sentinel = 0;
					break;
				}
			}
		} else {
			// starting from left
			// looking for fist element gt >
			for (i = nsp; ; i++) {
				if (a[i] > lme) {
					swap(a[i], a[lmepos]);
					nsp = lmepos - 1;
					lmepos = i;
					sentinel++;
					break;
				} else if (a[i] == lme) {
					// found myself. Im done.
					sentinel = 0;
					break;
				}
			}
		}
	}
	return(lmepos);
}

void swap(int &lv, int &rv) {
	int hold = lv;
	lv = rv;
	rv = hold;
	return;
}

void makeCopy(int d[], const int s[], int i) {

	// d -- dough
	// s -- stamp
	// i -- index

	for (int x = 0; x <= i; x++) {

		d[x] = s[x];

	}

	return;
}


void printArray( const int o[], const int m[], int s ) {

	// o -- original
	// m -- modified
	// s -- size

	cout << setw(9) << "original" << setw(8) << "sorted" << endl;
	cout << setw(9) << "--------" << setw(8) << "------" << endl;

	for (int i = 0; i <= s; i++){
		cout << setw(9) << o[i] << setw(8) << m[i] << endl;
	}

	return;
}

/*

  documentation in POD format suitable for pod2* programs found on most *nix systems

=head1 NAME

pa5a.cpp

=head1 SYNOPSIS

(Quicksort) In the examples and exercises of Chapter 4, we discussed the
sorting techniques of the bubble sort, bucket sort, and selection sort.
We now present the recursive sorting technique called Quicksort. The basic
algorithym for a single subscripted array of values is as follows:

a) Partitioning step:

    Take the first element of the unsorted array and determine its final
    location in the sorted array (i.e., all values to the left of the element
    in the array are less tan the element, and all values to the right of
    the element in the array are greater than the element). We now have one
    element in its proper location and two unsorted subaarays.

b) Recursive step:

    Perform step 1 on each unsorted subarray.

Each time step 1 is performed on a subarray, another element is placed in
its final location of the sorted array, and two unsorted subarrays are created.
When a subarray consists of one element it must be sorted. Therefore that
element is in its final location.

The basic algorythm seems simple enough, but how do we determine the final
position of the first element of each subarray? As an example, consider the
following set of values (the element in bold is the partitioning element--it
will be placed in its final location in the sorted array):

B<37> 2 6 4 89 8 10 12 68 45

a) Starting from the rightmost element of the array, compare each element
with B<37> until an element less than B<37> is found. Then swap B<37> and
that element. the first element less than B<37> is 12, so B<37> and 12 are
swapped. The new array is:

I<12> 2 6 4 89 8 10 B<37> 68 45

Element I<12> is in italic to indicate that it was just swapped with B<37>.

b) Starting from the left of the array, but beginning with the element after
12, compare each element with B<37> until an element greater than B<37> is
found. Then swap B<37> and that element. The first element grater than B<37>
is 89, so B<37> and 89 are swapped. The new array is:

12 2 6 4 B<37> 8 10 I<89> 68 45

c) Starting from the right, but beginnnig with the element before 89, compare
each element with B<37> until an element less than B<37> is found. Then swap B<37>
and that element. The first element less than B<37> is 10, so B<37> and 10 are
swapped. The new array is:

12 2 6 4 I<10> 8 B<37> 89 68 45

d) Starting from the left, but beginning with the element after 10, compare
each element with B<37> until an element grater than B<37> is found. Then swap
B<37> and that element. There are no more elements grater than B<37>, so when we
compare B<37> with itself, we know that B<37> has been placed in its final location
of the sorted array.

Once the partition has been applied on the array, there are two unsorted
subarrays. The subarray with values less than 37 contains 12, 2, 6, 4, 10,
and 8. The subarray with values grater than 37 contains 89, 68, and 45. The
sort continues with both subarrays being partitioned in the same manner as
the original array.

Based on the preceeding discussion, write a recursive function B<quickSort> to
sort a single-subscripted integer array. The function should recieve as
arguments an integer array, a starting subscript and an ending subscript.
Function B<partition> should be called by B<quickSort> to perform the partitioning
step.

=head1 ABSTRACT

This program implements a recursive function quickSort() to sort an array of
integers, as per the exercise. The array is initalized at compile time. The last
index of the array is fetched, and an interger array that will hold a copy
of the input is initalized. Next, the contents of the array to be sorted are
copied to the afformentioned array. Then the recursive function quickSort()
sorts the subject array. The result of the algorythm is then output to
the screen.

=head1 DESRIPTION

    void quickSort( int a[], int l, int r) {

        int p = 0;
	
        if (l < r ) { // if not, im done
            p = myPartition(a, l, r);
            quickSort(a, l, p - 1);
            quickSort(a, p + 1, r);
        }

        return;
    }

The function quickSort() is mainly a wrapper around the partition mechanism.
It also decides weather the subarrays are completely partitioned or not.

When quicksort is called and there is still work to do, myPartition() finds which
left-most element to work on.
MyPartition() then initializes a sentinel for the while() loop and an int variable
C<i> for use in for loops. The while loop is initialized to run until C<sentinel> evaluates to
false. Since C<sentinel> is odd, the if() part of the conditional is executed.

Initialize a loop, using left-most element of the (sub)array for comparison, starting from
the right-most element. Move "left" towards the "start" of the (sub)array, until
either a number less than the left-most element is encountered or the left-most
element is encountered.

If a number less than the left-most element is encountered,
swap the the left-most element and the element at index C<i>. Define the index to start at
for the next traversal through the (sub)array. Assign the position of the left-most
element (as defined above) as C<lmepos>. Incerement the sentinel so that the else()
part of the statement is ran the next time through the while() loop. There is no
more work to do in here, so break out of the for() loop.

The conditional is the
only statement inside the while() loop, So the condition of the while() loop
is evaluated again. This time C<sentinel> is odd, so the else() part of the
conditional is executed.

A for() loop is initalized, and C<i> is set to the next starting
position. This means that C<nsp> is now the current starting position. Move
"right" towards the "end" of the sub(array), until either a number greater than the
left-most element (as defined at the beginning of the subroutine) is encountered
or the left-most element is encountered.

If a number greater than the left-most element is encountered,
swap the the left-most element and the element at index C<i>. Define the index to use
for the next traversal through the (sub)array. Assign the position of the left-most
element as C<lmepos>. Incerement the sentinel so that the if() part of the
statement is ran the next time through the while() loop. There is no more work
to do in here, so break out of the for() loop.

Repeat this process until the left-most element is encountered during a for() in either
part of the conditional.

If the left-most element is encountered during a for() in either part of the conditional,
the left-most element is in its proper position in the (sub)array. Set C<sentinel> to
a false value and break out of the loop.

Retun the postion of the left-most
element( which probably isnt in the left-most postion anymore).

QuickSort() will then
repeat the above process on each of the (sub)array's subarrays, until each element
is found in its proper position during its first time through partition().


=head1 AUTHOR INFORMATION

    Todd Wade (waveright@gmail.com)

=head1 BUGS

unknown results if each element in the list is not unique. 100 elements
max. Unknown formatting result if an integer greater than 6 digits is
included in the list.

=cut

*/
```

---

### Post by hod139 on 2007-07-31
I've answered this question before on these forums: [http://ubuntuforums.org/showthread.php?t=399295](http://ubuntuforums.org/showthread.php?t=399295)

You could try doing your own homework.

---

