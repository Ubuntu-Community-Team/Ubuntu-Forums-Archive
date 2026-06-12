---
title: "Requesting Impressions of Boo and Ruby"
date: 2006-04-23
forum: Programming Talk
---

### Post by MojoX on 2006-04-23
This is another of those "overwhelmed newbie having hard time deciding on language" posts.  :)

A little about what I'm doing: First, I am learning for hobby. Second, I really want to learn to create GNOME apps.  So GUI support/libraries/bindings matter a lot. I've read through the forums here and have done quite a bit of Googling and have come down to deciding between Ruby and Boo.  I've read through some of Why's Poingant Guide and have gone through the Boo tutorials at codehaus.  Both seem like easy languages to learn.  I've only found one detailed [Ruby/Boo comparison]("http://www.cse.iitb.ac.in/~kart/writings/Ruby%20vs.%20Boo%20(short).html"), even still, I'd like to know what the minds here think.

I am sure that in my limited technical understanding, there are somethings I am overlooking.  So anyone reading this familiar with these two languages: What are your impressions of them? How are they similar?  How are they different?  What are their relative strengths and weaknesses?  I've seen Ruby desribed as a "pure" OO language.  How does Boo compare to this purity standard?

Thanks in advance for any replies! :-D

---

### Post by colo on 2006-04-23
I don't know "Boo" (except for the giant miniature space hamster in the Baldur's Gate Series of video games ;)), but after spending significant parts of my life with programming in quite a few languages the last 9 years or so, let me tell you: Ruby is wonderful. I've also plaid around with Ruby-GTK2 a bit, and of course, dealing with GUI-toolkits is ugly as ever - but you can leave the creepy stuff to something like glade, and happily divulge Ruby's crisp, clear and clean syntax in your programs. Have a look at The Pragmatic Programmer's "Prgramming Ruby" (the "pickaxe"), it's a great way to enter the beautiful world Ruby provides to weary and fresh programmers alike. ;)

---

### Post by LordHunter317 on 2006-04-23
That comparsion is biased and just plain wrong on several points.  Dynamic typing isn't a strict advantage, and Boo supports the same amount of 'dynamic' typing that Ruby does (i.e., late-bound duck-typing) at least to the degree that CLS-compliance allows.  FWIW, CLS is the standard for CLI language to ensure code written in one language can be called and introspected from another.  IOW, it's the standard that ensures your boo code can be called from C#, VB.NET, etc. transparently.  

In practice, the minimum typing required by Boo even in 'duck-typing' mode won't be a hinderence and you may find it helps your desigsn.

Aside: it's disgusting how many Ruby and pythonistas still get the typing debates totally wrong and don't understand what they're talking about.  

I'm not sure having method invocations not be explictly noted (i.e., you always must include '()' to indicate a method call) is a positive.  It can be, but I'm not sure it always is.  Having properties explcitly set off in .NET is a good thing, in my mind.

Be able to include symbols isn't a huge deal.  The only place I would care, predicates, I can use 'Is' instead of '?', and that doesn't bother me.  I'm not convinced that being able to further overload '!' or '=' even if it's like '!Sync'.  '!' already has too many orthogonal meanings and don't get me started on '='.

Calling ruby's naming conventions for scope disambiguation a good thing is an absolute ******* joke.  Sigils are terrible, terrible things.  It makes refactoring more difficult and makes the code more difficult to read.

Classes are first-class objects in .NET.  You can't alias them, but you can't do that to variables or methods, so that's not a limitation.  You can certainly generate classes at runtime.  What is true is that classes are immutable in .NET, once generated, you can't do anything that changes their type.  But that doesn't make them not first-class.  

Being able to change type signatures at runtime isn't a good thing either, *per se*.  In my experience, it's always a bad thing.  It indicates poor planning and forethought and abuse of encapsulation.

method_missing() is just Ruby showing it's lack of a Macro facility: Nemerle at least supports doing everything you'd want to do via method_missing() via macros and in a far superier, cleaner way.  It's infinitely less fragile.

Boo supports running dynamically generated code at runtime just like all other .NET languages, though you have to write it in IL.  This is a PITA, but it is possible.

Executing method definitions isn't a positive, it's a distinct negative.

.NET doesn't have a notion of a classpath, but that's a good thing.  And he's confusing the need to declare the code you're going to call to the compiler (i.e., namespace directives) to locating the code at runtime.  This sort of error, plus the other fundamental ones above, indicate whoever wrote this is confused about some fundamental things.

Having only a CLR implementation isn't a negative, and .NET supports translation to native code for *any* CLI language.

The issue with this comparions is the fundamental lack of knowledge the author has (he admits as such) and some fundamental technical errors he makes.

---

### Post by kartik_vad on 2006-04-24
>  Dynamic typing isn't a strict advantage

Well, I think it is. As I wrote in the introduction, my comparison is based on my preferences, and if you disagree with them, I'm not sure the article is worth reading for you.


> Boo supports the same amount of 'dynamic' typing that Ruby does (i.e., late-bound duck-typing) at least to the degree that CLS-compliance allows.

From the Boo site, you need to declare types in the following situations: "parameter types, recursive and mutually recursive method/property/field definitions, return for abstract and interface methods, for in untyped containers, properties with a only set defined". With Ruby, you never declare types -  seems a noticeable difference to me.

Yes, Boo is constrained by CLS compliance, but running on the CLR is not a requirement for me (if it were, Ruby wouldn't be in the picture in the first place), so I would consider mandatory declarations (in the above situations) a drawback.


> In practice, the minimum typing required by Boo even in 'duck-typing' mode won't be a hinderence

I've written about that [here]("http://kartik-log.blogspot.com/2005/09/what-dynamic-typing-really-buys-you.html").


> I'm not sure having method invocations not be explictly noted (i.e., you always must include '()' to indicate a method call) is a positive.

I've written about that [here]("http://kartik-log.blogspot.com/2006/01/function-invocations.html").

> Be able to include symbols isn't a huge deal.
It enables a better model for [properties ]("http://kartik-log.blogspot.com/2006/01/properties-built-on-methods-or-vice.html")and [operator overloading]("http://kartik-log.blogspot.com/2006/01/operator-overloading-in-ruby.html") and, as I wrote, enables the convention of having methods that change the state to have a ! in their name to distinguish them from methods that don't change object state.


>   Sigils ... makes refactoring more difficult and makes the code more difficult to read.

Agreed. But as I said, it's crystal clear - you know instantly what kind a given variable is, without any need for declarations or having to resolve name clashes using 'self.'.
Maybe in this case I'm mistaken and, as I gain more experience, I'll come to see that Ruby's scoping system is bad. Possible, but for now, I see no reason to subscribe to that view.

> Classes are first-class objects in .NET.  You can't alias them, but you can't do that to variables or methods, so that's not a limitation.  You can certainly generate classes at runtime.  What is true is that classes are immutable in .NET, once generated, you can't do anything that changes their type.  But that doesn't make them not first-class.  

Well, let's not argue about terminology, but Ruby classes are more flexible.


> Being able to change type signatures at runtime isn't a good thing either, *per se*.  In my experience, it's always a bad thing.  It indicates poor planning and forethought and abuse of encapsulation.

I'm not sure it has no valid use. As long as it may, I'd like the language to support it, rather than ban it because it's misused most of the time.


> method_missing() is just Ruby showing it's lack of a Macro facility

But sometimes method_missing may be exactly what you want.


> Executing method definitions isn't a positive, it's a distinct negative.

Once again, I'm not sure it has no valid use. As long as it may, I'd like the language to support it, rather than ban it because it's misused most of the time.


> he's confusing the need to declare the code you're going to call to the compiler (i.e., namespace directives) to locating the code at runtime. 

The statement about classpath was inaccurate. My point was: if the name of the assembly can be determined from the namespace, the compiler doesn't have to be told the former; we could avoid all the "-r:" portions of the command line. We might still need to tell the compiler which directory to look in, but we don't have to give it references to each dll file.

I believe IKVM does something similar.

> Having only a CLR implementation isn't a negative, and .NET supports translation to native code for *any* CLI language.

No doubt a CLR implementation does have its advantages, but the CLR is a sub-optimal target for dynamically typed languages.

> The issue with this comparions is the fundamental lack of knowledge the author has.

You misunderstand many of the points I make (a couple of some of them certainly deserve elaboration/clarification from my side). And I think that to some extent you lack understanding as well.


> (he admits as such)
Nope. All I said is that I don't have much experience with Ruby or Boo; I think I understand the concepts and the issues involved reasonably well.

---

### Post by LordHunter317 on 2006-04-24
[QUOTE=kartik_vad]Well, I think it is.[/quote]It isn't.  Static typing isn't a strict advantage either.  There are times when both are appropriate.

.NET is a perfect example of this.  VB.NET's ability to switch to late-binding is *incredibly* useful when dealing with COM Interop (especially because the interop DLL generator doesn't work correctly *sigh*).

However, the ability, *in the same language* to define a static interface that everyone uses is also useful, in case I'm generating my own API I expect others to implement. 

And I've worked on projects where I have to do both.  NB: I'm not advocating VB.NET per se, just noting that this feature is extraordinarily useful on occasion.

Anyone who says, "Static-binding is correct all the time" or "Dynamic-binding is correct all the time" is wrong.  Neither is correct all the time.

> As I wrote in the introduction, my comparison is based on my preferences, and if you disagree with them, I'm not sure the article is worth reading for you.Which makes the comparionsion *useless* for anyone.  What's the value in preaching to your own crowd?

