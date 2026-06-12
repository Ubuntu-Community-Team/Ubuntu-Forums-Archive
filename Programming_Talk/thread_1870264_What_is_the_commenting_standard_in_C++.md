---
title: "What is the commenting standard in C++?"
date: 2011-10-27
forum: Programming Talk
---

### Post by akand074 on 2011-10-27
I'm used to Java, and I really like their extensive documentation (javadoc). C++ doesn't seem to have anywhere near as much documentation. From people I've talked to and source code I've seen, people either like to use the javadoc standard for commenting C++ programs (apparently there is tools to give you a javadoc-like experience) and others use the absolute minimal amount of commenting. I often use the standard javadoc for C++ where I just comment a class like such:

```

/**
 * @author akand074
 * @version 1.0
 * Date
 * Info about class
 * /
public Class A {
// Instance variables ************
double x;
double y;

//Constructors ************
public A() {}

//Public methods ************

/**
 * Info about method
 * @param x Info about variable
 * @param y Info about variable
 * @return double Info about return value
 */
public double foo(double x, double y){ }

.... etc

```I comment similarly in C++, some say (I think including my textbook) to avoid /* */ comments but use // for each line to make it easier to comment out large blocks of code for debugging. I don't usually comment within the method or specific variables unless I feel it may not be clear what I'm doing. Does anyone have experience in a real world work environment or any personal recommendations on how to comment C++ code?

---

### Post by gsmanners on 2011-10-27
My experience is that it varies greatly. Some coders slap together uncommented spaghetti code ("comments are for the weak" or "true Klingons don't comment") and some coders like to put comments for everything. As for commenting out code, I've seen some of that, but I more often see ifdefs, personally.

As for how to comment, I would just say comment as much as you can provided it makes the code more readable rather than less.

---

### Post by Arndt on 2011-10-27
> **akand074 said:**
> I'm used to Java, and I really like their extensive documentation (javadoc). C++ doesn't seem to have anywhere near as much documentation. From people I've talked to and source code I've seen, people either like to use the javadoc standard for commenting C++ programs (apparently there is tools to give you a javadoc-like experience) and others use the absolute minimal amount of commenting. I often use the standard javadoc for C++ where I just comment a class like such:

```

/**
 * @author akand074
 * @version 1.0
 * Date
 * Info about class
 * /
public Class A {
// Instance variables ************
double x;
double y;

//Constructors ************
public A() {}

//Public methods ************

/**
 * Info about method
 * @param x Info about variable
 * @param y Info about variable
 * @return double Info about return value
 */
public double foo(double x, double y){ }

.... etc

```I comment similarly in C++, some say (I think including my textbook) to avoid /* */ comments but use // for each line to make it easier to comment out large blocks of code for debugging. I don't usually comment within the method or specific variables unless I feel it may not be clear what I'm doing. Does anyone have experience in a real world work environment or any personal recommendations on how to comment C++ code?

Comment out chunks of code with the preprocessor directive #if 0. Those nest. Then you can use ordinary comments for actual commenting.

---

### Post by muteXe on 2011-10-27
I have used Doxygen in a former job on a large-ish c++ project. Worked pretty well.

---

### Post by karlson on 2011-10-27
> **akand074 said:**
> Does anyone have experience in a real world work environment or any personal recommendations on how to comment C++ code?

Just have one suggestion:

Write your code in such a way that it doesn't need comments.

When I put in comments those are usually for the Doxygen to generate documents nothing more.  For that I normally use //

---

### Post by karlson on 2011-10-27
> **gsmanners said:**
> My experience is that it varies greatly. Some coders slap together uncommented spaghetti code

In this case even comments won't help you.

---

### Post by muteXe on 2011-10-27
> **karlson said:**
> Just have one suggestion:
Write your code in such a way that it doesn't need comments.


ROFL. Do you actually think this is possible all of the time??

---

### Post by karlson on 2011-10-27
> **muteXe said:**
> ROFL. Do you actually think this is possible all of the time??

Yes.

Write functions with descriptive names, use descriptive names for variables, functions under a page of code.

