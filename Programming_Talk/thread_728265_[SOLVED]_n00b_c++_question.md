---
title: "[SOLVED] n00b c++ question"
date: 2008-03-18
forum: Programming Talk
---

### Post by chris200x9 on 2008-03-18
my question is, why no matter what I input for ans it invokes main again?


```


#include <iostream>
#include <string>
#include <cstdlib>

void menu();
using namespace std;
int main()
{

    int counter2;
    string word2;
    string word;
    char ans;
    int counter = 0;

   menu();

    cin >> word;    

    counter2 = word.length();
    counter2 = counter2 - 1;

    while (counter2 != -1 )
    {

        word2[counter] = word[counter2];


       counter++;

counter2--;

    }         

  
    if ( strcmp(word.c_str(), word2.c_str()) == 0)

    {

        cout << "you got yourself a palindrome there, buddy" << endl;

    }

    else
        cout << "no palindrome for you!" << endl;

	cout << "do you want to check another word? [y/n]" << endl;
	cin >> ans;

	if (ans == 'Y' || 'y')
	{

		main();

	}

	else

	cout << "bye!";

	return 0;

}

void menu()

{

	 cout << "input a word you think is a palindrome" << endl;

 }



```

---

### Post by jespdj on 2008-03-18
This line is wrong:

if (ans == 'Y' || 'y')

Can you see why? It is equivalent to this:

if ((ans == 'Y') || 'y')

The expression 'y' is always true.
It should be:

if (ans == 'Y' || ans == 'y')

---

### Post by chris200x9 on 2008-03-18
ohhh my gosh! I knew that >_< thank you so much!

---

### Post by pmasiar on 2008-03-18
You have two ways to avoid this kind of bugs:

1) Learn priorities of operators
2) Learn to put explicit parens to force compiler understand what you want.

---

### Post by scourge on 2008-03-18
> ```
if ( strcmp(word.c_str(), word2.c_str()) == 0)
```

Dude, how did you come up with this? The awesome thing about C++ strings is that you can actually do it easier like this:
```

if (word == word2)

```

---

