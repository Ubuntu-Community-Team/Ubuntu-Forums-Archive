---
title: "[C++] Abstract class and constructor problem"
date: 2006-05-07
forum: Programming Talk
---

### Post by Laterix on 2006-05-07
It's me again confused with C++. I have abstract base class Base and I have definied constructor for it Base(Object &a, Object2 &b). I derived that class and have no class Derived. I defined constructor Derived(Object &a, Object2 &b). Now my question is that when I create Derived *d = new Derived(a,b); how can I get derived constructor to call base class constructor.

I get this error
```

Derived.cpp: In constructor ‘Derived::Derived(Object&, Object2&)’:
Derived.cpp:22: error: no matching function for call to ‘Base::Base()’
Base.cpp:7: note: candidates are: Base::Base(Object&, Object2&)
Base.hpp:43: note:                 Base::Base(const Base&)

```

Hopefully someone can help me again. I'm very close to relase alpha version of my first C++ program. Thrilling, isn't it? :)

---

### Post by LordHunter317 on 2006-05-07
Your derived constructor should be of the form:```
Derived::Derived(Object& a, Object2& b) : Base(a, b)
{
    // Body
} 
```Note that the default constructor (i.e., Base()) is only implicitly declared and defined if you declare no other constructors.  If you define any other constructors and still want a default constructor, you must explictly declare it.  

If you don't specify a base constructor to call for all base classes in your derived constructor, the default constructor is automatically called.  If it doesn't exist, you get a compile-time error.

As a rule though, abstract classes with constructors scare me, as do types name 'Object' and 'Object2'.  They're both indicative of design problems, IME.  Care to give some more details?

---

### Post by Laterix on 2006-05-07
[QUOTE=LordHunter317]
As a rule though, abstract classes with constructors scare me, as do types name 'Object' and 'Object2'.  They're both indicative of design problems, IME.  Care to give some more details?
[/QUOTE]
Thanks for you reply. This was helpful. 

I changed those class names to make code easier to read for you, so don't worry about it. :) Real class names are Phone and SonyEricsson. 

I'm working on application that shows libnotify notifications when my phone rings or I receive SMS message. Here is a [UML]("http://users.utu.fi/ljtaim/mn/UML-refactory.png") I came up with. I have mostly implemented it already, but this abstract class doesn't like me. I put the line after constructor as you told, but now I get n+1 errors instead that one. There's something that I don't know about C++ inheritance system.

The Phone class constructor opens serialport connection, but I quess I could move that to another function. Are there any tricks I should know about abstract classes in C++?

My current error is a lot of these
```

/tmp/ccW8VknY.o: In function `SonyEricsson::call(long)':/home/late/programming/mobile-notifier/SonyEricsson.cpp:88: undefined reference to `SerialportConnection::sendMessage(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'

```

Oops: some parts of UML are outdated.

---

### Post by LordHunter317 on 2006-05-07
[QUOTE=Laterix]I changed those class names to make code easier to read for you, so don't worry about it. :) Real class names are Phone and SonyEricsson.[/quote]Again as a rule, if your design is so complicated that you have to simplify it for others, it might be a sign your design is too complicated. 
 
> My current error is a lot of these
```

