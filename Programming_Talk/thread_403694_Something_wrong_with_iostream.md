---
title: "Something wrong with iostream?"
date: 2007-04-07
forum: Programming Talk
---

### Post by M$LOL on 2007-04-07
GCC errors:

g++ struct.cpp -Wall -o structs.exe
struct.cpp: In function ‘int main()’:
struct.cpp:16: error: ‘cout’ was not declared in this scope
struct.cpp:16: error: ‘endl’ was not declared in this scope
struct.cpp:17: error: ‘cin’ was not declared in this scope

Here's the source:

#include <iostream>

struct addr
{
	char name[30];
	char street[40];
	char city[20];
	char state[3];
	unsigned long int zip;
};

int main()
{
	struct addr addr_info;
	
	cout << "Enter your name" << endl;
	cin >> addr_info.name ;
	cout << "Your name is " << addr_info.name << endl;
	cin.get();
	
	return 0;
}

Is iostream not working, or am I missing something?

---

### Post by Wybiral on 2007-04-07
Ah... Those functions are in the "std" namespace within iostream. You have two options...

1. Add "using namespace std;" somewhere at the top of your program
2. Prefix every use of the namespaced functions with "std::"

---

### Post by M$LOL on 2007-04-07
D'oh! I knew it was something simple I was doing wrong. The funny thing is that I've put [COLOR="Red"]using namespace std;[/COLOR] in every other program I've written. Thanks. :)

---

