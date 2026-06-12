---
title: "c++ struct problem ?"
date: 2009-03-12
forum: Programming Talk
---

### Post by celticbhoy on 2009-03-12
OK folks, I am taking my first steps into learning c++, and I am trying to write a simple little program to help me understand how things work. My problem is trying to use struct.

My definition before int main() :-

struct stockrec {
	int stno;
	int op;
	int cur;
	float cst, bsale, ossingle, osmulti;
	char descript[30], sze[5];
};

My variable setting to use above (first line in int main()) :-

	struct stockrec work;

The first time my prog uses the variable in a function :-

	work.stno=lastrec;

The error the compiler throws at me :-

stock1.cpp: In function ‘int addrec()’:
stock1.cpp:82: error: ‘work’ was not declared in this scope

I think this must be something simple, but I just cant figure it out.


:confused:

---

### Post by shadylookin on 2009-03-12
> **celticbhoy said:**
> OK folks, I am taking my first steps into learning c++, and I am trying to write a simple little program to help me understand how things work. My problem is trying to use struct.

My definition before int main() :-

struct stockrec {
	int stno;
	int op;
	int cur;
	float cst, bsale, ossingle, osmulti;
	char descript[30], sze[5];
};

My variable setting to use above (first line in int main()) :-

	struct stockrec work;

The first time my prog uses the variable in a function :-

	work.stno=lastrec;

The error the compiler throws at me :-

stock1.cpp: In function &#8216;int addrec()&#8217;:
stock1.cpp:82: error: &#8216;work&#8217; was not declared in this scope

I think this must be something simple, but I just cant figure it out.


:confused:

well it would be a lot easier if you just posted the code however my guess is that you have work declared in main and then you have a function that tries to do something with work, but you didn't pass work as a parameter

[PHP]
int main(){
    struct stockrec work;
    function();
}

void function(){
    work.stno = 5;
}
[/PHP]

is it like that?

---

### Post by geirha on 2009-03-12
When you declare a variable in a function (including main), it will only be accessible in that function. If you want another function to use it, you need to pass it as an argument to that function...

---

### Post by cabalas on 2009-03-12
It isn't working because variables decleared in a function can only be used as in that function, to use it in the other function pass it as a parameters (as a reference would be a good idea). Here is an example based off of the code you posted.

[PHP]
#include <iostream>

struct stockrec {
	int stno;
	int op;
	int cur;
	float cst, bsale, ossingle, osmulti;
	char descript[30], sze[5];
};

int main() 
{
	stockrec work;
	
	addrec(work);
}

void addrec(stockrec &work) 
{
	int lastrec = 5;
	
	work.stno = lastrec;
}
[/PHP]

Now that is all of the top of my head so it may not work or even compile but from there you should be able to do what you need to do.

---

### Post by celticbhoy on 2009-03-12
Thanx for the quick help guys, that was it exactly.

---

### Post by celticbhoy on 2009-03-12
Guess I didnt have it after all, here is my complete code its freaking out at the setup function, and the addrec function as well. Why am I not getting this ??

```
// Very Simple Stock Control Version 1

#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std;

struct stockrec {
	int st_no, opening, actual;
	float cost, barsale, ossingle, osmulti;
	char description[30], size[5];
};

int lastrec, disrec, amrec, recno;

int menu();
int setup(int a,int b,int c,int d,int e,int f,int g, string h, string i);
int addrec(stockrec, recno);
int dataent(stockrec);


int main ()
{
	int st_no[100], opening[100], actual[100];
	float cost[100], barsales[100], ossingle[100], osmulti[100];
	string description[100], size[100];
	
	stockrec current;
	recno=0;
	for (recno=0; recno=100; recno++)
	{
		setup(recno,opening[recno],actual[recno],cost[recno],barsales[recno],
			ossingle[recno],osmulti[recno],description[recno],size[recno]);
		st_no[recno]=recno;
	}
	int choice; choice=0;
	system("clear");
	while (choice!=4)
	{
		choice=menu();
		system("clear");
		switch (choice)
		{
			case 1:
				recno=lastrec;
				dataent(current);
				addrec(current, recno);
				lastrec++;
				break;
			case 2:
				break;
			case 3:
				break;
		}
	}
	return 0;	
}

int menu()
{
	int mchoice;
	
	cout << "What would you like to do?\n";
	cout << "--------------------------\n";
	cout << "1) Add stock record to file\n";
	cout << "2) View item in file\n";
	cout << "3) Amend item in file\n";
	cout << "4) Exit Program\n";

	while (mchoice<1||mchoice>4)
	{
		printf("\nEnter Selection : ");
		scanf("%d", &mchoice);
	}
	return mchoice;
}

//int setup(a,b,c,d,e,f,g,h,i)
int setup()
{
		b=0;
		c=0;
		d=0;
		e=0;
		f=0;
		g=0;
		h="EMPTY";
		i="EMPTY";
}

void dataent(stockrec &current)
{
	system("clear");
	printf("stock record %d adding :-\n", lastrec);
	current.st_no=lastrec;
	printf("\nEnter Description     : "); cin.getline ( current.description, 30, '\n' );
	printf("\nEnter item size       : "); cin.getline ( current.size, 5, '\n' );
	printf("\nEnter item cost       : "); cin >> current.cost;
	printf("\nEnter bar sales price : "); cin >> current.barsale;
	printf("\nEnter O/S sales price : "); cin >> current.ossingle;
	printf("\nEnter multipack price : "); cin >> current.osmulti;
	printf("\nEnter opening stock   : "); cin >> current.opening;
	current.actual=current.opening;
}

void addrec(stockrec &current, int rec)
{
	st_no[rec]=current.st_no;
	description[rec]=current.description;
	size[rec]=current.size;
	cost[rec]=current.cost;
	barsales[rec]=current.barsale;
	ossingle[rec]=current.ossingle;
	osmulti[rec]=current.osmulti;
	actual[rec]=current.actual;
}
```

---

### Post by cabalas on 2009-03-12
Ok the setup function doesn't take any parameters and is assigning values to variables which don't exist in its scope.  Also on the setup function if you use the commented out version of the function the values still won't be assigned as you are passing them by value not by reference.

The addrec prototype at the top of the file doesn't match the implementation of the function (you need to include the & symbol in the prototype as well).

You can't have 2 main functions nor do you have to declare the prototype of the main function.

Hopefully that helps

---

### Post by celticbhoy on 2009-03-12
Just working on the setup function, how you pass the reference??

---

### Post by cabalas on 2009-03-12
pass by reference you just need to put an & in front of the parameter in the function prototype and implementation and then just use it like a regular function.

Just on the off chance that you haven't come across calling by value/reference before these links should help a little.

[http://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_reference](http://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_reference)
[http://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_value](http://en.wikipedia.org/wiki/Evaluation_strategy#Call_by_value)
[http://en.wikipedia.org/wiki/Evaluation_strategy](http://en.wikipedia.org/wiki/Evaluation_strategy)

---

