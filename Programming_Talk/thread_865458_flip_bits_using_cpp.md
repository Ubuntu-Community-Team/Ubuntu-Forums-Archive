---
title: "flip bits using cpp?"
date: 2008-07-20
forum: Programming Talk
---

### Post by Achetar on 2008-07-20
hello, i need to flip the bits in a string (or I can do it to a char or int from a converted string). I know the ~ operator is supposed to do that. Do I need to convert the string to a bitset before I can use the ~ operator? If not how would I do it?

---

### Post by Mr.Macdonald on 2008-07-20
is this flipping the bits
011010001
to
100101110

---

### Post by Achetar on 2008-07-20
Yes, that is what I mean

flipping the individual bits of the string

---

### Post by dwhitney67 on 2008-07-20
Do you mean a string containing unsigned characters or signed characters?  Or is it a string of ones and zeroes that you have?

For the latter, the code that follows is pretty much straightforward:
[PHP]#include <string>
#include <bitset>
#include <iostream>

int main()
{
  // create bitset from a string
  std::bitset<8> bs( std::string( "01101001" ) );

  // display original bitset
  for (size_t i = 0; i < bs.size(); ++i)
  {
    std::cout << bs[i];
  }
  std::cout << std::endl;

  // complement the bits in the bitset
  bs.flip();

  // display complemented bitset
  for (size_t i = 0; i < bs.size(); ++i)
  {
    std::cout << bs[i];
  }
  std::cout << std::endl;

  return 0;
}[/PHP]

---

### Post by slavik on 2008-07-21
> **dwhitney67 said:**
> Do you mean a string containing unsigned characters or signed characters?  Or is it a string of ones and zeroes that you have?

For the latter, the code that follows is pretty much straightforward:
[PHP]#include <string>
#include <bitset>
#include <iostream>

int main()
{
  // create bitset from a string
  std::bitset<8> bs( std::string( "01101001" ) );

  // display original bitset
  for (size_t i = 0; i < bs.size(); ++i)
  {
    std::cout << bs[i];
  }
  std::cout << std::endl;

  // complement the bits in the bitset
  bs.flip();

  // display complemented bitset
  for (size_t i = 0; i < bs.size(); ++i)
  {
    std::cout << bs[i];
  }
  std::cout << std::endl;

  return 0;
}[/PHP]
an std::vector<bool> creates a vector of bits :)

---

### Post by dribeas on 2008-07-21
> **slavik said:**
> an std::vector<bool> creates a vector of bits :)

Beware of [std::vector<bool>]("http://www.gotw.ca/gotw/050.htm").

```

void flip1( char& ch )
{
   ch = ~ch;
}

void flip2( char& ch )
{
   if ( ch == '1' ) 
   {
      ch = '0';
   }
   else if ( ch == '0' )
   {
      ch = '1';
   }
}

{
   std::string text( "01010010101101" );
   std::for_each( text.begin(), text.end(), flipX );  // either flip1 or flip2
}

```

Where flip1 switches the bits stored (ASCII code) and flip2 changes 0s into 1s and viceversa. I don't know what flavor you want. Note that the result of flipping ASCII bits will almost surely become unprintable.

David

P.S. Depending on your C++ implementation std::string can be defined using a different char type, requiring small modifications to the predicate flip. That can be solved by the compiler through the use of templates, but will make the example harder for beginners.

---

### Post by dwhitney67 on 2008-07-21
dribeas -

Although this is off-topic, I have question that I hope you can clear up.

When I was testing with a bitset, I had trouble using the for_each() algorithm to print out the string representation of bitset.  If I were to perform an intermediate step to obtain a reference to the bitset string, then I could get for_each to work; otherwise no joy.  Can you explain why?  Is it possible that to_string() is returning a difference string reference each time, and if so, would that really matter?

This code does not work (seg fault generated):
[PHP]std::bitset<8> bs( std::string("01101001") );
std::for_each( bs.to_string().begin(), bs.to_string().end(), printChar );[/PHP]

This works:
[PHP]std::bitset<8> bs( std::string("01101001") );
const std::string &str = bs.to_string();
std::for_each( str.begin(), str.end(), printChar );[/PHP]

This is printChar:
[PHP]void printChar( const char &ch )
{
  std::cout << ch;
}[/PHP]

P.S.  I realize this is a silly example; there is really no need to print individual characters, but I think the same concept (i.e. the error) might apply if I were flipping bits too.

---

### Post by Achetar on 2008-07-21
I want to flip the individual bits of a string (or char/int) from 0->1 or visa-versa. It is fine if they become unprintable, this is for a simple hash method I am writing (hash as in password hash). So there is a ~ operator on char/int? I tried mystring = ~mystring; but the compiler said operator~ undefined.

