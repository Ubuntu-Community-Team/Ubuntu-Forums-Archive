---
title: "Building strings that grow on eachother"
date: 2008-08-02
forum: Programming Talk
---

### Post by Neon612 on 2008-08-02
I've got six arrays, each with the numbers 0-9 and a-z in them.

I'm trying to get each one to a string that counts up 000000,000001,000002...999999,99999a,99999b...zzzzzz.

How do I get to to work? All I've managed to do so far is get strings where all six chars are the same.

---

### Post by drubin on 2008-08-02
From your example I can see only the need for the 0 padding on the left of the number. What would you need the a-z for?

But a simple solution for the 0-9 is just have a forloop and check the length.

if(tostring(mynumber).length()<length of desired string ){
//add padding to the left of the string.
}

---

### Post by Neon612 on 2008-08-02
THis is my dads business, inventory to be exact. This will create a list of all the possible prefixes. 

something like:
000000-3457383 could be part a
33hg6f-3457383 could be part b
22ff98-3457383 could be part c

I need to just output all of these prefixes to a file. The output to file part I've already got figured out.

The only problem with hand writing everything out is that I'd be there for a while, 217,682,336 lines would take a long time to type be hand.

---

### Post by drubin on 2008-08-02
> **Neon612 said:**
> THis is my dads business, inventory to be exact. This will create a list of all the possible prefixes. 

something like:
000000-3457383 could be part a
33hg6f-3457383 could be part b
22ff98-3457383 could be part c

I need to just output all of these prefixes to a file. The output to file part I've already got figured out.

Are the numbers "random" or do they follow an order?

**EDIT** 217,682,336 where do you get that number from, Is it the total items in the store or possible combinations

---

### Post by Neon612 on 2008-08-02
> **rubinboy said:**
> Are the numbers "random" or do they follow an order?

**EDIT** 217,682,336 where do you get that number from, Is it the total items in the store or possible combinations


The numbers follow somewhat of an order 000000...999aaa...zzzzzz.

The number comes from the 36 possible digits (0-9 and a-z) for each of the 6 positions in the final number. So if I am correct I believe it is a total of 217,682,336 or 36^6.

---

### Post by drubin on 2008-08-02
This isn't that hard to do. What language are you coding this in. So I am able to point you to some functions.

In java there is a Character.digit (letter, 36) that converts a letter, 0-9 a-z to a numeric. fordigit is the opposite.
[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Character.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/Character.html)

forDigit(int digit, int radix) 
[PHP]
//Amount length of each number
for(int j=0;j<6;j++){
  String temp="";
  //go from 0-9 then a-z
  for(int i=0;i<36 ;i++){
     temp+=String.tostring(forDigit(i,36));
  }
  //append string to a file. 
}[/PHP]

---

### Post by catchmeifyoutry on 2008-08-02
> **Neon612 said:**
> THis is my dads business, inventory to be exact. This will create a list of all the possible prefixes. 

something like:
000000-3457383 could be part a
33hg6f-3457383 could be part b
22ff98-3457383 could be part c

I need to just output all of these prefixes to a file. The output to file part I've already got figured out.

The only problem with hand writing everything out is that I'd be there for a while, 217,682,336 lines would take a long time to type be hand.


(10 + 26) ^ 6 = 2,176,782,336 different combinations, so i think you've missed a digit if I understand correctly what you're trying to do. 
Do you realize that if you write this in plain ASCII, using one byte per character, 6 bytes per string, 7 bytes per line (to include \n return charater), you will create a file of approximately 14 gigabyte? I can't see any practical application for this. What exactly are you trying to achieve with such a file?

Anyway, here is some pseudo code that generates the n-th code string. Again, if I understand you correctly.

```

# for a number 0 =< n < 2176782336, construct unique code 
function make_code_string(n)
{
   # initialization
   array chars = ['0', ..., '9', 'a', ..., 'z']; # 36 different characters
   int c = chars.length(); # c = 36
   string s(6); # string of 6 characters

   # construct string in backward order, starting at last character
   for(i = 5; i >= 0; i--) 
   {
      s[i] = chars[n % c];   # here '%' is the modulo operator
      n = n / c;             # here '/' uses integer division
   }

   # all done
   return string;
}

# exaples
make_code_string(0); # returns '000000'
make_code_string(1); # returns '000001'
make_code_string(10); # returns '00000a'
make_code_string(2176782335); # returns 'zzzzzz'
# etc.

```

