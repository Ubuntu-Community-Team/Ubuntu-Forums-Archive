---
title: "Java or C++?"
date: 2009-01-28
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-01-28
I care about performance, but also the debug environment.  

I will soon begin developing an application which will be very CPU intensive - lots of floating-point calculations involving a genetic algorithm.  I know C is about as close to the hardware as you can get without going to assembly, but when things go wrong, it is a lot harder to debug a C++ program than a Java program, at least from my experience.  Eclipse + Java seems very attractive to me, but how much performance would I be giving up vs. C++, just a rough estimate, assuming that good programming is used in both cases, basically the same code executed.  I know Java used to be slower and probably still is since it runs on a virtual machine.  But with runtime refinements and CPU optimizations, is that still the case when using modern JRE and hardware?  At some point, I will probably thread the application so the built-in threading in Java also plays a small factor.  Portability is not a major concern.

---

### Post by Branimir on 2009-01-28
If you are good with c++ I'll recommend c++ anytime, especially 
if you need floats and computations.
But, if you are not, go with Java.

Greets, Branimir.

---

### Post by SNYP40A1 on 2009-01-28
I can do it in C, but the development would take me longer.  Curious if anyone would have a rough guess of how much faster the C version would be over the Java version, assuming that both were reasonably optimized.  Would the difference in speed be less than 2x?

---

### Post by MadMan2k on 2009-01-28
c++ is ~2x faster

[http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=gpp&lang2=java](http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=gpp&lang2=java)

---

### Post by shadylookin on 2009-01-28
speed wise java is closing the gap with c++. so you can probably ignore that aspect and ask yourself which are you most comfortable in or which one you can complete the project faster in.

---

### Post by kavon89 on 2009-01-28
Just use NetBeans or Eclipse with a C++ plug-in if debugging difficulties have you worried.

---

### Post by Sorivenul on 2009-01-28
You may find [this thread]("http://ubuntuforums.org/showthread.php?t=1026962") interesting.

---

### Post by Javich on 2009-01-28
Dude, I've coded in both, in my opinion, unless you're programming some server-like app (or maybe a game), Java is the best choice. The performance gap is smaller every new JRE (yes, I know it may never be as C) and the java portability has no comparison point with C. For example, if you choose Java, I'd recommend use Eclipse-plug-in development, You'll be able to build for several OSs (Windows, Mac, Linux, Solaris, etc) and build them with OS native executable  as a start point in the same linux box you coded.

---

### Post by shadylookin on 2009-01-29
> **Javich said:**
> Dude, I've coded in both, in my opinion, unless you're programming some server-like app (or maybe a game), Java is the best choice. The performance gap is smaller every new JRE (yes, I know it may never be as C) and the java portability has no comparison point with C. For example, if you choose Java, I'd recommend use Eclipse-plug-in development, You'll be able to build for several OSs (Windows, Mac, Linux, Solaris, etc) and build them with OS native executable  as a start point in the same linux box you coded.

I thought server side was one of java's strong points with java EE and java's jit compilation I always thought long running server apps would be an area where java excelled. I'm I wrong about this?

Initial startup seems to be the only area where C really blows java out of the water.

---

### Post by jespdj on 2009-01-29
> **MadMan2k said:**
> c++ is ~2x faster
Nonsense. C++ is not in all cases two times as fast as Java. In that particular benchmark maybe, but that doesn't mean it's true in general.

However, if portability is not a major concern and number crunching is the main goal of the application, I'd choose C or C++ over Java.

I've heard that especially methods like Math.sin() and Math.cos() in Java are quite slow, because Java doesn't use the floating-point hardware instructions to calculate these. Sun implemented those functions in software to increase compatibility (they rather wanted to have a slow version of those functions that gives exactly the same result on all platforms than use a hardware-specific implementation that might give slightly different results).

> **shadylookin said:**
> I thought server side was one of java's strong points with java EE and java's jit compilation I always thought long running server apps would be an area where java excelled. I'm I wrong about this?
No, you're not wrong, and that's why so many companies use Java EE for their server side (web)applications.

---

### Post by Kilon on 2009-01-29
> **SNYP40A1 said:**
> I care about performance, but also the debug environment.  

I will soon begin developing an application which will be very CPU intensive - lots of floating-point calculations involving a genetic algorithm.  I know C is about as close to the hardware as you can get without going to assembly, but when things go wrong, it is a lot harder to debug a C++ program than a Java program, at least from my experience.  Eclipse + Java seems very attractive to me, but how much performance would I be giving up vs. C++, just a rough estimate, assuming that good programming is used in both cases, basically the same code executed.  I know Java used to be slower and probably still is since it runs on a virtual machine.  But with runtime refinements and CPU optimizations, is that still the case when using modern JRE and hardware?  At some point, I will probably thread the application so the built-in threading in Java also plays a small factor.  Portability is not a major concern.

Bottom line that it does not really matter. 

First of all , when you see a benchmark run for your life. Highly unreliable and it wont tell you what you really want to hear , whether under your conditions java will be slower under which conditions will be faster (yes Java can be faster than C).  

However , your choices are pretty unlimited. There is no reason why you should not start from high level and move down to lower level. For example you can start with a scripting language for java like jython or scheme or scala or groovy, if your experience slow downs move down to Java, if you still experience slow down move down to C++ and if you still experience slow downs then move down to assembly. There are no limits and most programs tend to utilize more than one programming language.  

An alternative to C with a much higher syntax but same execution speed (in some cases even faster) is pascal and delphi , a very popular language cross platform there is even a .NET version if .NET moves you.

