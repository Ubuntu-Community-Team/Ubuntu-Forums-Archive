---
title: "C++ While Loop help"
date: 2009-07-01
forum: Programming Talk
---

### Post by Swenghk on 2009-07-01
I was working on a text-based game and I want the program to continue prompting the user until he/she enters a valid answer...Here is what i have, but it won't work...what's wrong with it?

```
while (true)
	{
		cout << "\n\nChoose: ";
		cin >> menuChoose;
		
		if (menuChoose == 1)
		{
			newGame();
			break;
		}
		
		if (menuChoose == 2)
			credits();
		
		if (menuChoose == 3)
			quitGame();
			
		else
		{
			cout << "\nYour choice was invalid!";
		}
```

---

### Post by credobyte on 2009-07-01
```
else {
    cout << "Wrong answer! \n";
    continue;  // should start the while loop over and over again until satisfied ( if )
}
```

Still learning tough :P

---

### Post by WRDN on 2009-07-01
If it won't compile, its because you haven't closed the while loop.

Change it to this and it will work:

```

while (true)
	{
		cout << "\n\nChoose: ";
		cin >> menuChoose;

		if (menuChoose == 1)
		{
			newGame();
			break;
		}

		if (menuChoose == 2)
			credits();

		if (menuChoose == 3)
			quitGame();

		else
		{
			cout << "\nYour choice was invalid!";
		}
	}

```

---

### Post by Martin Witte on 2009-07-01
You have to make sure menuChoose is evaluated only once per loop
```
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

void newGame() { cout << "new game" << endl; }
void credits() { cout << "credits" << endl; }
void quitGame() { cout << "quit" << endl; }

int main()
{
	int menuChoose(0);

	while (true)
	{
		cout << endl << endl << "Choose: ";
		cin >> menuChoose;
		if (menuChoose == 1)
		{
			newGame();
			break;
		}
		else if (menuChoose == 2)
		{
			credits();
		}
		else if (menuChoose == 3)
		{
			quitGame();
			break;
		}
		else
		{
			cout << "Your choice was invalid!" << endl;
		}
	}

	return 0;
}
```

A kind request: please always post a minimal example which compiles and shows your problem (or if you have a cryptic compiler error which shows the error)

---

### Post by Swenghk on 2009-07-01
I tried continue, but it gives me this

```
Choose:
      Your choice was invalid!

Choose:
      Your choice was invalid!

Choose:
      Your choice was invalid!

Choose:
      Your choice was invalid!

Choose:
      Your choice was invalid!


```

It gets stuck in an infinite loop...

---

### Post by .Maleficus. on 2009-07-01
You will always be stuck in an infinite loop with the code you have (and were given).  This should be the indicator:
```
while (true)
```
If it never evaluates to false, why would it stop?

---

### Post by c0mput3r_n3rD on 2009-07-01
you can also just do this: (which i find easier)

while(menuChoose != 1 || menuChoose != 2 || menuChoose != 3)
{
    cout << "wrong choose\n";
    cout << "Re-enter: ";
    cin >> menuChoose;
}
/* then do a   if(menuChoose == 1) { /*do w/e */ }
                     else if(menuChoose == 2) { /*do w/e*/ }
                     else /*do w/e*/

--That's just me though

---

### Post by dwhitney67 on 2009-07-01
I believe the example provided earlier are fine, but only for certain cases.

I bet the OP is trying to input values other than integers, and that is what is throwing his application for a spin.

So borrowing Martin Witte's example, and tweaking it a bit, I came up with this working example:
```

include <iostream>

using std::cout;
using std::cin;
using std::endl;

void newGame() { cout << "new game" << endl; }
void credits() { cout << "credits" << endl; }

int main()
{
        unsigned int menuChoose(0);
        bool quit = false;

        while (!quit)
        {
                cout << "1. New Game.\n"
                     << "2. Credits.\n"
                     << "3. Quit.\n\n"
                     << "Choose: ";

                cin >> menuChoose;

                if (!cin.good() || menuChoose < 1 || menuChoose > 3)
                {
                        cout << "Your choice was invalid!" << endl;
                        cin.clear();
                        cin.ignore(1024, '\n');
                        continue;
                }

                switch (menuChoose)
                {
                   case 1: newGame(); break;
                   case 2: credits(); break;
                   case 3: quit = true; break;
                }
        }

        return 0;
}

```
Note that the issue was resolved with the usage of cin's clear() and ignore() methods.  The rest was merely reorganization of the code.

