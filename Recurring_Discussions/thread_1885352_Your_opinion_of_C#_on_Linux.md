---
title: "Your opinion of C# on Linux"
date: 2011-11-23
forum: Recurring Discussions
---

### Post by Drenriza on 2011-11-23
So i surfed around the internet yesterday, but i don't remember what i was surfing for :p and i stumbled upon a thread saying

"Linux is better off, not using C# and getting to dependent on it"

As the thread was referring to that C# is a Microsoft technology. And as i remember C# has property code which they are not willing to share in the open-source world. Which also slows down the Mono project. Correct me if i'am wrong.

_**But what is your opinion in all of this?**_
Do you fear that Linux will get to dependent on C# and .NET? In the future.

Do you think C# and .NET should be a vital part of Linux if Microsoft would open for their use of the code? So it freely could be used.

Do you think you can write / create the same quality of code / programs on Linux with C# as with other programming languages?

Is their any other reasons you think C# should or shouldn't be more integrated with Linux.

Kind regards.

---

### Post by Tibuda on 2011-11-23
It is just a language like any other language.

Don't start that NIH stuff.

C# is an ECMA standard. Windows Forms is the C# library used for Windows GUI, but it is not used in Mono apps like Banshee, which use Gtk#.

---

### Post by Sef on 2011-11-23
Another what's your opinion on ....? Moved to Recurring Discussions.

---

### Post by Dragonbite on 2011-11-23
C# is a language, just like Java, Python, PHP, Perl, etc.

Some people argue that C# is a trojan horse for Microsoft.  I don't know enough about the relationship with Java & openJDK and Oracle as a point of reference.

C# is used in some of the default programs in Ubuntu (and Gnome in general).  Shotwell is written in Vala and Vala is a C#-like language. The difference is it compiles down differently than Mono does.

I use .NET at work and I appreciate that I could, at my option, use Mono to develop things at home too.  I just don't.  Part of that is because I am using ASP.NET, and part of that is because I'm using VB.NET instead of C#.  But the option is there.

---

### Post by haqking on 2011-11-23
> **Dragonbite said:**
> 
**Some people argue that C# is a trojan horse for Microsoft.** 

[IMG]http://3.bp.blogspot.com/_NURTFz-26UI/TD-nMlyXSNI/AAAAAAAABpA/OrGmuphDgNs/s1600/DoubleFacePalm.jpg[/IMG]

---

### Post by Dragonbite on 2011-11-23
> **haqking said:**
> [IMG]http://3.bp.blogspot.com/_NURTFz-26UI/TD-nMlyXSNI/AAAAAAAABpA/OrGmuphDgNs/s1600/DoubleFacePalm.jpg[/IMG]

Wha? Are you saying that nobody in these forums have ever insinuated that C# (actually Mono) is a Microsoft trojan horse?  Rather a number of posts flat-out say they think it is.

I didn't say *I* say it is a trojan horse.

---

### Post by haqking on 2011-11-23
> **Dragonbite said:**
> Wha? Are you saying that nobody in these forums have ever insinuated that C# (actually Mono) is a Microsoft trojan horse?  Rather a number of posts flat-out say they think it is.

I didn't say *I* say it is a trojan horse.

It wasnt directed at you but at the statement itself.

And these forums are full of insinuations and opinions.

My opinion is that of Jean Luc and Rikers ;-)

---

### Post by Dragonbite on 2011-11-23
> **haqking said:**
> It wasnt directed at you but at the statement itself.

And these forums are full of insinuations and opinions.

My opinion is that of Jean Luc and Rikers ;-)

Ah. Ok, sorry about that.

---

