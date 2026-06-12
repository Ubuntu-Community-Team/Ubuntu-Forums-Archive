---
title: "increments by 2"
date: 2008-01-02
forum: Programming Talk
---

### Post by cowboy.bebop on 2008-01-02
I have a piece of code that I made for john when I was testing it on my network checking to see if I could beat john or not. So I made a numeric gen that will output my int's, but from what it shows its counting by 2's. IN windows it counts by 1's

```

#include <iostream>
#include <stdio.h>
#include <fstream>

using namespace std;

int main(){

	int add;
	int i=0,u=100000,v=200000,w=300000,x=400000;
	char g;

	ofstream a,b,c,d,e,f;

	cout << endl;
	cout << "\tThe program will now generate a numeric pass file\n"
		"\ton the desktop named numeric.lst...\n" << endl;

	cout << "\tto avoid complication with outputing all int's to\n"
		"\ttext file, the file size may increase drastically.\n"
		"\tTo narrow that possibility you are given a selection\n"
		"\tbelow to chose from options to avoid avoid such an\n"
		"\timmense file size.\n" << endl;

	cout << "\t\tA:   1->100K \tB: 100K->200K \tC:200K->300K\n"
		"\t\tD: 300->400K \tE: 400K->500K \tF: 500K->600K\n" << endl;

	cout << "You may continue to select your option: "; cin >> g;

	switch ( g ) {

case 'a':
	a.open("numeric00.lst");
	for (i = 0; i < 100000; i++){
	a << i << "\n";
	i++;} break; a.close();

case 'b':
	b.open("numeric01.lst");	
	for (u = u; u < 200000; u++){
	b << u << "\n";
	u++;} break; b.close();

case 'c':
	c.open("numeric02.lst");
	for (v = v; v < 300000; v++){
	c << v << "\n";
	v++;} break; c.close();

case 'd':
	d.open("numeric03.lst");	
	for (x = 0; x < 400000; x++){
	d << x << "\n";
	x++;} break; d.close();

/*case 'e':
	e.open("numeric04.lst");	
	for (i = 0; i < 999999999; i++){
	e << i;
	i++;} break;

case 'f':
	f.open("numeric05.lst");
	for (i = 0; i < 999999999; i++){
	f << i;
	i++;} break;*/

default:
	cout << "That key was incorrect please try again!";

		}
	return 0;}

```

I am still working on it, ALso before I was trying to set the value such i to be declared as:

int i = 00000000;

but when it compiles or is output to the screen it shows i as just one zero. I know that 00000000 is just the same as 0 but I would like it to output all zero's as maybe a string but then convert to an integer when its incrementing you know like:

00000001
00000002

instead of:

1
2

*smell*my*drift*?

Ooo I guess since im here, I have also been having some issues with trying to increment something that is 14-16 digits long, I have found this impossible for the compiler or at least impossible unless someone figured a way around it not me.

---

### Post by dwhitney67 on 2008-01-02
Use setfill() and setw() to achieve the output style you desire.

As for the values incrementing by two, why are you incrementing them twice in each of the for-loops?

Also, you should avoid declaring a variable within the main() block that is only used within a for-loop.  This includes the variables used to store the initial values.

Here's a cleaner chunk of code (for a case statement):
[PHP]    case 'a':
        ofstream a( "numeric00.lst" );
        if ( a )
        {
          for (int i = 0; i < 100000; ++i)
          {
            a << setfill('0') << setw(8) << i << endl;
          }
          a.close();
        }
        break;[/PHP]


P.S.  You will need to #include <iomanip> for the setfill() and setw().

---

### Post by dwhitney67 on 2008-01-02
> **Ubuntwha said:**
> 
Ooo I guess since im here, I have also been having some issues with trying to increment something that is 14-16 digits long, I have found this impossible for the compiler or at least impossible unless someone figured a way around it not me.
Can you be more specific concerning this issue?  An unsigned int can only hold a 32-bit number (with a max value of 2^32 - 1).  If you require a larger number, then use a 'unsigned long long' or a 'uint64_t'.  The latter (and a boat-load of other convenient types) are defined in /usr/include/stdint.h.

Usage:

[PHP]#include <iostream>
#include <stdint.h>

int main()
{
  uint64_t value = ~0;
  std::cout << "value = " << value << std::endl;
  return 0;
}
[/PHP]

---

### Post by cowboy.bebop on 2008-01-02
Yeah I declared say 'i' as a 14 digit number

int i = 99999999999999;

and thenn if I try to compile it, I get the compiler yelling at me that I cant do it, now if I prune off 5 digits It compiles fine.

btw the setfill put a huge smile on my face, ty.

```


/*case 'e':
	e.open("numeric04.lst");	
	for (i = 0; i < 999999999; i++){
	e << i;
	i++;} break;

case 'f':
	f.open("numeric05.lst");
	for (i = 0; i < 999999999; i++){
	f << i;
	i++;} break;*/

```

Had been commented out cause I wasnt done with the other block yet, Until I figured out what its purpose was I was going to come back to it

---

### Post by dwhitney67 on 2008-01-02
I would recommend that you stop thinking in term of "digits" and focus more in terms of "bits".

If all you require is a counter that will hold unsigned integers, then don't declare an 'int'; declare an 'unsigned int' .  You'll get one extra bit for storage.

If you require a large number, as in your example, try defining a 'uint64_t'.  When declaring large numbers, it is necessary to append a 'ULL' to the number.  For instance:

[PHP]uint64_t value = 18446744073709551615ULL;   // ULL = Unsigned Long Long[/PHP]

---

### Post by cowboy.bebop on 2008-01-02
I got ya, will keep in mind, I will attemtp to fix the rest ty

---

### Post by stroyan on 2008-01-03
You can get a leading zeros effect by setting a width and fill character.
But it would put the '-' sign of negative numbers after the leading zeros.```
#include <iomanip>
using namespace std;
    cout << setw(8) << setfill('0') << 78 << endl;
    cout << setw(8) << setfill('0') << 3374 << endl;
```

---

