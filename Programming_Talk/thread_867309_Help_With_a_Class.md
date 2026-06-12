---
title: "Help With a Class"
date: 2008-07-22
forum: Programming Talk
---

### Post by loganwm on 2008-07-22
In my pursuit of learning C++ I've attempted a few programs so far based loosely on the tutorials from cprogramming.com, I'm currently working on learning how to sort out classes, and I'm still a bit lost on a few topics.

Here's my code:
```
//Simple ATM
//Logan M.
//Class demonostration

#include <iostream>

using namespace std;

float total=1000;
float x=0;

class atm {
	public:
		void deposit(int amount);
		void withdraw(int amount);
		float checkbalance();
};

//function to deposit money
void atm::deposit(int amount) {
	total = total + amount;
}

//function to withdraw money
void atm::withdraw(int amount) {
	if (amount <= total) {
		total = total - amount;
	}
}

//function to check account balance
float atm::checkbalance() {
	return total;
}

int main() {
	//
	atm myatm;
	cout<<"Current Balance: " << myatm.checkbalance() << endl;
	cout<<"Deposit: ";
	cin>>x; myatm.deposit(x);
	cout<<"Current Balance: " << myatm.checkbalance() << endl;
	cout<<"Withdraw: ";
	cin>>x; myatm.withdraw(x);
	cout<<"Current Balance: " << myatm.checkbalance() << endl;
}
```

I read about the classes on this page [[http://www.cprogramming.com/tutorial/lesson12.html]](http://www.cprogramming.com/tutorial/lesson12.html]) and I need to know about class **constructors** and **deconstructors.** All help is appreciated! Feel free to criticize the code as you see fit, I'm learning, so any input is great.

---

### Post by dribeas on 2008-07-22
[QUOTE=loganwm;5438432]Here's my code:
```
//Simple ATM
#include <iostream>

using namespace std;

float total=1000;
float x=0;

class atm {
	public:
		void deposit(int amount);
		void withdraw(int amount);
		float checkbalance();
};

```

First things first OOP is about encapsulating into a class data and operations. In the example above data is outside of the class and not encapsulated at all.

You'll probably want something like:
```

// .h
class BankAccount
{
public:
   explicit BankAccount( double openingDeposit = 0 );
//   ~BankAccount(); // default destructor is good enough, no need to provide it here

   void deposit( double money );
   void withdraw( double money );
   double checkBalance() const;

private:
   double deposited_;
};

// .cpp
BankAccount::BankAccount( double openingDeposit )
   :   deposited_( openingDeposit )
{
}

void BankAccount::deposit( double money )
{
   deposited_ += money;
}
void BankAccount::withdraw( double money )
{
   deposited_ -= money; // 1
}
double BankAccount::checkBalance() const
{
   return deposited_;
}

```

The code demonstrates a couple of concepts. First, data is encapsulated inside the class, only possible changes to deposited_ are through the BankAccount interface (in your example user may change balance through the global variable directly). Users only see the definition (.h) and not the implementation. You may consider checking in withdraw whether there is enough money in the account for that withdrawal (well, this should be clearly documented in the interface: can withdraw fail? throw exceptions?)

The constructor is called whenever an object of the class is created, and thus deposited_ will be initialized for each object. The constructor takes an optional double as argument with the amount of the initial deposit, which if omitted defaults to 0 (default value is defined only in .h, not in the implementation). The constructor is marked as explicit, this is required so that the compiler is not allowed to make direct conversions from double to BankAccount, but only through direct calls to the constructor. Note the syntax, as initialization of member attributes can be (should be) done in initialization lists as there.

As no resources have to be freed at the end of the objects life, default constructor is sufficient and we do not need to define it.

All methods of the class have access to the deposited_ attribute directly. checkBalance is marked as const as this operation does not modify the internals of BankAccount. This is required if you want to be able to check the balance of a constant BankAccount (or a non constant account accessed through a constant reference).

The good part of data encapsulation is that you can later modify the internals and store an specific data type with a known precision (2 decimals, 3?). Or decide to charge for operations (.25 for each balance check). Or maintain a log of all operations on the account. This are details of the implementation that users (code) don't need to know. Well, users (people) will surely want to know if you charge them for operations, but thats another story.

---

### Post by loganwm on 2008-07-22
The idea of creating this ATM program for me was to experiment with C++ and to make sure that I know the fundamentals.

I'm glad that you've shown me the conventions for class usage (Thanks will be given :) ).

In your example and the explanation you provided, I have just a few questions:

[LIST]
[*]You suggested that the class definitions should be contained in a seperate .h (Header) file, correct?
[*]Why are the class methods outside (or possibly in a seperate file) from the prototypes?
[/LIST]

---

### Post by dribeas on 2008-07-23
> **loganwm said:**
> 
[LIST]
[*]You suggested that the class definitions should be contained in a seperate .h (Header) file, correct?
[*]Why are the class methods outside (or possibly in a seperate file) from the prototypes?
[/LIST]


Yes, for a couple of reasons. You offer a file that contains only the interface of your class. That is enough for any other user that wants to create BankAccount objects. But they don't necessarily need to know the implementation. Then you can compile each implementation file (compilation unit) separatedly.

The second reason is more technical, and assumes that you want your class to be used outside of this compilation unit. In a project with many compilation units that get linked together there must be only one implementation for each non-inlined method (there are special cases, as with templates, but that is a quite general rule). 

```

// X.h
class X
{
public:
   void foo() 
   {
      // implementation
   }
   void bar();
};

void X::bar()
{
   // implementation
}

// user1 .cpp
#include "X.h"
// ...

// user2 .cpp
#include "X.h"
// ...

```

If you tried that with at least two compilation units (.cpp files) that both include your .h then foo() would be correctly processed by the compiler (inlined in each call), but bar() yields a linker error as the linker will find a definition for X::bar() in each object file (.o) and does not know which is the correct one (does not even know that they are the same).

Hard part is knowing when to inline methods and when not to. That is out of experience. Most times, if you are only offering an accessor to some internal data (as in BankAccount::checkBalance() that only returns a copy of deposited_) then you are ok inlining and it might yield a faster (and possibly smaller) executable. If the method has some processing to it, then inlining it might generate a huge executable as the method implementation will be duplicated in each call. Knowing how much processing is 'some processing' is the hard part. If in doubt, do not inline.

Summarizing in your two questions:
[LIST]
[*] Class definition but not implementation in a header file so it can be used by clients
[*] If method implementations are inside the class definition you are asking the compiler to inline. If they are outside the class then they must be in a different compilation unit.
[/LIST]

---

### Post by loganwm on 2008-07-23
Alright, so if I'm following you correctly, this is the hierarchy that I should setup my class and header and such as?

main.cpp // is the program code such and such
[INDENT]-included in main.cpp: bank.h // is the class definition for BankAccount containing function prototypes[/INDENT]
[INDENT][INDENT]-included in bank.h: bank.c // contains the function definitions for BankAccount class[/INDENT][/INDENT]

As usual, if not, please correct me :)

