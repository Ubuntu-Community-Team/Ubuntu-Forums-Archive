---
title: "g++ question"
date: 2007-12-06
forum: Programming Talk
---

### Post by zerofreeze on 2007-12-06
i installed g++ compiler from synaptic manager but when i try to build a program it says "sh:g++: not found"

---

### Post by Wybiral on 2007-12-06
Use this command:

```

sudo apt-get install build-essential

```

To install everything you need. It's used with "g++", not "sh:g++" (I didn't know if that was intentional or now).

---

### Post by zerofreeze on 2007-12-06
Thanksfor help ;) ...please don't ignore me when i ask :)

---

### Post by zerofreeze on 2007-12-06
when i did u told me it said
mostafamagdy@ubuntu:~$ sudo apt-get install build-essential
Password:

when i enter my password it did nothing ...

---

### Post by Wybiral on 2007-12-06
Ignore you?

---

### Post by Wybiral on 2007-12-06
> **zerofreeze said:**
> when i did u told me it said
mostafamagdy@ubuntu:~$ sudo apt-get install build-essential
Password:

when i enter my password it did nothing ...

You have to enter your password to use apt-get, then hit enter and it should begin installing the "build-essential" package (which contains all the header files and build requirements for using gcc/g++).

---

### Post by zerofreeze on 2007-12-06
yes because i really need help

---

### Post by zerofreeze on 2007-12-06
i did, i enetered the password and it said "Sorry, try again."

---

### Post by Wybiral on 2007-12-06
Maybe you mistyped the password? It is case sensitive.

---

### Post by zerofreeze on 2007-12-06
yes its working ...maybe the keyboard is old enough and want to be changed :)

---

### Post by zerofreeze on 2007-12-06
when i try another program en error said:
equation solver.cpp: error: '::main' must reutrn 'int' :
equation solver.cpp: In function 'int main()' :
equation solver.cpp: error: 'stricmp' was not declared in this scope
equation solver.cpp: error: 'getch' was not declared in this scope

what can i do ?

---

### Post by Wybiral on 2007-12-06
Can you post the code you're compiling?

---

### Post by zerofreeze on 2007-12-06
sorry for answering too late... Here's the code :
#include<iostream>

#include<cmath>

using std::cout;

using std::cin;

using std::endl;





class Root 

{

public:

	Root() {};

	~Root() {};

	void pres();

    void select();

    double root(double a, double b);

    double root_part1(double a, double b, double c, double D);

    double root_part2(double a, double b, double c, double D);

};



double Root::root(double a, double b)

{

	return(-b/a);

}



double Root::root_part1(double a, double b, double c, double D)

{ 

    return sqrt(D)/(2*a);#include<iostream>

#include<cmath>

using std::cout;

using std::cin;

using std::endl;





class Root 

{

public:

	Root() {};

	~Root() {};

	void pres();

    void select();

    double root(double a, double b);

    double root_part1(double a, double b, double c, double D);

    double root_part2(double a, double b, double c, double D);

};



double Root::root(double a, double b

}



double Root::root_part2(double a, double b, double c, double D)

{

    return sqrt(-D)/(2*a);

}



void Root::pres()

{

    cout << "=============================================================================\n";

    cout << "		      Welcome to the equation solver!                                 \n";

    cout << " This program can solve any first or second degree polynomial equation \n";

    cout << "=============================================================================\n\n";

}



void Root::select()

{

    char car = (char)254;

    char exp = (char)253;

    cout << car << " For solving a first degree equation \"ax + b = 0\" enter '1' or enter '2' \n";

    cout << car << " for solving a second degree equation \"ax" << exp << " + bx + c = 0\": ";

}



void main()

{ 

    Root *p = new Root;

    double a = 0, b = 0, c = 0;

    int choix = 1;

    double D = 0, A = 0, B = 0, C = 0;

    char exp = ( char )253;

    char answer[5] = "yes";

    while( stricmp( answer, "no" ) != 0 )

	{

        p->pres();

        p->select();

        choix = getch();

		cout << endl << endl;

        	 

		switch(choix)

		{

		case '1':

			cout << "a = ";

			cin  >>  a;

            cout << "b = ";

            cin  >>  b;



			while( a == 0 ) 

			{

				cout << "\"a\" can't be 0, please choose another value: ";

				cin >> a;

			}



            cout << "your equation is: " << a << "x + " << b << " = 0" << endl;

            cout << "the solution is: x = "<< p->root( a, b ) << "\n";

            break;

		case '2':

			cout << "a = ";

            cin  >>  a;

            

			while( a == 0 ) 

			{

				cout << "\"a\" can't be 0, please choose another value: ";

				cin >> a;

			}



			cout << "b = ";

            cin  >>  b;

            cout << "c = ";

            cin  >>  c;



            D = b * b - ( 4 * a * c );

            A = -b/( 2 * a );

            cout <<"\nthe equation is: " << a << "x" << exp << " + " << b << "x + " << c << " = 0 " << endl;

            cout << "\nDelta = " << D  << endl << endl;

            if( D < 0 )

			{

                cout << "These equation have two complex roots" << endl;

                cout << "the first one is: x1 = "<< A << " + " << p->root_part2( a, b, c, D ) << "i" << endl;

                cout << "the second one is: x2 = "<< A << " - " << p->root_part2( a, b, c, D ) << "i" << endl;

            }

			else

			{

				cout << "These equation have two real roots" << endl;

                cout << "the first one is: x1 = " << ( -b/( 2 * a ) ) + p->root_part1( a, b, c, D )  << "\n";

                cout << "the second one is: x2 = " << ( -b/( 2 * a )) - p->root_part1( a, b, c, D )  << endl;

			}

            break;

		default: 

			cout << "\n\nThis selection is unknown,select '1' or '2'\n";

		}

        cout << "\nDo you want to solve another equation ? ( Yes ) or ( No )" << endl;

        cin >> answer;

        while(( stricmp( answer, "yes" ) != 0 ) && ( stricmp( answer, "no" ) != 0 ))

		{

            cout << "Please only answer by \"yes\" or \"no\"!" << endl; 

            cin  >>  answer;

		}

        system("cls");

	}

    delete p;



}

---

### Post by zerofreeze on 2007-12-06
can u answer me plz ?

---

### Post by LaRoza on 2007-12-06
> **zerofreeze said:**
> can u answer me plz ?

Can you use [ code ] or [ php ] tags, so we can all read the code?

---

### Post by smartbei on 2007-12-06
That, and remove uneccesary empty lines so we can read it in a single-digit number of pages? :D

Also, I actually wanted to see what was wrong but about the code you pasted...
[list]
[*]Why is class Root defined twice?
[*]What is:
> double Root::root(double a, double b

} Supposed to be?
[*]main should return an int - g++ won't compile otherwise.
[*]You have your includes and your usings there twice.
[/list]

Most of those are probably pasteing errors - fix those and we'll see about the rest :).

---

