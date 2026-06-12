---
title: "beyond C++?"
date: 2010-10-30
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-30
I have a set of instances derived from a base class named "host".
I want to set a method that will be called for the instance when I visit it.

... but I can't work out how to express that in C++ :(

Here is what I tried... is this beyond the C++ language or just me being particularly dense atm?

[php]

// g++ visitor.cpp
#include <stdio.h>

struct host {
	typedef bool (host::*visitor)(void); // visitor method
	static visitor fVisit;

	bool operator ()(void) {
		if (!fVisit) return; // NULL action = do nothing
		return (this->*fVisit)();
	}

	// possible methods to choose from
	virtual bool see_me() {
		printf("seeing\n");
	}
	virtual bool touch_me() {
		printf("touching\n");
	}
	virtual bool feel_me() {
		printf("feeling\n");
	}
	virtual bool heal_me() {
		printf("healing\n");
	}
};

host::visitor host::fVisit = NULL;

int main() {
	host::fVisit = host::see_me;
	host sH;
	sH(); // do the specified action on this instance
	return !printf("all done\n");	
}
[/php]

---

### Post by GeneralZod on 2010-10-30
I'm not quite sure what you're after: something like this?

```


// g++ visitor.cpp
#include <stdio.h>

struct host {
    typedef bool (host::*visitor)(void); // visitor method
    static visitor fVisit;

    bool operator ()(void) {
        if (!fVisit) return false; // NULL action = do nothing
        return (this->*fVisit)();
    }

    // possible methods to choose from
    virtual bool see_me() {
        printf("seeing\n");
    }
    virtual bool touch_me() {
        printf("touching\n");
    }
    virtual bool feel_me() {
        printf("feeling\n");
    }
    virtual bool heal_me() {
        printf("healing\n");
    }
};

host::visitor host::fVisit = NULL;

int main() {
    host::fVisit = &host::see_me;
    host sH;
    sH(); // do the specified action on this instance
    return !printf("all done\n");    
}  

```

What is the desired output?

Edit: 

VVV

Oh, cool.  You're welcome :)

---

### Post by worksofcraft on 2010-10-30
> **GeneralZod said:**
> I'm not quite sure what you're after: something like this?
...
What is the desired output?

Yes... That's exactly what I wanted :)
TYVM

p.s. you are pretty good at this kind of stuff... well awesome actually ;)
just to show it works with virtual methods...
[php]

// g++ visitor.cpp
#include <stdio.h>

struct host {
	typedef bool (host::*visitor)(void); // visitor method
	static visitor fVisit;

	bool operator ()() {
		if (!fVisit) return false; // NULL action = do nothing
		return (this->*fVisit)();
	}

	// possible methods to choose from
	virtual bool see_me() {
		return !printf("seeing\n");
	}
	virtual bool touch_me() {
		return !printf("touching\n");
	}
	virtual bool feel_me() {
		return !printf("feeling\n");
	}
	virtual bool heal_me() {
		return !printf("healing\n");
	}
};

struct frog: host {
	bool see_me() {
		return !printf("ribbet\n");
	}
};

host::visitor host::fVisit = NULL;

int main() {
	frog sH;
	host::fVisit = &host::see_me;
	sH(); // do the specified action on this instance
	return !printf("all done\n");	
}
[/php]
and the output I wanted was in this case "ribbet" :shock:

---

### Post by SledgeHammer_999 on 2010-10-30
Just a simple question to **workofcraft**, why do you use "struct" instead of "class"? I have seen you doing it in other code examples too. I know that in C++ a struct is basically the same as a class, but I find it odd. The established standard is to use "class" for this type of objects.

---

### Post by worksofcraft on 2010-10-30
> **SledgeHammer_999 said:**
> Just a simple question to **workofcraft**, why do you use "struct" instead of "class"? I have seen you doing it in other code examples too. I know that in C++ a struct is basically the same as a class, but I find it odd. The established standard is to use "class" for this type of objects.

By default everything in a class is private.
follow this link to read my reason [when to use private and protected]("http://ubuntuforums.org/showthread.php?p=10018746#post10018746").

---

### Post by nvteighen on 2010-10-30
> **worksofcraft said:**
> By default everything in a class is private.
follow this link to read my reason [when to use private and protected]("http://ubuntuforums.org/showthread.php?p=10018746#post10018746").

