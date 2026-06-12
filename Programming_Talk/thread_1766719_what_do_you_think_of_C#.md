---
title: "what do you think of C#"
date: 2011-05-24
forum: Programming Talk
---

### Post by android272 on 2011-05-24
I am attending DeVry and my professor seas that in my future classes I will be learning C#. I have heard that C# is a bad language to start with for it is hard to go from it to learning other languages. 

I was wondering what you guys thought of this. Is it hard to go from C# to other languages. is C# a good language to learn.

---

### Post by maddog39 on 2011-05-24
> **android272 said:**
> I am attending DeVry and my professor seas that in my future classes I will be learning C#. I have heard that C# is a bad language to start with for it is hard to go from it to learning other languages. 

I was wondering what you guys thought of this. Is it hard to go from C# to other languages. is C# a good language to learn.
I'm not entirely sure where you heard that it was a bad language to start off with.  But, I don't think you would be any worse off starting off with C# than if you were to start off learning something like Java. Most people in the open source community generally aren't particularly happy with it because of its ties with microsoft. Something you won't be exposed to with something like C# is memory management which is an enomously useful skill and if you attempt to transition to C for example from a C#/Java mind set I can almost gaurentee you will be quickly frustrated by its many nuances.

---

### Post by ve4cib on 2011-05-24
C# is a pretty decent language.  Very Java-like, which is both good and bad.  Specifically, having memory management taken care of behind-the-scenes is a mixed blessing.  It makes it easier to learn -- since you don't need to worry about cryptic errors like "segmentation fault," and you don't need to mess around with pointers manually -- but it means learning C, C++, or any assembly language may be slightly more headache-inducing.

Personally I think it's far better to start off learning to program in a language like Java, Python, or C#, and then have the pointer and memory management taught later.  Get the basics of conditionals, loops, objects, functions, etc... out of the way before diving into low-level stuff like pointers and memory management.

In terms of specific things I like about C#, the way it handles accessors and mutators is great.

```

public string SomeProperty {
    get {
        // some code that will return a string
    }
    set {
        // some code that accepts a string and stores it somewhere
    }
}

...

myObject.SomeProperty = "Hello There!";
print(myObject.SomeProperty);

```

is way cleaner IMO than the Java equivalent:

```

public void setSomeProperty(String str) {
    // code that stores the string
}
public String getSomeProperty() {
    // code that returns the string
}

...

myObject.setSomeProperty("Hello There!");
print(myObject.getSomeProperty());

```

---

### Post by doas777 on 2011-05-24
well, there are a couple dimensions to your query.

C# is a good language in my opinion, and is agumented by some wonderful development tools (sometimes the tools impact the development experience more than language choice), and if you were writing a business application for windows, it would be the first recommendation. since you are at devry, you probably want sellable skills, so C# is not a  bad place to start. The business world runs on platforms like java and  .net. 

the process of learning is different from development however, so folks are not so much hatin' on learning C# as they are hatin' on learning **with **C#. the same criticisms would be accurate for java and python as well. they are both very high level languages, which hide many of the basic concepts of programming from the developer (as others have mentioned, hardware access). depending on what type of programmer you want to be, that may be a caveat or a boon. 

the real question here is, will you become lazy after you have achieved enough skill to be dangerous, and not delve deeper than your circulum dictates, or will you relentlessly experiment with new languages and techniques? if you will settle, then go the traditional college route and get your trial by fire early, and if not, start with the practicals at Devry and dig deeper to find the theory yourself.

---

### Post by NovaAesa on 2011-05-24
I don't think much of C#. It's a good language if you are going to be developing on Windows, but if you are going to use Linux for development I would recommend Java instead - they are very similar languages.

---

### Post by PaulM1985 on 2011-05-25
Your professor says you are going to be learning it, so does it really matter if it is a bad language to start with?  I doubt you would be able to change your professor's mind and get him to teach you something else, so learn it.

Anyway... it seems like a lot of jobs (in the UK anyway) are tending towards requiring some level of C# experience, or Java.  Since C# is quite like Java you would probably be able to pick Java up.