> From the Boo site, you need to declare types in the following situations: "parameter types, recursive and mutually recursive method/property/field definitions, return for abstract and interface methods, for in untyped containers, properties with a only set defined". With Ruby, you never declare types -  seems a noticeable difference to me.My point is, from doing Nemerle development which has almost the same limitations, it's rarely a painful thing.  

I'll grant you Ruby removes the restrictions, you're correct.  In practice, I'm not sure it matters most of the time.

> Yes, Boo is constrained by CLS compliance, but running on the CLR is not a requirement for me (if it were, Ruby wouldn't be in the picture in the first place),Ruby.NET does exist, but I don't know how compatible it is.

> I've written about that [here]("http://kartik-log.blogspot.com/2005/09/what-dynamic-typing-really-buys-you.html").And your example is wrong.  You would have just subclassed 'File' and gotten on with your life.  Not having type declarations isn't your saviour there.

> I've written about that [here]("http://kartik-log.blogspot.com/2006/01/function-invocations.html").It's still not clear it's a positive.  Properties in .NET aren't presented as methods, neither are overloaded operators.  The latter clearly should be set apart, the former is somewhat questionable and ultimately a matter of preference I suppose.  My argument is that properties can be lvalues, functions are not.

> It enables a better model for [properties ]("http://kartik-log.blogspot.com/2006/01/properties-built-on-methods-or-vice.html")and [operator overloading]("http://kartik-log.blogspot.com/2006/01/operator-overloading-in-ruby.html")But it doesn't.  Your operator overloads written like that look nothing like a real operator.  '.+' isn't the same as '+' to a whole lot of people.  Which is why Ruby has to *special-case* them, so you can remove the '.'  Meaning, they're not written like functions or properties at all.  They're special-cased, and they deserved to be.  I thought we'd all learned from C that declartion mimics usage is a bad thing.  

I will agree that the decleration of overloaded operators is ugly in C++ and Python, but the usage is still consistent with other operators.  Ruby doesn't strictly enforce that, nor should it try.  *Operator usage doesn't appear as a function call to the coder.*  Even if that's what it really is, it doesn't appear that way, so it's senseless to try to unify the two.  What matters is it looks like '3 + 2', even if it's just a method of the integer class.

> and, as I wrote, enables the convention of having methods that change the state to have a ! in their name to distinguish them from methods that don't change object state.I prefer C++'s method of const-correctness myself, which has the advantage of being compiler-enforced and not just mere convention.  That is an advantage, but a questionable one.

> Agreed. But as I said, it's crystal clear - you know instantly what kind a given variable is,But I don't want to know, outside of when I declare them.  This is one of the things against dynamically-bound languages that don't enforce variable declaration: I have to now pull some sort of voodoo to resolve scope.  Whether it be naming sigils, 'global' or something else, I have to do something, and I have to do it all the time.  Some languages are worse than others, though (e.g., PHP, Perl).

This is why I strictly prefer variable declaration.  You solve the problem by saying, "You must declare everything in its scope".  Everything flows from that.  Really, that is the most sensical route, and it's not like you don't know what scope a variable should be in or else you wouldn't be using it in the first place.  

>  without any need for declarations or having to resolve name clashes using 'self.'.See, but that's not the right answer either.  You noted in your blog post 3 choices, and I'm saying choice number 1 is not only the correct one, it's really the only correct one :p

> Maybe in this case I'm mistaken and, as I gain more experience, I'll come to see that Ruby's scoping system is bad. Possible, but for now, I see no reason to subscribe to that view.Consider this: when you refactor, you've changed the name.  It's no longer '@foo', but '@@foo', or whatever the change requires.  That's a different string to mentally identify as being the same thing previously.  That, to me, is really annoying.

> Well, let's not argue about terminology, but Ruby classes are more flexible.I'll grant you that, but I'm not sure they are in a *good* way, which is my point.  

> I'm not sure it has no valid use. As long as it may, I'd like the language to support it, rather than ban it because it's misused most of the time.I've never seen one.  The entire idea of adding code to an existing class at runtime is silly: if you're adding it at runtime, why not include it at compile time? 

I'll grant the one useful exception: when you're prototyping something in an interpreter or playing around: then it can be useful to be able to extend a class definition on the fly.  But I'm not sure having the interperter be the special-case isn't the correct course of action here.  In fact, I'm pretty convinced it is, as it's the only case I've ever seen where the behavior makes sense.

> But sometimes method_missing may be exactly what you want.When?  I can do everything method_missing allows via macros, and it's far cleaner and less code.  If I want multiple proxies or selective lazy binding, for example, it means a messy method_missing.  Macros kill all of that mess for the same effect.

Again, the only useful time I see for this is in the debugger or interpreter, both of which could special-case such behaviors, and already do.

If I want it in my code *by design*, macros are a superior system for achieveing the same sorts of goals.

> Once again, I'm not sure it has no valid use. As long as it may, I'd like the language to support it, rather than ban it because it's misused most of the time.Code some PHP and you'll wish included scripts weren't executed. :p

Seriously, I don't see what it gets you.  Even if you were generating the method at runtime, you can just run whatever side-effect when you generate the method.  If necessary, create a wrapper method (i.e., use encapsulation) that does both things so you always get both effects.

My issue here is that the only uses I can think of are dubious, and can already be achieved through other mechanisms.  Maybe I'm not thinking it far enough through, but I'm not a fan of including features that solve problems that are already solved by other features.  Executing method definitions seems to cleary be in that camp.

> My point was: if the name of the assembly can be determined from the namespace,It can't be in .NET.  The namespace name has nothing to do with the assembly name.  This isn't Java, for better or for worse.  A huge portion of the base namespaces (all begining with 'System') live in mscorlib.dll, for example.  Ironcially, only a few of the base namespaces are totally contained in there.  

Many of the namespaces are named after their DLL counterparts, but not all of them.  There's no requirement, just convention, and I've seen it broken all over the place.

One could argue why doesn't the compiler search the GAC at compile time (and various reasons have been given) but that's another can of worms. 

[edit]Ahh, I see what you were saying now in the comparsion, and you are correct.  It's a limitation by-design.  You should rewrite the paragraph to be more clear, by explictly saying, "Must import namespaces in code but still tell the compiler what DLLs implement those namespaces".  You don't, and it's confusing as written.

My apologies for misunderstanding you.

> but the CLR is a sub-optimal target for dynamically typed languages.Only if you're interested in CLS compliance.  I haven't seen any issues that don't go away if you don't care about your language being inaccessible from all other CLR languages, besides ones releated to dynamic generation of generics, which are broken even for static languages.  I could however, be mistaken.  I'm hardly an expert on the inner works of the CLR.

---

### Post by kartik_vad on 2006-04-24
When you write a comparison, you can't draw any conclusions without having them reflect your personal opinions.  I wouldn't be interested in reading a comparison that just said, "Ruby has X, Boo has Y, Ruby has X2..."; I want to know which worked better for the author. 

So, yes, this is a subjective comparison - one I wrote because I had to choose between Ruby and Boo, not as a theoretical exercise.

In my example OutputDuplicator shouldn't be a subclass of File because it supports only write(); other File operations like read, seek, etc make no sense for this class. I think dynamic typing does enable a better solution.

Declaring types where Boo (and Nemerle) requires them may not be too painful in and of itself, but it restricts reuse. In the above case, if all the methods that took a file declared the argument type to say so, I wouldn't have been able to replace the file with an OutputDuplicator.


I still can't see much use for mandatory type declarations. It helps when writing a library or API only if the users are statically typed. Type declarations have their uses, and I'm not against language support for them; I'm complaining about them being mandatory (in certain situations).


> Properties in .NET aren't presented as methods... properties can be lvalues, functions are not.
A property is conceptually just a pair of methods, so I prefer not to have an artificial syntactic distinction. Yes, functions are not lvalues, but a use of a property as a lvalue is conceptually a function call:
dog.age= 4
is treated (by Ruby) as:
dog.age=(4)
This sounds pretty logical to me. The distance from the semantic model to Ruby's system is less than that to Boo's. Put differently, the syntax is closer to the semantics. I think of a property as a pair of methods, and Ruby reflects that better.

> Operator usage doesn't appear as a function call to the coder. Even if that's what it really is, it doesn't appear that way, so it's senseless to try to unify the two.

I beg to differ. Since (overloaded) operators are conceptually methods, I'd like to be able to treat them similarly and not worry about minor syntactic issues like the presence of a dot. Yes, it's important to understand what's going on, but once you do, I think this is the better model.

I don't like C++'s const-correctness because of the code bloat.

Yes, I understand the problem sigils pose to refactoring (besides making code look ugly), and I now realize that using sigils to indicate scope is a bad idea. Thanks a lot. But I think [ explicit self references]("http://kartik-log.blogspot.com/2006/01/local-variable-creation-and-scoping.html") is the best option, and that sigils are a better idea than mandatory declarations for instance variables. (I think it's a bad idea to specify centrally in one place what instance variables exist. Besides, we want to be able to dynamically add and remove instance variables, and it's not clear how static declarations are compatible with this.)

>> Ruby classes are more flexible.
> I'm not sure they are in a good way.

An example for use of dynamically adding instance variables: in a (Python) project, I had a class that represents a row in a database. Rather than hardcoding a set of instance variables, I looked in the database and then created the appropriate variables dynamically. That way, when the database schema evolved, my code didn't break.

Once you dynamically add and remove instance variables, you might want to dynamically add and remove their accessor methods, too (if you were using Ruby).

If objects can change their class (think a Manager being promoted to a VP) [Python supports this], you need to (dynamically) add instance variables used by the new class (and possibly remove unneeded ones).

Another example use for dynamically generated methods is attr_accessor.

A use of an executed import statement could be:
if platform == "win32"
    import somelib_win32
else
   import somelib_unix

This selects between two (interface-compatible) implementations of a library. I've seen python code that catches exceptions caused by import failure and deals with it.

There are more examples, many I don't know about. So I'm very reluctant to dismiss a feature as useless or redundant. 

method_missing may be the right solution for remote proxies. A macro may not be any better here. 


>> if the name of the assembly can be determined from the namespace,
> It can't be in .NET.
I know that. But why not? Could we have a rule that a namespace System:: Drawing::Forms must be implemented in System_Drawing_Forms.dll or System_Drawing.dll or System.dll? Then the compiler doesn't need to the told the dll file name. Maybe the directory (for non-System dlls), but not the name.


> You should rewrite the paragraph to be more clear, by explictly saying, "Must import namespaces in code but still tell the compiler what DLLs implement those namespaces".

Done :)  Sorry for the confusion.


