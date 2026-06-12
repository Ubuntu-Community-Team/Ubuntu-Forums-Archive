---
title: "Issues with creating a dynamic number of objects (C++)"
date: 2011-09-09
forum: Programming Talk
---

### Post by OlyPerson on 2011-09-09
I have class wherein I want to create a variable number of another class, but I'm having issues and I'm not sure what part I'm doing incorrectly.  For my code, each 'Mechanism' should have anywhere from 0 to infinite* Degrees of Freedom (DOFs) and they should be stored in a map (unless someone has a better idea?) with the key being the ID of the DOF (e.g. JOINT1, JOINT2).

To do this I write:
```
/*!
 * 	@brief		Adds a DOF to the map in Mechanism with the ID of inDOFID.
 *	@param		int inDOFID
 *	@return		void
 */
void Mechanism::addDOF ( int inDOFID )
{
    if (!_jointMap.count(inDOFID))
    {
        _jointMap[inDOFID] = new DOF(inDOFID);
    }
}
```
Note that I wrote DOF too, which doesn't have any dynamically allocated memory.

When I compile this I get a... confusing error message.
```
g++ -g -Wall -pedantic -I./include -c -MT .srcobjs/src/Mechanism.o -MD -MP -MF .srcobjs/src/Mechanism.d src/Mechanism.cpp -o .srcobjs/src/Mechanism.o
src/Mechanism.cpp: In member function ‘void Mechanism::addDOF(int)’:
src/Mechanism.cpp:135: error: no match for ‘operator=’ in ‘((Mechanism*)this)->Mechanism::_jointMap.std::map<_Key, _Tp, _Compare, _Alloc>::operator[] [with _Key = int, _Tp = DOF, _Compare = std::less<int>, _Alloc = std::allocator<std::pair<const int, DOF> >](((const int&)((const int*)(& inDOFID)))) = (operator new(72u), (<statement>, ((DOF*)<anonymous>)))’
./include/DOF.h:10: note: candidates are: DOF& DOF::operator=(const DOF&)
In file included from /usr/include/c++/4.4/map:61,
                 from ./include/Mechanism.h:5,
                 from src/Mechanism.cpp:7:
/usr/include/c++/4.4/bits/stl_map.h: In member function ‘_Tp& std::map<_Key, _Tp, _Compare, _Alloc>::operator[](const _Key&) [with _Key = int, _Tp = DOF, _Compare = std::less<int>, _Alloc = std::allocator<std::pair<const int, DOF> >]’:
src/Mechanism.cpp:117:   instantiated from here
/usr/include/c++/4.4/bits/stl_map.h:450: error: no matching function for call to ‘DOF::DOF()’
./include/DOF.h:9: note: candidates are: DOF::DOF(int)
./include/DOF.h:5: note:                 DOF::DOF(const DOF&)
make: *** [.srcobjs/src/Mechanism.o] Error 1

```

I've tried making operator=, copy constructors, and assignment operators for DOF and Mechanism objects, but still get that error.  Any help would be appreciated, or advice, always trying to learn.





* Realistically no more than 6 as that is the number of degrees of freedom necessary to make any orientation and position of an end-effector possible, side fact

---

### Post by Senesence on 2011-09-09
Well, your map declaration should look something like this:

[PHP]std::map<int, DOF*> _jointMap;[/PHP]

Is that what it looks like?

---

### Post by OlyPerson on 2011-09-09
> **Senesence said:**
> Well, your map declaration should look something like this:

[PHP]std::map<int, DOF*> _jointMap;[/PHP]

Is that what it looks like?

WOW, I feel so stupid ](*,) Didn't realize/think about that "new" returned a pointer... derp.  Thank you!

Since this is solved I'll mark it as such, but I have another couple non-thread worthy questions I'd like to ask if that's alright?

With my code I'm trying to be as efficient as is possible as it needs to run in real time, any tips for keeping it fast?  Such as use only pass by reference or something like that?

---

### Post by Senesence on 2011-09-09
> **OlyPerson said:**
> WOW, I feel so stupid ](*,) Didn't realize/think about that "new" returned a pointer... derp.  Thank you!

Glad I was able to help!

> With my code I'm trying to be as efficient as is possible as it needs to run in real time, any tips for keeping it fast?  Such as use only pass by reference or something like that?

"Real time" means different things to different people: Are you talking about keeping things fast enough to feel interactive - like keeping a game running at 60 fps - or are you talking about something along the lines of "If this function doesn't return in the next 0.153 seconds, my rover dives into a canyon"?

The latter would require the system itself to make execution time guarantees - this is something that the modern Linux kernel is actually capable of, but it's something you'll have to research on your own (I never actually tried using that feature).

Whatever the case may be, I'm not much of a "speed" guy, so I can't really help you there.

I didn't even know that pass by reference is faster than just passing a pointer .... assuming that's true.

Sorry.

---

### Post by OlyPerson on 2011-09-09
> **Senesence said:**
> Glad I was able to help!