First: A reference to [The Who's "See me, feel me"]("http://www.youtube.com/watch?v=m7AHblQ3_oM") in these forums!??

Second: Isn't it protected the default access setting? (Or maybe I'm confused with ObjC...)

Anyway, my impression is that in a language like C++, with such a complex syntax and way more complex semantics, the more explicit you are the better. Yes, we all know that a struct is a all-public class, but using the class keyword makes you explicitly use the access labels... 

The other issue is that people like me, who are much more used to C than to C++ have to read twice in order to switch from "C mode" to "C++ mode"... specially in your particular code snippets, where you use stdio.h instead of iostream... (by the way, you're doing it wrong, in C++, use **#include <cstdio>**... the reason is related to C++'s name mangling; ask someone more initiated in C++ than I am :P).

Ok, it's probably just a matter of style, but in such a language I do prefer the "public:" extra line is worth in order to make things clear.

---

### Post by worksofcraft on 2010-10-30
> **nvteighen said:**
> 
Anyway, my impression is that in a language like C++, with such a complex syntax and way more complex semantics, the more explicit you are the better. Yes, we all know that a struct is a all-public class, but using the class keyword makes you explicitly use the access labels...


Meh... IMO it has such a complex syntax *because* of all those keywords. However, when I see a private/protected member in my own code I know there is a reason behind that a bit like using underscores on names in Python: I'm trying to communicate with myself of the future... "don't forget to fulfill special conditions on this item".

I spent enough enough years programming to other people's standards, yes including compulsory Hungarian notation and rigid rules about capitalization and making nice little boxes of stars round the comments that had to be exactly so many characters wide and explicit where to put braces... and I'm confident all that code has long been wiped from cyber space because those businesses are no more :shock:

> **nvteighen said:**
> 
The other issue is that people like me, who are much more used to C than to C++ have to read twice in order to switch from "C mode" to "C++ mode"... specially in your particular code snippets, where you use stdio.h instead of iostream... (by the way, you're doing it wrong, in C++, use **#include <cstdio>**... the reason is related to C++'s name mangling; ask someone more initiated in C++ than I am :P).


Thanks for that reference... I never did get used to them dropping the .h (personally I preferred using .hpp suffix because no suffix is for folders and commands IMO). Anyway according to Stroustrup:

"With minor exceptions C++ is a superset of C."

That's the way I use it and **I never switch to "C++ mode"**. On a [thread about throwing instances]("http://ubuntuforums.org/showthread.php?p=10026992#post10026992") I did actually look at the full switch to using C++ type checked string composition as a replacement for C style formated error message, but apart from failing to make it work I just think it is such a convoluted way of thinking  :confused:

Whatever... I prefer the [pinball wizard]("http://www.youtube.com/watch?v=4AKbUm8GrbM") track by the Who :guitar:

---

### Post by dwhitney67 on 2010-10-30
> **worksofcraft said:**
> 
I spent enough enough years programming to other people's standards, yes including compulsory Hungarian notation and rigid rules about capitalization and making nice little boxes of stars round the comments that had to be exactly so many characters wide and explicit where to put braces... and I'm confident all that code has long been wiped from cyber space because those businesses are no more :shock:

Hmmm, and I wonder why?

---

### Post by worksofcraft on 2010-10-30
> **dwhitney67 said:**
> Hmmm, and I wonder why?

lol - I don't...

I'm **absolutely positive** it is because they spent more time and effort rigorously ensuring their hundreds of "weenies" were all adhering systematically to prevailing "industry programming standards" than actually producing something had a chance of working conceptually.

Naturally it was all coded to carefully crafted pseudo code which was systematically derived from assorted hierarchies of design documents... the production and maintenance of that I suspect has contributed to global deforestation. One of my bosses even had a huge structure chart of the complete project software covering a large office wall. It was updated about once a week, keeping a team of technical authors gainfully employed.

---

### Post by worksofcraft on 2010-10-30
However, that isn't really what this thread is about. Surprisingly, the reason I wanted said method pointer isn't to make a program that says "ribbit".

Instead this actually follows on from some other discussions about iterating graphs. Thus starting with a base class for generic graph facility I want to derive one that represents schematic drawings using affine transforms to place sub-diagrams within in diagrams of other shapes and already we have two algorithms for iterating :depth first and breadth first. I think graphically rendering a fractal diagram would really bring the difference to life... however I digress...