>> the CLR is a sub-optimal target for dynamically typed languages.
> Only if you're interested in CLS compliance.

AFAIK, the CLR doesn't support dynamic typed invocations (short of using reflection), adding and removing fields or methods or changing the class of an object. Its instruction set seems targeted towards statically typed languages.

---

### Post by LordHunter317 on 2006-04-24
> **kartik_vad]When you write a comparison, you can't draw any conclusions without having them reflect your personal opinions. [/quote]Yes, you can.  We call it objectivity.  

> I wouldn't be interested in reading a comparison that just said, "Ruby has X, Boo has Y, Ruby has X2..." said:**
> Wonderful, but your comparsion doesn't actually do that, you have to give use cases and example scenarios.  If that were your intent (which is perfectly acceptable) you didn't provide nearly enough detail.  

[quote]In my example OutputDuplicator shouldn't be a subclass of File because it supports only write(); other File operations like read, seek, etc make no sense for this class. I think dynamic typing does enable a better solution.Well, Pythons's file API isn't the best example, but this wouldn't be a problem in a better thought out API, e.g., C++ iostreams.  There the operations are properly encapsulated so you can have a write-only extension.

But the point remains: it's not dynamic-binding that's saving your bottom, it's polymorphism.  Dynamic-binding is only helpful here because the class API isn't properly abstracted, which is obviously useful.

But what you wanted to do can be achieved by static-binding, it just requires more forethought on behalf of the API designers for whatever APIs you're using and extending.  That's not necessarily a bad thing, it's not necessarily a good one either. 

I'd argue in the case you presented, dynamic-binding is being used as a band-aid over a more fundamental problem: a not well-thought out class API.  Dynamic-binding may let you do want you want with less fuss, but the problems of having to deal with poorly designed APIs will bite you eventually no matter what the type system is.  .NET's class library is a perfect example of this.

[quote]Declaring types where Boo (and Nemerle) requires them may not be too painful in and of itself, but it restricts reuse.Not if abstraction is properly used.  That's the *real* problem here: the methods aren't being properly defined as to what their parmeters really need to support.

This is a problem in all languages, regardless of binding method.  Duck-typing just lets you be more forgiving of the mistakes.

> I still can't see much use for mandatory type declarations. It helps when writing a library or API only if the users are statically typed.Not true, it helps going the other way: it forces the implementors to stick to their declared behaviors.  This is useful when working in teams: you can scaffold skeleton classes before you fill in the functionality, and retain API compatibility.  This means less code to change when the implementation is actually added.

> I'm complaining about them being mandatory (in certain situations).I understand that.  And that's fine, I suppose.  What I'm saying is in practice, for me anyway, it turns out to matter little, as long as you design your classes correctly in the first place.

> A property is conceptually just a pair of methods, so I prefer not to have an artificial syntactic distinction.Well, the distinction isn't just in the language syntax, but in the IL, the reflection mechanisms, etc.  Properties aren't really methods, even if they are implemented that way in .NET.  One can argue that this is a bad thing, as you are, but my point is different.  My point is that once you've made this distinction (as .NET has), then it's better to keep the distinction clear cut.

Ruby doesn't make the distinction.  It's certainly a different way of doing things, but I'm not sure it's a better way though I am leaning towards it.  I'm not sure it's really worse, either.  

What I do feel is important is for you to expand and note why properties are treated differently.  It's not some arbitrary choice, boo really has some say in the matter.  But it doesn't deserve the terse treatment given in the table.

> Put differently, the syntax is closer to the semantics. I think of a property as a pair of methods, and Ruby reflects that better.Yes, and that's true in nearly all languages but .NET ones, where they're *almost* a pair of methods.  But there's just enough dressing that's not the case.

Frankly, I'm not sure after dealing with .NET properties that I really like the idea.  It makes your IntelliSense and documentation prettier, but at the end of the day I think I'm just fine with a method with two overloads (i.e., foo() C++ style).

> I beg to differ. Since (overloaded) operators are conceptually methods,Overloaded operators are.  Primitive operators (in languages that have them) are not.  That's the problem.  Not all operators are function calls, and they don't appear to the user as function calls *at all*, so the corrrect abstraction is to completely hide the fact they are function calls.

> I'd like to be able to treat them similarly and not worry about minor syntactic issues like the presence of a dot.But '.+' means something totally different to me.  It's a totally different operator. 

> Yes, it's important to understand what's going on, but once you do, I think this is the better model.The whole point of operator overloading is I don't have to care what's going on underneath.  You're arguing against yourself here.  I shouldn't have to care, as the class user.  If I do, it's a poor model.

> I don't like C++'s const-correctness because of the code bloat.It does lead to bloated code, but I don't think that's a reason to discount them.

> Thanks a lot. But I think [ explicit self references]("http://kartik-log.blogspot.com/2006/01/local-variable-creation-and-scoping.html") is the best option, and that sigils are a better idea than mandatory declarations for instance variables. (I think it's a bad idea to specify centrally in one place what instance variables exist. Besides, we want to be able to dynamically add and remove instance variables, and it's not clear how static declarations are compatible with this.)But we don't.  If you said, 'method-scoped variables', I'd agree.  But I almost never, ever want private variables being declared willy-nilly.  They're sharing information between functions, and there has to be a reason for that, and that reason should be clear in the design.

In my mind, if there isn't a reason for a instance variable to exist during the entire lifetime of the class with some meaningful value, it probably shouldn't have class cope.  It should have function scope and be passed around, if necessary.  If it's not, it's usually a sign to me I've designed something wrong.

> Rather than hardcoding a set of instance variables, I looked in the database and then created the appropriate variables dynamically. That way, when the database schema evolved, my code didn't break.This can be and is done in .NET via named-accessors.  Given a DataReader of some sort, I can say reader["foo"] and get the value for the current row in column "foo".  I've given up type saftey explictly, but it can be done in a statically-bound 
language.

The only advantage a dynamically-bound language would have here is the removal of some the explict conversions I have to make:```
string foo = Convert.ToString(reader["foo"]);
``` or similiar.   However, obviously not all of them can be removed.

> If objects can change their class (think a Manager being promoted to a VP) [Python supports this], you need to (dynamically) add instance variables used by the new class (and possibly remove unneeded ones).In most systems, a VP is-not-a Manager in the OOP sense (i.e., I cannot substitute a Manager object in every place a VP can be) so this is breaking OOP principle.  Certainly in most every data object system I've worked in, this was the case.  Even if two items were related in the database, they were distinct, concrete objects in the code, with seperate methods for saving and instantiation. 

So no, I don't see the advantage here.   If I needed to convert, I'd write an constructor that did that for me.  Which is essentially what you're doing with the code generation, just in a different manner.

> This selects between two (interface-compatible) implementations of a library. I've seen python code that catches exceptions caused by import failure and deals with it.I'd much, much rather deal with this case at compile/install/setup time through other means, and have implementation details centralized and abstracted away.

They're enough of a headache to not have to deal with them in every file.

> method_missing may be the right solution for remote proxies. A macro may not be any better here. It clearly is better because it only requires an attribute designation, and I can do it to an arbitrary number of member variables without having to worry about generating the method to handle them all.

> I know that. But why not?I honestly don't know why MS didn't choose that route.

AFAIK, the CLR doesn't support dynamic typed invocations (short of using reflection), adding and removing fields or methods or changing the class of an object. Its instruction set seems targeted towards statically typed languages.[/QUOTE]

---

### Post by yaaarrrgg on 2006-04-24
Also... the technical details of the language aren't the only thing to consider.   The community, documentation, libraries, and tools associated with the language are (perhaps equally) important too.  So, I would avoid Boo until it is more mature, and has a larger developer base.

---

### Post by MojoX on 2006-04-25
[QUOTE=yaaarrrgg]Also... the technical details of the language aren't the only thing to consider.   The community, documentation, libraries, and tools associated with the language are (perhaps equally) important too.  So, I would avoid Boo until it is more mature, and has a larger developer base.[/QUOTE]
I've been thinking about these issues a lot and was hoping someone would mention them.  Does Boo get any advantage in being a Mono language, like all the bindings and libraries available on the Mono platform?  If so, that should be a plus, right?  It would be great to work with MonoDevelop, especially when Stetic supports Boo.  Still, the language documentation is poor and in my very brief experiences with the language, that has made learning difficult and, at times, frustrating.

