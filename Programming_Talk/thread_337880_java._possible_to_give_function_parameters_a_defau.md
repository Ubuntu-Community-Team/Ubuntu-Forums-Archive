---
title: "java. possible to give function parameters a default value?"
date: 2007-01-13
forum: Programming Talk
---

### Post by cocteau on 2007-01-13
I would have thought this was a simple question but I can't seem to find the answer anywhere.

Is it legal in Java to declare a default value for parameter functions in case none is supplied, like it is in C++?

Example:

void someFunction(int date, String name = "none")
{
     ...
}

---

### Post by jblebrun on 2007-01-13
> **cocteau said:**
> I would have thought this was a simple question but I can't seem to find the answer anywhere.

Is it legal in Java to declare a default value for parameter functions in case none is supplied, like it is in C++?

Example:

void someFunction(int date, String name = "none")
{
     ...
}

I googled for Java Parameter Default and this was the first link that came up:
[http://www.experts-exchange.com/Programming/Programming_Languages/Java/Q_21300351.html](http://www.experts-exchange.com/Programming/Programming_Languages/Java/Q_21300351.html)

The answer is: no. :-)

---

### Post by Tomosaur on 2007-01-13
Generally speaking, a function should never be called if there's no data to pass to it. If you find yourself in such a situation, chances are you've planned something incorrectly. Those functions which conceivably require a default value are likely poorly implemented, and can probably be broken up into at least two functions - one which requires data, and one which doesn't. If it can't, then the mistake is elsewhere.

Of course, you can always specify a fallback value, either through a class field, or within the body of the method, but it's not always applicable. Best bet (in Java, at least) is to go back and rethink what you're doing.

---

### Post by cocteau on 2007-01-13
True, but my problem is that I want to limit the number of constructors I need to define for a class. I have three attributes that each need to have a default value of none are declared so I could declare a single constructor instead of 7 seperate ones to have one for each combination of parameters.

---

### Post by Tomosaur on 2007-01-13
> **cocteau said:**
> True, but my problem is that I want to limit the number of constructors I need to define for a class. I have three attributes that each need to have a default value of none are declared so I could declare a single constructor instead of 7 seperate ones to have one for each combination of parameters.

Sorry, I'm a little unclear. Could you explain more specifically, or better yet, show your code? (Understandable if you can't).

---

### Post by jblebrun on 2007-01-13
> **Tomosaur said:**
> Sorry, I'm a little unclear. Could you explain more specifically, or better yet, show your code? (Understandable if you can't).

He means that he has some class that has three parameters for which many cases can simply use a default value. Using constructor overloading, you need to specify many additional constructors in order to specify default parameters. For example:

```

Constructor(a,b,c) {
   <other stuff>
}

Constructor(a,b) {
   c=0
   <other stuff>
}
Constructor(a) {
   b=0
   c=0
   <other stuff>
}

Constructor() {
  a=0
  b=0
  c=0
  <other stuff>
}

```

This is considerably more code than
```

Constructor(a=0,b=0,c=0) {
   <other stuff>
}

```

I'm still not following your argument about why functions with default parameters are a bad thing. Can you explain this a bit more, or perhaps forward me to some references that discuss this issue, and explain why it's undesirable to use default parameters?

---

### Post by Tomosaur on 2007-01-13
> **jblebrun said:**
> He means that he has some class that has three parameters for which many cases can simply use a default value. Using constructor overloading, you need to specify many additional constructors in order to specify default parameters. For example:

```

Constructor(a,b,c) {
   <other stuff>
}

Constructor(a,b) {
   c=0
   <other stuff>
}
Constructor(a) {
   b=0
   c=0
   <other stuff>
}

Constructor() {
  a=0
  b=0
  c=0
  <other stuff>
}

```

This is considerably more code than
```

Constructor(a=0,b=0,c=0) {
   <other stuff>
}

```

I'm still not following your argument about why functions with default parameters are a bad thing. Can you explain this a bit more, or perhaps forward me to some references that discuss this issue, and explain why it's undesirable to use default parameters?

I don't have any to hand, but that's what I was always told, the logic is as follows (and is contrived from some software engineering, possibly more so than software development). It's not like a standard or anything, it's just what I was always told (and feel) was good practice:

1) In cases where multiple constructors are required, this is often down to programmer taste, rather than due to any real benefit. Total lines of code is likely to be unaffected if you use multiple constructors rather than one with default values. Clarity of code implies that wherever possible, code should be clear as to what the purpose of the code is. When you have something like this:
> 
```

Constructor(a=0,b=0,c=0) {
   <other stuff>
}

```

