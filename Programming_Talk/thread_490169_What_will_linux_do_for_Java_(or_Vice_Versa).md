---
title: "What will linux do for Java? (or Vice Versa)"
date: 2007-07-02
forum: Programming Talk
---

### Post by laxmanb on 2007-07-02
They've open sourced Java under the GPL2 for a while now, but I really don't sense greater enthusiasm for Java in the FOSS world...  The only reason it's bundled (as GIJ) with Ubuntu and most other distros is because OpenOffice.org uses it for wizards. Whenever someone asks about using Java for a project they are sheperded
towards Python

.NET (through Mono) is now an integral part of GNOME despite it's questionable patent status - How long before Java gets its due in the FOSS world??

---

### Post by nitro_n2o on 2007-07-02
Believe it or not Java is a widespread language!!! It'll be a shame for linux not to have Java by default.. Linux tries to equip you with all the necessary tools that u need, might need, or the world uses... 
Even though if Java is not extensively used in Linux programming, having it as an option is a good choice :) 

It might be true that Python is easier, and maybe more powerful than Java. Java still the language of choice for developing huge commercial projects. It all goes down to business 

In short, i think having Java with linux distros  as an option is something not bad

---

### Post by kknd on 2007-07-02
I think its because Java its not 100% open yet (there is some third party code, that Sun cannot open).

I think that as soon as Sun release a true opensource JVM, Java will gaim more land in open source world.

---

### Post by samjh on 2007-07-02
Once OpenJDK is released (free from encumbered code), which will be JDK 7, I think there will be a lot more acceptance for Java in the Linux world.

I personally think that the obstinacy of the GNU/Linux community in not accepting Java, and Sun's past refusals to open-source it, have slowed Linux's growth in the mainstream business market.

If Java was not so widely used and adopted by enterprises who utilise *NIX-based infrastructure, or mixed Windows/Unix infrastructure, then I think Microsoft would have had a much easier time stealing market share away from *NIX to Windows using .NET.

Time for the GNU/Linux community to give Java a fair go, IMHO, even if some standard libraries are encumbered.  The vast majority of the encumbered parts are in the Java 2D portion anyway, with a little bit in Java Sound.

---

### Post by laxmanb on 2007-07-02
Doesn't GNU Classpath already have some Java2D code? And RedHat launched the IcedTea project which will replace the binary only bits of OpenJDK with a FOSS replacements from Classpath... I guess that's what ubuntu will have eventually... 

But the fact is Java was quite open (as in an Open Standard) even when it was proprietary- good IDEs which are Open Source, many (mostly compatible) implementations, and the code is quite well documented....

---

### Post by ankursethi on 2007-07-02
Ubuntu including Java by default will probably be a huge push for Java in the direction of desktop programming. Until now the language has been used extensively in the enterprise, but you don't get to see too many desktop apps built on Java (like media players and general utilities). Now that the language is open and is being embraced, however slowly, by the open source world, I think Java might take a bite out of C#'s desktop programming share (Banshee? Tomboy?).

---

### Post by Carlos Santiago on 2007-07-02
I think that Canonical does not provide Java installed by default on Ubuntu due to some copyright issues.
Due to this legal issues, other programs (even licensed as GPL, like JabRef) that require SUN's Java RE are also not installed by default. 
Java is loosing field because a program written in Java cannot be freely distributed and ready to run, if it requires a protected runtime environment. IMHO

---

### Post by vexorian on 2007-07-02
> **laxmanb said:**
> They've open sourced Java under the GPL2 for a while now, but I really don't sense greater enthusiasm for Java in the FOSS world...  The only reason it's bundled (as GIJ) with Ubuntu and most other distros is because OpenOffice.org uses it for wizards. Whenever someone asks about using Java for a project they are sheperded
towards Python

.NET (through Mono) is now an integral part of GNOME despite it's questionable patent status - How long before Java gets its due in the FOSS world??
MONO what? grr, thanks to your post I checked and MONO was actually installed! If it is gnome who is promoting this, I guess I will have to switch to KDE again, hmmm maybe I'll try xcfe...

Regarding Java, you should be happy that Java is on the repository, getting it was quite easy when compared to windows... right now if someone wants to release a Java program he just got to ask ubuntu users to sudo apt-get install j2re1.4

Before it is included by default though, it needs to be tototally open, and the integration should improve, seriously. Have you seen a Java app? it's compatibility with gtk is null, and it doesn't work all right with compiz-fusion...

---