Code written like this I have never had a problem understanding without comments even when I was in school.

---

### Post by 11jmb on 2011-10-27
I think that the Javadoc style is a little bit wordy unless you are using doxygen

I agree somewhat with Karlson that if you design your programs in a way that they are broken into small logical pieces with descriptive file names, function names, and variable names, very few comments are needed. I will usually put a short comment above each function header, and thats about it.

---

### Post by muteXe on 2011-10-27
I agree 'somewhat' with him as well, i just don't believe you can write **all** of your code such that it is understandable at a glance. For example, you could have a method that's full of bit-shifting operations.

---

### Post by 11jmb on 2011-10-27
> **muteXe said:**
> I agree 'somewhat' with him as well, i just don't believe you can write **all** of your code such that it is understandable at a glance. For example, you could have a method that's full of bit-shifting operations.

Obviously it depends on the context, but good function names, logical organization, etc. should cut your comments down do the bare minimum (like explaining anything tricky that you did)

---

### Post by karlson on 2011-10-27
> **muteXe said:**
> I agree 'somewhat' with him as well, i just don't believe you can write **all** of your code such that it is understandable at a glance. For example, you could have a method that's full of bit-shifting operations.

If the name of the method explains what it does and instead shift by 1, 2, 5, 10 you have enum'ed constant names I don't see an issue.

---

### Post by Arndt on 2011-10-27
> **karlson said:**
> Yes.

Write functions with descriptive names, use descriptive names for variables, functions under a page of code.

Code written like this I have never had a problem understanding without comments even when I was in school.

The code encountered in school tends to be neither large nor complicated.

---

### Post by karlson on 2011-10-27
> **Arndt said:**
> The code encountered in school tends to be neither large nor complicated.

It wouldn't be.  Download one of open source projects, like mysql, gcc, firefox, QT and take a look at the code.

---

### Post by akand074 on 2011-10-27
That's what I was saying, people have said that your code should be written as clear as possible so that it's self explanatory and then only comment what may not be obvious. But I was talking about any particular standard, not only for understanding the code itself but for being able to understand what a function/class does without even looking at the code. I know C++ isn't like Java, but in Java if I'm using encapsulated classes/methods when I get a list of methods in my IDE I can click one and it gives me the information about the method, the expected parameters and what the return value is so I can understand what the method does and what exactly it wants without having to go to the code. 

An example for using comments is, lets say, using a math library. If it wasn't commented, although I can look at the function and be clear what it's doing, like taking in a value, multiplying it by something, maybe evaluating an equation that is obvious to read, but it may not always be clear what the equation is and what it's used  for. 

A better example is writing an Android application. I often have no clue what most methods are, what they do, and what the parameters/return types even are even with descriptive names as there is just such a gigantic amount of available classes and object types that can be passed, returned, converted, grouped and displayed. The documentation helps you understand what the method is, what it does, what it returns, what exactly are the types it needs because even if I went to the code I'd have no clue what was going on because it would have even more code within it that I don't understand, so I'd basically end up jumping from class to class understanding each object just so I can find out whether it's a useful method or not. Obviously in big projects like that, very well documented code is very useful.

So I'm mostly just asking, is there a standard for commenting in C++, one that people actually expect you to use and stick to when writing programs, like Java, where you are essentially required to use javadoc commenting, which is obviously very useful when using classes/methods that others wrote, though honestly kind of makes the code a little harder to read, but it's a trade-off; mildy harder to read code, way easier to use code as you can use it without actually looking at it.

---

### Post by 11jmb on 2011-10-27
> **akand074 said:**
> 
So I'm mostly just asking, is there a standard for commenting in C++, one that people actually expect you to use and stick to when writing programs, like Java, where you are essentially required to use javadoc commenting, which is obviously very useful when using classes/methods that others wrote, though honestly kind of makes the code a little harder to read, but it's a trade-off; mildy harder to read code, way easier to use code as you can use it without actually looking at it.

Short answer: no.

The javadoc style has become pretty well known, and can be used with Doxygen, so people will generally not be confused if they see javadoc-style comments in C++ code