it is likely that this particular constructor will contain a fair amount of code which runs along the lines of deciding what to actually do with the data - otherwise there would be no need for extra constructors in the first place, as the procedure would be the same every time the constructor was called. In the case I suggest - you have more constructors, true - but less processing time would be used, and the code embodied in the seperate constructors is directly relevant to that constructor. Lines of code is not directly related to size of application - and for the sake of maintainablity - code clarity and obviousness is more important than cutting corners and speed to delivery. I guess it boils down to the taste of each individual programmer, but generally speaking, it is better to write code which can be examined and modified later on, than code which needs to be figured out before any work can be done on it.

2) Default paramaters are not bad in themselves, but there's no need for them aside from cutting code size. As I already stated above, less lines of code is not always benefical. Obviously, the debate is one of opinon rather than rule, and I don't really feel very strongly either way. It makes sense to me, however - that in an object/class which has multiple implementations (hence the need for multiple constructors), it's better to just write the different constructors than compressing everything into one constructor and working out what to do later. Lots of smaller constructors is better than one big constructor, to sum it all up, but like I said, it's not set in stone (except in Java, where you have no choice :P).

---

### Post by cocteau on 2007-01-13
> **Tomosaur said:**
> Obviously, the debate is one of opinon rather than rule, and I don't really feel very strongly either way. It makes sense to me, however - that in an object/class which has multiple implementations (hence the need for multiple constructors), it's better to just write the different constructors than compressing everything into one constructor and working out what to do later. Lots of smaller constructors is better than one big constructor, to sum it all up, but like I said, it's not set in stone (except in Java, where you have no choice :P).

Well I disagree. Having a single constructor with default parameters would remove the responsibility of having to declare all parameters every time I create an instance of the class or create a host of constructors to decide what to do if I declare one or two but all three parameters.

And in this case it really would equal less lines of code. The scenario is a simple. Supply the constructor with an object to make it reference to it, and if no object is supplid set the reference in the class to null.

And since my constructor looks like this:

```

    public Person(String navn, String adresse, String by, int tlf, String status, boolean foredragsHolder,
                    int ankomst, int afrejse, Firma firma, Hotel hotel, Ledsager ledsager)
    {
        //set parent class parameters
        ankomstDato = ankomst;
        afrejseDato = afrejse;
        
        //set own parameters
        this.navn = navn;
        privatAdresse = adresse;
        by_land = by;
        telefonNr = tlf;
        this.foredragsHolder = foredragsHolder;
        
        this.status = status;
        this.firma = firmat;
        this.hotel = hotel;
        this.ledsager = ledsager;
        
        regning = beregnPris();
    }

```

...declaring this six times over again seems to be an incredible hassle when I could specified a default to begin with, and as you can see from this it requires no extra conditions within the constructor itself.

I'll go with the other solution and just supply the parameters by hand when I create a new instance of this class but well... the language should really be there to help you and I prefer too much choice over too little. But I suppose that just indicates that I shouldn't be using Java to begin with :P

---

### Post by Tomosaur on 2007-01-13
Just out of interest, what is the difference between the various implementations of the Person class? I can't read whatever language that's written in :P

---

### Post by lloyd mcclendon on 2007-01-13
i didn't read the whole thread but you can just use overloaded constructors as delegates to one another.


```
Person()  {
  this(0);
}


Person(int x)  {
   this(x, null);
}


Person(int x, O y)  {
   this(x, y, new Z());
}

Person(int x, O y, Z z)  {
    this.x = x;
    this.y = y;
    this.z = z;
}

{
    Person p1 = new Person();
    Person p2 = new Person(5);
    Person p3 = new Person(5, someObject);
//  etc
}
```

---

### Post by sphinx on 2007-01-13
I like to pass 'null' into a method to signal I want to use a default value.

```

public void doSomething(Object o1, Object o2) {
   if(o1==null) {
      o1 = new DefaultObject1()

  }
 if(o2==null) {
      o2 = new DefaultObject2()

  }
  // do the stuff you wanted to do.
}

```

However I dont use it often, because genrally 'null' is a litigimate value and its really not good to use litigitmate values for flagging behavior.

Depending on your situation, it may solve your problem, or make it uglier.

---

### Post by kripkenstein on 2007-01-14
> **Tomosaur said:**
> Generally speaking, a function should never be called if there's no data to pass to it. If you find yourself in such a situation, chances are you've planned something incorrectly. Those functions which conceivably require a default value are likely poorly implemented, and can probably be broken up into at least two functions - one which requires data, and one which doesn't. If it can't, then the mistake is elsewhere.


I disagree completely. Default parameters are very useful in some cases, which is the reason they are allowed in e.g. Python. Basically a default parameter is like overloading the function to have several versions, and the overloaded versions all call the base version with the default parameter values plugged in. If you have several such parameters, and use call-by-name, then overloading can get very tedious and lengthy. Default parameters solve this. (But they are useful even with a single parameter, again because the code is shorter and clearer.)