So my advice is "Start high and move as needed low"

here is a thread i opened that may interest you. 

[http://ubuntuforums.org/showthread.php?t=1053072](http://ubuntuforums.org/showthread.php?t=1053072)

---

### Post by eye208 on 2009-01-29
> **Kilon said:**
> Java can be faster than C
No.

---

### Post by jespdj on 2009-01-29
> **eye208 said:**
> No.
Yes, it can. Provide proof why you say "no".

The JVM uses a [Just-In-Time compiler](http://en.wikipedia.org/wiki/Just-in-time_compilation) to compile Java bytecode to machine code on the fly. By doing this while the program is running, it can in principle make use of information that's only available at runtime to produce more optimized code. It's as if the JIT is profiling your running program and creating optimal machine code for it. An ahead-of-time compiler such as a traditional C compiler doesn't have this runtime information.

So, because of this, Java **can** be faster than C. That doesn't mean that it always or sometimes **is** faster than C, but there's no reason why it cannot be faster than C.

---

### Post by Kilon on 2009-01-29
> **jespdj said:**
> Yes, it can. Provide proof why you say "no".

The JVM uses a [Just-In-Time compiler](http://en.wikipedia.org/wiki/Just-in-time_compilation) to compile Java bytecode to machine code on the fly. By doing this while the program is running, it can in principle make use of information that's only available at runtime to produce more optimized code. It's as if the JIT is profiling your running program and creating optimal machine code for it. An ahead-of-time compiler such as a traditional C compiler doesn't have this runtime information.

So, because of this, Java **can** be faster than C. That doesn't mean that it always or sometimes **is** faster than C, but there's no reason why it cannot be faster than C.

He is a C++ troll , do not waste your time.

---

### Post by ajackson on 2009-01-29
> **Kilon said:**
> He is a C++ troll , do not waste your time.
Please, he is a **C** troll.

---

### Post by cl333r on 2009-01-29
> **ajackson said:**
> Please, he is a **C** troll.

He could be a troll, but "liars don't always tell lies". I know I'm not a C troll and I'm developing in Java on both the desktop and server side for almost 6 years, and last year I started learning C and believe me, C is a lot faster, not to mention it uses less memory.

> I care about performance, but also the debug environment.
You have to decide for yourself what's more important for you:
1. The speed advantage that C brings or Java.
2. The ease of development and debugging of Java.

---

### Post by Kilon on 2009-01-29
> **cl333r said:**
> He could be a troll, but "liars don't always tell lies". I know I'm not a C troll and I'm developing in Java on both the desktop and server side for almost 6 years, and last year I started learning C and believe me, C is a lot faster, not to mention it uses less memory.




define "a lot". 

Speed is not constant, it will be different under each situation.

There is no guarantee that Java will always perform slow or slower than C++. IF it does then you find which routine cause the speed lose , and convert to (after you made sure that it is not your coding causing the speed loss) either C++ or Assembly and still keep the vast majority of the program in JAVA.

---

### Post by ajackson on 2009-01-29
Speed is an strange thing in the IT world, most think that speed of the application when running is the only factor. It isn't but it does have a heavy weighting when considering what to implement an application in.

Interactive GUI programs don't need as much runtime speed as a non interactive process (say a billing engine for a large firm that has to spew out thousands of bills daily). Interactive GUIs have to cater for a real speed bottle-neck, namely the person sat the other side of the screen, so often quick is as good as very fast when it comes to speed.

Then there is the hidden speed (from an end users point of view), development and support. Lets take two imaginary languages (to avoid a certain blinkered individual trolling) *Bob* and *Fred* (OK not the best names in the world but they'll do).

If *Bob* (once compiled) runs twice as fast as *Fred* but takes twice as long to develop in, which is the "faster" language? Most would say *Bob* but what if the development time in *Bob* was 4 years? What if fixing bugs in *Bob* also took twice as long?

---

### Post by cl333r on 2009-01-29
> **Kilon said:**
> define "a lot". 

Speed is not constant, it will be different under each situation.

There is no guarantee that Java will always perform slow or slower than C++. IF it does then you find which routine cause the speed lose , and convert to (after you made sure that it is not your coding causing the speed loss) either C++ or Assembly and still keep the vast majority of the program in JAVA.

"a lot" is not a constant number and my words are backed by the experience I had with both C and Java. I won't give any examples on benchmarks because you'll prolly dismiss them as well as those on the web which is a fertile ground for large useless discussions.
If you don't agree that C is faster than Java - good for you, I don't have a right nor will to prove you right or wrong and I respect that, I speak for my experience.

---

### Post by nvteighen on 2009-01-29
> **Kilon said:**
> 
However , your choices are pretty unlimited. There is no reason why you should not start from high level and move down to lower level. For example you can start with a scripting language for java like jython or scheme or scala or groovy, if your experience slow downs move down to Java, if you still experience slow down move down to C++ and if you still experience slow downs then move down to assembly. There are no limits and most programs tend to utilize more than one programming language.

There's a problem with that. Moving lower in the "abstraction continuum" (tm by CptPicard) is always much more difficult than moving higher and sometimes and you can finally encounter limits: Such practice is subject to the existence of interfaces between languages, and these interfaces, although you can use them from the higher or the lower language, always will be defined from the lower one. So, in summary, even if you want to move lower, that's only possible if there's a way highwards between both languages.

Of course, I wouldn't worry... I guess (and hope) Java is not the case of Scheme, where no interface to a lower language exist and therefore you're "forced" to think in terms of a Lisp Machine (That's great! Utterly unpractical, but great!) and forget you're using a virtual machine, because you just can't get out from it. But from a theorical point of view, this is a point of interest for me: how far can you move between different semantical systems... how much can you translate in order to achieve automated mutual comprehension without any information loss?

---

### Post by Kilon on 2009-01-29
> **cl333r said:**
> "a lot" is not a constant number and my words are backed by the experience I had with both C and Java. I won't give any examples on benchmarks because you'll prolly dismiss them as well as those on the web which is a fertile ground for large useless discussions.
If you don't agree that C is faster than Java - good for you, I don't have a right nor will to prove you right or wrong and I respect that, I speak for my experience.

Where did you see me dismissing the benchmarks ?

Where did you see me disagreeing that C is faster than Java ?

---

### Post by Kilon on 2009-01-29
> **nvteighen said:**
> There's a problem with that. Moving lower in the "abstraction continuum" (tm by CptPicard) is always much more difficult than moving higher and sometimes and you can finally encounter limits: Such practice is subject to the existence of interfaces between languages, and these interfaces, although you can use them from the higher or the lower language, always will be defined from the lower one. So, in summary, even if you want to move lower, that's only possible if there's a way highwards between both languages.

Of course, I wouldn't worry... I guess (and hope) Java is not the case of Scheme, where no interface to a lower language exist and therefore you're "forced" to think in terms of a Lisp Machine (That's great! Utterly unpractical, but great!) and forget you're using a virtual machine, because you just can't get out from it. But from a theorical point of view, this is a point of interest for me: how far can you move between different semantical systems... how much can you translate in order to achieve automated mutual comprehension without any information loss?

I agree that is why out of the four I choose jython. I loved its direct approach. 

Unfortunately JNI (Java way of interfacing with C++ and other languages) is not that straightforward.  But it is not that hard to use either, and it is well worth compared to only using C++.

---

### Post by Simian Man on 2009-01-29
If you spend the minimal time writing an app in Java and also the minimal time writing the same app in Java, given equal skill in both languages, I guarantee the Java app will be faster.  That is because without digging into very aggressive optimization, Java's JIT compiler will outperform your C++ code.  Because it can optimize on the fly, it has access to profile data that a C++ compiler cannot access.  You can achieve somewhat the same thing with the use of the profile guided optimization, but this is still somewhat new and most programmers do not even attempt it.

Furthermore the restrictive nature of Java (ie no pointers) means that certain ambiguities such as aliasing cannot occur giving the compiler more lattitude to make changes.  It is possible to coax the compiler into such changes as well with the use of the g++ restrict qualifier but doing so requires careful insight and also you lose portability.

Given enough time and determination, a good C programmer can beat Java, but it certainly isn't easy.  That is why those benchmarks such as the shootout have C being so efficient - because somebody took a lot of time to optimize the C code.  **You cannot expect to get 2X speedup with C++ over Java on any reasonable program.**

```


  |                              o
  |                            o   
  |                 + + + + +o +
S |           + + +        o
P |     + + +          o o
E | + +             o o
E |             o o
D |       o o o
  | o o o
  |
  -------------------------------
     PROGRAMMER TIME
```

Where '+' signifies Java (or any other such language) and 'o' signifies C or C++.

---

### Post by igouy on 2009-01-29
> **jespdj said:**
> Nonsense. C++ is not in all cases two times as fast as Java. In that particular benchmark maybe, but that doesn't mean it's true in general.

However, if portability is not a major concern and number crunching is the main goal of the application, I'd choose C or C++ over Java.

Did you even look at "that particular benchmark"?

Did you wonder if "lots of floating-point calculations involving a genetic algorithm" would actually be like a long-running n-body simulation because the cost function would take up most of the computation?

_[When we look at n-body "Would the difference in speed be less than 2x?" turns out to be ~1.1x]("http://shootout.alioth.debian.org/u64q/benchmark.php?test=nbody&lang=all")_



> I've heard that especially methods like Math.sin() and Math.cos() in Java are quite slow, because Java doesn't use the floating-point hardware instructions to calculate these. Sun implemented those functions in software to increase compatibility (they rather wanted to have a slow version of those functions that gives exactly the same result on all platforms than use a hardware-specific implementation that might give slightly different results).

"If the angle is not within the range of +45 to -45 degrees, java doesn't use hardware for sin and cos ... That's because the x86 family of processors return incorrect results at the accuracy that Java requires."

_[And that shows up in the older version of "that particular benchmark"]("http://shootout.alioth.debian.org/gp4/fulldata.php?test=partialsums&p1=gcc-3&p2=icpp-3&p3=java-3&p4=java-3")_ - although Math.sin() and Math.cos() may be completely irrelevant for his genetic algorithm

_[And the problem might be ameliorated to some extent.]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=partialsums&lang=java&id=4")_

---

### Post by igouy on 2009-01-29
> **Simian Man said:**
> That is why those benchmarks such as the shootout have C being so efficient - because somebody took a lot of time to optimize the C code.

As if somebody didn't take a lot of time to optimize the Java code!

---

### Post by ajackson on 2009-01-29
> **igouy said:**
> As if somebody didn't take a lot of time to optimize the Java code!
Again we can drop down to relative time, is optimising Java quicker than C? Or vice versa? That is why I say measuring base running speed isn't always the best indicator for defining "speed".

---

### Post by igouy on 2009-01-29
> **SNYP40A1 said:**
> I will soon begin developing an application which will be very CPU intensive - lots of floating-point calculations involving a genetic algorithm.

Genetic algorithms aren't new - what libraries are available?

Look for libraries - 15 seconds with Google came up with this:

[n-genes]("http://spc.unige.ch/tools/n-genes/")

[n-genes Tutorials &#8212; the Max One Problem]("http://spc.unige.ch/n-genes:tutorial1")

[The Parallel Genetic Algorithm Library (PGAL, pronounced "Piggle") is a C++ toolkit...]("http://unix.freshmeat.net/projects/pgal/")


You'll find more for both Java and C++, try several, see which library works for you and use it.

---

### Post by Simian Man on 2009-01-29
> **igouy said:**
> As if somebody didn't take a lot of time to optimize the Java code!

But you can do a lot more to optimize C than you can Java.  The virtual machine only allows you to do so much.  More importantly, a C programmer can look at the generated assembly to find out exactly what the compiler is doing with any given snippet of source.  Java doesn't give you this by nature of JIT compilation.

That is why I say that given enough time you can *always* make C faster.  The problem is most humans don't want to spend that time.

---

### Post by igouy on 2009-01-29
> **ajackson said:**
> Again we can drop down to relative time, is optimising Java quicker than C? Or vice versa? That is why I say measuring base running speed isn't always the best indicator for defining "speed".

It isn't an *in general* question, it's a specific case - a genetic algorithm - and they can have very long run times.

---

### Post by ajackson on 2009-01-29
> **igouy said:**
> It isn't an *in general* question, it's a specific case - a genetic algorithm - and they can have very long run times.
Which invalidates my point about the relative time taken optimise the algorithm based on the language implemented in what way exactly?

---

### Post by Frak on 2009-01-29
I'd use Java, it's easier to code for, debug, and the speed is nearly at C++. Therefore, if you are very speed dependent, I mean *very*, then C++, but for all ease of use, Java.

EDIT
I'd use Fortran myself, though.

---

### Post by affran on 2009-01-29
Can any provide me some ebooks based on java.Please

---

### Post by Cracauer on 2009-01-29
The things that drove me away from Java (not sure where I am, though :)):

[list]
[*] Java zealots not only claiming but even believing they can write good, readable code that is as fast as a competent C++ programmer can (or Common Lisp for that matter).
[*] Lack of generics for too long.  This has caused pretty much all libraries that should use generics to be hacked up without generics, and now we are stuck with it.
[*] I don't use languages that need wrapper objects for basic types (int etc).
[*] Inner classes lack important closure features and the workaround are just that, workarounds.  Kinda OK.
[*] No printf or equivalent. Sorry, I'm just not using Byzantine constructions to print a couple objects in a formatted manner.  (Don't like C++ streams either).  Printing two numbers and their percentage of each other, using integer format on the first, scientific format on the second and a float with two digits after the dot is supposed to be one bloody line, thank you.
[*] Stupid semi-marketing looking technical papers and documentation. Up until I gave up on Java, tutorials come on paper or in PDFs and on pretty much all of them you can type what they say and you got syntax errors right in what they published.  Of course no English typos anywhere, because *that part* of the paper has been proofread to death.  Talk about screwed up priorities.
[*] JNI is too heavy. If I use a language that isn't the host language then I want non-function-call access to structure in host format.  Related to that, there's just no way to mmap() a whole bunch of language format data into Java and instantly start using it without copying and parsing.
[*] Of course no access to host scripting languages.
[*] OpenSourced about 500 times too late, pretty bad damage from that one.
[/list]

Just what I remember instantly, there has been more.

---

### Post by bruce89 on 2009-01-29
*cough* Vala *cough*. C# style syntax, converted to C, then compiled as C. No runtime dependency.

---

### Post by Kilon on 2009-01-29
> **Cracauer said:**
> The things that drove me away from Java (not sure where I am, though :)):

[list]
[*] Java zealots not only claiming but even believing they can write good, readable code that is as fast as a competent C++ programmer can (or Common Lisp for that matter).
[/list]



C++ can write readable code ? That is new :D

Personally I find Assembly code much more readable. I know that some people might call me crazy. But I do. I do not necessary remember all these weird assembly command but assembly code seems much more gentle to my eye. But calling C++ code , readable , i think you stretching it a bit. And comparing with Java, ouch , that did hurt....   

Faster ? ... sure ... readable ... well... no.

And do not get me started on the horrible MFC , must be the most stupid software I have seen in my life time. Doing GUI in this thing was a nightmare. Swing is weird as well, but at least I have some fun.

---

### Post by Cracauer on 2009-01-29
> **Kilon said:**
> C++ can write readable code ? That is new :D


I have no problem reading C++ code. Just reading the error messages is a problem.

Har har. Anyway, the point here is that to get good code performance in code that is pretty complex you have to use some abstractions to make it maintainable. In Java you can't even create an array of user-defined structs without getting an array of pointers. That is definitely worse than some syntactics details.

And thanks to the total absence of any macro capabilities you can't even fake it in Java.


 > **Kilon said:**
> 
Personally I find Assembly code much more readable. I know that some people might call me crazy. But I do. I do not necessary remember all these weird assembly command but assembly code seems much more gentle to my eye. But calling C++ code , readable , i think you stretching it a bit. And comparing with Java, ouch , that did hurt....   

Faster ? ... sure ... readable ... well... no.


As I said, high performance code. 

> **Kilon said:**
> 
And do not get me started on the horrible MFC , must be the most stupid software I have seen in my life time. Doing GUI in this thing was a nightmare. Swing is weird as well, but at least I have some fun.

I never did GUI work. I suppose fluffy languages like Smalltalk, Java etc work good for GUIs.

---

### Post by mnml on 2009-01-29
Use java if you want to dev something quickly.
Use C++ if you can.

Programing in java is easy and nice things can be done really quickly but really .. it doesn't look good on the performances.

---

### Post by Kilon on 2009-01-29
> **Cracauer said:**
> 


I never did GUI work. I suppose fluffy languages like Smalltalk, Java etc work good for GUIs. 

Well , yeah , GUI is ok and bearable in JAVA i guess. I cannot say I am hugely excited though. Delphi of course is light years ahead and .NET is very very good. There is nothing fluffy about those two since both are performance beasts easily compete with C++.  Python is very promising in GUI, have not tried it though.  

If you are not doing GUI in C++ , then sticking with it is very easy. But my main dislike is towards MFC , I guess GTK+ is a lot more bearable.

---

### Post by bruce89 on 2009-01-29
> **Kilon said:**
> If you are not doing GUI in C++ , then sticking with it is very easy. But my main dislike is towards MFC , I guess GTK+ is alot more bearable.

What, even subclassing?

```

#ifndef __DATE_EXPANDER_H__
#define __DATE_EXPANDER_H__

#include <glib-object.h>
#include <gtk/gtk.h>

G_BEGIN_DECLS

#define TYPE_DATE_EXPANDER		(date_expander_get_type ())
#define DATE_EXPANDER(obj)		(G_TYPE_CHECK_INSTANCE_CAST ((obj), TYPE_DATE_EXPANDER, DateExpander))
#define DATE_EXPANDER_CLASS(klass)	(G_TYPE_CHECK_CLASS_CAST ((klass), TYPE_DATE_EXPANDER, DateExpanderClass))
#define IS_DATE_EXPANDER(obj)		(G_TYPE_CHECK_INSTANCE_TYPE ((obj), TYPE_DATE_EXPANDER))
#define IS_DATE_EXPANDER_CLASS(klass)	(G_TYPE_CHECK_CLASS_TYPE ((klass), TYPE_DATE_EXPANDER))
#define DATE_EXPANDER_GET_CLASS(obj)	(G_TYPE_INSTANCE_GET_CLASS ((obj), TYPE_DATE_EXPANDER, DateExpanderClass))

typedef struct _DateExpander DateExpander;
typedef struct _DateExpanderClass DateExpanderClass;
typedef struct _DateExpanderPrivate DateExpanderPrivate;

struct _DateExpander
{
	GtkExpander parent;

	DateExpanderPrivate *priv;
};

struct _DateExpanderClass
{
	GtkExpanderClass parent_class;
};

GType		date_expander_get_type	(void) G_GNUC_CONST;
GtkWidget *	date_expander_new	(void);
void		date_expander_get_date	(DateExpander *expander,
					 guint        *year,
					 guint        *month,
					 guint        *day);

G_END_DECLS

#endif /* __DATE_EXPANDER_H__ */

```

```

#include <stdlib.h>

#include "date-expander.h"

struct _DateExpanderPrivate
{
	GtkWidget *calendar;
};

#define GET_PRIVATE(obj) (G_TYPE_INSTANCE_GET_PRIVATE ((obj), TYPE_DATE_EXPANDER, DateExpanderPrivate))

G_DEFINE_TYPE (DateExpander, date_expander, GTK_TYPE_EXPANDER);

static void	date_expander_dispose	(GObject *object);

static void
date_expander_class_init (DateExpanderClass *klass)
{
	GObjectClass *obj_class = G_OBJECT_CLASS (klass);

	obj_class->dispose = date_expander_dispose;

	g_type_class_add_private (klass, sizeof (DateExpanderPrivate));
}

static void
date_selected (GtkCalendar  *calendar,
	       DateExpander *expander)
{
	guint day;
	guint month;
	guint year;
	gchar *label;

	gtk_calendar_get_date (calendar, &year, &month, &day);

	label = g_strdup_printf ("%u/%u/%u", year, month + 1, day);
	gtk_expander_set_label (GTK_EXPANDER (expander), label);

	g_free (label);
}

static void
date_expander_init (DateExpander *expander)
{
	DateExpanderPrivate *priv;

	priv = expander->priv = GET_PRIVATE (expander);

	/* calendar */
	priv->calendar = gtk_calendar_new ();
	gtk_container_add (GTK_CONTAINER (expander), priv->calendar);
	g_signal_connect (priv->calendar, "day-selected",
			  G_CALLBACK (date_selected), expander);
}

static void
date_expander_dispose (GObject *object)
{
	DateExpander *expander = DATE_EXPANDER (object);
	DateExpanderPrivate *priv = expander->priv;

	if (priv->calendar)
	{
		gtk_widget_destroy (priv->calendar);
		priv->calendar = NULL;
	}

	G_OBJECT_CLASS (date_expander_parent_class)->dispose (object);
}

GtkWidget *
date_expander_new (void)
{
	return GTK_WIDGET (g_object_new (TYPE_DATE_EXPANDER, NULL));
}

void
date_expander_get_date (DateExpander *expander,
			guint        *year,
			guint        *month,
			guint        *day)
{
	DateExpanderPrivate *priv = expander->priv;

	gtk_calendar_get_date (GTK_CALENDAR (priv->calendar), year, month, day);
}

```

Thankfully Vala removes the need to code the boilerplate manually.

---

### Post by CptPicard on 2009-01-29
I'm not a Java fanboy, but some comments...


> **Cracauer said:**
> 
[*] Java zealots not only claiming but even believing they can write good, readable code that is as fast as a competent C++ programmer can (or Common Lisp for that matter).

C++ yes, but it's my impression that to push CL speedwise it takes quite a regression to imperative-style programming with lots of type annotations and all that.

> 
[*] Lack of generics for too long.

And when we got them, they still feel like they're just in the way most of the time :( One of those features that adds more complexity than usability IMO.

> [*] I don't use languages that need wrapper objects for basic types (int etc).

Well, autoboxing helps quite a bit here. At least in Java you can keep primitives on stack instead of having everything as object, all the time. But, true, arithmetic on BigDecimals or something like that looks ugly :)

> 
[*] Inner classes lack important closure features and the workaround are just that, workarounds.  Kinda OK.

At least you get closer to closures than in other languages that also formally do not have them, IMO. You can for example return an ad hoc implementation of some interface from a method that really does have access to everything in scope (with the Wrapper-hack). The really unforgivable thing about Java lack of closures is that IIRC it's just a decision not to have them -- they're doable, but Sun didn't want to allow people to do "difficult things that may cause problems" (in particular, different threads being able to touch each others' stack).

> 
[*] No printf or equivalent. Sorry, I'm just not using Byzantine constructions to print a couple objects in a formatted manner.

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Formatter.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Formatter.html)

> 
[*] Of course no access to host scripting languages.

But lots of interesting scripting languages coming up on the JVM...

---

### Post by Kilon on 2009-01-29
> What, even subclassing?

Oh my god ... looks very ugly ! yeap it is C++ alright. I changed my mind it is not MFC , it is the language.


> Thankfully Vala removes the need to code the boilerplate manually.


Very very interesting. And very tempting. Well I guess for every problem there is a solution. Does Vala work for Windows and MACOS as well ?

---

### Post by bruce89 on 2009-01-29
> **Kilon said:**
> Oh my god ... looks very ugly ! yeap it is C++ alright. I changed my mind it is not MFC , it is the language.

Actually, that's C with GObject. C++ would be slightly less long, but possibly more cryptic.

> **Kilon said:**
> Very very interesting. And very tempting. Well I guess for every problem there is a solution. Does Vala work for Windows and MACOS as well ?

Vala is a meta-compiler for GObject, and AFAIK it runs on Windows.

It probably halfs or even thirds the amount of typing that needs to be done.

```

using Gtk;

public class TestNotebook : Notebook
{
	construct
	{
		for (int i = 1; i < 4; i++)
		{
			var label = new Label ("Content");
			append_page (label, null);
			set_tab_detachable (label, true);
			set_tab_reorderable (label, true);
		}
	}
}

public class Test : Window
{
	construct
	{
		destroy += main_quit;
		resizable = false;

		var hbox = new HBox (false, 6);
		add (hbox);
		hbox.spacing = 6;

		var nb1 = new TestNotebook ();
		nb1.group = "TestGroup";
		hbox.pack_start_defaults (nb1);
		var nb2 = new TestNotebook ();
		nb2.group = "TestGroup";
		hbox.pack_start_defaults (nb2);
	}

	static void main (string[] args)
	{
		Gtk.init (ref args);

		var window = new Test ();
		window.show_all ();

		Gtk.main ();
	}
}

```

---

### Post by Kilon on 2009-01-29
> **bruce89 said:**
> Actually, that's C with GObject. C++ would be slightly less long, but possibly more cryptic.



Vala is a meta-compiler for GObject, and AFAIK it runs on Windows.

It probably halfs or even thirds the amount of typing that needs to be done.

Sorry I did not understand your reply , it run on Windows as well as Linux or only Windows ? No MACOS ?

---

### Post by bruce89 on 2009-01-29
> **Kilon said:**
> Sorry I did not understand your reply , it run on Windows as well as Linux or only Windows ? No MACOS ?

Perhaps, it would work on OS X, I don't know. It's aimed at GNOME's GObject, but that should work anywhere.

---

### Post by eye208 on 2009-01-29
> **jespdj said:**
> Yes, it can. Provide proof why you say "no".

The JVM uses a [Just-In-Time compiler](http://en.wikipedia.org/wiki/Just-in-time_compilation) to compile Java bytecode to machine code on the fly. By doing this while the program is running, it can in principle make use of information that's only available at runtime to produce more optimized code. It's as if the JIT is profiling your running program and creating optimal machine code for it. An ahead-of-time compiler such as a traditional C compiler doesn't have this runtime information.

So, because of this, Java **can** be faster than C. That doesn't mean that it always or sometimes **is** faster than C, but there's no reason why it cannot be faster than C.
Thanks for lecturing me about JIT compilation. Without you and Wikipedia I couldn't program my way out of a paper bag.

Now let me tell you something about garbage collection, array bounds checking, exception handling and all the other things a Java program does at runtime. These things are very useful, but they reduce performance. Think of them as hidden lines of code between the written lines. Even the most advanced JIT compiler cannot optimize all of them away. That's why an algorithm in Java will _always_ be slower than its C equivalent. Sometimes more, sometimes less. Java has many advantages over C, but speed is not one of them. I know some people here believe that I'm a troll, but I'm really just trying to inject some common sense into this forum. Statements such as "Java can be faster than C" usually come from people knowing neither Java nor C.

---

### Post by Cracauer on 2009-01-29
> **CptPicard said:**
> C++ yes, but it's my impression that to push CL speedwise it takes quite a regression to imperative-style programming with lots of type annotations and all that.


That's true, there's a lot of hair in fast Common Lisp.

But, and that's the thing that limits Java to some semi-toyish status in the end, they have extensive macro capabilities.

I know you know, but for the rest of the readers, Common Lisp is what we call a "programmable programming language". Just like you can define your own functions in C, but you can't define control constructs like if, when, while etc., Common Lisp allows you do define your own control constructs, too.

In Common Lisp people implemented the object-oriented things from C++ (classes with function pointers, implicit "this/self", inheritance) just in userspace with a couple macros, with no compiler modifications required. Try that in C, not to mention Java.

Anyway, the point here is that this kind of abstractive power allows you to then go and make your own language primitives that hide all the dirt from microoptimizations away from the code you actually write and read.

> **CptPicard said:**
> 
[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Formatter.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Formatter.html)


Well, as the URL says, in Java 1.5.  By the time I was gone.

> **CptPicard said:**
> 
But lots of interesting scripting languages coming up on the JVM...

That's true, and I really like that.

I want the cool scripting languages to use the JVM so that we get CPU-using threads, hopefully a benefit from JITs and general interoperability between the languages.

---

### Post by igouy on 2009-01-29
> **Simian Man said:**
> More importantly, a C programmer can look at the generated assembly to find out exactly what the compiler is doing with any given snippet of source. Java doesn't give you this by nature of JIT compilation.

If it's easier to see what the compiler is doing and if the language is intended to provide predictable performance why wouldn't we think the C programmers spent _less time_ to optimize the C code, the opposite of your claim - *"That is why those benchmarks such as the shootout have C being so efficient - because somebody took a lot of time to optimize the C code."*

---

### Post by Cracauer on 2009-01-29
> **igouy said:**
> If it's easier to see what the compiler is doing and if the language is intended to provide predictable performance why wouldn't we think the C programmers spent _less time_ to optimize the C code, the opposite of your claim - *"That is why those benchmarks such as the shootout have C being so efficient - because somebody took a lot of time to optimize the C code."*

I would be curious whether any Java implementation has the equivalent to (disassemble 'myfunc) to show what it is in machine code, right now?

Without that it gets mighty hard to write code that translates into good machine code for those of us who don't believe in fairy tale almighty compilers :)

---

### Post by eye208 on 2009-01-30
> **bruce89 said:**
> C++ would be slightly less long, but possibly more cryptic.
You should take a look at gtkmm. It's a proper C++ interface for GTK+.

---

### Post by Branimir on 2009-01-30
Well, I could not program in java. It kills imagination.
Haskell is great language, but unfortunately not that
popular and more difficult to learn to program in it properly
than it is in c++. But Haskell is beaty of computer languages.
I am really repulsive if someone wants me to do things
in Java. But sometimes I have to unwillingly.

Performance wise I don;t care.

Greetsa, Branimir.

---

### Post by bruce89 on 2009-01-30
> **eye208 said:**
> You should take a look at gtkmm. It's a proper C++ interface for GTK+.

I know, I was moaning about C++, not praising it.

---

### Post by eye208 on 2009-01-30
> **bruce89 said:**
> I know, I was moaning about C++, not praising it.
It looked like you were moaning about GTK+ because it's *not* C++. Did I miss something?

---

### Post by bruce89 on 2009-01-30
> **eye208 said:**
> It looked like you were moaning about GTK+ because it's *not* C++. Did I miss something?

Possibly.

> **bruce89 said:**
> C++ would be slightly less long, but possibly **more** cryptic.

---

### Post by eye208 on 2009-01-30
> **bruce89 said:**
> Possibly.
Unlikely. I'd rather say you missed the gtkmm part.

---

### Post by eye208 on 2009-01-30
> **Kilon said:**
> Oh my god ... looks very ugly ! yeap it is C++ alright. I changed my mind it is not MFC , it is the language.
No, it's the fact that the code was automatically generated, not written by hand. bruce89 didn't tell you that he just pasted the output of the Vala compiler which is far more verbose than necessary.

---

### Post by SNYP40A1 on 2009-01-30
> **igouy said:**
> ... although Math.sin() and Math.cos() may be completely irrelevant for his genetic algorithm

Some instances of trig functions, but probably insignificant.

---

### Post by SNYP40A1 on 2009-01-30
> **igouy said:**
> Genetic algorithms aren't new - what libraries are available?

Look for libraries - 15 seconds with Google came up with this:

[n-genes]("http://spc.unige.ch/tools/n-genes/")

[n-genes Tutorials — the Max One Problem]("http://spc.unige.ch/n-genes:tutorial1")

[The Parallel Genetic Algorithm Library (PGAL, pronounced "Piggle") is a C++ toolkit...]("http://unix.freshmeat.net/projects/pgal/")


You'll find more for both Java and C++, try several, see which library works for you and use it.

Thanks for the links.  The genetic algorithm is only the most speed-dependent part of the application.  The other parts will probably require more development time...if it was just a matter of implementing the GA, I would probably just use the most optimized open-source library available.

Thanks above for the idea of coding the most speed-critical part of the application in C, I did not know you could create a Java / C hybrid application.

---

### Post by SNYP40A1 on 2009-01-30
> **Simian Man said:**
> But you can do a lot more to optimize C than you can Java.  The virtual machine only allows you to do so much.  More importantly, a C programmer can look at the generated assembly to find out exactly what the compiler is doing with any given snippet of source.  Java doesn't give you this by nature of JIT compilation.

That is why I say that given enough time you can *always* make C faster.  The problem is most humans don't want to spend that time.

That's true, GA's can be implemented in parallel pretty easily.  So if the difference was small, I would opt to simply get more hardware.  That's why I was asking, as a rough guesstimate, what the difference in speed would be.  I see though that I could have been more clear on what calls my application will be using.  Most of the speed-critical part of the application will involve floating point arithmetic math and calls found in the Java and C math library.  I should have mentioned the floating point aspect earlier, but I assume Java uses hardware for that as it did in the n-body gaming benchmark referenced above.

---

### Post by SNYP40A1 on 2009-01-30
> **affran said:**
> Can any provide me some ebooks based on java.Please

Start here:

[http://www.stanford.edu/class/cs106a/](http://www.stanford.edu/class/cs106a/)

Then go here:

[http://www.stanford.edu/class/cs108/](http://www.stanford.edu/class/cs108/)

---

### Post by igouy on 2009-01-30
> **SNYP40A1 said:**
> Thanks for the links.  The genetic algorithm is only the most speed-dependent part of the application.  The other parts will probably require more development time...if it was just a matter of implementing the GA, I would probably just use the most optimized open-source library available.

In that case, perhaps you should consider **a scripting language** for the other parts and an optimized open-source library for the GA.

---

### Post by bruce89 on 2009-01-30
> **eye208 said:**
> Unlikely. I'd rather say you missed the gtkmm part.

No, I knew it existed, I probably just didn't explain myself properly.

> **eye208 said:**
> No, it's the fact that the code was automatically generated, not written by hand. bruce89 didn't tell you that he just pasted the output of the Vala compiler which is far more verbose than necessary.

Actually, I coded that C code myself (alright, I cleaned up the Vala-outputted code).

---

### Post by Kilon on 2009-01-30
> 
Actually, I coded that C code myself (alright, I cleaned up the Vala-outputted code).

please do not feed the troll , we have specialized personnel for that purpose.

---

### Post by SNYP40A1 on 2009-01-30
> **igouy said:**
> In that case, perhaps you should consider **a scripting language** for the other parts and an optimized open-source library for the GA.

I am kinda biased against scripting languages for anything but trivial cases, it's not the fault of the language, but I don't know of an IDE that makes debugging them easy for larger than trivial applications.  Although my experience with scripting languages is limited to Perl.

---

### Post by bruce89 on 2009-01-30
> **Kilon said:**
> please do not feed the troll , we have specialized personnel for that purpose.

I know, it's called me.

Also, I was only correcting their wrong assumption. The matter is now closed, bye.

---

### Post by igouy on 2009-01-30
> **SNYP40A1 said:**
> I am kinda biased against scripting languages for anything but trivial cases, it's not the fault of the language, but I don't know of an IDE that makes debugging them easy for larger than trivial applications.  Although my experience with scripting languages is limited to Perl.

Without knowing what else you need to do apart from the GA it's difficult to make sensible suggestions.

I tend to prefer somewhat more verbose languages that I can pick up months later - so Perl has never worked well for me either ;-)

Lua is very simple and clear.

Python is simple and clear.

It probably matters whether you are building GUIs or building command line. It probably matters whether the some of the other stuff you need to do could just use existing libraries.

Rather than fixate on debugging perhaps you should fixate on unit testing :-)

---

### Post by SNYP40A1 on 2009-01-30
> **igouy said:**
> Without knowing what else you need to do apart from the GA it's difficult to make sensible suggestions.

I tend to prefer somewhat more verbose languages that I can pick up months later - so Perl has never worked well for me either ;-)

Lua is very simple and clear.

Python is simple and clear.

It probably matters whether you are building GUIs or building command line. It probably matters whether the some of the other stuff you need to do could just use existing libraries.

Rather than fixate on debugging perhaps you should fixate on unit testing :-)

I have made unit tests in Java.  In either case, debugging in Perl can get ugly.  It's a great language for short scripts...funny story, I know a guy who wrote a pattern compiler in Perl...it was about 5000 lines of code long.  I don't know how he maintained his sanity.  Anyway, one thing that I hate about C / C++, which consumed several hours of my day today is the compiling.  In Java / .NET, you just list the relevant files and the compiler figures things out.  In C++, you have to specify which files to include, how to build the .dlls, it gets ugly, at least for me.

---

### Post by igouy on 2009-01-31
> **SNYP40A1 said:**
> I have made unit tests in Java.  In either case, debugging in Perl can get ugly.  It's a great language for short scripts...funny story, I know a guy who wrote a pattern compiler in Perl...it was about 5000 lines of code long.  I don't know how he maintained his sanity.

If you don't like Perl, don't use Perl :-)

But don't blame Perl for whatever mess your friend made of his tiny program - _[how about a 320,000 line Perl system...]("http://erwan.lemonnier.se/talks/pluto.html")_

It's easy enough to write modular maintainable code in a scripting language - write small functions, use name qualified imports, use OO when it's appropriate, don't just throw everything into the same file, test test test.  


> Anyway, one thing that I hate about C / C++, which consumed several hours of my day today is the compiling.  In Java / .NET, you just list the relevant files and the compiler figures things out.  In C++, you have to specify which files to include, how to build the .dlls, it gets ugly, at least for me.

And how long would you wait for Python to compile? :-)

---

### Post by SNYP40A1 on 2009-02-01
Fair points, I know Python is probably better, at least it has cleaner syntax...I just have not had the chance to pick it up yet.

---

