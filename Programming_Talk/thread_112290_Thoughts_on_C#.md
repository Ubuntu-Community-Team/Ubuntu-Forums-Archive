---
title: "Thoughts on C#?"
date: 2006-01-04
forum: Programming Talk
---

### Post by Jessehk on 2006-01-04
Yes, I know C# is a Windows only language, but having been able to make programs on Ubuntu with mono, I can say that Microsoft did a great job. 

Coming from C++ (just as a hobby, I am still a student), I really like the style of C#, and the extensive documentation that MSDN provides. 

As a(n amateur) programmer, I have come to realize that 99% of home-consumers use Windows. And if you want to write a program that people will use, being forced to write Windows programs is inevitable. Of course, with C# on hand, I'm not complaning! :D

What are your thoughts? (Compared to C++, Java, etc)

EDIT: Just a small sample of code I wrote

```


using System;

namespace Jesse {
	class Guess {
		private int number;
		private int attempts = 0;

		public Guess() {
			Random rand = new Random();
			number = rand.Next(1, 100);
		}

		public bool makeGuess(int guess) {
			++attempts;
		
			try {
				if(guess > 100 || guess < 0)
					throw new Jesse.RangeException();
			
				if(guess > number)
					Console.WriteLine("Too high!");
				else if(guess < number)
					Console.WriteLine("Too low!");
				else {
					Console.WriteLine("Correct!");
					return true;
				}
			}
			catch(Jesse.RangeException re) {
				Console.WriteLine(re.Message);;
			}

			return false;
		}

		public int Number {
			get {
				return number;
			}
		}
		
		public int Attempts {
			get {
				return attempts;
			}
		}

		public static void Main() {
			Guess g = new Guess();

			bool done = true;
			do {
				Console.Write("Enter guess <1 to 100>: ");
				while(true) {
					try {
						int guess = int.Parse(Console.ReadLine());
						if(g.makeGuess(guess))
							done = false;
					}

					catch(FormatException fe) {
						Console.WriteLine( "{0} Input must be a valid integer.", fe.Message);
					}

					catch(OverflowException oe) {
						Console.WriteLine("Invalid input. {0}", oe.Message);
					}

					break;
				}

			} while(done);

			Console.WriteLine("You guessed the number {0} in {1} guesses!", g.Number, g.Attempts);
		}
	}
	
	public class RangeException : Exception {
		private string message = "Invalid range! Guess must be between 1 and 100.";
			
		public override string Message {
			get {
				return message;
			}
		}
	}
}


```

---

### Post by Jungles on 2006-01-04
I taught myself C# just after graduating from uni, where I spent most of my time programming in Java and C.

Previously, I thought C# was a solution looking for a problem.  But now I realise that it is a legitimate and useful language in its own right.  It definitely eases the transition from Windows platform C++ to programming in the .NET framework, which will become inevitable when Longhorn is released.

Absolutely a language worth delving into.  In Australia, C# language skills are second to Java, for programming skills in demand.  .NET takes a marginal lead over Java/J2EE.

---

### Post by Bealer on 2006-01-04
I use both C# and Java. I've always like both and have been totally brought up on OO programming. I wish I could take the time to learn some C++!

C# though is great, I find the whole .Net environment very well thoughout, and easy to use. I have to use Visual Studio at work, but when learning .Net, I learned quickly just because it was so easy and accessible to pickup/develop in. 

The only pain is that I'm stuck between the Linux and Windows world in that I rely on both. .Net is quite common here (UK). We've got clients such as Microsoft, Natwest, Unilever, Intel, HP, etc... so it's worth learning and will be around for quite some time.

I'd personally like to get into J2EE a little more as it's used a lot in the financial part of the market, although I only really have time enough to learn/master one language, so .Net it is.

---

### Post by fastluck on 2006-01-04
C# is 50% of the code I maintain, and 90% of the new code I write.  As a language, it's awesome.  But every once in awhile, I run into academic language features that kill two days.  For example, yesterday:  I created a form and put a dbGrid on the form.  Then I loaded my data into it.  I don't use bound controls, so it was all code.  But the code was easy to write.

Then I tried to figure out how to resize ONE column programmatically without resizing the others.  Guess what?  Can't be done.  You have to write a crapload of code to make that very simple thing happen.  This is the exact same thing I ran into a year ago when I was building a Java gui for a customer.  It's my understanding that .NET 2.0 fixed that particular problem.  But that's not good enough. The more code I write, the further behind I fall sometimes.

What's interesting is that when the app is running I can easily resize a column.  But not from my own code.

I'm sick of it.

---

### Post by m87 on 2006-01-04
[quote=Jessehk]Yes, I know C# is a Windows only language, but having been able to make programs on Ubuntu with mono, I can say that Microsoft did a great job. 

Coming from C++ (just as a hobby, I am still a student), I really like the style of C#, and the extensive documentation that MSDN provides. 

As a(n amateur) programmer, I have come to realize that 99% of home-consumers use Windows. And if you want to write a program that people will use, being forced to write Windows programs is inevitable. Of course, with C# on hand, I'm not complaning! :D

What are your thoughts? (Compared to C++, Java, etc)
[/quote]

C# is actually an ISO/ECMA standard, therefore not a "Windows only language", and of course mono is not a porting but an IMPLEMENTATION...