---

### Post by 11jmb on 2011-10-27
Also, C++ has the benefit of classes being split between a header file and a source file. It is better to keep the comments in the header file, so if people want to read about your class's interface without worrying about code, they can do that. Then if they want to read your code they can look in the source file, which is unobscured by comments

---

### Post by akand074 on 2011-10-27
> **11jmb said:**
> Also, C++ has the benefit of classes being split between a header file and a source file. It is better to keep the comments in the header file, so if people want to read about your class's interface without worrying about code, they can do that. Then if they want to read your code they can look in the source file, which is unobscured by comments

Mind = Blown. This makes so much sense, I've always left my header files without comments and javadoc style commented my source files. Not sure why I didn't think of the other way around. That makes sense, keeps the source clean, yet detailed information about the classes/functions. Functions aren't even defined in header files so the javadoc format actually even makes more sense in header files.

---

### Post by karlson on 2011-10-27
> **akand074 said:**
> That's what I was saying, people have said that your code should be written as clear as possible so that it's self explanatory and then only comment what may not be obvious. But I was talking about any particular standard, not only for understanding the code itself but for being able to understand what a function/class does without even looking at the code. I know C++ isn't like Java, but in Java if I'm using encapsulated classes/methods when I get a list of methods in my IDE I can click one and it gives me the information about the method, the expected parameters and what the return value is so I can understand what the method does and what exactly it wants without having to go to the code. 


So how is class naming different from function naming?

> 
An example for using comments is, lets say, using a math library. If it wasn't commented, although I can look at the function and be clear what it's doing, like taking in a value, multiplying it by something, maybe evaluating an equation that is obvious to read, but it may not always be clear what the equation is and what it's used  for.


You lost me here.  If it wasn't commented you wouldn't know that methods inside have to do with Math(algebra, trigonometry, geometry)?  If you need to know what tan is in mathematical terms you look it up.  Teaching someone trigonometry isn't in the mandate of the software developers unless of course you are writing teaching software.  Or am I missing something here....

> 
A better example is writing an Android application. I often have no clue what most methods are, what they do, and what the parameters/return types even are even with descriptive names as there is just such a gigantic amount of available classes and object types that can be passed, returned, converted, grouped and displayed. The documentation helps you understand what the method is, what it does, what it returns, what exactly are the types it needs because even if I went to the code I'd have no clue what was going on because it would have even more code within it that I don't understand, so I'd basically end up jumping from class to class understanding each object just so I can find out whether it's a useful method or not. Obviously in big projects like that, very well documented code is very useful.


You lost me here again:  If you have a declaration of the function: 
```

public PNGImage convert(JPGImage src);
public BMPImage convert(PNGImage src);

```
It is not clear what it does?  If you are talking about something that you do not have source to then you definitely need documentation of what is the interface for the code you are going to use.

> 
So I'm mostly just asking, is there a standard for commenting in C++, one that people actually expect you to use and stick to when writing programs, like Java, where you are essentially required to use javadoc commenting, which is obviously very useful when using classes/methods that others wrote, though honestly kind of makes the code a little harder to read, but it's a trade-off; mildy harder to read code, way easier to use code as you can use it without actually looking at it.

If you read Effective C++ (or was it More Effective C++) it recommends you use // as comments, but in general it's a matter of habit or convenience on how your present your comments.

---

### Post by gsmanners on 2011-10-27
> **karlson said:**
> ... but in general it's a matter of habit or convenience on how your present your comments.

For old coders (who learned with punch cards and Fortran 77 or something like that) those variable-naming habits can be hard to break. :D

---

### Post by 11jmb on 2011-10-27
Thats certainly a better mindset than "if it was hard for me to code, it should be hard for you to understand" :)

---

### Post by karlson on 2011-10-27
> **gsmanners said:**
> For old coders (who learned with punch cards and Fortran 77 or something like that) those variable-naming habits can be hard to break. :D

Yeah I know....  :D

---

### Post by nvteighen on 2011-10-27
Hm... I think you have to use your brain.

