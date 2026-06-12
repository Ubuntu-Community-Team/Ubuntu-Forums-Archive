---
title: "c++ help"
date: 2008-02-01
forum: Programming Talk
---

### Post by Masterj15 on 2008-02-01
I was wondering if you could help him with this c++ program. He doesn't know how to get the info from the apples and oranges back to the main(). he wants the answer of the apples and the answer of oranges back to the main and then the main does the rest. (also he said that he needs the float and int for the apples and oranges to stay their.. It a part of his school's instructions. lololol)

Thanks in advance.

[http://www.divshare.com/download/3669645-401:](http://www.divshare.com/download/3669645-401:))

if you need anymore info just ask me. :)

also If you could post your fixes, that would be grateful

---

### Post by Masterj15 on 2008-02-01
bump

---

### Post by macogw on 2008-02-01
Then why is the oranges one returning 1 insted of what the main needs to get from it?  It looks like the apple one was done right.

---

### Post by stevescripts on 2008-02-01
hmm .... where to start?
(dons flame-retardent nomex )

1.  I doubt that anyone here is actually going to do *his* homework
for him.

2.  The code shows only a minimal understanding of how to
solve the problem using c++.  *He* needs to pay a bit more
attention in class, and try just a bit harder.

3.  Both the function prototypes, and functions themselves
are declared to return type int - this is not what *he* wants ...

That said - maybe an even simpler example might help:
```

#include <iostream>

using namespace std;

float compute_price(int, float);


int main () 
	{
		int pounds;
		float price_per_pound = 1.50;
		float total_price;

		cout << "How many pounds of rocks would you like to buy?" << endl;

		cin >> pounds;

		total_price = compute_price(pounds, price_per_pound);

		cout << "The total price of your order is: " << total_price << endl;

		return 0;
	}

float compute_price (int x, float y)
	{
		int pounds = x;
		float price_per_pound = y;
		float total = x * y;
		return total;
	}


```

Hope this helps.

Steve

---

