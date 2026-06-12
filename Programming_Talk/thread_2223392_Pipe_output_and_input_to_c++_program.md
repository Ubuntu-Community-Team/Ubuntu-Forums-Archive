---
title: "Pipe output and input to c++ program"
date: 2014-05-10
forum: Programming Talk
---

### Post by slooksterpsv on 2014-05-10
I'm a little confused here, here's what I'm trying to accomplish. I made a small app to try things like this out to see if it worked but it didn't. I created an application called lcase which converts strings to lowercase and even removes spaces - basically it takes in the string, puts it in a vector, outputs the string, but if an option is entered it removes the spaces via cout << arg[x] << " ";

Here's what i want to be able to do:

```

#hello.txt
Hello World!
#/hello.txt

$ cat hello.txt | lcase
hello world!
$ cat hello.txt | lcase -l
helloworld!

```

Even in reverse I'd like to do:
```

lcase -l | cat hello.txt
helloworld!
lcase | cat hello.txt
hello world!

```

It works if I do this:

```

lcase `cat hello.txt`

```

But that's not how I want it to work. Do I need to create pipes or read from stdout or what do I do...

---

### Post by dwhitney67 on 2014-05-10
You should be able to do the following:
```

$ cat hello.txt | lcase
hello world!

$ cat hello.txt | lcase -l
helloworld!

$ lcase < hello.txt
hello world!

$ lcase -l < hello.txt
helloworld!

$ lcase `cat hello.txt`
hello world!

$ lcase -l `cat hello.txt`
helloworld!

```

If your program is not supporting these features, then perhaps it is not reading from standard-in (std::cin), but instead merely analyzing the command line arguments using argc/argv.

Why not post your code so we can see what you are doing?

P.S.  You do not require a vector to accomplish the results shown above.

---

### Post by slooksterpsv on 2014-05-10
I'm addicted to vectors, don't ask why, I know they take up a bit a memory (and I keep forgetting to clear them), but here's my code:
```

#include <iostream>
//#include <stdio.h>
#include <string>
#include <vector>
#include <locale>

using namespace std;

string makeLowerCase(string x)
{
	locale loc;
	string ret = "";
	for(string::size_type i =0; i<x.length(); i++)
		ret += tolower(x[i], loc);
	return ret;
}

int main(int argv, char* argc[])
{
	bool combine = false;
	vector <string> arglist;
	unsigned int x;
	for(x = 1; x < argv; x++){
		string arg = argc[x];
		if(arg == "-l"){
			combine = true;
		}else {
			arglist.push_back(arg);
		}
	}
	for(x = 0; x < arglist.size(); x++) {
		if(combine)
//			printf("%s", arglist[x].c_str());
			cout << makeLowerCase(arglist[x]);
		else
//			printf("%s ", arglist[x].c_str());
			cout << makeLowerCase(arglist[x]) << " ";
	}
	cout << "\n";
	return 0;
}

```

---

### Post by dwhitney67 on 2014-05-11
Ok, now I can what you are doing.

A few comments:

1.  You can name the parameters in the main() function anything you want, but traditionally the int parameter is named 'argc' (argument count) and the char pointer array is named 'argv' (argument variables or vector).  There's also a third parameter (that most programmers rarely use) called 'envp', which is also a char pointer array, and contains environment variables.

2.  On line 23 of your code, you are comparing an unsigned int with an int (argv).

3.  Your program does not support quoted input (e.g. "Hello World") in cases where the white-space must be stripped away.
```

$ ./lcase "Hello World"      # This one is ok
hello world

$ ./lcase -l "Hello World"   # This one does not work
hello world

```

As for receiving data via pipes, there are bash shell types that I indicated earlier.  One involves using the vertical bar, which is typically referred to as the pipe symbol (that is |), and the other is the standard-in redirection symbol, or the less-than character <.

The only way to receive data using these types of constructs is to read from standard-in.  Your program will need to determine whether it is going to process exclusively the command-line arguments (via argc and argv), or read from standard-in.  If the latter, there may be one argument passed to you via argc/argv, and that is the -l option.

Note, after you have augmented your program to support reading from standard-in, you should be able to test it like this:
```

$ ./lcase
Hello World      <--- Your input
hello world      <--- app output
<ctrl-d>

$ ./lcase -l
Hello World      <--- Your input
helloworld       <--- app output
<ctrl-d>

```

P.S.  In lieu of the vector, consider combining argc/argv input into a space-delimited string.  For example:
```

std::string input;
int start;

//TODO:  Determine if start should be set to 1 or 2, depending whether the -l option is provided.  Or consider using getopt().

// Combine all cmd-line input into one large string.
for (int i = start; i < argc; ++i)
{
    input += argv[i];
    input += " ";
}

```

---

### Post by slooksterpsv on 2014-05-11
Gotcha, thanks! =D

---