For example, if you're implementing some algorithm that isn't that well-known and you want people understand what's going on, a comment is always a nice thing. Sometimes, the interface itself already tells you what's going on.

Dunno, maybe we're dealing with something that's more related to style than anything else.

---

### Post by karlson on 2011-10-27
> **nvteighen said:**
> Hm... I think you have to use your brain.

For example, if you're implementing some algorithm that isn't that well-known and you want people understand what's going on, a comment is always a nice thing. Sometimes, the interface itself already tells you what's going on.


Comments should be nice to have....  If you are targeting a wide audience that may not be aware of the obscure things you are trying to describe then yes comments are needed.

---

### Post by akand074 on 2011-10-27
> **karlson said:**
> So how is class naming different from function naming?

You lost me here.  If it wasn't commented you wouldn't know that methods inside have to do with Math(algebra, trigonometry, geometry)?  If you need to know what tan is in mathematical terms you look it up.  Teaching someone trigonometry isn't in the mandate of the software developers unless of course you are writing teaching software.  Or am I missing something here....


There is often cases where people need to code something they don't understand how it works, but they know how to use it (because it's well documented). For example, you can write client-server programs in java pretty easily without understanding how the underlying code is allowing different computers to interact over the network. You can easily interact between the two by simply calling a method like "handleMessagesFromClient()" or something. The documentation lets you know how to use it to do stuff when you get messages from the client, but you don't have to have any clue how it does it, just that it works. That's the whole point of encapsulation. Javadoc allows you to not have to go to an external documentation to find out, but lets you right from your editor understand what you need to know, if you need more detail you can go to more in depth documentation. 

> **karlson said:**
> 
You lost me here again:  If you have a declaration of the function: 
```

public PNGImage convert(JPGImage src);
public BMPImage convert(PNGImage src);

```It is not clear what it does?  If you are talking about something that you do not have source to then you definitely need documentation of what is the interface for the code you are going to use.



Sure that's pretty obvious, but that's not Android specific. For example: 

```

public void onCreate(Bundle savedInstanceState)
public void onActivityResult(int requestCode,int resultCode,Intent data)
```What's a Bundle? What's an Intent? Obviously when you first start you have no idea. But then I just highlight over "Intent" and I have a huge explanation of it so that I can learn how it works immediately. Obviously you can't know everything intuitively. Even in normal Java, once using ArrayLists I found need to store more than one value at a time. I saw the method "Collections<T>" but I have no idea how it works, or what it can do. I highlight over it and I get all the information about it, then used it instantly (because of the comments it had on it).

I'm not promoting the need for excessive commenting. I don't think you should comment anything **within** the function unless it's obscure (like you said, you don't explain what algebra,trig geometry is), but outside the function it's really useful to explain what the point of the method is, what parameters it can take in and what results of it but no information of **how** it's actually done. 

That's the best thing about Java. With C++ I always have to go do a Google search which usually puts me in the C++ documentation to explain things, but I haven't done anything using non-built in functions yet, so when it comes to code that someone else actually wrote in C++, without comments I'd have to actually go into all the code, read it and find out what is available to me and what it does by trying to understand the code rather than it being explained and I don't even have to look at the code. 

I should never have to look at the code for anything unless I'm actually overriding/deriving classes from them (which is a different story). Otherwise it should be available to use without knowing how it works. Again, **encapsulation** (information hiding).

---

### Post by 11jmb on 2011-10-27
> **akand074 said:**
> I just highlight over "Intent" and I have a huge explanation of it so that I can learn how it works immediately. 

This made me think of an interesting question. Does anybody know of a text editor or IDE that has a feature like this for standard C/C++ libraries or doxegen-ated C++? I have not heard of anything, because C++ is not a well-organized language like Java when it comes to standard libraries and documentation.

---

### Post by GeneralZod on 2011-10-27
> **11jmb said:**
> This made me think of an interesting question. Does anybody know of a text editor or IDE that has a feature like this for standard C/C++ libraries or doxegen-ated C++? I have not heard of anything, because C++ is not a well-organized language like Java when it comes to standard libraries and documentation.

