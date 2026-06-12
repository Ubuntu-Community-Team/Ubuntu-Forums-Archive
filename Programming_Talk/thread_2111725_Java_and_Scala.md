---
title: "Java and Scala"
date: 2013-02-02
forum: Programming Talk
---

### Post by Majorix on 2013-02-02
I am a Software Engineering student, and one of the languages I like to use is Java. I would consider myself an intermediate Java programmer, since I haven't really touched that many advanced concepts yet.

A few days ago, I came across this language called Scala. I looked at a few examples.

However I am undecided if I want to take the bite and start learning it. Would it be beneficial to use Scala instead of Java, in both becoming a better software developer, and for job opportunities?

---

### Post by trent.josephsen on 2013-02-02
Since I've never seen a job posting that said anything about Scala, but dozens upon dozens for Java (been job hunting recently, albeit in the US), I'd say Scala specifically is probably not going to help you get a job, unless you're lucky. 

That's not to say you shouldn't learn it; having a variety of languages on your resume is an asset regardless of what they are. But I have two extra pieces of advice:

1) Get to know at least one language really well. Know it well enough that when you sit down at the screen you don't have to continually refer to a book or the Internet. Knowing how to use one language effectively is better than knowing how to write "hello, world" 100 different ways. Skipping from one language to the next just says that you get bored easily; pick one and stick with it until you think "intermediate" doesn't give you enough credit.

2) Do real-world projects. Lots of languages on your CV may get you an interview, but having done real work that you can talk about during the interview will land you a job. Set clearly defined goals for your projects so that you can show your interviewer how you met them; have photos or screencaps that show the final product in action; document your time to demonstrate your ability to focus. People will be more impressed by "This is my Arduino door-closer" than the bare number of languages you claim to know.

---

### Post by Leuchten on 2013-02-05
Definitely take the bite. My example may be rare, but learning Scala and becoming proficient is probably the only reason I was able to get a job in France from the USA. 

As for more realistic job prospects, some big companies such as Twitter use Scala for parts of their backend, and Scala grows in popularity ever year.

On the becoming a better developer front, Scala will definitely help with that. Scala is a mixed functional/imperative/object oriented paradigm language. Due to this, newbies can start off using Scala as a Java++ of kinds, while dipping their toes in more functional concepts such as monads and streams.

---

### Post by slickymaster on 2013-05-09
> **trent.josephsen said:**
> Since I've never seen a job posting that said anything about Scala, but dozens upon dozens for Java (been job hunting recently, albeit in the US), I'd say Scala specifically is probably not going to help you get a job, unless you're lucky. 

That's not to say you shouldn't learn it; having a variety of languages on your resume is an asset regardless of what they are. But I have two extra pieces of advice:

1) Get to know at least one language really well. Know it well enough that when you sit down at the screen you don't have to continually refer to a book or the Internet. Knowing how to use one language effectively is better than knowing how to write "hello, world" 100 different ways. Skipping from one language to the next just says that you get bored easily; pick one and stick with it until you think "intermediate" doesn't give you enough credit.

2) Do real-world projects. Lots of languages on your CV may get you an interview, but having done real work that you can talk about during the interview will land you a job. Set clearly defined goals for your projects so that you can show your interviewer how you met them; have photos or screencaps that show the final product in action; document your time to demonstrate your ability to focus. People will be more impressed by "This is my Arduino door-closer" than the bare number of languages you claim to know.

A big +1 on trent.josephsen's post.

IMHO, Scala is best for people who are comfortable with functional programming e.g. those with a strong mathematical background. If you have an object orientated, procedural background you can still use Scala, but will take significant work to get its benefits.

Also, a good read on the subject, either you agree with it, or not, is this article: [Scala use is less good than Java use for at least half of all Java projects]("http://www.javacodegeeks.com/2011/09/scala-use-is-less-good-than-java-use.html")

---

### Post by Leuchten on 2013-05-12
> **slickymaster said:**
> A big +1 on trent.josephsen's post.

[B]IMHO, Scala is best for people who are comfortable with functional programming e.g. those with a strong mathematical background. If you have an object orientated, procedural background you can still use Scala, but will take significant work to get its benefits.
[/B]
Also, a good read on the subject, either you agree with it, or not, is this article: [Scala use is less good than Java use for at least half of all Java projects]("http://www.javacodegeeks.com/2011/09/scala-use-is-less-good-than-java-use.html")

I really have to disagree with this on both points. First off, my math background is extremely weak but I am now comfortable with functional programming. Second off, I am making a wholly procedural port of java's BigInt with value classes and long arrays, and it is no harder to read/write than the original java code.

