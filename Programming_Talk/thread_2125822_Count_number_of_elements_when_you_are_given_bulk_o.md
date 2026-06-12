---
title: "Count number of elements when you are given bulk of elements at once(as input) in c++"
date: 2013-03-15
forum: Programming Talk
---

### Post by hatsoff on 2013-03-15
I'm beginner to c++;
Today i was reading a piece of information during this i found a very large number of 1's(a long string of 1's) and interested to see how many are they, being a human i wanted to safe my effort and thought lets create a program that count number of 1's for me:
It would be working like this:
I will copy number of 1's from text and paste it in the IDE as input/initialize to array or a variable ,and as output i would have how many number of 1's there are. 
Plot:
Although i thought couple of ideas but this idea seems best:
Use array and initialize it with the 1's (copy and paste from text, but i gotta place "," one after another to initialize and that's annoying), then determine the size of array(how many elements are there in the array);
how can i do this? or i m not allowed to do this in c++?
Regards,

---

### Post by ofnuts on 2013-03-15
Without C++, in some editor (or with sed and wc), remove all end-of-line characters, and insert one such end-of-line character after all the 1s and then count the 
lines (or ask the editor to display the line numbers). 

With C++ (but this smells like homework), just paste the whole thing in a string, then scan the string character by character (using an iterator) and count the 1's.

.

---

### Post by r-senior on 2013-03-15
You *could* write a program like this:

```
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string paste_here = "[COLOR="#FF0000"]1111[/COLOR]";

	cout << paste_here.size() << endl;
}

```

But that wouldn't really be a very good program because you would have to paste into the source and recompile to count another string of '1'. It would be better to write a program that accepts input from standard input or a file so that you can re-use it for different strings of '1'.

---

### Post by hatsoff on 2013-03-15
```
#include <iostream>
using namespace std  ;

int counter ;

int main(void)
{
        // i want to give input like this and want 1's to be read one by one until newline encounter
     
     intput = 11111111111111111111111111111111111111111111111 \n or \0 ;   //suppose i have copy from text      and  directly paste here
     
  
    while (input == "\n")           // or \0 in case of array
    {
          count = count + 1 ;
          return counter ;
    }
    cout << count ;      
    
    system("PAUSE") ;
    return 0;
    

}
```

---

### Post by hatsoff on 2013-03-15
isn't require a intelligent program or it will solve simply?

---

### Post by r-senior on 2013-03-15
That's not going to compile. I think you need to look at some C++ tutorials.

[http://www.cplusplus.com/reference/string/string/begin/](http://www.cplusplus.com/reference/string/string/begin/)

The example on that page is a good starting point for your program.

---

### Post by hatsoff on 2013-03-15
Thank you that was hidden from me!!
what about this?

#
         #include <iostream>
#include <string>
int counter;
int main (void)
{
  std::string str ("11111111111111111111111111111111111111111111111111111111111");
  for ( std::string::iterator it=str.begin(); it!=str.end(); ++it)
  {
      
      counter = counter + 1 ;
      return counter ;
  }
  std::cout << counter ;
  

    system("PAUSE") ;

}
#

---

### Post by r-senior on 2013-03-15
Did you compile and test it?

---

### Post by ofnuts on 2013-03-15
> **hatsoff said:**
> Thank you that was hidden from me!!
what about this?

#
         #include <iostream>
#include <string>
int counter;
int main (void)
{
  std::string str ("11111111111111111111111111111111111111111111111111111111111");
  for ( std::string::iterator it=str.begin(); it!=str.end(); ++it)
  {
      
      counter = counter + 1 ;
      return counter ;
  }
  std::cout << counter ;
  

    system("PAUSE") ;

}
#

If your string only contains ones, you can use **[FONT=lucida console]string.size()[/FONT]** directly, without scanning it. You can even use **[FONT=lucida console]sizeof "11111111111111111111111"[/FONT]** directly...

---

### Post by hatsoff on 2013-03-16
@r-senior compiled successfully but command prompt just appears for nano second(i mean just appears and disappears although it has statement system("PAUSE") ;),
@ofnuts like this?:

#include <iostream>
#include <string>

int main (void)
{
  std::string str ("11111111111111111111111111111111111111111111111111111111111");
  str.size();
  system("PAUSE") ;
  return 0 ;
}

---

### Post by r-senior on 2013-03-16
I am slightly surprised the code you posted compiled. You must have a more lenient compiler than I do:

```
     intput = 11111111111111111111111111111111111111111111111 \n or \0 ;   //suppose i have copy from text      and  directly paste here
     
  
    while (input == "\n")  

```

The reason it returns without showing any output is that you had a return statement in your for loop:

```

for ( std::string::iterator it=str.begin(); it!=str.end(); ++it)
{

    counter = counter + 1 ;
    **[COLOR="#FF0000"]return counter ;[/COLOR]**
}
```

An example using size() is given in post #3.

Could you try and use code tags when you post code? There is a '#' button in the posting toolbar that does it, or you can hand-code the code tags (just leave out the space I added after the first square bracket):

[ code]My code here ...[/code]

---

### Post by ofnuts on 2013-03-16
> **hatsoff said:**
> @r-senior compiled successfully but command prompt just appears for nano second(i mean just appears and disappears although it has statement system("PAUSE") ;),
@ofnuts like this?:

#include <iostream>
#include <string>

int main (void)
{
  std::string str ("11111111111111111111111111111111111111111111111111111111111");
  str.size();
  system("PAUSE") ;
  return 0 ;
}
str.size() return the size of the string, but you have to print it... and this makes me wonder if you have ever written any kind of working code in the past?

Btw, system("pause") is also highly questionable, there are plenty of ways in C/C++ to wait for user input without having to call external programs.

---

### Post by r-senior on 2013-03-16
I think it would be good for you to work through a C++ Tutorial one step at a time, compiling and running each example, and ask questions if you get stuck at any point.

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

