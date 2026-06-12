---
title: "C# in Unix"
date: 2008-04-09
forum: Programming Talk
---

### Post by tashe on 2008-04-09
I was wondering if C# has any chances against Java on the Unix platforms. As I am a newbie in this stuff, can someone recommend either of these languages as better, or point to some of the basic differences?
Thanks in advance

---

### Post by LaRoza on 2008-04-09
If you are going to use C# or Java, I would recommend Java.

Java is cross platform and compatibility is greater in all platforms on which is it implemented.

The standard C# is implemented in mono, but many C# features are not part of the standard.

---

### Post by apoth on 2008-04-09
Java. It's a better language, better established, better job prospects.

---

### Post by Balazs_noob on 2008-04-09
in Linux environments they will probably never use c#
because MS wants it to be tied to the Windows platform. There is Mono but that won't be enough
for most people...

so if you want to develop under Linux then chosse Java
if you develop under Windows i think c# is a better choice
because c# has better performance under Win.

The languages them self are almost the same
no big difference...

about Jobs: Java has a lot of openings but there are a lot
of trained Java developers too, c# has less opportunities
but there are less developers for it.

if you are good then you can get Jobs easy with both.

IMHO c# will grow fast but we can never know what will
happen when java 7 goes 100%  open source :D

---

### Post by pmasiar on 2008-04-09
What are your goals? Both Java and C# are languages without smooth integration to Linux world.

C# is MSFT answer to Java, almost identical (some people say slightly improved, with interesting integration of dynamic languages recently added), but more proprietary: Java is GPL now, while C# has free reimplementation, Mono, which is always little behind C#, little more buggy, and possibly might have patent problems - nobody is sure either way (but you should be safe if you are Novel customer).

Linux has own set of languages: C, C++, Python, Ruby, PHP, etc.

Job situation is even more bogus answer than blindly suggesting java - unless apoth is expert on job market in Macedonia :-)

---

### Post by themusicwave on 2008-04-09
As someone who gets paid to program in box for different projects I would go with Java.

As has been said already, C# is intentionally tied to the Windows platform.  When Microsoft says C# and .Net more specifically is cross platform, they mean cross platform on THEIR platforms such as Windows XP, Vista, Windows CE, etc.

When Sun says Java is cross platform they mean Linux, Windows, Mac, BSD, Embedded stuff, etc.

C# will restrict you to Windows.  

Both Java and .Net really are platforms in themselves.  The idea being that they are a layer running on top of the OS.  They use a virtual machine to make this work.  They only work on Operating Systems with a VM for them.  Java simply has more Operating Systems with VMs.

Language choice depends on what you want to do.  C# is great if all you want is Windows and never ever the possibility of anything else.  Java is great if you want a well structured system that will run on all the major platforms with little code changing.  Maybe neither is the choice either, depends what you want to do.  It also depends on project constraints, sometimes you have no choice.

In my view though Java is clearly the winner.  Basically, C# is Microsoft's response to Java becoming more popular than their languages.  They saw the trend and needed to stop it so they essentially made a copy of Java with various changes.  

Mono has made C# at least possible on *nix, but Microsoft never intended .Net to work outside of their platforms.  It will never be the same as C# and will always lag behind.

---

### Post by alternatealias on 2008-04-09
I do C# programming on Linux for a living using Mono, so there are definitely jobs out there - and more companies seem to be moving to Mono every week if you pay attention to the Mono mailing lists.

The people claiming Mono doesn't work well on Linux or is "far behind .NET" are a bit out of touch with reality. If you want the les widely used features of Windows.Forms or ADO/ASP.NET, then maybe, yea, but this guy is asking about C# on Linux which leads me to suspect he's asking about writing desktop applications on Linux.

There are a growing number of applications written for Linux in C# - like Banshee, F-Spot, Muine, MonoDevelop (a really nice IDE for C#), Tomboy, etc.

