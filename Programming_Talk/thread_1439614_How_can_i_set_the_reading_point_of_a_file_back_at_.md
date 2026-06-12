---
title: "How can i set the reading point of a file back at the start??"
date: 2010-03-26
forum: Programming Talk
---

### Post by fasoulas on 2010-03-26
How can i set the reading point in a file back at the start of the file after something like this

```
   int i=0 ;
	
	
	while(readF >> code[i] >> num[i] >> price[i])
	{
		i++ ;
	}


```

then i want to do something like this

```

        char strg_get[80]

        while( !readF.eof() )
	{
		readF.getline(strg_get,80) ; 
		cout << strg_get << endl ;
	}

```

to show all the contents of the file on the screen

---

### Post by schauerlich on 2010-03-26
[http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)

seekg and seekp will move the get and put pointers, respectively.

```
readF.seekg(ios::beg);
readF.seekp(ios::beg);

```

ifstreams have a get pointer, ofstreams have a put pointer, and fstreams have both.

---

### Post by fasoulas on 2010-03-26
> **schauerlich said:**
> [http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)

seekg and seekp will move the get and put pointers, respectively.

```
readF.seekg(ios::beg);
readF.seekp(ios::beg);

```

ifstreams have a get pointer, ofstreams have a put pointer, and fstreams have both.

is there any other way to do it 
If i close the file and reopen it?

because i am not familiar with seek commands

---

### Post by fasoulas on 2010-03-26
i have tried 
```

readF.seekg(ios::beg) ;

```

and it doesn't work
nothing happens when i call the function

---

### Post by schauerlich on 2010-03-26
> **fasoulas said:**
> i have tried 
```

readF.seekg(ios::beg) ;

```

and it doesn't work
nothing happens when i call the function

That only moved the pointer back. Now you can do whatever operations you want with it, starting from the beginning.

file.txt:
```
This is a file with some words in it.
This is another line.

```

fileio.cpp:
```
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main() {
  fstream inf;
  string s;
  
  inf.open("file.txt", ios::in);
  
  getline(inf, s);
  cout << s << endl;
  
  getline(inf, s);
  cout << s << endl;
  
  inf.seekg(ios::beg);
  
  getline(inf, s);
  cout << s << endl;
  
  inf.close();
  
  return 0;
}
```

```
eric@river:~/src/cpp/practice$ g++ -Wall fileio.cpp -o fileio.out
eric@river:~/src/cpp/practice$ ./fileio.out 
This is a file with some words in it.
This is another line.
This is a file with some words in it.

```

---

### Post by fasoulas on 2010-03-26
> **schauerlich said:**
> That only moved the pointer back. Now you can do whatever operations you want with it, starting from the beginning.

file.txt:
```
This is a file with some words in it.
This is another line.

```

fileio.cpp:
```
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main() {
  fstream inf;
  string s;
  
  inf.open("file.txt", ios::in);
  
  getline(inf, s);
  cout << s << endl;
  
  getline(inf, s);
  cout << s << endl;
  
  inf.seekg(ios::beg);
  
  getline(inf, s);
  cout << s << endl;
  
  inf.close();
  
  return 0;
}
```

```
eric@river:~/src/cpp/practice$ g++ -Wall fileio.cpp -o fileio.out
eric@river:~/src/cpp/practice$ ./fileio.out 
This is a file with some words in it.
This is another line.
This is a file with some words in it.

```

i will see your code and try to learn from it,thanks for posting it
i managed to do what i wanted by closing and reopening the file .

```
	readF.close() ;
	readF.open("data.txt") ;
```

---

### Post by dwhitney67 on 2010-03-26
> **fasoulas said:**
> i have tried 
```

readF.seekg(ios::beg) ;

```

and it doesn't work
nothing happens when i call the function

Before calling that method, make sure you clear the state of the fstream:
```

...

readF.clear();
readF.seekg(0, ios::beg);

...

```
P.S.  seekg(ios::beg) works, but that is merely due to coincidence that ios::beg is equal to 0.  According to the C++ documentation, the single-arg form of seekg() takes a position, whereas the two-arg form takes a position and a relative direction indicator.

---