---

### Post by dribeas on 2008-07-23
> **loganwm said:**
> Alright, so if I'm following you correctly, this is the hierarchy that I should setup my class and header and such as?

main.cpp // is the program code such and such
[INDENT]-included in main.cpp: bank.h // is the class definition for BankAccount containing function prototypes[/INDENT]
[INDENT][INDENT]-included in bank.h: bank.c // contains the function definitions for BankAccount class[/INDENT][/INDENT]

As usual, if not, please correct me :)

Not quite so.

```

main.cpp
#include "bank.h"

bank.h
// does not include anything

bank.cpp
#include "bank.h"

```

Now you must compile both bank.cpp and main.cpp, simplest way would be:
```
g++ bank.cpp main.cpp -o executable
```

else

```
g++ -o bank.o -c bank.cpp # -c only compile, do not try to link
g++ -o main.o -c main.cpp
g++ -o executable main.o bank.o # links into executable

```

Of course once you have a couple of files using makefiles becomes easier. I personally use cmake to generate the makefiles as it is simple and multi-platform (our project must compile with VS2003, VS3005, g++ 3.4, g++ 4.1, g++ 4.2 in different linux flavors)

Note that bank.h is included in both compilation units, but implementations aren't.

David

---

### Post by loganwm on 2008-07-23
So, bank.cpp and the main.cpp do not need to be linked in the code, when the compiler runs, it links them?

And as for cmake, I installed it using apt and I just want to ask you if you can give me a quick demo of how to use it to generate a makefile for my scenario? And also on the cmake topic, how can I include compiler flags to my makefile for SDL apps for example? (-lSDL, etc)

---

### Post by dribeas on 2008-07-23
> **loganwm said:**
> So, bank.cpp and the main.cpp do not need to be linked in the code, when the compiler runs, it links them?

And as for cmake, I installed it using apt and I just want to ask you if you can give me a quick demo of how to use it to generate a makefile for my scenario? And also on the cmake topic, how can I include compiler flags to my makefile for SDL apps for example? (-lSDL, etc)

If you want to use it you should read the docs. For your sample code above:
```

File CMakeLists.txt:

add_executable( executable
   main.cpp
   bank.cpp
)

Command line:
cmake .

```

You are asking cmake to create a Makefile that will compile 'executable' from main.cpp and bank.cpp. After running "cmake ." you can run "make" to have it compile and link.

If you want to link to a given library you need to add
```

CMakeLists.txt as above plus:
target_link_libraries( executable
   SDL
)

```

If you have libraries in a non-default directory you may want to use one of the FindXXXX modules (if it exists for your library) or create one. But then again, read the docs.

---

