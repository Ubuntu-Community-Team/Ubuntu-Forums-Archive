---
title: "[C++] Splitting a string with spaces in it."
date: 2009-03-20
forum: Programming Talk
---

### Post by Nexusx6 on 2009-03-20
Hi everyone ^^ I'm writting a simple text based adventure game, and I'm trying to implement a feature that would allow the user to give two commands at once, like this:
```
>>move north
```
as opposed to doing something like
```
>>move
Where do you want to move?
>>north
```

What I thought I would do was write a split_string function that would write words to an array every time it ran into a space using "find" and "substr" from the string class -- however, this hasn't been working out so well :( I can't seem to find a way to return the words that this function splits apart. Is there a way to do this? Is there a function built in to handle this?

Thanks.

---

### Post by Sinkingships7 on 2009-03-20
I think you pretty much got it. If it were me, I'd read the input as a string, check for validity, and parse the string into an array, one element for every word. Then check through the array for keywords pertaining to the situation and carry out the responding sequence of events. I can't currently think of a better way to do it.

---

### Post by johnl on 2009-03-20
Depending on how advanced you want to get with handling commands, you could use a regular expression.

The simplest way to simply split the string though, is to use a stringstream:

```

#include <sstream>
#include <string>
#include <iostream>
#include <vector>
using namespace std;


int main(int argc, char* argv[]) 
{
   string input = "move a little to the left";
   
   vector<string> results;
   stringstream s(input);
   while(!s.eof()) {
      string tmp;
      s >> tmp;
      results.push_back(tmp);
   }

   // items now stored in results:
   for(vector<string>::const_iterator i = results.begin();
       i != results.end();
       ++i) {
       cout << *i << endl;
   }
   

}

```

---

### Post by dwhitney67 on 2009-03-20
What you need is a string tokenizer; I believe I posted one a couple of weeks ago here on the forum.  It was, if I recollect correctly, based on using std::string's find_first_of() and substr().

If you know that you will always have a command with an arg (i.e. "move north"), then you can also try using an std::stringstream.  Here's an example:
```

#include <string>
#include <sstream>
#include <iostream>

int main()
{
  std::string userInput;

  std::cout << "Enter command: ";
  getline(std::cin, userInput);

  std::string cmd;
  std::string arg;
  std::stringstream ss(userInput);

  iss >> cmd;
  iss >> arg;

  std::cout << "cmd = " << cmd << '\n'
            << "arg = " << arg
            << std::endl;
}

```
I do not recommend this approach if you plan will accept more than one arg following the command.  But the choice is yours.

---

### Post by nvteighen on 2009-03-21
Why not **strtok()** from cstdio/stdio.h?

---

### Post by dwhitney67 on 2009-03-21
> **nvteighen said:**
> Why not **strtok()** from cstdio/stdio.h?

strtok() does not accept a const char*, as provided by std::string.

I should further add, that strtok() can be used if the contents of std::string are copied to a temporary buffer.  I've demonstrated this "un-elegant" solution in a previous post someplace.

---

### Post by Sockerdrickan on 2009-03-21
> **dwhitney67 said:**
> What you need is a string tokenizer; I believe I posted one a couple of weeks ago here on the forum.  It was, if I recollect correctly, based on using std::string's find_first_of() and substr().

If you know that you will always have a command with an arg (i.e. "move north"), then you can also try using an std::stringstream.  Here's an example:
```

#include <string>
#include <sstream>
#include <iostream>

int main()
{
  std::string userInput;

  std::cout << "Enter command: ";
  getline(std::cin, userInput);

  std::string cmd;
  std::string arg;
  std::stringstream ss(userInput);

  iss >> cmd;
  iss >> arg;

  std::cout << "cmd = " << cmd << '\n'
            << "arg = " << arg
            << std::endl;
}

```I do not recommend this approach if you plan will accept more than one arg following the command.  But the choice is yours.
iss >> cmd;
iss >> arg;

Should be written as ss>>cmd>>arg;
remember it's streams! :) :guitar:

---

### Post by dwhitney67 on 2009-03-21
I found some code I posted a few weeks ago on the forum, and it had a bug.

I hope the code below is better (well, it seems to work!).
```

#include <algorithm>
#include <iostream>
#include <string>
#include <vector>

std::vector<std::string>
tokenize(const std::string& str, const std::string& delim)
{
  std::vector<std::string> tokens;

  size_t pos = 0;
  size_t loc = str.find_first_of(delim, pos);

  if (loc == std::string::npos)
  {
    tokens.push_back(str);
  }
  else
  {
    while (pos != std::string::npos)
    {
      tokens.push_back(str.substr(pos, loc - pos));

      pos = (loc == std::string::npos ? loc : loc + 1);
      loc = str.find_first_of(delim, pos);
    }
  }

  return tokens;
}


void displayString(const std::string& str)
{
  std::cout << str << std::endl;
}


int main()
{
  const std::string        line   = "move north|quickly|silently";
  std::vector<std::string> tokens = tokenize(line, " \t|");

  std::for_each(tokens.begin(), tokens.end(), displayString);
}

```

It really would be nice if the C++ standard offered a tokenizer that did not involve re-inventing the "wheel" as I have shown above.  The Boost library offers a tokenizer, but that means that one must have the library... which is not always possible on certain projects.

---

