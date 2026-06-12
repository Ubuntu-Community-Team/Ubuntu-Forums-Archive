---
title: "Interprocess communication"
date: 2008-11-02
forum: Programming Talk
---

### Post by whoelse on 2008-11-02
Hi to all out there, I have a problem.

I want to have something like a linked list in a C program. The list should only store a time value (long long int), and of course the link to the next node.

> 
typedef struct list_node {
	int64 time;
	struct list_node *next;
} llnode;


Would be easy, but the value time is coming from another process.
For all the other values I use shared memory, but as I do not know the size of the linked list (which is the reason I use linked lists) I cannot use shared memory.
So I tried to use pipes. I sent an integer value from process A to process B and process B just gets the time when something is found in the pipe. As this is happening in a loop a lot of repetions are causing process A to crash. It works for a couple of hundred, but somewhere after that it crashes. I assume that process B may be not fast enough to read all incoming data, or something like that.
Do I have to do anything special with the pipe so it can handle that much input? 
Are there any other options to transfer integer values from process A to process B? Or can is there some way to use a linked list by both processes?

Whoever reads this can feel free to check my other thread regarding the same program but caused by a different problem: [Stack Smashing]("http://ubuntuforums.org/showthread.php?t=965056") (therefore I hope its okay to open a new thread.)

---

### Post by Delever on 2008-11-02
Maybe you could communicate status of data transmission using shared memory (since you use it already)? And, to avoid race conditions, use semaphores?

I am not really sure, mind you, I am very new to this. Just a thought.

---

### Post by whoelse on 2008-11-02
I would have to predefine the size I need for the storage of the integers, but as it should be possible for this to increase with no end, I am clueless for now.

If I want to have it locally for 10 values, I would use a normal array,
if I want to have it locally for an infinite number of values, I would use a linked list,
If I want to have it for two processes for 10 values, I would use a shared memory array, 
but do I have to use if I want to have an infinite number of values for two processes?

---

### Post by pp. on 2008-11-02
Just stating that one of the processes crashes does not leave us with much information to analyze.

As someone already said, the process receiving the data could throttle the process sending the data so that it will be able to keep up with the data.

---

### Post by CptPicard on 2008-11-02
Either a shared linked list or array, and you need to make sure you synchronize properly when you are either reallocating/writing to your array, or manipulating your list. Welcome to the world of concurrent programming ;)

---

