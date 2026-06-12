---
title: "trying to do something like the ts push to talk"
date: 2007-09-11
forum: Programming Talk
---

### Post by nzadLithium on 2007-09-11
Hey i'm trying to write a program that like teamspeak can catch keys even when they are not in focus.

I found a way to do it using things similar to a key logger.

I'm using this code

```
#include <iostream>
#include <sys/io.h>
#include <stdio.h>

using namespace std;

unsigned char c;
int i = 0;

int main( int argc, char *argv[] )
{
  	if(getuid() || getgid())
  	{
    		printf("Have to be root to perform a iopl()!\n");
    		exit(1);
  	}//perform root checks
	if(iopl(3) == -1)
	{
    		perror("iopl()");
		printf("error!");
    		exit(1); //get required iopl level to access keyboard
  	}
	do 
	{
		c = NULL;
		c = inb(0x60); //catch scan codes from keyboard
		if (c != NULL)
			cout << c << endl; //write scan code to screen
		//fflush(0); //empty all??
	}while (i == 0);
}
```

I'm not sure what fflush is meant to do here but im assuming its clearing all streams?

Anyways i ran this code and my computer threw a spazz. It started opening random things then it just stopped and nothing would respond so i held down the power button :S

I'm just trying to a program running in the background to receive the key signals (and still let the program in focus receive them as well).

What am I doing wrong???

---

### Post by ddrichardson on 2007-09-11
My c is very rusty but would fflush (stdin) not accomplish this?

---

### Post by gnusci on 2007-09-11
You should use:

[PHP]fflush(stdout);[/PHP]

cause your want to print out to the standard output.

for more information:

[http://www.cplusplus.com/reference/clibrary/cstdio/fflush.html](http://www.cplusplus.com/reference/clibrary/cstdio/fflush.html)
[http://www.opengroup.org/onlinepubs/000095399/functions/fflush.html](http://www.opengroup.org/onlinepubs/000095399/functions/fflush.html)

---

### Post by nzadLithium on 2007-09-12
I'm more concerned about why my computer threw a spazz. Any idea's why this wouldnt print out the last key pressed scan code and instead makes my pc go crazy?

---