As far as I can tell, developers writing desktop applications for Linux consistently choose C# over Java, not the other way around. When was the last time you saw a Java desktop application other than Eclipse?

Since Mono runs on Linux, Windows, Mac, Solaris, game consoles, and embedded devices (including the iPhone), seems to me that writing apps in C# can be quite portable.

As far as what features C# has over Java, there are a lot of them. Java is desperately trying to incorporate many of the new features of C# into Java but are doing a poor job of it (e.g. Java has a very poor implementation of generics compared to C#). C# also has really nice syntax for acessor methods called Properties.

For example, in C# you can do something like this:

public class MyClass {
   int myNumber;

   public int MyNumber {
      get { return myNumber; }
      set { myNumber = value; }
   }
}


If you have an instance of MyClass called fu, you'd simply do:

int number = fu.MyNumber;

or

fu.MyNumber = 5;

If you decide to use a newer version of C# than 2.0 (I stick with 2.0 since our projects are all in 2.0), then it is even simpler.

In Java, equivalent would be much uglier:

public class MyClass {
   int myNumber;

   public int GetMyNumber ()
   {
      return myNumber;
   }

   public void SetMyNumber (int num)
   {
      myNumber = num;
   }
}


usage would be:

int number = fu.GetMyNumber ();

fu.SetMyNumber (5);


Properties are also extremely useful to accomplish similar tasks to things like unions in C which are very useful in graphics programming.

C# also has structs and enums which Java does not.

C# also has delegates/anonymous methods which Java does not (altho I hear that Java is planning on adding support for these in 7.0?)

Newer versions of C# introduce new features such as LINQ and 'var' which can be quite useful (in fact, the C++ standard is adding something similar to LINQ at the moment).


As you can see, Java is playing catch-up to C# in many ways.

If my assertion that you are planning on writing desktop applications is wrong and you are planning on writing server-side software, then yes, it /may/ be better to use Java as it is more common in the server (also it is probably safer as it is unclear as to whether Mono's ASP.NET is safe from patent attacks, but the core (anything you'd use to write GUI apps in Linux) should be safe as it is an ECMA standard).


For more information about C# on Linux, I suggest you look at [http://www.go-mono.org]("http://www.go-mono.org") or [http://www.monoproject.com]("http://www.monoproject.com")

If you decide to go with Java, you'll probably want to grab Eclipse as your IDE - I forget the url, but it's probably something like [http://www.eclipse.org](http://www.eclipse.org) or something.


Hope that helps.

---

### Post by tseliot on 2008-04-09
> **alternatealias said:**
> ...
 but this guy is asking about C# on Linux which leads me to suspect he's asking about writing desktop applications on Linux.

There are a growing number of applications written for Linux in C# - like Banshee, F-Spot, Muine, MonoDevelop (a really nice IDE for C#), Tomboy, etc.

As far as I can tell, developers writing desktop applications for Linux consistently choose C# over Java, not the other way around. When was the last time you saw a Java desktop application other than Eclipse?

There are Java bindings for both GTK (java-gnome) and QT4 (qt-jambi), therefore you wouldn't be limited to using Java's Swing.

I find QT-Jambi to be very cool even though I don't use Java. Have a look at[ this page]("http://trolltech.com/products/qt/jambi").

---

### Post by Nemooo on 2008-04-09
> **alternatealias said:**
> For more information about C# on Linux, I suggest you look at [http://www.go-mono.org]("http://www.go-mono.org") or [http://www.monoproject.com]("http://www.monoproject.com")

Just to avoid confusion/frustration, it's [http://www.mono-project.com/](http://www.mono-project.com/), and [http://www.go-mono.org/](http://www.go-mono.org/) redirects to [http://www.mono-project.com/](http://www.mono-project.com/).

---

### Post by alternatealias on 2008-04-09
> **tseliot said:**
> There are Java bindings for both GTK (java-gnome) and QT4 (qt-jambi), therefore you wouldn't be limited to using Java's Swing.


I never said otherwise :)