### Post by dniMretsaM on 2011-11-23
I don't think it's that big of a problem. However, I will try to avoid it when I get started with college/my career (software engineering) mainly because of the fact that many people don't like it. I was looking at a college the other day that used C# in it's courses and I decided not to go there. I also think C++ (the language most of the other colleges I'm looking at use) will be a more usefull language to me in the long run.

---

### Post by simpleblue on 2011-11-23
From wiki:
[http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.27s_patents](http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.27s_patents)
> Mono’s implementation of those components of the .NET stack not submitted to the [ECMA]("http://en.wikipedia.org/wiki/Ecma_International") for standardization has been the source of patent violation concerns for much of the life of the project.[[69]]("http://en.wikipedia.org/wiki/Mono_%28software%29#cite_note-68") In particular, discussion has taken place about whether Microsoft could destroy the Mono project through patent suits.[[70]]("http://en.wikipedia.org/wiki/Mono_%28software%29#cite_note-69") So far these concerns have proven to be unfounded.[[71]]("http://en.wikipedia.org/wiki/Mono_%28software%29#cite_note-70")
 The base technologies submitted to the ECMA, and therefore also the  Unix/GNOME-specific parts, are not problematic due to Microsoft's  explicitly placing both ECMA 334 and ECMA 335 standards under the [Microsoft Community Promise]("http://en.wikipedia.org/wiki/Microsoft_Community_Promise"). The concerns primarily relate to technologies developed by Microsoft on top of the .NET Framework, such as [ASP.NET]("http://en.wikipedia.org/wiki/ASP.NET"), [ADO.NET]("http://en.wikipedia.org/wiki/ADO.NET") and [Windows Forms]("http://en.wikipedia.org/wiki/Windows_Forms") (see [non-standardized namespaces]("http://en.wikipedia.org/wiki/Base_Class_Library#Non_standardized_namespaces")),  i.e. parts composing Mono’s Windows compatibility stack. These  technologies are today not fully implemented in Mono and not required  for developing Mono-applications, they are simply there for developers  and users who need full compatibility with the Windows system.
 Should patent issues ever arise, the Mono project's stated strategy for dealing with them is as follows:[[72]]("http://en.wikipedia.org/wiki/Mono_%28software%29#cite_note-71")
 
[LIST]
[*]Work around the patent by using a different implementation technique  that retains the API, but changes the mechanism; if that is not  possible, they would
[*]Remove the pieces of code that were covered by those patents, and also
[*]Find prior art that would render the patent useless.
[/LIST]

Mirosoft is trying to destroy Linux. We all know about the frivolous patents they have against Android... 

I think Microsoft is waiting for a few essential programs in Linux to use C# so they can start their crap.

---

### Post by Dragonbite on 2011-11-23
> **simpleblue said:**
> From wiki:
[http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.27s_patents](http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.27s_patents)

Mirosoft is trying to destroy Linux. We all know about the frivolous patents they have against Android... 

I think Microsoft is waiting for a few essential programs in Linux to use C# so they can start their crap.

Well that's an epic fail, with Banshee and Tomboy being (likely) dropped as default applications and F-Spot has lost its position long ago.  So there goes the foothold Microsoft would need to make any significant disruption in the Linux community.

---

### Post by Tibuda on 2011-11-23
> **Dragonbite said:**
> Wha? Are you saying that nobody in these forums have ever insinuated that C# (actually Mono) is a Microsoft trojan horse?  Rather a number of posts flat-out say they think it is.

I didn't say *I* say it is a trojan horse.
That's the worse argument ever. Mono is open source, and you know, thousand of eyes looking at it.



> **simpleblue said:**
> I think Microsoft is waiting for a few essential programs in Linux to use C# so they can start their crap.

They don't have to. There are enough patent-risky code written in the kernel written in C.

And why would Microsoft care about Linux? Linux never was a menace to their profits.

---

### Post by philinux on 2011-11-23
On a lighthearted note I find C# difficult on any instrument. Being a blues guitar player I like the key of E.

---

### Post by Tibuda on 2011-11-23
> **philinux said:**
> On a lighthearted note I find C# difficult on any instrument. Being a blues guitar player I like the key of E.

:guitar:

---

### Post by nothingspecial on 2011-11-23
> **philinux said:**
> On a lighthearted note I find C# difficult on any instrument. Being a blues guitar player I like the key of E.

Use a capo :p

---

### Post by Quadunit404 on 2011-11-23
> **simpleblue said:**
> Mirosoft is trying to destroy Linux. We all know about the frivolous patents they have against Android... 

Yes, how dare they contribute code to Linux, launch a site for open source developers to host their projects with no restrictions on the platform, mention the existence of Linux in their documentation (and that users can freely dual-boot between Linux and Windows in that same documentation), and write not one but TWO free licenses! They must obviously be working towards the death of Linux!

Oh wait...

---

### Post by directhex on 2011-11-23
C# is a genuinely nice language. Mono is a genuinely nice framework. Those agitating against it on either of those points are pretty deluded.

Is the patent thing real? Who knows. It's been a decade, and in that time, all Microsoft have done in this context is release chunks of code (like ASP.NET MVC) under fully Free licenses (which include a patent grant).

Does it have a bright future? I think the know-nothing reactionaries have done a number on its reputation, so not as bright as an empirical merit-based analysis would say.

---

### Post by fuduntu on 2011-11-23
> **Drenriza said:**
> So i surfed around the internet yesterday, but i don't remember what i was surfing for :p and i stumbled upon a thread saying

"Linux is better off, not using C# and getting to dependent on it"

As the thread was referring to that C# is a Microsoft technology. And as i remember C# has property code which they are not willing to share in the open-source world. Which also slows down the Mono project. Correct me if i'am wrong.

_**But what is your opinion in all of this?**_
Do you fear that Linux will get to dependent on C# and .NET? In the future.

Do you think C# and .NET should be a vital part of Linux if Microsoft would open for their use of the code? So it freely could be used.

Do you think you can write / create the same quality of code / programs on Linux with C# as with other programming languages?

Is their any other reasons you think C# should or shouldn't be more integrated with Linux.

Kind regards.

There is no issue with Mono on Linux, it is an Open Source ECMA standard that enjoys patent protection from Microsoft.  

The problem is with people that hate Microsoft because they have been programmed to do so by other people who hate Microsoft on the internet.

It's a non issue really blown way out of proportion by people wearing tin foil hats.

.. but that's just my opinion. :popcorn:

---

### Post by KiwiNZ on 2011-11-23
> **fuduntu said:**
> ....
It's a non issue really blown way out of proportion by people wearing tin foil hats.

.. but that's just my opinion. :popcorn:

That sums up nearly all Open source issue. Why can't people just use the Software that works  for them and stop making everything some crusade for humanity.

It's just Software](*,)

---

### Post by eric-yorba on 2011-11-23
Seems to me a desktop application shouldn't require a virtual machine. All the extra memory and CPU power you need is great news for hardware companies, but not users.

---

### Post by fuduntu on 2011-11-23
> **eric-yorba said:**
> Seems to me a desktop application shouldn't require a virtual machine. All the extra memory and CPU power you need is great news for hardware companies, but not users.

Jupiter is a Mono app that uses less than 10MB of memory, and 0 CPU.

---

### Post by Dragonbite on 2011-11-23
> **eric-yorba said:**
> Seems to me a desktop application shouldn't require a virtual machine. All the extra memory and CPU power you need is great news for hardware companies, but not users.

Is that why Java applications haven't made it into being a default?

---

### Post by Drenriza on 2011-11-24
> Seems to me a desktop application shouldn't require a virtual machine.
Then you would also need to remove Java as i recall. :p

---

### Post by directhex on 2011-11-24
> **eric-yorba said:**
> Seems to me a desktop application shouldn't require a virtual machine. All the extra memory and CPU power you need is great news for hardware companies, but not users.

I'd say the reverse. A desktop application should never be at risk of the usual security and crash concerns caused by manual memory management - and should be easily and rapidly improved by using a framework which encourages that. There's a reason Python is popular these days for desktop app writers.

---

### Post by directhex on 2011-11-24
> **Dragonbite said:**
> Is that why Java applications haven't made it into being a default?

Nah, there are 3 reasons for that:

1) Size. You can't get a Java app to take less than about 72 meg, because the Java framework itself is monolithic and can't be smaller than about that size. Running "Hello World" in Java needs 72 meg on disk. Comparatively, Mono will run Hello World in about 12 meg. Tomboy+Banshee+gbrainy+Mono is about 40 meg.