kdevelop (kind of) does this, except that it shows the contents of the comments preceding the method/ function in a tooltip, verbatim (e.g. semantic markers such as "@brief" are not removed and their meanings are ignored).

---

### Post by 11jmb on 2011-10-27
Does it do this with standard libraries as well? All of the C++ programming I have done has just been with text editors and command line, and my only extensive IDE experience is with Java.

---

### Post by GeneralZod on 2011-10-27
> **11jmb said:**
> Does it do this with standard libraries as well? All of the C++ programming I have done has just been with text editors and command line, and my only extensive IDE experience is with Java.

A big chunk of the GNU C++ standard libraries seem to have Doxygen-style comments, so yes :)

---

### Post by 11jmb on 2011-10-27
> **GeneralZod said:**
> A big chunk of the GNU C++ standard libraries seem to have Doxygen-style comments, so yes :)

Thats pretty cool, thanks for the info. Perhaps a plugin that parses those comments could be written. Unfortunately, I do not see myself moving all of my c++ projects to an ide anytime soon

---

### Post by karlson on 2011-10-28
> **akand074 said:**
> There is often cases where people need to code something they don't understand how it works, but they know how to use it (because it's well documented). For example, you can write client-server programs in java pretty easily without understanding how the underlying code is allowing different computers to interact over the network. You can easily interact between the two by simply calling a method like "handleMessagesFromClient()" or something. The documentation lets you know how to use it to do stuff when you get messages from the client, but you don't have to have any clue how it does it, just that it works. That's the whole point of encapsulation. Javadoc allows you to not have to go to an external documentation to find out, but lets you right from your editor understand what you need to know, if you need more detail you can go to more in depth documentation.


If your method is part of the class serverSocketCommHandler I don't know if I need to read the docs to understand what the function is supposed to do.  If you choose to add comments on top of this more power to you, but it should not be a requirement for someone to understand the code.

> 
Sure that's pretty obvious, but that's not Android specific. For example: 

```

public void onCreate(Bundle savedInstanceState)
public void onActivityResult(int requestCode,int resultCode,Intent data)
```
What's a Bundle? What's an Intent?


Context would be required but judging by what you have provided Bundle is a generic container, which in this case is used to store an application state.  As far as Intent goes I might break it up and name it better but I can't put it in the context...

> 
Obviously when you first start you have no idea. But then I just highlight over "Intent" and I have a huge explanation of it so that I can learn how it works immediately. Obviously you can't know everything intuitively.

The general idea is you should be able to...

> 
Even in normal Java, once using ArrayLists I found need to store more than one value at a time. I saw the method "Collections<T>" but I have no idea how it works, or what it can do. I highlight over it and I get all the information about it, then used it instantly (because of the comments it had on it).


Collections<T> is a class so that would be a type to a method parameter.

> 
I'm not promoting the need for excessive commenting. I don't think you should comment anything **within** the function unless it's obscure (like you said, you don't explain what algebra,trig geometry is), but outside the function it's really useful to explain what the point of the method is, what parameters it can take in and what results of it but no information of **how** it's actually done.


You mean parameter types? or parameter values?  The parameter types are listed in your method/function declaration or in Java in your method definition.  As far as the values are concerned it should be able to handle any.

> 
That's the best thing about Java. With C++ I always have to go do a Google search which usually puts me in the C++ documentation to explain things, but I haven't done anything using non-built in functions yet, so when it comes to code that someone else actually wrote in C++, without comments I'd have to actually go into all the code, read it and find out what is available to me and what it does by trying to understand the code rather than it being explained and I don't even have to look at the code.


You are referring more to the documentation of the APIs for which in a lot of cases source code may not be available.  That doesn't have to do with comments especially not in the code using it.

> 
I should never have to look at the code for anything unless I'm actually overriding/deriving classes from them (which is a different story). Otherwise it should be available to use without knowing how it works. Again, **encapsulation** (information hiding).

Again this has nothing to do with comments.

---

### Post by MG&amp;TL on 2011-10-28
Personally I remove all comments, and instead have a file that describes what each function, class, etc. does.

---

