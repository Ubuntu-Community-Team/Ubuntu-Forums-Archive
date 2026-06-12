---
title: "Could not convert to bool. HELP!"
date: 2010-11-06
forum: Programming Talk
---

### Post by cgroza on 2010-11-06
Hello, I made a secret language for me and my friends originaly in python.
The python version works great, but I want to do a c++ version. I started translating the syntax and al c++ specific actions but now I have 2 errors. 
The error says: 
/home/cgroza/hackers language/tester.cpp|96|error: could not convert ‘phrase’ to ‘bool’|

This happens in a for loop. Here is the code:

```
            for (letter; phrase;){

                if (letter == "a")
                    sentence = sentence + "~" ;
                if (letter == "b")
                    sentence = sentence + "@" ;

                if (letter == "c")
                    sentence = sentence + "#" ;

                if (letter == "d")
                    sentence = sentence + "$" ;

                if (letter == "e")
                    sentence = sentence + "%" ;

                if (letter == "f")
                    sentence = sentence + "^" ;

                if (letter == "g")
                    sentence = sentence + "&" ;

                if (letter == "h")
                    sentence = sentence + "*" ;

                if (letter == "i")
                    sentence = sentence + "(" ;

                if (letter == "j")
                    sentence = sentence + "{" ;

                if (letter == "k")
                    sentence = sentence + ")" ;

                if (letter == "l")
                    sentence = sentence + "_" ;

                if (letter == "m")
                    sentence = sentence + "-" ;

                if (letter == "n")
                    sentence = sentence + "+" ;

                if (letter == "o")
                    sentence = sentence + "=" ;

                if (letter == "p")
                    sentence = sentence + "|" ;

                if (letter == "q")
                    sentence = sentence + "\\" ;

                if (letter == "r")
                    sentence = sentence + "," ;

                if (letter == "s")
                    sentence = sentence + "<" ;

                if (letter == "t")
                    sentence = sentence + "." ;

                if (letter == "u")
                    sentence = sentence + ">" ;

                if (letter == "v")
                    sentence = sentence + "/" ;

                if (letter == "w")
                    sentence = sentence + "?" ;

                if (letter == "x")
                    sentence = sentence + ";" ;

                if (letter == "y")
                    sentence = sentence + ":" ;

                if (letter == "z")
                    sentence = sentence + "]";

                if (letter == " ")
                    sentence = sentence + " ";

                if (letter.find("0123456789"))
                    sentence = sentence + letter;


                if (letter.find("~!@#$%^&*()_+|-=\\,./<>?;\':\"[]{}"))
                    sentence = sentence + "`"+letter ;

            }
```I am new to c++ but I have a bit of python experience.
Thanks.

---

### Post by cgroza on 2010-11-06
With that for loop I am trying to do something like:

for letter in phrase:
>>>do something()
in python.

---

### Post by cgroza on 2010-11-06
Anyone?

---

### Post by cgroza on 2010-11-06
Ok, what is the c++ equivalent of  the python "in"?

---

### Post by johnl on 2010-11-06
```

#include <string>
#include <iostream>
#include <algorithm> // for option #3

void print_char(char c) {
  std::cout << c;
}

int main() {
  std::string phrase = "this is a test";

  // option one
  for(int i = 0; i < phrase.length(); ++i) {
	std::cout << phrase[i];
  }
  std::cout << std::endl;

  // option two
  for(std::string::const_iterator i = phrase.begin();
	  i != phrase.end(); ++i) {
	std::cout << *i;
  }
  std::cout << std::endl;

  // option three
  std::for_each(phrase.begin(), phrase.end(), print_char);

};

```

Also, C++ has a 'switch' statement which might be super useful in this case (assuming you dont want to use a std::map or something).

```

for(i = 0; i < phrase.length(); ++i) {
    char c = phrase[i];
    switch(c) {
        case 'a':
            /* do something */
            break;
        case 'b':
            /* do something */
            break;
        case 'c':
            /* do something */
            break;
        default:
            break;
    }
}

```

---

### Post by cgroza on 2010-11-06
Ok, thanks, reduced those 15 erors to just 2. I bet I will be back. Thank you very much.
Ill convert to case after. Now i need the basic functionality.

---

### Post by cgroza on 2010-11-06
Ok, just one error left. I don't even know if it will work if it compiles. I get this:
```
/usr/include/c++/4.4/bits/stl_algo.h|4200|error: no match for call to &#8216;(std::basic_string<char, std::char_traits<char>, std::allocator<char> >) (char&)&#8217;|
```

It says it instantiated from line 98. HELP! this is over my head.

---

### Post by schauerlich on 2010-11-06
What do you expect us to be able to do with no code? And why aren't you using a std::map (sort of like a python dictionary)?

---

### Post by cgroza on 2010-11-06
No, I am doing a secret language decoder. All want to do is to take the input, go through it letter by letter and decode it. I do this with if statements but i have problems with the for loop, the first one more exactly on line 98. Ill post the code again. Line 98 = first line.
```

