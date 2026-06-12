---
title: "standard libraries not standard enough"
date: 2010-09-07
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-07
Support for "wide strings" and "wide characters" was added to C++ to support a wider range of international character codes. Alas, apparently this does **not** equate to Unicode and the character width can could be 32, 16, or even 8 bits.

Now in processing utf-8 I want to have a size that is sufficient to store any Unicode value. I don't really want to care about how many bits... I mean I think 21 would suffice but a lot of processor architectures use multiples of 8 bits and 24 isn't a common word size either!

Thus std::wstring class is no use. The sizes of basic integer types like longs and ints and shorts aren't dependable either :shock:

Glib implements a ustring class, with a gunichar type, but Glib isn't available for all platforms so the more dependence on Glib the more portability issues I may get at a later date :(

From a more general perspective, i.e. besides for accommodating Unicode, is there a generic way to tell a C/C++ compiler to choose a basic data type that is big enough for my known data range?

---

### Post by NovaAesa on 2010-09-07
> **worksofcraft said:**
> From a more general perspective, i.e. besides for accommodating Unicode, is there a generic way to tell a C/C++ compiler to choose a basic data type that is big enough for my known data range?

You could try the cstdint library. Without using that, the only guaranteed data type with you can really count on is char.

---

### Post by worksofcraft on 2010-09-07
> **NovaAesa said:**
> You could try the cstdint library. Without using that, the only guaranteed data type with you can really count on is char.

Thanks for that info. I Googled it. In deed it does seem to be more or less what I want. However I also looked in the code and was horrified by the endless stream of conditional compilations ad typedefs... IMO it shows a serious problem with fundamental design philosophy of C and C++ :shock:

Ignoring that I've heard of 12 bit processors, there is no real reason to assume that we should have to even involve the concept of a bit: All I actually want is to define enum types with a give range e.g.

enum my_data_range { LOWEST = 1234, SYMBOLIC_VALUES_IN_BETWEEN, HIGHEST = 5678 };

... and then it would be trivial for the compiler to sort out the rest! OMG, why can't this industry just try to keep things simple. I remember why I quit computers now #-o

---

### Post by dwhitney67 on 2010-09-07
> **worksofcraft said:**
> ...

Thus std::wstring class is no use. The sizes of basic integer types like longs and ints and shorts aren't dependable either :shock:

...

Did you invent your own OS?  The size of longs, ints, and shorts is well defined.  It's been a while since I have used Windoze, so the following may be incorrect for that OS, but the aforementioned data types have sizes of 4 bytes, 4 bytes, and 2 bytes, respectively.

As for the std::wstring, that is merely a container for wchar_t values.  A wchar_t has a size of 4 bytes.  Coincidently, so does the std::wstring.  Note that the std::wstring contains an object pointing to a location on the heap where the actual string is stored; thus the length of the string has no bearing on the size of the wstring object.  If you want the length of the string contained within the wstring, use the size() method.

For you to issue statements that something is of no use raises questions as to whether you are utilizing the tools correctly.  Please prove me wrong.

---

### Post by NovaAesa on 2010-09-07
> **dwhitney67 said:**
> Did you invent your own OS?  The size of longs, ints, and shorts is well defined [for Windows].

While long, int, and short are well defined platform-wise, they aren't defined well across different platforms (between either OS or actual computer architecture).

A good way to check the size of these types on any particular platform is the using sizeof(int) for example to find the number of bytes an int is using.

---

### Post by dwhitney67 on 2010-09-07
> **NovaAesa said:**
> While long, int, and short are well defined platform-wise, they aren't defined well across different platforms (between either OS or actual computer architecture).

A good way to check the size of these types on any particular platform is the using sizeof(int) for example to find the number of bytes an int is using.

I agree that the sizeof() is the easy way to deduce the size of a data type; however using it inappropriately can lead to errors (eg. sizeof(std::wstring)).

As for the information I provided earlier, it holds for Linux (32-bit and 64-bit) and the Mac (64-bit).

---

### Post by Simian Man on 2010-09-07
Weren't you the guy who was recently arguing that C++ should be considered a "high-level language"?

