---
title: "Way to insert element into start of C pointer."
date: 2011-08-19
forum: Programming Talk
---

### Post by J05HYYY on 2011-08-19
Hello,

I know how to place an element to the end of a buffer (or pointer array) by reallocing and inserting, but I want to be able to append an element to the start. Is there an easy way of doing this w/o shifting each element one place for instance by changing where the pointer points to? I am using C.

Thanks.

---

### Post by karlson on 2011-08-19
> **J05HYYY said:**
> Hello,

I know how to place an element to the end of a buffer (or pointer array) by reallocing and inserting, but I want to be able to append an element to the start. Is there an easy way of doing this w/o shifting each element one place for instance by changing where the pointer points to? I am using C.

Thanks.

Not really.  You can allocate the new buffer.  Copy the buffer into the new buffer offset by 1 element insert the element into new buffer at offset 0 and free the old buffer.

The thing you might want to consider is to use a data structure other then a contiguous array.

---

### Post by Bachstelze on 2011-08-19
```

void *prepend(void *buf, int oldsize, unsigned char c)
{
    unsigned char *res = malloc(oldsize+1);
    memcpy(res+1, buf, oldsize);
    res[0] = c;
    free(oldbuf);
    return res;
}
```

---

### Post by J05HYYY on 2011-08-19
Thumbs up for the swift replies. :KS

Would I be correct in saying that using memcpy on a pointer copies the the reference to the data but not the actual data itself?

---

### Post by Bachstelze on 2011-08-19
> **J05HYYY said:**
> 
Would I be correct in saying that using memcpy on a pointer copies the the reference to the data but not the actual data itself?