Scala can be used as java with more features even if you avoid functional programming. Type classes, implicit values/classes, mixins, etc. make the language more expressive than java. 

There are a couple of things that make Scala harder than java if you choose to use them to their fullest. One example is the new macro system in scala 2.10. Scala macros currently require you parse and output scala's internal AST trees, which is not terribly well documented at the moment. Thankfully this feature is still being worked on heavily and will probably become easier to use with time. Another example would be the type system in scala. While types in general in scala are about as difficult to deal with as java's, if you choose to use the full power of the type system you can do crazy things that are impossible in java like [constructing an unboxed union type]("http://www.chuusai.com/2011/06/09/scala-union-types-curry-howard/") out of existing types (IE: Definining type Int |V| String that can accept either an int or string and nothing else).

If you want to learn functional programming in scala, there was a coursera course just a month or so ago. You can probably still sign up for it and browse the lectures/homework.

---

### Post by King Dude on 2013-05-12
Learn C++. I mean, Java is a great language, but C++ is just as good, and perhaps even better. You can also extend C++ with other languages such as Lua and Python.

Also, Java isn't supported by Macintosh, so it will be a big problem if you're interested in cross-platform development.

---

### Post by Leuchten on 2013-05-12
> **King Dude said:**
> Learn C++. I mean, Java is a great language, but C++ is just as good, and perhaps even better. You can also extend C++ with other languages such as Lua and Python.

Also, Java isn't supported by Macintosh, so it will be a big problem if you're interested in cross-platform development.


[http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html) has .dmg for mac for both the jre and jdk, so not sure what you're talking about.:confused:

---

