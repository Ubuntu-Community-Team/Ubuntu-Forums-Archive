---
title: "A C++ question just off the top of my head"
date: 2008-12-10
forum: Programming Talk
---

### Post by Habbit on 2008-12-10
This has been bugging me for some time: the stream classes in the C++ standard library can be used in expressions like "if(stream)" or "while(!stream)". I thought support for such operations would be implemented through a "operator bool" member function, i.e. a cast operator to bool. However, it is really managed by an "operator!" (not surprising) and a "operator void*" (wtf?).

Theoretically, what happens in an expression like "if(cin >> myvar)" is that the istream& returned by operator>> is turned into a void* by "istream:: operator void*", which then gets evaluated by the if statement. However, why isn't this managed by a "istream:: operator bool"? Why are _two_ implicit casts (from istream to void* to bool) performed?.

Maybe my asking this question shows my marginal level of knowledge of C++, but I hope some guru (or geek :KS) here would shed some light into the mystery. Thanks everyone!

---

### Post by Habbit on 2008-12-11
Hm? I'm surprised, it seems the forums no longer have the amount of geek population they once had. Maybe I posted in the wrong section?

---

### Post by dribeas on 2008-12-11
> **Habbit said:**
> This has been bugging me for some time: the stream classes in the C++ standard library can be used in expressions like "if(stream)" or "while(!stream)". I thought support for such operations would be implemented through a "operator bool" member function, i.e. a cast operator to bool. However, it is really managed by an "operator!" (not surprising) and a "operator void*" (wtf?).

Theoretically, what happens in an expression like "if(cin >> myvar)" is that the istream& returned by operator>> is turned into a void* by "istream:: operator void*", which then gets evaluated by the if statement. However, why isn't this managed by a "istream:: operator bool"? Why are _two_ implicit casts (from istream to void* to bool) performed?.

Maybe my asking this question shows my marginal level of knowledge of C++, but I hope some guru (or geek :KS) here would shed some light into the mystery. Thanks everyone!

This is a hard question, and not so simple to answer. The basic idea is that cast operators open your code to a whole set of unwanted conversions. Choosing void* instead of bool closes some of those unwanted doors, even if not all.

```

struct X {
   operator bool() { return true; }
};
int main()
{
   X x;
   //int i = std::cin; // won't compile void* cannot be converted to an integer type implicitly
   int i = x; // compiles fine, as bool can be implicitly converted to int
}

```

Later on people came with other solutions, as providing a conversion operator to a pointer to a private class, but the current standard was already there.

---

### Post by Habbit on 2008-12-11
> **dribeas said:**
> Choosing void* instead of bool closes some of those unwanted doors, even if not all.

That makes sense, but still, why [FONT="monospace"]void*[/FONT] instead of [FONT="monospace"]const void*[/FONT]? I mean, both work equally well on conditional statements and loops, and the cast is declared as [FONT="monospace"]operator void*() const[/FONT], i.e. creating a non-const pointer from a const object/reference/whatever. In fact, the GNU stdlibc++ code for streams is:```
template<typename CharT, typename Traits>
basic_ios<CharT, Traits>::operator void*() const {
    return this->fail() ? 0 : const_cast<basic_ios*>(this);
}
```That is, the code has to explicitly cast the constness of the [FONT="monospace"]this[/FONT] pointer away. This seems a result of severe brain damage to me, but maybe there is a reason to have code that indirectly allows me to write code like [FONT="monospace"]delete std::cout;[/FONT] :lolflag:

*PS: I should add that trying to [FONT="monospace"]delete[/FONT] the pointer passed by the discussed cast operator results in a warning about the deletion of void pointers being undefined and a runtime disaster (actually, a "libc detected - free() - invalid pointer" abort). *

---

### Post by Kazade on 2008-12-11
This page holds the answer: [http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.4](http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.4)

---

### Post by Habbit on 2008-12-11
> **Kazade said:**
> This page holds the answer: [http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.4](http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.4)
That's the page that prompted my question, actually. It explains *how* the [FONT="monospace"]while(cin >> foo)[/FONT] construction works, but not *why* its design has the kind of "minor" defects I mentioned, like: in both conditional statements and loops a [FONT="monospace"]const void*[/FONT] expression suffices (at least on g++ 4.3 :p), so why insist on casting a const object into a non-const [FONT="monospace"]void*[/FONT]?

---

### Post by Kazade on 2008-12-11
> **Habbit said:**
> That's the page that prompted my question, actually. It explains *how* the [FONT=monospace]while(cin >> foo)[/FONT] construction works, but not *why* its design has the kind of "minor" defects I mentioned, like: in both conditional statements and loops a [FONT=monospace]const void*[/FONT] expression suffices (at least on g++ 4.3 :p), so why insist on casting a const object into a non-const [FONT=monospace]void*[/FONT]?


