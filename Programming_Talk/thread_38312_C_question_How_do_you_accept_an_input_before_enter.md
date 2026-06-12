---
title: "C question: How do you accept an input before enter is pressed"
date: 2005-05-30
forum: Programming Talk
---

### Post by epb613 on 2005-05-30
Normally using scanf, when a user inputs a character, C doesn't register the fact until after they also press enter.

Is there a way to register the keypress immediatly?

Thanks in advance.

---

### Post by ech0 on 2005-05-31
[QUOTE=epb613]Normally using scanf, when a user inputs a character, C doesn't register the fact until after they also press enter.

Is there a way to register the keypress immediatly?

Thanks in advance.[/QUOTE]

use getchar()

[http://goforit.unk.edu/cprogram/c_030.htm](http://goforit.unk.edu/cprogram/c_030.htm)

---

### Post by epb613 on 2005-05-31
No dice; it still waits for enter.

I did find this though: [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1045691686&id=1043284392](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1045691686&id=1043284392)
Doesn't help me so much, but interesting nonetheless.

Thanks anyhow.

---

### Post by epb613 on 2005-05-31
Haha I found it! After hours of searching... [http://cboard.cprogramming.com/showthread.php?t=27714](http://cboard.cprogramming.com/showthread.php?t=27714)

> 
```
#include <stdio.h>
#include <termios.h>
#include <unistd.h>

int mygetch( ) {
  struct termios oldt,
                 newt;
  int            ch;
  tcgetattr( STDIN_FILENO, &oldt );
  newt = oldt;
  newt.c_lflag &= ~( ICANON | ECHO );
  tcsetattr( STDIN_FILENO, TCSANOW, &newt );
  ch = getchar();
  tcsetattr( STDIN_FILENO, TCSANOW, &oldt );
  return ch;
}

```


---

### Post by ironfistchamp on 2007-04-25
Sorry for bringing this back from the grave but I am having serious problems with the code from the link. 

If I use it twice in a function it seems to break. I had problems that if I used cin >> varname; to get a line of code it would interpret the ending \n as the input for the mygetch() function. Now that I use getline(cin, varname) the second mygetch call doesn't work. 

Source code included

```

#include <iostream>
#include <stdio.h>
#include <string>
#include "character.h"
#include "miscfunc.h"

using namespace std;

void Character::print_stats() {
	cout << "Name: "	<< 	c_name	<<endl;
	cout << "Class: "	<<	c_class	<<endl;
	cout << "Strength: "	<<	stren	<<endl;
        cout << "Intelligence: "<< 	intel	<<endl;
        cout << "Dexterity: "	<< 	dexte	<<endl;
        cout << "Endurance: "	<< 	endur	<<endl;
};


void Character::define_char() {
	// define variables
	string choice_name;
	string choice_class;
	string accept;

	//start loop (easy to repeat if they make a mistake)
	while (true) {

                // put instructions on screen
		cout << "Please choose a name for your character." <<endl;
		cout << "Name: ";
        
                // get the characters name
		getline(cin, choice_name);
		cout << "Please choose a class for your character." <<endl;
		cout << "[w] Warrior" <<endl;
		cout << "[m] Mage" <<endl;
		cout << "[a] Assassin" <<endl;
		cout << "[p] Priest" <<endl;
		cout << "> ";
    
                // use mygetch to get single character... if I use getline above THIS one works fine
		choice_class = mygetch();
		
		
		if (choice_class == "w") {
			choice_class = "warrior";
		};
		
		if (choice_class == "m") {
			choice_class = "mage";
		};

		if (choice_class == "a") {
			choice_class = "assassin";
		};
	
		if (choice_class == "p") {
			choice_class = "priest";
		};

		cout << "Name:  " << choice_name <<endl;	
		cout << "Class: " << choice_class <<endl;
            	cout << "Are these values correct? [Y/n]";

                // this time mygetch will no work. The first time a key is pressed nothing happens
                // the second time it is pressed it will echo the key that was pressed.
		accept = mygetch();

		if (accept != "n") {
			break;
		};
	};
};

```

I get no compilation errors at all and everything runs fine apart from the error mentioned above.

Thanks

Ironfistchamp

---

