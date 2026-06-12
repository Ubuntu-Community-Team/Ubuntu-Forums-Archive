---
title: "C++memory allocation/freeing"
date: 2007-07-27
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-07-27
Hey all,

Just a question about how memory get allocated/freed in C++.

I am doing a particle engine (for the fireworks demo), and the particles are stored in a linked list.  Each node gets deleted when the particle dies, but the demo still gobbles up memory like there's no tomorrow when it's running.  Quitting the program seems to give back all the memory to system though.  I would have thought deleting allocated objects would free the memory on the spot, right?  (I guess if this is the case, I have a memory leak somewhere which I just can't find!)

This is really doing my head in- I've been re-coding, debugging this issue for ages!

Any help?  suggestions?

My kill_particle function...
```

void MyParticles::removeParticle(_node *kill_node)
{
	// Check for invalid node
	if (kill_node == NULL)
	{
		printf("NULL node- can't destroy\n");
		return;
	}
	
	// Kill node is only node
	if (start_ptr == end_ptr)
	{
		delete kill_node;
		start_ptr = NULL;
		end_ptr = NULL;
		return;
	}
	
	// Kill node is first node
	if (start_ptr == kill_node)
	{
		start_ptr = kill_node->next;
                delete kill_node;
		return;
	}
}

```

This is called with...
```

	// Cull the dead
        _node *iter = start_ptr;
	while (iter != NULL)
	{
		_node *next_node = iter->next;
		if (iter->life <= 0) removeParticle(iter);
		iter = next_node;
	}

```

---

### Post by Wybiral on 2007-07-27
If you want to post the source up somewhere I can help you look for the leak.

I would say to use a vector if you haven't tried, but I've always got better profiles from custom lists for particles then C++'s containers (though C++'s don't require as much thought when it comes to implementing).


EDIT:

Don't let go of the kill pointer even if it's the first particle in the list!

Also, what happens when it's not the first or the only one?

---

### Post by hod139 on 2007-07-27
In addition, you are deleting a copy of the pointer.  C++ defaults to pass by value.  When you pass the pointer to that function, C++ copies the pointer, and then you delete the copy.  Try passing by reference 
```
removeParticle(_node* &kill_node)
```

---

### Post by slavik on 2007-07-27
> **AlexThomson_NZ said:**
> Hey all,

Just a question about how memory get allocated/freed in C++.

I am doing a particle engine (for the fireworks demo), and the particles are stored in a linked list.  Each node gets deleted when the particle dies, but the demo still gobbles up memory like there's no tomorrow when it's running.  Quitting the program seems to give back all the memory to system though.  I would have thought deleting allocated objects would free the memory on the spot, right?  (I guess if this is the case, I have a memory leak somewhere which I just can't find!)

This is really doing my head in- I've been re-coding, debugging this issue for ages!

Any help?  suggestions?

My kill_particle function...
```

void MyParticles::removeParticle(_node *kill_node)
{
	// Check for invalid node
	if (kill_node == NULL)
	{
		printf("NULL node- can't destroy\n");
		return;
	}
	
	// Kill node is only node
	if (start_ptr == end_ptr)
	{
		delete kill_node;
		start_ptr = NULL;
		end_ptr = NULL;
		return;
	}
	
	// Kill node is first node
	if (start_ptr == kill_node)
	{
[SIZE="5"][COLOR="Red"]//WHERE IS DELETE? YOU ARE CHANGING start_ptr WITHOUT FREEING![/COLOR][/SIZE]
		start_ptr = kill_node->next;
		return;
	}
}

```

This is called with...
```

	// Cull the dead
        _node *iter = start_ptr;
	while (iter != NULL)
	{
		_node *next_node = iter->next;
		if (iter->life <= 0) removeParticle(iter);
		iter = next_node;
	}

```

emphasis for easier viewing :)

---

### Post by AlexThomson_NZ on 2007-07-27
Thanks Slavik, there is a 'delete' command there, I must have accidently removed it during the cut+paste, I'll corrent the original post now

---

### Post by AlexThomson_NZ on 2007-07-27
> **Wybiral said:**
> If you want to post the source up somewhere I can help you look for the leak.

I would say to use a vector if you haven't tried, but I've always got better profiles from custom lists for particles then C++'s containers (though C++'s don't require as much thought when it comes to implementing).

Also, what happens when it's not the first or the only one?

Here is the structure of my node:
```

		struct _node {
			_vector direction;
			_color  color;
			_position position;
			int		life;
			_node *next;
		};

```

Well spotted about that is doesn't delete middle nodes! - however  this is the 3rd rewrite, and I haven't yet put this in because in theory, even if it deletes just the first node, it should eventually clear the whole list and the memory be fully returned

---

### Post by AlexThomson_NZ on 2007-07-27
> **hod139 said:**
> In addition, you are deleting a copy of the pointer.  C++ defaults to pass by value.  When you pass the pointer to that function, C++ copies the pointer, and then you delete the copy.  Try passing by reference 
```
removeParticle(_node* &kill_node)
```

That would certainly explain all the symptoms!  I'll have a look into this now...

---

### Post by AlexThomson_NZ on 2007-07-28
Ok, I haven't had any luck with this at all, so I thought I might just submit the whole codebase (it's pretty small) and hope some kind soul can spend a minute or two going through finding why the memory is not getting freed properly.