The Ruby community is definitely larger, but it doesn't appear to have the tool, documentation and library base that Python has.  Still, in my time researching the language and reading Why's guide, I've found myself learning it fairly quickly.  I don't have much programming experience (Turbo Pascal, VB, Java Script), but the little Ruby I have experimented with has impressed me much.

The reason why I am deciding between these two languages is because: 1) I am very excited about the Mono project and just think it would be neat to program using it.  2) I really love Ruby's syntax and feel it may help me discipline my programming habits and help keep the hobby fun.  I tried to learn Python, but wasn't as intellectually excited about using the language as I am about using Ruby or Boo.  Ideally, I'd like to use a CLI implementation of Ruby, but obviously that isn't an option.  I have tried to find for information about the Queensland Ruby.NET project, but since it is MS funded, I'm pretty sure it will be encumbered with a crappy license and MS tie-ins.  I may be misguided in my fascination with the CLI but I really feel it has a great future in free software development.

Another question: How important/useful are IDEs for folks using languages like Ruby or Python?

Before I posted, I figured Ruby would be best for someone new, like me.  I that is the language I'll ultimately choose.

Thanks for the replies! :-D

---

### Post by kartik_vad on 2006-04-25
> Dynamic-binding is only helpful here because the class API isn't properly abstracted

That's true only from a static typing perspective. In a dynamically typed language, a more complex hierarchy is uncalled for. I've written about this in greater detail [here]("http://kartik-log.blogspot.com/2005/09/what-dynamic-typing-really-buys-you.html").


> Duck-typing just lets you be more forgiving of the mistakes.

They're not mistakes in a dynamically typed language.


>> I still can't see much use for mandatory type declarations. It helps when writing a library or API only if the users are statically typed.
> Not true, it helps going the other way: it forces the implementors to stick to their declared behaviors.

I think a type is only a small part of the behavior. You lose the freedom to substitute an object with another that is unrelated by inheritance but defines the required methods. I don't consider it a good tradeoff.


> important ... for you to expand and note why properties are treated differently... it doesn't deserve the terse treatment given in the table.

The terse statement in the table links to posts discussing it in detail.

I find a model that says, "the operator + maps to the method +" to be more straightforward than one that says, "the operator + maps to the method __add__". So + and .+ is just the operator/method duality - when you look at it as an operator, it's +, and when you look at it as a method, it's .+ . That's what I said you need to understand, not the implementation of individual overloaded operators.

Regarding primitive operators, there are none in Ruby (AFAIK).


>> created the appropriate variables dynamically.
> This can be and is done in .NET via named-accessors.

Yes, I didn't mean it can't be done otherwise but that it's more straightforward this way.


> a VP is-not-a Manager
Of course not. They're sibling classes. Sure you can handle promotion by creating a new VP object, but you'll have to update all references, and object identity goes for a toss.


>> I've seen python code that catches exceptions caused by import failure and deals with it.
> I'd much, much rather ... have implementation details centralized and abstracted away.

Because of transitive imports, you can import a module in one file, with error-handling code, and import *that *file from the others. So centralizing error-handling code is an orthogonal concern. The fact that an import is an executable statement (as opposed to a compiler/loader directive) enables this strategy in the first place.


>>  method_missing may be the right solution for remote proxies. A macro may not be any better here.
> It clearly is better because it only requires an attribute designation, and I can do it to an arbitrary number of member variables without having to worry about generating the method to handle them all.

I'm not sure I understand you. method_missing can proxy method invocations (and therefore attribute accesses) without knowing what it's proxying.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=MojoX]I've been thinking about these issues a lot and was hoping someone would mention them.  Does Boo get any advantage in being a Mono language, like all the bindings and libraries available on the Mono platform?[/quote].NET is .NET.  CLS-compliant .NET languages, like Boo, can call any portion of the .NET framework, including code written in other languages.

> If so, that should be a plus, right?To a certain extent, yes.

> Still, the language documentation is poor and in my very brief experiences with the language, that has made learning difficult and, at times, frustrating.If you're a novice developer, I don't feel either route is correct.  Go read *How to Design Programs* or *Structure and Interpretation of Computer Programs*.  You'll find learning Boo much eaiser afterwards.

> Ideally, I'd like to use a CLI implementation of Ruby, but obviously that isn't an option.  I have tried to find for information about the Queensland Ruby.NET project, but since it is MS funded, I'm pretty sure it will be encumbered with a crappy license and MS tie-ins.Doubtful.  It's unlikely it'l lbe say, GPL'd, but MS has been more than reasonable with most of their .NET development stuff.

[quote=kartik_vad]hat's true only from a static typing perspective.[/quote]No, it's true from a **design** perspective too, like I said.

Dynamic-typing doesn't change the rules of OO inheritence: it is still an is-a relationship.  If your class API requires you to use the type system to subvert that rule, then you have a crappy class API in any language.  End of story.

In your case, all you wanted is a write() method.  Python lets you do this without any explicit declarations, and that's ok.  

In a statically-typed language, if the class API didn't provide that, I'd say it's crap API.  It's not letting you follow the is-a relationship.  In a duck-typed language, if the only reason you're using the dynamic typing is because the API had no forethought, then it's still a crap API, just not as infuriating for the user.

Yes, dynamic typing means you don't have to have as much abstraction as a static-hieharchy.  But I'm not sure that's a inherently good thing, in the sense of, it can lead to design decisions that don't have as much forethought, because you're not really considering what behaviors you do need and don't need.

> In a dynamically typed language, a more complex hierarchy is uncalled for.No, it is still called for.  Duck-typing doesn't allieve you of the rules.

> I've written about this in greater detail here.Linking the same blog post again does not an argument make.

> I think a type is only a small part of the behavior.But a fundamental part.  It's to my advantage to fix it so other people can code to it.

> You lose the freedom to substitute an object with another that is unrelated by inheritance but defines the required methods.Only if I don't control it's inhertience hieharchy.

> I don't consider it a good tradeoff.It's not remotely the black-and-white case you're describing.

> I find a model that says, "the operator + maps to the method +" to be more straightforward than one that says, "the operator + maps to the method __add__".For the class designer, sure.   But the class designer isn't why we have operator overloading, it is for the class users.  So to be blunt, **** the class designer.  Making his life eaiser is secondary here.  If you can provide a clean implementation to the user and make his life eaiser, great.  If you cannot, oh well.

> So + and .+ is just the operator/method duality - when you look at it as an operator, it's +, and when you look at it as a method, it's .+ . That's what I said you need to understand, not the implementation of individual overloaded operators.I understand, what I'm saying is, that's not a valid argument *because Ruby special cases the methods anyway.*.  The minute you get special treatement the value of the duality is exteremely questionable.  It's only of any benefit to the class designer, and as I said, his goals are secondary.  It's actually now a negative, because as I said, '.+' has a specific, different meaning to many people.

> Yes, I didn't mean it can't be done otherwise but that it's more straightforward this way.I fail to see how.  If all I want is to read data, neither way is more straightforward.  If I need a real class with business logic, I won't be using either solution by themselves.

> Sure you can handle promotion by creating a new VP object, but you'll have to update all references,Why is anything holding onto a reference longer than it should be?  I think this is specious: again, you're using the language features to defend bad coding practices to begin with.  

> and object identity goes for a toss.It already went for a toss, you changed the identity.  The fact I'm still pointing to the same address means nothing, you changed the semantics underneath.  Object identity is more than the pointer.

> I'm not sure I understand you. method_missing can proxy method invocations (and therefore attribute accesses) without knowing what it's proxying.I have 3 interfaces: IFoo, IBar, IBaz.  I have a class with 3 members, each one implementing one of those interfaces.   I want to proxy calls to each of those interfaces through the respective variable.  Write the method_missing() to do that.

---

### Post by thumper on 2006-04-25
[QUOTE=kartik_vad]I don't like C++'s const-correctness because of the code bloat.[/QUOTE]
*cough* bullsh*t

* C++ hat ON *

Const correctness normally only has code bloat for library creators.  For example  - iterators in the standard library.  Most of the time for code that you write, a method will either be const or not - not both.  You rarely need to provide both a const and a non-const version of a method in C++.

* all hats OFF *

Part of the problem is that people end up choosing one language and they say
> Language X is the language for me.
I'm going to use it for everything
A language is just a tool.  No tool is good for every job.  These days I use mostly python, but I wouldn't use it for everything.  I'm still a hard core C++ hacker too.

FYI - C++ templates can give duck-like typing (at compile time), which is being formalised into Concepts.

---

### Post by LordHunter317 on 2006-04-25
[QUOTE=thumper]Const correctness normally only has code bloat for library creators.  For example  - iterators in the standard library.  Most of the time for code that you write, a method will either be const or not - not both.  You rarely need to provide both a const and a non-const version of a method in C++.[/quote]To be fair, certain concepts, iterators and smart pointers to name just two, will always require const and non-const versions unless you're sure you need only one form of access or the other.

> FYI - C++ templates can give duck-like typing (at compile time), which is being formalised into Concepts.Which is useful to illustrate my point about duck-typing not resolving bad APIs: you still have to write your classes so they all use write() with the same arguments, for example.  Duck-typing doesn't absolve you of that, it just absolves you of explictly saying it.  That's what I was trying to spit out earlier, unsuccessfully.