There are different operations one might do while itterating said graph... e.g. to draw it on the screen, or to find a particular node and delete it or move it, or add to it, or to read and write the whole lot to an XML file and so on, so rather than code all of them as separate iterations I just want to set a virtual method to be applied.

note: It's just an idea, IDK yet if it's a good idea :P
p.s. The wiki has articles about [visitor patterns]("http://en.wikipedia.org/wiki/Visitor_pattern#C.2B.2B_Example") and [double dispatch]("http://en.wikipedia.org/wiki/Double_dispatch"), but that way I can't do things like removing a node as the visitor action. However this is perhaps going a bit beyond the intention of my thread here.

---

### Post by worksofcraft on 2010-10-31
... you aren't going to believe this, but I've ended up having to write my own implementation of STL list template :shock:

and why on Earth would I have to do that you may wonder?
well it's like this...

I made this iterator iterate through my graph until I find a node I wanna delete from the graph.

STL list has an erase method and that method sure enough takes an iterator to say which one to delete... but that is still a method of a list instance.

Alas at this point all I have is said iterator and not the list which is somewhere in some parent node instance, so I can't call erase.

Making my own list template I can easily code it to extract the entry from whatever chain it is in... but why do I somehow always seem to end up having to rewrite standard libraries ??? :shock:

---

### Post by CptPicard on 2010-10-31
Would it have been possible to write your own iterator class that contains a reference to the underlying list and generally just delegates to an iterator you get from STL?

EDIT: Well, you'll probably have to maintain your own iteration state if you choose to write your own iterator, so that you can "fix" the iteration position when you remove elements from the underlying collection...

---

### Post by worksofcraft on 2010-10-31
> **CptPicard said:**
> Would it have been possible to write your own iterator class that contains a reference to the underlying list and generally just delegates to an iterator you get from STL?

EDIT: Well, you'll probably have to maintain your own iteration state if you choose to write your own iterator, so that you can "fix" the iteration position when you remove elements from the underlying collection...

Yes, that is a much better idea even if it does carry round an extra pointer to a list. I think it was the syntax that put me off trying that before, but its' not actually that bad in retrospect... and perhaps it could be written better too :)

[php]
// g++ cs_iterator.cpp
// an enhanced iterator for standard lists that identifies which list it is in.
#include <list>
#include <cstdio>

template<class T> struct cs_iterator: std::list<T>::iterator {
	std::list<T> *pInList; // identify the list I'm iterating
	cs_iterator & erase() {
		std::list<T>::iterator::operator=(pInList->erase(*this));
		return *this;
	}
	cs_iterator(std::list<T> &rL): std::list<T>::iterator(rL.begin()), pInList(&rL) {}
};

// diagnostic
void show(std::list<int> &iL) {
	for (std::list<int>::iterator iT = iL.begin(); iT != iL.end(); ++iT)
		 printf("%d, ", (*iT));
	printf("\n");
}

int main() {
	std::list<int> iL;

	// create some sample data
	for (int i = 1; i <= 10; ++i) iL.push_back(i);
	show(iL);

	cs_iterator<int> iT(iL); // iterate iL
	++iT; ++iT; // move to item #3

	// Thanks to CptPicard idea I can now erase element at the iterator
	// without having to know what standard list instance it is in !
	iT.erase();
	show(iL); // see #3 is gone :)

	return !printf("exits normally\n");
}
[/php]

---

### Post by dwhitney67 on 2010-10-31
There's a flaw in the design of your templated struct; however it is not your fault; it's just an inherent "gotcha" with C++.

Consider the case where the template type T of the list is a pointer to an object.  Erasing an item from list would always result in a memory leak (unless smart pointers were employed).

As for you handiwork, I cannot fathom why it would be of any practical use versus just passing the reference to the list along to where it is needed.  Passing around a "bucket" containing both the list and the iterator merely compresses the data into one object.  Woo-hoo.

---

### Post by worksofcraft on 2010-10-31
> **dwhitney67 said:**
> There's a flaw in the design of your templated struct; however it is not your fault; it's just an inherent "gotcha" with C++.

Consider the case where the template type T of the list is a pointer to an object.  Erasing an item from list would always result in a memory leak (unless smart pointers were employed).

