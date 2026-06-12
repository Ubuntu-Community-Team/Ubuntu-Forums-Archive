---
title: "C++, (eof) help"
date: 2008-09-11
forum: Programming Talk
---

### Post by Sharpiedeluxe on 2008-09-11
So, quite basically I'm writing a program that accepts input from a user and stores data in an array. However, I want to make it so that when the user hits ctrl+D, that it will ONLY stop reading data. Unfortunately, if I try this normally It will just stop the program completely and go to the end of file. Any suggestions? :)

---

### Post by dwhitney67 on 2008-09-11
I'm not sure what type of data you are trying to read in, whether something simple (such as an int), or something more complex.  Nevertheless, the following should provide a clear example:
[PHP]#include <iostream>
#include <vector>

int main()
{
  int value = 0;
  std::vector<int> array;

  while ( std::cin >> value )
  {
    std::cout << "value: " << value << std::endl;

    array.push_back( value );
  }

  std::cout << "all done... user must have entered ctrl-d" << std::endl;

  // play with array...

  return 0;
}[/PHP]

---

### Post by hildebrand_us on 2008-09-11
You need to write your own signal handler for Ctrl+D to over ride the system one for your program.

---

### Post by dribeas on 2008-09-11
> **Sharpiedeluxe said:**
> So, quite basically I'm writing a program that accepts input from a user and stores data in an array. However, I want to make it so that when the user hits ctrl+D, that it will ONLY stop reading data. Unfortunately, if I try this normally It will just stop the program completely and go to the end of file. Any suggestions? :)

Simple example:
```

#include <iostream>
#include <string>
int main()
{
	std::string word;
	while (true)
	{
		std::cin >> word;
		if ( std::cin.eof() )
		{
			std::cin.clear(); // reset eof flag
			std::cout << "eof received and cleared" << std::endl;
		}
		else
		{
			std::cout << "Readed: " << word << std::endl;
		}
	}
}
// press Ctrl-C to quit the test

```

When you press Ctrl-D (I am assuming you are using linux, on windows Ctrl-D is not EOF) eof flag is marked on the input stream. Read operations on that stream will fail from there on, unless you clear() the eof flag.

Note that if you test with fail() the last operation _has_ failed as eof is not a string (in this case).

I am not sure if this is what you are looking for, if it is not, post your code and what you expect from it.

---

### Post by Sharpiedeluxe on 2008-09-11
Thanks for your help guys! Good examples, I ended up getting it to work. =)

---