---

### Post by kartik_vad on 2006-04-25
> I would avoid Boo until it is more mature
(As I mention in the comparison,) Boo's interpreter throws exceptions given programs with mistakes. You are given no indication what's wrong. I found it so frustrating - even for toy programs - that I stopped using Boo (at least for the moment).

---

### Post by kartik_vad on 2006-04-26
> **LordHunter317]Dynamic-typing doesn't change the rules of OO inheritence: it is still an is-a relationship.[/QUOTE]
The rules do change - you need to inherit only for implementation convenience. Inheritance to establish interface compatibility (IS-A) solves a problem dynamically typed languages don't have. In our example, you want to use an explicit interface so that you can reuse code in the manner I described. But you can already do that! A more complex hierarchy is just overhead.

Now, you may still want to have explicit interfaces for other reasons (clarity, finding bugs, etc), and I have no problem with that as long as all type declarations are optional.

> It's actually now a negative, because as I said, '.+' has a specific, different meaning to many people.
I'm unaware of that. Could you please explain?

> > I find a model that says, "the operator + maps to the method +" to be more straightforward than one that says, "the operator + maps to the method __add__".
For the class designer, sure.
To some extent, even as a user. When I think about what the code is doing, I find this the simpler model.

> If you can provide a clean implementation to the user and make his life eaiser, great. If you cannot...
I'd say, at least make the implementor's life easier.

> neither way is more straightforward
[LIST=1]
[*]If you overload operator[], you need to write code  to lookup and insert into a map (and create/declare the map in the first place). If you dynamically add attributes, you can avoid writing this boilerplate.
[*]We normally access attributes as object.attrib rather than as object['attrib'], and dynamically addable attributes allow that convention to be adhered to.[/LIST]

> Why is anything holding onto a reference longer than it should be?
Perhaps it has a valid use for the object. Why should all actions involving an employee come to an end just because it's promoted?

> > object identity goes for a toss.
It already went for a toss ... you changed the semantics underneath.
It's still an employee said:**
> I have 3 interfaces: IFoo, IBar, IBaz. I have a class with 3 members, each one implementing one of those interfaces. I want to proxy calls to each of those interfaces through the respective variable. Write the method_missing() to do that.

```
class Foo
	def doFoo
		puts "foo!"
	end
end

class Bar
	def doBar
		puts "bar!"
	end
end

class Container
	def initialize
		@foo = Foo.new
		@bar = Bar.new
	end
	
	attr_accessor :foo, :bar
end

class Proxy
	def initialize(realObject)
		@realObject = realObject
	end
	
	def method_missing(meth, *args)
		puts "calling " + meth.id2name
		@realObject.send meth, *args
	end
end
	

c = Container.new
proxy = Proxy.new c
proxy.foo.doFoo
proxy.bar.doBar

```
Output:
calling foo
foo!
calling bar
bar!

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=kartik_vad]The rules do change - you need to inherit only for implementation convenience.[/quote]No, they don't change in the manner you suggest.  The rule is just enforced at the method-level, instead of the class level.  Your 'write()' method still has to be the same in all instances.

> Inheritance to establish interface compatibility (IS-A) solves a problem dynamically typed languages don't have.No, they still have it, just not at the class level.

> In our example, you want to use an explicit interface so that you can reuse code in the manner I described.No, that's not what I said.  I wasn't very clear, so permit me to start over.

What I said was dynamic typing didn't let you do what you wanted, polymorphism did, which is true.  Otherwise, languages like Java would be incapable of achieving what you did.

What is true is that *duck-typing* allowed you to do what you did without the need for an explicit interface.  This is true.  However, *dynamic-binding of types* has nothing to do with it, otherwise C++ templates would be impossible.

This is a confusion many late-bound language advocates make: when the binding occurs has nothing to do with what is going on here.  You could still conceptually do it at compile time (or at least check it) and still achieve the same effect.

Now, the real question is, "Is duck-typing, static or dynamically-bound, better than explict typing by interface/class?"  I suspect the answer is typically, Yes.  But note that when the binding occurs matters little, and it's possible to do duck-typing in either situation.

This is the confusion your blog entry makes.  It's a confusion I furthered for not being totally clear in expressing myself, and you have my apologies for that.

I also (seperate point) further went on to say that if you couldn't do this in a statically-typed language, it is not because static-binding is bad, but because the class API is poor.  

It was poorly worded, but the point I was ultimately trying trying to get to was: write() still has to be the same everywhere, even if it's never explictly declared.  This plagues you regardless of type system.

You're not freed from the responsibility to make everything have a consistent interface, even if it's only at the method level.  

> I'm unaware of that. Could you please explain?By-element vector or matrix addition.  It's really more important for '.*', './', and '.^', since matrix-multiplication is special.  This is common in languages designed around matrix manipulation, e.g., Matlab.  

> To some extent, even as a user. When I think about what the code is doing, I find this the simpler model.Why does the class user care about how it is implemented?  Again, if he has to care, the *abstraction is crap.*  It's a non-sequitur.  If you break the abstraction, the abstraction is meaningless.

> I'd say, at least make the implementor's life easier.It doesn't though.  Implementing a meanginless abstraction helps no one.  You're writing code with no value.

[LIST=1][*]If you overload operator[], you need to write code  to lookup and insert into a map (and create/declare the map in the first place).[/quote]No, you don't.  In fact, I'm not sure how most DataReaders store data, but I'm 99% positive it is an array.  The lookup by field name is done on the fly, or via some (presumably static) field -> column order mapping.

> If you dynamically add attributes, you can avoid writing this boilerplate.No, at sompoint you still must do a name -> value lookup, if you must do one at all.  So at somepoint, there is a mapping operation going on, or there isn't.  You may have just shifted it to a lower level: i.e., the DB driver.  But you still must be correlating field names to column order *somehow*.  And seeing as a DataReader in .NET is a member of the DB driver, the above logic applies to it.

> [*]We normally access attributes as object.attrib rather than as object['attrib'],Indexers are perfectly permissible and a logical model for a row of data from the database, which is inherently a tuple with potentially named fields.  If you're going to argue that, you need to argue against tuples and associative arrays, for just returning rows of data from a database.

Remember, the minute we add logic to our class, this argument goes away: you won't be using just the DataReader or just your nifty field->property code generator.  And at that point, I suspect it's debatable in terms of which one will ultimately be more terse.

>  and dynamically addable attributes allow that convention to be adhered to.If it bothers you that much it's more than possible to take a DataReader in and spit a dynamically generated class out for any schema you want.  MS has tools to do this, but not at runtime.  However, it certainly would be possible.  But as I said, if you're just returning rows from the DB and have no logic behind the fields, I don't see why an associative array isn't an acceptable data structure.  That's all it is in the database, so there's no reason for it not to be the same in my code.

> Perhaps it has a valid use for the object.What has use to hold onto for its lifetime besides some sort of caching functionality, which by it's very nature is designed to deal with the object not existing at any time?

> Why should all actions involving an employee come to an end just because it's promoted?You didn't say there was a parent interface.  I can see the occassional usefulness of allowing transforms within a class hieharchy (specifically for object instaniation).  Certainly arbitrary transforms are evil. 

So I'll grant you that, in part. :)

Your method_missing() proxy is clever and legal, but not quite what I had intended.  I had intended for the methods to be part of the proxy class, so given:```
interface IFoo {
    void foo();
}

interface IBar {
   void bar();
}
```And a proxy class:```
class Proxy {
    private IFoo foo; // Or some subclass implementing IFoo
    private IBar bar; // Or some subclass implementing IBar
}
```You would automatically provide:```
class Proxy {
    void foo() { foo.foo(); }
    void bar() { bar.bar(); }
}
```

---

### Post by kartik_vad on 2006-04-26
I can't agree more with you regarding dynamic vs. static typing. (I wrote something on the same lines [here]("http://www.cse.iitb.ac.in/~kart/writings/Mostly-Static%20Duck%20Typing.html"), in case you're interested.) By "static typing", I actually meant static typing at the class level or, equivalently, static typing with type declarations (the way the popular statically typed languages do it). Sorry for the inaccuracy.

So, in the file example, dynamic typing enabled a simpler solution than static typing at the class level, but not more than static typing at the method level.

> > Inheritance to establish interface compatibility (IS-A) solves a problem dynamically typed languages don't have.
No, they still have it, just not at the class level.
All I'm saying is that with dynamic typing you don't need inheritance to exploit commonality. Yes, the two methods must be signature-compatible (it never occured to me that things could be otherwise).

> This is the confusion your blog entry makes.
If you mean [this one]("http://kartik-log.blogspot.com/2005/09/what-dynamic-typing-really-buys-you.html"), it has a qualifier in the beginning. But I probably wasn't clear somewhere else. Sorry.


Regarding understanding abstractions while using them, I still find myself curious about what's going on behind the scenes. I might never overload an operator, so perhaps theoretically it shouldn't matter to me whether the operator + maps to the method + or to __add__, but I hate mysteries; I need to know what's really going on.

So it does matter as a user and as an implementor (both deal with the same abstraction). And I think having a more straightforward model is more important than eliminating a superficial similarity to some other languages that might cause a little confusion for newcomers.

