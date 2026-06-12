---
title: "Object-c question"
date: 2012-06-03
forum: Programming Talk
---

### Post by roknron on 2012-06-03
I've been reading a bit on the Object-c language and was trying to relate to some of the difference in ANSI C.  Is it a good comparison to look at the interface code the same as function prototypes and the implementation the same as the function it self?  The examples I've found us the analogy of a car is a class as a chevy is an object of the car class?  Is that right as well?

---

### Post by hyper2hottie on 2012-06-03
First question.  Have you ever done any object oriented programming in other languages?  If you have never done object oriented programming then you might want to try a different language such as Java or C# to learn object oriented coding.

Your analogy for a car being the class and the chevy being the object is correct.  A class is an encapsulation and abstraction of an object.  One way to relate this to ANSI C is to think of an integer.  The integer could be called a class where it abstracts away the bits into a number.  An integer can have 32 bits, for example.  This is part of the class.  A car can have a color, body type, number of wheels, etc.

You can look at instantiating a class variable just like an integer variable.

int integerVariable;
Car carVariable;

Here you can see the relationship.  Int is the type of integerVariable just like Car is the type of carVariable.  What is special in object oriented programming is that you can define the Car class to have methods and variable inside of it.  So you can change its state.

--------------------------------
I believe that your understanding of an interface is slightly off.  I have not ever coded in objective C so I do not know its specifics.  In most objective languages an interface is used to make a subset of classes consistent.  It allows you to create the interface, use that as the type of your variable and then actually have a different class instantiated in the variable.  This can be confusing as it gets into static and dynamic binding(don't know how Objective C handles this) and is not necessary for a beginner.  

One big difference is that prototypes are there for the compiler.  It allows a function to access a function defined below it.  Interfaces are used to allow abstraction, making coding easier/more consistent.  As a beginner, you probably don't need to grasp interfaces to strongly just yet.  Worry more about classes first.

---------------------------------
Well, sorry for the wall of text.  If I have incorrectly assumed your knowledge of Object oriented languages then I apologize. 

If anything in my message is not true for Objective C please let me know.  As I mentioned, I have never coded in Objective C and am basing this information off of my knowledge of procedural C as well as C++, Java, and C#

---

### Post by 11jmb on 2012-06-03
> **roknron said:**
> Is it a good comparison to look at the interface code the same as function prototypes and the implementation the same as the function it self?  


I'm not entirely sure what you mean here. I like to think of headers and a sort of guarantee that the functions are implemented elsewhere. In this respect a class interface would be similar; It is just another layer of organization, but you are still guaranteeing that the functions are implemented elsewhere.

> **roknron said:**
> 
The examples I've found us the analogy of a car is a class as a chevy is an object of the car class?  Is that right as well?

This is ambiguous. Chevy could just as easily be a subclass. A better example of an object might be Bob's '64 Malibu SS, which has all of the attributes described by "Car" as well as any subclasses, such as "Chevrolet" or "Chevelle"

---

### Post by r-senior on 2012-06-04
> **hyper2hottie said:**
> I believe that your understanding of an interface is slightly off.  I have not ever coded in objective C so I do not know its specifics.  In most objective languages an interface is used to make a subset of classes consistent.
Objective-C calls this a protocol rather than an interface.

The @interface directive in Objective-C is used to define the "public" API for the class. The interface is usually defined in a .h file which other files can import to get the relevant definitions. It can define instance variables and method prototypes.

The implementation goes in a separate .m file that has the method bodies and accessors for instance variables as required.

For example:

*Driveable.h* 
```

#import <Foundation/Foundation.h>

@protocol Driveable <NSObject>

- (void)drive;

@end

```

*Car.h* 
```

#import <Foundation/Foundation.h>
#import "Driveable.h"

// Car is a subclass of NSObject and implements the Driveable protocol
@interface Car : NSObject <Driveable>
{
    NSString *_model;
}

- (NSString *)model;
- (void)setModel:(NSString *)model;

@end

```


*Car.m* 
```

#import "Car.h"

@implementation Car

- (void)drive
{
    NSLog(@"Implement drive here ...");
}

// Accessor and mutator for model property

- (NSString *)model
{
    return _model;
}

- (void)setModel:(NSString *)model
{
    // Manage the reference counting of the objects
    if (_model != model) {
        [_model release];
        _model = [model retain];
    }
}

@end

```

```

#import "Car.h"
...
// The mini variable is an object, Car is the class.
// Allocation allocates heap memory (like malloc() in C)
Car *mini = [[Car alloc] init];
[mini setModel:@"Mini Cooper"];
[mini drive];
...
// Release the object, if nobody else has a reference, reference count
// drops to zero and object is deallocated (like free() in C)
[mini release];
...

```

I've written that code off the top of my head so it may have mistakes but it's the general idea. This is also an Objective-C 1.x style of coding as you would use with GNUStep. Modern Objective-C, 2.0 as used in iPhone/iPad has properties and automatic reference counting for simpler memory management. I can give the equivalent example in the modern style if anyone wants it.

---

### Post by hyper2hottie on 2012-06-04
```
 	Quote:
 	 	 		 			 				 					Originally Posted by **hyper2hottie** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11996274#post11996274") 				
 				*I believe that your understanding of  an interface is slightly off.  I have not ever coded in objective C so I  do not know its specifics.  In most objective languages an interface is  used to make a subset of classes consistent.*
 			 		 	 	 
Objective-C calls this a protocol rather than an interface.

The @interface directive in Objective-C is used to define the "public"  API for the class. The interface is usually defined in a .h file which  other files can import to get the relevant definitions. It can define  instance variables and method prototypes.

The implementation goes in a separate .m file that has the method bodies and accessors for instance variables as required.

```

Thanks for the correction. 

Your example is excellent.  I could almost write some objective C now.:)

---

