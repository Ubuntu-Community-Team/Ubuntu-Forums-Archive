---
title: "C++ question"
date: 2018-07-12
forum: Programming Talk
---

### Post by Reddoug on 2018-07-12
Hello

  I am trying to figure out why I am getting errors when trying to run Hello World C++ program. I have tried to find a solution but I am not able to.

  1 #include <iostream>
  2 
  3 int main(int argc, char *argv [])
  4 {
  5     std::cout << "Hello World!" << std::endl;
  6 
  7     return 0;
  8 }

Error

./helloworld.cpp: line 3: syntax error near unexpected token `('
./helloworld.cpp: line 3: `int main(int argc, char *argv [])'


I used   gcc helloworld.cpp -o helloworldcpp    to compile in Ubuntu. Don't see why it works in Code Blocks in Windows but not Ubuntu.
I used ./helloworld.cpp to try and run it. Permissions were changed to 755

I also tried to create with C and I get the same error when trying to run it.

  1 #include <stdio.h>
  2 int main(int argc, char *argv[])
  3 {
  4    printf("Hello World!\n");
  5    return 0;
  6 }

./helloworld.c: line 2: syntax error near unexpected token `('
./helloworld.c: line 2: `int main(int argc, char *argv[])'


Stumped
Doug

---

### Post by steeldriver on 2018-07-12
... because you are trying to run the source code in a shell - you need to compile it first, then run the resulting binary executable

```

g++ -o helloworld helloworld.cpp

./helloworld

```

---

### Post by Reddoug on 2018-07-13
Thank you for your reply

I ran g++ -o helloworld helloworld.cpp and received same error when I tried ./helloworld.cpp. I tried ./helloworld and it ran properly. 
I always thought I needed the .cpp extension.

Thank you for your help.
Doug

---

### Post by steeldriver on 2018-07-13
EDIT: nevermind - I reread your post and it seems like you've got it now

---