> > If you overload operator[], you need to write code  to lookup and insert into a map (and create/declare the map in the first place).
No, you don't. 
We seem to have lost context (or maybe I wasn't clear to begin with). I was referring to a situation where we create an object, populate it with data from the database and then hand it off to users who can read its attributes without trigerring further database access. To implement this by overloading [], you need to declare and instantiate a map, populate it with data from the database, and then have the operator[] read this map. It would be simpler to use the object itself as the map by adding attributes dynamically. Yes, at some point there is a mapping going on, but the language now handles it for us.

My intent in giving this example was to demonstrate a (valid) use for dynamically added attributes. You can certainly come up with a different example where this doesn't help you, but that doesn't invalidate my point.

> Indexers are perfectly permissible and a logical model for a row of data from the database, which is inherently a tuple with potentially named fields.
That's one way of looking at it, and if you take that view, overloading [] is perfectly reasonable. The other view is that it's just an object and so I expect to be able to access its attributes using '.'

If you take this idea to its conclusion, we don't logically need two operators [] and '.' Javascript has the beautiful equivalence obj.attrib == obj['attrib']. But as long as the language we use has two distinct operators, we have to make a choice, and sometimes obj.attrib may indeed be preferable (in which case, dynamically added attributes are useful).

> Remember, the minute we add logic to our class, this argument goes away
Yes.

> You didn't say there was a parent interface... I can see the occassional usefulness of allowing transforms within a class hieharchy (specifically for object instaniation).  Certainly arbitrary transforms are evil. 
Good. We're in perfect agreement. Unstated assumptions are wasting a lot of time for us.

 
```
class Proxy {
    private IFoo foo; // Or some subclass implementing IFoo
    private IBar bar; // Or some subclass implementing IBar
}
```You would automatically provide:```
class Proxy {
    void foo() { foo.foo(); }
    void bar() { bar.bar(); }
}
```

Maybe a method_missing is the worse (or infeasible) way to do what you want. I'm not saying method_missing is on the whole superior to macros, only that it can sometimes be better. You agree with that, don't you?


My apologies for saying (in my first post) that I think you lack understanding.

---

### Post by LordHunter317 on 2006-04-26
> **kartik_vad]All I'm saying is that with dynamic typing you don't need inheritance to exploit commonality.[/quote]No, you don't need it with duck-typing, but it be checked at compile time if one chooses to do so.

> Regarding understanding abstractions while using them, I still find myself curious about what's going on behind the scenes.That's wonderful and I suppose all good programmers, computer scientists, and developers are naturally curious.  But from an engineering perspective, we don't design things to give clean interfaces to the curious programmer, we design abstractions to give clean interface in usage.

Curiousity falls by the wayside in application.  If you can satisfy both, great.  But if you're writing code to solve a problem, writing code that's clean for "the curious programmer" doesn't gain you anything :p

> So it does matter as a user and as an implementor (both deal with the same abstraction).But it doesn't.  It doesn't matter to the user, because there's no requirement to fufill their curiosity to get working code.  At the end of the day, I get paid for working code, not stasifying the curositities people using my code.

> And I think having a more straightforward model is more important than eliminating a superficial similarityIt's hardly superifical, it's identical syntax with a different meaning.

> I was referring to a situation where we create an object, populate it with data from the database and then hand it off to users who can read its attributes without trigerring further database access.Correct.

>  To implement this by overloading [], you need to declare and instantiate a map, populate it with data from the database, and then have the operator[] read this map.At somepoint, you have to do something like this, though I think most .NET data readers have an additional layer of indirection.

> It would be simpler to use the object itself as the map by adding attributes dynamically.No, it's not clear it's clearer for the end user (the amount of information they have to know is constant) and it's not clear it's any clearer for the class writer, either.  It ultimately boils down to which one will yield less code, which really depends on the language.

> My intent in giving this example was to demonstrate a (valid) use for dynamically added attributes.Yes, but my point remains: the value is questionable if there are already equivalent ways to do it in the language.

I'll grant it's valid, but my perspective is that features of limited value probably shouldn't be included if all use cases can be reasonable covered with other mechanisms.  In this specific case, they certainly can be.

> The other view is that it's just an object and so I expect to be able to access its attributes using '.'I would argue if the object is just attributes with no code behind them, you just have an assocative array, record, whatever you wish to call it, in a different form.  You're in agreement with me here, I think.

The only advantage is the type-checking in statically-bound languages.  But we're not talking about them, are we?  said:**
> But as long as the language we use has two distinct operators, we have to make a choice, and sometimes obj.attrib may indeed be preferable (in which case, dynamically added attributes are useful).This case you've given doesn't show a clear preferable manner, though. 

> I'm not saying method_missing is on the whole superior to macros, only that it can sometimes be better. You agree with that, don't you?In the solution you gave, it's slightly less code.  That's the only advantage.  Macros are far more flexible and clearer, and I'd give up a little conciseness for more general-purpose utility in this case.

> My apologies for saying (in my first post) that I think you lack understanding.And the same to you. :)

---

### Post by kartik_vad on 2006-04-27
> **LordHunter317]from an engineering perspective, we don't design things to give clean interfaces to the curious programmer, we design abstractions to give clean interface in usage.[/QUOTE]

For the user, it largely doesn't matter what method an operator maps to, so the "operator + maps to method +" model doesn't seem any more complex than the alternatives. Yes, there is the issue of confusion with vector operators in matlab and friends, but I'm trying to say that syntax clashes with operators in other languages are far less important than having a clean model within the language. Which matters because...
[LIST=1]
[*]A user of one class could well be an implementor of another, so I would say it matters how things look to the implementor.
[*]We don't explicitly go out of our way to satisfy users' curiosities said:**
> 

For instance, Ruby's (and Python's) array unpacking operator '*' looks very much like a pointer dereference in C, but I have no problem with that. Similarly, I would consider the matlab clash to be a small price to pay, given the other advantages.

> I would argue if the object is just attributes with no code behind them, you just have an assocative array, record, whatever you wish to call it, in a different form.
That's a valid view, and if you take that, my argument collapses.

But I prefer not to take that view:  I'd like to look at it as an object rather than as a map. Given an employee object, I'd rather access its salary as fred.salary than as fred['salary']. As I look through my code, I find that '.' accesses far outnumber [] accesses, and I'd like to stick with that convention.Supporting the former allows the user to use this object consistently with other objects whose data did not come from the database.

But if you want to look at it as a data structure, that's perfectly reasonable.
[QUOTE]and it's not clear it's any clearer for the class writer, either.
In Python, using '[]' gives you:
```

class Employee:
    def __init__(self, database_cursor):
        self.state = {}
        for each column in the current row
            self.state[col_name] = col_value

    def __getitem__(self, name):
        return self.state[name]

```
whereas using '.' is simpler:
```

class Employee:
    def __init__(self, database_cursor):
        for each column in the current row
            setattr(self, col_name, col_value)

```
> It ultimately boils down to which one will yield less code, which really depends on the language.
It seems to me that the two differences between the two versions - creating the map and overloading [] - must be present in some form or shape irrespective of the language.

> The only advantage is the type-checking in statically-bound languages. But we're not talking about them, are we? ;) 
Even if the language did type inferencing to detect bugs, the inferencer would be thrown off by the dynamic creation of attributes.

> > I'm not saying method_missing is on the whole superior to macros, only that it can sometimes be better. You agree with that, don't you?
In the solution you gave, it's slightly less code... I'd give up a little conciseness
Well, if method_missing is sometimes a better tool for the job, I'm all for it.

---

### Post by LordHunter317 on 2006-04-27
> **kartik_vad]For the user, it largely doesn't matter what method an operator maps to, so the "operator + maps to method +" model doesn't seem any more complex than the alternatives.[/quote]Except for the part where it isn't hidden, yes.  You ought not to be able to do '.+' at all, in my mind.  You've defeated the point of operator overloading if the method is directly callable.  

> [*]A user of one class could well be an implementor of another, so I would say it matters how things look to the implementor.This doesn't matter.  They still don't care about the implementation of your class if they're using it in the implementation of their own.  Once you get to the class user it doesn't matter what they're doing with it.  Again, if it does, you go back to having a poor abstraction.  Once we hit the user, it had better be abstracted, full-stop. :)

> Put differently, I think we should try to make abstractions as transparent as possible so that when the user wants to peer through the abstraction, things are easy for him.I'll agree to that in theory, but again, this is a class implementator's concern.  It's a secondary goal.  If it compromises the abstraction to the user, it's compromising the abstraction itself, and must be sacrified.

I'd be fine with the naming, I consider it novel in fact, but I'm not fine with the fact that the methods can be so trivally called.  If you want to be LISP, then be LISP and switch to prefix notation :p  Otherwise, don't stratle the fence.

> For instance, Ruby's (and Python's) array unpacking operator '*' looks very much like a pointer dereference in C, but I have no problem with that. Trodding on C's shoes isn't something to be upset about.  Especially when it comes to pointers.

> Similarly, I would consider the matlab clash to be a small price to pay, given the other advantages.I don't consider exposing the overload as a method an advantage, personally.  It doesn't gain you anything, it provides another way to achieve the exact same behavior (generally a negative thing) and it's not relevant to the class user.


> But I prefer not to take that view:  I'd like to look at it as an object rather than as a map.I don't see that view as valid unless you're imbuing additional logic.  A way to read and write related fields is jsut a name->value map, no matter what you call it.