Example (Python vs. C++):

```

def Norm(x, y, p=2.0):
   return pow(pow(x,p) + pow(y,p), 1/p)

```

instead of

```

float Norm(float x, float y, float p) {
   return pow(pow(x, p) + pow(y, p), 1/p);
}

float Norm(float x, float y) {
   return Norm(x, y, 1.0);
}

```

Here we use the Euclidean norm (p=2) by default, but other norms are also possible, in very short and readable Python (IMO).

---

### Post by Grey on 2007-01-14
Actually, C++ supports default values as well.  So in C++, it would look like this:

```

float Norm(float x, float y, float p=2.0) {
   return pow(pow(x, p) + pow(y, p), 1/p);
}

```

Not much different at all.  ;)  It's just bad languages (IMO) like Java that it gets verbose.

(NOTE:  My dislike for Java stems from its slow runtime, lack of unsigned types, and now lack of default values.  I realize you can work around all these issues, but I would rather not, and just use Python.  Or C.  Not trying to start a flame war.).

---

### Post by kripkenstein on 2007-01-14
> **Grey said:**
> Actually, C++ supports default values as well. 

Thing is, I wanted both examples in Python, then realized Python doesn't have function overloading... so I wrote the second one in C++ ;)

---

### Post by Grey on 2007-01-14
No function overloading in Python????

Wow.  That's something I use all the time.  (I try not to abuse it, but sometimes I like the option of passing in either a struct or all the members of the struct.  This is useful when doing vector math).

I have used Python a little bit, but never in a big project.  That will be something to remember when the time comes.

---

### Post by cocteau on 2007-01-14
I liked McClendon's answer. I think I will try to incorporate that. I don't think it's a particularly pretty feature of Java that you have to do something like that but at least a better way to get it done than declaring each function seperately.

> **sphinx said:**
> I like to pass 'null' into a method to signal I want to use a default value.

The thing about passing null to an instance is that you still have to declare it every time you call create the instance and I would like to avoid that.

> **Tomosaur said:**
> Just out of interest, what is the difference between the various implementations of the Person class? I can't read whatever language that's written in :P

It's danish :P 

It's a made up example for a programming class I'm doing. It's about people signing up to attend a conference. The first stuff is personal information name, address, phone number. The part that is causing trouble however is that they may be employed by a firm (firma), they may request a hotel room and they may bring a companion (ledsager).

Since it's a beginners course the implementation doesn't go beyond that and I'm seriously considering copping out and just leave a note saying that's it's the Controller's job to make sure that default values are supplied to Person's constructor.

---

### Post by kripkenstein on 2007-01-14
> **Grey said:**
> No function overloading in Python????

Wow.  That's something I use all the time.  (I try not to abuse it, but sometimes I like the option of passing in either a struct or all the members of the struct.  This is useful when doing vector math).

I have used Python a little bit, but never in a big project.  That will be something to remember when the time comes.

Well, Python doesn't need it as much as other languages do. For one thing, overloading so you can get parameters of different types isn't needed in Python. Also, you have default parameters as  mentioned in this thread. And you can use parameters by-name, instead of by-position. The thing is, overloading was originally meant to solve things that these three capabilities solve. So Python doesn't really need overloading.

---

### Post by justinup on 2009-07-02
of cause simpler is better, overloading makes the writing simpler but the logic complex. it's not a matter of taste but where you want the complexity to be. 
also i would like to see some language where you can set the default value on the fly.

---

### Post by bodselecta on 2009-07-02
Overloading is the right way to do this in java and I don't think it's more complex.

Overloading is not about OO but for the purposes of making the same method call easier to call (a kind of c++ equivalent), you can implement the defaults possibly at class level or the constructor and call them when you need them i.e. in your un- overloaded methods
my tuppenceworth ;)

---

### Post by Can+~ on 2009-07-02
> **justinup said:**
> of cause simpler is better, overloading makes the writing simpler but the logic complex. it's not a matter of taste but where you want the complexity to be. 
also i would like to see some language where you can set the default value on the fly.

January 14th, 2007.

As for the question. Both Python and C++ have default parameters as stated above, I guess Perl, PHP and Ruby have too (as the high level scripting languages they are)

In fact, python has default variables even for standard functions and methods, for example, sort:

[PHP]mylist = [6, 4, 1, 5, 3, 2, 7]

mylist.sort()

print mylist #outputs [1, 2, 3, 4, 5, 6, 7][/PHP]

Has a parameter which defines the comparative function, that can be modified

[PHP]mylist = [6, 4, 1, 5, 3, 2, 7]

mylist.sort(lambda x,y: y-x)

print mylist #outputs [7, 6, 5, 4, 3, 2, 1][/PHP]

---