2) Alien look & feel. No matter how hard a Java app tries, you can tell it's a Java app. It looks, feels, and behaves like an alien toolkit, even when trying to emulate GTK. Whereas GTK# is an accurate wrapper around GTK+, so looks & feels like a real C app

3) No compelling apps. Which Java app should be on the default? I can't think of any which have ever been seriously proposed. There isn't a world of general-purpose apps which make sense for a default install.

---

### Post by fuduntu on 2011-11-24
> **KiwiNZ said:**
> That sums up nearly all Open source issue. Why can't people just use the Software that works  for them and stop making everything some crusade for humanity.

It's just Software](*,)

Please implement a voting system so this can be upvoted into oblivion because you sir have just won the internet.

[-o<

---

### Post by BrokenKingpin on 2011-11-24
> **eric-yorba said:**
> Seems to me a desktop application shouldn't require a virtual machine. All the extra memory and CPU power you need is great news for hardware companies, but not users.
Haha. So all python apps shouldn't be used either then... as it requires a runtime as well. 


I come from a .Net development background, so having Mono for Linux is just awesome. I can do all my development under Linux, and is very easy to write cross-platform applications.

Put simply, Mono is a very good development platform, and I just don't understand all the hate for it. If the only reason is because it is a Microsoft standard, people are just ignorant.

---

### Post by kaldor on 2011-11-24
As a student learning C#, I'm thankful for Mono. The above poster pretty much sums up my stance.

---

### Post by Drenriza on 2011-11-26
> **BrokenKingpin said:**
> Haha. So all python apps shouldn't be used either then... as it requires a runtime as well. 
 
 
I come from a .Net development background, so having Mono for Linux is just awesome. I can do all my development under Linux, and is very easy to write cross-platform applications.
 
Put simply, Mono is a very good development platform, and I just don't understand all the hate for it. If the only reason is because it is a Microsoft standard, people are just ignorant.
 
What kind of development do you do under C#?

---

### Post by Thewhistlingwind on 2011-11-26
I'm still wary of the whole 'patent trap' criticism. 

For my projects, I won't be using it.

---

### Post by dniMretsaM on 2011-11-26
> **BrokenKingpin said:**
> Haha. So all python apps shouldn't be used either then... as it requires a runtime as well.

Python uses an interpreter, not a virtual machine.

---

### Post by cgroza on 2011-11-26
> **dniMretsaM said:**
> Python uses an interpreter, not a virtual machine.
It depends on the implementation. And his point still stands.

---

### Post by WinterMadness on 2011-11-26
I dont think C# should exist period. Not because I prefer linux or anything, and not because I hate MS, but rather, having ANOTHER language that does the same thing as other ones is just pointless.

We already have Java, we dont need an imitator

---

### Post by dniMretsaM on 2011-11-26
> **cgroza said:**
> It depends on the implementation. And his point still stands.

True, but I was referring to the version installed by default in Ubuntu. I guess I should've been more clear.

> **WinterMadness said:**
> I dont think C# should exist period. Not  because I prefer linux or anything, and not because I hate MS, but  rather, having ANOTHER language that does the same thing as other ones  is just pointless.

We already have Java, we dont need an imitator

+1

---

### Post by directhex on 2011-11-26
> **WinterMadness said:**
> We already have Java, we dont need an imitator

Sorry, but in language terms, you may as well be saying "we already have smoke signals, we don't need broadband". C# is Java with hindsight - the greatest sins of Java's design (most of which remain unfixed to this day) resolved. Up to and including making it a real standard via a standards body

---

### Post by directhex on 2011-11-26
> **dniMretsaM said:**
> True, but I was referring to the version installed by default in Ubuntu. I guess I should've been more clear.

Er... like most things these days which start off as interpeters, CPython is VM-based. Try reading [http://www.troeger.eu/teaching/pythonvm08.pdf](http://www.troeger.eu/teaching/pythonvm08.pdf)

---

### Post by Tibuda on 2011-11-27
> **WinterMadness said:**
> I dont think [s]C#[/s] **Linux** should exist period. Not because I prefer linux or anything, and not because I hate **R**MS, but rather, having ANOTHER [s]language[/s] **operating system** that does the same thing as other ones is just pointless.

We already have [s]Java[/s] **[s]Windows[/s]** **BSD**, we dont need an imitator

Do you like the changes I made?

If you don't like the language, don't use it for your applications.

---

### Post by CryptAck on 2011-11-27
> **WinterMadness said:**
> I dont think C# should exist period. Not because I prefer linux or anything, and not because I hate MS, but rather, having ANOTHER language that does the same thing as other ones is just pointless.

We already have Java, we dont need an imitator

I disagree. 

In my humble opinion, the design of C#/.NET is superior to Java. In addition, software development can be quite different between the technologies. Take a look at WPF versus JFC/Swing/AWT.

---

### Post by fuduntu on 2011-11-27
> **WinterMadness said:**
> I dont think C# should exist period. Not because I prefer linux or anything, and not because I hate MS, but rather, having ANOTHER language that does the same thing as other ones is just pointless.

We already have Java, we dont need an imitator

I don't think C, C++, Perl, Python, Java, or any other language should exist because we do have Assembly, and we don't need OTHER languages that do the same thing. ;)

---

### Post by WinterMadness on 2011-11-28
> **Tibuda said:**
> Do you like the changes I made?

If you don't like the language, don't use it for your applications.

linux is fundamentally different than windows. bad analogy

---

### Post by WinterMadness on 2011-11-28
> **fuduntu said:**
> I don't think C, C++, Perl, Python, Java, or any other language should exist because we do have Assembly, and we don't need OTHER languages that do the same thing. ;)

