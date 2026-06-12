---
title: "C# is a strange language"
date: 2011-09-04
forum: Programming Talk
---

### Post by snip3r8 on 2011-09-04
This is basically a discussion thread.

I am currently taking a C# coarse and Im finding that the language is a tad strange at some parts ,for example im now on .net remoting and the size of the namespaces! System.OMG.These.Namespaces.Are.Long; seems to be an acceptable length for a namespace

So i just want to see who else finds the language strange(particularly if you are used to c/c++).

---

### Post by Bachstelze on 2011-09-04
I wish people would stop saying "C/C++", as if those languages were the same. I am used to C, C++ and C# are equally strange to me.

---

### Post by snip3r8 on 2011-09-04
> 
As you may know, C++ was built upon the foundation of C.
In fact, C++ includes the entire C language, and (with minor
exceptions) all C programs are also C++ programs. When C++
was invented, the C language was used as the starting point. To C
were added several new features and extensions designed to
support object-oriented programming (OOP). However, the C-like aspects of
C++ were never abandoned, and the ANSI/ISO C standard is a base document for
the International Standard for C++. Thus, an understanding of C++ implies an
understanding of C.


That came out of a book written by this guy: [http://www.herbschildt.com/](http://www.herbschildt.com/) ,and im pretty sure he knows whats going on ,so sorry but people will never stop saying "C/C++"

---

### Post by NovaAesa on 2011-09-04
I have to respectfully disagree with Herb Schildt. While technically C is a (near) subset of C++, you *shouldn't* be using certain C constructs in C++ code. E.g. if someone in my programming team was to use malloc etc without very good reason in a C++ program, they would be rewriting the code. The languages are only superficially similar in a technical sense.

---

### Post by snip3r8 on 2011-09-04
> **NovaAesa said:**
> I have to respectfully disagree with Herb Schildt. While technically C is a (near) subset of C++, you *shouldn't* be using certain C constructs in C++ code. E.g. if someone in my programming team was to use malloc etc without very good reason in a C++ program, they would be rewriting the code. The languages are only superficially similar in a technical sense.

I think the point with saying "C/C++" is to show that the C++ language was based on C ...or though thats why its called C++ and not just ++ so its kind of like saying "FBI Investigation" which expands to "Federal Bureau of Investigation Investigation "   ... anyway i would like to make it a point that when i posted C/C++ i meant C or C++ as in both languages as separate entities.

---

### Post by akand074 on 2011-09-04
> **NovaAesa said:**
> I have to respectfully disagree with Herb Schildt. While technically C is a (near) subset of C++, you *shouldn't* be using certain C constructs in C++ code. E.g. if someone in my programming team was to use malloc etc without very good reason in a C++ program, they would be rewriting the code. The languages are only superficially similar in a technical sense.

C++ is an extension to C. It's C further developed to give it object oriented capabilities. That said they are two completely different languages and should not be referred to in anyway the same. I'd only use C/C++ if I'm using the "/" as an AND/OR like saying "he knows how to program in C/Java". Which is what the OP may have been referring to.

---

### Post by snip3r8 on 2011-09-04
> **akand074 said:**
> C++ is an extension to C. It's C further developed to give it object oriented capabilities. That said they are two completely different languages and should not be referred to in anyway the same. I'd only use C/C++ if I'm using the "/" as an AND/OR like saying "he knows how to program in C/Java". Which is what the OP may have been referring to.

Here:
> when i posted C/C++ i meant C or C++

---

### Post by LinuxSavedMyComputer on 2011-09-04
It is essentially an imitation of C++ and Java, and as such it has Java's ridiculously long names.

---

### Post by karlson on 2011-09-05
> **snip3r8 said:**
> This is basically a discussion thread.

I am currently taking a C# coarse and Im finding that the language is a tad strange at some parts ,for example im now on .net remoting and the size of the namespaces! System.OMG.These.Namespaces.Are.Long; seems to be an acceptable length for a namespace

So i just want to see who else finds the language strange(particularly if you are used to c/c++).

May be I spent too much time in New York that I find nothing strange.  Every programming language has a need to solve a particular problem and does it in a best way the designer knows how.  And as such no programming language is weirder then the other.

---

### Post by hakermania on 2011-09-05
> **NovaAesa said:**
> I have to respectfully disagree with Herb Schildt. While technically C is a (near) subset of C++, you *shouldn't* be using certain C constructs in C++ code. E.g. if someone in my programming team was to use malloc etc without very good reason in a C++ program, they would be rewriting the code. The languages are only superficially similar in a technical sense.

What's an alternative to malloc for c++ ?

---

### Post by disabledaccount on 2011-09-05
> **hakermania said:**
> What's an alternative to malloc for c++ ?
C++ doesn't have equivalent for malloc() - sometimes people say that equivalent is "new", but it's not true. malloc() is low level buffer allocator while new is semi-automatic object allocator.

---

### Post by hakermania on 2011-09-05
> **tomazzi said:**
> C++ doesn't have equivalent for malloc() - sometimes people say that equivalent is "new", but it's not true. malloc() is low level buffer allocator while new is semi-automatic object allocator.

So why not to use malloc in C++ code?

---

### Post by nvteighen on 2011-09-05
Wait, why are we discussing C++ when the thread is about C#?

For the record:
Ok, people use language in a way they find appropriate, not necessarily the one which reflects the true nature of things. We keep talking about "atoms", even though we know they can be divided... or we consider tomatoes a "vegetable" when it's actually a fruit, from a biological point of view. The same goes for "C/C++"... ok, it may nerve me as well as Bachstelze, but it has a useful meaning for people even if I cannot tell exactly what it is. But that it serves its purpose is clear from the fact that people use it and understand eachother.

Do not discuss names, discuss facts. As long as you know that "C/C++" isn't a language and that C++ isn't C, it's fine for me, even though I've never used that expression nor will.

(This is what you get from a linguist like me... :P)

---

### Post by PaulM1985 on 2011-09-05
> **snip3r8 said:**
> 
I am currently taking a C# coarse and Im finding that the language is a tad strange at some parts ,for example im now on .net remoting and the size of the namespaces! System.OMG.These.Namespaces.Are.Long; seems to be an acceptable length for a namespace

I don't really see the namespace thing as an issue.  Isn't
System.Runtime.Remoting.Channels.Tcp;
better than:
Sys.Rnt.RMG.CHNL.TCP
?

At least the names of the namespaces are descriptive and you have a good idea what are going to be contained in them.  

Additionally, you are probably only going to have that line in your file once at the top as part of a using statement.  You are never in practice going to want to use this line during the file.  The only issue that could come up is if you have classes with clashing class names.  For example (and I am making up classes here, they might not exist), if you needed to use a Manager class which is defined in TCP and UDP, which were defined as:
System.Runtime.Remoting.Channels.Tcp.Manager
and
System.Runtime.Remoting.Channels.Udp.Manager

You could use aliasing to distinguish between the two and have:
using TcpManager = System.Runtime.Remoting.Channels.Tcp.Manager;
using UdpManager = System.Runtime.Remoting.Channels.Udp.Manager;

Paul

---

### Post by MadCow108 on 2011-09-05
namespaces tend to get long for complex libraries.
e.g. random finds with google:
python:
import twisted.words.protocols.irc
or java:
import java.rmi.registry.LocateRegistry;
or c++ (boost)
using local::stream_protocol::socket

as long as you can alias it (which you can) and there is a reason for the long names (= organizing stuff) its no reason to consider it a language strange.

---

### Post by Arndt on 2011-09-05
> **karlson said:**
> May be I spent too much time in New York that I find nothing strange.  Every programming language has a need to solve a particular problem and does it in a best way the designer knows how.  And as such no programming language is weirder then the other.

I do remember Snobol and TECO as at least slightly weird.

Along another dimension, some languages are more well-thought-out than others.

---

### Post by ve4cib on 2011-09-05
> **snip3r8 said:**
> This is basically a discussion thread.

I am currently taking a C# coarse and Im finding that the language is a tad strange at some parts ,for example im now on .net remoting and the size of the namespaces! System.OMG.These.Namespaces.Are.Long; seems to be an acceptable length for a namespace

So i just want to see who else finds the language strange(particularly if you are used to c/c++).

I've never found C# particularly strange.  Wrapping my brain around some of the ASP.NET stuff was tricky, but that was because I had zero experience or training with web programming prior to getting a job where it was required knowledge.  But C# itself seems quite nice to me.

I especially like the way C# handles get/set methods.

```

private string m_name;
...
public string Name
{
    set {this.m_name = value;}
    get {return this.m_name};
}

```

is much easier to me than the Java equivalent:

```

private String m_name;
...
public string getName() {return this.m_name;}
public void setName(String value) {this.m_name = value;}

```

Yes, this is a trivial example, but you can see the general trend of what I mean.  Being able to simply use the = operator to call the set method, instead of typing out a big function call is not only faster, but makes more sense visually to me.

As for the namespaces being lengthy, that's where the "using" keyword comes in handy.  Like someone mentioned in a previous post, you can define your own shorthand names for classes in specific namespaces if necessary.  Or if you don't have any classes with conflicting namespaces you can simply include the entire namespace as you would in C++.

---

### Post by snip3r8 on 2011-09-05
C# is generally nice to me but sometimes it just doesnt like Boolean values in its if statements.

---

### Post by cgroza on 2011-09-05
> **snip3r8 said:**
> C# is generally nice to me but sometimes it just doesnt like Boolean values in its if statements.
Could you elaborate please?

---

### Post by snip3r8 on 2011-09-05
For example

```

bool check = true;

for(int i =0;i < 2;i++)
{
         check = !check;
         if(check)
         {
                 Console.WriteLine("Hello World");
         }
}


```

this will print "Hello World" twice (but only sometimes).

---

### Post by PaulM1985 on 2011-09-05
> **snip3r8 said:**
> For example

```

bool check = true;

for(int i =0;i < 2;i++)
{
         check = !check;
         if(check)
         {
                 Console.WriteLine("Hello World");
         }
}


```

this will print "Hello World" twice (but only sometimes).

This claim was amazing.  So amazing I downloaded Monodevelop to try it myself!

Here is my code:
```

using System;

namespace Test
{
	class MainClass
	{
		public static void Main (string[] args)
		{
			int wrong = 0;
			for (int j = 0; j < 500000; j++)
			{
				bool check = true;

				int testVal = 0;
				for(int i =0;i < 2;i++)
				{
					check = !check;
					if(check)
					{
						testVal++;
					}
				}
				
				if (testVal == 2)
				{
					wrong++;
				}	
			}
			
			Console.WriteLine("There were " + wrong + " wrong");
		}
	}
}

```

This prints:
```

There were 0 wrong

```

Which is exactly what I would expect.  I can't make it do the weird stuff you mentioned.

Paul

---

### Post by cgroza on 2011-09-05
I don't know how true that statement was, but a language that does random things like that is not reliable.

---

### Post by PaulM1985 on 2011-09-05
True. I guess in addition you have to consider is the bytecode being compiled incorrectly or is the runtime interpretting it wrongly. Either way, it works fine on my Pc.

Paul

---

### Post by snip3r8 on 2011-09-06
> **PaulM1985 said:**
> This claim was amazing.  So amazing I downloaded Monodevelop to try it myself!

Here is my code:
```

using System;

namespace Test
{
    class MainClass
    {
        public static void Main (string[] args)
        {
            int wrong = 0;
            for (int j = 0; j < 500000; j++)
            {
                bool check = true;

                int testVal = 0;
                for(int i =0;i < 2;i++)
                {
                    check = !check;
                    if(check)
                    {
                        testVal++;
                    }
                }
                
                if (testVal == 2)
                {
                    wrong++;
                }    
            }
            
            Console.WriteLine("There were " + wrong + " wrong");
        }
    }
}

```This prints:
```

There were 0 wrong

```Which is exactly what I would expect.  I can't make it do the weird stuff you mentioned.

Paul


It only does it in visual studio , I think its the Visual Studio compiler because its even happened to me in C++ one time. Microsoft...

---

### Post by PaulM1985 on 2011-09-06
> **snip3r8 said:**
> It only does it in visual studio , I think its the Visual Studio compiler because its even happened to me in C++ one time. Microsoft...

Using Microsoft Visual Studio 2010 and .NET 4.0 on Windows 7, I still can't reproduce the issue you are talking about.

I think C# is a good language.  I have found it to be quite reliable and easy to use, especially moving to it from a Java background.  It's ability to use C and C++ code also makes it great for building on top of old systems with "tried and tested" libraries without having to re-write stuff for a new programming language/technology.

Paul

---

### Post by JupiterV2 on 2011-09-06
Rather than start a new thread I thought this might be a good place to ask this opinion question: Though C# is an OS agnostic language due to the Mono project, is there any concern of "vendor lock-in" with the language? Especially concerning it's relation to the .Net framework which was designed to be Windows-only? Does the legal shadow over the project worry anyone? I've always avoided C# for this reason but I wonder if it's FUD spread by the FOSS community or are the worries well founded?

---

### Post by PaulM1985 on 2011-09-06
I think that possibly there may be some issue.  As the language (or rather Windows implementation) grows it may be that open source projects can't keep up with the rate of growth.  This has already happened in the Mono project in that they have said that they will not be providing support for Windows Presentation Framework (WPF) which is a new way of developing user interfaces in .NET.

Paul

---

### Post by snip3r8 on 2011-09-06
> **JupiterV2 said:**
> Rather than start a new thread I thought this might be a good place to ask this opinion question: Though C# is an OS agnostic language due to the Mono project, is there any concern of "vendor lock-in" with the language? Especially concerning it's relation to the .Net framework which was designed to be Windows-only? Does the legal shadow over the project worry anyone? I've always avoided C# for this reason but I wonder if it's FUD spread by the FOSS community or are the worries well founded?

I have heard that Microsoft actually helped out a lot with mono ,so I'm not worried.

---

### Post by karlson on 2011-09-06
> **JupiterV2 said:**
> Though C# is an OS agnostic language due to the Mono project, is there any concern of "vendor lock-in" with the language?


I don't think so although the stigma exists in addition the development of the language and hence its standardization is done almost entirely by Microsoft, who only supports it's own operating system..  (I am still surprised that Office for Mac exists).

> 
Especially concerning it's relation to the .Net framework which was designed to be Windows-only?


That got nothing to do with the programming language per-se just as it was designed for it.

> Does the legal shadow over the project worry anyone?

Not sure what legal shadow you are referring to?

> I've always avoided C# for this reason but I wonder if it's FUD spread by the FOSS community or are the worries well founded?

The reason is mostly stigma but in addition as far as I can tell C# standard is only 5 years and non-Microsoft specific C# libraries and toolkits are few so why switch to use C# on Linux/Solaris/MacOS etc, when you can use C/C++ or Objective-C on a Mac, which have 20-30 years under their belts and quite a bit of tools already written?

The only way I could see mass acceptance of C# as a development platform on Linux for example is that there is a significant push from a major commercial player that does its own software development to dump Microsoft as a desktop platform of choice and even then I see better chance of using Java then C#.

---

### Post by karlson on 2011-09-06
> **snip3r8 said:**
> I have heard that Microsoft actually helped out a lot with mono ,so I'm not worried.

With what exactly?

---

### Post by snip3r8 on 2011-09-06
Didnt get that much detail but... [http://techrights.org/2009/06/05/embrace-extend-and-monodevelop/](http://techrights.org/2009/06/05/embrace-extend-and-monodevelop/)

...looks interesting

---

### Post by JupiterV2 on 2011-09-06
> **karlson said:**
> Not sure what legal shadow you are referring to?

I refer to patent or IP/Copyright infringements on the part of the Mono project. While I believe Microsoft has expressed that they have no intention of pursuing Mono on those grounds (I may be mistaken here) but that doesn't mean they won't.

---

### Post by karlson on 2011-09-06
> **JupiterV2 said:**
> I refer to patent or IP/Copyright infringements on the part of the Mono project. While I believe Microsoft has expressed that they have no intention of pursuing Mono on those grounds (I may be mistaken here) but that doesn't mean they won't.

But that sort of is the point.  The use of closed source patented technology reduces portability and while that has nothing to do with C# it reduces it's usability since it was designed and continues to be designed specifically for the purpose of .NET...

---

### Post by alegomaster on 2011-09-06
> **snip3r8 said:**
> It only does it in visual studio , I think its the Visual Studio compiler because its even happened to me in C++ one time. Microsoft...

Isn't that how Microsoft always is....:twisted:

---

### Post by directhex on 2011-09-07
> **snip3r8 said:**
> Didnt get that much detail but... [http://techrights.org/2009/06/05/embrace-extend-and-monodevelop/](http://techrights.org/2009/06/05/embrace-extend-and-monodevelop/)

...looks interesting

Consider the source. That site has less than zero credibility. Every claim on it should be assumed to be a lie.

---

### Post by directhex on 2011-09-07
> **snip3r8 said:**
> im now on .net remoting and the size of the namespaces! System.OMG.These.Namespaces.Are.Long; seems to be an acceptable length for a namespace

You're not paying by the byte. Source code should be human-readable. Meaningful namespaces are part of that.

---

### Post by snip3r8 on 2011-09-07
> **directhex said:**
> Consider the source. That site has less than zero credibility. Every claim on it should be assumed to be a lie.
True,they do seem a bit crazy

---

### Post by nvteighen on 2011-09-07
> **directhex said:**
> Consider the source. That site has less than zero credibility. Every claim on it should be assumed to be a lie.

LOL... that's a typical 'conspiranoic' website whose audience thinks to be right just because they're a minority.

EDIT: Minorities might be right. But if they're right, it's because their ideas are... not just because they're "non-mainstream". That's my point.

---