/tmp/ccW8VknY.o: In function `SonyEricsson::call(long)':/home/late/programming/mobile-notifier/SonyEricsson.cpp:88: undefined reference to `SerialportConnection::sendMessage(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'

```This means you're trying to call a method that was never declared, or that the linker cannot find.  This could be because you failed ot specify the object or library file containing that code or because it doesn't actually exist.

As far as your class design:
If your factories only have one method, they probably shouldn't be a class.  They should be non-member, possibly friend, functions.  Stuff them and the related classes in the same namespace.  It's rather nonsensical to have factories as classes in C++ unless they do some sort of resource or other lifetime management.  IOW, if they have no state, they probably shouldn't be a class *per se*.  

Also, if you're not going to support more phones via a plugin mechanism, the right place for the factory function is as a static member of the class.  

I'm confused by all the wrapping around properties.  If they're just name->value pairs, just expose a map.  It's a logical interface in C++ and doesn't need any further abstracting.  I'm not sure the fact they are saved to/from a file requires a class.  Just have a save() function that's non-member.  I presume properties in the file are actually distinct from the objects they belong to, so this makes more sense, I think.  At anyrate, if you're going to wrap them, just directly expose a map.  It only makes sense to not do that unless you have a limited set of properties.  In which case, you should expose an identical interface to map that only allows for those fixed keys.  That way, STL algorithms can still be applied to your properties.  THhis may be more work, but worthwhile.

Third, do both phones really support everything in the phone ABT?  If not, you have a design problem, but C++ has an easy solution.

Finally, does SerialConnection really need to know about phone and vice-versa?  Cyclic relationships make resource management more difficult, and presumably SerialConnection has an FD associated with it, etc.  Or does serial connection solely exist within the lifetime of the Phone object and is always destroyed when the phone is?  If so, you're ok.

The problem with UML is what it doesn't tell you. ;)

---

### Post by Laterix on 2006-05-08
[QUOTE=LordHunter317] 
This means you're trying to call a method that was never declared, or that the linker cannot find.  This could be because you failed ot specify the object or library file containing that code or because it doesn't actually exist.
[/QUOTE]
Hmm... wierd, because I don't call that method anywhere. I just declare/define it.

[QUOTE=LordHunter317] 
If your factories only have one method, they probably shouldn't be a class.  They should be non-member, possibly friend, functions.  Stuff them and the related classes in the same namespace.  It's rather nonsensical to have factories as classes in C++ unless they do some sort of resource or other lifetime management.  IOW, if they have no state, they probably shouldn't be a class *per se*.
[/QUOTE]
Thanks for this tip. I actually tried to implement them as static functions at first, but couldn't get it work. :) But you're right, that there's no sense define a class for only one static method.

> 
Also, if you're not going to support more phones via a plugin mechanism, the right place for the factory function is as a static member of the class.  

Hmm... to Notity interface (abstract class) for example?

> 
I'm confused by all the wrapping around properties.  If they're just name->value pairs, just expose a map.  It's a logical interface in C++ and doesn't need any further abstracting.  I'm not sure the fact they are saved to/from a file requires a class.  Just have a save() function that's non-member.

Yes, it's quite bloated design for such a simple and small appilcation. I agree. I wanted to hide properties behind interface, because I'm planning to use gconf instead of conf-file in the future. I don't know anything about gconf right now, but I hope that I can hide it behind that Properties interface. AvatarManager wrapper is useless in technical point of view. It just adds abstraction with getAvatar() function. I might take that class away in the future also.

> 
Third, do both phones really support everything in the phone ABT?  If not, you have a design problem, but C++ has an easy solution.

Well, my Sony Ericsson does support all of those and a lot more! I'm not sure about my Nokia, but I'm very confident. :D No, seriously Phone interface is far from fixed. I have just put there some functions to be able to test this whole system. Phone class implements about half of the functions it has and other half is implemented in derived classes. This way common part is kept in one class.
Would you mind to tell me what this easy solution is that you refer above.

> 
Finally, does SerialConnection really need to know about phone and vice-versa?  Cyclic relationships make resource management more difficult, and presumably SerialConnection has an FD associated with it, etc.  Or does serial connection solely exist within the lifetime of the Phone object and is always destroyed when the phone is?  If so, you're ok.

This was part of the UML that was outdated. SerialportConnection does not know about Phone. Phone has serial connection and it lives just as long as phone. My idea was that serialport connection takes Phone class's handelReceivedMessage() function as parameter (callback). I just don't know how to do that yet, but I have understood that this is possible in C++. :) 

I have updated my [UML]("http://users.utu.fi/ljtaim/mn/uml.png") and also I draw [sequence diagram]("http://users.utu.fi/ljtaim/mn/sequence-diagram.png") to illustrate class creation/call relations.

Thanks for you reply again. I'm very happy that you used time to look my UML.

---

### Post by thumper on 2006-05-08
[quote=Laterix]My idea was that serialport connection takes Phone class's handelReceivedMessage() function as parameter (callback). I just don't know how to do that yet, but I have understood that this is possible in C++.[/quote]
The [boost signal and slots library](http://www.boost.org/doc/html/signals.html) would be good for this type of thing.

---

### Post by LordHunter317 on 2006-05-08
[QUOTE=Laterix]Hmm... wierd, because I don't call that method anywhere. I just declare/define it.[/quote]Clearly you are, otherwise the system wouldn't complain.

> Hmm... to Notity interface (abstract class) for example?I'm not sure I understand.  Notification almost certainly wouldn't be a plugin interface.

> Yes, it's quite bloated design for such a simple and small appilcation. I agree. I wanted to hide properties behind interface, because I'm planning to use gconf instead of conf-file in the future. I don't know anything about gconf right now, but I hope that I can hide it behind that Properties interface. This is a major danger.  You need to know what you're abstracting before you do so.  You need to kill this interface and redesign it after learning about gconf.

> Well, my Sony Ericsson does support all of those and a lot more! I'm not sure about my Nokia, but I'm very confident. :D No, seriously Phone interface is far from fixed. I have just put there some functions to be able to test this whole system. Phone class implements about half of the functions it has and other half is implemented in derived classes. This way common part is kept in one class.OK, but you need to remember the fundamental rule: Inheritence defines a 'is-a' relationship.  If all the children cannot implement everything in the parent class, the parent class is wrong or the children are not really children.  In this case, it would be the latter.

> Would you mind to tell me what this easy solution is that you refer above.Variants and vistors are usually a quick and easy solution when you don't care bout extensibility to external code (i.e., plugins loaded at runtime).

---

### Post by Laterix on 2006-05-08
> **LordHunter317]Clearly you are, otherwise the system wouldn't complain.
[/QUOTE]
You're right, I miss read the error. I call **this->c->sendMessage("ATD" + phoneNumber) said:**
> 
This is a major danger.  You need to know what you're abstracting before you do so.  You need to kill this interface and redesign it after learning about gconf.

Well, yes I'm well aware that this is not a way to make serious programs, but this is just "for fun" project and my way to learn C++. Remember, this is my very first C++ program ever. So, it's all about learning. If gconf doesn't fit to my interface then I just reject it and use config file.

> 
OK, but you need to remember the fundamental rule: Inheritence defines a 'is-a' relationship.  If all the children cannot implement everything in the parent class, the parent class is wrong or the children are not really children.  In this case, it would be the latter.

True, this is a really a annoying thing, because every phone support different things. Of course I could create some soft of "check what this one supports" thing.

Thanks for you reply again. I didn't have time to work on this today though...

---

### Post by LordHunter317 on 2006-05-08
[QUOTE=Laterix]You're right, I miss read the error. I call **this->c->sendMessage("ATD" + phoneNumber);** in SonyEricsson class. c is a pointer to SerialConnection class and it is declared in Phone class and is set in Phone constructor. It seems to me that dynamic binding fails here. You seem to be very advanced C++ programmer. Do you think this could be a problem?[/quote]No, it has nothing to do with a failure to dynamic bind.  You need to include the object file that has the code for the method in question on the command line.  The linker stage doesn't know about it.  Alternatively, pass all your C++ source files to the compiler invocation that generates the executable output.

---

### Post by Laterix on 2006-05-25
Hi again, I was busy and didn't have time to work on this project, but now I'm back with all new problems! :)

I got all error corrected and now it compiles neatly. My last remaining problem is about callback function. I tried to get it work with this [guide]("http://www.newty.de/fpt/fpt.html#chapter2") without any luck.

I have a **handleIncomingMessage(string message)** as a pure virtual function in a Phone class. This function is implemented in SonyEricsson class. Now I would like to pass this function as a callback function to SerialportConnection object and for more I would like to do this in Phone constructor. My [UML is here]("http://users.utu.fi/ljtaim/mn/uml.png").

Is this even possible? I can't figure out any way to get SerialportConnection to call Phone function.

---

### Post by thumper on 2006-05-26
The problem is that you are trying to pass a virtual function as a callback from the base class in it's constructor.  

The derived class is not constructed at the time you are wanting to pass a pointer to a function to the SerialportConnection object.  So you will not see any derived behaviour.

One way to solve this is to have a non-virtual method in your Phone class that is used as the callback, and it calls the virtual method.

So...
```

class Phone
{
   public:
      void incomingMessage(string const& message);
   protected:
      // pure or not - up to you
      virtual void handleIncomingMessage(string const& message) = 0;
   // ... everything else
};

void Phone::incomingMessage(string const& message)
{
   // virtual dispatch is done here
   handleIncomingMessage(message);
}
```
The Phone constructor registers the non-virtual incomingMessage function with the SerialportConnection object.

---

### Post by Laterix on 2006-05-28
[QUOTE=thumper]The problem is that you are trying to pass a virtual function as a callback from the base class in it's constructor.  
......[/QUOTE]

That's a good idea. Thanks for the tip.

---

