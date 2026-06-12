---
title: "a java package/classpath lesson for noobs like me with Prefuse (prefuse.org) demos"
date: 2009-10-19
forum: Programming Talk
---

### Post by InkyDinky on 2009-10-19
For a class project I made the somewhat unwise decision to choose the java api prefuse (prefuse.org).  I typically write in C++ but figured learning another language and adding it to my repertoire wouldn't hurt. Well, so far it hasn't hurt too much.  

Step 1: download and unzip the prefuse-beta-20071021.zip package. 
Step 2: try to figure out how to compile the daggone demos! I like IDEs as much as the next person but sometimes I find them too bulky. Eclipse and NetBeans are just too bulky and bog down my computer. For directions on compiling the demos via theses IDEs go here:[www.cs.mun.ca/~hoeber/teaching/cs4767/notes/04-prefuse/]("www.cs.mun.ca/~hoeber/teaching/cs4767/notes/04-prefuse/")
Step 3: Learn about the classpath variable. Unlike C++ java uses a set directory path structure for its packages. Packages are sets of classes organized in a deliberate manner. Here are two great resources I found that helped me solve my problem.
[http://www.javaworld.com/javaforums/showflat.php?Number=21619]("http://www.javaworld.com/javaforums/showflat.php?Number=21619")[http://www.cs.usfca.edu/~parrt/course/601/lectures/java.tools.html]("http://www.cs.usfca.edu/~parrt/course/601/lectures/java.tools.html")
Also the official Java description didn't hurt :[java.sun.com/j2se/1.3/docs/tooldocs/win32/classpath.html]("java.sun.com/j2se/1.3/docs/tooldocs/win32/classpath.html")
So I wanted to compile the Congress demo.  For me it was found at /home/[user]/Documents/Projects/prefuse-beta/demos/prefuse/demos/Congress.java.  I needed to tell the compiler where to find the prefuse class files. The prefuse class files are found in the prefuse.jar which was placed here:/home/[user]/Documents/Projects/MySQLStockMarketData/prefuse-beta/build/prefuse.jar to do this I needed to set the classpath variable during compile time
javac -cp /home/[user]/Documents/Projects/MySQLStockMarketData/prefuse-beta/build/prefuse.jar Congress.java
I executed the previous command from within the folder that the Congress.java file was found i.e. /home/[user]/Documents/Projects/prefuse-beta/demos/prefuse/demos/ 
Yeah it compiled without a hitch!
Step 4: Run the compiled code: 
So I tried :
java Congress 
from the /home/[user]/Documents/Projects/prefuse-beta/demos/prefuse/demos/ directory and got 
Exception in thread "main" java.lang.NoClassDefFoundError: Congress (wrong name: prefuse/demos/Congress)
	at java.lang.ClassLoader.defineClass1(Native Method) ....
as the error output.
This [http://www.cs.usfca.edu/~parrt/course/601/lectures/java.tools.html]("http://www.cs.usfca.edu/~parrt/course/601/lectures/java.tools.html") helped me to figure out my problem.
The way that the demos were packaged was setup in a directory structure such that I needed to execute my java command from the /home/[user]/Documents/Projects/prefuse-beta/demos/ directory because the packaged class was telling the compiler to look in prefuse/demos for the Congress class file. ***[see note at end]
So I needed to change my java call to 
java prefuse.demos.Congress
but then I got this error:
Exception in thread "main" java.lang.NoClassDefFoundError: prefuse/render/RendererFactory
Caused by: java.lang.ClassNotFoundException: prefuse.render.RendererFactory
So even though I didn't think that I needed to set the classpath for the compiled class it turns out that I did.
java -cp .:/home/[user]/Documents/Projects/prefuse-beta/build/prefuse.jar prefuse.demos.Congress
gave a clean compile but...it was missing the data file.
so from /home/[user]/Documents/Projects/prefuse-beta/demos/ I executed cp prefuse/demos/fec.txt .
Re-executing java -cp .:/home/[user]/Documents/Projects/prefuse-beta/build/prefuse.jar prefuse.demos.Congress
gave me a clean compile and clean run of the program.
[note] in the above java command there are two classpaths present. We need the current directory specified so that java knows where to find the Congress.class file. The period (.) tells it to include the current directory. Remember how the compiled Congress.class file was made in /home/[user]/Documents/Projects/prefuse-beta/demos/prefuse/demos/ but we are executing this command from the /home/[user]/Documents/Projects/prefuse-beta/demos/ directory!  We separate additional classpath variables with the colon. The second variable tells the compiler where to find the other prefuse libraries (specifically prefuse.render.RendererFactory ) This may not seem intuitive but the prefuse.jar is just an archive preserving the desired directory structure.  You can open the prefuse.jar file and find a render folder with a RendererFactory.class file in that folder.

To recap:
Set the classpath variable when compiling a file that relies on packages.
Set the classpath variable when running a file that relies on packages.
Understand that Java imposes a logical directory structure when calling the members of a class or when importing subclasses.
***[note] I believe that this error could have easily been overcome by removing/commenting out  the package prefuse.demos; line of Congress.java.  This would have removed the packaging structure imposed and I believe I could've safely compiled the code from there via this command : java -cp .:/home/[user]/Documents/Projects/prefuse-beta/build/prefuse.jar Congress
No guarantees but it should be that or something relatively close to get it to work.

---