---

### Post by Neon612 on 2008-08-02
Sorry, forgot to mention the language. I'm using C++.

Heres the code I've got at the moment:
[PHP]#include <iostream>
#include <string>

using namespace std;

int main ()
{
	int i=48, j=97;
	string firstdigit[36];
	string seconddigit[36];
 	string thirddigit[36];
	string fourthdigit[36];
	string fifthdigit[36];
	string sixthdigit[36];
	string strtotal;
	
	//Assign letters/numbers to respective array address	
	while (i<58)
	{
		firstdigit[i-48] = i;
		seconddigit[i-48] = i;
		thirddigit[i-48] = i;
		fourthdigit[i-48] = i;
		fifthdigit[i-48] = i;
		sixthdigit[i-48] = i;
		i++;
	}
	
	while (j<123)
	{
		firstdigit[j-87] = j;
		seconddigit[j-87] = j;
		thirddigit[j-87] = j;
		fourthdigit[j-87] = j;
		fifthdigit[j-87] = j;
		sixthdigit[j-87] = j;
		j++;
	}
		
	for (int a=0, b=0, c=0, d=0, e=0, f=0; a<36, b<36, c<36, d<36, e<36, f<36; a++, b++, c++, d++, e++, f++)
	{
		strtotal = firstdigit[a];
		strtotal += seconddigit[b];
                strtotal += thirddigit[c];
		strtotal += fourthdigit[d];
		strtotal += fifthdigit[e];
		strtotal += sixthdigit[f];

                cout << strtotal << endl;
	}

	return 0;
}
	[/PHP]

---

### Post by drubin on 2008-08-02
> **Neon612 said:**
> Sorry, forgot to mention the language. I'm using C++.

 Take a look at catchmeifyoutry's post. See if you can implement it in c++ might be easier to understand then trying to find the forDigit function in c++.

Then just have ONE forloop from 0-2,176,782,336

> (10 + 26) ^ 6 = 2,176,782,336 different combinations, so i think you've missed a digit if I understand correctly what you're trying to do.
Do you realize that if you write this in plain ASCII, using one byte per character, 6 bytes per string, 7 bytes per line (to include \n return charater), you will create a file of approximately 14 gigabyte? I can't see any practical application for this. What exactly are you trying to achieve with such a file?

Never even thought of this. It is extremely funny huge how exponentially big things get with out you even noticing.

---

### Post by catchmeifyoutry on 2008-08-02
> **rubinboy said:**
> 
Never even thought of this. It is extremely funny huge how exponentially big things get with out you even noticing.

Lol, yeah, but the "curse of dimensionality" giving me headaches at study/work.

---

### Post by drubin on 2008-08-02
> **catchmeifyoutry said:**
> Lol, yeah, but the "curse of dimensionality" giving me headaches at study/work.

Double number of rice grains for each square of the chess board...

---

### Post by Neon612 on 2008-08-02
> **catchmeifyoutry said:**
> Anyway, here is some pseudo code that generates the n-th code string. Again, if I understand you correctly.

```

# for a number 0 =< n < 2176782336, construct unique code 
function make_code_string(n)
{
   # initialization
   array chars = ['0', ..., '9', 'a', ..., 'z']; # 36 different characters
   int c = chars.length(); # c = 36
   string s(6); # string of 6 characters

   # construct string in backward order, starting at last character
   for(i = 5; i >= 0; i--) 
   {
      s[i] = chars[n % c];   # here '%' is the modulo operator
      n = n / c;             # here '/' uses integer division
   }

   # all done
   return string;
}

# exaples
make_code_string(0); # returns '000000'
make_code_string(1); # returns '000001'
make_code_string(10); # returns '00000a'
make_code_string(2176782335); # returns 'zzzzzz'
# etc.

```

Thanks the only thing that I can't seem to get to work right is when I declare the array. Is it supposed to be declared as a char or a string?

---

### Post by drubin on 2008-08-02
> **Neon612 said:**
> Thanks the only thing that I can't seem to get to work right is when I declare the array. Is it supposed to be declared as a char or a string?