Personally speaking, I don't think I would need to build some software optimized for windows users (that's why firefox on GNOME still SUCKS), mostly because free software should put the priority over free platforms, therefore I would choose at first some language that is well supported on my system (C and python are the best choices, even over C++, mostly because C++ can wrap around C losing most of the OOP facilities with some libs, while python can wrap perfectly, also, if you look at gtkmm and pygtk, I guess you'll find gtkmm's event handling a bit confusing).

Speaking of mono, well... I used to like mono a lot. Unfortunately it still lacks lots of useful libraries, but that's not the main problem. The main problem is the garbage collector that sucks BAD ASS when it comes to heavy load. For example, Banshee Music Player is quite a cool program, it's got a nice UI and some cool functions (it's VERY YOUNG). BUT, what about my 13.000 tracks library? No way to handle it for more than 10 minutes. And beagle suffers from the same disease, and so do other programs. Surprise f-spot doesn't... probably because, as they said, performance-oriented parts of code are written in C :)

I would definitely choose Python and being in the last year of high school I feel I've wasted lots of time not having tried it before. Of course if your priority is cross-platform programming, Python may not be the best choice (as opposed to Java and .net), but still, definitely worth a try!

~marco

Oh and if you want to use mono, I think you should give [Nemerle]("http://nemerle.org") a try.

---

### Post by LordHunter317 on 2006-01-04
[QUOTE=m87]C# is actually an ISO/ECMA standard, therefore not a "Windows only language",[/quote]The standard is of course, also totally useless when talking about any real applications and doesn't include the majority of the .NET framework.

> and of course mono is not a porting but an IMPLEMENTATION...It could easily be considered both.  There isn't a worthwhile semantic distinction to make here, at any rate.

> Personally speaking, I don't think I would need to build some software optimized for windows users (that's why firefox on GNOME still SUCKS),No, it's really not.  There are many issues as to why Firefox is less performing on Linux than Windows.  Windows-specific optimizations are just one issue.  There are others.

> mostly because free software should put the priority over free platforms,What?  This statements makes no sense.

> therefore I would choose at first some language that is well supported on my system (C and python are the best choices, even over C++, mostly because C++ can wrap around C losing most of the OOP facilities with some libs, while python can wrap perfectly, also, if you look at gtkmm and pygtk, I guess you'll find gtkmm's event handling a bit confusing).This also makes little sense.  Language has *almost nothing* to do with cross-platform portability.  APIs are far more important.

Though at any rate, writing portable pure C that does anything useful is far more trouble than it's worth, especially for GUI applications.  It's just too hard to make useful abstractions.  GUI programming in C is generally terrible anyway.

> Surprise f-spot doesn't... probably because, as they said, performance-oriented parts of code are written in C :)No, that doesn't have anything to do with it.  You're impacting far more meaning to language than you should.

I've seen systems written in Java that are far more scalable than equivalent C systems.    I've seen the opposite.

---

### Post by m87 on 2006-01-04
[quote=LordHunter317]The standard is of course, also totally useless when talking about any real applications and doesn't include the majority of the .NET framework. [/quote]

Who cares. It includes the System namespace and lots of language definition, and of course it's NOT useless when talking about _real_ applications. Unless you're talking about apps that need external wrappers, most popular gtk# apps are a clear example

> No, it's really not.  There are many issues as to why Firefox is less performing on Linux than Windows.  Windows-specific optimizations are just one issue.  There are others.

Firefox being more optimized on Windows than on Linux/GNOME is not an opinion, it'a a matter of fact, and I'm not the only one who thinks so.

> This also makes little sense.  Language has *almost nothing* to do with cross-platform portability.  APIs are far more important.

Good vocabulary, but I didn't mention "cross-platform" and "API", speaking of Python and C, you can re-read the bit you quoted if you don't believe it :) I was talking about *how Python fits well in my OS*, full stop.

> Though at any rate, writing portable pure C that does anything useful is far more trouble than it's worth, especially for GUI applications.  It's just too hard to make useful abstractions.  GUI programming in C is generally terrible anyway.

Honestly, this is the only thing I agree

> I've seen systems written in Java that are far more scalable than equivalent C systems.    I've seen the opposite.

And I'm not denying this :)

Anyway, I wasn't flaming you, it's just a forum and these are just "opinions" or "thoughts" or whatever they are, calm down.

~marco

---

### Post by LordHunter317 on 2006-01-04
[QUOTE=m87]Who cares. It includes the System namespace[/quote]It includes a trivally small part of the System namespace.  It doesn't include System.Windows.Forms or anything *useful*.  It includes the classes necessary to define the language types, and a clas library on the level of ANSI C and that's really it.

> and lots of language definition, and of course it's NOT useless when talking about _real_ applications. Unless you're talking about apps that need external wrappers, most popular gtk# apps are a clear exampleShow me where GTK# is part of the standard.  It isn't.  The standard by itself is quite useless.

> Firefox being more optimized on Windows than on Linux/GNOME is not an opinion, it'a a matter of fact, and I'm not the only one who thinks so.I didn't argue that.  What I said was it's *not the only reason* that Firefox is slow on Linux.  There are other issues too, like that the dynamic linker on Linux isn't very fast, and it has more work to do on Windows.

