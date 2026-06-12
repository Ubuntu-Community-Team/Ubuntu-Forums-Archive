---
title: "C++ question :how to add space in string? and how to create array without value?"
date: 2009-04-22
forum: Programming Talk
---

### Post by AlexenderReez on 2009-04-22
my program =

> #include <iostream>
#include <fstream>

int main()
{

  int i = 0;
  bool  array[5];
  int max_read = 5;
  int amountRead = 0;

  std::ifstream in("part.txt",std::ios::in |std::ios::binary);

  if(!in)
  {

    std::cout<<"Could not open file"<<std::endl;
    return 1;

  }
  //this is where we are reading in the information into our array
  while(in>>array[amountRead]&& amountRead < max_read)
  {

    amountRead++;

  }

  for(i = 0; i < 5; i++)
  {
    printf("%d",array[i]);
  }

  std::cin.get();

  return 0;

}
i just create basic c++ program to get binary input from text file. But the real text file contains data 

```
010101001010101010101011010
```

instead of 

> 1 0 1 0 1 0 

noted that it should be space between each number .any help please to add space for number that doesn't have gap between each other.

and another one is i define array length as 5 but what if i dont know how many max_read?how to define that?
please help

---

### Post by Pollox on 2009-04-22
There are a number of different ways to read data in from a file stream.  In this case, you could use "get" ([http://www.cplusplus.com/reference/iostream/istream/get/](http://www.cplusplus.com/reference/iostream/istream/get/)) to read in one character at a time.  Or, read the whole string in with >>, and then iterate over the characters in the string as you would with an array or vector.  So, you don't have to add a space between each number.

If you want to create an array, but you don't know the size ahead of time, use a vector.  In this case, vector< bool > vectorname; would declare the vector.  I suggest you read up on those.

---

### Post by Arndt on 2009-04-22
> **AlexenderReez said:**
> my program =


i just create basic c++ program to get binary input from text file. But the real text file contains data 

```
010101001010101010101011010
```

instead of 



noted that it should be space between each number .any help please to add space for number that doesn't have gap between each other.

and another one is i define array length as 5 but what if i dont know how many max_read?how to define that?
please help

It seems the specification of the task is somewhat unclear. Is the format of the infile fixed, and simply given to you? How is it defined? It looks to me to consist of a number of bits, with no separators, and then you have to read character by character and check if you got a 0 or 1 for each one. How to group them into numbers doesn't appear from your description. Where does the number 5 come from?

If the size of the input data is "arbitrarily large", you can either allocate something reasonably big, like 2048, or else begin by determining the size of the file, allocate the array, and then read.

---

### Post by AlexenderReez on 2009-04-22
> **Pollox said:**
> There are a number of different ways to read data in from a file stream.  In this case, you could use "get" ([http://www.cplusplus.com/reference/iostream/istream/get/](http://www.cplusplus.com/reference/iostream/istream/get/)) to read in one character at a time.  Or, read the whole string in with >>, and then iterate over the characters in the string as you would with an array or vector.  So, you don't have to add a space between each number.

If you want to create an array, but you don't know the size ahead of time, use a vector.  In this case, vector< bool > vectorname; would declare the vector.  I suggest you read up on those.


i tried to store data.txt file in array,it failed ...help correct this code please --->

```
#include <iostream>
#include <fstream>
using namespace std;

int main () {


  int i, max_read = 5, amountRead = 0; 
  bool array[5];
  char c, str[256];
  ifstream is;

  cout << "Enter the name data text file( usually data.txt): ";
  cin.get (str,256);

  is.open (str);        // open file

  while (is.good())     // loop while extraction from file is possible
  {
    array[amountRead] = is.get();       // get character from file
    if (is.good())
      cout << array[amountRead];
  }

  is.close();           // close file

  return 0;
}
```

vector < bool > vectorname is complicated for me...do you mind to give example of its usage....and how does it can help my program?


> **Arndt said:**
> It seems the specification of the task is somewhat unclear. Is the format of the infile fixed, and simply given to you? How is it defined? It looks to me to consist of a number of bits, with no separators, and then you have to read character by character and check if you got a 0 or 1 for each one. How to group them into numbers doesn't appear from your description. Where does the number 5 come from?

If the size of the input data is "arbitrarily large", you can either allocate something reasonably big, like 2048, or else begin by determining the size of the file, allocate the array, and then read.

i'm trying to get binary (0101010101001) data from 2 text files...which is might contains more than 10000 numbers...and i don't know the quantity..and 

i need to multiply those two...which is using binary method...please do give example...

---

### Post by Pollox on 2009-04-22
There's much more to vectors than I can cover in a single post, so I'll just give you a link to detailed documentation: [http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/) .  Of course, there's other sites with references on c++ functions and data structures, but that just happens to be my favorite.  I will cover a short example for use in your code.

vector< bool > name; creates a vector (an array of dynamic size) of type bool called name.
It's similar to
bool name[5], except now you don't specify the size to be 5.

Now, to add elements to your vector, read in the element from your file:
element = is.get()
 and then go:
name.push_back( element )

By the way, it looks like you've got the "get" stuff figured out.  Well done.  One thing you have to be careful with get is detecting the end of file (the >> operator takes care of that more easily), but it looks like the good() function takes care of that.  If you ever run into issues with get(), be sure to check your logic to make sure it's not reading too far/assigning nonsense.

---

### Post by tneva82 on 2009-04-22
> **AlexenderReez said:**
> 
vector < bool > vectorname is complicated for me...do you mind to give example of its usage....and how does it can help my program?

```

vector<bool> myVector;

myVector.resize(preferedSize); 
/* not neccessary but in speed critical programs if you are expecting to add lots of stuff 
this helps for speed. It initially contains room for 5(IIRC) values and if you add more it
internally creates new vector of bigger size and copies old vector to new vector. If you 
add 1000 values that's 995 times copying vector to new vector...And if vector happens to contain classes with tons of values(worst case in my program: Could be thousands of values! Needless to say I make damn sure I resize() vector :D*/

for(as long as you want) {
myVector.push_back(new value);
}

```

You can access values either via iterator, .at(index) method or good old [index] style. Iterators are good when doing for loop for every element. Worthwhile to check indexes for array boundaries with other methods. Iterator would work like this:

```

for(vector<bool>::iterator it=myVector.begin();it!=myVector.end();it++) {
//and access the value by (*it). Like if( (*it) ) to see wether it's true or alse
}

```

That should help a bit. Vectors are great. Definetly worth studying and they aren't THAT hard to figure out from here: [http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

I mean if _I_ can get it so can anybody ;-)

---

### Post by Arndt on 2009-04-22
> **AlexenderReez said:**
> 


i'm trying to get binary (0101010101001) data from 2 text files...which is might contains more than 10000 numbers...and i don't know the quantity..and 

i need to multiply those two...which is using binary method...please do give example...

I suggest you first concentrate on how to perform the computation, regardless of language. That is, given two binary numbers, where you read the bits one at a time, you are to multiply the two numbers. Try to do it on paper alone, using two small numbers. I suppose the most significant bit comes first in the input files?

When you are clear about what you want the program to do, then comes the problem of choosing the correct types, declaring variables, etc.

Designing and implementing at the same time may work well when you're fully at home in a language, but I find I do it too often anyway myself - keeping semantics and implementation apart is worth it, and it also simplifies the process of documenting.

---

### Post by AlexenderReez on 2009-04-22
> **Pollox said:**
> 
vector< bool > name; creates a vector (an array of dynamic size) of type bool called name.
It's similar to
bool name[5], except now you don't specify the size to be 5.

Now, to add elements to your vector, read in the element from your file:
element = is.get()
 and then go:
name.push_back( element )

.

i still having problem...but it is really interesting because i feel like i'm learning new thing :D ...ok after a while

my code goes -->

```
#include <iostream>
#include <fstream>
using namespace std;

int main () {


  int i, max_read = 5, amountRead = 0; 
  vector < bool > array;
  vector < bool > array2; /second text file
  char c, str[256];
   char c2, str2[256];
  ifstream is;

  cout << "Enter the name data text file( usually data.txt): ";
  cin.get (str,256);

  is.open (str);        // open file

  while (is.good())     // loop while extraction from file is possible
  {
    c = is.get();       // get character from file
    if (is.good())
      cout << c; //just to check
  }

  array.push_back( c ); 
  
  
  //second text file
  
   cout << "Enter the name PN text file( usually PN.txt): ";
  cin.get (str2,256);

  is.open (str2);        // open file

  while (is.good())     // loop while extraction from file is possible
  {
    c2 = is.get();       // get character from file
    if (is.good())
      cout << c2; //just to check
  }

  array2.push_back( c2); 
  
  
  //lastly i need to multiply these two array..which example array * array2 where ([1][0][1]) x ([1][0][0]) = ([1] [0] [0]),please do help give me clue how to do this for vector array...do i need to use for loop?
  
  
  is.close();           // close file

  return 0;
}
```

it give error for vector array initialization...hope you can correct it.

ERROR
[HTML]witechmine.cpp: In function ‘int main()’:
witechmine.cpp:9: error: ‘vector’ was not declared in this scope
witechmine.cpp:9: error: expected primary-expression before ‘bool’
witechmine.cpp:9: error: expected `;' before ‘bool’
witechmine.cpp:10: error: expected primary-expression before ‘bool’
witechmine.cpp:10: error: expected `;' before ‘bool’
witechmine.cpp:10: error: expected primary-expression before ‘/’ token
witechmine.cpp:10: error: ‘second’ was not declared in this scope
witechmine.cpp:10: error: expected `;' before ‘text’
witechmine.cpp:16: error: ‘str’ was not declared in this scope
witechmine.cpp:22: error: ‘c’ was not declared in this scope
witechmine.cpp:27: error: ‘array’ was not declared in this scope
witechmine.cpp:27: error: ‘c’ was not declared in this scope
witechmine.cpp:44: error: ‘array2’ was not declared in this scope
[/HTML]


Actually i try to create program that read data.txt which **example** like

data.txt
```
100110101010101010101010
``` 

and multiply with

PN.txt
```
001110101010001010101111
```

for each digit (as binary multiplication)..which example array * array2 where ([1][0][1]) x ([1][0][0]) = ([1] [0] [0]),please do help give me clue how to do this for vector array...do i need to use for loop?please do help T_T

---

### Post by Jiraiya_sama on 2009-04-22
First of all you need to add #include <vector> to your program.

---

### Post by AlexenderReez on 2009-04-22
> **Jiraiya_sama said:**
> First of all you need to add #include <vector> to your program.

erk..my mistake..careless...ok then still cant multiply those two binary file...please help...see error comment in the code

> #include <iostream>
#include <fstream>
#include <vector>
using namespace std;

int main () {


  int i, max_read = 5, amountRead = 0; 
  vector < bool > array;
  vector < bool > array2; //second text file
  vector < bool > result;
  char c, str[256];
   char c2, str2[256];
  ifstream is;

  cout << "Enter the name data text file( usually data.txt): ";
  cin.get (str,256);

  is.open (str);        // open file

  while (is.good())     // loop while extraction from file is possible
  {
    c = is.get();       // get character from file
    if (is.good())
      cout << c; //just to check
  }

  array.push_back( c ); 
  
  
  //second text file
  
   cout << "Enter the name PN text file( usually PN.txt): ";
  cin.get (str2,256);

  is.open (str2);        // open file

  while (is.good())     // loop while extraction from file is possible
  {
    c2 = is.get();       // get character from file
    if (is.good())
      cout << c2; //just to check
  }

  array2.push_back( c2); 
  //******************ErrOR HERE
  // result = array * array2;
  // cout << result;
  
  //lastly i need to multiply these two array..which example array * array2 where ([1][0][1]) x ([1][0][0]) = ([1] [0] [0]),please do help give me clue how to do this for vector array...do i need to use for loop?
  
  
  is.close();           // close file

  return 0;
}

---

### Post by Jiraiya_sama on 2009-04-22
insert text here.```

#include <bitset>
#include <string>
#include <iostream>
#include <fstream>
using namespace std;

int main () {

  bitset<1024> file1;
  bitset<1024> file2; //second text file
  string filename;
  char c;

  ifstream is;

  cout << "Enter the name data text file( usually data.txt): ";
  cin >> filename;

  is.open (filename.c_str());        // open file

  for(int i = 0; i != 1024; ++i)
  {
    is >> c;       // get character from file
    if(c == '1')
       file1.set(i);
  }
  
  is.close();
  //second text file
  
  cout << "Enter the name PN text file( usually PN.txt): ";
  cin >> filename;

  is.open(filename.c_str());        // open file

  for(int i = 0; i != 1024; ++i)
  {
    is >> c;       // get character from file
    if(c == '1')
      file2.set(i);
  }

  file1 |= file2;
  
  is.close();           // close file

  cout << file1;

  return 0;
}

```

You might try this out. It has the disadvantage of being more rigid, you will need to determine how many bits you want to read from each file. But it is easier to deal with the subsequent math and print from. It will also probably have a smaller memory footprint than a series of bool.

---

### Post by tneva82 on 2009-04-22
> **AlexenderReez said:**
> erk..my mistake..careless...ok then still cant multiply those two binary file...please help...see error comment in the code

Well for one your push_backs need to be within while loops. Right now you push only last c you read. Rest are forgotten along the way.

---

### Post by eye208 on 2009-04-22
This should multiply n1.txt with n2.txt and write the result to n3.txt. Both input numbers can be any length. Characters other than 0 and 1 will be ignored. It's quick and dirty but seems to work. I didn't bother cutting off leading zeros though.
```
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

void read_number(std::string const &file, std::vector<bool> &num) {
        std::ifstream in(file.c_str());
        num.reserve(100);
        while (in.good()) {
                int v = in.get();
                if (v == (int)'0') num.push_back(false);
                else if (v == (int)'1') num.push_back(true);
        }
}

void write_number(std::string const &file, std::vector<bool> const &num) {
        std::ofstream out(file.c_str());
        for (std::vector<bool>::const_iterator it = num.begin(); it != num.end(); it++) out << (*it ? '1' : '0');
        out << std::endl;
}

void multiply(std::vector<bool> const &num1, std::vector<bool> const &num2, std::vector<bool> &num3) {
        size_t s1 = num1.size();
        size_t s2 = num2.size();
        num3.resize(s1 + s2);
        for (size_t i1 = s1 - 1; i1 < s1; i1--) {
                if (num1[i1]) {
                        size_t i3 = s2 + i1;
                        bool c = false;
                        for (size_t i2 = s2 - 1; i2 < s2; i2--) {
                                bool o1 = num2[i2];
                                bool o2 = num3[i3];
                                num3[i3--] = o1 ^ o2 ^ c;
                                c = o1 & o2;
                        }
                }
        }
}

int main() {
        std::vector<bool> n1, n2, n3;
        read_number("n1.txt", n1);
        read_number("n2.txt", n2);
        multiply(n1, n2, n3);
        write_number("n3.txt", n3);
        return 0;
}
```
Example:
[quote=n1.txt]1100[/quote]
[quote=n2.txt]1010[/quote]
[quote=n3.txt]01111000[/quote]
Have fun!

---

### Post by AlexenderReez on 2009-04-22
> **eye208 said:**
> This should multiply n1.txt with n2.txt and write the result to n3.txt. Both input numbers can be any length. Characters other than 0 and 1 will be ignored. It's quick and dirty but seems to work. I didn't bother cutting off leading zeros though.
```
#include <iostream>
#include <fstream>
#include <string>
#include <vector>

void read_number(std::string const &file, std::vector<bool> &num) {
        std::ifstream in(file.c_str());
        num.reserve(100);
        while (in.good()) {
                int v = in.get();
                if (v == (int)'0') num.push_back(false);
                else if (v == (int)'1') num.push_back(true);
        }
}

void write_number(std::string const &file, std::vector<bool> const &num) {
        std::ofstream out(file.c_str());
        for (std::vector<bool>::const_iterator it = num.begin(); it != num.end(); it++) out << (*it ? '1' : '0');
        out << std::endl;
}

void multiply(std::vector<bool> const &num1, std::vector<bool> const &num2, std::vector<bool> &num3) {
        size_t s1 = num1.size();
        size_t s2 = num2.size();
        num3.resize(s1 + s2);
        for (size_t i1 = s1 - 1; i1 < s1; i1--) {
                if (num1[i1]) {
                        size_t i3 = s2 + i1;
                        bool c = false;
                        for (size_t i2 = s2 - 1; i2 < s2; i2--) {
                                bool o1 = num2[i2];
                                bool o2 = num3[i3];
                                num3[i3--] = o1 ^ o2 ^ c;
                                c = o1 & o2;
                        }
                }
        }
}

int main() {
        std::vector<bool> n1, n2, n3;
        read_number("n1.txt", n1);
        read_number("n2.txt", n2);
        multiply(n1, n2, n3);
        write_number("n3.txt", n3);
        return 0;
}
```
Example:



Have fun!

lets say

a.txt = b.txt * c.txt * d.txt * e.txt;

where e.txt contain data alternating the values of 1 and -1

what should i modified ?

---

