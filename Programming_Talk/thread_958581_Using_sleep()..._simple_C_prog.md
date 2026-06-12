---
title: "Using sleep()... simple C prog"
date: 2008-10-25
forum: Programming Talk
---

### Post by kachofool on 2008-10-25
I'm using Geany as my compiler... I'm trying to have the thread sleep for 'x' amount of seconds, output a message, then loop...but the program just seems to halt indefinitely. What am I doing wrong? (tiA)

#include <iostream>
#include <string>
#include <unistd.h>

using namespace std;

int main(int argc, char** argv)
{
	string blah = "blah";
	
	while (1)
	{
		cout << blah;
		sleep (1);
	}
	
	return 0;
}

---

### Post by snova on 2008-10-25
I think sleep() counts in seconds. Try sleep(1) instead, or use the alternate version of sleep that counts in milliseconds.

---

### Post by gomputor on 2008-10-25
***while (1)*** means forever... so it's very logical that your program will halt indefinitely unless you change the loop, isn't it?

---

### Post by snova on 2008-10-25
Oh! That reminds me. Remember to flush the output stream before sleeping, or your output will remain buffered until who-knows-when.

---

### Post by gnusci on 2008-10-26
You have to flush the output stream buffer

[PHP]#include <iostream>
#include <string>
#include <unistd.h>

int main(int argc, char** argv)
{
  std::string blah = "blah";

  while(1){
    std::cout << blah <<std::endl;
    std::cout.flush();
    sleep (1);
  }
  return 0;
}
[/PHP]

[http://www.cplusplus.com/reference/iostream/ostream/flush.html](http://www.cplusplus.com/reference/iostream/ostream/flush.html)

---

### Post by wmcbrine on 2008-10-26
Minor point, but that program is in C++, not C. Also, Geany is an editor/IDE, not a compiler.

---

