---
title: "Item class: Joining all variables together"
date: 2008-02-23
forum: Programming Talk
---

### Post by amingv on 2008-02-23
Hi,

Trying to befriend my spare time (very abundant lately) I have created a little
library; which contains the Item class (yay for originality). Inspiration came
from the neat way Python manages variables, without having to declare a specific type.
I am aware that this is not the way Python does things, but hey, I'm not Guido van Rossum...

I'd really appreciate if you download it, try it and tell me any way in which I
can improve it (or my programming in general); please DO nitpick, tell me everything
from somewhere you consider should have comments to different/more efficient ways of
doing things, as well as good programming manners. Just have in mind I have just a few months
programming, and I may not understand very advanced concepts.

FAQS:
    Q: Does this mean I can start using spam, sausages, ham and eggs 
       as metasyntactic variables in C++?
    A: Er... yeah, whatever.
    Q: Should I use this in <insert super secret project from the government here>?
    A: I do not recommend it, and I doubt that's GPL friendly anyway.
    Q: Is this going to replace the way we do things in C++?
    A: No, it's for educational purposes only.
    Q: Should I use this, istead of what my C++ guide says? Looks so much easier...
    A: HELL NO!!! You should learn C++ the way it is!
    Q: It's this memory-wise?
    A: By far not. Everything is a string (amongst other ineptitudes), see source for details.
    Q: Can you post the source so I don't have to download it?
    A: No, because I want you to try it and tell me what you think (pretty please).
    Q: Do you like spam?
    A: No. I try to avoid mistery meat.

Here's the file: [ATTACH]60502[/ATTACH]

---

### Post by Jessehk on 2008-02-23
While it's definitely good to be experimenting and writing software, I'd focus more on programs at this point rather than libraries. :)

You had a **using namespace std** in your header file, which isn't good.
Also, this sort of functionality would much better be accomplished with templates. To expand, you've only accounted for a few types.
A truly generic implementation could handle any type and instead of providing things such as **operator+**, etc, would provide a mechanism for getting the "raw" type from the class.

Plus, this exact this already exists in the Boost libraries: [http://www.boost.org/doc/html/any.html](http://www.boost.org/doc/html/any.html) ;)

```

#include <iostream>
#include <string>
#include <cassert>

#include <boost/any.hpp>

using boost::any_cast;

int main() {
    boost::any x;

    x = 3;
    assert( any_cast<int>( x ) == 3 );

    x = std::string( "abc" );
    assert( any_cast<std::string>( x ) == "abc" );
}

```

I'm not saying this to be harsh or discourage you. Just to point out that library writing (especially in C++ due to its many intricacies) is difficult. It's always a good idea to keep learning and practicing.

EDIT: If you wanted to write a similar class as Boost.Any using templates (which I'd first learn, as I'm guessing you're not familiar with them yet), something like Boost.TypeTraits ( [http://www.boost.org/doc/html/boost_typetraits.html](http://www.boost.org/doc/html/boost_typetraits.html) ) *might* be useful.

EDIT2: If you ignore everything I just said regarding the fundamental "correctness" of this library, there are still several changes you could make.
Instead of
```

int type;

```

I'd use an enumeration:
```

enum Type {
    INTEGER,
    FLOATING_POINT,
    STRING,
    // etc
};

```

To make things clearer.

Second, in all the functions, you're passing by value. While this isn't a problem with built-in types such as **int** and **float**, when you pass in a std::string, it will be copied (which takes time and memory). instead, it in by const-reference which is functionally equivelent but more efficient. For example:
```

void foobar( const std::string &str ) {
    std::cout << str << std::endl;
}

```.

Other than that, there are not many things I would change. However, like I said, the premise for this library is flawed. :)

---

### Post by amingv on 2008-02-23
Thank you for your reply,

I do admit writing libraries is not my main purpose, but I'll also admit it was fun and I learned a few things (which was all the point, it's usefulness is null). But I get your point.

I have seen many projects that do not specify the namespace at the top; but use the namespace::element notation. I always assumed this was because they had more than one namespace, and did this to avoid confusion, but I guess my assumption was wrong... can you explain why it is not appropriate?