As hod mentioned, it is probably freeing temporary objects rather than the actual ones, but I can't really see why, as I am passing a pointer to node and deleting what it points to (as far as I can see).  I tried putting double-pointers and &'s in, but confused myself too much, and was just pretty much guessing as it got a bit convoluted.  I tried following your code too Wybiral, but again the ** pointers were a bit much for my tiny brain.

Thanks for your help so far guys :)

// Damn I hate not being able to work these things out myself!  This should be so simple in theory!

---

### Post by AlexThomson_NZ on 2007-07-28
BTW- that's not my demo submission- just the framework around the particle engine

Press F1 to start the engine, and watch your memory dry up...

---

### Post by the_unforgiven on 2007-07-28
C++ doesn't have garbage collection built into the language - there are garbage collector libraries available, they are sold separately by the tools vendors though.

Did you try running it through [valgrind]("http://www.valgrind.org")?
That should point out if you have leaks.

---

### Post by AlexThomson_NZ on 2007-07-28
Thanks for the suggestion unforgiven.  I was aware that there is no inherant GC like Java.

I tried Valgrind too- and deleting the nodes does make a difference to the stats given at the end, however while running, whether the 'delete's' are there or not, memory use hits 100%

---

### Post by AlexThomson_NZ on 2007-07-28
Output from Valgrind if anyone's interested.  This is after generating nodes until 50% of memory is used, then clearing the whole list.

==13308== LEAK SUMMARY:
==13308==    definitely lost: 446 bytes in 4 blocks.
==13308==    indirectly lost: 120 bytes in 10 blocks.
==13308==      possibly lost: 25,932 bytes in 723 blocks.
==13308==    still reachable: 78,226 bytes in 2,593 blocks.
==13308==         suppressed: 0 bytes in 0 blocks.
==13308== Reachable blocks (those to which a pointer was found) are not shown.

---

### Post by slavik on 2007-07-28
here is one of my queue implementations (not one of the best or effecicient)
```

/*
 *      ll.h	a very simple queue called linked list
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail.com>
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 */

#ifndef _queue_
#define _queue_ 1

#include <malloc.h>

//individual node 'class'
struct _node {
	int pid;
	struct _node * next;
};

//the ll 'class'
typedef struct _list {
	struct _node * head;
}list;

	#ifdef DEBUG
	//prints the list if debug is enabled :D
	//see? I do learn new things :D
	void ll_print(struct _list * ll) {
		if (ll == NULL) return;
		struct _node * trav = ll->head;
		while (trav != NULL) {
			printf("%d ",trav->pid);
			trav = trav->next;
		}
		printf("\n");
	}
	#endif

//adds a new node onto the listpointed to by ll
int ll_add(struct _list * ll, int pid) {
	struct _node * travel = ll->head;
	struct _node * new_node;

	//special case if list is empty
	if (ll->head == NULL) {
		new_node = (struct _node *)malloc(sizeof(struct _node));
		if(new_node == NULL) return 0;
		new_node->pid = pid;
		new_node->next = NULL;

		ll->head = new_node;
		return 1;
	}

	//find end of the list (this is inefficient,
	//but I didn't want to maintain a 'tail'
	while (travel->next != NULL) {
		travel = travel->next;
	}

	//allocate new node and check that it was actually allocated
	new_node = (struct _node *)malloc(sizeof(struct _node));
	if(new_node == NULL) return 0;

	//set up the new node with proper info
	new_node->pid = pid;
	new_node->next = NULL;

	travel->next = new_node;
	return 1;
}

//remove first element
int ll_remove(struct _list * ll) {
	struct _node * t = ll->head;
	int pid = -1;
	if(t == NULL) return pid;
	pid = t->pid;
	ll->head = t->next;
	free(t);
	return pid;
}

//clears the list completely
void ll_clear(struct _list * ll) {
	while(ll->head != NULL) ll_remove(ll);
}

//allocates a new list :)
struct _list * ll_list(){
	struct _list * ret;
	ret = (struct _list *)malloc(sizeof(struct _list));
	ret->head = NULL;
	return ret;
}
#endif

```

