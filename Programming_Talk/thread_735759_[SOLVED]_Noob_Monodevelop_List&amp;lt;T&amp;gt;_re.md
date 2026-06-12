---
title: "[SOLVED] Noob Monodevelop List&amp;lt;T&amp;gt; reference"
date: 2008-03-26
forum: Programming Talk
---

### Post by sum1nil on 2008-03-26
Hello.
I'm new to monodevelop. I understand it has a Xaml parser and of course runs c#. 
I copied over some xaml and code behind classes. 
When I build, I get 4 errors all having to do, I think, with
using System.Collections.Generic;
The code snips are:
	public interface IContactProvidier

	{

		List<Contact> GetContacts();

	}
The error says:
error CS1041: Identifier expected
The List doesn't seem to be recognized as a class. I searched add references from Monodevelop but didn't recognize anything close to 
using System.Collections.Generic;
The question is what reference do I use to get a List<T> class?
Thank you in advance for your help.

---

### Post by themusicwave on 2008-03-26
If you want to set a list equal to a function call it would be:

List<Contact> =  GetContacts();

Without the equal sign it would certainly be an error.  I think adding the equal sign will fix this problem.

You have the correct reference it is:
using System.Collections.Generic;

---

### Post by sum1nil on 2008-03-26
I appreciate the response.
The snippet:

public interface IContactProvidier
{ List<Contact> GetContacts(); }

is for an interface which only defines the methods a class that uses the interface must implement. If I remember right they are called virtual abstract classes in c++, all function declarations and no implementation.  I'm not sure why the example I worked from felt the need to state an interface for one method.

By the way I like Ubuntu, it was so much easier to set up than my old Mandrake. When I reboot, I'll go back into it and  I'll rewrite without utilizing an interface and post the results back.
Thanks for your time.

---

### Post by themusicwave on 2008-03-26
Yeh that was a silly mistake on my part....

I know what an interface is, yet somehow completely missed that problem.

Another possible issue is where is the reference to Contact?  I pasted your little snippet into visual studio here at work and it says:

Error	1	The type or namespace name 'Contact' could not be found (are you missing a using directive or an assembly reference?)	

So it appears you need a using statement for your contact Class.  Unless you have one but it isn't in the snippet.

---

### Post by sum1nil on 2008-03-26
I didn't want to fill up the forum with the code but rather direct to the example I was working/learning from at:

[http://blogs.sqlxml.org/bryantlikes/archive/2006/09/20/Enabling-WPF-Magic-Using-WCF-_2D00_-Part-1.aspx](http://blogs.sqlxml.org/bryantlikes/archive/2006/09/20/Enabling-WPF-Magic-Using-WCF-_2D00_-Part-1.aspx)

[The code on the web page has nasty number lines and copies and pastes badly so I can post it all if it would be better]

Monodevelop doesn't complain about the Xaml code only that there is no type at the List<T> GetContacts(). Meaning, I believe, that it just doesn't believe it exist. The tooltips on Monodevelop work fine when I hover over other classes telling me the namespace and other very useful info. If I hover over List<T>,  no tooltip pops up.

I'm bouncing back and forth between boots of ubuntu and xp. The code works fine under windows.
I'm not that experienced yet with ubuntu but I have used mandrake in the past. I'm I guess a linux hobbyist. No urgent need for a fix, just darn curious if I can do work in VS C# express then copy and work on it in ubuntu. :popcorn:

---

### Post by uzusan on 2008-03-26
I found this : [http://lists.ximian.com/pipermail/monodevelop-list/2007-October/006798.html](http://lists.ximian.com/pipermail/monodevelop-list/2007-October/006798.html) which may help. It seems you need to switch the monodevelop profile to .net 2.0 rather than 1.0/1.1

---

### Post by sum1nil on 2008-03-26
Yes, that works. The generic list class is found.
I have a fatal build error but not due to the List class not being recognized. Maybe I'm confused about this whole Xaml thing and everyone has a different version. 
I'll read on but one problem solved.
Thanks for the answer.

---

### Post by uzusan on 2008-03-26
> **sum1nil said:**
> Yes, that works. The generic list class is found.
I have a fatal build error but not due to the List class not being recognized. Maybe I'm confused about this whole Xaml thing and everyone has a different version. 
I'll read on but one problem solved.
Thanks for the answer.

What is the error you are getting now?

---

### Post by sum1nil on 2008-03-26
Building Project: test (Debug)
Performing main compilation...

Build failed. ApplicationName='gmcs', CommandLine='"@/tmp/tmp6fdeb344.tmp"', CurrentDirectory='/home/sum1nil/Projects/test/test', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'


Seems a little vague to me. :confused:

By the way, how do I mark my question as answered and give people thanks/kudos for their help?

---

### Post by uzusan on 2008-03-26
> **sum1nil said:**
> Building Project: test (Debug)
Performing main compilation...

Build failed. ApplicationName='gmcs', CommandLine='"@/tmp/tmp6fdeb344.tmp"', CurrentDirectory='/home/sum1nil/Projects/test/test', PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'


Seems a little vague to me. :confused:

By the way, how do I mark my question as answered and give people thanks/kudos for their help?

That is quite a vague error. Have you managed to build other programs before or is this the first? I think it may be that some of the programs required (such as the linker) may not be included in the path.

To mark the thread as solved, use the thread tools at the start of the thread, click on thread tools and the last entry should be mark as solved and you can click on the icon that looks like this: [IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG] to thank people.

---

### Post by sum1nil on 2008-03-26
No, I have never built anything with Monodevelop before except for "hello world". This was the program I picked to see if xaml and c# behind works with Monodevelp. I wonder... mmmm should have tried something easier, maybe? 
Thanks again.

---

### Post by uzusan on 2008-03-26
> **sum1nil said:**
> No, I have never built anything with Monodevelop before except for "hello world". This was the program I picked to see if xaml and c# behind works with Monodevelp. I wonder... mmmm should have tried something easier, maybe? 
Thanks again.

XAML seems pretty complicated to me and still in development. I'd suggest having a look through this page : [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight) for details. I would start with something simpler, that is part of the .net spec or perhaps some GTK+ stuff to learn your way round monodevelop.

---

### Post by sum1nil on 2008-03-26
Installing packages I found mono-gmcs is:
Mono C# 2.0 compiler 
This is the Mono C# (C-Sharp) 2.0 compiler, a platform-independent compiler
which produces CIL (Common Intermediate Language) binary executables.
The gmcs compiler supports the C# 2.0 featureset like generics, anonymous
methods, iterators, partial types and nullable types.

I will try again now that I've installed this package.

---

