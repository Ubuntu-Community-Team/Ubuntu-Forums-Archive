---
title: "Simple c++ help"
date: 2007-02-07
forum: Programming Talk
---

### Post by sdmike on 2007-02-07
Ok I have a program which takes the values enter in and then subtracts them from my acount balance, but I'm not sure what's going on.

#include <iostream>
using namespace std;

int main ()
{
  int citi;
  int chase;
  int bofa;
  int wamu;

  cout << "Please enter your citi total: ";
  cin >> citi;
  cout << "Please enter your chase total: ";
  cin >> chase;
  cout << "Please enter your bofa total: ";
  cin >> bofa;
  cout << "Please enter your wamu total: ";
  cin >> wamu;
  cout << "Your total debt is: "(citi + chase + bofa) - wamu";
  return 0;

What simple thing am I missing here.

---

### Post by neilp85 on 2007-02-07
You didn't state what the problem is, but if it's not compiling it's because you don't have a closing brace for main.

---

### Post by Wybiral on 2007-02-07
If it isn't compiling... It could also be this line:

```

cout << "Your total debt is: "(citi + chase + bofa) - wamu";

```

Notice the stray double quote at the end? And the lack of the "<<" operator between ~is: "~ and ~(~

---

### Post by neilp85 on 2007-02-07
> **Wybiral said:**
> If it isn't compiling... It could also be this line:

```

cout << "Your total debt is: "(citi + chase + bofa) - wamu";

```

Notice the stray double quote at the end? And the lack of the "<<" operator between ~is: "~ and ~(~

That isn't the only problem, there should also be another << operator. What you should do is this:
```
cout << "Your total debt is: " << (citi + chase + bofa) - wamu << endl;
```

---

### Post by kinson on 2007-02-07
Its probably minor, but you might wanna initialize the variables first too :p

---

### Post by LotsOfPhil on 2007-02-07
> Its probably minor, but you might wanna initialize the variables first too

He does initialize the variables, as int. I think you probably want them to be double.

---

### Post by hod139 on 2007-02-07
> **LotsOfPhil said:**
> He does initialize the variables, as int. I think you probably want them to be double.
That's a declaration.  An initialization is supplying an initial value, e.g. 
int foo = 0.

---

### Post by sdmike on 2007-02-07
I got it to work. This did the trick for me.

[COLOR="Red"]#include <fstream>
#include <iostream>
using namespace std;

int main ()
{

float citi;
float chase;
float bofa;
float wamu;
float sprint;
 

ofstream outFile("finances.file");

cout << "File open, preparing to write..." << endl;

cout << "Please enter your WAMU total: ";
cin >> wamu;
cout << "Please enter your Citi total: ";
cin >> citi;
cout << "Please enter your Chase total: ";
cin >> chase;
cout << "Please enter your BofA total: ";
cin >> bofa;
cout << "Please enter your Sprint total: ";
cin >> sprint;

cout << "Your total debt is: " << wamu - (citi + chase + bofa) << endl;

outFile 
<< "Your WAMU Account Balance is $"<< wamu << ". \n"
<< "Your Citi charge is $" << citi << ". \n"
<< "Your Chase charge is $" << chase << ". \n"
<< "Your BofA charge is $" << bofa << ". \n"
<< "Your Sprint charge is $" << sprint << ". \n"
<< "Your total debt balance is $" << wamu - (citi + chase + bofa + sprint) << ". \n";

cout << "File written to, and now being closed..." << endl;

outFile.close();

return 0;
}


[/COLOR]

---

