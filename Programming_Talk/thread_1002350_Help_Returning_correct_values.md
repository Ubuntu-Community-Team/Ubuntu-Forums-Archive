---
title: "Help Returning correct values"
date: 2008-12-04
forum: Programming Talk
---

### Post by steve21 on 2008-12-04
Hey i have a program but it does not return the correct values for calories after the user inputs the product which is the food that has already been entered previously. I cant figure out how to make it search for the correct food, also im not sure how to make it says "product not found" if no previous input is found please help me>



```
#include <iostream>
#include <string>
using namespace std;
int main()
{
string foods[100];
double calories[100];
string product;
int x = -1;
do
{
x++;
cout << "Enter a menu item (enter 'done' when finished):";
getline(cin, foods[x]);
if (foods[x] != "done")
{
cout << "Enter the number of calories: ";
cin >> calories[x];
cin.ignore();
}
} while (foods[x] != "done");
for (int y = 0; y < x; y++)
{
	string temp;
	cout<<"Enter a product to look up:"<<endl;
	cin >>temp;
cin.ignore();
cout << temp << " has " << calories[y] << " calories"
<< endl;
}
}
```

---

### Post by pp. on 2008-12-05
Homework?

---

### Post by slavik on 2008-12-05
show us sample input and output

---

### Post by Tony Flury on 2008-12-05
just as a hint - you are storing the names of the foods in the food array, but then you are not using the food array at all in your 2nd loop.

I would have expected you to be trying to find temp in your food array - but you are not doing that.

---

### Post by steve21 on 2008-12-05
pizza, 300, steak, 800, then you type done and it should say
"Enter a product to look up:" and you type in steak and it should say steak has 800 calories, but it will say steak has 300 calories. It just goes in order from the first calorie input.

---