L.
O.
L.

---

### Post by SledgeHammer_999 on 2010-09-07
> **dwhitney67 said:**
> As for the information I provided earlier, it holds for Linux (32-bit and 64-bit) and the Mac (64-bit).

No it doesn't. Long is 4 bytes in 32bit but 8 bytes in 64bit (at least on Linux).

---

### Post by dwhitney67 on 2010-09-07
> **SledgeHammer_999 said:**
> No it doesn't. Long is 4 bytes in 32bit but 8 bytes in 64bit (at least on Linux).

Your right; next time I will need to do proper testing before committing to an answer.

I also found that the std::wstring is 8 bytes long on a 64-bit architecture; no doubt because of the underlying pointer that is used to reference the allocated memory for the wide-char string.

P.S.  I just realized why drew a poor conclusion earlier; my employer-issued Mac, albeit a 64-bit machine, is running the 32-bit OS-X 5.8.

---

### Post by worksofcraft on 2010-09-08
According to web sites such as 
[http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring.html#_details](http://library.gnome.org/devel/glibmm/2.23/classGlib_1_1ustring.html#_details)

I read things like: "Note that std::wstring ... contains only fixed-width characters (where width could be 32, 16, or even 8 bits)."

You see apparently wchars mapping to unicode is only one possibility. Under those circumstance I feel the implementors of wstring have been wasting their time... and ours too. It's just untrustworthy garbage that is bloating our standard libraries and I wouldn't touch it with barge pole.

Just a mention of the contention that having all these options would make C++ a low level language: Well I could simply use "long" everywhere and pretend that the others don't exist :shock: Wouldn't it be just as "good" as all the "real" high level languages in that respect then?

All I'm saying is that the C/C++ standard could do a lot better than they have by letting us programmers specify the range of data that we intend to work with rather than a subjective preference based on what we might considered to be "short" or "long" for a number. It's really annoying they can't get their act together [-(

Oh well under the circumstances decide dwhitney67 makes most practical solution so I simply use
```

typedef unsigned unicode; // max can be 0x10FFFF: needs 21 bits

```

What it doesn't do is give me a generic solution for any other ranges I might need :(

---

### Post by dwhitney67 on 2010-09-08
> **worksofcraft said:**
> 
What it doesn't do is give me a generic solution for any other ranges I might need :(

See if this information will help you:
[http://en.wikipedia.org/wiki/C%2B%2B0x#New_string_literals](http://en.wikipedia.org/wiki/C%2B%2B0x#New_string_literals)

To experiment with C++0x, before it is officially released, use the -std compiler option.  For example:
```

g++ -Wall -std=c++0x MyProgram.cpp

```

---

### Post by worksofcraft on 2010-09-08
> **dwhitney67 said:**
> See if this information will help you:
[http://en.wikipedia.org/wiki/C%2B%2B0x#New_string_literals](http://en.wikipedia.org/wiki/C%2B%2B0x#New_string_literals)

To experiment with C++0x, before it is officially released, use the -std compiler option.  For example:
```

g++ -Wall -std=c++0x MyProgram.cpp

```

Hey that's really interesting stuff :)

There definitely some good ideas in there, yet while I haven't had a chance to assimilate it all yet, there is plenty that gives me cause for concern. I think the compiler explains it best:

```

#include <stdio.h>
#include <iostream>
using namespace std;

enum unicode { MINVAL = 0, MAXVAL = 0x10FFFF };

int main() {
	// a literal value
	unicode U = '€';

	// I don't want to swamp the compiler with a complete list of all defined
	// code points, but I DO want to be able to define the ones I need
#define EURO 0x20AC
	unicode U2 = EURO;

	// and I also DO want to be able to do computations with my values
	U2 = (U2 << 6) + (getc(stdin) & 0x3F); // read next 6 bits of utf 8

	// now don't both of these look like reasonable way to output?
	printf("Euro symbol is %c\n", U2);
	cout << "Euro symbol is " << U << " or maybe " << U2 << "... :P" << endl;

/*
 g++ -Wall -std=c++0x enum.c
enum.c:10:14: warning: multi-character character constant
enum.c: In function ‘int main()’:
enum.c:10: error: invalid conversion from ‘int’ to ‘unicode’
enum.c:15: error: invalid conversion from ‘int’ to ‘unicode’
enum.c:18: error: invalid conversion from ‘int’ to ‘unicode’

Why don't they ever put PRACTICAL people on these committes?

*/
const signed FAIL = -1;
	return FAIL;
}

```

---

### Post by TheBuzzSaw on 2010-09-08
Don't forget that string is nothing more than a basic_string<char>, and wstring is a basic_string<wchar>. If you can settle on a particular datatype that you want to work with, you could use that template to your own advantage and still enjoy all the functionality of string classes (short of working with string literals).

---

### Post by worksofcraft on 2010-09-08
Hum... yes
so I was typing why I wanted to use wide chars in the first place and well the moment I inserted some non ascii in this edit box *BoOOom* Google Chrome crashed... I hope people in foreign countries who use those character sets by default don't have the same problem.

So I'll explain it with only ASCII -

One way to generate the digits for numeric output might be:

char C = Number % 10 + '0';

But that doesn't work for hexadecimal and completely fails for other cultures that use different non ASCII digits. A generic solution would be:

unicode C = Digits[Number % Base];

and the Digits array could be a translatable string:

Digits = L"0123456789ABCDEF";

Evidently the middle east and in India and even China I think they can then translate that string into their own digit codes... and with a few locale dependent tweaks... hey - presto! you got global number formatting :biggrin:

---

### Post by worseisworser on 2010-09-08
Not having looked closely at this or even tested it, but GCC-4.5.x is needed for Unicode string literals: [http://gcc.gnu.org/projects/cxx0x.html](http://gcc.gnu.org/projects/cxx0x.html) (search for "string literals" on the page).

Other languages and environments has had support for this stuff for a long time already though. SBCL does Unicode 5.2 and uses UTF-8 (best way IMHO) for instance:

```

AMX> (let ((u1 #\&#8364;)     ;; #\ is used for character literals in Common Lisp; this is the same as '&#8364;' seen in your code.
           (u2 #x20AC))
       (format t "Euro symbol is ~C~%" (code-char u2))
       (cout "Euro symbol is " u1 " or maybe " (code-char u2) " ... :P"
             " ... or just inline in strings; like this: &#8364;"))
Euro symbol is &#8364;
Euro symbol is &#8364; or maybe &#8364; ... :P ... or just inline in strings; like this: &#8364;
AMX> 

```

..of course manipulation and computation of characters is possible:


```

AMX> (let ((u #x20AC))
       (format t "~C~%" (code-char u))
       (incf u)
       (format t "~C~%" (code-char u))
       (decf u)
       (format t "~C~%" (code-char u))
       (format t "Character code for &#8364; is ~A, or ~X (in hex).~%" 
               (char-code #\&#8364;)
               (char-code #\&#8364;)))
&#8364;
&#8365;
&#8364;
Character code for &#8364; is 8364, or 20AC (in hex).
AMX>

```


..and in languages/environments with seamless transition to bignums, the problems with regards to data-type size is gone.

---

### Post by dribeas on 2010-09-08
> **dwhitney67 said:**
> It's been a while since I have used Windoze, so the following may be incorrect for that OS, but the aforementioned data types have sizes of 4 bytes, 4 bytes, and 2 bytes, respectively.

That is not even right in linux, I can guess that you are running a 32bit OS by the looks of your data sizes. If you move to a 64 architecture with a 64 bit distro, the size of long will bump up to 8 bytes (64 bits) even if the size of int remain at 32 bits.

There are standard (in C, and in C++0x) data types of fixed sizes that have the size in the name, like int32_t, uint16_t...

```

dribeas@golden:tmp$ cat > test.cpp << eof
> #include <iostream>
> int main() {
>    std::cout << sizeof(long) << std::endl;
> }
> eof
dribeas@golden:tmp$ g++ -o test test.cpp && ./test
8
dribeas@golden:tmp$ g++ --version | head -1
g++ (Ubuntu 4.4.3-4ubuntu5) 4.4.3
dribeas@golden:tmp$ uname -a
Linux drodriguez-desktop 2.6.32-25-generic #43-Ubuntu SMP Wed Sep 1 09:46:13 UTC 2010 x86_64 GNU/Linux

```

The same goes in my mac with:
```

dribeas@golden:tmp$ g++ --version | head -1
i686-apple-darwin10-g++-4.2.1 (GCC) 4.2.1 (Apple Inc. build 5664)

```

---

### Post by worksofcraft on 2010-09-08
> **dribeas said:**
> 
There are standard (in C, and in C++0x) data types of fixed sizes that have the size in the name, like int32_t, uint16_t...


Yes I was just reading that after following that other link about the C++0x and TBH I think they got it **completely wrong**!

The size in bytes or what ever storage unit the machine works with needs to be transparent to the programmer. The programmer should be able to define their data set and bit twiddling fanataics would then be at liberty to define their bytes and nibbles if they really have to:

enum char { MINCHAR = -128, MAXCHAR = 127 };

or let's make the identifiers optional...

enum short { -(1 << 15), (1 << 15) - 1 };
enum unsigned_32 { 0, 0xFFFFFFFF }

and so on... you get the picture?

ONE SIMPLE SYNTAX CAN DEFINE THEM ALL
There is no need to put anything else in the language... hum...
:idea: I'm getting more and more in favor of developing --C by taking out all the utter nonsense committees have been putting in :shock:

---

### Post by worksofcraft on 2010-09-08
> **worseisworser said:**
> 
Other languages and environments has had support for this stuff for a long time already though. SBCL does Unicode 5.2 and uses UTF-8 (best way IMHO)...


Yes I'm in total agreement with you there. I do however also think there can be a place for "wide characters". For instance my digit character selection for other locales: Indexing in UTF-8 is possible but not a natural operation. A wide character array index is the appropriate construct.

> **worseisworser said:**
> 
..and in languages/environments with seamless transition to bignums, the problems with regards to data-type size is gone.

That is true, and bignums have their place I'm sure, but are not always desirable.

Imagine for instance some kind of algorithm, like my bit shifting and oring-in of then next UTF-8 byte... and perhaps then I might be masking out just the part I want, but behind the scenes a phenomenal "bignums" shift register is born... and all transparently until it's **so** big I get an out of memory crash :shock:

---

### Post by worseisworser on 2010-09-08
> **worksofcraft said:**
> That is true, and bignums have their place I'm sure, but are not always desirable.

Imagine for instance some kind of algorithm, like my bit shifting and oring-in of then next UTF-8 byte... and perhaps then I might be masking out just the part I want, but behind the scenes a phenomenal "bignums" shift register is born... and all transparently until it's **so** big I get an out of memory crash :shock:

I'm referring to what you said about "automatic selection of type" (quoted freely); this can be seen in relation to that.

..but of course one will declare that some value is to stay an *int* and not switch to a *bignum* representation under any circumstance if that is needed.

---

### Post by dwhitney67 on 2010-09-08
> **worksofcraft said:**
> 

enum char { MINCHAR = -128, MAXCHAR = 127 };

or let's make the identifiers optional...

enum short { -(1 << 15), (1 << 15) - 1 };
enum unsigned_32 { 0, 0xFFFFFFFF }


This is silly.  I think you should check out a beginner's book on C/C++.

P.S.  I wanted to use more colorful metaphors, but it isn't worth it.

---

### Post by worksofcraft on 2010-09-08
> **dwhitney67 said:**
> This is silly.  I think you should check out a beginner's book on C/C++.

P.S.  I wanted to use more colorful metaphors, but it isn't worth it.

It's silly to pre-define chars and shorts and longs and int32's and all that garbage. Programmers should be able to define the range that their integer data resides in and let the compiler choose appropriate size.

Some people are so entrenched in their ways they can't think outside the square and can't recognize a good idea when they see one.

I also suggest you refrain from trolling.

---

### Post by dwhitney67 on 2010-09-08
> **worksofcraft said:**
> It's silly to pre-define chars and shorts and longs and int32's and all that crap.

Some people are so entrenched in their ways they can't think outside the square and can't recognize a good idea when they see one.

I also suggest you refrain from trolling.

I haven't a clue what you are seeking.

enums are used to define discrete constants!  Not variable values.

But I will comply... see ya... where's that un-subscribe button?

---

### Post by schauerlich on 2010-09-08
> **worksofcraft said:**
> It's silly to pre-define chars and shorts and longs and int32's and all that garbage. Programmers should be able to define the range that their integer data resides in and let the compiler choose appropriate size.

You should check out the haskell type system.

> Some people are so entrenched in their ways they can't think outside the square and can't recognize a good idea when they see one.

Hint: 99% of the time, if you think something's a good idea and nobody else does, it's probably because someone else already tried it and found out it's not really that cool. Not saying this isn't the other 1%, but.

> I also suggest you refrain from trolling.

[img]http://grab.by/grabs/9ef5d27a5d411d8805d78f8036dc2613.png[/img]
Problem?

---

### Post by nvteighen on 2010-09-09
> **worksofcraft said:**
> 
The size in bytes or what ever storage unit the machine works with needs to be transparent to the programmer. The programmer should be able to define their data set and bit twiddling fanataics would then be at liberty to define their bytes and nibbles if they really have to:


No. No. No. (No, I am not Amy Winehouse)

You want a language that doesn't predefine data types so that you can do whatever you like? Assembly. Well, not even Assembly, because register sizes are already predefined, so it should be actually building your own CPU and then creating your own Assembly for it.

Why? Because C isn't the lowest-level language there is. Ok, it's low-level, but it is far much higher-level than ASM and there's no language in between them I know of. It gives you predefined data types that the language creators (correctly) thought to be useful for programmers so they avoid creating their own data type systems... The C Standard was also very wise to define some data types not in absolute terms but relative to int, as that gave the language great
adaptability to new platforms.

But C gives you ways to use bits: use a char and masks. It is 100% portable as char is explicitly defined as 1 byte by the standard, and it works. What if the implementation doesn't follow the standard? Blame the implementation and don't care about that, because your code is what you're working on (I sense the same mindset that led you to avoid environment variables because of mistrust...). So, use a char.

You want a 17 bytes long data type? Use a struct aggregating data types (17 char?) and create a sane API to use it so that the details are hidden. You don't even need to make that struct unaligned to make the data type 17 bytes long in memory: as long as it holds 17 bytes of data, it may serve your purpose even though it is bigger in memory because of padding.

If C doesn't give you the access you want, try Assembly, but I'm sure there are better ways to do what you want... Maybe even trying a higher-level language that makes you free from bit-nitpicking and gives you concept-based data types that might help you far much more than what you imagine.

---

### Post by worksofcraft on 2010-09-09
> **nvteighen said:**
> 
You want a 17 bytes long data type? Use a struct aggregating data types (17 char?) and create a sane API to use it so that the details are hidden. You don't even need to make that struct unaligned to make the data type 17 bytes long in memory: as long as it holds 17 bytes of data, it may serve your purpose even though it is bigger in memory because of padding.


That's not what I'm suggesting at all.

I'm suggesting that I can say what my minimum and maximum values are and then the compiler should choose an appropriate sized entity.

So like if my range fits in 17 bits then the compiler can put it in 32 bits, but not in 16. 

If I really do want say a 16 bit unit then I can create a range that fits that exactly and the compiler should be smart enough to make the most of that and allocate a 16 bit unit to it. It's a rather simple concept IMO... and a whole lot more flexible and intelligible than what they got now.

Also the standard doesn't say that chars are always 8 bits. It says that a char is smallest addressable unit of the machine. So like if you have a 12 bit processor with memory that is 12 bits wide you would get 12 bit chars. As the standard currently stands we have no way to know if longs are going to be 32 bits or 64 bits.

The compiler happily truncates shorts to chars, sign extends them back to integers of indeterminate size shifts bits off the end... will it overflow at 16, 32 or 64 bits... who knows?!

However I try to define a type suitable for unicode. Beyond dispute conceptually an enumerated type, yet one where I clearly have justifiable grounds for wanting to do arithmetic (as explained). Suddenly the standard gets all fussy about being type safe :shock: Not correct at all IMO.

---

### Post by schauerlich on 2010-09-09
If you're doing something that is so little abstracted as to care how many bits something takes up, then just make your own struct with chars as nvteighen has said. Simple, really. If you want a dynamically resizing int type, do it like a lot of HLL do... use a word-sized (C-style) int until it's about to overflow, then switch to a bignum.

---

### Post by SledgeHammer_999 on 2010-09-09
> **worksofcraft said:**
> 
Also the standard doesn't say that chars are always 8 bits. It says that a char is smallest addressable unit of the machine.

If I am not mistaken the smallest DIRECTLY addressable memory unit in C is a byte. As you know the only way to "access" bits is by bitwise operations. Thus a char is 1 byte in size.

---

### Post by Simian Man on 2010-09-09
This is still coming from your inability to accept that C and C++ are low-level languages.  C was created as a portable assembly language.  That's what it remains to this day.  As such it should use the same sizes as the native machine would use which is why the sizes of data types are not fixed.  If you think your problems are bad, back when C was developed there were machines with six, seven or nine bits to a byte!

If you want to do this, there are ways that have been outlined for you, but don't expect anybody else to care about this, because the point of C (and C++ by extension) isn't to provide a nice environment to the programmer.  It's to be one step up from assembly while somewhat portable.

---

### Post by worksofcraft on 2010-09-09
> **Simian Man said:**
> This is still coming from your inability to accept that C and C++ are low-level languages...

What I suggest is still only one step from assembler and in fact closer to the machine than the current standard because the existing concepts of chars, shorts, ints, longs etc can all be expressed using it.

When devising an algorithm, as a competent programmer I would have a clear idea of the data set and domain it is to work within. OTOH having a "long" that I can't tell if it will overflow at 32, or at 64 bits is not any use to me what-so-ever: In exactly the same way as having wide chars that may or may not accommodate unicode: A standard like that is a complete waste of space.

So I show a very simple idea that will let you do EVERYTHING you can do now and let you do a whole lot more. I get responses that to me sound more like religeous mantras :P I'll just assume I can't have explained it properly.

---

### Post by SledgeHammer_999 on 2010-09-09
> **worksofcraft said:**
> OTOH having a "long" that I can't tell if it will overflow at 32, or at 64 bits is not any use to me what-so-ever:

Then why not use **int32_t/uint32_t** or **int64_t/uint32_t** and be done with it? You know beforehand the size of this types.

---

### Post by worseisworser on 2010-09-09
> **worksofcraft said:**
> What I suggest is still only one step from assembler and in fact closer to the machine than the current standard because the existing concepts of chars, shorts, ints, longs etc can all be expressed using it.

In fact, no, what you suggest is actually further away from what the actual machine at hand (low-level) prefers.

The *int*s and *char*s have their sizes because of reasons related to the machine at hand in a portable fashion; it is important for memory allocation strategies, bus bandwidth and performance in general.


> **worksofcraft said:**
> When devising an algorithm, as a competent programmer I would have a clear idea of the data set and domain it is to work within. OTOH having a "long" that I can't tell if it will overflow at 32, or at 64 bits is not any use to me what-so-ever: In exactly the same way as having wide chars that may or may not accommodate unicode: A standard like that is a complete waste of space.


No, people have already told you what to do or use instead here, and the plain *char*s and *int*s are still useful as-is because of the reasons I mentioned above.


> **worksofcraft said:**
> So I show a very simple idea that will let you do EVERYTHING you can do now and let you do a whole lot more. I get responses that to me sound more like religeous mantras :P I'll just assume I can't have explained it properly.

Perhaps you should direct your assumptions in some other direction, or just drop them altogether.

If you need bit-manipulation C can do it, but if you need to do it extensively and in a high-level "nice" way HLLs are better at it. (yes really)

---

### Post by worksofcraft on 2010-09-09
> **worseisworser said:**
> In fact, no, what you suggest is actually further away from what the actual machine (low-level) prefers.

The *int*s and *char*s have their sizes because of reasons related to the machine at hand in a portable fashion; it is important for memory allocation strategies, bus bandwidth and performance in general.


I'm fully aware of that and I programmed hard real-time embedded systems in C++ for many years.

If I want a type to match exactly to a particular machine word I could simply define it's "enum" range in terms of MAX_CHAR or or MAX_SHORT or some such machine dependent symbol.

The fact that I can express ANY of the existing machine dependent quantities with what I propose, while you CANNOT express mine with the primitive types we currently have is proof irrefutable proof that I am right and you are wrong: Mine is more fundamental and gives superior control over storage allocation.

> **worseisworser said:**
> 
No, people have already told you what to do or use instead here, and the plain *char*s and *int*s are still useful as-is because of the reasons I mentioned above.


And I have already told you that the "plain chars and ints" could be defined to be exactly as they are on the basis of what I have proposed.

People have told me nothing useful: They suggest I use data types that may or may not support unicode depending on the implementation. Which is rubbish.

I can hardly lend credence to those who think it would be desirable to have the language indefinitely expanding our integral types with bignums behind the scenes. Practically every conceivable case where that would happen would be an indication of poor algorithm design and a lack of understanding of the problem they are trying to solve.

> **worseisworser said:**
> 
Perhaps you should direct your assumptions in some other direction, or just drop them altogether.


... and perhaps some of you should stop treating other people like idiots and be open to ideas that don't conform to your preconceptions?

---

### Post by worseisworser on 2010-09-09
I don't see anyone in the right or wrong because we aren't even agreeing about what the discussion is or what the actual issues and their relation (or lack thereof) are in the first place.

You seem to be quoting things, but I often see very little relation to what others and I say, or even you've said yourself previously -- which is why I'm not answering or quoting several of your "points" right now.

In any case, perhaps you know about [bit-fields]("http://publications.gbdirect.co.uk/c_book/chapter6/bitfields.html"), but I certainly do not care about you and your "problems". Actually, you should just go away; you're an inventor or "discoverer" of fake, misguided or misunderstood "problems" and you're a proponent of drama; probably executed in this fashion (and poorly I might add) to put yourself in a more interesting light.

---

### Post by Simian Man on 2010-09-09
> **worksofcraft said:**
> 
If I want a type to match exactly to a particular machine word I could simply define it's "enum" range in terms of MAX_CHAR or or MAX_SHORT or some such machine dependent symbol.

The fact that I can express ANY of the existing machine dependent quantities with what I propose, while you CANNOT express mine with the primitive types we currently have is proof irrefutable proof that I am right and you are wrong: Mine is more fundamental and gives superior control over storage allocation.

And I have already told you that the "plain chars and ints" could be defined to be exactly as they are on the basis of what I have proposed.
You totally missed the point.  The reason for having the types of variable size is so that programmers don't have to define the sizes of all of their types on *every* machine they target.  They use the type that matches their intent and they will be mapped to the appropriate types on the machine.

If you want to do bit twiddling just use the sized types (eg int32_t) or bit fields.  If you just want to use numbers without worrying about when they overflow, use something like Python.

---

### Post by worksofcraft on 2010-09-10
> **Simian Man said:**
> You totally missed the point.  The reason for having the types of variable size is so that programmers don't have to define the sizes of all of their types on *every* machine they target.  They use the type that matches their intent and they will be mapped to the appropriate types on the machine.

If you want to do bit twiddling just use the sized types (eg int32_t) or bit fields.  If you just want to use numbers without worrying about when they overflow, use something like Python.

D'oh [-X#-o I think you might not have been reading very attentively.

I was responding to the ones who say they need these types to do efficient bit twiddling.

I'm the one who wants a data type that has ADEQUATE size to store unicode characters: Apparently the standard is so utterly useless that it can't offer me one that will be dependable cuz it's "implementation and platform dependent".

The new C++0x standard is going to offer us char_16 and char_32... (let's just hope we never have to deal with a 24 bit machine) :shock: Anyway I was trying to show that there is a much more universal and flexible way to give integer types of guaranteed adequate size and still cater for bit twiddlers... whatever... evidently it's currently not available atm and not worth discussing on this forum atm either.

---

