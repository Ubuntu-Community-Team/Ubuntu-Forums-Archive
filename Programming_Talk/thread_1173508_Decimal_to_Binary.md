---
title: "Decimal to Binary"
date: 2009-05-29
forum: Programming Talk
---

### Post by smc18 on 2009-05-29
**This is NOT homework - just for personal satisfaction**

Language: C++

Hey guys and girls,

I begining to program my own subnetting calculator to brush up my subnetting skills and get back into some programming. 
The problem I'm having is my logic keeps returning the binary values backwards.

192 converted to binary is: 11000000

My programs logic is displaying: 00000011

I need to convert the IP address and the default mask to binary, so I can perform ANDing.

I will post up all my source code.  I have tried to document everything nicely, if you can any questions please ask.

(I'm using the Dev-C++ 4.9.9.2 compiler on a Windows machine.)

> #include <iostream>
#include <iomanip>
#include <cmath>

using namespace std;

const int maxsize = 4; //global constant to determine maximum size of array

int i, decvalue, binvalue, FIRoctat, SECoctat, THIoctat, FORoctat;
char period;

int main()
{    
    cout << "Please enter the Network Address you want to subnet: ";
    cin>> FIRoctat >> period >> SECoctat >> period >> THIoctat >> period >> FORoctat;
    cout<<"You entered: ";
    cout<< FIRoctat << period << SECoctat << period << THIoctat << period << FORoctat << endl;
    
    //Declare Ip Address array and assign values.    
    int ipaddress[maxsize] = {FIRoctat, SECoctat, THIoctat, FORoctat};
    
    //Cycle through the array; outputting each element value
    cout <<"\nListing the array elements\n";
         
    for (i = 0; i < maxsize; i++)
         cout << i << "  " << ipaddress[i] << endl;
    
    //Return the binary values of each octat
    cout <<"\nReturning the binary values of each octat\n";
    
    for (i = 0; i < maxsize; i++)
    {
     decvalue = ipaddress[i];
     while ( decvalue >= 1 )
     {
      binvalue = decvalue % 2;
      decvalue = decvalue / 2;
      cout << binvalue;
     }
     cout << ".";    
}  
    
    cout << endl << endl;       
    system("PAUSE");
    return 0;
}

---

### Post by MadCow108 on 2009-05-29
int i=INTEGERSIZE-1; (64bit32bit or for your case just 8bit)
while (i>=0)
{
  std::cout <<((dec>>i--)%2);
 // equivalent: dec/pow(2,--i)%2
}

or just use yours and swap the order:

std::deque<int> bin;
while (dec >= 1)
{
	bin.push_front(dec%2);
	dec = dec/2;
}
for (int i=0; i<bin.size(); i++) std::cout <<bin[i];
(deque for effective push_front)

or with vector and reverse iterator:
std::vector<int> bin;
std::vector<int>::reverse_iterator it;
while (dec >= 1)
{
	bin.push_back(dec%2);
	dec = dec/2;
}
for (it=bin.rbegin(); it<bin.rend(); ++it) std::cout << *it;
(or just counting index down :) )

---

### Post by unknownPoster on 2009-05-29
There is a very elegant recursive solution to this problem that you may want to consider. 

Think of how you would solve this by hand and then try to implement it in your code.

---

### Post by smc18 on 2009-05-29
I'd like to try this solution

> std::deque<int> bin;
while (dec >= 1)
{
bin.push_front(dec%2);
dec = dec/2;
}
for (int i=0; i<bin.size(); i++) std::cout <<bin[i];
(deque for effective push_front)


I'm trying to add it to my code and find the right preproccesor to add.
I've added #include <list> but still no luck.


I'm no expert so any more guidance would be nice. :)

---

### Post by smc18 on 2009-05-29
Actually the compiler is saying push_front has not been declared. I'll look around to find the syntax


EDIT: Looks like I have to learn about some vectors.

EDIT:

So I've added this 

> 
#include <list>
#include <vector>
#include <deque>


(I ommited some code here)

deque <int> binvalue;

while (decvalue >= 1)
    {
     binvalue.push_front(decvalue%2);
     decvalue = decvalue/2;
    }
    for (i=0; i<binvalue.size(); i++) 
    cout << binvalue[i];

It compiles and runs;however the program isn't outputing any elements from binvalue[] :(

---

### Post by unknownPoster on 2009-05-29
> **smc18 said:**
> Actually the compiler is saying push_front has not been declared. I'll look around to find the syntax


EDIT: Looks like I have to learn about some vectors.

make sure that you have

[PHP]#include <vector>[/PHP]

---

### Post by smc18 on 2009-05-29
haha one sec, I think I forgot to add something else back in. Let me give this a try.