> Good vocabulary, but I didn't mention "cross-platform" and "API", speaking of Python and C, you can re-read the bit you quoted if you don't believe it :) I was talking about *how Python fits well in my OS*, full stop.I didn't see any other way to interpret your statements, since you started talking about the platform-neutrality of C#.  My apologies.

> Anyway, I wasn't flaming you, it's just a forum and these are just "opinions" or "thoughts" or whatever they are, calm down.The problem is that many of them aren't actually opinions, but have basis in fact.  This is just a cop-out response and to be honset (this isn't directly solely at you) I'm sick of people using this as a defense.  Not everything you've said is an opinion, after all.

---

### Post by m87 on 2006-01-04
[quote=LordHunter317]It includes a trivally small part of the System namespace.  It doesn't include System.Windows.Forms or anything *useful*.  It includes the classes necessary to define the language types, and a clas library on the level of ANSI C and that's really it.[/quote]

Yeah, that's it, should a language specification include modules to make you some kind of coffeemaker or rocket to Neptune?

> Show me where GTK# is part of the standard.  It isn't.  The standard by itself is quite useless.

WHAT?? gtk# part of the standard? Who said that?

> I didn't argue that.  What I said was it's *not the only reason* that Firefox is slow on Linux.  There are other issues too, like that the dynamic linker on Linux isn't very fast, and it has more work to do on Windows.

Wrong reply then.

> The problem is that many of them aren't actually opinions, but have basis in fact.  This is just a cop-out response and to be honset (this isn't directly solely at you) I'm sick of people using this as a defense.  Not everything you've said is an opinion, after all.

I'm not using anything as a defense, and opinions/thoughts/facts, does it really matter? I don't think I have to feel sorry as I haven't offended anyone :)

~marco

---

### Post by LordHunter317 on 2006-01-04
[QUOTE=m87]Yeah, that's it, should a language specification include modules to make you some kind of coffeemaker or rocket to Neptune?[/quote]Potentially, yes.  Certainly the C++ Standards committe is intending on adding all sorts of useful things (Large portions of boost, a GUI, networking).  Java's standard class library has all these things where ECMA C# does not.

That doesn't mean a language must include such things but everything I've used C# for goes way beyond the standard.

> WHAT?? gtk# part of the standard? Who said that?You mentioned GTK# applications as proving the standard is useful.  That can only be logically possible of GTK# is part of the standard, and it isn't.  


> I'm not using anything as a defense, and opinions/thoughts/facts, does it really matter?Yes, it rather does.  If facts are at the level of an opinion, then I'm not stupid for saying '2+2=5', because I feel that's how it ought to be.

---

### Post by m87 on 2006-01-04
[quote=LordHunter317]Potentially, yes.  Certainly the C++ Standards committe is intending on adding all sorts of useful things (Large portions of boost, a GUI, networking).  Java's standard class library has all these things where ECMA C# does not.[/quote]

I guess that System.Net and System.Collections are part of the standard System namespace, while C++ as far as I know hasn't got a standard implementation for signals, i.e., and it has the same level of implementation for data structures. Anyway, this whole stuff is far off the thread we've monopolized, I'm out :)

---

### Post by Jessehk on 2006-01-05
My general impression is that programmers like C# as a language, but don't like it because it is (mostly) bound to Windows. Would I be correct in thinking that?

---

### Post by m87 on 2006-01-05
[quote=Jessehk]My general impression is that programmers like C# as a language, but don't like it because it is (mostly) bound to Windows. Would I be correct in thinking that?[/quote]
You fully are. I have recently become one of those, but of course that's not the only reason :)

---

