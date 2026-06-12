---
title: "program using struct to determine prime numbers in c++"
date: 2009-02-03
forum: Programming Talk
---

### Post by kapok on 2009-02-03
i have read every tutorial out there on structures in c++, and was falsely convinced i knew what i was doing. so i wrote a program. its purpose is to determine all prime numbers between 1 and 100. it compiles and runs with no errors, but does absolutely nothing. here it is:
```

#include <iostream> //am i missing a structure allowing header file?
using namespace std;

/******************************************************************************************/

struct prime_node { int x; prime_node *next; };
prime_node *primes;
prime_node *traverser;

int prime_test( int x );
int main()
{
int counter;

primes = new prime_node; //memory allocation here.
primes->x = 1;
primes->next = 0;
traverser = primes;

for ( counter = 1; counter <= 100; counter ++ ) //take each number...
	{ if ( prime_test(counter) == 1 ) { traverser->x = counter; //and if it passes the prime test, add it to the integer value in the structure of primes. then, allocate 										//memory for the next structure, and tell the next prime number to go in that. and so on...
					    traverser->next = new prime_node; 
					    traverser = traverser->next; /*i've considered putting the 'cout' function in this loop. that would solve the 'starting over'.*/ 						  }
	}
while ( traverser->next != 0 ) //loop that runs through the structure, one node at a time, and prints the contents of its x member's value. stops at the null pointer
	{
	cout<<traverser->x<<endl; /*is there some way of setting it back to the first of the nodes that i am missing? i thought it did that automatically when you break the 						loop that it is used in.*/
	traverser = traverser->next; //moves on to the next node. this cannot be 0, or the loop will have stopped.
	}	
}

/***********************************************************************************************/

int prime_test( int x )
{ 
while ( traverser->next != 0 )
{ 
	if ( x % traverser->x == 0 ) //if the number passed to it can divide into any prime number with no remainder, it is not prime.
		{ return 0; }
traverser = traverser->next;
}
return 1; //otherwise, it is.
}
```

all help is greatly appreciated; this problem has been stumping me for a few hours.

---

### Post by kapok on 2009-02-03
eeh, sorry for my code being hard to read. it autowrapped in my text editor, so i added spaces to make it look nice.

---

### Post by croto on 2009-02-03
I'm sorry man, but I'm too lazy to look for the bug in your code. The code's intention was very clear. So I just took your code as the skeleton and implemented it my way, especially the way you were using the linked list. I think it works fine now.

EDIT: and you definitely know what you're doing, the code just needed small adjustments :).

```

#include <iostream>
using namespace std;

/******************************************************************************************/

struct prime_node { int x; prime_node *next; };

int prime_test( int x, prime_node* prime );

int main()
{
  prime_node *primes, *last_node;

  primes = new prime_node;
  primes->x = 1;
  primes->next = 0;
  last_node = primes;

  for ( int counter = 2; counter <= 100; counter ++ ) //take each number... but not 1
  { 
    if ( prime_test(counter, primes) == 1 ) 
    { 
      last_node->next = new prime_node;
      last_node = last_node->next;
      last_node->x = counter;
      last_node->next = 0;
    }
  }
  prime_node* traverser = primes;
  while ( traverser != 0 ) 
  {
    cout<<traverser->x<<endl; 
    traverser = traverser->next;
  }	
}

/***********************************************************************************************/

int prime_test( int x, prime_node* prime )
{ 
  prime = prime->next; // skip the 1
  while ( prime != 0 )
  { 
    if ( x % prime->x == 0 ) //if the number passed to it can divide into any prime number with no remainder, it is not prime.
    { 
      return 0; 
    }
    prime = prime->next;
  }
  return 1;
}

```

---

### Post by HuaiDan on 2009-02-03
I'm not a coder, but I did notice your interest in prime numbers.

Have you checked out [http://www.numberspiral.com](http://www.numberspiral.com) ? It will blow your mind.

---

### Post by kapok on 2009-02-04
thanks. it works fine now. thread = solved.

what i was missing was the 'traverser = primes;' at the beginning of each funtion that used it, so instead of being set back to the first node pointer, it just went from where it was.

---