As for you handiwork, I cannot fathom why it would be of any practical use versus just passing the reference to the list along to where it is needed.  Passing around a "bucket" containing both the list and the iterator merely compresses the data into one object.  Woo-hoo.

Well thanks for that pointer on pointers... of course it does happen that sometimes they don't point to something that is on the heap however I'll keep an eye on it :)

The reason the link is relevant is because I have an iterator class to  hierarchical container class. Well actually I have two different iterators to said container, one is a "breadth first" iterator and the other a "depth first" iterator and I want to be able to apply an erase and and insert at the current iteration.

However as you may have guessed, being a hierarchy, the current iteration can be positioned anywhere in **any of countless sub-containers** within said hierarchy.

Now I suspect you are fully aware that with plain old C style  pointer to a link in a C style doubly linked list it is trivial to unlink, or to insert at whatever element you are pointing to, regardless which "instance" of a list it is in.

Alas with STL lists we need to know which list it is as well as where in that list. Thus my iterator needs to include a pointer to the container within which it is currently iterating within the hierarchy.... so the above template is a base class to my hierarchy iterator.

Just to give concrete details... what I'm making is a generalization of what was [discussed about graphs]("http://ubuntuforums.org/showthread.php?p=10032351#post10032351") elsewhere:

This is a template of two classes, one the attributes of an "edge" and the other are the attributes of a "node".

With this template I create nodes that are containers of edges to other nodes plus some simple graphical primitives. The edges have an affine transform and a graphics context (color, pen tip, line style etc...) to place the node they refer to. IOW it's a graphical schematic tree and the iterator serves to draw it on the screen, or to find things and delete them or to dump it to an XML file or well whatever I want without having to code for internal details of said structure because it's all done by my generic graph template :guitar:

---

### Post by worksofcraft on 2010-11-01
ultimately I just could not get the proper C++ version to compile. I can see why people have to switch their mode of thinking and tbh I can see why some people don't like C++... I don't like using it "the proper way" either :P

So to make it actually work and able to delete a visited "edge" from the graph template, I had to stay with my own C style linked list.

I simplified my resulting template and included a noddy test main() for anyone who want to see first hand what the issues really are:
[php]
// g++ cs_graph.cpp
#include <list>
#include <cstdio>
#include <cstring>

// need to be able to unlink just given the link, so std:list is unsuitable
struct _cs_list {
	_cs_list *pNext, *pPrev;

	// circular list is easy to insert and delete from head and toe
	_cs_list() { pPrev = pNext = this; }

	// add new node as last element
	void append(_cs_list *pNew) {
		pNew->pNext = this;
		pNew->pPrev = pPrev;
		pPrev->pNext = pNew;
		pPrev = pNew;
	}

	// take link out of chain
	void unlink() {
		pPrev->pNext = pNext;
		pNext->pPrev = pPrev;
	}
};

// for diagnostics
unsigned gIdGen = 0; // generate sequential identifiers

// basic hierarchical graph, with a class for Edge attributes
// to define Node attributes, derive from the cs_graph::node class
// the edges are all unique and exist only in a list of children of a node
// The root is an exception just in a list of it's own
struct cs_graph: _cs_list {
	// double dispatch: visit the node, supplying data of this edge
	virtual bool visit() = 0;

	// a node has a bunch of "edges" to child nodes
	// Each edge is unique, but multiple edges can be to the same node.
	// Derive from this to add node attribute data.
	struct node: _cs_list {} *pNode;

	// constructor links to a node: Every edge should have one!
	cs_graph(node *pN): pNode(pN) {}

	// iterator classes
	struct _iter_base {
		std::list<cs_graph *> aL; // iteration to do list
		inline bool empty() { return aL.empty(); }
		inline bool visit() { return aL.front()->visit(); }
		inline cs_graph * operator*() { return aL.front(); }
		// front or back makes no difference when only one is in the list
		_iter_base(cs_graph *pRoot) { aL.push_front(pRoot); }
	};

	// breadth first iterator
	struct bfs_iterator: _iter_base {
		bfs_iterator(cs_graph *pRoot): _iter_base(pRoot) {}
		bfs_iterator & operator++();
	};

