---
title: "C++ Beginner Help (Really Easy Question)"
date: 2009-12-09
forum: Programming Talk
---

### Post by Swenghk on 2009-12-09
I have no idea what's going on. When I run this code:

```
#include <iostream>
using namespace std;

int main()
{
	int score1, score2, score3;
	
	unsigned int average;
	average = (score1 + score2 + score3) / 3;
	
	cout << "Enter your first score: ";
	cin >> score1;
	
	cout << "\nEnter your second score: ";
	cin >> score2;
	
	cout << "\nEnter your third score: ";
	cin >> score3;
	
	cout << "\n\nYour average is " << average << "." << endl;
	
	return 0;
}
```

I get an answer like 4456654. Even though the values I enter are 98, 99, and 100. Even if I enter "0" I get a strange value. HELP PLEASE!

---

### Post by TheBuzzSaw on 2009-12-09
Look carefully at your code. I will say this: **order matters!** When do you think the average should be calculated?

As for the bizarre values, that one is much more difficult to spot for novices, so I'll just tell you where that comes from. When you setup a variable "int x", it simple allocates the memory for that data, but it does not clear that data at that memory location. As a result, your variables will carry garbage/random data (almost never just zero as you would expect). Put simply, you should initialize your variables upon declaration:
```
int x = 0;
```

---

### Post by lisati on 2009-12-09
> **thebuzzsaw said:**
> look carefully at your code. I will say this: **order matters!** when do you think the average should be calculated?

As for the bizarre values, that one is much more difficult to spot for novices, so i'll just tell you where that comes from. When you setup a variable "int x", it simple allocates the memory for that data, but it does not clear that data at that memory location. As a result, your variables will carry garbage/random data (almost never just zero as you would expect). Put simply, you should initialize your variables upon declaration:
```
int x = 0;
```

+1. :)

---

### Post by Swenghk on 2009-12-09
Thanks you so much mate! I actually remember reading that the order does matter now. Thanks a lot :]

---