### Post by briancurtin on 2006-01-05
[QUOTE=m87's signature]i don't care what the layouts of your computers are, seriously.
insult me[/QUOTE]
i checked out that link in your signature and got a rough translation of the posting you made there, and you are a total jackass. graduate high school first before thinking you are "l33t" in anything at all.

---

### Post by LordHunter317 on 2006-01-05
[QUOTE=Jessehk]My general impression is that programmers like C# as a language, but don't like it because it is (mostly) bound to Windows.[/quote]Linux programmers obviously do not, and some members of the C# community that do Windows work do not (including people at MS, who are aware of Mono and do track it's progress, even if they don't contribute).  By and large, I suspect the fact that .NET is currently really only a Windows framework doesn't bother most people.  By that I mean they simply do not care one way or the other.

For most people, cross-platform features are irrelevant.  For many people developing on Windows, they still have to use very Windows-specific features like COM Interop for many tasks (including certain GUI things, rectified to a large degree in .NET 2.0) so they'd be stuck on Windows *anyway* even if most of .NET was portable.

Certainly on my current application, the website could conceptually run on Mono if the ASP.NET 2.0 stuff was fully up to snuff, but the GUI application is dependent on COM interop and would not function on Linux no matter what.

And my customers don't care about it being Windows only so I honestly don't care either.  It doesn't affect me getting paid. 

That being said, I would love to be able to run ASP.NET on Linux hosted machines, and provide that as a customer solution, especially for those looking to avoid licensing costs.  Mono is alas, not up to the task yet, even for simple serving.

Certainly though, it's not something that stops me from writing .NET solutions, and even Windows-specific ones, though I wish I could leverage Linux further.

---

### Post by m87 on 2006-01-05
[quote=LordHunter317]Linux programmers obviously do not, and some members of the C# community that do Windows work do not (including people at MS, who are aware of Mono and do track it's progress, even if they don't contribute).  By and large, I suspect the fact that .NET is currently really only a Windows framework doesn't bother most people.  By that I mean they simply do not care one way or the other.

For most people, cross-platform features are irrelevant.  For many people developing on Windows, they still have to use very Windows-specific features like COM Interop for many tasks (including certain GUI things, rectified to a large degree in .NET 2.0) so they'd be stuck on Windows *anyway* even if most of .NET was portable.

Certainly on my current application, the website could conceptually run on Mono if the ASP.NET 2.0 stuff was fully up to snuff, but the GUI application is dependent on COM interop and would not function on Linux no matter what.

And my customers don't care about it being Windows only so I honestly don't care either.  It doesn't affect me getting paid. 

That being said, I would love to be able to run ASP.NET on Linux hosted machines, and provide that as a customer solution, especially for those looking to avoid licensing costs.  Mono is alas, not up to the task yet, even for simple serving.

Certainly though, it's not something that stops me from writing .NET solutions, and even Windows-specific ones, though I wish I could leverage Linux further.[/quote]

I agree, but I guess that some .net solutions are not appreciated (asp.net is not the most supported in the free software community) because they are like "a microsoft product", as i.e. vb.net and asp.net are not a standard specification or so. Maybe this is one of the reasons why mono doesn't support asp.net well...

The matter of cross-platform portability is quite tricky. Some people who write applications just think about compatibility between WinXP and Win98 :) It sounds like a joke, but in my area people use nothing but Windows, even Mac's are quite rare, and I've seen different kinds of "solutions" written for Windows which totally lack portability, and this is just because "they don't need it"...

Anyway seeing Mono spreading among the enterprises is good news, although I don't know when/if this will really mean something.

~marco

---

### Post by LordHunter317 on 2006-01-05
[QUOTE=m87]I agree, but I guess that some .net solutions are not appreciated (asp.net is not the most supported in the free software community)[/quote]That's because it's not visible to end-users, but it's easily the most wortwhile thing to work on in .NET.

And the basics are supported just fine, though a lot of the backend stuff for a modern web applciation isn't 100% up to par.  The problem is mono can't perform well enough to handle even a small load, due to GC issues.

> Some people who write applications just think about compatibility between WinXP and Win98 :)Some don't even worry about that, because they don't have to.  And there's rarely a point in writing cross-platform code unless you need it.

---

### Post by m87 on 2006-01-05
[quote=LordHunter317]The problem is mono can't perform well enough to handle even a small load, due to GC issues.[/quote]

Yeah I pointed that. I wonder when they'll fix this, I think it's some kind of high priority rather than adding a CLI plugin to gcc :) (there was a summer of code bounty for that)

---

### Post by Viro on 2006-01-09
[QUOTE=LordHunter317]
And the basics are supported just fine, though a lot of the backend stuff for a modern web applciation isn't 100% up to par.  The problem is mono can't perform well enough to handle even a small load, due to GC issues.[/QUOTE]

Do you have any numbers to back up the claim that the GC is what makes Mono slow? I have seen none so far.

---

### Post by Viro on 2006-01-09
From reading through all the replies, I see that no one has brought up the main issue that I seem to have with Mono. That is, it lacks a good IDE and a debugger. Honestly, how can you write large scale applications without a functional debugger? MDB is coming along slowly, and until it is mature and is included in the default Mono distribution, it is hard for me to take Mono seriously.

Mono develop has a long way to go. Compare Monodevelop to Eclipse and you'll understand just how far it has to go before being a modern IDE. As it is, it doesn't have functionality that Visual Studio 6 (released in 1998) has, e.g. resource editor/GUI designer, integrated debugger, quick API reference. Compared to the current crop of IDEs, it lacks even more (code folding, automatic syntax checking, background compilation, quick fix).

In its current state, I see very little reason to use Mono. It is too similar to Java to make it stand out, and it suffers from the same performance problems that plague Java. At least, there are some decent IDEs for Java.

I won't go into the fact that some (not me, btw) view Mono as a potential patent time bomb. Suffice to say, Mono has a long way before being accepted by the majority of GNOME programmers and Linux programmers.

---

### Post by LordHunter317 on 2006-01-09
[QUOTE=Viro]Do you have any numbers to back up the claim that the GC is what makes Mono slow? I have seen none so far.[/QUOTE]I don't have to, it's common knowledge.

Besides, it's pretty easy to verify yourself.  You can force the GC to run and see how slow it is.

[quote=Viro]From reading through all the replies, I see that no one has brought up the main issue that I seem to have with Mono. That is, it lacks a good IDE and a debugger.[/quote]That's because a framework doesn't have to provide one, nor should it.  The Visual Studio Express editions aren't in the .NET framework... 

> Mono develop has a long way to go. Compare Monodevelop to Eclipse and you'll understand just how far it has to go before being a modern IDE.You want it to be buggy, broken, useless, illogical crap?  Eclipse is not the gold-standard.  It's not even close.  Lots of people think it is because it's free, but it's really just garbage.