Before spending more time on this, I would rather try and explain why these ALL need to be in a text file?

As the file would be HUGE 14gigs and almost impossible to use for any thing worth while. (Please don't even think about printing this out on paper)

---

### Post by Neon612 on 2008-08-02
Right now I'm not worried about outputting the number sequence to anything other than the terminal to see if it works. And now that I know how large that file could get I may find another way of doing this. Like just outputing the sequences I need and nothing else.

On a side note: this is possibly more to see if I can do it than anything. I'm trying to teach myself some C++ programming, coming from a background in Visual Basic (large step, I know). Since for the inventory part of it I could code this up in an hour or two in VB, and the fact that this program will mainly be used on a Windows (cringe) machine.

---

### Post by catchmeifyoutry on 2008-08-02
> **Neon612 said:**
> Thanks the only thing that I can't seem to get to work right is when I declare the array. Is it supposed to be declared as a char or a string?

You can, for example use an array of characters, 
char chars[] = {'0', '1', ...etc };
which is basically what an old skool c string is, or you can use a C++ string from #include<string>:
std::string chars = "0123.... etc";
Whatever works for you such that chars[i] returns the i'th character.
But I think that if you have trouble with this you should maybe first google some tutorials on strings and characters to get yourself more familiar with the subject.
Otherwise, here is a std::string reference with the [] operator:
[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/)


> **Neon612 said:**
> Right now I'm not worried about outputting the number sequence to anything other than the terminal to see if it works. And now that I know how large that file could get I may find another way of doing this. Like just outputing the sequences I need and nothing else.

Yes, that sound more reasonable.

---

### Post by Neon612 on 2008-08-02
I've been using cplusplus.com since I started working on c++. Great stuff.

ANd another question: on the line where you declared the string s(6). Let me just make sure I'm getting this, its declaring a string named s that is 6 characters long?


Then when I compile it it says "warning: this decimal constant is unsigned only in ISO C90" I'm using g++ to complie it, I know that gcc uses the C90. Does g++ use it or what can I do to get this to compile the right way. And this is when I go cout << make_string(2176782335) << endl;  .

---

### Post by dwhitney67 on 2008-08-02
I agree with the others... are you really intent on generating this huge amount of data, whether to the screen or file?  There's got to be a better way, perhaps using unique numbers instead of relying on the letters.

Anyhow, here's a C++ program that will generate the data per your original request.  I did not put much design thought into it, other than to create a class that keeps track of a base-36 "number" ranging from 0 to 'z'.

If you run the program, I do not recommend saving the data to disk!
[PHP]#include <cstdio>


class Base36
{
  public:
    Base36()
      : m_start('0'),
        m_cur('0')
    {
    }

    void reset()
    {
      m_cur = m_start;
    }

    char cur()
    {
      return m_cur;
    }

    char next()
    {
      char rtn = m_cur++;

      if ( m_cur == ':' )
      {
        m_cur = 'a';
      }
      else if ( m_cur > 'z' )
      {
        m_cur = '0';
      }

      return rtn;
    }

  private:
    char m_start;
    char m_cur;
};


void displayString( const char *str, const size_t size )
{
  for ( size_t len = 0; len < size; ++len )
  {
    printf( "%c", str[len] );
  }
  printf( "\n" );
}

int main()
{
  Base36 p0;
  Base36 p1;
  Base36 p2;
  Base36 p3;
  Base36 p4;
  Base36 p5;

  char str[6];

  for ( size_t w = 0; w < 6; ++w )
  {
    for ( size_t c0 = 0; c0 < 36; ++c0, p0.next() )
    {
      str[0] = p0.cur();

      for ( size_t c1 = 0; c1 < 36; ++c1, p1.next() )
      {
        str[1] = p1.cur();

        for ( size_t c2 = 0; c2 < 36; ++c2, p2.next() )
        {
          str[2] = p2.cur();

          for ( size_t c3 = 0; c3 < 36; ++c3, p3.next() )
          {
            str[3] = p3.cur();

            for ( size_t c4 = 0; c4 < 36; ++c4, p4.next() )
            {
              str[4] = p4.cur();

              for ( size_t c5 = 0; c5 < 36; ++c5, p5.next() )
              {
                str[5] = p5.cur();

                displayString( str, sizeof(str) );
              }
            }
          }
        }
      }
    }
  }

  return 0;
}[/PHP]

---

### Post by drubin on 2008-08-02
> **dwhitney67 said:**
> 
If you run the program, I do not recommend saving the data to disk!
[PHP]//CODE removed to save electrons. [/PHP]


The idea of having 7!! nested forloops makes me want to cry a little inside:confused:

---

### Post by dwhitney67 on 2008-08-02
Yep, I know.  I really think the OP should devise a more worthy challenge for a Saturday night; perhaps a program that can be used to shed light on the meaning of life?

---

### Post by catchmeifyoutry on 2008-08-02
> **Neon612 said:**
> I've been using cplusplus.com since I started working on c++. Great stuff.

ANd another question: on the line where you declared the string s(6). Let me just make sure I'm getting this, its declaring a string named s that is 6 characters long?


Then when I compile it it says "warning: this decimal constant is unsigned only in ISO C90" I'm using g++ to complie it, I know that gcc uses the C90. Does g++ use it or what can I do to get this to compile the right way. And this is when I go cout << make_string(2176782335) << endl;  .

Yeah that string(6) thingy wasn't specifically meant for C++, it was pseudo code to make it clear that the memory was reserved before starting the loop.
Let's see, you could do it like this:

at the beginning create a character array of size 6 to hold the code:
[PHP]
std::string make_code(int n)
{ 
  char s[6];
  // rest of code
  // the loop i = 5 ... 0 etc ...
  //   in the loop character s[i] is set
  // next

  // all done, return C++ string
  return std::string(s, 6);
}
[/PHP]

So at the end you convert the character array (in fact, it is a c-style string of size 6, without null character delimiter) to a more safe C++ string using the std::string constructor.
From web reference on the constructor:
```

string ( const char * s, size_t n );
    Content is initialized to a copy of the string formed by the first n characters in the array of characters pointed by s.

```

Should work I think.

O btw, in the pseudo code I gave you should be able to replace the 6 by any integer m (and in the loop start at m-1). In fact, you could make m a second parameter, e.g. make_code(int n, int m = 6); to enumerate codes of any size.
That is the benefit of a single loop over using nested loops.


One more thing about your error message, I'm now thinking that maybe the compiler says that the number exceeds the maximum value allowed for int. The maximum value actually differs per platform and system.
Some tips on this: [http://www.daniweb.com/forums/thread18963.html](http://www.daniweb.com/forums/thread18963.html)

Good luck.

---

### Post by Neon612 on 2008-08-03
Thank you. That solved my problem. Well except for the error message.

I changed the makecode(int n) to an unsigned int but I still get the error. Though isn't the unsigned int supposed to be valid from 0 to 4 billion something?

---

### Post by catchmeifyoutry on 2008-08-03
> **Neon612 said:**
> Thank you. That solved my problem. Well except for the error message.

I changed the makecode(int n) to an unsigned int but I still get the error. Though isn't the unsigned int supposed to be valid from 0 to 4 billion something?

A quick google on your error message showed this forum thread:[http://bytes.com/forum/thread474270.html](http://bytes.com/forum/thread474270.html)
where it is explained that the compiler warns you that such big -hard coded- numbers may be treated differently depending on used C language standard.
But since it was just a test case (and the program works, I presume?) it is not required to hard code the number for actually using makecode.
If you do want to get past this warning, you can instead of defining it by hand let C++ sort it out:

[PHP]
// add this head to top of page 
#include <math.h>
// headers bla bla

std::string makecode(unsigned int n) {
// bla bla
}

// test code
// more bla
unsigned int num_codes = pow(36, 6);
std::cout << "total number of possible codes: " << num_codes << std::endl;
std::cout << "last code: " << makecode(num_codes - 1) << std::endl;
[/PHP]

Well, good luck with it. I you do hope you understand _why_ the code works, otherwise you should read on the integer % and / operators and work out what the algorithm does.
It's a good exercise, even when you're normally using other program languages. But especially for learning C++ these programs are great to familiarize yourself with common libraries and error messages.

Anywho, don't thank me, thank the thanks button :p ! (my first thanks, that would make my day :D ).

Have fun.

---

