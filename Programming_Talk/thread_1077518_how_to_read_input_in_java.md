---
title: "how to read input in java?"
date: 2009-02-22
forum: Programming Talk
---

### Post by abhilashm86 on 2009-02-22
so if we want read input from user,like i want to read integers from user, 
alternate for scanf/raw_input in java??howto

> public class jp3
{
        public static void main(string args[])
        {
                int a,b,choice;

                system.out.println("enter the any one of following choices\n");
                system.out.println("1:add\n2:subtraction\n3:multiply\n");
..................

---

### Post by fiddler616 on 2009-02-22
> **abhilashm86 said:**
> so if we want read input from user,like i want to read integers from user, 
alternate for scanf/raw_input in java??howto

```
public class jp3
{
public static void main(string args[])
{
int a,b,choice;[B]
Scanner scan = new Scanner(System.in);[/B]

system.out.println("enter the any one of following choices\n");
system.out.print("1:add\n2:subtraction\n3:multiply:");[B]
int userInput = scan.nextInt();[/B]
.................. 
```
Read the API on the Scanner class in general (for String input and such)...

---

### Post by apoth on 2009-02-22
Old way:

[http://www.particle.kth.se/~lindsey/JavaCourse/Book/Part1/Java/Chapter09/consoleTextIn.html](http://www.particle.kth.se/~lindsey/JavaCourse/Book/Part1/Java/Chapter09/consoleTextIn.html)

New way (version 6 onwards I think?):

[http://www.java2s.com/Code/Java/Development-Class/UseScannertoreaduserinput.htm](http://www.java2s.com/Code/Java/Development-Class/UseScannertoreaduserinput.htm)

---

### Post by jimi_hendrix on 2009-02-22
imo java fails at reading input :)

---

### Post by abhilashm86 on 2009-02-22
> public class jp3
{
        public static void main (String args[])
        {
                int a,b,choice;
        //      Scanner scan=new Scanner(System.in);

                System.out.println("enter the any one of following choices\n");
                System.out.println("2:add\n2:subtraction\n3:multiply\n");

                choice=System.in.read();

                System.out.println(+choice);
        }
}
            
so following error was given,

abhilash@abhi:~$ javac jp3.java
----------
1. ERROR in jp3.java (at line 11)
	choice=System.in.read();
	       ^^^^^^^^^^^^^^^^
Unhandled exception type IOException
----------
1 problem (1 error)

how to check version of java being currently used?? 
java -v din't work

---

### Post by simeon87 on 2009-02-22
```

public static void main(String[] args) {
		try {
			BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
			String line = in.readLine();
			
			System.out.println("You just entered:  " + line);
			
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

```

---

### Post by jespdj on 2009-02-22
> **jimi_hendrix said:**
> imo java fails at reading input :)
What do you mean by this?

---

### Post by cabalas on 2009-02-22
> **jimi_hendrix said:**
> imo java fails at reading input :)

+1 - The amount of cruft you have to add to read command line input in java is just crazy.

---

### Post by jimi_hendrix on 2009-02-22
> **jespdj said:**
> What do you mean by this?

python: str = raw_input("input please");

C#: str = Console.ReadLine();

C++: cin.getline(str, 256);

C: str = gets(); /*depricated i know but i am too lazy to google the format for fgets*/

Erlang: str = io:get_line("input please");

java requires instantiation and other stuff...must i go on?

---

### Post by fiddler616 on 2009-02-22
> **jimi_hendrix said:**
> python: str = raw_input("input please");

C#: str = Console.ReadLine();

C++: cin.getline(str, 256);

C: str = gets(); /*depr**a**cated i know but i am too lazy to google the format for fgets*/

Erlang: str = io:get_line("input please");

java requires instantiation and other stuff...must i go on?
When I first learned about Scanner I had one of the biggest wtf moments of my programming life. Never mind about the difference between scan.next(), scan.nextLine(), scan.nextInt(), etc.
Python wins the prize, as usual, raw_input() gives you a string, and you can just wrap it up in an int() function (or _insert-datatype-here_ function) if you want something else.

---

### Post by Tomosaur on 2009-02-22
Input is my biggest annoyance with Java. Seriously, why does it have to be so damn stupid about it?

It's better to just emulate the C# way by creating a Console class like the example given by apoth, but it still requires way too much.

---

### Post by fiddler616 on 2009-02-22
> **Tomosaur said:**
> Input is my biggest annoyance with Java. Seriously, why does it have to be so damn stupid about it?

It's better to just emulate the C# way by creating a Console class like the example given by apoth, but it still requires way too much.
I also get pretty upset about applets...

---

### Post by jimi_hendrix on 2009-02-22
i am sorry linux world

C# > Java *ducks*

---

### Post by fiddler616 on 2009-02-22
> **jimi_hendrix said:**
> i am sorry linux world

C# > Java *ducks*
Java's more common though, as far as I know.
Also, the company that made it also made a ***ing RE for Linux (Mono's nice, but where's Microsoft Mono?)

---

### Post by jimi_hendrix on 2009-02-22
> **fiddler616 said:**
> Java's more common though, as far as I know.
Also, the company that made it also made a ***ing RE for Linux (Mono's nice, but where's Microsoft Mono?)

when we become popular it will appear

and C# is growing fast...i just read a post on stackoverflow.com about it

---

### Post by fiddler616 on 2009-02-22
> **jimi_hendrix said:**
> when we become popular it will appear

and C# is growing fast...i just read a post on stackoverflow.com about it
I don't know...the less we rely on Microsoft software the better, as far as I'm concerned. I just spent a *fun* hour today figuring out why my Zune software would only play the first thirty seconds of a given track. Don't get me wrong, I like Zunes a lot, but the software tends to drive me bonkers.
*ducks, as slavik swoops in and closes thread for being OT*

---

### Post by abhilashm86 on 2009-02-23
friends this topic is becoming a debate?? where is the solution?? i want a good book that has java from basics and number of programs?? can anyone tell, now i'm using head-first-java

---

### Post by directhex on 2009-02-23
> **abhilashm86 said:**
> friends this topic is becoming a debate?? where is the solution?? i want a good book that has java from basics and number of programs?? can anyone tell, now i'm using head-first-java

Try Deitel&Deitel. It worked for me when I was an undergrad

---

### Post by jespdj on 2009-02-23
> **jimi_hendrix said:**
> python: str = raw_input("input please");

C#: str = Console.ReadLine();

C++: cin.getline(str, 256);

C: str = gets(); /*depricated i know but i am too lazy to google the format for fgets*/

Erlang: str = io:get_line("input please");

java requires instantiation and other stuff...must i go on?
So you say "Java fails at reading input" just because the syntax looks strange and unfamiliar to you? Hmmm... :rolleyes:

What about this method:
```
System.out.println("What's your name?");
String name = System.console().readLine();
```
I really don't see how this is much more complicated than those other languages that you quoted.

> **Tomosaur said:**
> Input is my biggest annoyance with Java. Seriously, why does it have to be so damn stupid about it?
Because you didn't read the Java documentation or don't know how to use it?

> **Tomosaur said:**
> It's better to just emulate the C# way by creating a Console class like the example given by apoth, but it still requires way too much.
Lookup the class java.io.Console in the Java SE 6 API documentation.

---

### Post by abhilashm86 on 2009-02-23
> **jespdj said:**
> 
What about this method:
```
System.out.println("What's your name?");
String name = System.console().readLine();
```


i just tried this and found following error, 
> public class jp2
{
        public static void main (String[] args)
        {
        System.out.println("whts ur name?");
        System.out.println("What's your name?");
        String name = System.console().readLine();

        }
}






abhilash@abhi:~$ javac jp2.java
----------
1. ERROR in jp2.java (at line 7)
	String name = System.console().readLine();
	                     ^^^^^^^
The method console() is undefined for the type System
----------
1 problem (1 error)abhilash@abhi:~$

---

### Post by Zugzwang on 2009-02-23
> **abhilashm86 said:**
> 
1. ERROR in jp2.java (at line 7)
	String name = System.console().readLine();
	                     ^^^^^^^
The method console() is undefined for the type System
----------
1 problem (1 error)


Did you made sure that you are using the Sun JDK with a version number >= 1.6?

---

### Post by abhilashm86 on 2009-02-23
> **Zugzwang said:**
> Did you made sure that you are using the Sun JDK with a version number >= 1.6?

i am using following java version, i had initially used eclipse for learning python but using vim editor to learn java, is it correct version?
if not tell how to change? please help

abhilash@abhi:~$ javac -v
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

---

### Post by Tomosaur on 2009-02-23
> **jespdj said:**
> So you say "Java fails at reading input" just because the syntax looks strange and unfamiliar to you? Hmmm... :rolleyes:

What about this method:
```
System.out.println("What's your name?");
String name = System.console().readLine();
```I really don't see how this is much more complicated than those other languages that you quoted.


Because you didn't read the Java documentation or don't know how to use it?


Lookup the class java.io.Console in the Java SE 6 API documentation.

No, because this is ******* ugly: *System.console().readLine()*. Even using that, it is still better to wrap it up in a static method in a Console class so you can just use Console.readLine(). Just because Java now has a slightly less crappy way to read input does not make it  'good'.

---

### Post by simeon87 on 2009-02-23
> **Tomosaur said:**
> No, because this is ******* ugly: *System.console().readLine()*. Even using that, it is still better to wrap it up in a static method in a Console class so you can just use Console.readLine(). Just because Java now has a slightly less crappy way to read input does not make it  'good'.

I think you're overreacting here.. Java has simply chosen a different way of solving this than the one you would have preferred. In usage, the difference is minor anyway (ooh, a static method or a console() call in between).

---

### Post by Tomosaur on 2009-02-23
> **simeon87 said:**
> I think you're overreacting here.. Java has simply chosen a different way of solving this than the one you would have preferred. In usage, the difference is minor anyway (ooh, a static method or a console() call in between).

If you don't care about your software failing disastrously, then yes, the difference is minor. What jespdj neglected to mention is that to ensure we don't end up with errors and broken beaviour, reading from the console now **actually** requires the following:

```

Console cons = System.console();
string s;
if(cons != null){
      s = cons.readLine();
}

```

And if System.console() DOES return null when you don't expect it to, what do you do? Why, you try to instantiate Console yourself and check for exceptions! Assuming the JVM will always successfully instantiate the console if it exists is just not an option for many developers, unfortunately.

The Java API designers need to look up 'simplification' in the dictionary, as far as I'm concened.

---

### Post by howlingmadhowie on 2009-02-23
> **jimi_hendrix said:**
> i am sorry linux world

C# > Java *ducks*

that's a bit like saying friday the 13th part 5 has more intellectual depth than nightmare on elm street part 7.

---

### Post by howlingmadhowie on 2009-02-23
> **jespdj said:**
> 
```
System.out.println("What's your name?");
String name = System.console().readLine();
```


does that actually work nowadays? i know it doesn't work in netbeans, not sure about eclipse.

---

### Post by jimi_hendrix on 2009-02-23
@Tomosaur

thank you

and if sun's ide (netbeas is suns right?) doesnt support it then something is fishy...

@howie

i fail to see the logic of calling either language a horror movie...java is well known and used and i find .Net genious (i wish it was open source :()

---

### Post by howlingmadhowie on 2009-02-23
> **abhilashm86 said:**
> i am using following java version, i had initially used eclipse for learning python but using vim editor to learn java, is it correct version?
if not tell how to change? please help

abhilash@abhi:~$ javac -v
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.

you can check your jvm version by entering:

```

java -version

```
note the single minus sign. typical sun... #-o

---

### Post by fiddler616 on 2009-02-23
> **jimi_hendrix said:**
> java is well known and used
So are toilets. Does this make them elegant?

---

### Post by jimi_hendrix on 2009-02-23
> **fiddler616 said:**
> So are toilets. Does this make them elegant?

solid 24k gold ones are

---

### Post by fiddler616 on 2009-02-23
> **jimi_hendrix said:**
> solid 24k gold ones are
...Python? :)
(Actually, that would be kind of tacky, seems like...)

---

### Post by jespdj on 2009-02-24
> **Tomosaur said:**
> If you don't care about your software failing disastrously, then yes, the difference is minor. What jespdj neglected to mention is that to ensure we don't end up with errors and broken beaviour, reading from the console now **actually** requires the following: ...
So, what happens in C# / Python / some other language when you run the program without a console and you try to read user input from it? Will it magically work OK if the console is not there?

---

### Post by jespdj on 2009-02-24
> **abhilashm86 said:**
> abhilash@abhi:~$ javac -v
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.
Really strange that you have the Eclipse Java compiler setup in such a way that you can call it from the command line like that.

Install the JDK for Sun Java 6:
```
sudo apt-get install sun-java6-jdk
```
Then, use this command to make Sun Java 6 the default version of Java that's used on your system:
```
sudo update-alternatives --config java
```
If necessary, remove the directory that contains the javac from Eclipse from your PATH.

---

### Post by abhilashm86 on 2009-02-24
> **jespdj said:**
> Really strange that you have the Eclipse Java compiler setup in such a way that you can call it from the command line like that.


hey i actually installed eclipse through scratch, so i also have sun java installed i think, check this out,

 
abhilash@abhi:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

so should i need to upgrade or how to make it default version in command line??
i don't want eclpise as default

---

### Post by jespdj on 2009-02-24
> **abhilashm86 said:**
> abhilash@abhi:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
That's OpenJDK Java, which is not exactly the same as Sun Java. It's almost the same, so using this is OK.

Did you try the update-alternatives command? What does your PATH look like; does it have a reference to a directory containing an Eclipse version of javac?
```
echo $PATH
```

---

### Post by abhilashm86 on 2009-02-24
> **jespdj said:**
> 
Did you try the update-alternatives command? What does your PATH look like; does it have a reference to a directory containing an Eclipse version of javac?


yea i tried updating, its not updating as its latest version,

abhilash@abhi:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-22-generic linux-headers-2.6.24-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

so i guess using this jdk is not much difference to learn java,also

abhilash@abhi:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

i don't know much about path, hey but i compiled two java programs with no errors and i hope everything is working right:)thanls

---

### Post by Tomosaur on 2009-02-24
> **jespdj said:**
> So, what happens in C# / Python / some other language when you run the program without a console and you try to read user input from it? Will it magically work OK if the console is not there?

This:
```

try{
  //read input
}
catch(Exception ex){
 //deal with it
}

```

I'm willing to accept that Java has to do things differently because it runs on so many different platforms, but the fact that you have to check it twice is just stupid.

Anyway - as far as I can make out, the logic behind Java trying to get the console itself is this: 'You might need it'. I'd rather recognise **when** I need it and sort it out myself than have Java trying to be clever. It saves me no time or effort by forcing me to check for another point of failure.

---

### Post by jimi_hendrix on 2009-02-24
> **jespdj said:**
> So, what happens in C# / Python / some other language when you run the program without a console and you try to read user input from it? Will it magically work OK if the console is not there?

what do you mean?
last time i tried this (a long long time ago) it opened a terminal...until the program ended

if you mean some other type of input please specify

---

### Post by jespdj on 2009-02-25
> **jimi_hendrix said:**
> what do you mean?
last time i tried this (a long long time ago) it opened a terminal...until the program ended

if you mean some other type of input please specify
Tomosaur was complaining that if you run a Java program not from the console, System.console() returns null, and that you have to check if the console is really there or not, which makes the code a little bit longer than a single line System.console().readLine().

My response was that you'd have to so similar checking in other programming languages - so his argument that it's still more cumbersome in Java than in other programming languages is not valid.

---

### Post by Tomosaur on 2009-02-25
> **jespdj said:**
> Tomosaur was complaining that if you run a Java program not from the console, System.console() returns null, and that you have to check if the console is really there or not, which makes the code a little bit longer than a single line System.console().readLine().

My response was that you'd have to so similar checking in other programming languages - so his argument that it's still more cumbersome in Java than in other programming languages is not valid.

Who said anything about running the program from console? That's not what I was saying at all. My point was that if I need to use the console, and I want my code to be safe, then **I am forced to check the console twice** if I'm using Java. System.console() could return null for any number of reasons - there are other things which could go wrong than the console simply not being there.

Sanity says I should be doing this:
```

try
{
  //normal code including console input
}
catch(Exception)
{
 //failure code
}

```Whilst Java forces me to do this:
Java:
```

//You can put the if-else in the try-catch or whatever - the point is that you'll be doing both if you don't want your program to just fail miserably

Console c = System.console();
if(c != null)
{
 //continue
}
else
{
  try
  {
   //normal code including console input
  }
  catch(Exception)
  {
  //failure code
  }
}

```Obviously the Java code can look different - and that's precisely the problem. How do you do it in a way which means you've covered every eventuality? You have to check the console is not null - but where do you go from there? Since the JVM doesn't throw an exception, and I assume you don't just want your program to fail, you should check one more time since you haven't received an error. So you use a try-catch block (maybe). Oh but obviously you don't want to write the same code twice so you should probably put the actual console reading bit in a different method (and so on, and so on). This is absolutely ridiculous. Java has got it wrong here, plain and simple.

There is no standardised way to get console input because no matter what we do, we always have to check twice that we have received the console. The console should throw an exception if there's a problem, not just return null. It's all well and good that the JVM hides the error by just returning null - but until you receive an exception you don't know what the problem is. There's only so much hand holding the JVM can do before it starts causing its own problems (i.e this).

Exceptions should not be converted to return values for precisely this reason.

---

### Post by jimi_hendrix on 2009-02-25
> **jespdj said:**
> Tomosaur was complaining that if you run a Java program not from the console, System.console() returns null, and that you have to check if the console is really there or not, which makes the code a little bit longer than a single line System.console().readLine().

My response was that you'd have to so similar checking in other programming languages - so his argument that it's still more cumbersome in Java than in other programming languages is not valid.

i just tried:

```

print 'hello world'

```

and ran from a file browser...not cli...generated a console...

i am not trying to be a troll, just trying to understand the statement of the console not being there...

---

