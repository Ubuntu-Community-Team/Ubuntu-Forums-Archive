---
title: "Very Basic C++ help"
date: 2012-06-22
forum: Programming Talk
---

### Post by fdgod33 on 2012-06-22
My problem is whenever i run this syntax on c++, it counts -1 as part of the loop.
i did something similar to the "THENEWBOSTON" syntax, his -1 was not included

Basically, I'm looking for the average of ages..




#include <iostream>

using namespace std;

int main()
{
    int age;
    int numberofpeople = 0;
    int  sumofage= 0;

    while (age !=-1){

        cout << "Enter age value here or press -1 to quit" << endl;
        cin >> age;

        sumofage = sumofage + age;
        numberofpeople ++;



}

    cout << "The number of people is " << numberofpeople << endl;

    cout << sumofage/numberofpeople;



    return 0;
}


**Whenver i compile this, it sees -1 as a value, how can i prevent this from happening**

---

### Post by december0123 on 2012-06-22
```
cout << "The number of people is " << numberofpeople [COLOR=Red]-1[/COLOR] << endl;

cout << (sumofage [COLOR=Red]+ 1[/COLOR])/(numberofpeople[COLOR=Red] - 1[/COLOR]);
```The simplest solution is usually the best one :)

---

### Post by trent.josephsen on 2012-06-22
I think rewriting the loop as a do...while is probably a simpler solution:

```
	int age = 0;
	int numberofpeople = -1;
	int sumofage = 0;

	do {
		numberofpeople++;
		sumofage = sumofage + age;
		cout << "Enter age value here or press -1 to quit" << endl;
		cin >> age;
	} while (age != -1);
```
Less magic.

@OP, you should wrap your code in [CODE] tags when posting, which will help us read your code more easily (provided you indented it well, of course).

---

### Post by 3Miro on 2012-06-22
```
#include <iostream>

using namespace std;

int main()
{
**int age = 0;**
int numberofpeople = -1;
int sumofage= 0;

while (age !=-1){

sumofage = sumofage + age;
numberofpeople ++;

cout << "Enter age value here or press -1 to quit" << endl;
cin >> age;


}

cout << "The number of people is " << numberofpeople << endl;

cout << sumofage/numberofpeople;

return 0;
}
```

First of all, you should always initialize your variables. You were checking the value of (age!=-1) before any value was stored in it.

Second, you should count how many times the loop is counted, when -1 is entered, you still count both the age and number of people. 

I hope I didn't just do your homework for you.

---

### Post by dwhitney67 on 2012-06-22
I doubt the OP intended to add -1 to the sum-of-ages???  Yet some of the previous examples seems to show that or increment numberofpersons prematurely.  :-k

The program should check the value of the variable 'age' before using it within an computation.  Similarly, the value of numberofpersons should be checked before using it as a divisor.  Something like:
```

#include <iostream>

int main()
{
    using std::cout;
    using std::cin;
    using std::endl;

    int sumofage = 0;
    int numberofpeople = 0;

    while (true)
    {
        int age = -1;

        cout << "Enter age value, or -1 to quit: ";
        cin  >> age;

        if (age == -1) break;

        sumofage += age;
        ++numberofpeople;
    }

    cout << "\nNumber of people: " << numberofpeople << endl;

    if (numberofpeople > 0)
    {
        cout << "Avegage age of people: " << (float) sumofage / numberofpeople << endl;
    }
}

```

P.S.  It is important to reset 'age' for each cycle around the loop; one never knows if the user will force an EOF (ctrl-d) when the cin is being used to read user input.

---