> Given an employee object, I'd rather access its salary as fred.salary than as fred['salary']. As I look through my code, I find that '.' accesses far outnumber [] accesses, and I'd like to stick with that convention.Supporting the former allows the user to use this object consistently with other objects whose data did not come from the database.I'm not sure consistent syntax is a winning argument here.  It is a argument, but my code in practice uses multiple data structures with multiple forms of access.  As such, I'm not sure I buy it.  The consistency gain may not be strong enough in many cases to justify it, anyway.  I'm sure there are some where it would, too.  IOW, this isn't a clear win, unless you consider it on a case-by-case basis.

> But if you want to look at it as a data structure, that's perfectly reasonable.That's what I was taught I was supposed to be doing, so...  said:**
> It seems to me that the two differences between the two versions - creating the map and overloading [] - must be present in some form or shape irrespective of the language.They are, but in .NET the indexer is less code.  In python, the properties are less, due to setattr().  

> Even if the language did type inferencing to detect bugs, the inferencer would be thrown off by the dynamic creation of attributes.I think my point was that you wouldn't do it dynamically.

> Well, if method_missing is sometimes a better tool for the job, I'm all for it.I think my point was that conciseness isn't the only thing to consider here, especially when designing a language or it's API.

---

### Post by kartik_vad on 2006-04-29
> exposing the overload as a method... doesn't gain you anything
>>> map (int.__neg__, [1, 2, 3])
[-1, -2, -3]
In general, any higher-order operation where you're invoking a method without knowing its name benefits from not having to special-case operators.

> You've defeated the point of operator overloading if the method is directly callable... compromising the abstraction itself
The abstraction is not being compromised, because no guarantee provided by the abstraction is being violated; after doing a .+, you can do a + (as in x+y) and it works as expected. So the abstraction is not being compromised, only bypassed.

Which is perfectly fine since the abstraction is built on top of a lower-level abstraction (methods) in a well-defined way (the operator + maps to the method +).

Moreover, I strongly feel I should be able to do a .+ since + is a method (and my notion of a method includes it being callable by name).

> it provides another way to achieve the exact same behavior
Ruby doesn't explicitly add another way; it's already there - part of the basic notion of a method, that you can call it by name. I see no point in going out of your way to forbid it, given that it's harmless and actually useful.

Python and C++ also (largely) follow this approach.

> They still don't care about the implementation of your class if they're using it in the implementation of their own.
Oops. Another misunderstanding. I was disagreeing with the view "I don't care how this language feature affects the implementor (of a class)" because there's a high chance you'll be an implementor - if not of one class, of another, where you may use the said feature.

> I'm not fine with the fact that the methods can be so trivally called.
I fail to see how calling a method named + as .+ is any more or less trivial than calling a method named foo as .foo . When I see object.something, it's perfectly clear to me what's going on.

> Trodding on C's shoes isn't something to be upset about.  Especially when it comes to pointers.
My point was that when I have no problem with a syntax clash with a basic operator in something as familiar as C, neither do I have a problem with a syntax clash with a matlab operator.

> A way to read and write related fields is jsut a name->value map, no matter what you call it.
So you're saying behavior-less objects are a bad idea. Many of my classes start out without behavior and gradually acquire it. By creating them as objects (rather than maps, hashtables or whatever you call them), I have the flexibility to add behavior at any time without breaking clients. I not only benefit from consistent syntax with objects with behavior but the attribute access syntax has a little less noise (obj.attrib as compared to obj['attrib']), which I think matters quite a bit because this syntax is heavily used. And, FWIW, a type inferencer may not be able to detect bugs in the [] use.

> I think my point was that conciseness isn't the only thing to consider here, especially when designing a language or it's API.
I thought the conciseness of method_missing over macros reflects their being a better fit to the problem at hand.

---

### Post by LordHunter317 on 2006-04-29
> **kartik_vad]>>> map (int.__neg__, [1, 2, 3])
[-1, -2, -3]
In general, any higher-order operation where you're invoking a method without knowing its name benefits from not having to special-case operators.[/quote]Huh?  Come again, I'm having a devil of a time comprehending that sentence.

> The abstraction is not being compromised,Yes, it is.  You've violated orthogonality.

>  because no guarantee provided by the abstraction is being violated said:**
> Yes, I never said they weren't.

[quote]after doing a .+, you can do a + (as in x+y) and it works as expected. So the abstraction is not being compromised, only bypassed.Which still makes the abstraction mechanism *poor*.  One point of an abstraction is I cannot bypass it.

[quote]Which is perfectly fine since the abstraction is built on top of a lower-level abstraction (methods) in a well-defined way (the operator + maps to the method +).But to the user, it's not really ok.  There's no point in presenting two *identical* methods for doing the same thing.  That's almost not just universally bad, but terrible from several perspectives.

> Moreover, I strongly feel I should be able to do a .+ since + is a method (and my notion of a method includes it being callable by name).My point is, you're still looking at operator overloads the wrong way.  The fact it is a method is an *implementation detail.*  
That means, from the perspective of the person using the operator, I shouldn't be able to access it as a method.  It should be abstracted away.

Your notion of a method is clearly wrong: (lambda).  The only property we imbue to a method is callability (engrish rules).  A name is common, but not required.

> Ruby doesn't explicitly add another way; it's already there - part of the basic notion of a method, that you can call it by name.Right, and it should be removing it.

>  I see no point in going out of your way to forbid it, given that it's harmless and actually useful.It's not harmless, that's the whole point: It leaves two public entrypoints for calling the same code.   This complicates refactoring, complicates your public API (not that Ruby has private ones anyway, but the argument is in general), and is confusing to users in a complicated API.

The only time it's ever useful is inside the class, so you don't have to define a method that actually does the work and an operator-overload method that just calls the former.  But given the choice between some syntax overhead or a nastier public API, I'll take the former everytime.

> Python and C++ also (largely) follow this approach.That's because Python doesn't understand the value of Simula OOP yet and C++ does not, unless I'm misunderstanding you.

> So you're saying behavior-less objects are a bad idea.I'm not saying they're a bad idea, what I'm saying is there's no reason to perfer them to other data structures if we have them.

> Many of my classes start out without behavior and gradually acquire it. By creating them as objects (rather than maps, hashtables or whatever you call them), I have the flexibility to add behavior at any time without breaking clients.Yes, but you didn't say that originally.  

> I not only benefit from consistent syntax with objects with behavior but the attribute access syntax has a little less noise (obj.attrib as compared to obj['attrib']), which I think matters quite a bit because this syntax is heavily used.I'm not crying over 3 extra characters.

> And, FWIW, a type inferencer may not be able to detect bugs in the [] use.I'm aware.

> I thought the conciseness of method_missing over macros reflects their being a better fit to the problem at hand.Yes, but when designing a language, one must consider more cases.  Macros are clearly a better general-case solution and are not significantly more complicated.  It's not quite that terse, but it's terse enough.

---

### Post by kartik_vad on 2006-04-29
> **LordHunter317]Your notion of a method is clearly wrong: (lambda)....  A name is common, but not required.[/QUOTE]
That describes a function, not a method. A method, being a member of a class, always has a name.


> >>> map (int.__neg__, [1, 2, 3])
[-1, -2, -3]
> In general, any higher-order operation where you're invoking a method without knowing its name benefits from not having to special-case operators.
Huh?  Come again, I'm having a devil of a time comprehending that sentence.
If an operator weren't a method, i.e., if it weren't callable by name, you wouldn't be able to pass an operator in a context where a function is required, like the map above. Making operators callable by name allows higher-order functions to work with operators as well as methods.

This is the heart of my argument - that the "other way" has its advantages. If not, why would anyone want two ways to do the same thing?

> One point of an abstraction is I cannot bypass it.
That depends on what you consider as the abstraction. If you consider operator overloading as allowing you to define overloads, then, yes, Ruby's (and Python's) model is bad because users shouldn't see that an overload is just a method said:**
> It leaves two public entrypoints for calling the same code.   This complicates refactoring, complicates your public API (not that Ruby has private ones anyway, but the argument is in general), and is confusing to users in a complicated API.
In general, yes. But here, I don't think anybody (who understands Ruby) will find the presence of both + and .+ confusing or a complication or complain about refactoring because .+ would be used rarely.


> I'm not crying over 3 extra characters.
Neither am I; I'm complaining about the readability loss they entail.


> Macros are clearly a better general-case solution... not quite that terse, but it's terse enough
If macros are not quite as good as method_missing (in some cases), I want to have method_missing (not instead of macros but in addition to them). Besides, at least for me, the notion of trapping calls to undefined methods is simpler than that of rewriting code (macros).

---

### Post by LordHunter317 on 2006-04-29
> **kartik_vad]That describes a function, not a method. A method, being a member of a class, always has a name.[/quote]Clearly though, languages like C++ show that's not the case. Ruby and Python also prove this is false: constructors have names, but you're not supposed to call them by their actual name.  Same goes to destructors in nearly every language that has them.

The requirement to 'always be called by name' is clearly not a property of a method.  It's not even apparent it is a desirable trait as there are clear cases where it is not, like constructors and destructors.

