---
title: "Parsing a micro-laguage to c++ native code"
date: 2009-01-20
forum: Programming Talk
---

### Post by ArchangelUriel on 2009-01-20
I'm trying to use the operator overloading capabilities of c++ (and the #define from the preprocessor) to make the later code to be a valid c++ code.

```

AUTOMATON(A1) [
              STATES [
                      S(1), // Comments
                      S(2),
                      S(3),
                      FINAL S(4)
                     ]
               INPUT [
                      I(A),
                      I(B),
                      I(C),
                      I(D)
                     ]

              TRANSITION [ S(1), S(2) ] WITH [ I(A), I(B) ]
              TRANSITION [ S(1), S(3) ] WITH [ I(C) ]
              TRANSITION [ S(2), S(4) ] WITH [ I(D) ]
              ];
```
The code above is the equivalent of the constructor of an automaton.

I have created the 3 later classes to hold the data.

```

class states
class input
class automaton
```
class automaton holds an array of states, an array of inputs and array of transitions.

Any ideas how operator[] overloading can be used to transform this code into c++ native code?

---

### Post by dribeas on 2009-01-20
> **ArchangelUriel said:**
> I'm trying to use the operator overloading capabilities of c++ (and the #define from the preprocessor) to make the later code to be a valid c++ code.
[...]
Any ideas how operator[] overloading can be used to transform this code into c++ native code?

You are up to a really hard task. I am not sure whether even feasible. I will give it a try. Some of the things you might want to know are that operator[] can only take a single argument (and not a comma separated sequence of arguments as a regular function call) and it must be implemented as a member function.You can, and this may help, overload operator, to convert two arguments into a single resulting element.

I have given it a first try:

```

// class S
struct S {
   S( int v ) : v_( v ) {}
   int v_;
};

// convert a sequence of S(1), S(2), S(3) into std::list<S> { S(1), S(2), S(3) }
// that is, convert the sequence of comma separated elements into a single argument
std::list<S> operator,( S const & a, S const & b ); // generates the list [a,b]
std::list<S> operator,( std::list<S> l, S const & b ); // appends b to l

```

Now, operator[] must take a std::list<S> (single argument). But we are left with building an instance of a class that can implement such operator. I will try to find some time tomorrow to research into this, but it is already 2am and the alarm will ring out at 7. Good night.

---

### Post by ArchangelUriel on 2009-01-21
> **dribeas said:**
> Some of the things you might want to know are that operator[] can only take a single argument (and not a comma separated sequence of arguments as a regular function call) and it must be implemented as a member function.
That was one of my great problems.
> **dribeas said:**
> You can, and this may help, overload operator, to convert two arguments into a single resulting element.
This gave me a jump-start and destroyed my sleep. It's 7am and I'm still designing... :)

> **dribeas said:**
> Now, operator[] must take a std::list<S> (single argument). But we are left with building an instance of a class that can implement such operator. I will try to find some time tomorrow to research into this, but it is already 2am and the alarm will ring out at 7. Good night.

To simplify things a bit, I removed the TRANSITION part for now. So we actually remain with:
```
AUTOMATON(A1)[STATES[std::list<S>]INPUT[std::list<S>]];
```
Let's create some classes here.
```
class S{
   public:
   S(string s) : s_(s) {}
   std::list<S> operator[]( std::list<S> l){return l;}
   string s_;
};

class automaton{
   std::list<S> states_;
   std::list<S> input_;
   void operator[] (std::list<std::list<S> > l) 
   {
     states_ = *l.begin();
     input_ = *l.end();
   }
};
```
I don't know if this is going to work, but using the preprocessor we can create this macros:
```
#define AUTOMATON(name) automaton ##name
#define STATES tmp_s
#define INPUT , tmp_i

```
This will give us
```
automaton A1[tmp_s[std::list<S>], tmp_i[std::list<S>]];
```
Using
```
std::list<S> operator[]( std::list<S> l){return l;}
``` from class S, will give us ```
automaton A1[std::list<S>, std::list<S>];
which shall give us
automaton A1[std::list<std::list<S> >];
```
which (in a developer's paradise) will give us a new automaton with variable name A1 and two lists with symbols. 

Of course, all these are designed by a drunk, tired and out-of-inspiration developer, so probably they are totally wrong.

dribeas, thank you any way for the jump start you gave me. I suppose now I have something to work on. Saludos amistosos desde Grecia.

---

### Post by jpkotta on 2009-01-21
It sounds like you want flex and bison.  I have never had the need to figure them out, but this is what they're for.  They generate C code, which would be fairly straightforward to integrate, but I wouldn't be surprised if there was a C++-specific version.  I know there is a Python class that implements flex+bison.

*Maybe* you could do this with cpp, but that would be beyond preprocessor abuse, and probably not with the syntax you want.

---

### Post by dribeas on 2009-01-21
> **jpkotta said:**
> It sounds like you want flex and bison.  I have never had the need to figure them out, but this is what they're for.  They generate C code, which would be fairly straightforward to integrate, but I wouldn't be surprised if there was a C++-specific version.  I know there is a Python class that implements flex+bison.

*Maybe* you could do this with cpp, but that would be beyond preprocessor abuse, and probably not with the syntax you want.

Completely agree. Parser tools (or even implenting a parser in C++) are probably the way to go if you want to parse the automaton. Now, it seemed as a interesting test of how much you can force the c++ into domain specific languages.

My believe is that it can be done with just a couple of macros, most of them just to insert separators where there are none.

---