	// depth first iterator
	struct dfs_iterator: _iter_base {
		dfs_iterator(cs_graph *pRoot): _iter_base(pRoot) {}
		dfs_iterator & operator++();
	};
};

// breadth first iterator
// uses the list as a queue: current position is head of the queue
// to move forward, append all it's children to the queue then remove
// the one we just did
cs_graph::bfs_iterator & cs_graph::bfs_iterator::operator++() {
	if (!_iter_base::aL.empty()) {
		// append all it's edges to child nodes
		node *pNode = _iter_base::aL.front()->pNode;
		for (
			_cs_list *iT = pNode->pNext;
			iT != pNode;
			iT = iT->pNext
		) _iter_base::aL.push_back((cs_graph *) iT);
	}
	_iter_base::aL.pop_front(); // remove the one we just did (no going back!)
	return *this;
}

// depth first iterator
// uses the list as a stack: current position is on top of the stack
// to move forward pops the current then pushes all it's children (if any)
cs_graph::dfs_iterator & cs_graph::dfs_iterator::operator++() {
	cs_graph *pTop = _iter_base::aL.front(); // the one we just were at
	_iter_base::aL.erase(_iter_base::aL.begin()); // remove it
	// stack it's children in reverse order
	node *pNode = pTop->pNode;
	for (
		_cs_list *iT = pNode->pPrev;
		iT != pNode;
		iT = iT->pPrev
	) _iter_base::aL.push_front((cs_graph *)iT);
	return *this;
}

struct my_graph;
// derive node class(es) from the base class handled by the template
struct my_node: cs_graph::node {
	const char *pShape;
	my_node(const char *name): pShape(name) {}
	// visitor model
	virtual bool visit(my_graph &rEdge);
};

struct my_graph: cs_graph {
	int iD;
	virtual bool visit();
	my_graph(my_node *pNode): cs_graph(pNode), iD(gIdGen++) {} 
};

bool my_node::visit(my_graph &rEdge) {
	printf("visiting edge %u to node %s\n", rEdge.iD, pShape);
	return strcmp(pShape, "square");
}

bool my_graph::visit() {
	return ((my_node *) pNode)->visit(*this);
}

int main(int argc, char *argv[]) {
	my_node sNode[] = { "triangle", "square", "circle", "dodecahedron" };
	my_graph sRoot(&sNode[0]);
	my_graph sChild1(&sNode[1]);
	my_graph sChild2(&sNode[2]);
	my_graph sChild3(&sNode[3]);

	sNode[0].append(&sChild1);
	sNode[0].append(&sChild2);
	sNode[1].append(&sChild3);

	printf("breadth first\n");
	for (my_graph::bfs_iterator iT(&sRoot); !iT.empty(); ++iT) iT.visit();

	printf("depth first\n");
	for (my_graph::dfs_iterator iT(&sRoot); !iT.empty(); ++iT) {
		if (iT.visit()) printf("keep!\n");
		else {
			printf("remove the square and all it's kids!\n");
			(*iT)->unlink();
		}
	}

	printf("check no squares are left\n");
	for (my_graph::bfs_iterator iT(&sRoot); !iT.empty(); ++iT) iT.visit();

	return !printf("exits normally\n");
}
[/php]

enjoy - lol :P

---

### Post by dwhitney67 on 2010-11-01
All that code needs is a pinch of salt and some...

---

### Post by worksofcraft on 2010-11-01
> **dwhitney67 said:**
> All that code needs is a pinch of salt and some...
No doubt you think it would be trivial to use C++ std::list as the base class of such a general purpose hierarchical data structure instead of my C style version. However I suspect that if you actually tried you would fail dismally.

This is just like in my [thread about throwing with std::exception]("http://ubuntuforums.org/showthread.php?t=1605125&page=2") and producing a formatted error message that can optionally be intercepted and handled rather than reported: No doubt that is possible with Glib::ustring. However as a practical application I looked at implementing it that way to produce simple text. To include an rgb plane color mask expressed as 8 digit hexadecimal (something I actually needed at the time). I am convinced dogmatic pursuit of "the one true C++ way" would be utterly inappropriate to the task.

Now admittedly that cs_graph template is experimental code where I was exploring possible ways of structuring this. At one stage it was a template of two different classes:

[LIST]
[*]one for the edge attributes which in my application included an affine transform and a graphical context.

