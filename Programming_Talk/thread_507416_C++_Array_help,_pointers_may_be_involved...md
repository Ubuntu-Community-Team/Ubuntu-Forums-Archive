---
title: "C++ Array help, pointers may be involved.."
date: 2007-07-23
forum: Programming Talk
---

### Post by w1nD on 2007-07-23
Hello everyone,

I'm stuck on this part of my program...

Here's the main:

```
int main()
{
 employee a[5];

 case 1: 
 {
   employee a[5];   // declared an array a (This hides the a that was previously declared)
    << STUFF >>
   break;   
 } // a is going out of scope (All its content is destroyed)
        
 case 2: 
 {
   employee a[5];   // declared an array a (This hides the a that was previously declared)
   a[5].get_name(); // This gets the name from the local 'a' which is newly defined and thus empty.
   break;
 } // a is going out of scope
 case 3: 
 {
   employee a[5];   // declared an array a (This hides the a that was previously declared)
   a[5].get_sal();  // This gets the salary from the local 'a'
   break;
 } // a is going out of scope
 case 4: 
 {
   employee a[5];   // declared an array a (This hides the a that was previously declared)
   cout<<a[5].get_name()<<" has a salary of $"<<a[5].get_sal(); // getting empty stuff from new array
   break;
 } // a is going out of scope
 case 5: 
 {
   string name;
   int raise;
   employee a[5];   // declared an array a (This hides the a that was previously declared)
   cout<<"Who's salary do you want to raise?"<<endl;
   a[5].get_name(); //getting the name from local emty array,
   cin>>name;
   cout<<"How much in percentage do you want to raise? ";
   cin>>raise;
   a[5].calcSal();  // Calling calc on local array.
   cout<<"Done."<<name<< "'s salary has been raised. New salary is: $"<<a[5].calcSal()<<endl;
  break;
 }  // local a is going out of scope. Thus any changes will be lost.

} 

```

How do I keep the array from case 1 so the array can be used in case 2, case 3, etc?

Thanks.

---

### Post by dawdler on 2007-07-23
First off, your code is missing the switch statement i.e.:

switch(*variable*){
    case 1:
    .
    .
    .
    etc.
}

Now to answer your question, as I understand it...

First point, declaring the employee array in line three of your code takes care of your problem.  Since it is declared outside the scope of the case statements but inside the function, it will not be destroyed until you leave the function.  Also, manipulation of data will be preserved throughout the function while inside the scope of the function.

Second point, if you want to go from case to case in manipulating the array, remove the *break*s.  However, IMHO this is bad programming and would recommend using a chain of *if* statements.

---

### Post by w1nD on 2007-07-23
Ah, thanks for the help!

Well, I have another problem now. How would I cout the array?

Here's the entire code:

```

#include<iostream>
#include<string>
using namespace std;

class employee
{
public:
	employee();
	int calcSal();
	void input();
	string get_name();
	int get_sal();
	
	

private:
	string name;
	int salary;
	int raise;
};

employee::employee()
{
	name="";
	salary=0;
	raise=1;
		

}

void employee::input()
{
	cout<<"Please enter employee name: ";
	cin>>name;
	cout<<"Please enter salary for "<<name<<": ";
	cin>>salary;
}

string employee::get_name()
{
	return name;
}

int employee::get_sal()
{
	return salary;
}
int employee::calcSal()
{
	return salary*((raise+100)/100);
}

void main()
{
	employee a[5];
	
	cout<<"Welcome to Wind Corporation!"<<endl<<endl;
	int choice;
	do{
	cout<<"What do you want to do?"<<endl;
	cout<<"1. Enter a new employee and his/her salary."<<endl;
	cout<<"2. Display all employees and their respective salaries."<<endl;
	cout<<"3. Raise an employee's salary."<<endl;
	cout<<"4. Exit."<<endl;
	cin>>choice;

	if(choice==1)
	{
		a[5].input();                                   // array declared, right?
	                                                              // how to cout the array?
	}

	
	}while(choice!=4);


```

Thanks!

---

### Post by PaulFr on 2007-07-23
Maybe something like```
int main()
{
     employee a[5];

     ... <stuff> ...

    {
           employee a[5];   <-- this definition will be valid for the whole block
                            <-- and will override the definition at the start of main.

           ... <stuff> ...

           switch (<something>)
           {
           case 1: {
                        ... <case 1 stuff> ...
                   }
                   break;
           ... <other cases including **default:**> ..
           }
    }
}
```Comment:
1. I assume you really need to override the definition at the start of main. If not, you should just use it :-)
2. I think you mean a[4] in your example code. a[5] is undefined when you define an array of 5 elements (index 0 to 4). But you already know this.

---

### Post by w1nD on 2007-07-23
Oooo...

I never thought of that! Thanks man! I'll try it right now!

Thanks again!

EDIT:

There's something wrong when I try to cout the array.

```

employee a[5];
		{
			switch (choice)
			{
			case 1:
				{
			
					int i;
					for(i=0; i<5; i++)
					{
						a[i].input();
					}
					cout<< a[5];  //gives this error: Error	3	error C2679: binary '<<' : no operator found which takes a right-hand operand of type 'employee' (or there is no acceptable conversion)	

				}
				break;

```

this is the error:

error C2679: binary '<<' : no operator found which takes a right-hand operand of type 'employee' (or there is no acceptable conversion)

Is there something I have to declare before I can cout the array?

Thanks

---

### Post by bbzbryce on 2007-07-23
> **w1nD said:**
> Is there something I have to declare before I can cout the array?

You need to overload the << operator for your employee class. This function must be declared as a friend.

Something like this:

```

friend ostream& operator <<(ostream& outs, const SMatrix& theMatrix);

ostream& operator <<(ostream& outs, const SMatrix& theMatrix) {
  for (int i = 0; i < theMatrix.n; i++) {
    theMatrix.col[i]->resetCurr();
    const Entry* temp = theMatrix.col[i]->currValue();
    while (temp != NULL) {
      outs << "(" << temp->row << ":" << i << ")= " << temp->value << endl;
      temp = theMatrix.col[i]->advanceValue();
    }
  }
  return outs;
}
```

---

### Post by w1nD on 2007-07-23
> **bbzbryce said:**
> You need to overload the << operator for your employee class. This function must be declared as a friend.

Something like this:

```

friend ostream& operator <<(ostream& outs, const SMatrix& theMatrix);

ostream& operator <<(ostream& outs, const SMatrix& theMatrix) {
  for (int i = 0; i < theMatrix.n; i++) {
    theMatrix.col[i]->resetCurr();
    const Entry* temp = theMatrix.col[i]->currValue();
    while (temp != NULL) {
      outs << "(" << temp->row << ":" << i << ")= " << temp->value << endl;
      temp = theMatrix.col[i]->advanceValue();
    }
  }
  return outs;
}
```

Declared as a friend? What does that mean?

Thanks.

---

### Post by bbzbryce on 2007-07-23
> **w1nD said:**
> Declared as a friend? What does that mean?

A friend of a class is a class/function that is not a member of the class, but still has access to the protected and private variables of the class. The << operator does not get called on a particular class and thus it cannot be a member. Therefore in order to get the private or protected data it must be declared a friend. In addition classes can be friends of other classes.

An example of this would be having a generic node class as a friend to a linked list class.

---

### Post by slavik on 2007-07-24
may I suggest using Java's toString idea? (as part of the class)

---

