---
title: "simple C++ code question."
date: 2009-10-05
forum: Programming Talk
---

### Post by rtumatt on 2009-10-05
This code is in no way finished but what the eventual aim of the program is to record lower case key strokes then display them when the program terminates as displayed in case a and b (other letters i have not yet implemented). The code runs fine and does what i want however when the loop runs it asks twice for an input but takes the first as blank and the second letter you enter a letter. Why is this?


#include <iostream>
using namespace std;
int main()

{ 
  char letter;
  int num = 0;
  string textSaved;
  while (letter !='0'){
  cout << "enter any character : ";
  cin.get(letter);
  switch (letter) {
  case 'a': //cout << "thats an a";
		num ++;
		textSaved = textSaved +  'a';
            break;
  case 'b': //cout << "\nthats a b";
		num ++;
		textSaved = textSaved +  'b';
		break;
  case 'c': cout << "thats a c"; 
            break;
  case 'd': cout << "\nthats a d"; 
            break;
  case 'e': cout << "\nthats a e"; 
            break;
  case 'f': cout << "\nthats a f"; 
            break;
  case 'g': cout << "\nthats a e"; 
            break;
  default: cout << "\nthats not A B or C";
  } 
 // cout; "\n";
  }

cout << "\n\n\n" << "Letters pressed : " <<textSaved << "\n\n\n";
cout <<"number of letters: " << num << "\n\n";

}

---

### Post by MadCow108 on 2009-10-05
because you input 2 characters when you press a letter and enter, the letter and the newline
you can solve this by ignoring the newline after the cin.get:
cin.ignore(somenumber,'\n');

---

### Post by dwhitney67 on 2009-10-05
Rather than using a switch to examine which character was selected, check its value against the values used to identify ASCII characters.

For instance:
```

char   letter;
string textSaved;

do
{
   // read letter; see MadCow108's suggestion too!

   // check if input is a lowercase letter
   if (letter >= 0x61 && letter <= 0x7A)
   {
      textSaved += letter;
   }
} while (letter != 0);

cout << "Lowercase letters entered are: " << textSaved << endl;

```

You can find out more about the ASCII values by examining the manpage for ascii.
```

man ascii

```

---

### Post by rtumatt on 2009-10-05
Thank you for both providing me with a simple fix (which worked thankyou) and a more complex fix which has got me thinking. Again thanks for both replies guys i appreciate it alot.

---

### Post by fct on 2009-10-06
(letter >= 'a' && letter <= 'z') works too.

---

### Post by Arndt on 2009-10-06
> **fct said:**
> (letter >= 'a' && letter <= 'z') works too.

And if you care about non-ASCII letters too, islower is better.

---