Here is my hew Code
> decvalue = ipaddress[i];
    while (decvalue >= 1)
    {
     binvalue.push_front(decvalue%2);
     decvalue = decvalue/2;
    }
    for (j=0; j < 4; j++)
    {
    for (i=0; i<8; i++) 
        cout << binvalue[i];
    cout << ".";
    }       

Here is my output:

> 
Please enter the Network Address you want to subnet: 192.168.1.1
You entered: 192.168.1.1

Listing the array elements
0  192
1  168
2  1
3  1

Returning the binary values of each octat
11111000.11111000.11111000.11111000.



For some reason each octat is the same.

---

### Post by smc18 on 2009-05-29
Oh by the way, thanks for sticking around and helping.  I really appreciate it.

---

### Post by dwhitney67 on 2009-05-29
I can only imagine that this exercise is for a homework problem.  There are various ways to resolve this problem, and here is the "slow" way.
```

#include <iostream>
#include <string>
#include <cstdlib>

std::string toBinary(const unsigned char value);
const char* nibbleToBinary(const unsigned char value);

int main()
{
  std::string ip = "192.168.1.1";

  size_t pos = 0;
  for (unsigned int i = 0; i < 4; ++i)
  {
    size_t stop = ip.find_first_of('.', pos);
    std::string quad = ip.substr(pos, stop - pos);
    pos = stop + 1;

    unsigned char value = atoi(quad.c_str());
    std::cout << toBinary(value) << (i < 3 ? "." : "");
  }
  std::cout << std::endl;
}

std::string toBinary(const unsigned char value)
{
  return std::string(nibbleToBinary((value >> 4) & 0xF)) + nibbleToBinary(value & 0xF);
}

const char* nibbleToBinary(const unsigned char value)
{
  switch (value)
  {
    case  0: return "0000";
    case  1: return "0001";
    case  2: return "0010";
    case  3: return "0011";
    case  4: return "0100";
    case  5: return "0101";
    case  6: return "0110";
    case  7: return "0111";
    case  8: return "1000";
    case  9: return "1001";
    case 10: return "1010";
    case 11: return "1011";
    case 12: return "1100";
    case 13: return "1101";
    case 14: return "1110";
    case 15: return "1111";
  }

  return "0000";
}

```

---

### Post by smc18 on 2009-05-30
> I can only imagine that this exercise is for a homework problem. There are various ways to resolve this problem, and here is the "slow" way.


Nope, I'm doing this for my myself.  I took a few CS classes but never really had a use for it at my age then.

I figured, I could use the practice now, and try to make something useful.

By the way I changed a few things, and it is working to a certain extent now.

```

#include <stdio.h>
#include <stdlib.h>
#include <iostream>
#include <iomanip>
#include <cmath>

using namespace std;

const int maxsize = 4; //global constant to determine maximum size of array

int i, j, decvalue, binvalue, FIRoctet, SECoctet, THIoctet, FORoctet;
char buffer[50];
char period;
//const char ASCIICONVERT = 0x0F;


int main()
{    
    cout << "Please enter the Network Address you want to subnet: ";
    cin>> FIRoctet >> period >> SECoctet >> period >> THIoctet >> period >> FORoctet;
    cout<<"You entered: ";
    cout<< FIRoctet << period << SECoctet << period << THIoctet << period << FORoctet << endl;
    
    //Declare Ip Address array and assign values.
    
    int ipaddress[maxsize] = {FIRoctet, SECoctet, THIoctet, FORoctet};
    
    //Cycle through the array; outputting each element value
         
    for (i = 0; i < maxsize; i++)
         cout <<i<< "  " << ipaddress[i] << endl;
    
    cout <<"\nThis is the IP address in the binary\n";
        
    i=0;    
    for (i = 0; i < maxsize; i++)
    {
      decvalue = ipaddress[i];
      itoa(decvalue, buffer, 2);        //use itoa function: using 2 for binary
      cout << fixed << setprecision(8) << setw(8) << buffer;
      if(i < 3)
      cout <<".";
     }
    
    cout << endl << endl;
     
    system("PAUSE");
    return 0;
}
```

Output:

> 
Please enter the Network Address you want to subnet: 192.168.1.1
You Entered: 192.168.1.1
0  192
1  168
2  1
3  1

This is the IP address in binary:
11000000.10101000.       1.       1

However the binary shows up with 7 spaces in the 3rd and 4th octet.

Next, I need to find a way for it show up as x.x.00000001.00000001

---

### Post by NielsBhor on 2009-05-30
You can use the STL <iomanip> and use the setw(number) function call to set the number of spaces you want for the cout. Where number is the number of space you need.

---

### Post by smc18 on 2009-05-30
Thank for the suggestion. :)