No, it copies the data (that's why you have to specify the number of bytes to copy).

---

### Post by J05HYYY on 2011-08-19
Hmm, that's a problem, I want to try and avoid copying the actual data. :/

---

### Post by Bachstelze on 2011-08-19
> **J05HYYY said:**
> Hmm, that's a problem, I want to try and avoid copying the actual data. :/

Then you're out of luck. As karlson said, you might want to use a more sophisticated data structure like a linked list, but it might not play well with the kind of data you need to manipulate.

---

### Post by J05HYYY on 2011-08-19
Alrighty, cheers anyway

If I find a way I'll let yous know but otherwise I will copy the data as you suggested.:popcorn:

---

### Post by J05HYYY on 2011-08-19
Here's my attempt at soft copying; it works, kinda.

```
#include <stdio.h>
#include <stdlib.h>
int main(void){
	int *pointerBufferOne = malloc(sizeof(int)*5);

		int index;
		for (index=0;index < 5;++index)
		{
			pointerBufferOne[index] = index + 2;
			printf("%d",pointerBufferOne[index]);
		}
		printf("\n");

	int *pointerBufferTwo = malloc(sizeof(int)*6);
	pointerBufferTwo = pointerBufferOne - 1;
	pointerBufferTwo[0] = 1;

	pointerBufferOne[0] = 9; //check to make sure it doesn't hard copy values;

		for (index=0;index < 6;++index)
		{
			printf("%d",pointerBufferTwo[index]);
		}
		printf("\n");

	pointerBufferOne = pointerBufferTwo;
	pointerBufferTwo = NULL;
	free(pointerBufferTwo);

		for (index=0;index < 6;++index)
		{
			printf("%d",pointerBufferOne[index]);
		}
		printf("\n");
}
```

Output:
```
23456
193456
193456
```

You'll notice that I set pointerBufferTwo to NULL before freeing, I think this is because "pointerBufferTwo - 1" is really an invalid pointer, so free complains. If I wanted to free pointerBufferOne at the end, I would have to do the same.

It's nasty trickery, which shows just how clever gcc can be in regards to circular buffers. Not sure if it'll work for other compilers. Suggestions are welcome.

---

### Post by Bachstelze on 2011-08-19
Well, this is obviously wrong, but I have the feeling that you don't care, so whatever. Enjoy your segfault when you will get one.

Everyone else, please don't do that.

---

### Post by karlson on 2011-08-19
> **J05HYYY said:**
> Here's my attempt at soft copying; it works, kinda.

```
#include <stdio.h>
#include <stdlib.h>
int main(void){
	int *pointerBufferOne = malloc(sizeof(int)*5);

		int index;
		for (index=0;index < 5;++index)
		{
			pointerBufferOne[index] = index + 2;
			printf("%d",pointerBufferOne[index]);
		}
		printf("\n");

	int *pointerBufferTwo = malloc(sizeof(int)*6);
	pointerBufferTwo = pointerBufferOne - 1;
	pointerBufferTwo[0] = 1;

	pointerBufferOne[0] = 9; //check to make sure it doesn't hard copy values;

		for (index=0;index < 6;++index)
		{
			printf("%d",pointerBufferTwo[index]);
		}
		printf("\n");

	pointerBufferOne = pointerBufferTwo;
	pointerBufferTwo = NULL;
	free(pointerBufferTwo);

		for (index=0;index < 6;++index)
		{
			printf("%d",pointerBufferOne[index]);
		}
		printf("\n");
}
```

Output:
```
23456
193456
193456
```

You'll notice that I set pointerBufferTwo to NULL before freeing, I think this is because "pointerBufferTwo - 1" is really an invalid pointer, so free complains. If I wanted to free pointerBufferOne at the end, I would have to do the same.

It's nasty trickery, which shows just how clever gcc can be in regards to circular buffers. Not sure if it'll work for other compilers. Suggestions are welcome.

This code is wrong on so many levels.

1.  After allocating buffer 2 you assign the pointer to be buffer1 - 1.  This means that you have just leaked memory you have allocated for buffer 2.
2.  When you set buffer2 to be buffer1 - 1 you set it to invalid pointer, which can crash the program
3.  You assign pointer to NULL before freeing it, which means you are freeing nothing.  You should free then assign.  Which also means you have just leaked memory for buffer1.

I suggest you install valgrind and run your program through it.

---

### Post by Arndt on 2011-08-20
> **J05HYYY said:**
> Hmm, that's a problem, I want to try and avoid copying the actual data. :/

If this operation of prepending is done often, copying all the data will be a real bottleneck.

I suggest allocating more than you need and placing the data in the middle, keeping track of how much free space you have at the front. Then you don't need to shift the data so often.

Something like

```
char *m = malloc(1000);
int front = 100;
char *str = m + front;
strcpy(str, "ello");
```

Now prepending consists of doing
```
if (front > 0) {
  str--;
  str[0] = 'H';
} else {
malloc and copy
}
```

I've assumed here that the data are characters, so you would want them to be contiguous, but if they are for example pointers to something, you can make this into a circular buffer, where prepending at the start consists of putting it at the end. Then you only need to copy when the data exceed the original allocation in size.

---

### Post by ofnuts on 2011-08-20
> **J05HYYY said:**
> 
    ```
int *pointerBufferTwo = malloc(sizeof(int)*6);
    pointerBufferTwo = pointerBufferOne - 1;

```You'll notice that I set pointerBufferTwo to NULL before freeing, I think this is because "pointerBufferTwo - 1" is really an invalid pointer, so free complains.
Yes, because you clobbered it. I don't see the purpose of allocating it to lose the value returned in the next line? Freeing "null" pointer does nothing, so the memory you originally allocated for pointerBufferTwo is lost and you have a memory leak.

If you want two arrays with some overlap, allocate them this way:
```

int *pointerBufferTwo = malloc(sizeof(int)*6);
pointerBufferOne = pointerBufferTwo + 1;

```(this in no way endorses the rest of your code...)

And at the end: 
```

    pointerBufferOne = pointerBufferTwo;

```Just ensure that pointBufferOne is now pointing outside the allocated memory (now pointerBufferOne-1) so you won't be able to free it either.

> **J05HYYY said:**
> It's nasty trickery, which shows just how clever gcc can be in regards to circular buffers. Not sure if it'll work for other compilers. Suggestions are welcome.It's not GCC which is clever, it's you that don't understand some basic things about pointer and memory allocation. On the whole, if you want to be a good coder, be modest, the folks who designed C and C++ as well as those who write and maintain are several light-years ahead of you (and most of us here) in their understanding of computers and programming languages, so if something doesn't work like you expect it's likely that you have the wrong expectations.

---

### Post by nvteighen on 2011-08-20
Please, learn about linked lists (they're trivial to implement and do what you want) or try implementing Arndt's suggestion. One should never rewrite a pointer returned by a call by malloc(), except in the case that you're rewriting that pointer with the value returned by realloc()... which you're not.

---

### Post by Bachstelze on 2011-08-20
> **nvteighen said:**
> Please, learn about linked lists (they're trivial to implement and do what you want)

Will not work on evrything, though. What if for example I want to compute the SHA hash of the buffer with e.g. OpenSSL?

---

### Post by nvteighen on 2011-08-20
> **Bachstelze said:**
> Will not work on evrything, though. What if for example I want to compute the SHA hash of the buffer with e.g. OpenSSL?

Of course, linked lists are not the Holy Grail of programming, but IMO they serve the OP's purpose.

---

### Post by Bachstelze on 2011-08-20
> **nvteighen said:**
> Of course, linked lists are not the Holy Grail of programming, but IMO they serve the OP's purpose.

That's funny because OP has never said what his purpose was. ;)

---

### Post by nvteighen on 2011-08-20
> **Bachstelze said:**
> That's funny because OP has never said what his purpose was. ;)

Wasn't it "Way to insert element into start of C pointer"? And by judging his less than acceptable code, it seemed to me that he was referring to pushing an object to a list's head. Something like a regular cons'ing.

---

### Post by ofnuts on 2011-08-20
> **nvteighen said:**
> Wasn't it "Way to insert element into start of C pointer"? And by judging his less than acceptable code, it seemed to me that he was referring to pushing an object to a list's head. Something like a regular cons'ing.He also mentioned circular buffers, and I don't see anything in the OP's code that could hint at them.

---

### Post by nvteighen on 2011-08-20
> **ofnuts said:**
> He also mentioned circular buffers, and I don't see anything in the OP's code that could hint at them.

Very true :|

Why do some people make threads that are plainly incomprehensible? We're glad to help here, but none of us is a psychic AFAIK.

---

### Post by J05HYYY on 2011-08-20
Yes, the code I gave was clearly bad, like I said, twas nasty trickery.

The other suggestions sound interesting, assigning more memory than initially needed and using a linked list.

Problem is that I need the data to be indexed, so a linked list won't really work ... I'm trying to make a music sequencer with adjustable start and end points and need to be able to read from a certain 'beat'.

I mentioned circular buffers because I expected to free the original buffer. If the free worked, the pointer to the information in the original buffer would have vanished and so the second buffer should have also been corrupted. Little did I know, what I was actually freeing was null and thus the data was still there when printing it out.

I guess the normal way of doing things is what I wanted to avoid in the first place and tbh I think that's better than allocating more memory than needed, especially when working with big audio buffers. Or alternatively I could start working in C++ and use vectors.

It's a shame there is no function for appending to the start in C w/o copying. I'm sure it can be done with pointers (properly) somehow but clearly, it's beyond me.

---

### Post by karlson on 2011-08-20
> **J05HYYY said:**
> Yes, the code I gave was clearly bad, like I said, twas nasty trickery.


Wouldn't be quite the term I'd use

> 
The other suggestions sound interesting, assigning more memory than initially needed and using a linked list.

Problem is that I need the data to be indexed, so a linked list won't really work ... I'm trying to make a music sequencer with adjustable start and end points and need to be able to read from a certain 'beat'.


So why not use a hash map with a linked list?

> 
I guess the normal way of doing things is what I wanted to avoid in the first place and tbh I think that's better than allocating more memory than needed, especially when working with big audio buffers. Or alternatively I could start working in C++ and use vectors.


You might want to take a look at the implementation of C++ vector.  All it does it just hides the copy from you.

> 
It's a shame there is no function for appending to the start in C w/o copying. I'm sure it can be done with pointers (properly) somehow but clearly, it's beyond me.

As I have said earlier you might want to consider using a linked list and a hashmap to generate indexed list of "beats" so you have fast access.

---

### Post by ofnuts on 2011-08-20
> **J05HYYY said:**
> 
Problem is that I need the data to be indexed, so a linked list won't really work ... I'm trying to make a music sequencer with adjustable start and end points and need to be able to read from a certain 'beat'.
Ok, so you need your music to be put inside a buffer, and be able to read starting with some index !=0. Nothing more...

> **J05HYYY said:**
> 
I mentioned circular buffers because I expected to free the original buffer. 
I fail to see the connection between the two concepts.

> **J05HYYY said:**
> 
 I guess the normal way of doing things is what I wanted to avoid in the first place and tbh I think that's better than allocating more memory than needed, especially when working with big audio buffers. 
This is where you design can take advantage of behavior specific to your app. If you think there is a good chance to often increase the music size by less than 10%, you can allocate buffers with these 10% extra, that may avoid deallocation/reallocation later. You can even leave some free space in the buffer head to handle the "nice" cases of insertions without having to move the existing buffer contents.

> **J05HYYY said:**
> 
  It's a shame there is no function for appending to the start in C w/o copying. I'm sure it can be done with pointers (properly) somehow but clearly, it's beyond me.
Of course, a SMOP, for others. Maybe that if that function doesn't exist, it's because it cannot be done?

---

### Post by J05HYYY on 2011-08-20
> **karlson said:**
> You might want to take a look at the implementation of C++ vector.  All it does it just hides the copy from you.

Didn't know this, that is poor.

> **karlson said:**
> So why not use a hash map with a linked list?

Won't I have to update the hash map every time a beat is added, ie. cycling through all the hashes and updating them :confused:

 - If so, I might as well do on the buffer instead.

---

### Post by J05HYYY on 2011-08-20
> **ofnuts said:**
> Ok, so you need your music to be put inside a buffer, and be able to read starting with some index !=0. Nothing more...

No, I already have my music (events) in a buffer and I want be able to append or add more music (events) to the beginning w/o copying.

> **ofnuts said:**
> This is where you design can take advantage of behavior specific to your app. If you think there is a good chance to often increase the music size by less than 10%, you can allocate buffers with these 10% extra, that may avoid deallocation/reallocation later. You can even leave some free space in the buffer head to handle the "nice" cases of insertions without having to move the existing buffer contents.


It's not an ugly way of doing things but it's not good either. I have many buffers recorded at 44100 samples per second and with several tracks I could run out of space pretty quickly, especially on rubbishy computers and handheld devices.

> **ofnuts said:**
> Of course, a SMOP, for others. Maybe that if that function doesn't exist, it's because it cannot be done?

Maybe.

---

### Post by Arndt on 2011-08-21
> **J05HYYY said:**
>  I already have my music (events) in a buffer and I want be able to append or add more music (events) to the beginning w/o copying.



Can you give some hard (estimated) data about the memory and speed requirements? When you have a buffer A and want to prepend a piece B, how large are A and B typically? How often (times per second) is the buffer A read? How often will the prepending have to be done? How many times will the operation be done? Do you ever cut away pieces again?

Is it char buffers we are talking about, by the way? The suggestions have been about all sorts of data. You say music events, does that mean a pointer to data, a small piece of data itself, or something large?

---

### Post by GeneralZod on 2011-08-21
C++'s std::deque offers (amortised?) O(1) addition to the end or beginning of a vector, and O(1) random-access of elements.

---

### Post by karlson on 2011-08-21
> **GeneralZod said:**
> C++'s std::deque offers (amortised?) O(1) addition to the end or beginning of a vector, and O(1) random-access of elements.

That claim would certainly depends on the implementation details of deque.

---

### Post by J05HYYY on 2011-08-21
I've worked out how I can do it in C.

I have two actual buffers, one for the start and one for the end. First I read the start buffer backward and then I read the end buffer forward.

---

### Post by karlson on 2011-08-21
> **J05HYYY said:**
> I've worked out how I can do it in C.

I have two actual buffers, one for the start and one for the end. First I read the start buffer backward and then I read the end buffer forward.

Humor me on this but why not have a linked list keeping a count of the number of elements inserted then when you want to play it you allocate an array of pointers to those elements and traverse it in the indexed fashion?

I mean creating a heap and a stack may be overcomplicating a problem.

---

### Post by J05HYYY on 2011-08-21
> **karlson said:**
> Humor me on this but why not have a linked list keeping a count of the number of elements inserted then when you want to play it you allocate an array of pointers to those elements and traverse it in the indexed fashion?

I mean creating a heap and a stack may be overcomplicating a problem.

I guess the benefit of this would be that I could add elements half way through. The downsides, previously discussed, is that I'd have to keep a hash table and update it if I wanted to play from the 'middle' of a track.

---

### Post by karlson on 2011-08-21
> **J05HYYY said:**
> I guess the benefit of this would be that I could add elements half way through. The downsides, previously discussed, is that I'd have to keep a hash table and update it if I wanted to play from the 'middle' of a track.

I don't see you avoiding a shifting of elements since adding an item in the middle of the combined buffer will require shifting of either 1 or other buffer.

---

### Post by J05HYYY on 2011-08-21
> **karlson said:**
> I don't see you avoiding a shifting of elements since adding an item in the middle of the combined buffer will require shifting of either 1 or other buffer.

Most probably - at least without doing something complicated.

---

### Post by ve4cib on 2011-08-21
Just to toss another idea out there, what about some kind of modified B+ tree structure instead of the buffer?  You'd have a normal tree (with O log n insert/delete times anywhere in the structure), and the leaf nodes form a circular linked list, allowing you to run through them like a buffer/array one node at a time.

The inserts would be faster than shifting an entire array, but the search time would drop from O(1) to O(log n), which may or may not be a serious issue for this application.  The other tricky bit would be indexing the data so the tree is searchable in a reasonable fashion.

---

### Post by J05HYYY on 2011-08-21
> **ve4cib said:**
> Just to toss another idea out there, what about some kind of modified B+ tree structure instead of the buffer?  You'd have a normal tree (with O log n insert/delete times anywhere in the structure), and the leaf nodes form a circular linked list, allowing you to run through them like a buffer/array one node at a time.

The inserts would be faster than shifting an entire array, but the search time would drop from O(1) to O(log n), which may or may not be a serious issue for this application.  The other tricky bit would be indexing the data so the tree is searchable in a reasonable fashion.

I was thinking about doing this for when inserting some data whilst the buffer is being simultaneously read, then when the user clicks stop, the data can be shifted in the usual way to create a flat buffer again.

---

### Post by ofnuts on 2011-08-22
> **J05HYYY said:**
> I've worked out how I can do it in C.

I have two actual buffers, one for the start and one for the end. First I read the start buffer backward and then I read the end buffer forward.

If you are doing this (ie keep the data in several buffers), there is an even simpler solution: keep all the music segments as individual buffers, and manage them in a list of  start_pointer/length. And when you need to insert something in the middle of an existing buffer, just replace that buffer entry by two: 

[phpcode]
struct {
  int *start
  int length
} buffer

struct buffer original,half1,half2;

/* split original buffer at sample N */
half1.start=original.start;
half2.length=N;

 half2.start=original.start+N;
half2.length=original.length-N;
[/phpcode]

and then insert the buffer entry with you new data between the two halves. You can use a similar technique to delete stuff (but don't return the memory!).

Just keep on the side a second list of all the memory buffers for memory management (pointer to original allocation, plus counter to handle splits as above and avoir returning  a buffer when part of it is still used)

---

### Post by J05HYYY on 2011-08-22
No doubt I will be keeping data in several (more than two) buffers when the music is being edited and at the same time, being played. I will be using minus values to point to a different buffer.

The problem with several buffers though is that indexing becomes a pain. Random access gets extremely complicated, if not, impossible. So, as soon as the music has stopped, I will be able to shift the data around and be able to flatten it out, hopefully making things easier.

---

### Post by ofnuts on 2011-08-22
> **J05HYYY said:**
> No doubt I will be keeping data in several (more than two) buffers when the music is being edited and at the same time, being played. I will be using minus values to point to a different buffer.

The problem with several buffers though is that indexing becomes a pain. Random access gets extremely complicated, if not, impossible. So, as soon as the music has stopped, I will be able to shift the data around and be able to flatten it out, hopefully making things easier.

Random access isn't that complicated (walk down the list of buffers, adding the buffer length) and definitely not impossible. And your program only does random access on the first sample, the rest is sequential (until the end of that buffer).

---

### Post by J05HYYY on 2011-08-22
> **ofnuts said:**
> Random access isn't that complicated (walk down the list of buffers, adding the buffer length) and definitely not impossible.

I guess it depends on how you define random.

> **ofnuts said:**
> And your program only does random access on the first sample, the rest is sequential (until the end of that buffer).

True, at least for playing but not for the other necessary things such as event selection and viewing, using the gui.

---

