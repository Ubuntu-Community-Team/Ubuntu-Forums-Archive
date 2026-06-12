---
title: "C++ question"
date: 2008-04-10
forum: Programming Talk
---

### Post by toolbox03 on 2008-04-10
Hi,

How do I create a C++ program that allows me to process the output from ls -ali

It will be pipe to the c++ program using ls -ali | ./a.out

I need to generate a summary report with the c++ program for the following:

Number of files with write permission
Number of link files
Number of directories
Total size of all files
A list of owners who create the files or directories.

---

### Post by tseliot on 2008-04-10
Is it for your homework?

---

### Post by toolbox03 on 2008-04-10
Yes, need a little help to get started. 

I just need to know how to capture the output and process it. 

> **tseliot said:**
> Is it for your homework?

---

### Post by tseliot on 2008-04-10
> **toolbox03 said:**
> Yes, need a little help to get started.
Ok, no problem. Have a look at [this link]("http://www.linuxforums.org/forum/linux-programming-scripting/73711-c-c-how-receive-bash-pipe.html"). As regards the rest, well you will have to figure it out yourself.

Here's the [forum's stance on homework]("http://ubuntuforums.org/showthread.php?t=717011").

---

### Post by toolbox03 on 2008-04-10
Great. Thanks for your help. 

> **tseliot said:**
> Ok, no problem. Have a look at [this link]("http://www.linuxforums.org/forum/linux-programming-scripting/73711-c-c-how-receive-bash-pipe.html"). As regards the rest, well you will have to figure it out yourself.

Here's the [forum's stance on homework]("http://ubuntuforums.org/showthread.php?t=717011").

---

### Post by scourge on 2008-04-10
> **tseliot said:**
> Ok, no problem. Have a look at [this link]("http://www.linuxforums.org/forum/linux-programming-scripting/73711-c-c-how-receive-bash-pipe.html").

For just reading input, it's easier to use popen():
```

#include <iostream>
#include <cstdio>
#include <cstdlib>
#include <cstring>
using namespace std;

int main(void)
{
	FILE *fp;
	char input_buffer[256];
	
	// Open a pipe for reading
	fp = popen("ls -l", "r");
	if (!fp) {
		cerr << "Couldn't open the pipe" << endl;
		return EXIT_FAILURE;
	}
	
	// Read input from the pipe
	while (fgets(input_buffer, sizeof input_buffer, fp) != 0)
		cout << input_buffer;
	
	// Close the pipe
	if (pclose(fp)) {
		cerr << "Couldn't close the pipe" << endl;
		return EXIT_FAILURE;
	}
	
	return EXIT_SUCCESS;
}

```

---

