---
title: "FAQ: Compiling and Running Java Programs"
date: 2008-03-02
forum: Programming Talk
---

### Post by LaRoza on 2008-03-02
**Working on the rest, post suggestions as well. I am not skilled or experienced in Java**

So you're willing to write your own Java programs, or simply compile someone else's code? This guide will get you started...

This FAQ assumes you're trying to compile *error-free* code. To actually learn the Java languages, see the [How to start programming](http://ubuntuforums.org/showthread.php?t=333867) thread.

[SIZE="5"]**0.a. Make sure the [COLOR="Blue"]third party repositories[/COLOR] are enabled**[/SIZE]

The easiest way to do this is open Applications->Add/Remove and select "All Available Applications".

[SIZE="5"]**0.b. Make sure the [COLOR="Blue"]sun-java6-jdk[/COLOR] package is installed**[/SIZE]

This package installs the essential tools needed to write and run Java programs.

```
sudo aptitude install sun-java6-jdk
```

Also run this to set the Sun Java as the default.
```

sudo update-java-alternatives --set java-6-sun

```

[SIZE="5"]**1. Compiling your [COLOR="Blue"]first Java program[/COLOR]**[/SIZE]

Copy & paste this code into a new file. Save the file as **Main.java**
[php]
//First Java Program
class Main
{
    public static void main (String[] args) 
   { 
       System.out.println ("Hello, world.");
   }
}
[/php]
Open a terminal, go to the directory where you saved **Main.java**, and type:
```
javac Main.java
```If all went fine, nothing is printed and you get back to the shell. Now, run it:
```
java Main
```"Hello World!" gets printed in the terminal.

**Explanations:**[list][*] **[COLOR="Navy"]javac[/COLOR]** is the Java compiler
[*] obviously, **[COLOR="Navy"]Main[/COLOR]** means that the compiler must compile this file.
[*] **[COLOR="Navy"]java Main[/COLOR]** runs the newly compiled executable.[/list]


[SIZE="5"]**2. [COLOR="Blue"]Paranoid programming[/COLOR] is good for your health!**[/SIZE]

Many beginners want to avoid compiler errors and warnings at *any* cost, which often leads them to ignore the "cryptic" messages the compiler outputs and to tinker anxiously with the relevant line until the error goes away.
**Don't fall in that trap!** The compiler is your friend, the messages it outputs are *kind advices* rather than *punishments*. You should really take the time to try and understand those messages, this is a very good way to improve your code's quality.

As a matter of fact, most seasoned programmers set the compiler's warning level as high as possible, so that it catches the little errors they make when they aren't paying much attention.

**Help needed** Post in thread to recommend content or deletion of this section.


[SIZE="5"]**3. [COLOR="Blue"]Useful tips[/COLOR]**[/SIZE]

**Help needed** Post in thread to recommend content or deletion of this section.

[SIZE="5"]**4. [COLOR="Blue"]Read the manual![/COLOR]**[/SIZE]

Plain old manpage:
```
man java
```

Naturally, the Documentation and Tutorial on the Sun site is a great place to get answers: [http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)


Thanks to so many people @UF for their very useful help, this FAQ wouldn't be the same without them. In particular, this thread is based on aks44's thread on C and C++ (see link in sticky). Not only is this thread based on it, it is blatently copying it, I hope he doesn't mind...

---

### Post by petzworld999 on 2008-03-02
Wouldn't it be this?

```

javac Main.java

```

Whenever I compile a file without the extension the compiler spits at me.

---

### Post by LaRoza on 2008-03-02
> **petzworld999 said:**
> Wouldn't it be this?

Whenever I compile a file without the extension the compiler spits at me.

Quite right, thanks. It has been a while...

---

### Post by mssever on 2008-03-03
Just a small suggestion: Blue text looks like a link (even if the site in question doesn't use blue links). Changing your text highlight color to something other than blue would improve the usability of the page. (useit.com has some info on this, though I don't have the exact link handy.)

---

### Post by pmcastillo on 2008-03-03
Thanks!!! This would be very good for those who are beginning with programming! ^_^

---

