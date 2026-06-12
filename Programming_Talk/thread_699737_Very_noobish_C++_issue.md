---
title: "Very noobish C++ issue"
date: 2008-02-17
forum: Programming Talk
---

### Post by sujinge9 on 2008-02-17
Hi,
I was just doing a very basic C++ exercise to build a program that calculates the cost of parking a car based on the number of hours. The thing is that when the hours is greater then 24, it should always return 10, but its not working right. 
```

#include <iostream> 
using namespace::std;
#include <iomanip>
using namespace::std;
double calculatecharges(double hour)
{
	if (hour<=3)
		return 2;
	else if (3<hour<=23)
		return 2+.5*(hour-3);
	else return 10;
}
		
	
int main()
{
	double one, two, three;
	cout<<"Enter the times parked for the cars\n";
	cin>>one>>two>>three;
	cout<<endl;
	cout<<"Car"<<setw(8)<<"Hours"<<setw(8)<<"Charge\n";
	cout<<"1"<<setw(9)<<one<<setw(7)<<calculatecharges(one)<<endl;
	cout<<"2"<<setw(9)<<two<<setw(7)<<calculatecharges(two)<<endl;
	cout<<"3"<<setw(9)<<three<<setw(7)<<calculatecharges(three)<<endl;	

	
	
	
	return 0;
}	

```

---

### Post by Fbot1 on 2008-02-17
```

#include <iostream>
using namespace::std;
#include <iomanip>
using namespace::std;
double calculatecharges(double hour)
{
	if (hour<=3)
		return 2;
	else if (hour<=23)
		return 2+.5*(hour-3);
	else return 10;
}


int main()
{
	double one, two, three;
	cout<<"Enter the times parked for the cars\n";
	cin>>one>>two>>three;
	cout<<endl;
	cout<<"Car"<<setw(8)<<"Hours"<<setw(8)<<"Charge\n";
	cout<<"1"<<setw(9)<<one<<setw(7)<<calculatecharges(one)<<endl;
	cout<<"2"<<setw(9)<<two<<setw(7)<<calculatecharges(two)<<endl;
	cout<<"3"<<setw(9)<<three<<setw(7)<<calculatecharges(three)<<endl;




	return 0;
}

```

It was the else if.

---

### Post by aks44 on 2008-02-17
> **sujinge9 said:**
> else if (3<hour<=23)

C++ doesn't allow range comparisons like you're trying to do.
What happens here is that the compiler evaluates ((3 < hour) <= 23).
First, (3 < hour) is evaluated to true (it's always true if you got that far in the if/else statement), and the boolean value is then compared to 23 (which again is true, as a boolean value can either be 0 or 1 when cast to an integer).

---

### Post by rye_ on 2008-02-17
**beat me to the punch there**

The above poster is correct, the problems with you 'if' argument

---

### Post by sujinge9 on 2008-02-17
lol, ok, thank you guys very much.

---