### Post by laxmanb on 2007-07-02
They're getting better by the day at making Java (Swing) apps look native on GNOME by incorporating more native code. And hey - It's open source now - Sun already already has the burden of making JDKs for Windows, Linux, Solaris (x86 and SPARC) - maybe the community could chip in by fixing the chinks that exist (there aren't that many in Java 6u1). Compiz Fusion is easy to fix - The good point about FOSS is that you can already change things you don't like...

---

### Post by pmasiar on 2007-07-02
> **laxmanb said:**
> They've open sourced Java under the GPL2 for a while now, but I really don't sense greater enthusiasm for Java in the FOSS world...  The only reason it's bundled (as GIJ) with Ubuntu and most other distros is because OpenOffice.org uses it for wizards. Whenever someone asks about using Java for a project they are sheperded
towards Python

To understand dynamic of accepting Java in FOSS community, you need to return back 12 years. Back then, Java looked as a way out of MSFT strong grip of desktop. By design, everything was designed to be incompatible with Windows - and by mistake, also incompatible with Unix :-(

Yes, good news is that Java has huge library for anything - but  bad naws is it is huge and mostly incompatible with C/Unix world. Including developer's tools. So for Linux developer to switch to Java is to throw most of tools and tricks she learned. And what is payoff? Java is little easier to code in than C++, but it is also little slower. And there are many other languages in C ecosystem which are more productive for developer. 

Combination Python (for rapid app development) & C (for libraries for speed) is hard to beat, that's why many people advise that. Certainly Java alone cannot beat it. Sun realized that, realized that Java for simple web apps (80% of the market)  is not as productive as Ruby on Rails or Python frameworks, so they tried to include RAD languages, like JRuby or Jython. So battle continues, dust did not settled yet. But decision to dedicate couple of years of your life to learn Java well enough to become expert is far from obvious, IMHO. Especially for someone who already *is* expert in Linux ways of doing things :-)

---

### Post by vanadium on 2007-07-02
What also has worked agains Java is that Microsoft has broken the java platform for many years by providing their java version that deliberately had incompatabilities with Sun java.

---

### Post by vexorian on 2007-07-02
> Java is little easier to code in than C++ It is not.

> Combination Python (for rapid app development) & C (for libraries for speed) is hard to beat,

If you really think that using a language simply as layer and thus exploit C "for speed" then Java plus a C library's binding is a better answer. Java is afterall Jit compiled ...

imho Java is integrated to windows better than python

---

### Post by laxmanb on 2007-07-02
Using Python for large applications is bad (I even think alacarte works slow on my computer). And I definitely think programming in Java is easier than C/C++. It's hard writing a simple GUI application using C and I prefer the Netbeans/Visual Studio of GUI design.

And Java is quite similar to C++, so it's not too hard to jump right in. but really, I don't think it's the syntax that's stopping Java from becoming a first class citizen of the linux programming world.

---

### Post by Ramses de Norre on 2007-07-02
> **pmasiar said:**
> To understand dynamic of accepting Java in FOSS community, you need to return back 12 years. Back then, Java looked as a way out of MSFT strong grip of desktop. By design, everything was designed to be incompatible with Windows - and by mistake, also incompatible with Unix :-(

Yes, good news is that Java has huge library for anything - but  bad naws is it is huge and mostly incompatible with C/Unix world. Including developer's tools. So for Linux developer to switch to Java is to throw most of tools and tricks she learned. And what is payoff? Java is little easier to code in than C++, but it is also little slower. And there are many other languages in C ecosystem which are more productive for developer. 

Combination Python (for rapid app development) & C (for libraries for speed) is hard to beat, that's why many people advise that. Certainly Java alone cannot beat it. Sun realized that, realized that Java for simple web apps (80% of the market)  is not as productive as Ruby on Rails or Python frameworks, so they tried to include RAD languages, like JRuby or Jython. So battle continues, dust did not settled yet. But decision to dedicate couple of years of your life to learn Java well enough to become expert is far from obvious, IMHO. Especially for someone who already *is* expert in Linux ways of doing things :-)

Do you really need to switch the subject to python in every thread? 
In almost every thread on this board I can find a post by you with the exact same python propaganda...

I'm sorry if you take this as rude or impolite but I had to say it... And don't take me wrong, I do appreciate most of your posts.

---

### Post by pmasiar on 2007-07-02
> **Ramses de Norre said:**
> Do you really need to switch the subject to python in every thread? 

Yes, I have to. At work, I am forced to use Java, where Python will be 3 times simpler, and promoting Python against Java helps me to overcome the frustration.

I promise that when my boss will let me use python, I will tone down 50% :-)


> In almost every thread on this board I can find a post by you with the exact same python propaganda...

Well, Sun spent millions to hype Java, and it still did not get as far as Python is terms of convenience. Of course Java is embedded now in 'enterprisey' computing, but having new OO COBOL gets you only that far. Real hackers prefer Python to Java. And I was trying to explain why Java is is the state as it is, and why having Java is not holy grail and does not add anything substantial beyond enterprise computing. Which is fine for people who needs it. 

> I'm sorry if you take this as rude or impolite but I had to say it... And don't take me wrong, I do appreciate most of your posts.

No, you are right. This propaganda helps me to survive :-)

---

### Post by vexorian on 2007-07-02
> Using Python for large applications is bad (I even think alacarte works slow on my computer). And I definitely think programming in Java is easier than C/C++. It's hard writing a simple GUI application using C and I prefer the Netbeans/Visual Studio of GUI design.
You mentioned GUI, I think making GUI on Java was the most frustrating thing I have ever done, and I have tried visual basic, delphi, wxwidgets(C++), winapi(C)  and C#

I don' t really think this has anything to do with syntax either, I also think that everybody will love to mass move to Java once it is fully Open Source, and I am betting ubuntu will be first to jump.

---

### Post by Praill on 2007-07-02
I think this has already been touched upon but I'm going to be redundant.

Java is not licensed as GNU software. When you write a java program you arent required to distribute the source. Plus I belive the people at Sun require $$ to bundle the jre with the OS. Thats my understanding anyways regarding the whole licensing battle with MS and Sun to include the JRE in windows.

---

### Post by samjh on 2007-07-02
> **Praill said:**
> I think this has already been touched upon but I'm going to be redundant.

Java is not licensed as GNU software. When you write a java program you arent required to distribute the source. Plus I belive the people at Sun require $$ to bundle the jre with the OS. Thats my understanding anyways regarding the whole licensing battle with MS and Sun to include the JRE in windows.You're 10 years too late. ;)

Most of Java is licensed under GPL.  The only bits that aren't are the pluggable binary modules that contain encumbered code, which is only a small part of the whole Java platform and SDK.

And Sun does not require $$ to bundle the JRE with the OS.

If the JRE is the standard GPL'ed Java by Sun, then it is distributed under GPL.  On the other hand, if someone or an organisation wishes to distribute a modified version of Java using a license other than GPLv2, they need to obtain a commercial license from Sun.

So as long as Linux distros stick to the GPL license for Java, there is no need for $$.

---

### Post by kknd on 2007-07-02
> **samjh said:**
> You're 10 years too late. ;)

Most of Java is licensed under GPL.  The only bits that aren't are the pluggable binary modules that contain encumbered code, which is only a small part of the whole Java platform and SDK.

And Sun does not require $$ to bundle the JRE with the OS.

If the JRE is the standard GPL'ed Java by Sun, then it is distributed under GPL.  On the other hand, if someone or an organisation wishes to distribute a modified version of Java using a license other than GPLv2, they need to obtain a commercial license from Sun.

So as long as Linux distros stick to the GPL license for Java, there is no need for $$.

You are right. And to clarify some things:

- The code you do with Java doesn't need to be open-source. You can do wathever you want with it.

---

### Post by Praill on 2007-07-02
Ok I'm confused. I thought the whole basis of the GPL license was that you must distribute the source with the finished product. Ie. if I use the SDL library to create somethinga nd then distrubute that something without the source, I am breaking the agreements of the license... I thought. So java has to be one or the other.

---

### Post by slavik on 2007-07-03
SDL is LGPL, much like the standard C library :) (meaning you don't have to GPL your code).

---

### Post by vexorian on 2007-07-03
> **Praill said:**
> Ok I'm confused. I thought the whole basis of the GPL license was that you must distribute the source with the finished product. Ie. if I use the SDL library to create somethinga nd then distrubute that something without the source, I am breaking the agreements of the license... I thought. So java has to be one or the other.
Actually, you just have to make sure that the library's source code is available , unless you modiffied the library, which I doubt would be the case for most of Java programs

---

### Post by samjh on 2007-07-03
> **Praill said:**
> Ok I'm confused. I thought the whole basis of the GPL license was that you must distribute the source with the finished product. Ie. if I use the SDL library to create somethinga nd then distrubute that something without the source, I am breaking the agreements of the license... I thought. So java has to be one or the other.

That's only if something is licensed solely under GPL.

Java is dual-licensed.  It has a commercial license for those who do not wish to comply with GPL, and it has the GPL.  This is a similar situation to Trolltech's QT: if you make software using QT, it has to be open-source, or else you need to obtain a commercial license from Trolltech for a fee.

So GPL is still being upheld.  If you don't uphold it, you need a commercial license from Sun, obtained with said $$.

---

### Post by laxmanb on 2007-07-03
No actually Java is GPLed with the Classpath exception: any programs created using the GPLed OpenJDK can be under whatever license you want.

---

### Post by jespdj on 2007-07-03
> **samjh said:**
> That's only if something is licensed solely under GPL.

Java is dual-licensed.  It has a commercial license for those who do not wish to comply with GPL, and it has the GPL.  This is a similar situation to Trolltech's QT: if you make software using QT, it has to be open-source, or else you need to obtain a commercial license from Trolltech for a fee.

So GPL is still being upheld.  If you don't uphold it, you need a commercial license from Sun, obtained with said $$.

This is ofcourse nonsense.

You are absolutely not required to make the source of your own software written in Java available. And you do not need to pay Sun for the JDK or JRE - ever. Doesn't matter whether you write open source or closed source, commercial software.

The JDK is now going to be open source under the GPL license. That means that you can have the source for free, and if you make modifications to it, you are required to make the source code of those modifications available.

It does NOT mean that if you write a Java program yourself, that uses the standard Java library, your program has to be open source. This is a common misunderstanding about the GPL license.

I've been a professional Java developer for the past 8 years. I've written lots of commercial, closed source Java code for a lot of different clients. You do not have to pay Sun anything for the JDK or the JRE, doesn't matter if you are writing free or commercial software. There is no such thing as a "commercial license from Sun, obtained with said $$".

I'm really glad that Sun's Java is going to be open source, because that means we'll finally have a high quality version of Java by default in the Linux distro's. I hate the GNU Java junk that comes with Ubuntu. It is a very weak clone of Sun's Java - very slow and incomplete. GNU Java gives Java a bad name, because people will think that Java is slow, which it isn't - it's just GNU's fake Java which is slow. The only reason that GNU Java exists is because the free software fundamentalists wanted to have a completely open source version of Java. Once Sun's Java is completely open source, GNU's fake Java is fortunately obsolete.

---

### Post by pmasiar on 2007-07-03
> **jespdj said:**
> I hate the GNU Java junk that comes with Ubuntu. It is a very weak clone of Sun's Java - very slow and incomplete. GNU Java gives Java a bad name, because people will think that Java is slow, which it isn't - it's just GNU's fake Java which is slow. The only reason that GNU Java exists is because the free software fundamentalists wanted to have a completely open source version of Java. Once Sun's Java is completely open source, GNU's fake Java is fortunately obsolete.

Funny is, that without this GNU java you hate so much, and without excellent hard work of other volunteers, you will not have neither GNU or Linux, Sun and Microsoft would battle each other, and you would have 0% chance to Java become free/GLP. It is only *after* GPL revolution and runaway success of of free software, when Sun realized that to keep Java relevant, it need to release it under GPL. Otherwise free reimplementation of java (financed by IBM) would overtake it.

So go ahead and hate the hand which forced Sun to release Java under GPL. It just proves you do not understand forces behind the scenes. Which is of course your right - to be misinformed and even hate GNU. You still can use results of work of people you hate.

---

### Post by jespdj on 2007-07-04
I did *not* say I hate GNU, I just don't like GNU *Java*. I don't hate any *people*. I hate this one piece of software. Please don't misunderstand my text.

GNU and free software are great, without them we would not have such an excellent free operating system and lots and lots of great quality free software.

But GNU's Java version is not great quality software. It's a kind of half-working amateur version of Java, useless for any serious Java programming.

---

### Post by laxmanb on 2007-07-04
like I said... I don't think there is anymore interest in Java after it became GPLed. And GNU Classpath really is a bad Java VM. not only does it support only Java 1.4, but is incompatible with most Java apps and applets, and slower than Hotspot as well.

btw, I'm 100% sure that linux (or any other *nix) on the server wouldn't be what it is today if it didn't have a Java stack...

---

### Post by jespdj on 2007-07-04
> **laxmanb said:**
> like I said... I don't think there is anymore interest in Java after it became GPLed.
Well, the problem is that JDK 6 at the moment is only 96% open source. The other 4% is proprietary third-party code that Sun used and which they cannot make open source themselves, because they don't have the legal rights to do so. So the current Java 6 is unfortunately not open enough to be included in a 100% open source Linux distro. Hopefully the open source community will work in the coming months to replace the last 4% by open source code, and if they succeed then Java 6 might be 100% open source.

The next version of Java, version 7, will certainly be 100% open source. But Java 6 has been released last December and there is usually about two years between major new Java versions, so it will take some time before Java 7 is released.

If the newest version of Sun's Java could be bundled with the major Linux distro's by default, then Java might become more popular for desktop apps on Linux.

> **laxmanb said:**
> btw, I'm 100% sure that linux (or any other *nix) on the server wouldn't be what it is today if it didn't have a Java stack...
Absolutely agree!

---

### Post by laxmanb on 2007-07-04
Well... that 4% of code is from stuff like Java 2D, and some audio playback code for Java Audio APIs. No desktop application I've seen uses these APIs. Also. RedHat/FSF have launched the IcedTea project to replace that 4% code with GPLed code, and that'll replace GNU Classpath, possibly even by the time Ubuntu 7.10 is released.

---

### Post by jespdj on 2007-07-04
> **laxmanb said:**
> Well... that 4% of code is from stuff like Java 2D, and some audio playback code for Java Audio APIs. No desktop application I've seen uses these APIs.
Really? If you are drawing anything in a Java app, you are most likely using the Java 2D API. Swing and AWT are probably also using Java 2D behind the scenes to draw widgets etc. I've heard that font rendering is also (partly) encumbered code, so if your program draws text on a GUI, it is using closed code. So I don't think it is possible to take these APIs out and release a 100% open Sun Java version now without those APIs.

> **laxmanb said:**
> Also. RedHat/FSF have launched the IcedTea project to replace that 4% code with GPLed code, and that'll replace GNU Classpath, possibly even by the time Ubuntu 7.10 is released.
That would be good news if they succeed.

---

### Post by Alex Fernandez on 2007-07-04
> **ankursethi said:**
> Ubuntu including Java by default will probably be a huge push for Java in the direction of desktop programming. Until now the language has been used extensively in the enterprise, but you don't get to see too many desktop apps built on Java (like media players and general utilities). Now that the language is open and is being embraced, however slowly, by the open source world, I think Java might take a bite out of C#'s desktop programming share (Banshee? Tomboy?).

Reason you dont see much Java is because Java sucks compared to C/C++ (and yes even C# which is based on Java).

---

### Post by runningwithscissors on 2007-07-04
> **Alex Fernandez said:**
> Reason you dont see much Java is because Java sucks compared to C/C++ (and yes even C# which is based on Java).No it doesn't. It's not a brilliant language but it isn't bad at all.

---

### Post by vexorian on 2007-07-04
huh, GNU Java was very good at compiling stuff and it can compile to binary! I think it is a very nice thing, its only weakness is that it doesn't have all of Java's libraries, but for console apps was a realistic alternative to C++ ...

---

### Post by pmasiar on 2007-07-04
> **jespdj said:**
> I did *not* say I hate GNU, I just don't like GNU *Java*. I don't hate any *people*. I hate this one piece of software. Please don't misunderstand my text.

GNU and free software are great, without them we would not have such an excellent free operating system and lots and lots of great quality free software.

But GNU's Java version is not great quality software. It's a kind of half-working amateur version of Java, useless for any serious Java programming.

I understand you perfectly good - it seems to me that *you* do not understand how market forces work and how hard is to make a free software project successful.

Obviously version 0.1 is not as good as version 3.0. But you need to realize that **without making that free GPL sucky 0.1 Java, there would be no almost-GPL Sun's Java.** Like without Gnome, KDE would be still running on proprietary Qt. You seems to not understand the simple fact that companies like Sun don't release software under GPL from pure heart and love of humanity: they make it because it helps them to keep market position and accomplish other financial goals.

So my heroes are *especially* people who start huge projects with unclear end like GNU Java, and go from really sucky 0.1 to half-usable 0.8 version and don't give up, even as other people like you discourage them and say it will be never as good as Sun's java. They are real white knights of free software. Obviously is half-working, and even they cannot use it for professional work, But they continue to slug away, adding features and fixing bugs, while being subject of ridicule by "professionals" with no clue - and then suddnly Sun realizes that unless Sun makes Java GPL, GNU Java will became viable option and Sun's java become irrelevant - and to prevent this, Sun is *forced* to make Java GPL, and GNU Java is not needed anymore. 

But it would not happened if GNU java would not go through those sucky 0.1 releases, and you missed that.

---

### Post by jespdj on 2007-07-04
> **Alex Fernandez said:**
> Reason you dont see much Java is because Java sucks compared to C/C++ (and yes even C# which is based on Java).

Do you have any actual evidence to back this claim up, or is this just your personal feeling about Java? I suspect it's the latter.

Yes, GNU Java sucks and is slow, but Sun Java is not. The JIT (Just-In-Time) compiler and other advanced performance optimalisations in Sun's JVM are very good and make Java run very fast.

The Java programming language itself is easier to use than C++. No difficult pointer bugs. Garbage collection saves you the huge task of memory management and makes it almost impossible to create memory leaks in your software.

---

### Post by jespdj on 2007-07-04
> **pmasiar said:**
> Obviously version 0.1 is not as good as version 3.0. But you need to realize that **without making that free GPL sucky 0.1 Java, there would be no almost-GPL Sun's Java.**

I disagree with you that the open source GNU Java is the main reason why Sun is open sourcing its own version of Java.

If you're working in the IT industry, then you know that Java is huge and is used for a wide range of applications, from games on mobile phones to enterprise software running on the biggest clusters of servers. Most companies who run Java run either Sun's Java, or IBM's or HP's versions of Java (tailored for their flavours of Unix - AIX and HP-UX) or BEA's JRockit Java VM (which is highly optimized for x86 hardware).

Nobody uses GNU Java for any serious project, because it is too slow and incomplete. GNU Java is totally not suited for any serious production software and is no competition at all for Sun's, IBM's, HP's or BEA's implementations.

Sun is changing the way it does business and it's open sourcing a large part of its software, including the Solaris operating system. They are open sourcing Java as part of their new philosophy. It doesn't have anything to do with GNU Java. If you want to read more about Sun's open source philosophy, read here: [Sun's Free and Open Source Software Initiatives](http://www.sun.com/software/opensource/).

---

### Post by pmasiar on 2007-07-04
> **jespdj said:**
> Sun is changing the way it does business and it's open sourcing a large part of its software, including the Solaris operating system. They are open sourcing Java as part of their new philosophy. 

LOL if you believe such corporate PR spin, I have a nice bridge for sale for you - really good deal :-)

*Obviously* Sun cannot tell *why* they are changing corporate philosophy - they would look like suckers. But as obviously Sun's community license *was not good enough* - nobody cared, otherwise Sun would not flipfloped to GPL. I don't follow the details, but IIRC it was IBM and HP who financed GNU Java - and IIRC GNU java was under Apache license.

Corporation directors have *fiduciary duty to act in best interest of shareholders*. Shareholders are first, customers are second, and community is distant third. Sun management tried to keep Java as long and as proprietary they could - and if they did not, they would get fired by board, or sued by stockholders. All they care is profit - just after success of Linux, market changed and they have to adapt. 

But all is fine, Sun did right thing as a result of market changes - but those changes were forced on them by GNU/Linux, not by shareholders.

---

### Post by kknd on 2007-07-04
GNU Classpath and GCJ are great.
Java would not be open-source now if they (and Mono) doesn't existed.

By the way.:

You will only have to redistribute source-code if you modify the Java VM, or the SDK.
If you make application in Java, you are free to use it as you like (it's called "Classpath exception").

Java rules =).

---

### Post by ankursethi on 2007-07-05
Yes, yes. Java is fast and open source and free of corporate evil and everything. But it's not Java we see on Ubuntu, it's C#. Miguel de Icaza is working not with Sun but with Novell to integrate C# into GNOME. It's C# which is being pushed by Novell on the enterprise desktop. It's C# (well, .NET) which is being pushed by Microsoft, and *everyone* listens to those jokers. We do have the Debian founder working with Sun, but IMHO C# has a larger corporate backing than Java. Moreover, the guy behind C# (whatshisname?) is the one who has worked with several companies on several programming languages, and as a result C# looks like a nicer language than Java.

We also have Microsoft's Silverlight, which runs as Moonlight under Mono, as a semi-working almost-usable technology, while Sun's JavaFX Script is still nowhere to be seen.

In this case, who wins? Unless Sun gains a lot of community support, which they were looking for in the first place when they GPL'd Java, only then can Java counter the surge in C#'s popularity, otherwise it'll be stuck where it was initially. Where is the community support? Who here will push Java harder than any other language? Do we see the same amount of love for Java as we see for Python? Is Java as widely used on websites as PHP or RoR? Nope.

Java needs community love to survive. I just hope we see some soon, because with Java nobody has fears of lawsuits and IP issues. Even if C# is a better Java than Java, Java must survive. Not survive as in "Java must not die". Java cannot just die. It's too nice a tool to just wilt away like that. Java must not die as in it must not become another language you must learn in order to get a job.

It'll be nice for Sun if a popular OSS project such as, say, KDE or a widely used Linux distribution embraces Java.

---

### Post by vexorian on 2007-07-05
If Sun loses the battle, it would be sun's fault, until Java is 100% Open Source you won't see KDE pushing for it, although I think KDE was going to push ruby????111 I don't remember.

---

### Post by pmasiar on 2007-07-05
I think that MSFT realized sooner than Sun that next generation of apps will be written in combo: dynamic scripting language for agile development of non-time-critical parts, and compiled language for libraries (for speed). MSFT hired smart developers from Python and Ruby to make CLR for .NET good not only for C#, but also for dynamically typed languages.

Funny part is that Sun could have it first, but was not interested,  did not supported Jython development and let MSFT snatch Jython developer (he is making IronPython for .NET now). Again, Sun was not sure whether they are hardware company or not.

Once I read interesting article which helped me (and still does) to understand reasons why proprietary companies are getting involved in promoting free software. Concept is called "commoditization" and it's goal is to make commodity from whatever other companies sell. Idea is, commodity is sold for very competitive price and with minimal margin. Like IBM in '70  was hardware company which was giving software for free (to run on their hardware). They were little late to personal computer market with dozens of incompatible 8-bit machines. IBM decided to go for open architecture (anyone can make clones) and even operating system from outside vendor (MSFT). That decision created commodity PC market, where top dog, Dell, has no own research and sells PC like - well, commodity, with minimal margin and profit made on fast turnaround of commodity parts. IBM lost it's PC hardware business, and now reinvented itself as software services and integrator. So it's interest is to commoditize one level up - software. This is the reason why IBM helps free software - it helps commoditize software market. Hence free java financed by IBM, and resulting opening of "proprietary" Sun's java.

Commoditizing office application (MSFT money-printing machine is why Sun supports OpenOffice. Commoditizing C# is why Novel supports Mono. Commoditizing web applications is why MSFT supports Ruby on Steel - Ruby for .NET (including Rails), after Sun started thinking about supporting RoR - another web app framework for more rapid web app development than their current Java offering (Struts, Spring and friends).

So I don't care much why companies support free software (to hurt their competitors), I like it when they do, but I do not trust their PR for reasons *why* they do it - they are obliged *not* to tell the truth. 

GNU/Linux must stay independent of all that, hitchhiking a ride if we can, and fearlessly going against the wind if we need to. Having free java will be nice, but it's not a gift from Novel - it is something earned by efforts of free software hackers and done for promoting of Sun's own proprietary interest (as all proprietary companies are required to do by law, nothing wrong in it).

---

### Post by vexorian on 2007-07-05
> I think that MSFT realized sooner than Sun that next generation of apps will be written in combo: dynamic scripting language for agile development of non-time-critical parts, and compiled language for libraries (for speed). MSFT hired smart developers from Python and Ruby to make CLR for .NET good not only for C#, but also for dynamically typed languages.
I hope that isn't the future cause it is pretty lame.

It all sounds like letting most programmers learn only toy languages so only big companies get access to tools to develop core libraries and stuff.

Of course, lazy developers love their toy languages and think that big corporations are truly making their life easier and not splitting the developer community into 2 different classes.

---

### Post by vcardona on 2007-07-06
There are a couple of issues with Java that have made it seem less popular with the FOSS community then it really is.  First, it is mainly found in two places today: on mobile devices, and on enterprise servers.   The mobile market tends to be proprietary, so you wouldn't expect to see much FOSS community interest there.  On the other hand, the FOSS community has come up with some good or at least decent alternatives to Java on the server.  So in that area there is some competition between the two.  Second are Sun's earlier refusals to open up Java which have now been rectified.

Despite all that.  Keep in mind that Java really has grown in importance because of the FOSS community.  Many of the best and most popular servers, development tools, and libraries are open source.  The Apache Project and Red Hat are both major players in the Java world, and that is as it should be.

Honestly, I think that Java's importance to the FOSS community as a whole will rise in the next year or two.   Sun and others are working very hard through the JCP to make Java easier for users.  At the same time, Sun is making it easier for programmers too by open sourcing java, and its tools.

---

### Post by vcardona on 2007-07-06
> **pmasiar said:**
> LOL if you believe such corporate PR spin, I have a nice bridge for sale for you - really good deal :-)

*Obviously* Sun cannot tell *why* they are changing corporate philosophy - they would look like suckers. But as obviously Sun's community license *was not good enough* - nobody cared, otherwise Sun would not flipfloped to GPL. I don't follow the details, but IIRC it was IBM and HP who financed GNU Java - and IIRC GNU java was under Apache license.

Corporation directors have *fiduciary duty to act in best interest of shareholders*. Shareholders are first, customers are second, and community is distant third. Sun management tried to keep Java as long and as proprietary they could - and if they did not, they would get fired by board, or sued by stockholders. All they care is profit - just after success of Linux, market changed and they have to adapt. 

But all is fine, Sun did right thing as a result of market changes - but those changes were forced on them by GNU/Linux, not by shareholders.

Sorry, but I think you are a bit off here.  Gnu Java really isn't used anywhere outside of the FOSS world.  Java is mainly used by large corporations, and they use commercial JREs.  The biggest problem Sun had was that most Comp. Sci. students cut their teeth on free and open source tools and languages, and Java was not doing well there.  Open sourcing Java is a great  way for them to boost its popularity, and thus ensuring its longevity.  Gnu Java wasn't doing that.

---

### Post by laxmanb on 2007-07-06
Nobody actually uses GNU Java. The distros that enterprises actually use come with Sun Java. And IBM/HP are funding Apache Harmony, not GNU Classpath. both are atleast one version behind Sun Java. (which is bad for desktop apps.)

---

### Post by jespdj on 2007-07-06
> **pmasiar said:**
> I think that MSFT realized sooner than Sun that next generation of apps will be written in combo: dynamic scripting language for agile development of non-time-critical parts, and compiled language for libraries (for speed). MSFT hired smart developers from Python and Ruby to make CLR for .NET good not only for C#, but also for dynamically typed languages.

Funny part is that Sun could have it first, but was not interested,  did not supported Jython development and let MSFT snatch Jython developer (he is making IronPython for .NET now). Again, Sun was not sure whether they are hardware company or not.
Sun did hire the two most prominent JRuby developers and JRuby is doing very well, version 1.0 was released a few weeks ago and it runs Rails applications very well. Sun recognises that dynamic languages are important, in Java 6 there's the new scripting API (package javax.script) which allows you to run scripts from your Java program (and let your Java program provide objects for the scripts to interact with).

In a future version of JRuby, the Ruby script will be compiled to Java bytecode and then we'll have a very good and fast Ruby implementation. (One of the downsides of Ruby currently is that its performance isn't great).

> **vexorian said:**
> I hope that isn't the future cause it is pretty lame.

It all sounds like letting most programmers learn only toy languages so only big companies get access to tools to develop core libraries and stuff.

Of course, lazy developers love their toy languages and think that big corporations are truly making their life easier and not splitting the developer community into 2 different classes.
Actually, Ruby is quite a fun and powerful language. It has a lot of advanced OO concepts. I don't really know Python (just looked at it for half a day or so) but my first impression compared to Ruby is that Ruby is a better, more OO language than Python.

I wouldn't write a large, mission-critical, complicated business application in something like Ruby or Python, I'd choose something more robust like Java for it.

---

### Post by invictus on 2007-07-06
> **ankursethi said:**
> It'll be nice for Sun if a popular OSS project such as, say, KDE or a widely used Linux distribution embraces Java.

I agree...and I really hope this will happen now that we have QT Jambi... I would switch to KDE at least if they had working Java (in my opinion Sun has embraced Gnome and forgotten about KDE...look at all the Java/swing KDE bugs and the lack of QT looknfeel).

---

### Post by vcardona on 2007-07-06
> **invictus said:**
> I agree...and I really hope this will happen now that we have QT Jambi... I would switch to KDE at least if they had working Java (in my opinion Sun has embraced Gnome and forgotten about KDE...look at all the Java/swing KDE bugs and the lack of QT looknfeel).

Well we don't really need for Sun to embrace KDE.  There is nothing stopping anyone from writing a KDE look and feel for Swing.  That would be a good start I think.

---

### Post by pmasiar on 2007-07-06
> **vcardona said:**
> Sorry, but I think you are a bit off here.  Gnu Java really isn't used anywhere outside of the FOSS world. 

You obviously weren't listening. You prefer misinterpret what I said and then attack that strawman (which is your own). Suit yourself, but ....  

I never said free java is better: what I said that free java was getting close to usable, and if free java become as good as Sun's own java, nobody would bother with Sun's version anymore (Sun would lost any control over java). To prevent this, Sun was forced to make Java GPL (and not releasing it under Apache license, what was IIRC IBM financed free java).

Sun's java under GPL is not altruistic gift to free software community: it is hitchhiking a ride on free software wagon to squeeze little more value from otherwise diminishing asset. Which again I repeat is fine: resources otherwise wasted to recreate free reimplementation of java could be used now to more useful pursuits, and people who like java now don't have to chose between functionality and freedom.

Edit: "close to usable" - in 2 years, not in two weeks.

---

### Post by laxmanb on 2007-07-06
GNU Classpath = Java 1.4.something, and it still didn't run about 75% of my Java apps and no applets.

this was close to usable?? and IBM, BEA, HP and Sun would still keep their Java proprietary.
and IBM's Java is a clean room version without much of Sun's code - and it's still proprietary. Sun is a much bigger supporter of FOSS than IBM. Sun developed code is present in OpenOffice.org and GNOME - two of the most prominent components of Ubuntu.

---

### Post by pmasiar on 2007-07-06
> **vexorian said:**
> programmers learn only toy languages so only big companies get access to tools to develop core libraries and stuff.

Of course, lazy developers love their toy languages...

This would be funny if it was not 25 years old: [Real Programmers Don't Use Pascal](http://www.pbm.com/~lindahl/real.programmers.html) distinguishes between Real Programmers (who use ASM or FORTRAN) and Quiche Eaters (using toy language Pascal). I bet that "real Programmers" would consider today's java a toy language: you even don't manage creation and destruction of your data - and even use the abomination: objects! :-)

Funny thing when youngsters, too young to remember previous round of language wars (and using result of the victorious side), will start new round of same battle with almost the same arguments which losing side used last time... New is just well forgotten old, I guess.

You seems to miss (among many other things) that if language is opensourced, anyone (and not only big companies) can contribute with C-compiled library.

---

### Post by vcardona on 2007-07-06
> **pmasiar said:**
> You obviously weren't listening. You prefer misinterpret what I said and then attack that strawman (which is your own). Suit yourself, but ....  

I never said free java is better: what I said that free java was getting close to usable, and if free java become as good as Sun's own java, nobody would bother with Sun's version anymore (Sun would lost any control over java). To prevent this, Sun was forced to make Java GPL (and not releasing it under Apache license, what was IIRC IBM financed free java).

Sun's java under GPL is not altruistic gift to free software community: it is hitchhiking a ride on free software wagon to squeeze little more value from otherwise diminishing asset. Which again I repeat is fine: resources otherwise wasted to recreate free reimplementation of java could be used now to more useful pursuits, and people who like java now don't have to chose between functionality and freedom.

Edit: "close to usable" - in 2 years, not in two weeks.

Explain how I misinterpreted you.  You said that Gnu Java and Gnu Linux forced Sun's hand.  That is what you said, right? That implies that Linux and Gnu Java are as good or at least close to their proprietary counterparts.  Now I will accept the Gnu Linux part of that statement.  The popularity or Linux in particular and FOSS in general did force Sun's hand.  It did so by changing the way the software market works, and allowing users and developers more choice.

The point I am trying to make is that while that might have forced Sun's had with regard to Solaris, it was far less influential when it came to Java.  Sun isn't GPLing Java for altruistic reasons, but neither are they doing it because Gnu Java and Apache Harmony forced them to.  Instead Sun is trying to buy into the popularity of open source, by open sourcing Java.  This is Sun's push to try and grow the Java developer community.

So in some ways you and I agree.  Where we disagree is on our views of the success (or not) or Gnu Java and Harmony.  You think they are close in terms of functionality.  I don't.  You think Jonathan Schwartz worries his little pony tail silly over Free Java.  I don't.

Anyway, I see this degenerating into a flame war that is inappropriate for these forums.  Send me a private message if you would like to continue the discussion.

---

### Post by ankursethi on 2007-07-07
I've run Azureus on GNU Java for a long, long time. It was slow, and sometimes behaved erratically, but I'm sure it could have been usable in another year or so. Mind you, Azureus is not a small application. It uses advanced GUI widgets and implements the BT protocol, not to mention the plugin architecture.

---

### Post by xlinuks on 2007-07-07
There is no single reason why Java is getting/got open sourced. I might miss something, but at least all of the following reasons contributed to this:
-.NET has been released. Rather fast and almost crossplatform.
- MSTF managed to push .NET to Linux through Migues de lcaza
- The IBM (and other) implementation of Java
- Ruby, Python and so on - great alternatives and open sourced.
-The need to get it integrated by default into Linux cause Sun has realized its meaning (and for other reasons)

Some people still think Java is slow, especially those who haven't tried/coded using Sun's Java 6. Sun is now working (among other things) on a 'Java Kernel' and 'pre-caching' - two BIG improvements to the Java Runtime.
Let's take Java vs NET on:
1. Windows. Java is slower than NET. Guess why. (for a hint see next 2 points).
2. Linux. Java is (a bit) faster (than Mono) because on Linux SUN and Miguel de lcaza (MSFT under the hood) are playing on an even ground.
3. Solaris. The vice-versa of point one. Java is.. integrated into the OS (much like NET in windows) and a Java developer can even use DTrace. A Java Developer feels like a God on Solaris. Where is NET in Solaris? NET is nowhere to be seen here -it's deader than dead.

Mark Shuttleworth is a very wise and smart man. Way smarter than the average Joe User thinks. It's no coincidense he chose Java over Mono. "Timeo Danaos et dona ferentes" - "I fear Greeks, even bearing gifts" 

Sun and Canonical are working closely together to integrate Sun's (almost GPLed) Java 6 into the upcomming Ubuntu 7.10 . I hope they manage it. Good luck to them (to finally have a decent default Java implementation on Linux/Ubuntu)!

---

### Post by rekahsoft on 2007-07-07
> **Carlos Santiago said:**
> I think that Canonical does not provide Java installed by default on Ubuntu due to some copyright issues.
Due to this legal issues, other programs (even licensed as GPL, like JabRef) that require SUN's Java RE are also not installed by default. 
Java is loosing field because a program written in Java cannot be freely distributed and ready to run, if it requires a protected runtime environment. IMHO

the JVM is not a protected environment..it is GPL. Although there are some third party code (mostly Java2D) that is not opensource (yet) it is planned to be opened soon.

---

### Post by xlinuks on 2007-07-08
First off what does the author mean by "protected environment".
The versions of JRE and JDK (not the Java programs!) before being GPLed were closed source (CDDL License), but these JRE/JDK versions did NOT put any restrictions on your ability to share your programs and/or the source code for them, be it for money or for free.

"a program written in Java cannot be freely distributed and ready to run" - wrong, a program written in Java can be freely distributed and run! ( "ready to run" - what exactly does he mean?, even a virus is ready to run)
Azureus - It's free, it's even open source.
NetBeans - free
Eclipse - an open-source and free software framework written primarily in Java.

---

### Post by laxmanb on 2007-07-08
Java was never CDDled. CDDL is a certified open source license too (based on the Mozilla Public License, used by Firefox), btw.

---

### Post by xlinuks on 2007-07-09
You are right, there's another license where SUN whispers "royalty-free" among different restrictions.
IMO if not Linux and GNU we wouldn't see Java GPLed any soon.

---

### Post by gotdalife on 2007-07-09
Personally, I don't think any language is "easier" to learn or use. It really depends on what you've gotten accustomed to. In my case, I can code a full Java application in a matter of minutes, but at this rate, it'd probably take me at least a month to code a half-decent Python app (seeing as I have absolutely no idea about it, except perhaps that it's interpreter-based and not compiler-based (correct me on this one?)).

Perhaps it's just the fact that Python's gotten better recognition in the Linux world? Don't hold me to my word on this though. I really haven't a clue. But my point is, after using it for several projects of different scopes (web, desktop), Java isn't even slightly difficult for me anymore, while something like Python or Ruby is still a huge head-scratcher. To each his own, eh?

---

### Post by pmasiar on 2007-07-09
> **gotdalife said:**
>  Python ...perhaps that it's interpreter-based and not compiler-based (correct me on this one?)).

Often when people express opinion on something they don't know, they are bit off. Python compiles code (into .pyc), you can even distribute it instead of source. Because of late binding of name with type information, it works differently than java (and is infinitely more flexible because of that).

For you, it is hard to judge language (Python) you never used. I know enough Java to struggle by (I programmed in C, C++ and other statically typed languages, so I can even appreciate where Java is simpler than C), and can get feeling for productivity.

If you know other languages, and give Python a try, just one week, you will be surprised how for you can get in that one week. All you need is to accept significant whitespace - and I know it was a big barrier for me, and I went for Perl instead of Python, and wasted couple years on Perl. But after Perl, I did developed deep appreciation for clean readable code :-)

> Perhaps it's just the fact that Python's gotten better recognition in the Linux world? 

Did you ever wondered why many of smartest hackers prefer for their fun projects dynamically typed languages, like Perl, Python, Ruby? What they know what less experienced people don't? Why is Java mostly used in enterprise-level projects, and not for small cute nimble projects?

I am not challenging position of Java for enterprise. J2EE is, for better or worse, new COBOL++, to stay with us for decades.

---

### Post by kknd on 2007-07-09
What makes Java and Python so good is that both are platform independent and have a huge standard library. No effort must be made to make it portable.

Java and Python differs in its target.:

Java is mostly used in big enterprise projects / web, and Python in small / medium desktop (even web) projects, but there is no limitation in what they can do.

---

### Post by Smygis on 2007-07-09
> **gotdalife said:**
> Personally, I don't think any language is "easier" to learn or use. It really depends on what you've gotten accustomed to. In my case, I can code a full Java application in a matter of minutes, but at this rate, it'd probably take me at least a month to code a half-decent Python app (seeing as I have absolutely no idea about it, except perhaps that it's interpreter-based and not compiler-based (correct me on this one?)).

Perhaps it's just the fact that Python's gotten better recognition in the Linux world? Don't hold me to my word on this though. I really haven't a clue. But my point is, after using it for several projects of different scopes (web, desktop), Java isn't even slightly difficult for me anymore, while something like Python or Ruby is still a huge head-scratcher. To each his own, eh?

After strugling to learn C, C++ and java for a couple of hundred hours (about a half year) i stumbled up on Python. And guess what? It took me **THREE** hours to fully understand the main concepts of Python. I learned objectoriented programming/thinking thanks to Python.

So, Try it. You wont be sorry.
Open a terminal and fire up "python" (If you are on ubuntu, or other linux dist). And go to
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)
and download "Dive into python" from: [http://www.diveintopython.org/](http://www.diveintopython.org/)

Use the official python docs to familiarize yourself with the interactive enviroment and use Dive Into Python to... Err... Dive into Python...

---