Thanks, I'll try the recommended methods out.

P.S. The string I have consists of letters, not 1/0s, so flip2 isn't what I need, but thanks anyway

---

### Post by dwhitney67 on 2008-07-21
> **Achetar said:**
> I want to flip the individual bits of a string (or char/int) from 0->1 or visa-versa. It is fine if they become unprintable, this is for a simple hash method I am writing (hash as in password hash). So there is a ~ operator on char/int? I tried mystring = ~mystring; but the compiler said operator~ undefined.

Thanks, I'll try the recommended methods out.

P.S. The string I have consists of letters, not 1/0s, so flip2 isn't what I need, but thanks anyway
The ~ is available to char and int (including their unsigned counterparts).  It is not available for string... unless you define it.

Something like this may meet your needs (note, I have not fully tested this code):
[PHP]
#include <string>
#include <algorithm>
#include <iostream>

class FlippableString : public std::string
{
  public:
    FlippableString( const char *str ) : std::string(str) {}
    FlippableString( const std::string &str ) : std::string(str) {}

    FlippableString & operator~()
    {
      std::for_each( this->begin(), this->end(), FlippableString::flipChar );
      return *this;
    }

  private:
    static void flipChar( char &ch )
    {
      ch = ~ch;
    }
};

int main()
{
  FlippableString str( "The dogs are free to roam the range." );
  FlippableString flip = str;

  ~flip;

  std::cout << "str  = " << str  << std::endl;
  std::cout << "flip = " << flip << std::endl;

  return 0;
}
[/PHP]

---

### Post by Achetar on 2008-07-21
OK, using mychar = ~mychar; works great. Thank you so much!

---

### Post by dribeas on 2008-07-21
> **dwhitney67 said:**
> This code does not work (seg fault generated):
[PHP]std::bitset<8> bs( std::string("01101001") );
std::for_each( bs.to_string().begin(), bs.to_string().end(), printChar );[/PHP][/QOUTE]

Surely, each call to to_string() creates a different string. You should never compare iterators into different containers. Usual result is a segmentation fault as you already found.

[QUOTE=dwhitney67;5429411]This works:
[PHP]std::bitset<8> bs( std::string("01101001") );
const std::string &str = bs.to_string();
std::for_each( str.begin(), str.end(), printChar );[/PHP]


This is also wrong, even if it works here. You should never create a reference to a temporary. There are no warranties whatsoever on the destruction of the temporary.

Correct:
```

std::bitset<8> bs( std::string("01101001") );
const std::string str = bs.to_string();
...

```

Uhm... I forgot to point you to [docs]("http://www.sgi.com/tech/stl/bitset.html"). As you see in the signature it does not return a reference but an object.

---

### Post by badrunner on 2008-07-21
> **Achetar said:**
> this is for a simple hash method I am writing (hash as in password hash)

Dont do this, ever. There are pleny of hash methods available that actually are well studied and found to be cryptographically sound (for now at least). Writing your own is both a waste of effort, and what you come up with will likely be worse than useless. Smart people put a phenomonal amount of work into finding (and breaking) good hashing algorithms.

---

### Post by dwhitney67 on 2008-07-21
> **badrunner said:**
> Dont do this, ever. There are pleny of hash methods available that actually are well studied and found to be cryptographically sound (for now at least). Writing your own is both a waste of effort, and what you come up with will likely be worse than useless. Smart people put a phenomonal amount of work into finding (and breaking) good hashing algorithms.
Ouch!  If everyone were to adopt this attitude, then nothing new would ever be developed.  How do you determine who is smart and who isn't?

---

### Post by Achetar on 2008-07-21
OK, using mychar = ~mychar; works great. Thank you so much!

---

### Post by Achetar on 2008-07-21
This is just an experiment for my own personal use. It is not intended for any production/commercial/public use. Although I would like to see if anyone can crack it without the source code.

---

### Post by badrunner on 2008-07-21
> **dwhitney67 said:**
> Ouch!  If everyone were to adopt this attitude, then nothing new would ever be developed.  How do you determine who is smart and who isn't?

Well anyone using bit flipping for a password hash clearly doesn't understand the large body of work thats been done in this area, so i can say with lots of certainty that they wont create a good hashing solution.

Cryptography is hard, very very few programmers (some of which are very very good programmers) get it right. By default, its just easier to assume a given person doesnt understand it, and its incredibly rare to be incorrect about that. Even very smart people get it wrong (look at the mess that is wireless security, the problems with older ssl versions etc. etc.). 

Oh, and i very much include myself in the people who will screw it up category.

---