> Compared to the current crop of IDEs, it lacks even more (code folding, automatic syntax checking, background compilation, quick fix).I would drop all of those features in Eclipse for a set of real, working, sane web development tools.

> In its current state, I see very little reason to use Mono. It is too similar to Java to make it stand out,I don't see how you can conclude in this, beyond the fact portions of the .NET framework class libraries are clearly ripped from Java.

.NET is a totally different runtime, you do know, right?

> and it suffers from the same performance problems that plague Java.No, it doesn't.  Mono's performance issues are due to it's young age, and nothing more.  Java isn't slow either, BTW.

---

### Post by Thirsteh on 2006-01-09
Why you argue that things made by Microsoft are awesome on a Linux forum is beyond me.

And yes, Java is slow compared to languages such as C, C++ and even Python. You can't even **start** arguing that fact.

---

### Post by LordHunter317 on 2006-01-09
[QUOTE=Thirsteh]Why you argue that things made by Microsoft are awesome on a Linux forum is beyond me.[/quote]Bceause the .NET framework is quite useful and wonderful for many applications, including those made on Linux.

> And yes, Java is slow compared to languages such as C, C++ and even Python.No, it isn't.  In some cases, it's even *faster* than traditional compiled languages.

And Python is byte-compiled interpreted, just like Java.  It's VM is more compact, but it's still overhead.  I'm not sure why you included it.  Me thinks you don't understand what you're saying, and you're just parroting stuff you've heard.

>  You can't even **start** arguing that fact.Yes, I can.  Just  Google "java faster than C" and have a party.

You can come up with mostly pathological cases to support either side.  A more moderate position would run useful tests and realize that generally, the differences are negligable or in the cases where they're not, there's no consistent winner.

---

### Post by Viro on 2006-01-09
[QUOTE=Thirsteh]Why you argue that things made by Microsoft are awesome on a Linux forum is beyond me.

And yes, Java is slow compared to languages such as C, C++ and even Python. You can't even **start** arguing that fact.[/QUOTE]

Absolute nonsense, especially when you throw Python into the mix. I do a lot of numerical analysis and from my experience, Java is close to C most of the time, and Python is far far slower than Java. Seriously, write some serious code in both languages, and then you'll realize that your 'facts' are nothing but hogwash.

---

### Post by Viro on 2006-01-09
[QUOTE=LordHunter317]
Besides, it's pretty easy to verify yourself.  You can force the GC to run and see how slow it is.
[/quote]

Progress is made when common knowledge is challenged. 

It will be slow, because you're forcing the runtime to go through **all** the allocated objects to see if any are unused. This is fundamentally different from how free/delete work in C/C++ and to compare them to the GC is an apples to oranges comparison. Such a test does not prove that the GC slows down the language. Instead, it shows you why all the programming guidelines say you should trust the runtime to know when to invoke the GC, and not liberally sprinkle System.gc() all throughout your code.

For performance speed ups in traditional compiled languages (like C/C++) due to a GC, look for testimonials from code that has switched to the Boehm GC and be amazed. 

> 
That's because a framework doesn't have to provide one, nor should it.  The Visual Studio Express editions aren't in the .NET framework... 


No, the framework doesn't need to provide one, but the framework is not used in isolation. The Mono runtime isn't practical for large applications unless it has a debugger. Whether it's a 3rd party who provides it or it's included as part of the framework (like in Python), who cares for it doesn't matter? The fact that it is absent matters.

> 
You want it to be buggy, broken, useless, illogical crap?  Eclipse is not the gold-standard.  It's not even close.  Lots of people think it is because it's free, but it's really just garbage.

I would drop all of those features in Eclipse for a set of real, working, sane web development tools.


Eclipse was just an example. Put your favorite IDE here, and by your raving about how buggy Eclipse is.... either that's fanaticism or you have something wrong with your config. Eclipse is not the be all end all of IDEs, which is probably why you find it unsuitable for web development (HTML? PHP? Javascript? GCI?).

> 
I don't see how you can conclude in this, beyond the fact portions of the .NET framework class libraries are clearly ripped from Java.


Please, there is practically a one-to-one mapping for the features in Java and C#. I wasn't even having in mind the .NET framework, since the scope of this discussion was the C# language. Compare Python to these languages and you'll see that it's different, not that it's always a good thing mind you. In terms of productivity, how much more productive will you be if you coded in C# instead of Java? My guess is, pretty much equal provided the supporting frameworks are of the same quality. Compare this with a language like Python, where the equivalent code is usually much shorter. This isn't a pimp for Python, but I mention it to demonstrate how similar C# and Java are.

> 
No, it doesn't.  Mono's performance issues are due to it's young age, and nothing more.  Java isn't slow either, BTW.

JITs sacrifice runtime footprint for execution speed. Java/Mono will run at speeds close to native code like C provided there is enough RAM. If you look at the memory consumption of a Java/Mono app, you'll see that it is usually about 2x the memory of a similar native app. You can see where this is going. The simple solution is to make sure your system has enough RAM, but what happens if you are working on a dataset that is almost the same size of your total system memory? Such a performance 'issue' will always be there when you are using a virtual machine.

---