"Real time" means different things to different people: Are you talking about keeping things fast enough to feel interactive - like keeping a game running at 60 fps - or are you talking about something along the lines of "If this function doesn't return in the next 0.153 seconds, my rover dives into a canyon"?

The latter would require the system itself to make execution time guarantees - this is something that the modern Linux kernel is actually capable of, but it's something you'll have to research on your own (I never actually tried using that feature).

Whatever the case may be, I'm not much of a "speed" guy, so I can't really help you there.

I didn't even know that pass by reference is faster than just passing a pointer .... assuming that's true.

Sorry.

I'm talking about hard realtime running at 1000Hz- I'm working with a haptics device and that's the accepted resolution for realistic haptic perception.  I have a kernel patch installed (RT Preempt) that handles the timing portion of it, I just need the program to run as quickly as possible, lending the most processor time to the graphical process (it's an old computer).

I was being ambiguous with the reference to references, I just meant using references/pointers in place of, say, passing a double by value.  I already have larger classes passed by reference/pointers, but just curious if it'd be worth it for other values.

That was just one example though, I've been reading up on C++ efficiency but could always use more references and ideas :)

---

### Post by Senesence on 2011-09-09
Oh, I see.

Well, I may have a bit of useful advice in this case, even though I'm not a speed guy:

Use arrays where ever possible, instead of typical container types like linked lists. It's easier for the processor to guess what you're going to fetch when dealing with objects that are in contiguous memory; usually, if the array is small enough, the processor can get it into cache in a single fetch, and even if not, it's makes it easier for the system to guess what data you're going to touch next, and then pre-fetch that.

So, large, pre-allocated chunks of contiguous memory are usually better for speed - I've been told many times.

---

### Post by OlyPerson on 2011-09-09
Hmmm, I gave that some thought but didn't think it mad THAT big of a difference, maybe I should just use arrays instead of a Map for storing the objects, I would just have to specify in the API that ID's need to be between 0-7 (which is probably all they'd need to be for now as that's how many encoders are on the board).  /selfrant

I think I'll do that!

---

### Post by OlyPerson on 2011-09-09
> **Senesence said:**
> Oh, I see.

Well, I may have a bit of useful advice in this case, even though I'm not a speed guy:

Use arrays where ever possible, instead of typical container types like linked lists. It's easier for the processor to guess what you're going to fetch when dealing with objects that are in contiguous memory; usually, if the array is small enough, the processor can get it into cache in a single fetch, and even if not, it's makes it easier for the system to guess what data you're going to touch next, and then pre-fetch that.

So, large, pre-allocated chunks of contiguous memory are usually better for speed - I've been told many times.


Ok, I've run into a hole in my knowledge while doing this.  Previous I had done the following (not exactly, but basically this):
```

... in header
private:
	Force *	_force;
	Position * _position;
...

... in cpp file
	_force = new Force();
	_position = new Position();
...
```
Which would create the Force and Position objects in the heap yes?  What if I change it to:
```
... in header
private:
	Force 	_force;
	Position  _position;
...
```
Then just use them as normal objects in the class.  Are they in the stack then (and therefore faster to reference)?

---

### Post by Senesence on 2011-09-09
> **OlyPerson said:**
> Ok, I've run into a hole in my knowledge while doing this.  Previous I had done the following (not exactly, but basically this):
```

... in header
private:
	Force *	_force;
	Position * _position;
...

... in cpp file
	_force = new Force();
	_position = new Position();
...
```
Which would create the Force and Position objects in the heap yes?


Yes.

> What if I change it to:
```
... in header
private:
	Force 	_force;
	Position  _position;
...
```
Then just use them as normal objects in the class.  Are they in the stack then (and therefore faster to reference)?

They are allocated on the stack, yes, but I don't know if that would make it faster; both the stack and the heap are just pieces of DRAM reserved by the OS, so read/write speed should be the same, because it's the same kind of memory, just used differently.

But, I don't really think you should waste your time on stuff like this, at least not in the beginning.

I mean, if there were any differences from either allocating in the stack or the heap (in terms of speed), it would be largely irrelevant when compared to the speed difference between contiguous memory (which the processor can easily pre-fetch) and multiple levels of indirection which make efficient caching more difficult.

However, all of that would be completely irrelevant if your base algorithms are inefficient. So doing something in O(n!) that can actually be done in constant time is one example - it's very unlikely that any level of hardcore optimization could actually make the former situation faster (or you could do it, but you would probably end up in some crazy sublevel of hell, where no one else can possibly understand what you did, and you find it troublesome to make even trivial changes, because everything is so specialized for speed).

My overall advice regarding optimization: Don't do it until it becomes absolutely necessary.

Use linked lists (if they fit in as a convenient structure) and maps, and whatever else helps to make the code more readable, and the implementation more natural.

Then, if things are not fast enough, profile, profile, profile -> Usually there are a few "hot" areas that require deeper levels of optimization, so find them, and then direct your focus there.

But not before then.

---