However, one must note that the Java-GNOME bindings are not mature and do not commit to API stability (I just re-read their website in case things had changed).

Also, I can still not find any desktop apps written using the java-gnome bindings... can you? Part of the reason there are so few (if any?) java-gnome apps out there is because the java-gnome developers refuse to commit to an API, which in turn prevents application developers from bothering to write apps using java-gnome.

You'd think that since the java-gnome bindings have been in development since 1998 (years before C# ever showed up), that they'd have stable bindings by now, but they do not... The Gtk# bindings for C#, on the other hand, *are* stable.

This basically means that if you are serious about writing Java desktop applications, you have to choose a fugly UI toolkit that will not fit in with any other applications running on the desktop. Who in their right mind would want to do that? Clearly not many people do, or we'd have Java apps on our desktop - but we don't! ;-)

Fact of the matter is, there is more popularity and development behind C# on Linux than there is for Java (as far as desktop development goes, anyway) for quite a number of reasons... and it appears to me that the Java crowd aren't willing to fix those problems because they are too arrogant in thinking that everyone else is as anti-Microsoft as they are and that they therefor do not have to bother improving their language, tools, bindings, etc.

The sad thing is, is that 10 years ago Java was #1 and had no real competition... so Sun slacked off, and now C# has totally kicked their butts. Java continues to sadden me because Sun is *still* slacking off, hoping that if they hide their heads in the sand, C# will just go away instead of doing what needs to be done. Oh sure, they are implementing some of the C# features, but in a half-arsed way (e.g. generics) and they appear to be doing absolutely no innovation of their own. What's even sadder is that many of the C# features they are now desperately trying to get into Java were proposed/requested nearly 10 years ago by Sun's customers using Java, but they ***REFUSED*** to implement them. Sun f'd up. Big time. And now they are paying for it.

Innovate or die. Java chose to die.

---

### Post by tseliot on 2008-04-09
> **alternatealias said:**
> I never said otherwise :)
I was replying to the suitability of Java for desktop applications. I know that GTK# is more widespread than java-gnome.


> **alternatealias said:**
> However, one must note that the Java-GNOME bindings are not mature and do not commit to API stability (I just re-read their website in case things had changed).
I have never tried Java-GNOME therefore, if you say so, I believe you ;)

> **alternatealias said:**
> This basically means that if you are serious about writing Java desktop applications, you have to choose a fugly UI toolkit that will not fit in with any other applications running on the desktop. Who in their right mind would want to do that? Clearly not many people do, or we'd have Java apps on our desktop - but we don't! ;-)
I'm not a fan of Swing integration either. I have tried QT4 with both Python and C++ and if QT-Jambi is at least as good as the Python bindings then I think that QT-Jambi would be a sensible choice for Java developers. And QT4 is cross platform too.

> **alternatealias said:**
> Innovate or die. Java chose to die.
I think that making Java open source was a good move though. I hope it's not too late.

---

### Post by alternatealias on 2008-04-09
> **tseliot said:**
> I was replying to the suitability of Java for desktop applications. I know that GTK# is more widespread than java-gnome.

Ah, okay - I misunderstood your comment.

> I have never tried Java-GNOME therefore, if you say so, I believe you ;)

Hopefully it will improve some day...

> I'm not a fan of Swing integration either. I have tried QT4 with both Python and C++ and if QT-Jambi is at least as good as the Python bindings then I think that QT-Jambi would be a sensible choice for Java developers. And QT4 is cross platform too.

I haven't yet tried QT-Jambi and I'm not sure that I ever will, mostly because I prefer the Gtk widget toolkit that the rest of my ubuntu desktop uses, but also because I'm quite happy using C# now and it would take a bit more than bindings to a UI toolkit to get me to go back to Java (I make heavy use of generics and properties which Java does very poorly/not at all respectively) ;-)

> I think that making Java open source was a good move though. I hope it's not too late.

Yes, I agree. Too little too late? Only time will tell...

---

