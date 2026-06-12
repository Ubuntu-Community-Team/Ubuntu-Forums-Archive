---
title: "32bit memory management &amp; global vs local pointers for linked lists"
date: 2009-09-05
forum: Programming Talk
---

### Post by aatyler on 2009-09-05
EDIT: I found the problem this time for good, it had nothing to do with anything i posted.....just shoot me. 
 
EDIT: Below is the relevant information. The question simply is: (should have written this in the first place)
 
if I have a global pointer, and a locally declared pointer, and I set the local pointer = the global pointer, will any changes in the local pointer be reflected in the global pointer?
 
Again, sorry for not starting the post this way in the first place.....
 
**************Long post for those interested*********************
 
Hello all, thanks in advance for the help!
 
Ok, heres the computer setup:
 
ASUS EEEpc 1000-ha
1 gig of ram
has the (single core as far as I can tell, though system info lists 2 cores) intel ATOM N270 1.6 Ghz
running EEEbuntu with ubuntu 9.04
kernel: Linux 2.6.29-1-netbook
Compiler: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Language of code: C 
compiling options w/ gcc : -ggdb3 -Wall -lncurses <source...> (I doubt these options are causing my bug......but who am I to fathom the whims of the great gcc?)
 
The bug:
 
I am writing a roguelike game and using a linear, singly linked-list, with a global head-node pointer for all the items (food, weapons, etc...etc...) in my game. In one of my functions I iterate through the list and load any items in the current room (as defined by a global struct that stores the player location / info) into a static, global array (type int). The problem is that it loads the items all fine and dandy but in the process the whole item list gets lost (through more checking that I'll explain at the end of this post, I've developed the theory that the local pointer is changing the value of the global pointer). the start of my function that does the check looks like this:
 
```

struct item* currentitem; /* pointer local to the function and will refer to the head NODE */
 
currentitem = firstiteminlist; /* set to global headnode refference */

```
 
then, i use a while loop does the following:
 
```

while (currentitem != NULL)
{
    if (currentitem->y == y && currentitem->x == x && currentitem->id != 0)
    {
          itemsincurrentroom[counter] = currentitem->id;
          ++counter;
    }
    currentitem = currentitem->next;
}

```
 
The only thing I want this function to do is go through the list, process it by loading any items it finds that matches the coordinates i pass by value to the function into a global array that is initialized to zero every time this function loads, but leaves the head-node ptr (the global one) intact.
 
Now, I know that the problem lies somewhere in the above code because I have done an itterative dump of the item linked-list to a file before and after the above while loop. Before the loop the list is still intact, however, after the loop, the global head reference (firstiteminlist) is NULL. 
 
One final fact, I have two computers that I work on, when I compile this code on a 64-bit install of Ubuntu 9.04 (sorry I don't have the GCC version off the top of my head with that comp. and I'm away from it right now) with an intel dualcore processor, it functions as I want it to, only on the EEEPc will it compile and some how lose the list. 
 
* the reasons I make the assumption that the local pointer is changing the information in the global is:
 
1) I declared another pointer called headREF of the same type, local to this function
2) I set it to equal the value of the firstieminlist global pointer before I run the while loop.
3) after the while loop ends I set the global pointer equal to the local pointer (assuring that the head pointer is again refering to the head node)
 
and this fixed the bug......but Im still lost as to why I needed to do that. Am I just lost on the concepts of linked lists? I have other functions that use the same while loop setup on the SAME global pointer / linked list that are called before this function and they work just fine.... is this possibly something that is hardware / software related? IE the EEEpcs memory management is different than for ubuntu on the dual core? or maybe I just don't know what I'm doing...lol.
 
Well, even though I fixed the bug I still want to understand it a bit better, thanks again for the help! 
 
PS if someone wants I can email / post the full source but its nearly 800 lines long and has debugging printfs/file writes all over the place and is broken into 3 files + a header, but, if it will help, ill gladly post it.
 
 
Adam

---