### Post by HuBaghdadi on 2008-03-03
One more thing:
In order to set Sun Java SDK's tools as the default for your Ubuntu, run the following command:
sudo update-java-alternatives --set java-6-sun

---

### Post by Vladislav Mkrtychev on 2008-06-02
Thanks!
Page one instructions worked for me - no probs!
I got another question: Does Linux(Ubuntu) have it's 
developing tool like DrJava or something similar?

Thanks.

---

### Post by LaRoza on 2008-06-02
> **Vladislav Mkrtychev said:**
> Thanks!
Page one instructions worked for me - no probs!
I got another question: Does Linux(Ubuntu) have it's 
developing tool like DrJava or something similar?

Thanks.

[http://drjava.org/](http://drjava.org/)

It works on Linux.

---

### Post by xlinuks on 2008-06-02
3. Useful tips
After the user gets comfortable with compiling and running the hello world app, would be good to let him know that nowadays every modern Java program is inside (let's call it) a package namespace. Anonymous packages (like the one in LaRoza's example) should be avoided since it's considered to be a bad habit (more precisely since JDK 1.4). This is especially true when sharing/using third-party libraries to avoid class name collisions.
Since this is probably gonna scare/confuse the user, I think the explanation/example should be very short and comprehensive.
[http://en.wikipedia.org/wiki/Java_package](http://en.wikipedia.org/wiki/Java_package)
only shows how to import packages, not how the user can create/compile/run them.

---

### Post by themusicwave on 2008-06-02
You may also want to add links to the major Java APIs these are really helpful and I always have them open anytime I am writing Java.

Here is the page that leads to the various APIs:
[http://java.sun.com/reference/api/]("http://java.sun.com/reference/api/")

Also, java ranch has some great cattle drives for beginers at:
[http://www.javaranch.com/java-college.jsp]("http://www.javaranch.com/java-college.jsp")

Otherwise it's a pretty good intro to Java.

---

### Post by LaRoza on 2008-06-02
These FAQ's are just how to get thing working on Ubuntu, not intros to the languages. The compiling of the sample programs are just to show it works (and a general howto)

My wiki is dedicated to learning, and those links are on it.

---

### Post by themusicwave on 2008-06-02
We should also add some information abotu setting the CLASSPATH.  That can be a major source of issues for newbies and experienced programmers alike.

There are several ways to do this and I am not sure which one is best really.  I know the path is: /usr/lib/jdk1.6.0/bin

Any suggestions on which way to set the CLASSPATH.

---

### Post by jamesstansell on 2008-06-03
> **themusicwave said:**
> 
Any suggestions on which way to set the CLASSPATH.

For larger projects you should define the classpath through a project definition via ant, maven, or your IDE.

For small projects it should be fine to just use the -cp option to javac, perhaps from a shell script for convenience.

---

### Post by Èync on 2008-06-03
javac *.java
This works

---

### Post by Vladislav Mkrtychev on 2008-06-08
> **LaRoza said:**
> [http://drjava.org/](http://drjava.org/)

It works on Linux.

Thanks. I got it installed.
However, when I try to compile, It says "No Compiler Available"
or something similar.
Any ideas on where the compiler might be?

---

### Post by NormR2 on 2008-06-08
I've never had an IDE with interactive debugging and have had to rely on print statements to tell me where the program is executing and how variables values are changing.

For example:  System.out.println("Here I am. x=" + x);

Often conditional using a boolean so I can turn the output on and off with a single statement change:```

	boolean debug = true;			
		...
       if(debug){
          System.out.println("Here I am. x=" + x);
	 } 
```		

To find out how a method is being called, I add the following statementin the method to print the call stack:
```

      try{throw new Exception("who called");}catch(Exception ex) {ex.printStackTrace();}

```
You'll need the -g option on the javac compile to have the statement numbers in the code.

If the method is called many times you may only want to see it once:
```

   boolean oneTime = true;
     ....
    if(oneTime) {
      oneTime = false;
      try{throw new Exception("who called");}catch(Exception ex) {ex.printStackTrace();}
   }
```


Finding NullPointerException in large program that doesn't have enough try{}catch blocks:
Copy the NullPointerException.java class from the source.zip file for your JDK and modify by adding:
```

    // Insert our own special debugging version
    public String getMessage() {
      try{throw new Exception("Where am I");}catch(Exception ex){ex.printStackTrace();}
      return super.getMessage();
    }
```
Compile it and put the class file(s) in its own jar file. Prepend that jar file to the classpath for the java program using the -Xbootclasspath option:
```

java  -Xbootclasspath/p:D:\JavaDevelopment\MyJavaClasses.jar -classpath .... ...

```
When you get a NullPointerException, your code will be called with its printStackTrace() showing who called.

---

### Post by turtlepaul on 2008-06-09
> **Vladislav Mkrtychev said:**
> Thanks. I got it installed.
However, when I try to compile, It says "No Compiler Available"
or something similar.
Any ideas on where the compiler might be?

Same thing for me. It says that it is unable to locate 'tools.jar'.

---

### Post by NormR2 on 2008-06-09
> It says that it is unable to locate 'tools.jar'.
What is the "It" you refer to?

---

### Post by jamesstansell on 2008-06-09
> **NormR2 said:**
> What is the "It" you refer to?

I believe they're talking about DrJava.  Here is what the quickstart guide has to say:

"To compile programs in DrJava, you must make sure you have a Java JDK (Java Development Kit) installed on your machine."

[http://drjava.org/quickstartdocs/gettingready.html](http://drjava.org/quickstartdocs/gettingready.html)

To turtlepaul and vladislav:

That page talks about manually downloading and installing the Java SDK from Sun, but hopefully you can just use synaptic to install the sun-java6-jdk package.

Hopefully just installing the JDK package will get things working, but if not then the tools.jar preference mentioned at [http://drjava.org/quickstartdocs/preferences.html](http://drjava.org/quickstartdocs/preferences.html) may need to be set.

---

### Post by turtlepaul on 2008-06-16
I found the tools.jar file and put the location in in the preferences, and it still doesn't work. It says it's incompatible.

---

### Post by NormR2 on 2008-06-17
It would help if you would copy and post the full text of the error message you are getting.

---

### Post by LaRoza on 2008-06-17
> **NormR2 said:**
> It would help if you would copy and post the full text of the error message you are getting.

...on another thread.

---

### Post by Shin_Gouki2501 on 2008-06-17
if certainly i had too much time and i would consider some kind of :
create GUI's using Eclipse RCP
FAQ. You think that would fit into ubuntu programming forums? Or would it be too complex ?
For myself i'm deeply impressed by the productivity which is offered by the API and i would like to share that experience.

---

### Post by LaRoza on 2008-06-17
> **Shin_Gouki2501 said:**
> if certainly i had too much time and i would consider some kind of :
create GUI's using Eclipse RCP
FAQ. You think that would fit into ubuntu programming forums? Or would it be too complex ?
For myself i'm deeply impressed by the productivity which is offered by the API and i would like to share that experience.

Sure, write up a howto, and we can have a small tutorials section in the sticky for non basic things. That would be cool.

---

### Post by Shin_Gouki2501 on 2008-06-17
I have already something , which i "just" need to translate into english. When i'm done , i'll post again!

---

### Post by Flynn555 on 2008-10-09
thank you!

this was very helpful...
thinking of taking a java course next semester, i wanna get a head start ;)

---

### Post by monkeystuner on 2008-10-09
Thanks, this tutorial was helpful to me...

---

### Post by 0cton on 2009-04-06
I think a usefull tip would be to use an IDE
such as Eclipse or Neatbeans

---

### Post by anotherusernametoforget on 2011-09-13
The following does not, in fact, install anything for me. I imagine the file is obsolete... but I'm a newb so I'll dust off a years-old thread




This package installs the essential tools needed to write and run Java programs.

 	Code:
 	sudo aptitude install sun-java6-jdk

---

### Post by sisco311 on 2011-09-13
Outdated. Thread closed.

@anotherusernametoforget

I moved your post here: [http://ubuntuforums.org/showthread.php?t=1843630](http://ubuntuforums.org/showthread.php?t=1843630)

---

