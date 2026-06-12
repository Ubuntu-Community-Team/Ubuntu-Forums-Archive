---
title: "C++, pointers to arrays, and segmentation faults"
date: 2010-10-02
forum: Programming Talk
---

### Post by SavantStrike on 2010-10-02
So I'm currently stumped on a programming assignment that I just cannot seem to make any headway on, and things are getting desperate as it's due soon and there are other problems on the assignment which are more complicated (and build on this one).

The prof wants me to create an int[] array in memory, referenced by a pointer, and controlled by an integer variable "size". I've spent hours trying to get this to work, and it just doesn't want to work.

The problem is I need to be able to add to this array. Either I need to make it larger than it should be so I can add to it, or I need to do a deep copy to copy it to another array, deallocate it, and then create it again, adding the data back in plus an extra integer.

The two offending functions are as follows

```

void List::printall(){
		int counter = 0;
		while (counter <= size){
			cout << (ptr + counter) << " ";
			counter++;
		}
		cout << endl;
}

```

```

void List::add(int x){
	if (ptr == NULL){
		ptr = new int[size];
		ptr[size] = x;
	}
	else{

		int *tmpPointer = new int[size];

		//deep copy values in pointer to tmpPointer
		for(int i=0; i<size; i++){
		*(tmpPointer + i) = *(ptr + i);
		}

		delete [] ptr;
		size++;

		//reallocate pointer to point to a larger array
		ptr = new int[size];

		for(int i=0; i<size; i++){
			ptr[i] = tmpPointer[i];
		}
		ptr[size] = x;
		cout << "pointer array from inside add function: ";
		for(int i=0; i<=size; i++){
			cout << *(ptr + i) << " ";
		}
		cout << endl;
	}
}

```

It runs like this, but not right. The integer's are added to the array, and printing the pointers without the * dereference operator shows that there are memory addresses being pointed to. However, when I try to use * in the printall function to print human readable text, I get a segmentation fault. 

Any suggestions? I would be the first suggestion would be not to use pointers to an array in memory, but it's required ](*,).

Thanks in advance!

---

### Post by dwhitney67 on 2010-10-02
It's hard to read your code without the CODE tags; please edit your post.

As for arrays in C++ (*shudder*), they are cake to implement.  Here's an example:
```

const size_t N = 5;

// declare and allocate array
int* array = new int[N];

// use array (ie populate with values)
for (size_t n = 0; n < N; ++n)
{
   array[n] = n+1;
}

// destroy array
delete [] array;
array = 0;

```


P.S.  Here's a bug in your code:
```

while (counter **<=** size){

```
That should be *less-than*, not *less-than-or-equal*.

---

### Post by SavantStrike on 2010-10-02
> **dwhitney67 said:**
> It's hard to read your code without the CODE tags; please edit your post.

As for arrays in C++ (*shudder*), they are cake to implement.  Here's an example:
```

const size_t N = 5;

// declare and allocate array
int* array = new int[N];

// use array (ie populate with values)
for (size_t n = 0; n < N; ++n)
{
   array[n] = n+1;
}

// destroy array
delete [] array;
array = 0;

```


P.S.  Here's a bug in your code:
```

while (counter **<=** size){

```
That should be *less-than*, not *less-than-or-equal*.


Err, sorry, I should have put those code tags in all along. I'm going to digest what you've just said now. Thanks :)

And you're right, there is a bug in the print function. How embarassing :oops:

Is the way I declared the array for tmpPointer that much different than what you just showed? 

I feel like I'm missing something here. The pointers can be dereferenced to print a real value inside the add function, but by the time they get to the print function, it's like they are no longer in memory..

---

### Post by psusi on 2010-10-02
You appear to be allocating a new array TWICE for no good reason.

---

### Post by dwhitney67 on 2010-10-02
> **psusi said:**
> You appear to be allocating a new array TWICE for no good reason.

Now that the OP's code is clearly readable, I could not agree more with your assessment.

The OP should also be aware that for an array of size N, the indices needed to access the data range from 0 to N-1.  It appears that he is intent on using N to index into the array, which is a no-no.

---

### Post by SavantStrike on 2010-10-02
> **psusi said:**
> You appear to be allocating a new array TWICE for no good reason.

The prof states we must access the array with the original pointer...

I was doing it twice so I could perform a deep copy, deallocate, and reallocate one larger, then do a deep copy of the temporary array into the array referenced by the pointer the prof wanted us to use.

As for the accessing to N, I'm a bit embarassed to say I hadn't realized I couldn't do that.

Edit: Hot dang, problem solved!!!

Don't I feel dumb now. My whole problem was trying to access up to element N in the array. The first element starts at 0... I cannot believe I was so thick headed. Thank you all for your help!!!

solution

```

void List::printall(){
		int counter = 0; //temporary counter used for printing the elements of the array referenced by ptr
		while (counter < size){ // loop which runs from 0 to N where j is the last element of the array referenced by ptr
			//and n is the element of the array at the position "counter"
			cout << *(ptr + counter) << " ";//print out the value of array[n]
			counter++; //increment counter to the next position in the array
		}//all of the elements in the array that ptr references have been printed to the screen
		cout << endl;
}

```

```

void List::add(int x){
	if (ptr == NULL){
		size++;
		ptr = new int[size];
		ptr[(size-1)] = x;
	}
	else{

		int *tmpArray = new int[size];

		//deep copy values in pointer to tmpPointer
		for(int i=0; i<size; i++){
		tmpArray[i] = *(ptr + i);
		}

		delete [] ptr;

		size++;

		//reallocate pointer to point to a larger array
		ptr = new int[size];

		for(int i=0; i<(size-1); i++){
			ptr[i] = tmpArray[i];
		}

		ptr[(size-1)] = x;

		delete[] tmpArray;
	}
}

```

---

### Post by Some Penguin on 2010-10-02
> **SavantStrike said:**
> The prof states we must access the array with the original pointer...

I was doing it twice so I could perform a deep copy, deallocate, and reallocate one larger, then do a deep copy of the temporary array into the array referenced by the pointer the prof wanted us to use.
[/code]

Uh, "same pointer" might mean "same pointer", not "same variable", in which case your allocate / copy / deallocate method is incorrect.

---