thats not even remotely close to what i said.

Assembly, by its design is not object oriented, Java is good for RAD and cross platform development, thus it brings something NEW to the table.

Was this meaning REALLY so difficult to comprehend? We do not need a bunch of languages that do the same things, and no, linux does *not* just do the same thing windows does, it actually corrects a big chunk of what windows does(in addition if one were to make this argument, youd have to claim foss is the same as CC...). C++ added new things to the C paradigm. C# was made to be an imitation, and it offers no practical use other than perhaps the subjective taking to the syntax.Theres no purpose, even with biased false analogies.

---

### Post by fuduntu on 2011-11-28
> **WinterMadness said:**
> thats not even remotely close to what i said.

Assembly, by its design is not object oriented, Java is good for RAD and cross platform development, thus it brings something NEW to the table.

Was this meaning REALLY so difficult to comprehend? We do not need a bunch of languages that do the same things, and no, linux does *not* just do the same thing windows does, it actually corrects a big chunk of what windows does(in addition if one were to make this argument, youd have to claim foss is the same as CC...). C++ added new things to the C paradigm. C# was made to be an imitation, and it offers no practical use other than perhaps the subjective taking to the syntax.Theres no purpose, even with biased false analogies.

C# was made to be an imitation?  Do you have evidence of this?  Experience with the language tells me that it has plenty of uses, perhaps you are simply speaking from a lack of experience.