### Post by LordHunter317 on 2006-01-09
[QUOTE=Viro]It will be slow, because you're forcing the runtime to go through **all** the allocated objects to see if any are unused.[/quote]No, you're not, unless you specifically ask for a sweep of all generations.

> This is fundamentally different from how free/delete work in C/C++ and to compare them to the GC is an apples to oranges comparison.I was never comparing it to C or C++, nor was anyone else in this thread.  AFAIK, all comparsions made by everyone (certainly my own) were against MS' .NET runtime, which doesn't have nearly as slow of a garbage collector.

> Such a test does not prove that the GC slows down the language.I never made that claim.

> No, the framework doesn't need to provide one, but the framework is not used in isolation.I realize, but I'd be more than happy with using MS tools for the most part and being able to *run* on Mono.  Which certainly reduces the number of debugging tools I need.

I'm not arguing that an IDE or a debugger shouldn't be provided by someone at some point, I'm just pointing out it's not the onus of the framework itself to do so.  More importantly, there are other, more important things to still be done at this point.

> Eclipse was just an example. Put your favorite IDE here, and by your raving about how buggy Eclipse is.... either that's fanaticism or you have something wrong with your config.No, I've used Eclipse on several projects.  It's crap.  The UI is inconsistent.  There's no way to force a project layout but trivally allow for people to have custom project configurations.  This is a PITA when some moron hardcodes a path and then checks in the project configuration, breaking other's systems.

There are too many views that in essence, do the same thing.  The views don't have consistent interfaces or use consistent dialogs. 

It's 'Ant Integration' is crap and was still very buggy until recently.  Some of this is Java's fault with it's classloader retardation, but not totally.

> Eclipse is not the be all end all of IDEs, which is probably why you find it unsuitable for web development (HTML? PHP? Javascript? GCI?).I was referring to J2EE development, specifically.

> Please, there is practically a one-to-one mapping for the features in Java and C#.Not in the least.  Java doesn't have anything that really rivals ASP.NET (not standard anyway, JSF is close but oh-so-far away).  Java's unsafe code features are far, far weaker.  There's no COM Interop.  

>  I wasn't even having in mind the .NET framework, since the scope of this discussion was the C# language.As I pointed out, in most practical discussions, it's usless to talk about C# with considering the framework as well.

> My guess is, pretty much equal provided the supporting frameworks are of the same quality.Which they're not.  You'd know this if you did any .NET programming.

>  If you look at the memory consumption of a Java/Mono app, you'll see that it is usually about 2x the memory of a similar native app. You can see where this is going.Wonderful, great even.  That doesn't *ipso facto* translate into performance problems.  It doesn't even come close.  It's borderline FUD.

> The simple solution is to make sure your system has enough RAM, but what happens if you are working on a dataset that is almost the same size of your total system memory? Such a performance 'issue' will always be there when you are using a virtual machine.It'll always be there when you're writing native code too, this is why we have operating systems and use virtual memory and paging, so we can handle these cases.  Non-sequitur, as the cases aren't different at all.

---

### Post by Viro on 2006-01-09
Hmm...
[quote=LordHunter317]
The problem is mono can't perform well enough to handle even a small load, due to GC issues.
[/quote]
[Quote=Viro]
Do you have any numbers to back up the claim that the GC is what makes Mono slow? I have seen none so far.
[/quote]
[quote=LordHunter317]
I don't have to, it's common knowledge.

Besides, it's pretty easy to verify yourself. You can force the GC to run and see how slow it is.[/quote]
[quote=Viro]
It will be slow, because you're forcing the runtime to go through all the allocated objects to see if any are unused. This is fundamentally different from how free/delete work in C/C++ and to compare them to the GC is an apples to oranges comparison. Such a test does not prove that the GC slows down the language.[/quote]
[QUOTE=LordHunter317]
I never made that claim.
[/quote]

Maybe I'm going senile here, but I'm fairly certain you made the claim that GC issues cause Mono to be slower. Perhaps I misunderstood you when you actually meant that a particular GC issue (i.e. bug) made Mono slower? However, you said to force the GC to run, hence the assumption that you implied that manual memory management was superior which led to the C/C++ comparison.

If I've misunderstood, you have my apologies. Sorry.

> 
I realize, but I'd be more than happy with using MS tools for the most part and being able to *run* on Mono.  Which certainly reduces the number of debugging tools I need.


Yes, and MS tools run on all platforms Mono runs on? Besides, Mono has two stacks, the .NET framework is just one stack. What if I'm interested in developing Gtk# which is far more likely, given Mono's target as a GNOME development platform?

> 
I'm not arguing that an IDE or a debugger shouldn't be provided by someone at some point, I'm just pointing out it's not the onus of the framework itself to do so.  More importantly, there are other, more important things to still be done at this point.


I suppose if you're using Windows tools on Windows, sure. But not all of us are doing that and it would be nice to have a workable IDE on the platforms where Mono ran on. Some of us would actually like to do some development for GNOME and not just target Windows.

> 
Not in the least.  Java doesn't have anything that really rivals ASP.NET (not standard anyway, JSF is close but oh-so-far away).  Java's unsafe code features are far, far weaker.  There's no COM Interop.  