> If an operator weren't a method, i.e., if it weren't callable by name, you wouldn't be able to pass an operator in a context where a function is required, like the map above.Yes, you would, it would require a wrapper is all.  No, you couldn't pass them directly.  I'm not sure that alone is enough to justify making them publically callable.  If anything, it's a justification for being able to do boost-like lambda expressions in code, e.g.:```
std::vector<int> myvector said:**
> This is the heart of my argument - that the "other way" has its advantages.I'm not sure it does; I'm not sure that mechanism shouldn't be provided by other features that are potentially far more useful anyway.  C++ in this case makes a very compelling argument for lambda expressions.

> But if you consider operator overloading as just defining a mapping from the operator + to the method + (or __add__, depending on the language),That's clearly an incorrect view to take in general, because it doesn't work for primitives.  Yeah, yeah, Ruby and Python don't have them, I know.  But the better abstraction in my mind is the one that's more generally applicable, which isn't this one.

> I use the second model - I insist that overloads be plain methods - because it allows higher-order functions to work with operators.I'm distinctly of the mind lambda expressions are superior.  They're more readable unless the language requires god-awful syntax, it means consistent syntax all the time when using the class, and it avoids all the nasty public API consequences. 

> As a side effect, the language is simpler because we don't have two abstractions - methods and overloads - which are very similar except that one is callable by name and the other isn't.But we already have that so this is a non-sequitur.  

> In general, yes. But here, I don't think anybody (who understands Ruby) will find the presence of both + and .+ confusing or a complication or complain about refactoring because .+ would be used rarely.Until they have 100k lines to slog through, then they'll complain immensely.  Just because something's expected doesn't change the fact it's a pain.

> Neither am I; I'm complaining about the readability loss they entail.There is no readability loss unless your language lacks arrays of any sort, least in my mind.

> If macros are not quite as good as method_missing (in some cases), I want to have method_missing (not instead of macros but in addition to them).But they are.  Conciseness isn't the only thing to consider when measuring a feature as "good" or "bad".  You need to state other criteria, as this is rather specious.

> Besides, at least for me, the notion of trapping calls to undefined methods is simpler than that of rewriting code (macros).It's not rewriting per se, it's generating it in the first place, but I knew what you meant. :)

---

### Post by kartik_vad on 2006-04-30
> **LordHunter317]Clearly though, languages like C++ show that's not the case. Ruby and Python also prove this is false: constructors have names, but you're not supposed to call them by their actual name. Same goes to destructors in nearly every language that has them.

The requirement to 'always be called by name' is clearly not a property of a method. It's not even apparent it is a desirable trait as there are clear cases where it is not, like constructors and destructors.[/QUOTE]
Constructors (or initialize or __init__) and destructors (or finalize or whatever) are different - they are not callable (or intended to be called) on an existing object. Which is different from being callable, but not by name - the case with operators in your model.

So, if you insist on calling constructors and the like methods, yes, the "methods are callable by name" view may not be accurate, but the "methods are callable, perhaps not by name" view is no more accurate. In fact, it's less so, because all methods that are callable (or intended to be called - the language may not enforce this) are callable by name.

> Yes, you would, it would require a wrapper...  I'm not sure that alone is enough to justify making them publically callable.
But a wrapper is still a roundabout way of doing things. I'd rather say, *apply negation on the elements of this list* than *apply a function that applies negation on its argument on the elements of this list*.
map(int.__neg__, list)
is more straightforward than
map(lambda - _1, list)
or whatever the syntax is.

The fact that some operations are methods and some are operators is an irrelevant detail here - both an operator and a method take some argument(s), do some computation and return something, and that's all that matters for a map. Forbidding operators from being callable by name forces me to express my intention in a roundabout way. And adds an artificial distinction said:**
>   for_each(myvector.begin(), myvector.end(), std::cout << _1);
I can pass it to a method expection a functor and get the desired behavior with no additional code.
In this case, perhaps. But if C++ had a polymorphic output method and bound methods, I'd rather write:
for_each(myvector.begin(), myvector.end(), cout.write);

Operators callable by name won't help in every case, but they clearly do in some, and for me that's enough of a reason to have them, especially when I see hardly any downside (see below).

> I'm not sure that mechanism shouldn't be provided by other features that are potentially far more useful anyway.  C++ in this case makes a very compelling argument for lambda expressions.
There may be a case for lambda expressions, but that doesn't change the fact callable operators enable a more direct solution. I'd want callable operators whether or not there are lambda expressions, just as I'd want method_missing whether or not macros are supported.

> That's clearly an incorrect view to take in general, because it doesn't work for primitives.  Yeah, yeah, Ruby and Python don't have them, I know.  But the better abstraction in my mind is the one that's more generally applicable, which isn't this one.
I'd say primitive operators is the incorrect model because [LIST=1]
[*]it prevents me from treating operators like methods,
[*]it's not uniform - addition for integers is not a method whereas addition for matrices is.
[/LIST]
I'm not sure primitive operators bring any significant advantage (in a dynamically typed language).

> Lambda expressions... means consistent syntax all the time when using the class
Callable operators also means consistent syntax (though perhaps in a different way) - any operation can be invoked as
object.operation_name

> But we already have that so this is a non-sequitur.
We don't - in the present model, overloads are just ordinary methods, they only have a specific name.  

> it avoids all the nasty public API consequences. ...(refactoring) is a pain.
That's an argument against any decision that gives multiple ways to do a given task, like providing convenience methods. Should there be no convenience methods at all because it makes the public API larger and hurts refactoring? I don't think so. The relevant question is if the advantages of multiple ways outweigh the cost.

In this case, most code would do a x+y, and .+ will be used only by higher-order functions (and perhaps other specific situations). I think it's a good tradeoff.

> There is no readability loss unless your language lacks arrays of any sort, least in my mind.
In a language with arrays and maps, I still find
enterprise.warp_drive.speed = 9.6
more readable than
enterprise['warp_drive']['speed'] = 9.6

> Conciseness isn't the only thing to consider when measuring a feature as "good" or "bad".  You need to state other criteria, as this is rather specious.
I'm trying to say that [Succinctness is Power]("http://www.paulgraham.com/power.html"). Or is this an exception to that rule?

---

### Post by LordHunter317 on 2006-04-30
> **kartik_vad]Constructors (or initialize or __init__) and destructors (or finalize or whatever) are different - they are not callable (or intended to be called) on an existing object.[/quote]They're still methods though, by your definition.

> Which is different from being callable, but not by name - the case with operators in your model.Yes, but it still breaks your definition.

> So, if you insist on calling constructors and the like methods, yes, the "methods are callable by name" view may not be accurate, but the "methods are callable, perhaps not by name" view is no more accurate.Clearly it is, as it includes operator overloads and constructors and destructors.

>  In fact, it's less so, because all methods that are callable (or intended to be called - the language may not enforce this) are callable by name.C++ again, clearly proves this isn't the case.

> I'd rather say, *apply negation on the elements of this list* than *apply a function that applies negation on its argument on the elements of this list*.
map(int.__neg__, list)
is more straightforward than
map(lambda - _1, list)
or whatever the syntax is.Only if the syntax is ugly.  I find writing exactly how I would when I write a foreach() loop more intuitive and sensical.    

> The fact that some operations are methods and some are operators is an irrelevant detail here - both an operator and a method take some argument(s), do some computation and return something, and that's all that matters for a map. But in languages with primitives it does matter, because in the former case I must use a lambda expression of sorts.  I have no choice in the matter.  

> Forbidding operators from being callable by name forces me to express my intention in a roundabout way.My point is, if the choice is being forced on you in some cases, it's more consistent to force it on you in all cases.  I realize that's not applicable to Ruby, but it is applicable in general.

One could conclude perhaps this is justification for not having primitives and perhaps not having operator overloads either, neither of which I'll say is neccessarily horrible.

>  And adds an artificial distinction said:**
> You already don't have a square-root operator, so I think this is somewhat specious.  The distinction already exists, it's just being furthered.

[quote]But if C++ had a polymorphic output method and bound methods, I'd rather write:You can do polymorphic binding via boost bind.  But this code isn't equivalent C++ anyway, because << doesn't directly map to .write(), FWIW.  I wrote it that way for a reason ;)

[quote]I'd say primitive operators is the incorrect model because [LIST=1]
[*]it prevents me from treating operators like methods,I'm still not convinced that's a correct abstraction.  I'll concede it makes more sense in a dynamically-typed language, but I still feel operator overloads having their method nature being obscured is more correct because it's more applicable everywhere.

> Callable operators also means consistent syntax (though perhaps in a different way) - any operation can be invoked as
object.operation_nameBut only if you do that *all the time.*  At which point, you've lost the purpose of the overload.

The fact is, in ruby's model, I can call the '+' overload in two ways:```
3.+ 4
``` and ```
3 + 4
```This is less consistent because it's two different syntaxes.  We have two ways to do the same thing.  That's less orthogonal, period.

> We don't - in the present model, overloads are just ordinary methods, they only have a specific name.  But they have different syntax too.  Special-case syntax, so operator overloads look like real infix notation.  The distinction does exist.

> That's an argument against any decision that gives multiple ways to do a given task, like providing convenience methods. Should there be no convenience methods at all because it makes the public API larger and hurts refactoring?If they reduce total code written, they should be included, for something of pure convinence.  The issue here is that the feature in question doesn't do that.

I don't think so. The relevant question is if the advantages of multiple ways outweigh the cost.

> I'm trying to say that [Succinctness is Power]("http://www.paulgraham.com/power.html"). Or is this an exception to that rule?Yes, possibly.  Features shouldn't be designed in simply because they make code succinct.  Things like orthogonality and the level of abstraction they provide need to be considered as well.

---

### Post by kartik_vad on 2006-04-30
We seem to be covering the same points again and again in different ways, so let me end the discussion here.

---

