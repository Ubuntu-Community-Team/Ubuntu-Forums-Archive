---
title: "[C++] Fun Excercise"
date: 2011-01-10
forum: Programming Talk
---

### Post by TheBuzzSaw on 2011-01-10
Here is your starting code.

[php]#include <iostream>
using namespace std;

class Blargh
{
    public:
        Blargh()
        {
            mIndex = index++;
            cout << spaces << mIndex << " is born!\n";
            *spaceUpdate++ = ' ';
        }

        ~Blargh()
        {
            *--spaceUpdate = '\0';
            cout << spaces << mIndex << " dies!\n";
        }

    private:
        static size_t index;
        static char spaces[128];
        static char* spaceUpdate;
        size_t mIndex;
};

size_t Blargh::index = 0;
char Blargh::spaces[128] = {};
char* Blargh::spaceUpdate = spaces;

int main(int argc, char** argv)
{
    // ???

    return 0;
}[/php]

Here is your target output.
```
0 is born!
 1 is born!
  2 is born!
   3 is born!
    4 is born!
     5 is born!
      6 is born!
       7 is born!
        8 is born!
        8 dies!
       7 dies!
      6 dies!
      9 is born!
       10 is born!
       10 dies!
      9 dies!
     5 dies!
    4 dies!
   3 dies!
  2 dies!
 1 dies!
```

Write the code for main. Good luck. :)

(NO. This is not a homework assignment.)

---

### Post by MadCow108 on 2011-01-10
my probably over complicated but concise way:
```

#include <list>
#include <iterator>
#include<boost/shared_ptr.hpp>
#include<boost/make_shared.hpp>
...
  std::list<boost::shared_ptr<Blargh> > b;
  generate_n(std::front_inserter(b), 9, boost::make_shared<Blargh>);
  b.pop_front();
  b.pop_front();
  b.pop_front();
  b.push_front(boost::make_shared<Blargh>());
  b.push_front(boost::make_shared<Blargh>());
  boost::shared_ptr<Blargh> * alive = new boost::shared_ptr<Blargh>(b.back());
  return 0; 

```
for minimal line count you could drop make_shared and iterator (included by shared_ptr.hpp) includes

---

### Post by worksofcraft on 2011-01-10
Lol yes ok... here how is this one... just for fun ;)
[php]

// g++ blargh.cpp
#include <iostream> 
using namespace std; 

class Blargh 
{ 
    public: 
        Blargh() 
        { 
            mIndex = index++; 
            cout << spaces << mIndex << " is born!\n"; 
            *spaceUpdate++ = ' '; 
        } 

        ~Blargh() 
        { 
            *--spaceUpdate = '\0'; 
            cout << spaces << mIndex << " dies!\n"; 
        } 

    private: 
        static size_t index; 
        static char spaces[128]; 
        static char* spaceUpdate; 
        size_t mIndex; 
}; 

size_t Blargh::index = 0; 
char Blargh::spaces[128] = {}; 
char* Blargh::spaceUpdate = spaces; 

template <int N> struct my_blargh: Blargh {
	my_blargh<N-1> mBn;
};
 
template <> struct my_blargh<0> {};

int main(int argc, char** argv) {
	my_blargh<6> sMb6;
	{
		my_blargh<3> sMb3;
	}
	{
		my_blargh<2> sMb2;
	}
    return 0; 
}  
[/php]

p.s. you should ought to null terminate your spaces string on the way up too, but I didn't want to change your class or you might disqualify my solution :shock:

---

### Post by TheBuzzSaw on 2011-01-10
HA! I need to compile and run these. After a few more solutions, I'll post mine.

> **worksofcraft said:**
> p.s. you should ought to null terminate your spaces string on the way up too, but I didn't want to change your class or you might disqualify my solution :shock:
What do you mean? It properly null terminates going both directions.

EDIT -- Plus, your solution fails. In your program, 0 dies, but if you look at the answer carefully, 0 never dies. ;) You are very very close, though. You only need one little tweak.

---

### Post by worksofcraft on 2011-01-10
> **TheBuzzSaw said:**
> HA! I need to compile and run these. After a few more solutions, I'll post mine.


What do you mean? It properly null terminates going both directions.

EDIT -- Plus, your solution fails. In your program, 0 dies, but if you look at the answer carefully, 0 never dies. ;) You are very very close, though. You only need one little tweak.

Lol... my bad... I never seem to read the question properly... I'll have another look but speaking of zero's

```

            *spaceUpdate++ = ' '; 

```

Are you sure that there will always be a '\0' to terminate that string of spaces you are making?

---