If you do not need a bunch of languages that do the same things then we shouldn't have any use for Perl because you can do it all with Bash.  We shouldn't need Ruby because you can do it all with PHP, and we don't need Python because you can do it all with Java.

---

### Post by directhex on 2011-11-28
> **WinterMadness said:**
> C# was made to be an imitation, and it offers no practical use other than perhaps the subjective taking to the syntax.Theres no purpose, even with biased false analogies.

Here's the history lesson.

Microsoft licensed Java from Sun, to make their own better-integrated version of the Java Runtime Environment built into Windows.

Microsoft made changes to their version of Java (usually referred to as "Microsoft Java") to make it more appealing for Windows programmers. They added a direct GUI binding to Win32 (so Java apps would look like real Windows apps, not alien). And they added mechanisms to make calling C libraries and COM objects not an enormous effort in pain (since JNI is pure ****). The uncharitable amongst you would call this "Embrace & Extend".

Any programs using either of these mechanisms would only work with Microsoft Java, not Sun Java. Sun sued and revoked their license, pointing out that these changes violated their license.

This is why Windows XP received both a Service Pack 1, and a Service Pack 1a (1a had Microsoft Java removed).

Having greatly enjoyed Java's design as compared to the still-popular Visual Basic, and not wanting to throw everyone under a bus, Microsoft decided to make their OWN Java, with blackjack and hookers, fixing not only the JNI and Swing "bugs", but also addressing every other complaint against Java they had.

