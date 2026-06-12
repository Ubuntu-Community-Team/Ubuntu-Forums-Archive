---
title: "Circular references in C/C++ headers"
date: 2007-09-10
forum: Programming Talk
---

### Post by bluedalmatian on 2007-09-10
I asked a couple of weeks back about problems with infinite loops in the compiler caused by 2 C++ classes having references to each other's header files and was pointed in the direction of using

#ifndef H_DDRoute
  #define H_DDRoute
        //content of header here
#endif

This sure enough solved the infinite loop but Im getting errors from the compiler about classes being undefined which just doesnt make sense to me. 

For example my program has 4 classes in total all of which are very simple but have references to each other. 

The class diagram is here www2.simple.org/classes.pdf

The class Exchange compiles fine. The class's DDRoute, SnapshotCard and ServiceCode dont. 

Taking DDRoute as an example,  you'll see on the class diagram it has a pointer to Exchange and a pointer to SnapshotCard. SnapshotCard also has a pointer to DDRoute.

The header file for DDRoute is

#ifndef H_DDRoute
  #define H_DDRoute

#include "Exchange.h"
#include "SnapshotCard.h"

using namespace std;

class DDRoute
{

	protected:
		int id;
		int code;
		Exchange* dest_exch;
		SnapshotCard* snapshot;
		

	public:
		DDRoute();
		~DDRoute();
		int getID();
		void setID(int pk);
		int getCode();
		void setCode(int c);
		Exchange* getDestinationExchange();
		void setDestinationExchange(Exchange* e);
		SnapshotCard* getSnapshotCard();
		void setSnapshotCard(SnapshotCard* card);
		


};

#endif

When compiled GCC says:



andrew@p4-gw2k-black:~/Desktop/thg$ g++ ./DDRoute.cpp -c -I .
In file included from SnapshotCard.h:9,
                 from DDRoute.h:5,
                 from ./DDRoute.cpp:1:
ServiceCode.h:17: syntax error before `*'
ServiceCode.h:27: syntax error before `*'
ServiceCode.h:28: `SnapshotCard' was not declared in this scope
ServiceCode.h:28: `card' was not declared in this scope
ServiceCode.h:28: variable or field `setSnapshotCard' declared void
In file included from DDRoute.h:5,
                 from ./DDRoute.cpp:1:
SnapshotCard.h:24: `DDRoute' was not declared in this scope
SnapshotCard.h:24: parse error before `>'
SnapshotCard.h:41: parse error before `::'
SnapshotCard.h:45: `DDRoute' was not declared in this scope
SnapshotCard.h:45: parse error before `>'
SnapshotCard.h:46: `DDRoute' was not declared in this scope
SnapshotCard.h:46: `ddr' was not declared in this scope
SnapshotCard.h:46: variable or field `addDDRoute' declared void


I cannot see a reason for any of these errors. Its been given the headers for the other classes so why are they 'undefined' and also why is it moaning about methods that return void values.

The headers for the other 2 classes are at

www2.simple.org/SnapshotCard.txt

www2.simple.org/ServiceCode.txt


I appreciate I've given you a lot of stuff here but if anyone can help me fathom this out (im sure its something basic ive done wrong) I'd be happy to compensate your time through PayPal.

Thanks
Andrew

---

### Post by LaRoza on 2007-09-10
Use a forward declaration.

Quick Google search: [http://www-subatech.in2p3.fr/~photons/subatech/soft/carnac/CPP-INC-1.shtml](http://www-subatech.in2p3.fr/~photons/subatech/soft/carnac/CPP-INC-1.shtml)

Hope it helps!

---

### Post by tripokey on 2007-09-10
You need to forward declare the classes.

```
#ifndef H_DDRoute
#define H_DDRoute

#include "Exchange.h"
#include "SnapshotCard.h"

using namespace std;

//FORWARD DECLARATION BELOW
class SnapshotCard;

class DDRoute
{

protected:
int id;
int code;
Exchange* dest_exch;
SnapshotCard* snapshot;


public:
DDRoute();
~DDRoute();
int getID();
void setID(int pk);
int getCode();
void setCode(int c);
Exchange* getDestinationExchange();
void setDestinationExchange(Exchange* e);
SnapshotCard* getSnapshotCard();
void setSnapshotCard(SnapshotCard* card);



};

#endif
```

(i might be wrong has been some time since i coded in c++ now)

---

### Post by aks44 on 2007-09-10
As the others said, you need to use forward references.


**But**... really, 4 classes all referencing each other is usually a symptom of a bigger problem. Perhaps you may want to rethink your design in order to get rid of some of the dependencies?

---

### Post by bluedalmatian on 2007-09-12
spot on thanks

---

### Post by dwhitney67 on 2007-09-12
Not related, but remove the "using namespace std" from the header file(s).  In the one example you provided, not a single data type is from the "std" namespace.

Rule of thumb:  _Never_ put a "using namespace" statement in a header file.

---

### Post by Coyote21 on 2007-09-12
> **aks44 said:**
> As the others said, you need to use forward references.


**But**... really, 4 classes all referencing each other is usually a symptom of a bigger problem. Perhaps you may want to rethink your design in order to get rid of some of the dependencies?

Sure that seems spaghetti code, try to redefine your design, and group things that seem related in an common class. Also looking at your design, isn't SnapshotCard class with too many methods? Also if SnapshotCard already has an DDRoute and ServiceCode vector in his field, why does two classes need an reference to his parent class? If they've accessed only by SnapshotCard calls, the caller always knows, that an specific DDRout object and ServiceCode object, belong to an specific SnapshotCard.

---

### Post by Harry Zhang on 2012-01-29
> **LaRoza said:**
> Use a forward declaration.

Quick Google search: [http://www-subatech.in2p3.fr/~photons/subatech/soft/carnac/CPP-INC-1.shtml]("http://www-subatech.in2p3.fr/%7Ephotons/subatech/soft/carnac/CPP-INC-1.shtml")

Hope it helps!

Hey guy, thank you for your reference to the forward declaration, which really helps. :D

:P

---

### Post by howefield on 2012-01-29
Thread closed.

---

