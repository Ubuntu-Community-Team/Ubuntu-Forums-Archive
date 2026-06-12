---
title: "Getting a program to accept input before executing - Yes, it's a newbie question."
date: 2008-04-26
forum: Programming Talk
---

### Post by RudolfMDLT on 2008-04-26
Hi,

I don't know what it's called so could someone please tell me and I'll happily go search Google for it! :)

when you in the terminal do a command:

rsync **-ruv --delete**

What do you call the bold bits? How do you write a c++ application to accept those extra "flags"/"options". I've tried some google searches but ended up with a lot of spam.

Thanks for any pointers,

Rudolf

---

### Post by CptPicard on 2008-04-26
Command line arguments, and they are passed as parameters to the main method. In

```

int main(int argc, char **argv)

```

argv is an array of strings which are the command line args, and argc is the number of said arguments.

---

### Post by heikaman on 2008-04-26
hi...
It's called a command-line argument/option.
"-r" is called a short option , "--recursive" is called (guess what ?) a long option :).

There are two ways to use cmd args:

**1-** parse the arguments yourself (argc holds the number of args and argv is an array of char* to the args) just like **CptPicard** said.

**2-** use getopt to parse the args for you, say you want to make a program that accepts -h for help, -v for verbose and -w for width, you use it like this:

[PHP]
	const char *opts="w:hv"; // w: means w takes an argument, for example -w 500
	char opt;

	while( (opt=getopt(argc, argv, opts))){
		switch(opt){
			case '?':{
				//unknown option
				exit(1);
			}
			case 'h':{
				//print help
				printf("%s\n", help_mesg);
				exit(0);
				break;
			}
			case 'v':{
				//be verbose
				VERBOSE=1;
				break;
			}
			case 'w':{
				//w's argument in optarg
				sscanf(optarg, "%d", &width);
				break;
			}	
		}
	}
[/PHP]

to parse long options read the manual
man 3 getopt
man 3 getopt_long

---

### Post by JupiterV2 on 2008-04-26
There are libraries (can't think of the name off the top of my head) for command-line parsing of arguments. Here is a very basic example:

C
```

#include <stdio.h>

int main(int argc, char** argv)
{
  if( argc != 2 )
    printf("Usage: <program_name> <argument1>\n");
  else
    printf("You typed '%s' as the argument to this program!\n", argv[1]);

  return 0;
}

```


C++
```

#include <iostream>

int main(int argc, char** argv)
{
  if( argc != 2 )
    std::cout << "Usage: <program_name> <argument1>\n";
  else
    std::cout << "You typed '" << argv[1] <<
       "' as the argument to this program!\n";

  return 0;
}

```

You can find a more complete example on the GNU Manual site: [http://www.gnu.org/software/libtool/manual/libc/Example-of-Getopt.html#Example-of-Getopt]("http://www.gnu.org/software/libtool/manual/libc/Example-of-Getopt.html#Example-of-Getopt")

---

### Post by Can+~ on 2008-04-26
For the record, a week ago I was checking "Python in a nutshell", and found an interesting library called "optparse", which, does exactly that.

[PHP]
#!/usr/bin/env python

import optparse

def init():
	p = optparse.OptionParser()
	p.add_option("-l", "--long", action="store_true")
	p.add_option("-n", "--name", default="there")
	
	opts,args = p.parse_args()
	
	if opts.long:
		print "I welcome you",opts.name
	else:
		print "Hello", opts.name

if __name__ == "__main__":
	init()[/PHP]

```
python optsample.py -nWorld
Hello World
```

```
python optsample.py --long -nWorld
I welcome you  World
```

```
python optsample.py --help
Usage: optsample.py [options]

Options:
  -h, --help            show this help message and exit
  -l, --long            
  -n NAME, --name=NAME
```

Maybe there's an optparse for c++?

---

### Post by pmasiar on 2008-04-26
OP: no offense, but as such green newbie, you will be **much** better off to start learning with Python and not C++. See wiki in my sig for links, see sticky FAQ for discussion and poll why.

---

### Post by LaRoza on 2008-04-26
> **Can+~ said:**
> 
Maybe there's an optparse for c++?

Use what is available for C, it will work the same I imagine.

> **pmasiar said:**
> OP: no offense, but as such green newbie, you will be **much** better off to start learning with Python and not C++. See wiki in my sig for links, see sticky FAQ for discussion and poll why.

Anything but C++ IMO.

---

### Post by RudolfMDLT on 2008-04-27
Thanks so much for all the replies guys! I'm used to getting flamed once or twice a year in this part of the forums! ;)

C++ is what the guys at varsity teach in Software 1, and it gets taken further next year in Software 2. I think they start off with C++ as later in the year the IDE to the PIC controllers work with C.

Anyway, for the sake of peace I won't ask what you guys have against C++. :) And as soon as this term's over I'll take your advice on Python to heart!

Thanks again for all the detailed replies, I really appreciate the time that went in to them!

Cheers,

Rudolf

---

### Post by LaRoza on 2008-04-27
> **RudolfMDLT said:**
> 
Anyway, for the sake of peace I won't ask what you guys have against C++. :) And as soon as this term's over I'll take your advice on Python to heart!


See the sticky on the Holy Wars thread...

---

### Post by WW on 2008-04-27
> **CptPicard said:**
> Command line arguments, and they are passed as parameters to the main method. In

```

int main(char **argv, int argc)

```

argv is an array of strings which are the command line args, and argc is the number of said arguments.
CptPicard, you might want to fix your post. It should be argc first.

---

### Post by Patsoe on 2008-04-27
A library that helps you do this in C++:
[http://www.boost.org/doc/libs/1_35_0/doc/html/program_options.html](http://www.boost.org/doc/libs/1_35_0/doc/html/program_options.html)

And yeah, python is fun too. Assuming you're on ubuntu, check out this doc package: [http://packages.ubuntu.com/hardy/doc/diveintopython](http://packages.ubuntu.com/hardy/doc/diveintopython)

Edit: Huh?? The Dive Into Python book is part of a default Hardy installation!? According to aptitude ubuntu-desktop depends on it. That's a bit unnecessary, or?

---