Namespaces were rewritten from scratch in a more logical and consistent hierarchy. The design ensured from day 1 that the language and VM were fully uncoupled (Java bytecode is incredibly Java-centric, whereas .NET bytecode is not tied to C# at all). And, as a final insult to Java, they ensured that the language and bytecode spec were ratified as ISO and ECMA standards, rather than being a proprietary spec like Java.

Since then, .NET and C# have improved, and Java has been a joke. Let's take generics as an example - Generics are a reasonably basic concept for object-oriented languages. They're like C++ templates. In 2001, neither Java nor C# supported them. In 2004, Java 5.0 added support for Generics. A decision was made in the design of Java's generics to make them a compiler feature in the Java language, so you could run a Generics app on older Java releases. This required that Java's generics be relatively primitive. However, due to various technical issues, Java 5.0 broke bytecode compatibility with older releases anyway - resulting in crap generics support that didn't achieve the backwards-compatibility goal that caused the crapness. Conversely, when .NET 2.0 shipped in 2005, Generics were a core feature in the 2.0 bytecode format (updated with ISO and ECMA, of course), and simply made available in languages such as C# and VB.NET, without compromise.

Want to call C# an imitation? Fine, at its simplest level that's true, it started that way. But only a non-programmer without the vaguest concept of how these languages differ would say there's no purpose.

---

### Post by directhex on 2011-11-28
And another thing...

```
root@dream:/# aptitude install mono-runtime
The following NEW packages will be installed:
  libmono-corlib4.0-cil{a} libmono-security4.0-cil{a} libmono-system-configuration4.0-cil{a} libmono-system-security4.0-cil{a} 
  libmono-system-xml4.0-cil{a} libmono-system4.0-cil{a} mono-4.0-gac{a} mono-gac{a} mono-runtime 
The following packages are RECOMMENDED but will NOT be installed:
  binfmt-support cli-common libmono-i18n-west4.0-cil 
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3957 kB of archives. **After unpacking 11.5 MB will be used.**
Do you want to continue? [Y/n/?] ^C
```

versus

```
root@dream:/# aptitude install openjdk-6-jre-headless  
The following NEW packages will be installed:
  ca-certificates{a} ca-certificates-java{a} java-common{a} libavahi-client3{a} libavahi-common-data{a} libavahi-common3{a} libcups2{a} 
  libfreetype6{a} libgcrypt11{a} libgnutls26{a} libgpg-error0{a} libgssapi-krb5-2{a} libjpeg62{a} libk5crypto3{a} libkeyutils1{a} libkrb5-3{a} 
  libkrb5support0{a} liblcms1{a} libnspr4{a} libnss3{a} libnss3-1d{a} libtasn1-3{a} openjdk-6-jre-headless openjdk-6-jre-lib{a} openssl{a} 
  tzdata-java{a} 
The following packages are RECOMMENDED but will NOT be installed:
  icedtea-6-jre-cacao icedtea-6-jre-jamvm 
0 packages upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.9 MB/35.8 MB of archives. **After unpacking 99.4 MB will be used.**
Do you want to continue? [Y/n/?] ^C
```

Is it any wonder not everyone wants Java doing their dirty work, when the minimal install is 100 meg?

---

### Post by Tibuda on 2011-11-29
> **WinterMadness said:**
> linux is fundamentally different than windows. bad analogy

> **WinterMadness said:**
> nd no, [s]linux[/s] **C#** does *not* just do the same thing [s]windows[/s] **Java** does, it actually corrects a big chunk of what [s]windows[/s] **Java** does
Did you see windows was striked? What about other UNIXes? Linus said Linux is an imitation of Minix since day 1. Using your logic, Linux should not exist because it is an imitation. What about Android? It is an imitation of iOS.

That said, this logic of "imitation should not exist" is flawed. Imitation, or incremental innovation, is a critical part of technological progress. But C# is a radical innovation from Java.

> (in addition if one were to make this argument, youd have to claim foss is the same as CC...).
What is CC?

From a user without ideology point of view, FOSS is the same as Closed-source. The license is just a COPYING file in the app folder for FOSS or a wall of text they click "I agree" during install.

---

### Post by eric-yorba on 2011-11-29
> **Tibuda said:**
> But C# is a radical innovation from Java.

How is it "radically" different?  Seems there's more similarities than differences to me.

---

### Post by |{urse on 2011-11-29
I might be crazy but C#/gtk#/mono seems to run much much faster than anything I've cranked out with C#/visual studio. I do wish there was the same level of documentation/support that java brings to the table.

---