### Post by Queue29 on 2011-01-10
```
#include <iostream>
using std::cout;

int main(int argc, char** argv) 
{ 
    cout << 
"0 is born!" << "\n" <<
" 1 is born!" << "\n" <<
"  2 is born!" << "\n" <<
"   3 is born!" << "\n" <<
"    4 is born!" << "\n" <<
"     5 is born!" << "\n" <<
"      6 is born!" << "\n" <<
"       7 is born!" << "\n" <<
"        8 is born!" << "\n" <<
"        8 dies!" << "\n" <<
"       7 dies!" << "\n" <<
"      6 dies!" << "\n" <<
"      9 is born!" << "\n" <<
"       10 is born!" << "\n" <<
"       10 dies!" << "\n" <<
"      9 dies!" << "\n" <<
"     5 dies!" << "\n" <<
"    4 dies!" << "\n" <<
"   3 dies!" << "\n" <<
"  2 dies!" << "\n" <<
" 1 dies!" << "\n";

    return 0; 
}  

```

Well that was easy

---

### Post by TheBuzzSaw on 2011-01-10
> **worksofcraft said:**
> Lol... my bad... I never seem to read the question properly... I'll have another look but speaking of zero's

```

            *spaceUpdate++ = ' '; 

```

Are you sure that there will always be a '\0' to terminate that string of spaces you are making?
Yes. The array is defaulted to all zeroes at the start via the {}. Whenever one is added, a space is placed, and the pointer is moved. Whenever one is removed, the pointer is moved back first, and it is set to zero.

> **Queue29 said:**
> Well that was easy
HAHAHA! Success! I was waiting for someone to "solve" it that way. XD

---

### Post by worksofcraft on 2011-01-10
> **TheBuzzSaw said:**
> Yes. The array is defaulted to all zeroes at the start via the {}. Whenever one is added, a space is placed, and the pointer is moved. Whenever one is removed, the pointer is moved back first, and it is set to zero.


HAHAHA! Success! I was waiting for someone to "solve" it that way. XD

Lol - I must admit I thought about that too but I'm glad I didn't actually post it... was that your solution too?

p.s. oops soz forgot to post my update
```


int main(int argc, char** argv) {
	my_blargh<1> sMbImortal;
	{
		my_blargh<5> sMb6; 
		{ my_blargh<3> sMb3; } 
		{ my_blargh<2> sMb2; }
	}
	freopen("/dev/null","w", stdout); // happy now ? :P
//	abort(); // or you can try this one: run no more destructors
	return 0;  
}  

```

---

### Post by MadCow108 on 2011-01-10
> 
HAHAHA! Success! I was waiting for someone to "solve" it that way. XD

well if we don't need to use your class... ;)
```

#include <cstdlib>
int main(int argc, const char *argv[])
{
  system("curl \"http://ubuntuforums.org/showpost.php?p=10339916&postcount=1\" 2>/dev/null | grep -A 19 \" 1 is born\\!\" | sed -e \"s#</pre>##\"");
  return 0;
}

```

I like worksofcraft's template solution :)

---

### Post by TheBuzzSaw on 2011-01-10
[php]int main(int argc, char** argv)
{
    new Blargh; // memory leak wooooo
    Blargh a[5];
    { Blargh b[3]; }
    { Blargh c[2]; }
    return 0;
}[/php]

---

### Post by worksofcraft on 2011-01-10
> **TheBuzzSaw said:**
> [php]int main(int argc, char** argv)
{
    new Blargh; // memory leak wooooo
    Blargh a[5];
    { Blargh b[3]; }
    { Blargh c[2]; }
    return 0;
}[/php]

Lol nice one I didn't think of leaking memory... 
Quite some creative ideas comin in now... I tried madcow's solution:
```

cjs@cjs-ubuntu:~/Desktop/examples$ g++ madcowblargh.cpp
cjs@cjs-ubuntu:~/Desktop/examples$ ./a.out
cjs@cjs-ubuntu:~/Desktop/examples$ 

```
... no output :'(
However I DO understand what it supposed to do and I think that is really funny... you can even edit the solution you want some time in the future and it will still work :D

I don't suppose you got some more things like this?!
;)

---

### Post by TheBuzzSaw on 2011-01-10
> **worksofcraft said:**
> I don't suppose you got some more things like this?!
;)

I have a few. I'll have to dig into my archive of coding nonsense. Until then, I recommend you attempt the Codility free test: [http://codility.com/demo/take-sample-test/](http://codility.com/demo/take-sample-test/)

---

### Post by TheBuzzSaw on 2011-01-12
I tested Madcow108's code. Worked great! :P

---