Given that we're talking about languages here, how is ASP.NET and COM interop part of the language? That is *Non-sequitur* if I do say so myself. Nevertheless, I agree that unsafe code is different in C# and Java but the original point still stands. They are very similar and there is a one-to-one mapping for most language constructs in C# and Java. That is, if you looked at the parsers and grammars you would see that they were similar.

> 
As I pointed out, in most practical discussions, it's useless to talk about C# with considering the framework as well.


I agree, but there is not just the .NET framework, which is what you seem to be referring to all the time. What about GNOME#? This is Linux after all and most Linux developers are interested in churning out Linux applications.

> 
Wonderful, great even.  That doesn't *ipso facto* translate into performance problems.  It doesn't even come close.  It's borderline FUD.

It'll always be there when you're writing native code too, this is why we have operating systems and use virtual memory and paging, so we can handle these cases.  Non-sequitur, as the cases aren't different at all.

You seem to have missed the point of that illustration. Swapping to disk causes performance penalties (up to an order of 10 sometimes). With the additional overhead of the virtual machine, you will hit the swap faster (especially if the memory footprint of your app is 2x what is should be). That is why I brought up the case where a dataset that just about fits into the system memory. I have run into cases where the system started swapping with my Java code, but it still ran happily with native code. With native code, you can work with larger datasets before hitting the swap, hence you get better performance in most scenarios.

---

### Post by LordHunter317 on 2006-01-09
[QUOTE=Viro] Perhaps I misunderstood you when you actually meant that a particular GC issue (i.e. bug) made Mono slower?[/quote]Yes.  I don't know if it's just a long series of bugs or if their GC implementation is inferior to MS', but their GC is much slower than the one provided by MS.  This is trivally verifiable and well known.

>  However, you said to force the GC to run, hence the assumption that you implied that manual memory management was superior which led to the C/C++ comparison.No, I meant to provide your own benchmark.  

> Yes, and MS tools run on all platforms Mono runs on?No, but I don't need Visual Studio to run on Linux for my web application.  I just need Mono.

> Besides, Mono has two stacks, the .NET framework is just one stack. What if I'm interested in developing Gtk# which is far more likely, given Mono's target as a GNOME development platform?You can do that on Windows, for at least portions of the OSS libraries.  Not all of them, certainly.

But for me anyway, I'd like to be able to write web applications that run on both platforms, and potentially simple GUI supporting applications.  I'm not interested in desktop stuffs at all.

> Some of us would actually like to do some development for GNOME and not just target Windows.I realize.  I have little interest, but even conceding your needs, I still feel like Mono has more important things to worry about then a good IDE or debugger, at this point.  

It's still very young, after all.

> Given that we're talking about languages here, how is ASP.NET and COM interop part of the language?As I've said before, considering the languages without their respective frameworks is pointless.

No one writes Java without the provided APIs of J2SE or J2ME.  As such, *for practical purposes*,  discussing the languages without their frameworks is pointless.

>  They are very similar and there is a one-to-one mapping for all language constructs in C# and Java.No, OTTOMH for C#:[list][*]Real namespaces I can place how I want[*]Assemblies[*]Properties[*]More real generics[*]More complicated override system[*]Anonoymous methods[*]Delgates[*]Events[/list]None of those have language provided analogues in Java, you have to include the library.  Which brings me to my original point.

>  That is, if you looked at the parsers and grammars you would see that they were similar.All LALR parses look similar.  Heck, traditionally we had tools to generate the parses for us, and we still use them.  Non-sequitur.

> I agree, but there is not just the .NET framework, which is what you seem to be referring to all the time. What about GNOME#?Not nearly featureful enough to be a demand on it's own.  Or mature enough.

>  This is Linux after all and most Linux developers are interested in churning out Linux applications.And a lot of them are interested in writing ASP.NET as well.  You can't pretend they're exclusive, and for all intents and purposes, the .NET framework (well, large portions thereof) is more important.  There isn't going to be an OSS framework for .NET to replace ASP.NET anytime soon, for example.

I'll concede the desktop is different, but as I've already said, I could really care less.  That's not to say such things aren't important, but Mono is useless to me without a more or less fully working .NET framework.

> You seem to have missed the point of that illustration.I didn't, You missed the point of my response.

>  Swapping to disk causes performance penalties (up to an order of 10 sometimes).Native code isn't immune.

> With the additional overhead of the virtual machine, you will hit the swap faster (especially if the memory footprint of your app is 2x what is should be).Not true.  Modern operating systems are demand paged for code, and won't drop code pages actively in use unless they must.  And datasets where you must keep all the code and RAM in all the time are really small.  You can almost always toss a few pages.

If you can't, the VM overhead isn't likely to make much difference, in the end.  Oracle is native-code, but when you're out of RAM, you're just out.  

Code, even with a VM and all it's overhead, is a tiny part of the programs you're discussing anyway.  10-20 MiB makes little difference.

>  That is why I brought up the case where a dataset that just about fits into the system memory. I have run into cases where the system started swapping with my Java code, but it still ran happily with native code. With native code, you can work with larger datasets before hitting the swap, hence you get better performance in most scenarios.You can also trivally code such things to avoid these problems.  And native applications that work with large datasets generally use memory-mapped I/O and *depend on the paging behavior* to avoid these sorts of problems.

---