Things have been said about the difficulty of learning C afterwards and how scary memory management is.  I started with Java and then went on to learn C++.  Its not impossible.

I'd recommend learning C#, then SQL.  That should help you in the job market if you want to do programming for a living.

Paul

---

### Post by YesWeCan on 2011-05-25
I am naturally anti-C# as it is a Microsoft "me too" effort to make a proprietary Java competitor. Makes me wince.

I have also read a small amount about C# and I get the impression, which is what I would expect from MS, that it is not as rigorous. I imagine it is easier to hack in C#, eg:
> In C#, all exceptions are unchecked and there is no analog to the throws clause. One major side effect of this is that unless the creator of the API explicitly documents the exceptions thrown then it is not possible for the users of the API to know what exceptions to catch in their code leading to unrobust applications that can fail unexpectedly. Thus users of C# are reliant on the documentation skill of programmers as their primary error handling mechanism which is a less than optimal situation.
*from: [http://www.25hoursaday.com/CsharpVsJava.html#checked](http://www.25hoursaday.com/CsharpVsJava.html#checked)*

It depends what you are trying to achieve. If you want to become proficient at a Microsoft platform then learn C#. If you want to learn to be a good programmer then I would advise a language that is very rigorous and resists the temptation to become a lazy hacker. For this reason, I would stay away from C.

Java is also cross-platform. This is a great strength unless you are only interested in MS operating systems.

---

### Post by simeon87 on 2011-05-25
> **YesWeCan said:**
> I am naturally anti-C# as it is a Microsoft "me too" effort to make a proprietary Java competitor. Makes me wince.

I have also read a small amount about C# and I get the impression, which is what I would expect from MS, that it is not as rigorous. I imagine it is easier to hack in C#, eg:

*from: [http://www.25hoursaday.com/CsharpVsJava.html#checked](http://www.25hoursaday.com/CsharpVsJava.html#checked)*

It depends what you are trying to achieve. If you want to become proficient at a Microsoft platform then learn C#. If you want to learn to be a good programmer then I would advise a language that is very rigorous and resists the temptation to become a lazy hacker. For this reason, I would stay away from C.

Java is also cross-platform. This is a great strength unless you are only interested in MS operating systems.

Your opinion seems more influenced by anti-Microsoft sentiments than facts.

Java and C# are so similar that there's nothing wrong with learning programming in C# as opposed to Java. In fact, C# improves upon features that Java has, such as the properties mentioned earlier and various other features, such as constructs from functional programming. I would argue that C# is more rigorous in the features that it offers, which should come as no surprise because Java was developed first and lessons have been learned from that.

Disclaimer: I have programmed more with Java than with C#.

---

### Post by Petrolea on 2011-05-25
I had the same problem as you. In school we were learning C++ but I wanted to learn every other language than C++. I got all the basic knowledge of data types, loops, functions... and later on I quickly picked up every other language.

So if you are forced to learn C# don't worry too much about it being useless in some ways. You will learn OO programming which will make it easier to learn other languages like Java, C++ or Smalltalk (especially Java). 

Those who say C# is much more useful on Windows are right. I don't think many apps in Linux world are written in it. But learning a new language is never a bad thing.

---

### Post by ve4cib on 2011-05-25
> **YesWeCan said:**
> I am naturally anti-C# as it is a Microsoft "me too" effort to make a proprietary Java competitor. Makes me wince.

Conveniently there's Mono/GTK# which lets you write completely free, open-source, Linux-compatible programs in C#.  Some examples include Banshee, Gnome-Do, and Docky.  C# is no longer a strictly Microsoft domain.

> I have also read a small amount about C# and I get the impression, which is what I would expect from MS, that it is not as rigorous. I imagine it is easier to hack in C#, eg:

...

*from: [http://www.25hoursaday.com/CsharpVsJava.html#checked](http://www.25hoursaday.com/CsharpVsJava.html#checked)*

That doesn't make it any easier to hack, really.  All it means is that any function can throw an exception.  Exceptions are still caught just like in Java.  Worst calse you can throw in a generic try/catch block inside main you'll catch everything safely.

However, in my experience using C# there are relatively few undocumented exception-throwing functions, and for the few that are there any decent programmer should test their software for bugs and random crashes by throwing both good and bad input at it.

Also, sometimes it's nice to be able to ignore exceptions that *might* be thrown by a function call.  If you've already sanitized your input, and know that a division by zero exception cannot occur then why bother with a try/catch(DivideByZeroException), just because the function *sometimes* throws one?

> Java is also cross-platform. This is a great strength unless you are only interested in MS operating systems.

As mentioned above, with Mono C# is also cross-platform.

---

### Post by nvteighen on 2011-05-25
Please. The problem with C# is just that it's unnecessary from a technological point of view; it was created to do business after the MS J++ fiasco. But the language itself does no harm.

Now, let's state things clearly:
1) The C# language is cross-platform.
2) There is the MS .NET implementation, which is Windows-only and is the "original" one (like Sun/Oracle's is the original Java implementation).
3) There is the Mono implementation, which is available for many platforms and is Free Software.

---

### Post by stchman on 2011-05-25
If you plan on doing a lot of Microsoft software development then C# might the way to go.

I prefer Java as it's platform independent.

---

### Post by android272 on 2011-05-26
ok so C# is not a bad language to learn, it is like to Java so learning both wont be too hard. I can use it in Linux, I was wondering about that. I would like to develop for Linux and maybe do a cross platform to Micro$oft or Macinto$$$h. I as well do not like Micro$oft.

I have done some codeing with python but not much.

---

### Post by ve4cib on 2011-05-26
C# and Java are very similar in terms of design and syntax.  Once you know one the other is pretty easy to pick up.

One distinct advantage Java does have is that it includes a single universal, cross-platform GUI library.  So you can write a program with a GUI using Java's standard library, and it will work exactly the same on Windows as it does on Linux, or Mac.

The .NET framework on the other hand does not include the same universal GUI kit.  .NET was designed for use with Windows, and therefore relied on the Windows Forms library.  Once the Mono project got rolling, making a .NET framework for other platforms, they couldn't use Windows Forms since that's a proprietary Microsoft library.

So Mono programs that need to be cross-platform tend to use an open-source GUI library like GTK.  This works because you can recompile GTK for any platform.  But it's not a standard Windows library, and will generally need to be distributed along with your program if you intend Windows users to be able to use your software.

It's a bit of a nuisance, but as long as you remember to either include GTK, or make sure your users know they need to install that on their own separately, it's not the end of the world.

---

### Post by PaulM1985 on 2011-05-26
> **ve4cib said:**
> The .NET framework on the other hand does not include the same universal GUI kit.  .NET was designed for use with Windows, and therefore relied on the Windows Forms library.  Once the Mono project got rolling, making a .NET framework for other platforms, they couldn't use Windows Forms since that's a proprietary Microsoft library.

Really? I am pretty sure I have run Windows Forms apps on Ubuntu.  Almost certain.
And developed using it. You just need to add it as a reference to your project.

---

### Post by ve4cib on 2011-05-26
> **PaulM1985 said:**
> Really? I am pretty sure I have run Windows Forms apps on Ubuntu.  Almost certain.
And developed using it. You just need to add it as a reference to your project.

Really?  Hmm.  Well, I was clearly mistaken then.  I'll have to look into this.  Thanks for pointing out my error!

---

### Post by Reiger on 2011-05-26
Yes, Mono does support some GUI library that you can use on .NET, too. But no, you don't want to. It uses fixed layouts, and makes tk look modern by comparison.

---

### Post by android272 on 2011-05-29
I would like to make open source software, so if I write it in java window, mac, and linux will for the most part be able to run it.  is there any modifications that need to be done to the code to make it work in windows or mac if I code it in linux, GUI's and all. 

> **Reiger said:**
> Yes, Mono does support some GUI library that you  can use on .NET, too. But no, you don't want to. It uses fixed layouts,  and makes tk look modern by comparison.


what do you mean modern, could some one give an example of what he is talking about.

---

