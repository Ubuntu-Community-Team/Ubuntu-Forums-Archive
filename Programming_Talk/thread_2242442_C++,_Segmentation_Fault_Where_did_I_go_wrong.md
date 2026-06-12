---
title: "C++, Segmentation Fault: Where did I go wrong?"
date: 2014-09-01
forum: Programming Talk
---

### Post by cppneo on 2014-09-01
Hi, I'm pretty new to C++ and very new to Ubuntu. 
I'm having an issue where I run my program, a "Hello World" program using getopt to choose a name and number of repeats, I get the error "Segmentation Fault: Core Dumped". I am aware that this means that something is pointing to memory that either doesn't exist or is inaccesible, but I am not able to pinpoint exactly where in the code this is occuring. 

Here is the code:

```
#include <iostream>
#include <getopt.h>


using namespace std;

int main(int argc, char* argv[]){
if (argc <= 1) //checks to see if there is a given argument.
{
    
    cout << "Hello World!" << endl; //if not, simple output.
}

else
{
int m;
char *name = NULL;
int t;
char *r = NULL; //number of repeats
int ir = *r; //converts char to int
int c = 0; //counter

while ((m = getopt (argc, argv, "n:t:")) > -1) 
         switch (m)
           {
           case 'n':
             name = optarg; //if so, grabs arguments
             break;
       case 't':
         r = optarg;
             break;
             }

while (c >= ir)
    c = c+1;
    cout << "[" << c << "]" << "Hello " << name << "!" << endl;
        
    return 0;
}
}
```

(Sorry about formatting, again, I'm pretty new at this)

One thing to note is that another version of this program I had to write simply used a name, no repeats (ie ./a.out -n Bob had to return "Hello Bob!", while this program ./a.out -t 3 -n Bob has to return "Hello Bob!" 3 times) and it works perfectly fine, yet if I even try to just give this program a name to use in place of "World", it gives me the same error.

For reference, here is the code for the previous program:

```
#include <iostream>
#include <getopt.h>


using namespace std;

int main(int argc, char* argv[]){
if (argc <= 1) //checks to see if there is a given argument.
{
    
    cout << "Hello World!" << endl; //if not, simple output.
}

else
{
int n;
char *name = NULL;

while ((n = getopt (argc, argv, "n:")) > -1) 
         switch (n)
           {
           case 'n':
             name = optarg; //if so, grabs arguments
             break;
           }


    cout << "Hello " << name << "!" << endl;
        
    return 0;
}
}
```

Any help would be greatly appreciatted 

Note: I may use some methods in my code that may be less efficient than other potential methods, but as long as they work, the methods should remain. Reason being, my professor is a very "Teach yourself" type and if he sees any codes that either look a) Above our level or B) like another students, he will deduct points and you have to go through long tedious tasks in order to regain those points... so yeah.

Thanks!

---

### Post by steeldriver on 2014-09-01
Hello and welcome to the forums - I have changed your QUOTE tags to CODE tags to better preserve the formatting

I *think* you will find that the issue is you can't simply copy pointer types returned in the optarg - you need to allocate space for the returned character array (e.g. as 'char name[128]' instead of 'char *name'; or dynamically using malloc) and use a strcpy (or - better - strncpy) so copy the *contents*. But let's wait for one of the real coders to chime in.

---

### Post by cppneo on 2014-09-01
Yeah thanks, I couldn't find the code tags for some reason but knew they were there. 

If I'm interpretting what youre saying correctly, shouldn't my first code (second one up there) not have worked?

---

### Post by steeldriver on 2014-09-01
Ooops - looks like I was wrong about that - from the [GNU getopt documentation]("http://www.gnu.org/software/libc/manual/html_node/Using-Getopt.html#Using-Getopt"):

> If the option has an argument, getopt returns the argument by storing it in the variable optarg. ** You don't ordinarily need to copy the optarg string, since it is a pointer into the original argv array, not into a static area that might be overwritten.**

In fact I think the issue is in the conversion of your numeric argument - your code

```

char *r = NULL; //number of repeats
int ir = *r; //converts char to int

```

doesn't really make sense - instead try something like

```

int ir;

```

then 
```

       case 't':
**          ir = atoi(optarg);**
             break;
             }

```

(you can use an intermediate char *r but it's not really needed). *In fact I think atoi is deprecated so you should probably use a long integer type and strtol instead.*

---

### Post by cppneo on 2014-09-01
Yeah I just figured out that's where the error comes from. Thanks for the input.

---

