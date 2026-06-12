---
title: "iostream not found"
date: 2012-02-15
forum: Programming Talk
---

### Post by jldoll on 2012-02-15
I'm trying to compile a c++ program with g++.  I've found several search results that show how to use -I, but this isn't working for me. My command is g++ -I /usr/include/c++/4.6  /home/john/Ubuntu\ One/MIT\ 6.096/helloWorld.cpp

The error /home/john/Ubuntu One/MIT 6.096/helloWorld.cc:1:24: fatal error:  iostream : No such file or directory

The file iostream is in two directories: /usr/include/c++/4.6 and /usr/include/c++/4.6.1

I've tried using both paths with the -I option.

I've also tried moving iostream to several locations suggested to be default search paths in other posts.  Removing from those locations when it didn't work.

I noticed when I posted the font changed.  I am using -I (capital i).

Any help would be greatly appreciated.

---

### Post by muteXe on 2012-02-16
what's the code look like?

---

### Post by Simple Name on 2012-02-16
Is your syntax ok ?

```
#include <iostream>

```

---

### Post by r-senior on 2012-02-16
Why does your error refer to .cc when you are compiling .cpp?

If you have the development libraries installed, a hello world in C++ should just work. No need to specify location of standard includes:

```
$ cat hello.cpp 
#include <iostream>

int main()
{
	std::cout << "Hello" << std::endl;
}
$ g++ -o hello hello.cpp
$ ./hello
Hello
```

If it doesn't work, check the paths that gcc is searching for includes (the quotes are backticks - `):

```
`gcc -print-prog-name=cc1plus` -v
```

Hit Ctrl-C when it's shown the include paths and post the output.

---

### Post by jldoll on 2012-02-16
Thanks r-senior.  I copied and pasted your code and it worked. So I took a close look at mine.  Apparently you can't have spaces between the angle brackets < iostream >.  It was subtle in the font I was using, but when I remove the space everything worked as expected.

---