I have tried right here, but I still get x.x_______1._______1  (There are no underscores, however this forum removes numerious spaces; so I had to add them as a placeholder)

I think for what I'm going to need is x.x.00000001.00000001

```
i=0;    
    for (i = 0; i < maxsize; i++)
    {
      decvalue = ipaddress[i];
      itoa(decvalue, buffer, 2);        //use itoa function: using 2 for binary
      cout << fixed << setprecision(8) << setw(8) << buffer;
      if(i < 3)
      cout <<".";
     }

```

I've tried to and it just makes blank spaces on the output.  Sadly, I think Im going to need zero's.

Im going to be ANDing the binary IP address and with the binary Subnet mask.

I'm not sure if ANDing a 1 or 0 with a blank space will work.

---

### Post by gtcoffee on 2009-05-30
cout << setw( 8 ) << setfill('0') << 1 << end;

00000001

---

### Post by NielsBhor on 2009-05-30
Excellent!

---

### Post by smc18 on 2009-05-30
:D Thanks alot! It worked great.

---

### Post by smc18 on 2009-05-30
Just like to post an update of my progress.

When I decided to use the itoa function.  It was making my binary addresses in a char data type.  I needed an int data type.
I tried to do Type Casting but I wasn't having an luck. :(

So I decided to write the binary addresses into a file.  Then read from the exact same file and save them in a new int array.

So far it's coming along fine. My next step is to add the logic of ANDing to the program.

I'll try to make more progress updates.

---

### Post by MadCow108 on 2009-05-30
converting into char then write to file and read again is kind of inefficient.
why not use one of the many solutions given here to convert directly into an vector/array/deque of ones and zeros?
this structure offers alot of flexibility for whatever (printing) use.

just to quote one of my suggestions (every other works just as fine)
```

int i=INTEGERSIZE-1; //(INTEGERSIZE=8 in cour case)
vector<int> binary(INTEGERSIZE);
while (i>=0) binary.push_back((decimalnumber>>i--)%2);

```
(number>>i just integer divides the number by the power of 2^i [bitshifting operator])
Of course this needs adapting to store your 4 different binary numbers (hint: multidimensional vector,deque or array would be one possiblity)

---

### Post by smc18 on 2009-05-31
Ok now I have another challenge; converting binary array elements into decimals.

Basically, this is what I need to work with.

```
FIRoctet=11111111;
SECoctet=11111111;
THIoctet=11111111;
FORoctet=10000000;

int newsubnetmask[4] = {FIRoctet, SECoctet, THIoctet, FORoctet};
```

I need to convert newsubnetmask[0] through newsubnetmask[3] into a decimal value, and I would like to keep my array in the program.

In the beginning of my program; I've used the itoa function to convert a decimal number into binary.  I'm wondering if there is a nice function to do binary to decimal.

---

### Post by NielsBhor on 2009-05-31
I don't know if this helps but I have this function.
```

<li class="li1">int bin2dec(char *bin)   
<li class="li1">{
<li class="li2">  int  b, k, m, n;
<li class="li1">  int  len, sum = 0;
<li class="li1"> 
<li class="li1">  len = strlen(bin) - 1;
<li class="li1">  for(k = 0; k <= len; k++) 
<li class="li2">  {
<li class="li1">    n = (bin[k] - '0'); // char to numeric value
<li class="li1">    if ((n > 1) || (n < 0)) 
<li class="li1">    {
<li class="li1">      puts("\n\n ERROR! BINARY has only 1 and 0!\n");
<li class="li2">      return (0);
<li class="li1">    }
<li class="li1">    for(b = 1, m = len; m > k; m--) 
<li class="li1">    {
<li class="li1">      // 1 2 4 8 16 32 64 ... place-values, reversed here
<li class="li2">      b *= 2;
<li class="li1">    }
<li class="li1">    // sum it up
<li class="li1">    sum = sum + n * b;
<li class="li1">    //printf("%d*%d + ",n,b);  // uncomment to show the way this works
<li class="li2">  }
<li class="li1">  return(sum);
<li class="li1">}
<li class="li1">
```
Ignore the stuff between the angle brackets.

---

### Post by smc18 on 2009-05-31
I saw that snippet online too.  I tried to change a few things around to make it work with what I have. No luck.

I will have to continue trying.


Edit:

I compiled it by itself, and it works.  I have to study it, and understand what's going on in the code.

---

### Post by MadCow108 on 2009-06-01
does the same, in less code (maybe even faster,depends on compiler optimization):
```

int bin[8] ={1,1,0,1,0,0,1,1};
int dec=0;
for (int i=7; i>=0; i--)
  dec += bin[7-i]*1<<i;
std::cout << dec << std::endl;

```
1<<i is just exp(2,i)

---

