---
title: "How to convert Windows C++ to run in Ubuntu Terminal."
date: 2011-09-16
forum: Programming Talk
---

### Post by ryn.cor21 on 2011-09-16
I wrote this cool program for Windows DOS prompt and I would like to compile it to run in an Ubuntu terminal. The cc compiler gave me some errors like "cout not declared" and there were also some problems with "system". Any help is appreciated.

```

/*Hello World Program
Ryan Corcoran 9-14-11*/

#include <iostream>
using namespace std;

int main(void)
{
    //Preface
    cout<<"                Information:\n";
    cout<<"This is a \"Hello World!\" program by Ryan Corcoran.\n";
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 1
    cout<<"Hello World!\n";
    cout<<endl;
    cout<<"I am a computer, and I can do many things.\n";
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 2
    cout<<endl;
    cout<<"I can calculate the area of a circle...\n";
    cout<<endl;
    cout<<"-Calculate the Area of a Circle-\n";
    cout<<"           Radius="<<10<<endl;
    cout<<"           Area="<<(3.14*10*10)<<endl;
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 3
    cout<<endl;
    cout<<"          *\n";
    cout<<"          |\\\n";
    cout<<"       ___|_\\_\n";
    cout<<"~~~~~~~\\_____/~~~~~~\n";
    cout<<"~~~~~~~~~~~~~~~~~~~~~\n";
    cout<<"  I can draw boats!!\n";
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 4
    cout<<"          /\\\n";
    cout<<"         /  \\\n";
    cout<<"        /    \\\n";
    cout<<"        | -- |\n";
    cout<<"        |_||_|\n";
    cout<<endl;
    cout<<"   I can draw houses!\n";
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 5
    cout<<"This is my favorite quote:\n";
    cout<<endl;
    cout<<"\"I think, therefore I am\"\n";
    cout<<"              Rene Descartes\n";
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 6
    cout<<"I love my programmer...\n";
    cout<<endl;
    cout<<"Ryan Corcoran\n";
    cout<<"Grade\n";
    cout<<"School\n";
    cout<<"City\n";
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 7
    cout<<"I can calculate that area and perimeter of a rectange!!\n";
    cout<<endl;
    cout<<"Length="<<5<<endl;
    cout<<"Width="<<3<<endl;
    cout<<endl;
    cout<<"Area="<<(3*5)<<endl;
    cout<<"Perimeter="<<(5+5+3+3)<<endl;
    cout<<endl;
    system( "Pause" );
    system( "CLS" );
    
    //Page 8
    cout<<"I can do math problems!\n";
    cout<<endl;
    cout<<"Lengths:\n3.3m\n3.5m\n4.0m\n3.0m\n";
    cout<<endl;
    cout<<"Average Length:\n"<<(3.3+3.5+4.0+3.0/4)<<endl;
    cout<<endl;
    system( "Pause" );
    system( "CLS" );

    //Page 9 -End
    cout<<"That's all for now until Chaper 3.\n";
    cout<<endl;
    cout<<"Have a nice day!!";
    cout<<endl;
    system( "Pause" );
}
```

---

### Post by doyleman on 2011-09-16
your system commands are windows specific. its sorta running batch commands in c++, but batch is windows, and this is linux.

not sure why you're having problems with cout, however.

---

### Post by Smart Viking on 2011-09-17
GNU/Linux version:
```
/*Hello World Program
Ryan Corcoran 9-14-11*/

#include <iostream>
#include <stdlib.h>
#include <stdio.h>
using namespace std;

int main(void)
{
    //Preface
    cout<<"                Information:\n";
    cout<<"This is a \"Hello World!\" program by Ryan Corcoran.\n";
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 1
    cout<<"Hello World!\n";
    cout<<endl;
    cout<<"I am a computer, and I can do many things.\n";
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 2
    cout<<endl;
    cout<<"I can calculate the area of a circle...\n";
    cout<<endl;
    cout<<"-Calculate the Area of a Circle-\n";
    cout<<"           Radius="<<10<<endl;
    cout<<"           Area="<<(3.14*10*10)<<endl;
    cout<<endl;

    getchar();
    system( "clear" );
    
    //Page 3
    cout<<endl;
    cout<<"          *\n";
    cout<<"          |\\\n";
    cout<<"       ___|_\\_\n";
    cout<<"~~~~~~~\\_____/~~~~~~\n";
    cout<<"~~~~~~~~~~~~~~~~~~~~~\n";
    cout<<"  I can draw boats!!\n";
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 4
    cout<<"          /\\\n";
    cout<<"         /  \\\n";
    cout<<"        /    \\\n";
    cout<<"        | -- |\n";
    cout<<"        |_||_|\n";
    cout<<endl;
    cout<<"   I can draw houses!\n";
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 5
    cout<<"This is my favorite quote:\n";
    cout<<endl;
    cout<<"\"I think, therefore I am\"\n";
    cout<<"              Rene Descartes\n";
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 6
    cout<<"I love my programmer...\n";
    cout<<endl;
    cout<<"Ryan Corcoran\n";
    cout<<"Grade\n";
    cout<<"School\n";
    cout<<"City\n";
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 7
    cout<<"I can calculate that area and perimeter of a rectange!!\n";
    cout<<endl;
    cout<<"Length="<<5<<endl;
    cout<<"Width="<<3<<endl;
    cout<<endl;
    cout<<"Area="<<(3*5)<<endl;
    cout<<"Perimeter="<<(5+5+3+3)<<endl;
    cout<<endl;
    getchar();
    system( "clear" );
    
    //Page 8
    cout<<"I can do math problems!\n";
    cout<<endl;
    cout<<"Lengths:\n3.3m\n3.5m\n4.0m\n3.0m\n";
    cout<<endl;
    cout<<"Average Length:\n"<<(3.3+3.5+4.0+3.0/4)<<endl;
    cout<<endl;
    getchar();
    system( "clear" );

    //Page 9 -End
    cout<<"That's all for now until Chaper 3.\n";
    cout<<endl;
    cout<<"Have a nice day!!";
    cout<<endl;
    getchar();
}
```

Name as "file.cpp", and compile with:
```
g++ file.cpp -o helloworld
```
Executable will be named "helloworld".

---

### Post by amingv on 2011-09-17
Above post is correct, but I have a few notes :P:

1. You probably want to include cstdlib instead of stdlib.h for c++
2. You probably want to use cin.get() + cin.ignore() from iostream instead of getchar() from stdio.h.
3. If for some reason you want to use cc instead of g++, just pass the "-l stdc++" flag and it should work fine (although g++ is generally preferred)
4. Use of system() is generally frowned upon (regardless of the target OS), clearing the screen is tricky, but usually can be decently achieved by inserting a bunch of newlines (which is essentially what 'clear' does).

---

### Post by ryn.cor21 on 2011-09-17
You guys are so great. Thank you.

---

