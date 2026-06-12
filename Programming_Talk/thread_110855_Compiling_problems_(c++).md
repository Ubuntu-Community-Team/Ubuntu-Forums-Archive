---
title: "Compiling problems (c++)"
date: 2005-12-31
forum: Programming Talk
---

### Post by janfsd on 2005-12-31
Hi! ive got some problems with c++, well im learning it so im still a newbie in it...
i was trying to make a library and a implementation file...so i make the header which in this case looks like this:

```
/* Library HEat

-------------------*/

const double HeatOfFusion = 79.71; //calorias por gramo

const double HeatOfVaporization = 539.55; // calorias por gramo

/*-------------------------------------------------------------------------------------------------------
	Program FahrToCelsius
------------------------------------------------------------------------------------------------------*/

double FahrToCelsius(double);

/*-------------------------------------------------------------------------------------------------------
		Program CelsiusToFahr
-------------------------------------------------------------------------------------------------------*/

double CelsiusToFahr(double);
```

and after i made the implementation file which looks like this...

```

#include "Heat.h"
using namespace std;
//-------------------------------------------------------------------------------------------------------

double FahrToCelsius(double FTemp)
{
	return (FTemp - 32.0) / 1.8;
}

//-------------------------------------------------------------------------------------------------------

double CelsiusToFahr(double CTemp)
{
	return CTemp * 1.8 + 32.0;
}

```

the header i saved like Heat.h and the imp. file like Heat.C
while trying to compile Heat.C with g++ Heat.C -o Heat

it gives me the following error:

```
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/crt1.o: In function `_start':
../sysdeps/x86_64/elf/start.S:109: undefined reference to `main'

```


am i doing sthing wrong?? plz any kind of help would be appreciated! thx in advance, by the way happy new year!!

---

### Post by LordHunter317 on 2005-12-31
GCC is trying to create a program, not a library, because you didn't tell it otherwise.

Adding '-shared' at the end of the line ought to generate a shared library, IIRC.

---

### Post by janfsd on 2005-12-31
thx that worked! 

but now when i want to use the library in another program, for example here:

```
#include <iostream>
#include "Heat.h"

using namespace std;
int main()
{
	cout << "\nFahr to Cel.\n";

double FahrTemp;

cout << "\nTemperature en Fahr: ";
cin >> FahrTemp;

double CelsiusTemp = FahrToCelsius(FahrTemp);

cout << "\n\t" <<FahrTemp
	<< " in F is "
	<< CelsiusTemp << " in Celsius . \n\n";

return 0;
}
```

i get this error while i try to compile

```
juanito@janfsd:~/c++$ g++ temp2.cpp -o temp2
/tmp/ccn1IXtI.o: In function `main':
temp2.cpp:(.text+0x43): undefined reference to `FahrToCelsius(double)'
collect2: ld returned 1 exit status

```

all the files are in the same folder, should i add sthing more to the g++ command?

---

### Post by LordHunter317 on 2005-12-31
Yes, you have to add the appropriate -l command.  If the library is named 'foo.so', you need to add -lfoo.  You may need to make it -l./foo to get the search to work correctly, or some other variant.  It has been some time since I've done linking of custom shared libs on Linux.  Reading the GCC/LD info docs may be a good idea.

---

### Post by janfsd on 2006-01-01
ive done how u say, however i dont have a *.so file, when i was compiling the implementation file with
```
g++ Heat.C -o Heat -shared
```
it worked and produce a file just named   Heat
and when i was trying this -lHeat with
```
g++ temp2.cpp -o temp2 -lHeat
```
i got this output:
```
/usr/bin/ld: cannot find -lHeat
collect2: ld returned 1 exit statu
```
even with -l./Heat it gets the same answer...
ive been reading the doc but till now i dindt find something to help me :(

---

### Post by thumper on 2006-01-01
Just a stab but I don't think that the current directory is defined as a library location, so you need to add -L or --library-path
```

g++ temp2.cpp -o temp -lHeat -L.

```
HTH

---

### Post by LordHunter317 on 2006-01-01
You need to rename your library to something .so.

---

### Post by thumper on 2006-01-01
```
g++ Heat.C -o libHeat.so -shared
g++ temp2.cpp -o temp -lHeat -L.
```

---

### Post by cylon359 on 2006-01-01
Actually, to build a shared library, you should do something like:

gcc -o libheat.so -shared -Wl,-soname,libheat.so -fPIC -Os Heat.C

---

### Post by janfsd on 2006-01-01
ok now it compiles, but whenever i try to run it with ./temp2
it gives me an error:

```
./temp2: error while loading shared libraries: libHeat.so: cannot open shared object file: No such file or directory

```

maybe to run it i should link it? or what should i do to run it?

---

### Post by thumper on 2006-01-01
If your machine is like mine you don't have an LD_LIBRARY_PATH set by default.

```
export LD_LIBRARY_PATH=.
./temp2

```

---

### Post by janfsd on 2006-01-01
thanks a lot for the help!!! :D 
now everything works great!!!

---

