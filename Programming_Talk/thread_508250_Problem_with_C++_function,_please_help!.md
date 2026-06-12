---
title: "Problem with C++ function, please help!"
date: 2007-07-24
forum: Programming Talk
---

### Post by w1nD on 2007-07-24
Hey everyone,

I will try to explain this as clear as possible.

The problem:
When the user enters the raise (int) number, it will raise a person's salary by that percentage (raise in percentage). Then, the program should output (cout) the new salary. However, my program does not do that! I have tried many different ways in my calc function, but none of them seemed to changed the salary.

Solution?
Try to make the user's inputted raise variable "stick" in the program.

I am not quite sure what I'm doing wrong, so please take a look:

This is the case in the main function that calls the calc function.
```

case 3:
	{
		cout<<"Current Wind Employees: "<<endl;
		
		for(int j=1; j<6; j++)
		{
			cout<<a[j].get_name();
			cout<<" has a salary of $"<<a[j].get_sal()<<".";
			cout<<endl;
		}
		cout<<endl;
		cout<<"Who's salary do you want to raise?"<<endl<<endl;
		cout<<a[1].get_name()<<endl;
		cout<<a[2].get_name()<<endl;
		cout<<a[3].get_name()<<endl;
		cout<<a[4].get_name()<<endl;
		cout<<a[5].get_name()<<endl;
		cout<<endl<<endl;
		int pickEmp;
		cin>>pickEmp;
		
		if(pickEmp==1)
		{
			int raise;
			cout<<"This is the current salary for "<< a[1].get_name(); 
			cout<<": $"<<a[1].get_sal()<<endl;
			cout<<"How much in percentage do you want to raise?"<<endl;
			cin>>raise;
			a[1].calcSal(raise);
			cout<<"Done. "<<a[1].get_name()<<" now has a salary of $"<<a[1].calcSal(raise)<<"."<<endl;
		}
		break;
		cout<<endl;	
	}

```

This is the calc function.
```

int employee::calcSal(int raise)
{
	do{
		
	int result=1;
	
	if(raise>0)
	{	
		return result = salary*((raise+100)/100);
	}
	else
	{
		cout<<"Error. Please enter a larger number."<<endl;
		return 0;
	}
	}while(raise<0);
}

```

This is the entire source code:

```

#include<iostream>
#include<string>
using namespace std;

class employee
{
public:
	employee();
	int calcSal(int);
	void input();
	string get_name()
	{
		return name;
	}
	int get_sal()
	{
		return salary;
	}
	
	
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



int employee::calcSal(int raise)
{
	do{
		
	int result=1;
	
	if(raise>0)
	{	
		return result = salary*((raise+100)/100);
	}
	else
	{
		cout<<"Error. Please enter a larger number."<<endl;
		return 0;
	}
	}while(raise<0);
}

int main()
{
	employee a[6];
	cout<<"Welcome to Wind Corporation!"<<endl<<endl;
	int choice;
	do{
	cout<<"What do you want to do?"<<endl;
	cout<<"1. Enter a new employee and his/her salary."<<endl;
	cout<<"2. Display all employees and their respective salaries."<<endl;
	cout<<"3. Raise employee's salaries."<<endl;
	cout<<"4. Exit."<<endl<<endl;
	cin>>choice;

	switch (choice)
	{
	case 1:
	{
	
		for(int i=1; i<6; i++)
		{
			a[i].input();
		}
		cout<<endl;
		break;
	}
	case 2:
	{
		cout<<"Current Wind Employees: "<<endl<<endl;
		
		for(int j=1; j<6; j++)
		{
			cout<<a[j].get_name();
			cout<<" has a salary of $"<<a[j].get_sal()<<".";
			cout<<endl;
		}
		break;
		cout<<endl<<endl;
	}
	case 3:
	{
		cout<<"Current Wind Employees: "<<endl;
		
		for(int j=1; j<6; j++)
		{
			cout<<a[j].get_name();
			cout<<" has a salary of $"<<a[j].get_sal()<<".";
			cout<<endl;
		}
		cout<<endl;
		cout<<"Who's salary do you want to raise?"<<endl<<endl;
		cout<<a[1].get_name()<<endl;
		cout<<a[2].get_name()<<endl;
		cout<<a[3].get_name()<<endl;
		cout<<a[4].get_name()<<endl;
		cout<<a[5].get_name()<<endl;
		cout<<endl<<endl;
		int pickEmp;
		cin>>pickEmp;
		
		if(pickEmp==1)
		{
			int raise;
			cout<<"This is the current salary for "<< a[1].get_name(); 
			cout<<": $"<<a[1].get_sal()<<endl;
			cout<<"How much in percentage do you want to raise?"<<endl;
			cin>>raise;
			a[1].calcSal(raise);
			cout<<"Done. "<<a[1].get_name()<<" now has a salary of $"<<a[1].calcSal(raise)<<"."<<endl;
		}
		break;
		cout<<endl;	
	}
	case 4:
	{
		cout<<"Have a nice day!"<<endl;
	}
		break;
		
	default:
		{
			cout<<"Please enter a valid number."<<endl;
		}
		break;
	}
	}while(choice!=4);
	
return 0;
}

```

Thanks for your help! :)

---

### Post by bbzbryce on 2007-07-24
> **w1nD said:**
> 
```

int employee::calcSal(int raise)
{
	do{
		
	int result=1;
	
	if(raise>0)
	{	
		return result = salary*((raise+100)/100);
	}
	else
	{
		cout<<"Error. Please enter a larger number."<<endl;
		return 0;
	}
	}while(raise<0);
}

```

This doesn't even make sense; The loop is incredibly pointless. Rewrite as:

```
int employee::calcSal(int raise)
{
	if(raise>0)
		return result = salary*((raise+100)/100);
	else
 	{
		cout<<"Error. Please enter a larger number."<<endl;
		return 0;
	}
}
```

Finally you are never storing the solution for the salary. You must do something like this somewhere:

a[1].set_sal(a[1].calcSal(raise));

Alternatively change this line:
```
return result = salary*((raise+100)/100);
```
to
```
salary *= ((raise+100)/100);
return salary;
```

---

### Post by w1nD on 2007-07-24
Lol. Ok, if you say so. Haha. I'll try it now!

Thanks.

[quote="bbzbryce"]Finally you are never storing the solution for the salary. You must do something like this somewhere:

a[1].set_sal(a[1].calcSal(raise));
[/quote]

Did you mean a[1].get_sal(*stuff*);  ?

Or do I need to create set_sal()?

EDIT:

Never mind, everyone. I got it. Basically, I had to change everything to float, since integer can't make decimals (raise).

Thanks for the help, bbzbryce!

---