---

### Post by MrHippocampus on 2007-07-28
Your definatley leaking stuff from your code, valgrind picks up leaks from all over the place from things like X and SDL, but this one is your problem:

```

==4809== 34,608 bytes in 721 blocks are still reachable in loss record 74 of 75
==4809==    at 0x4A2048C: operator new(unsigned long) (in /usr/lib64/valgrind/amd64-linux/vgpreload_memcheck.so)
==4809==    by 0x401B82: MyParticles::addParticle() (in somedemo/demo)
==4809==    by 0x401647: program_loop() (in somedemo/demo)
==4809==    by 0x401772: main (in somedemo/demo)

```

Ill try and have a look to see whats going on.

edit: You have no destructor for your class to handle when the class is destroyed, that means any particles left flying around when you exit wont be deleted!

edit2: Ah, I think I know what the problem is :D ill make a new post for it

---

### Post by MrHippocampus on 2007-07-28
Right, firstly the code which you posted.

It had two main problems, the first was you haddn't implemented deleting the middle of a linked list, ive edited the code and put this in for you with comments so you can see how it works (my implementation is inefficient, theres a better way of doing it if you think about it).

The second was that you have no deconstructor, this means when the particles class is destroyed when the program ends, theres nothing which takes care of deleting all of the remaining particles. To help illustrate this ive added a "refcount" variable to your particles class, it gets incremented by 1 every time a particle is created by new, and gets decremented by 1 every time a particle is deleted.
If you run the program, create loads of particles, let them all disappear and then quit, youll notice that the variable ends up at 0. That means there have been an equal number of new/delete's and thats what we want :).
If you run the program, create loads of particles but then quit before they dissapear the variable ends up with 200 (or some high positive number) which means particles have been created by new, but not deleted.

Just google for deconstructors and you should find out enough information to create one and take care of all those lost little particles :)


Anyway, the reason why I think your program is using huge amounts of memory is down to your use of openGL.

Warning, my openGL is a bit rusty :/

Your using glNewList to create your list of particles every loop, this is not what glNewList is for. glNewList is a way to store a load of operations/instructions (like rotations and verticies) in one place to be reused again and again, so e.g. I would create a cube out of triangles once in a glNewList and then if I wanted to use that cube again I would just use the List instead of doing all of the triangle commands.

What you should be doing is not using a glNewList but simply drawing the the particles as you already have (except without the list stuff that is).


Hopefully some of that helps :), I apologise in advance if anything is unclear.

---

### Post by Wybiral on 2007-07-28
OK, just looked at the source. Here's the biggest problem I can find with why you haven't figured it out... You're trying to remove a node from a singly linked list. Suppose we had this linked list:

A->B->C->D

We have a pointer to B and we decide that we want to delete it...

If we free up B, how do we change A's "next" pointer to C?

We can't because B doesn't know where A is.

You need to use a doubly linked list so that each node knows the previous and next nodes, this way when you remove one, you can patch up the list correctly.

---

### Post by the_unforgiven on 2007-07-28
We all seem to agree that your list implementation needs loads of improvement. :D
First off, I think it would be much easier if you use a doubly-linked list instead of a singly-linked list. Addition of one pointer hardly takes any space and the overhead is worth it - it allows you to browse the list in both directions ;)

Secondly, as MrHippocampus pointed out, you have forgotten to delete the GL list - particlesObj.
That is where it seems to leak a lot of memory; for every screen update, it creates a new list without deleting the earlier one.

I have zero experience of OpenGL, so I don't know what's the right way of handling display lists. :(

I'm attaching a diff to your original code; adding only the display list deletion code. I haven't gotten time to work on the other design aspects of the code, but I think there is room for improvement there too - as everybody pointed out, you don't have dtors. ;)

So, here comes the quick fix that seems to make the code a bit more responsive and remove the major memory leak. ;)