[*]the other for the node attributes which was essentially a container of graphical primitives.
[/LIST]

I'm wondering about whether I need to use a template at all, because I can add edge attributes in the same way I added node attributes: with inheritance. However the real and pivotal requirement is not just to iterate and draw the structure but to be able to insert and delete from it dynamically.

---

### Post by worksofcraft on 2010-11-02
... anyway indeed using [double dispatch]("http://en.wikipedia.org/wiki/Double_dispatch#Double_dispatch_in_C.2B.2B") as explained in the linked wiki the use of a template does become redundant. The big advantage is that all that iterator malarkey becomes common to any graph derivatives, but IDK if I got the wiki wrong because I can't get away from an unsafe C style type casting. I decided to put in the my_graph::visit method, because the constructor will only let me add my_nodes to my_graphs and so it's relatively safe ;)

Meh I shouldn't think anyone CBA to follow all that but writing it gets it clear in my own head and so I just replaced the code in previous post... so it's double dispatch instead of template :P

---

### Post by dwhitney67 on 2010-11-02
> **worksofcraft said:**
> No doubt you think it would be trivial to use C++ std::list as the base class of such a general purpose hierarchical data structure instead of my C style version. However I suspect that if you actually tried you would fail dismally.

You missed the point... with your "new" coding style, the code's appearance is abysmal.  Trying to decipher it is near impossible for anyone who has a life beyond that of sitting in front of a computer.

Day-in/day-out at work, I have decipher s/w that was written over 10-years ago by code monkeys whose code was not judged (ie not peer reviewed).  When I come home, and I read posting's like yours where the coding style makes it difficult to discern the intent of the code, I say just pour some sauce over it.

Don't take it personally, but your coding style sucks.  You are focused too much on how to make the code appear to your liking, that you have forgotten the purpose of code... and I presume that is to share it with others.  Who would want to use your code?

---

### Post by worksofcraft on 2010-11-02
> **dwhitney67 said:**
> You missed the point... with your "new" coding style, the code's appearance is abysmal.  Trying to decipher it is near impossible for anyone who has a life beyond that of sitting in front of a computer.

Day-in/day-out at work, I have decipher s/w that was written over 10-years ago by code monkeys whose code was not judged (ie not peer reviewed).  When I come home, and I read posting's like yours where the coding style makes it difficult to discern the intent of the code, I say just pour some sauce over it.

Don't take it personally, but your coding style sucks.  You are focused too much on how to make the code appear to your liking, that you have forgotten the purpose of code... and I presume that is to share it with others.  Who would want to use your code?

The purpose of my code on this thread has been to explore the different techniques of implementing the same functionality.

In this case a generic hierarchical data structure. IMO the difficult bit has been to allow operations such as unlink/insert from/to said hierarchy to be effected using the position given by an "iterator" of said hierarchy.

I looked objectively at using templates and I looked at using polymorphism and I looked at using STL containers or one of my own. 

When it comes to actually using this code in a project I split off the headers and keep anything that is not of general use hidden inside the object file. Thus all the application programmer sees are those very simple and clean class derivations from cs_graph and node.

The experimental version above is however intended to be compiled and debugged as a single entity and so it might look messy, but it's still not half as "sucky" as any of the standard library code IMO.

---

### Post by worksofcraft on 2010-11-04
I just thought some people might like to know what this about, so it's my research into recursive data structures:
[php]
	// create a triangle
	polyline *qTriangle = new polyline;
	qTriangle->push_back(coord(100, 40));
	qTriangle->push_back(coord(160, 140));
	qTriangle->push_back(coord(220, 40));

	// Testing recursive data structure:
	// in this shape place an instance of itself, but reduced in size
	graphplacement *qShrink = new graphplacement(*qTriangle, affine::scale(0.8));
	qTriangle->append(qShrink);
[/php]

Which when you call the iterator of the resulting data structure produces the attached image, although evidently I did need something to stop infinite iteration of the cycle:
[php]
	if (sScreenXform.sMatrix.det() < 0.005) return NULL;
[/php]

Just to clarify: There is only one triangle shape and it's coordinates are never changed.
It is placed as a node in a graph data structure.
The data structure has an "edge" back to itself and the property of that edge says to shrink the transformation that
places things on the screen.

So you see it's just for fun and maybe to make some cool 2D graphics games soon ;)

---