### Post by King Dude on 2013-05-12
> **Leuchten said:**
> [http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html) has .dmg for mac for both the jre and jdk, so not sure what you're talking about.:confused:
[http://www.reuters.com/article/2012/10/19/us-apple-java-idUSBRE89I1A920121019](http://www.reuters.com/article/2012/10/19/us-apple-java-idUSBRE89I1A920121019)

Java is supported still, but you have to download it from Oracle as it isn't included with the OSX package by default anymore.

---

### Post by BluNova on 2013-05-12
> **King Dude said:**
> [http://www.reuters.com/article/2012/10/19/us-apple-java-idUSBRE89I1A920121019](http://www.reuters.com/article/2012/10/19/us-apple-java-idUSBRE89I1A920121019)

Java is supported still, but you have to download it from Oracle as it isn't included with the OSX package by default anymore.

And? It's not included on Windows or Ubuntu by default

---

### Post by slickymaster on 2013-05-13
> **Leuchten said:**
> ... if you choose to use the full power of the type system you can do crazy things that are impossible in java like [constructing an unboxed union type]("http://www.chuusai.com/2011/06/09/scala-union-types-curry-howard/") out of existing types (IE: Definining type Int |V| String that can accept either an int or string and nothing else).

Union types were specifically not included in Java, due to the security and type-safety issues they caused in C, and because Java has safer and more expressive ways to code instance-level polymorphism.
The best approach for implementing a dynamic type system would be munging up something with an explicit type descriptor and a java.lang.Object payload.

---

### Post by Leuchten on 2013-05-13
The union type I linked to is definitely type safe, since it is built entirely of standard scala types like this: 

```
type ¬[A] = A => Nothing
type ¬¬[A] = ¬[¬[A]]
type &#8744;[T, U] = ¬[¬[T] with ¬[U]]
type |&#8744;|[T, U] = { type &#955;[X] = ¬¬[X] <:< (T &#8744; U) }
def intOrOutputStream[T: (Int  |&#8744;| OutputStream)# &#955;](t:T) = t match { //function that takes either int or outputstream and nothing else.
  case i: Int => doSomething()
  case os: OutputStream => doSomethingElse()
}

```


All of that is defined via normal scala keywords and functions, so it fits in the type system. I am curious what kind of security issues they caused in c and if they apply here, but I don't think they would.

---

### Post by ofnuts on 2013-05-13
> **Majorix said:**
> I am a Software Engineering student, and one of the languages I like to use is Java. I would consider myself an intermediate Java programmer, since I haven't really touched that many advanced concepts yet.

A few days ago, I came across this language called Scala. I looked at a few examples.

However I am undecided if I want to take the bite and start learning it. Would it be beneficial to use Scala instead of Java, in both becoming a better software developer, and for job opportunities?

Java programmers are a dime a dozen. What employers are looking for is someone proficient with some specific uses of Java and the associated frameworks. But of course the fashionable ones change often so they are also interested on how teachable (or self-taught) you can be, and from that point of view, showing that you know a couple of extra-curricular languages (not too many, remain credible) may put you ahead of the pack.

---

### Post by King Dude on 2013-05-13
ofnuts is right, the more languages you know the better. Like I said in my first post, I suggest that you learn C++ because the language is used *everywhere*.

---

### Post by ofnuts on 2013-05-13
> **King Dude said:**
> ofnuts is right, the more languages you know the better. Like I said in my first post, I suggest that you learn C++ because the language is used *everywhere*.
The employers and jobs for Java devs and C++devs are quite different... (I tend to think that the stuff written in C++ is more likely to be interesting than yet another Intranet/Internet site in Java, and any decent C++ coder can be proficient in Java in a couple of days). 

But if you try to sell yourself as a Java developer, the other languages that are much used around Java apps are SQL, JavaScript, and shell scripts (with Python for the more evolved ones, Perl and regular expressions being seen as l33t h4ck3r stuff).

---

### Post by trent.josephsen on 2013-05-13
"The more languages you know the better" may be true up to a point, but as I said in my earlier post: Having many languages on your resume will help you land an interview, but having experience with real-world projects will score you a job. Spend some time mucking about with Scala and Ruby and Erlang and whatever, sure. Do the minimum necessary to put it on your resume and still sleep at night. But pick a language you want to do a project in and follow through with it. (Listing experience with too many languages may also cause you to be discarded as an obvious liar. Don't overdo it.)

<offtopic>

As for C++, it really doesn't overlap that much with Java in terms of applications... Learn it if you want to, I guess, but it probably won't be relevant to most jobs that seek Java experience. Honestly, in this day and age, I can't really think of a particular class of project for which C++ would be the natural choice; most of its native domains have been subsumed by C#, Java or a mixture of higher and lower level languages. Maybe that's just wishful thinking on my part though.

> **Leuchten said:**
> I really have to disagree with this on both points. First off, my math background is extremely weak but I am now comfortable with functional programming. Second off, I am making a wholly procedural port of java's BigInt with value classes and long arrays, and it is no harder to read/write than the original java code.

Not that I speak for him or her, but slickymaster did not imply that one has to have a strong mathematical background to be good at functional programming -- merely that those who are uncomfortable with functional programming will struggle to reap any of the benefits of Scala. Furthermore, it's not clear that you have been able to reap any benefits of Scala by merely doing a straight port of BigInt from Java.

Scala may be the best functional language out there, but functional programming is simply not as accessible to most people -- and most programmers are "most people". More power is an asset for good programmers, but a liability for inexperienced ones. That's what the article slickymaster linked was talking about.

</offtopic>

---

### Post by Leuchten on 2013-05-13
> **trent.josephsen said:**
> Not that I speak for him or her, but slickymaster did not imply that one has to have a strong mathematical background to be good at functional programming -- merely that those who are uncomfortable with functional programming will struggle to reap any of the benefits of Scala. Furthermore, it's not clear that you have been able to reap any benefits of Scala by merely doing a straight port of BigInt from Java.

I'm not doing a straight port, that would be pretty useless. Scala has access to value classes now, which I'm using, along with a Array[Long] for the storage. So far I've only implemented addition, but it easily beats java's BigInteger in my tests. I'm thinking about using macros as well to get some calculations done at compile time.

As I said, there are plenty of non-functional programming benefits to Scala. Here's a short list:


[LIST]
[*]Type inference - Eliminates a lot of needless type declarations
[LIST]
[*]```
 val x = new BigInt(5); def add(x: Int, y: Int) = x + y; val y = Array(1,2,4)
```
[/LIST]

[*]Implicit values/methods/classes
[LIST]
[*]Implicit values - Allows you to define unbound variables for functions. Most useful in the context of functional programming
[LIST]
[*]```
 
implicit val y = 5
def fn(x: Int)(implicit y: Int) = x * y
def fn2(x:Int)(implicit z: Int) = x * z
fn(5) // returns 25
fn2(5) //compile time error
```
[/LIST]

[*]Implicit methods - Less used nowadays, but allows for implicit conversion of types into other types. Must be imported into the current context to work.
[LIST]
[*]```
 
object x { 
  def int2Rational(i: Int) = new Rational(i)

  def fn(r: Rational) = r

  fn(15) //works
}

object y {
  def fn(r: Rational) = r
  fn(15) //doesn't work, int is not a rational
}

object z {
  import x.int2Rational
  def fn(r: Rational) = r
  fn(15) // works now because int2Rational was imported
}
```
[/LIST]

[*]implicit classes - the most useful use of implicit at the moment, can be used to create type classes or just add new functionality to old classes.
[LIST]
[*]```

implicit class RichString(s: String) {  //define methods that allows Strings to be used like a standard scala collection of chars
   def map[A](fn: String => A) = fn(s) 
}
"hello world" map (_ toUpper) //"HELLO WORLD"

```
[/LIST]
[/LIST]

[*]value classes - single element classes that have minimal overhead compared to a standard class
[*]tuples - useful for returning multiple values
[LIST]
[*]```
 val x = (5,"a", 2.0f) 
```
[/LIST]

[*]mixins - interfaces with defineable methods and members
[LIST]
[*]```

trait A {
  def x = 15
  var y = System.out
}

val i = new Object with A
i.x// 15
```
[/LIST]

[*]type classes - allows you to define relationships between classes without inheritance. Useful for adding a class of functionality to a set of classes that the library writer didn't envision
[LIST]
[*]```
 
def add[T: Numeric](x: T, y: T) = {
  import Numeric.Implicits._
  x + y
}

add(5.2d, 2l) //7.2d is result
add('a', 2) //doesn't work
```
[/LIST]

[*]pattern matching - overpowered switch statements
[LIST]
[*]```

val x = Array(1,2,3)
x match {
    case Array(t,u,v) => t + u + v //decompose a 3 element array and bind the elements to names t, u, and v
    case a: Array[Int] => a.doStuff //match on type, can match on subtype/supertype too
    case "a" => doStuff() //primitive match, most like a normal switch
    case _ => doDefaultStuff() //default match, only reached if all others fail
}
```
[/LIST]

[*]case classes - simple classes that don't require the new keyword to be constructed. Also decomposable by pattern matching by default.
[LIST]
[*]```
 
case class RGB(r: Int, g: Int, b: Int) extends Color {}
val c = RGB(255,255,255)
val c2 = c match {
    case RGB(r, _, b) => RGB(r+15, 0, b+15)
}
```
[/LIST]

[*]if/else is the ternary operator
[*]macros - compile time calculation and other trickery
[*]lazy values/call by name parameters - parameters and values that are not calculated until they are used.
[LIST]
[*]```

def time(f: => Unit) = { //Unit is the equivalent of void in java
  val start = System.currentTimeMillis()
  f
  System.currentTimeMillis - start
}

time( 5+12 ) // returns the amount of time needed to run this calculation
time { 
   val a = Array(5,6,7)
   a.toList
} // same

lazy val x = y //doesn't error out because y is defined by time x is called.
val y = 15.5l
```
[/LIST]
[/LIST]

That's just off the top of my head. Scala is very much a hybrid imperative/object oriented/functional language and it has plenty of benefits over java even without using it's functional capabilities.

---

### Post by slickymaster on 2013-05-14
Let me first start by saying that it wasn't, and it isn't, my intention to start any sort of meaningless discussion over one language versus the other. I was just stating to the OP my feeling/opinion over the way I see both languages.

I do recognize the aspects of Scala that make it so appealing, on a developer's point of view, things like richer libraries, reduced need to code for the lowest common denominator programmer, transformational rather than procedural approach, and so on.
Scala is a powerful language, no doubts about it, it's like two languages in one. It is a clever fusion of OO and strict functional programming and is regarded as the ultimate language to date for writing libraries and embedded DSL’s with static types. Many things that are specialized syntax in other languages are just library code in Scala. You can warp the syntax to many uses, all within a static type system. Libraries can be modularly extended and composed without modifying their sources. These abilities go way beyond any prior statically typed language and for me, _in my personal opinion_, the problem is that these abilities come at a high cost in complexity. The syntax has so many ways of doing things that it can be bewildering. As with Macro-based languages, you are always a little uncertain about what your code is really doing underneath.

Simply put, or putting it in a figurative way, to me in Java before you can hammer a nail you have to go build a hammer. Scala just gives you the hammer and it’s up to you not to hit your thumb with it!

---

### Post by Edward_G_Prentice on 2013-08-29
I think Scala has a learning curve that is steeper than some other languages, but the rewards are great.  The job market has been slow to heat up for Scala developers, so don't start learning if you're looking to get paid to write Scala. Not just yet, anyway. On the other hand, since it will take a while to learn and many many months of practice, you might as well get started. Google can help you find resources. I recommend the coursera.org course on Functional Programming.

---

