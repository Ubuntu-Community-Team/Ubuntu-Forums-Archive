---
title: "Festival.h problems"
date: 2012-03-19
forum: Programming Talk
---

### Post by El Gaz on 2012-03-19
Good day everyone, i didn't know where to ask this so i thought might as well do it here, i been working making an interface for my ubuntu machine using festival.h (the text to speech library),  tried this simple program:

[PHP]```

#include <stdio.h>
#include <stdlib.h>
#include <festival.h>

int main(int argc, char **argv)
{
int heap_size = 300000;  // default scheme heap size
int load_init_files = 2; // we want the festival init files loaded
int flag = 1;
festival_initialize(load_init_files,heap_size);
char name[10]="NULL";

	festival_say_text("type your name");	
	cin >> name;
	cout << "Hello " << name << endl;
	festival_say_text(name);	
  return 0;

} 

```[/PHP]

All i want is for the pc to ask for your name, you type it in and then for the pc to say your name, the first part is ok but when it asks your name it times out regardless if you typed your name or not and just prints out "Hello NULL" and the pc says NULL ignoring the cin, i wonder am i doing something wrong? Does any one have experience with festival.h

thanks in advanced

---

### Post by lisati on 2012-03-19
Mixing C and C++ might not be the best idea. I'm not overly fluent in either, but suspect you might need to include the following in your code:
```
#include <iostream>
```

---

### Post by Zugzwang on 2012-03-20
Are you sure that the code compiles? Other than what lisati said, I am missing an "using namespace std;".

Assuming that the program does compile: I'm not sure if this is really the root cause of the problem, but streaming into a character array is kind of odd.

Try replacing 'char name[10]="NULL";' by 'std::string name = "NULL";' and  'festival_say_text(name);' by 'festival_say_text(name.c_str());'

---

### Post by 11jmb on 2012-03-20
> **lisati said:**
> Mixing C and C++ might not be the best idea. I'm not overly fluent in either, but suspect you might need to include the following in your code:
```
#include <iostream>
```

For the most part, C++ is backwards-compatible with C. Not perfectly, but at very least including/linking C headers/libraries with C++ should be fine.

---

### Post by El Gaz on 2012-03-20
Thank you all for your input on this one and Zugzwang I'll give your suggestion a try when i get home.

---

### Post by El Gaz on 2012-03-22
hello to all, i tried this same program in a Debian machine and it worked perfectly, so i think it is a configuration problem, Thanks to all for your input

---