OK I think I get it...

The istream header defines the following operator:

__istream_type& operator>>(void*& __p);

Of course if you are chaining stuff... you want a non-const void* so that you can edit fill the value from the input. I think that's the reason.

---

### Post by Habbit on 2008-12-11
> **Kazade said:**
> Edit: IGNORE WHAT I SAID I'M TIRED AND TALKING RUBBISH :) 
I sooo understand you: I've been studying non-stop for the last 4 days (I have a thermodynamics exam this Saturday) and caffeine has been my friend. Withdrawal, however, will be much worse :D

---

### Post by dribeas on 2008-12-11
> **Habbit said:**
> 
This seems a result of severe brain damage to me, but maybe there is a reason to have code that indirectly allows me to write code like [FONT="monospace"]delete std::cout;[/FONT] :lolflag:


No matter how many consts you add there, you will still be able to delete it:
```

struct X
{
   operator void const * const () { return 0; }
};
int main()
{
   X x;
   delete x; // warning: result is undefined
}

```

That is why later trends go into using a private class like:
```

class X
{
   class private_class { private: ~private_class(); }
public:
   operator X::private_class* () { return 0; }
};
int main()
{
   X x;
   delete x; // error private_class has no public destructor
}

```

It can be implemented either as a private class or in an unnamed namespace.

---

### Post by Kazade on 2008-12-11
> 
I sooo understand you: I've been studying non-stop for the last 4 days (I have a thermodynamics exam this Saturday) and caffeine has been my friend. Withdrawal, however, will be much worse 

Hehe sorry I edited that post again, but I think that I still am talking nonsense. I'm gonna think about this and post back later... after coffee ;)

---

### Post by dribeas on 2008-12-11
> **Kazade said:**
> OK I think I get it...

The istream header defines the following operator:

__istream_type& operator>>(void*& __p);

Of course if you are chaining stuff... you want a non-const void* so that you can edit fill the value from the input. I think that's the reason.

I don't quite see where this is relevant to the discussion. As pointed in the C++FAQ-lite, operator>> is left-associative, so that when you are chainning you get:

```

( std::cin >> var1 ) >> var2;

```

With the parenthesized expression returning a std::istream that does not get converted to a pointer, but rather used directly in the call to std::istream.operator>>( std::cin, var2 ).

I fail to detect now a valid use of the operator>> for insertion into a void*, but anyway it is not relevant to the question.

---

### Post by Kazade on 2008-12-11
Yeh sorry, I'm completely not making any sense :)

I've had a look everywhere and even in the spec. It just says that streams should provide operator void*() it doesn't say why it's that way.

I'm intrigued to find out too.

---

### Post by Habbit on 2008-12-11
Regarding [FONT=monospace]istream& istream:: operator>>(void* p)[/FONT], it's a simple input routine for pointers, i.e. it is not related to my OP, though I can't grasp why would the standard library provide a mechanism for easy and direct parsing of things as non-portable as pointers :confused: Nevertheless, I also can't find a word on why the "good state check" cast must remove the constness from the pointers.

I'm also baffled as to why the compiler allows deleting a [FONT=monospace]const X*[/FONT], automatically performing a [FONT=monospace]const_cast<X*>[/FONT] without even a warning (and I'm on -Wall -Wconversion -pedantic !). In particular, directly invoking [FONT=monospace]operator delete[/FONT] on such a pointer fails with a compiler error, since the function (sanely) expects a non-const pointer.

---

### Post by Kazade on 2008-12-11
I've done some research into this. Apparently the C++ standard allows deletion using pointers to const types. So making it const void* won't make any difference you could still write "delete std::cin" and it would compile. I guess as it doesn't make a difference they just chose to use the non-const version.

It seems like this idiom of casting to void* is quite common (I'd never noticed it before today). There is more information (and a safe implementation) here: [http://www.artima.com/cppsource/safebool2.html](http://www.artima.com/cppsource/safebool2.html)

---

### Post by dribeas on 2008-12-12
> **Habbit said:**
> I'm also baffled as to why the compiler allows deleting a [FONT=monospace]const X*[/FONT], automatically performing a [FONT=monospace]const_cast<X*>[/FONT] without even a warning (and I'm on -Wall -Wconversion -pedantic !). In particular, directly invoking [FONT=monospace]operator delete[/FONT] on such a pointer fails with a compiler error, since the function (sanely) expects a non-const pointer.

It does not fail because the pointer is constant, but because the memory was never allocated with new. In fact, std::cin/cout/cerr are defined as:

```

// C++03 Standard, 27.3
namespace std
{
   extern istream cin;
   extern ostream cout;
   extern ostream cerr;
   extern ostream clog;
}

```

Thus you are getting the same error as if you wrote:

```

int main()
{
   int a;
   delete &a;
}

```

---

