---
title: "C++ undefined reference"
date: 2011-02-12
forum: Programming Talk
---

### Post by cozzbp on 2011-02-12
Hi, I am having a problem that I just cannot figure out for the life of me.  I am a Java programmer, just starting C++. 

I am trying to write a general outline of my program, but it won't compile.

Here is my code:

```

//Crawler.h
#ifndef CRAWLER_H
#define CRAWLER_H

#include <string>


//Stores an object of type word, with a value, and a list of occurences
class Crawler {

private:
	
	Index* index;
	
	
public:
	
	//!  Constructor
	Crawler();
	~Crawler();


		


};



#endif
```


```

//Crawler.cpp
#include <iostream>
#include <string.h>
#include <stdlib.h>
#include <cstring>
#include <fstream>
#include <string>
#include "..\inc\Crawler.h"

using namespace std;

Crawler::Crawler() 
{

}

```



```

#include <iostream>
#include <string.h>
#include <stdlib.h>
#include <cstring>
#include <fstream>
#include <string>
#include "../inc/Crawler.h"
using namespace std;



int main(int argc, char * argv[]) 
{
	Crawler* crawler = new Crawler();



}

```

Here is what I get when I try to compile:

```

Test.cpp:(.text+0x20): undefined reference to `Crawler::Crawler()'
collect2: ld returned 1 exit status


```

I have other Classes that I can successfully include, and I really can't see the difference between them and the Crawler class.  Any insight you could offer would be amazing.  Thank you all.

---

### Post by worksofcraft on 2011-02-12
> **cozzbp said:**
> Hi, I am having a problem that I just cannot figure out for the life of me.  I am a Java programmer, just starting C++. 
....
Here is what I get when I try to compile:

```

Test.cpp:(.text+0x20): undefined reference to `Crawler::Crawler()'
collect2: ld returned 1 exit status


```

I have other Classes that I can successfully include, and I really can't see the difference between them and the Crawler class.  Any insight you could offer would be amazing.  Thank you all.

I suspect you may be forgetting to add your Crawler.cpp file to the compile command. It should be something like:

```

g++ main.cpp Crawler.cpp

```

because each .cpp file produces a separate object module.
Quite often people put all these modules in a software library.

p.s. To make my life easy I name all my implementation files that do not contain a "main" as with a .cc suffix and only the ones with a main() in them are .cpp. That way I can compile and run any project of mine as follows:
```

g++ -c *.cc
g++ main.cpp *.o
./a.out

```

evidently renaming a.out is quite a good idea once you are satisfied it works ;)

---

### Post by cozzbp on 2011-02-12
Thank you so much! I couldn't figure it out for the life of me.  The naming things *.cc is a great idea.  Thanks again!

---