### Post by Viro on 2006-01-10
I suppose we are targeting different platforms, and hence have different needs. For ASP.NET, I can see Mono being a useful tool for MS shops intending to port their applications to Linux. However, as a Linux desktop development tool, it still has a long way to go.

---

### Post by asimon on 2006-01-10
[QUOTE=Viro]From reading through all the replies, I see that no one has brought up the main issue that I seem to have with Mono. That is, it lacks a good IDE and a debugger.[/quote]
That's absolutely right. My impression is that the thing most of the C#/.NET developers I know value the most is actually Visual Studio .NET. It's not C# as a language and or the extensive .NET APIs which bring them the most productivity, it's Visual Studio. Some have tried Mono but the lack of something equal to Visual Studio .NET for Linux made them all go back rather quickly.

---

### Post by sunzaru on 2008-02-10
I know this isn't really the right spot to post but,  the ubuntu forums are so far the MOST supportive forums i have ever found.

I have what "hopefully" has a quick answer.  I have seen DLLImport's here and there and they are fine and dandy.  IF you know what the DLL Method signature looks like.  

Question is.. how do you know what the dll signature is?  Is there a dll signature explorer or something that i could use?  Do i have to rely on other supplying the DLL's method signatures?

---

### Post by aks44 on 2008-02-10
> **sunzaru said:**
> I know this isn't really the right spot to post

<snipped question>

Since you know this thread was not the best place to post, why didn't you create a new thread for your specific question? ;)

---

### Post by cprofitt on 2008-02-10
> **fastluck said:**
> ...snip...
 
What's interesting is that when the app is running I can easily resize a column. But not from my own code.
 
I'm sick of it.
 
Not sure if this will help, but if you use the DataGridView you can do the following:
 
```

[SIZE=2]dataGridView1.Columns[0].Width = 90;
[/SIZE]
```
 
You can also make columns hidden (they can be 'key' fields but not visible), you can make column titles friendly names that the database names will not be.

---

### Post by YourSurrogateGod on 2008-02-10
> **PrivateVoid said:**
> Not sure if this will help, but if you use the DataGridView you can do the following:
 
```

[SIZE=2]dataGridView1.Columns[0].Width = 90;
[/SIZE]
```
 
You can also make columns hidden (they can be 'key' fields but not visible), you can make column titles friendly names that the database names will not be.

I wonder if that will work for ASP .NET as well...

---

### Post by cprofitt on 2008-02-10
> **YourSurrogateGod said:**
> I wonder if that will work for ASP .NET as well...
 
I am not sure... ASP.Net uses the GridView or DataList instead of the DataGridView.
 
My guess... sorry not at my Visual Studio machine right now...
 
would be
 
```

[SIZE=2]GridView1.Rows[1].Width = 95;

```
[/SIZE]

---

### Post by Jordanwb on 2008-04-03
I learned C# between grade 11 (C++) and grade 12 (Java). C# is my second favourate language (PHP is first). Java is near the bottom. VB is last.

---

### Post by LaRoza on 2008-04-03
> **Jordanwb said:**
> I learned C# between grade 11 (C++) and grade 12 (Java). C# is my second favourate language (PHP is first). Java is near the bottom. VB is last.

Odd mix, have you tried other paradigms?

---

### Post by bigoperm on 2009-02-24
Call me archaic, but I love working in Emacs and using the command line for program development. Can I do this with C#? The Emacs part is straightforward, but are there build tools that remove the need for GUI-based IDE's? I guess I could use make, but what about something more specialised, like ant/Java? Thanks

---

### Post by directhex on 2009-02-24
> **bigoperm said:**
> Call me archaic, but I love working in Emacs and using the command line for program development. Can I do this with C#? The Emacs part is straightforward, but are there build tools that remove the need for GUI-based IDE's? I guess I could use make, but what about something more specialised, like ant/Java? Thanks

There's a "nant" if you're used to working with that kind of thing

And also "xbuild" to build msbuild (Visual Studio) project files, for maximum Windows interoperability

Or you could just use good ol' autofoo (as most Mono apps do)

---

### Post by jimi_hendrix on 2009-02-24
C# is the language i learned with and i love it

i also thing XNA is pure brillience

---

### Post by Can+~ on 2009-02-24
Old post is old.

Oh, and I just noticed LaRoza's burnt beans.

---

### Post by MasterNetra on 2009-02-24
> **can+~ said:**
> ... Oh, and i just noticed laroza's burnt beans.

+1

---

### Post by wootah on 2009-02-24
> **MasterNetra said:**
> +1
 
How'd LaRoza get banned?! Last time I checked, he always provided good info :(

---

### Post by namegame on 2009-02-24
> **wootah said:**
> How'd LaRoza get banned?! Last time I checked, he always provided good info :(

That happened months ago.

[http://ubuntuforums.org/showpost.php?p=6155490&postcount=1310](http://ubuntuforums.org/showpost.php?p=6155490&postcount=1310)

You can also read his side of the story on his blog.

---

### Post by wootah on 2009-02-24
> **namegame said:**
> That happened months ago.
 
[http://ubuntuforums.org/showpost.php?p=6155490&postcount=1310](http://ubuntuforums.org/showpost.php?p=6155490&postcount=1310)
 
You can also read his side of the story on his blog.
 
Oops. My bad for bringing it up :(

---