I didn't know about Boost, thanks.

Although making the functions/operators get their values by reference is in my to-do list, I will admit that I wasn't very bothered by memory efficiency. At this point I just wanted to see a working something, but I can see the importance of what you state.

I will make some time to learn about templates, interestingly enough none of the guides I've read so far even mentions them (except for cpluplus.com, but I haven't got there). Thanks for mentioning them.

---

### Post by Wybiral on 2008-02-23
> **amingv said:**
> I have seen many projects that do not specify the namespace at the top; but use the namespace::element notation. I always assumed this was because they had more than one namespace, and did this to avoid confusion, but I guess my assumption was wrong... can you explain why it is not appropriate?

It's just good practice to avoid name collisions (and not pollute the global namespace).

I will also add that using a string to store your data is going to be really inefficient. Think about integers that are hundreds of digits long, you're storing each one as a byte! That blows a normally 4 or 8 byte integer into a hundred byte string representation.

A more efficient method might be to use a union, like this:

```

union {
    int i;
    double d;
    char *s;
    char c;
} typeUnion;

typeUnion data;


```

Then:

```

data.i = *integer*
...
data.d = *double*
...
so forth...

```

This way, sizeof(data) will never be larger than the largest type in the union (they share bytes) in this case, a double (normally 8 bytes). The downside is that std::string wont work in a union, so you have to use char* strings (you can always cast that in and out).

---

### Post by amingv on 2008-02-23
My... that union thing is brilliant. (And it's the ultimate proof that 100+ lines of novice code can't beat 3 lines of expert code). Thank you for mentioning it.
 I did have to modify the example a bit to get it to compile (looks like you have to specify a statement next to union, which will be used to declare the next, or use typeUnion.i, etc as an only union, am I correct?).

I did find something I can't comprehend, if I do:

```
item.i = 1;
item.d = 3.0;
item.s = "A Elbereth Gilthoniel!";

cout<< item.i <<"\n";
cout<< item.d <<"\n";
cout<< item.s <<"\n";
```

I'll get the output (notice the integer):

```
134514688
3
A Elbereth Gilthoniel!

```

Yet if I modify the previous example:

```
item.i = 1;
item.d = 3.0;
//item.s = "A Elbereth Gilthoniel!";

cout<< item.i <<"\n";
cout<< item.d <<"\n";
//cout<< item.s <<"\n";
```

I'll get

```
0
3

```

Only by being by itself does i yield a correct value. Does this mean only one data type should be used by each declared union?
Now, how is int directly (or indirectly)  affected by char or double?

---

### Post by Wybiral on 2008-02-23
> **amingv said:**
> Only by being by itself does i yield a correct value. Does this mean only one data type should be used by each declared union?
Now, how is int directly (or indirectly)  affected by char or double?

OK, be very careful with unions. The data inside them ALL shares the same bytes. So if you have, for instance: an int (4 bytes), a pointer (4 bytes), and a float (4 bytes) instead of having 12 bytes (like you would if you declared them all separately), you have only 4 bytes because they SHARE the bytes. So yes, if you change the integer, you corrupt the float and the pointer. You use them one at a time. The main advantage is that they only use the number of bytes that are in the largest data type being stored. In your case, the double is the largest data type (at 8 bytes) so the union wont exceed 8 bytes (on a 32-bit machine).

---

### Post by amingv on 2008-02-23
I see, thanks for mentioning that method nevertheless. It is easier to implement, and even with my method I could only use one value per variable, so I guess it's no big deal.

---

### Post by Wybiral on 2008-02-23
> **amingv said:**
> I see, thanks for mentioning that method nevertheless. It is easier to implement, and even with my method I could only use one value per variable, so I guess it's no big deal.

That's what I was expecting. If you use it for each variable, you can essentially keep the size down to 8 bytes per value (plus the type flag) and access each value using something like:

```

void set(int value) {
    flag = INT;
    data.i = value
}

int getInt() {
    return data.i;
}

... so forth

```

---