### Post by LaRoza on 2008-04-09
Considering that Java wasn't originally meant to be used on the desktop, it is remarkably resilient.

It is now the new DVD menu technology (DVD's have been using something not so great for menu's, but Blu-Ray uses Java), so to say it is dying is obviously wrong. I think that statically typed languages like Java will be used less where they aren't needed, but they will certainly still be used.

---

### Post by lnostdal on 2008-04-09
dunno of this has been mentioned .. but most developers don't bother with gnome integration anyway (_regardless_ of language) .. they use gtk+ instead .. this is true for java desktop apps also .. some examples are frostwire and azureus

[http://www.eclipse.org/swt/](http://www.eclipse.org/swt/) .. is, afaik, the most widely used java bindings for gtk+

edit:
note; gtk+ isn't gnome .. in the same way kde isn't qt

edit2:
more examples:
[http://www.eclipse.org/screenshots/](http://www.eclipse.org/screenshots/)
[http://gumtree.codehaus.org/Screenshots](http://gumtree.codehaus.org/Screenshots)
[http://udig.refractions.net/gallery/](http://udig.refractions.net/gallery/)
[http://sourceforge.net/project/screenshots.php?group_id=211252](http://sourceforge.net/project/screenshots.php?group_id=211252)
..and the ones i mentioned..
[http://www.frostwire.com/screenshots/](http://www.frostwire.com/screenshots/)
[http://azureus.sourceforge.net/screenshots_v2.php](http://azureus.sourceforge.net/screenshots_v2.php)

edit3 / note / disclaimer:
i don't care for either language (java nor c#) .. i do find the potential of a portable VM interesting though (to run other languages on) .. the work sun is doing on making the JVM smaller is interesting

---

### Post by pmasiar on 2008-04-09
Lots of good insight - which will be lost in this thread. We should have started "Java vs C# on Linux" long time ago.

Yes, I also believe that Java screwed up 10 years head-start, and now might not have enough money to catch up.

MSFT is already step ahead: they are integrating CLR with DLR (Dynamic language runtime), so you can mix and match C#, Python, Ruby, Javascript and I bet VB :-) in one application. Sad part is that Jython, Python for Java, was ignored for 10 years. I know that past data is not guarantee of future performance, but IMHO it is very strong hint that Sun does not get it.

---

### Post by themusicwave on 2008-04-09
Good points all around.

I too am hoping that Open Source will be a huge improvement for Java.  I know there are a few things I would like to see in Java that I might be willing to implement.

I'll be the first to admit part of why I don't like C# is that it was designed to be a vendor lock in.  That's what Microsoft has always wanted form .Net.  Technically it's not a bad language, although most of it was just reimplementing what Java already had :) then they added on.

It should also be noted that you can set the UIManager to native look and feel.  This makes it look pretty similar to gnome.  I can't tell the difference, although I am not a graphics designer.  Works well on Windows XP too.

I have not ventured into Mono at all, just used Microsoft C# on Windows, I was writing some early today honestly.

I still think Java has a bright future ahead of it, but C# will also gain market share.  When Windows has 80+% market share it's primary programming language has to be popular.

I too am not too happy with the whole Jython thing, they are trying to bring groovy in now. I haven't tried it though.

Maybe later I'll post some places Java is superior, no time now.  Both have places they are better.

---

### Post by pmasiar on 2008-04-09
> **themusicwave said:**
> I too am not too happy with the whole Jython thing, they are trying to bring groovy in now. 

That's yet another proof that they don't get it. Python is accepted, but no, they have to force something different down community throats, so they are in the control. Microsoft hired Jython developer to make DLR better, and released IronPython (which is faster then CPython) to community - of course under their own Non-GPL license, and they jawboned OSI to approve that license to have cover. Sad.

But now it looks that "Google for the rescue" will have more elegant solution [ Free webhosting by Google: App Engine (with Python and Django)](http://ubuntuforums.org/showthread.php?t=749285) will change game - quite a lot, IMHO.

---