---

### Post by Swenghk on 2009-07-01
> **.Maleficus. said:**
> You will always be stuck in an infinite loop with the code you have (and were given).  This should be the indicator:
```
while (true)
```
If it never evaluates to false, why would it stop?

You provide an exit...like break, a function call, or continue

---

### Post by unknownPoster on 2009-07-01
> **c0mput3r_n3rD said:**
> you can also just do this: (which i find easier)

while(menuChoose != 1 || menuChoose != 2 || menuChoose != 3)
{
    cout << "wrong choose\n";
    cout << "Re-enter: ";
    cin >> menuChoose;
}
/* then do a   if(menuChoose == 1) { /*do w/e */ }
                     else if(menuChoose == 2) { /*do w/e*/ }
                     else /*do w/e*/

--That's just me though

Except for the fact that your proposed solution won't work. You made a simple flaw in boolean logic...

```


while(menuChoose != 1 && menuChoose != 2 && menuChoose != 3)
{
    cout << "wrong choose\n";
    cout << "Re-enter: ";
    cin >> menuChoose;
}


```

The above is a more appropriate solution...

---

### Post by dwhitney67 on 2009-07-02
> **unknownPoster said:**
> ...

while(menuChoose != 1 && menuChoose != 2 && menuChoose != 3)
{
    cout << "wrong choose\n";
    cout << "Re-enter: ";
    cin >> menuChoose;
}

[/code]

The above is a more appropriate solution...

Yes, but it does not address the issue the OP was having.  Please take a look at my previous post where I provided a working solution, although not a very good one.

---

### Post by Swenghk on 2009-07-02
I don't know what it is...maybe it's my compiler or something, but I trieds everything above. But when i run it, it just displays the message indicating the user entered something  wrong endlessly...is there any other way to do this?

---

### Post by Swenghk on 2009-07-02
Wait! Nevermind!

dwhitney67's example worked...I just don't understand some of the member functions you're using...what book contains those?

---

### Post by dwhitney67 on 2009-07-02
> **Swenghk said:**
> Wait! Nevermind!

dwhitney67's example worked...I just don't understand some of the member functions you're using...what book contains those?

Go here:  [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

Look under the section for IOstream Library, or more specifically for istream (click the appropriate box in the diagram).

---

### Post by Swenghk on 2009-07-02
Thank you everybody for all of your help!

---

### Post by Can+~ on 2009-07-02
> **c0mput3r_n3rD said:**
> you can also just do this: (which i find easier)

while(menuChoose != 1 || menuChoose != 2 || menuChoose != 3)
{
    cout << "wrong choose\n";
    cout << "Re-enter: ";
    cin >> menuChoose;
}
/* then do a   if(menuChoose == 1) { /*do w/e */ }
                     else if(menuChoose == 2) { /*do w/e*/ }
                     else /*do w/e*/

--That's just me though

Remember [De Morgan's laws]("http://en.wikipedia.org/wiki/De_Morgan%27s_laws")?

x != 1 || x != 2 || x != 3 <=> !([COLOR=#CC0000]x == 1 && x == 2 && x == 3[/COLOR])

That implies that the value is true when what's [COLOR=#CC0000]inside the parenthesis[/COLOR] is false, and it will always be false for any value of x defined on integers, ergo, condition will always be true.

It's a common mistake ;), I had a lot of them when I first started with logic.

As for the OP, there other fun ways to create menus, instead of "switching" or "if-ing" (if that's a word), you can also create a Hash with pointers to function, which is my personal favorite :KS (Although, it's kinda overkill here, but great thing to learn).

---