HTH ;)

PS: One more option I can think of is using threads: one for calculating particle properties, one for handling screen updates.
Also, I didn't see and GLUT code, so linking to glut library was useless. My Makefile patch removes this.

---

### Post by Wybiral on 2007-07-28
OK, here is how I would fix it. I kept your code as in-tact as possible and commented any parts that I did change.

Basically I rendered it in place and implemented a doubly linked list.

It's all working now, no leaks.

The reason I took the display lists out is that building them is time consuming, so it doesn't help unless you can pre-render them... And with a dynamic particle system you can not.

---

### Post by slavik on 2007-07-28
SDL cleans up all memory upon exit ... :(

---

### Post by AlexThomson_NZ on 2007-07-28
Hey, just got all the replies.  Thanks so much for all the help- especially those that took the time to sift their way through my hackish code!

Absolutely rapt to see memory use idle at 1.4% you made my day!

// now I can get on with some real coding, wohoo:)

---

### Post by hod139 on 2007-07-28
> **Wybiral said:**
> 
It's all working now, no leaks.

I haven't looked at any code, (I might later tonight) but there are still leaks (among other problems).  I have attached the output of valgrind.

---

### Post by MrHippocampus on 2007-07-28
The question is how many of those leaks are from the program itself and not the libraries its using?


I worked with a 3D engine once and valgrind said something along the lines of

"Over 1000000 errors have been logged, I will stop logging now, to disable this limit......"

And that was only when my code was only just initalising the engine.

---

### Post by the_unforgiven on 2007-07-29
> **MrHippocampus said:**
> The question is how many of those leaks are from the program itself and not the libraries its using?


I worked with a 3D engine once and valgrind said something along the lines of

"Over 1000000 errors have been logged, I will stop logging now, to disable this limit......"

And that was only when my code was only just initalising the engine.
The point is that valgrind seems to be based on defensive programming techniques - for example, it logs an error whenever an uninitialized variable is used anywhere in the code; it logs an error whenever using uninitialized variable in conditional jumps etc. 
And the libraries (especially Xlib) have plenty of code that still uses a lot of uninitialized code (albeit, it gets initialized before use, but not at declaration/definition).
That's why, I believe, we get tons of error messages while running code linked to such libraries.
I haven't found any major memory leak in any of these libraries though - most of them result from our code only.

---

### Post by hod139 on 2007-07-29
Sorry about the false alarms with valgrind.  After looking more closely at the output (like I should have the first time) they errors are all related to libSDL.

---

### Post by Wybiral on 2007-07-29
It shouldn't leak... Well... It should... But not accumulatively. The entire particle system class needs a destructor that removes all the remaining particles from the list, but the particle spawn/kill methods shouldn't be leaking anything.

I was only concerned with his main problems... Regenerating the display list each frame and the accumulative particles lost when the pointer was changed without freeing it.

NEEDS DESTRUCTOR.

---

### Post by AlexThomson_NZ on 2007-07-29
Yeah it seems the thing that really chewed the memory was recreating the display list each frame.  I don't know why I thought that would be a good idea (other than consistancy with my 3d objects in my helper classes).  No doubt mem was lost by not free-ing pointers too, but nowhere near like the display list thing was causing.

---

### Post by Wybiral on 2007-07-30
> **AlexThomson_NZ said:**
> Yeah it seems the thing that really chewed the memory was recreating the display list each frame.  I don't know why I thought that would be a good idea (other than consistancy with my 3d objects in my helper classes).  No doubt mem was lost by not free-ing pointers too, but nowhere near like the display list thing was causing.

Well, it was leaking the particles with the first source you posted because you didn't have any way to handle them when they weren't on the ends of the list (it was impossible to delete something in the middle without a leak).

The display lists... You were using glGenLists each frame... Think of this like a "new" or "malloc" of display lists. So it would have kept making new lists when you only needed one for the particle system. You might want to look into glDeleteLists. But you can use the same list multiple times, just don't generate it multiple times.

But display lists are going to make things worse in a situation like this. Building them is time consuming, then you have to call to render them... It's just as easy to render them on the spot.

Display list's magic is mostly useful for static scenes that you can build once and render multiple times. But with a dynamic scene where you're building and rendering the dl each frame, it's not going to help out any.

---

