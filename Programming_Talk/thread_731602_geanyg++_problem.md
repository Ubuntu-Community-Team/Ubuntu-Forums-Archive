---
title: "geany/g++ problem"
date: 2008-03-22
forum: Programming Talk
---

### Post by DAC1138 on 2008-03-22
I can't get this app compiled in Geany. It's just a simple app, and I can't figure out why Geany won't let it compile. 

#include <iostream>



using namespace std;



int main()

{

    int value; 

    

    1024 = value;

    

    cout << "This program prints the value: " << value;


    

    return 0;

}


The g++ error it reports is:
int.cpp:11: error: invalid lvalue in assignment

What gives? I have had this compile in  Eclipse and kdevelop and in DevC++ in linux. This is just a sample test app I compile to get used to the IDE s I've been testing.

---

### Post by LaRoza on 2008-03-22
Look at the code again, there is no way that that compiled.
[php]
#include <iostream>

using namespace std;

int main()
{

    int value;
/* The following line should be a dead give away... */ 
   1024 = value;
    cout << "This program prints the value: " << value;
    return 0;
}
[/php]

---

### Post by TreeFinger on 2008-03-22
The first step is to head to the line number the compiler is telling you is causing the error.

---

### Post by Sinkingships7 on 2008-03-22
HINT: in c++, you pass the value from the right of the statement to the variable on the left of the statement.

---

### Post by hyperair on 2008-03-22
Like Sinkingships7 said.
1024 isn't an lvalue (value that can be put on the left). You can't assign "value" onto "1024". But you can do it the other way (which your probably want to).

---

### Post by DAC1138 on 2008-03-22
Hmm. I got it. Thanks for the help. I was under the impression that you can pass values that way to integers.

The file that I compiled with other compilers was the same thing, the only difference being this was a modified version (duh!) that I was messing around with in Geany when I first installed it a few weeks ago. So this was all just a misunderstanding on my part, but thanks for clarifying.

---

### Post by Nemooo on 2008-03-22
I made a similar mistake the other day. Took me a while to figure out the mistake :)

---

### Post by DAC1138 on 2008-03-22
So while this thread is open, can someone explain why C++ won't allow an expression like "100 = value" to work? I've been reading up on lvalues (thanks for that reference, none of my C++ books talked about lvalues yet and I'm halfway through) But I still can't grasp why the C++ compiler won't automatically see the lvalue and switch it around.

I know it's so much easier just to avoid asking and just learn to do it the right way, but I always learn best when I understand why things have to be done a certain way.

---

### Post by WW on 2008-03-22
> **DAC1138 said:**
> So while this thread is open, can someone explain why C++ won't allow an expression like "100 = value" to work? [...] But I still can't grasp why the C++ compiler won't automatically see the lvalue and switch it around.

If the destination of the assignment wasn't always on the left, how would the compiler know what do to with a statement like this:
> 
   x = y;

(where x and y are both variables)?

---

### Post by slavik on 2008-03-22
> **WW said:**
> If the destination of the assignment wasn't always on the left, how would the compiler know what do to with a statement like this:

(where x and y are both variables)?
that and it is also the same way we do it in mathematics.

---

### Post by hyperair on 2008-03-22
I always accepted it as the way programming is done. Are there any languages that don't use the concept of lvalues and automatically switch them over? I don't think there are any.

---

### Post by LaRoza on 2008-03-23
> **DAC1138 said:**
> So while this thread is open, can someone explain why C++ won't allow an expression like "100 = value" to work? I've been reading up on lvalues (thanks for that reference, none of my C++ books talked about lvalues yet and I'm halfway through) But I still can't grasp why the C++ compiler won't automatically see the lvalue and switch it around.

I know it's so much easier just to avoid asking and just learn to do it the right way, but I always learn best when I understand why things have to be done a certain way.

Because the assignment operator means something, and isn't just a pretty symbot for the compiler to use however it wants. 

I think are mistaking the purpose of a compiler. It isn't there to be be silenced or to assume anything.

See:
```

int x = 100;
int y = 2;
const int z = 20;

y = x;
x = z
z = y

```

---

### Post by supergenius1994 on 2010-02-21
> **DAC1138 said:**
> I can't get this app compiled in Geany. It's just a simple app, and I can't figure out why Geany won't let it compile. 

#include <iostream>



using namespace std;



int main()

{

    int value; 

    

    1024 = value;

    

    cout << "This program prints the value: " << value;


    

    return 0;

}


The g++ error it reports is:
int.cpp:11: error: invalid lvalue in assignment

What gives? I have had this compile in  Eclipse and kdevelop and in DevC++ in linux. This is just a sample test app I compile to get used to the IDE s I've been testing.
you said:
"1024=value;"
1024 is a number, it cannot be set to a value, anything on the left of the equal sign is changed

---