std::for_each(phrase.begin(), phrase.end(), letter);




                if (letter == "a")
                    sentence = sentence + "~" ;
                if (letter == "b")
                    sentence = sentence + "@" ;

                if (letter == "c")
                    sentence = sentence + "#" ;

                if (letter == "d")
                    sentence = sentence + "$" ;

                if (letter == "e")
                    sentence = sentence + "%" ;

                if (letter == "f")
                    sentence = sentence + "^" ;

                if (letter == "g")
                    sentence = sentence + "&" ;

                if (letter == "h")
                    sentence = sentence + "*" ;

                if (letter == "i")
                    sentence = sentence + "(" ;

                if (letter == "j")
                    sentence = sentence + "{" ;

                if (letter == "k")
                    sentence = sentence + ")" ;

                if (letter == "l")
                    sentence = sentence + "_" ;

                if (letter == "m")
                    sentence = sentence + "-" ;

                if (letter == "n")
                    sentence = sentence + "+" ;

                if (letter == "o")
                    sentence = sentence + "=" ;

                if (letter == "p")
                    sentence = sentence + "|" ;

                if (letter == "q")
                    sentence = sentence + "\\" ;

                if (letter == "r")
                    sentence = sentence + "," ;

                if (letter == "s")
                    sentence = sentence + "<" ;

                if (letter == "t")
                    sentence = sentence + "." ;

                if (letter == "u")
                    sentence = sentence + ">" ;

                if (letter == "v")
                    sentence = sentence + "/" ;

                if (letter == "w")
                    sentence = sentence + "?" ;

                if (letter == "x")
                    sentence = sentence + ";" ;

                if (letter == "y")
                    sentence = sentence + ":" ;

                if (letter == "z")
                    sentence = sentence + "]";

                if (letter == " ")
                    sentence = sentence + " ";

                if (letter.find("0123456789"))
                    sentence = sentence + letter;


                if (letter.find("~!@#$%^&*()_+|-=\\,./<>?;\':\"[]{}")){
                    sentence = sentence + "`"+letter ;

            }
        }
    }
```

---

### Post by schauerlich on 2010-11-07
Instead of using a ton of if statements, why not put your "language" into a [std::map](http://www.cplusplus.com/reference/stl/map/)? Then, the "translation" would only be this:

```
std::map<char, char> my_map;
std::ifstream infile("foo.txt", std::ifstream::in);
std::ifstream lang("language.txt", std::ifstream::in); // store you language in this file, in case you want to change it later
char from, to, c;


// initialize map, assuming the file looks like this:
// a~b@c# ... etc
// of course you can refine the formatting 
while (lang >> from >> to) {
    my_map[from] = to;
}

while (infile >> c) {
    std::cout << my_map[c] << std::endl;
}
```

Of course this is very rough (and completely untested), but it should get you in the right direction.

---

### Post by cgroza on 2010-11-09
Thanks, but I do this as a practice for the FOR loops. Your advice is super useful.

---

### Post by dwhitney67 on 2010-11-09
Simple for-loop example with a string containing N characters:
```

#include <string>
#include <ctype.h>

...

std::string  str    = "some string";
const size_t strLen = str.size();

**for (size_t i = 0; i < strLen; ++i)**
{
   switch (tolower(str[i]))
   {
      case 'a':
          //do something a-ish
          break;

      case 'b':
          //do something b-ish
          break;

      ...

      case 'z':
      default:
          // do something z-ish
          break;
   };
}

```
Hopefully the example helps.  But seriously, what you should do is spring for a C++ book that you can reference as you learn the language.  Using the forum to learn a language is lame, and frankly a waste of everybody's time.

---

### Post by worksofcraft on 2010-11-09
> **dwhitney67 said:**
> 
...But seriously, what you should do is spring for a C++ book that you can reference as you learn the language.  Using the forum to learn a language is lame, and frankly a waste of everybody's time.

I don't think it's a waste of anyone's time. Lots of people read these threads and learn new ways of looking at things. Many of us arrive here from search engines and sometimes we even decide it's quite a good forum, or thread and might even post our own contributions :)

After all, it's easy enough to skip the ones that don't interest us ... isn't it? ;)

p.s. I notice this thread had 121 vistors and has only 12 posts so that's 10 times more people reading it than are responding :shock:

---

### Post by GenBattle on 2010-11-10
Post full code.

Without posting full code we can't know what includes you do/not have, how/where you have declared your variables, etc. etc.

My guess is that one problem is that letter is of type char, not type string, so you need to wrap the char constants in single quotes '' rather than double quotes "".

I could recommend the tutorial [here]("http://www.cplusplus.com/doc/tutorial/") as a great starting point.

---

### Post by schauerlich on 2010-11-10
> **cgroza said:**
> Thanks, but I do this as a practice for the FOR loops. Your advice is super useful.

```
#include <iterator>
#include <fstream>
#include <iostream>
#include <string>
#include <map>

using namespace std;

int main(void) {
  map<char, char> my_map;
  ifstream lang("language.txt", ifstream::in);
  char from, to;
  string phrase("abcd");

  // initialize map, assuming the file looks like this:
  // a~b@c# ... etc
  // of course you can refine the formatting 
  while (lang >> from >> to) {
    my_map[from] = to;
  }

  for (string::iterator itr = phrase.begin(); itr != phrase.end(); ++itr) {
	cout << my_map[*itr];
  }
  
  return 0;
}

```

Now it's a for loop, using fancy iterators. Magic!

---

### Post by Vox754 on 2010-11-10
> **dwhitney67 said:**
> 
Hopefully the example helps.  But seriously, what you should do is spring for a C++ book that you can reference as you learn the language.  Using the forum to learn a language is lame, and frankly a waste of everybody's time.

I agree!

When I read that the OP originally used Python, my thought was "Python is supposed to help learn new languages". However, that doesn't mean that anyone can just "translate" line-by-line code from one language to the other, let alone hack their way around it, until it works.

Python helps understand higher-level concepts, such as Object Orientation, classes, instance methods, inheritance, and also procedural programming, but some other reference is still needed to learn proper C++.

---

### Post by cgroza on 2010-11-10
Ok, thank you. You solved the problem. It stll goes with the for loop and the if statements, but it gets the job done. 
I will perfect it and I will post the final code.
Thank you!

---

### Post by wkhasintha on 2010-11-11
What do you expect us to be able to do with no code? And why aren't you using a std::map (sort of like a python dictionary)?

---

