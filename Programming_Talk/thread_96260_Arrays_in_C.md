---
title: "Arrays in C"
date: 2005-11-28
forum: Programming Talk
---

### Post by rock freak on 2005-11-28
hi there guys this may seem liek s strange question but my mind is total mush today(typical monday) and i cant rember for my life how to assign enteries into a int array

basically i want to put a randomly generated number into a array of 7 numbers so that each of them are different!!

any help will be great

Ollie

---

### Post by ofek on 2005-11-28
How about doing a "for" loop from i=1 to i<=7 with jumps of 1 (i++) that will get a random number and put it in array[i].
Thats the concept I use, but you gotta understand you need to  include headers for the arrays and random numbers.

---

### Post by rock freak on 2005-11-28
cheers the for loop worked and my mind seems to be working again (as much as it does hehe)

cheers

---

### Post by rock freak on 2005-11-28
```

int main(){

	int numbers[7];

	printf("%5d\n", numbers);

	return(0);
	
}
```

this returns a stupidly high negative number i mean in the billions at least

i no there is summit wrong but what!!!

---

### Post by gord on 2005-11-28
two things; 
when you create an array in c, you are basically using up the memory on your computer, that memory is reused by many applciations and thus isn't clean, so your left with whatever the program used it lasts data in that memory space, ie; garbage.

also the namspace 'number', is actually just a pointer to where the memory is located, you can't just use 'number' and hope it prints out the whole shu-bang, the best you could do with that is *number which would just print out the first item in the array.

you need to make sure you assign a number to each item in the array (even if it is just '0') and to print out the whole array youd either have to make a for loop that prints them out one at a time or;
numbers[0]
numbers[1]
numbers[2]
numbers[3]
...
...
...

---

### Post by Chuck Adams on 2005-11-28
When you statically create an array in C (that is, you don't malloc it), it will usually be zeroed out unless you compile with optimizations.  

Static arrays are easy:
int x[] = {1, 2, 3, 4, 5, 6, 7};

Notice you don't need the size.  The compiler gets it from the initializer. Even cooler is C99 struct initializers, but that's another topic.  Note that the values have to be constants, you can't initialize the members with variables (unless they're themselves constants) or a function.

Really though, if you're doing a lot with arrays, it's a good time to learn C++ if only just to use STL.  You don't have to do one bit of classes or anything else, but once you start using std::vector, you will never want to go back to arrays.

---

### Post by rock freak on 2005-11-29
must of just been that monday muind i had lol i looked at it first thign this morning and did it straight of! 

but not to sure how the best way to do the next section i want to do is! i need to make sure that when making the random numbers and putting them intoa  array that there isnt a duplicate number like therre arnt two number 34's in the array so that they are all different??!!!!

i weas thinking about a while loop of if statements!!

any ideas would be great cheers

---

### Post by David Marrs on 2005-11-30
Here's an untested (and buggy)* algorithm that uses loops to achieve what you want. It should be fine for a small collection of data like array[7], but for larger stuff you should check out sorting algorithms. There was a thread on this subject earlier this week.

```
for(i=0; i<7; i++){
  rnd = random_number();  /* pseudo code */  
  for(j=0; j<i; j++){
    if(rnd == numbers[j]){
      printf("Number %d already exists", rnd);
      return(EXIT_FAILURE);
    } else
      numbers[i] = rnd;
  }
}
```
*I've made at least one mistake in the code, but I'll leave you to work out what it is. :)

---

