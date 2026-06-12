---
title: "Bottles of beer on the wall?"
date: 2011-06-30
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-06-30
Hi idk why it was closed but i would like to share what i did with the first challenge:

Warning Windows:

```

#include <cstdio>
#include <cstdlib>
#include <windows.h>
#include <iostream>
#include <string>

using namespace std;

int main()
{
	
int a;
string c, d, e, f, F, s; 

c = " bottles of beer on the wall, ";
d = " bottles of beer";
e = "Take one down and pass it around, ";
f = " no more bottles of beer on the wall";
F = "No more bottles of beer on the wall";	
s = "Go to the store and buy some more, ";
	
for (a = 99; a > 1; a --)
{

cout << a << c << a << d << endl << e << a - 1 << c << endl << endl;


}

cout << a << c << a << d << endl << e << f << endl << endl << F << " no more " << d << endl;	
	
a = 99;

cout << s << a << c;	
	
	
	
cin.get();
return 0;
}

```

For Linux it would be like this:
```


#include <cstdio>
#include <cstdlib>
#include <iostream>
#include <string>

using namespace std;

int main()
{
	
int a;
string c, d, e, f, F, s; 

c = " bottles of beer on the wall, ";
d = " bottles of beer";
e = "Take one down and pass it around, ";
f = " no more bottles of beer on the wall";
F = "No more bottles of beer on the wall";	
s = "Go to the store and buy some more, ";
	
for (a = 99; a > 1; a --)
{

cout << a << c << a << d << endl << e << a - 1 << c << endl << endl;

Sleep(8000);

}

cout << a << c << a << d << endl << e << f << endl << endl << F << " no more " << d << endl;	
	
a = 99;

cout << s << a << c;	
	
	
	
cin.get();
return 0;
}
 
```


I think the sleep(); function, Sleep(); on Windows, could be added for sing along LOL too bad was closed was a good thread.

---

### Post by juancarlospaco on 2011-06-30
...I was thinking of [Bottle]("http://www.bottlepy.org") framework :(

---

### Post by ThatCoolGuy220 on 2011-06-30
Por tu nombre creo que hablas español no?

---

### Post by schauerlich on 2011-06-30
Just a tip - use better variable names. abcdef is not a good way to go through life.

No sabías? Todos hablamos español.

Pues... quizás no todos. Pero no me importan lo otros. :)

---

### Post by ThatCoolGuy220 on 2011-07-01
XD

Nooo no lo sabia jeje.

Yes those variable names arent that creative, but for a beginer is ok

---

### Post by Tony Flury on 2011-07-01
Just curious - why in your "windows" version do you include windows.h - and then it seems not use anything from it.

I would have thought that your linux version would compile perfectly on windows - the only difference between the two versions is the Sleep function you use in your "linux" version.

---

### Post by ThatCoolGuy220 on 2011-07-01
Cause I Have my templates that way, and I was using the Sleep idea but not for the presentation

---

