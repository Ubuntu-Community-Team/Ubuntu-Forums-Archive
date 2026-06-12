---
title: "Help with java!"
date: 2008-01-05
forum: Programming Talk
---

### Post by theparticle010 on 2008-01-05
First of all I don't want anyone to compile code for me I want to know how to compile code! I have this mile thick book on the topic of Java so  I thought I'd read it, so I did, and now I can't make any Programs! So if someone could recommend a devolment kit, and how to use it, I would really really like that.

Just Rember that I do not want you to compile anything, I want to know how to compile the code on my own.

---

### Post by LaRoza on 2008-01-05
See [http://laroza.wikidot.com](http://laroza.wikidot.com) and the Java page to help you get started.

---

### Post by pmasiar on 2008-01-05
I don't want to start flamewars, but if Java is not hard requirement, IMNSHO Python is much simpler language to start learning programming. You can easily switch to Java after you learn and understand programming basics, which are language-independent: variables, loops, functions, scope (local/global/module), debugging, data structure design. Of course you will have to learn Java's way of handling same issues, but knowing two languages will enable you to understand what is just syntax of a specific language, and what is real programming issue.

And Python books are not mile thick. :-) Wiki in my sig has links to free online books.

And Python compiles code for you without any effort - it is invisible, as it should be. :-)

---

### Post by LaRoza on 2008-01-05
> **pmasiar said:**
> I don't want to start flamewars, but if Java is not hard requirement, IMNSHO Python is much simpler language to start learning programming. You can easily switch to Java after you learn and understand programming basics, which are language-independent: variables, loops, functions, scope (local/global/module), debugging, data structure design. Of course you will have to learn Java's way of handling same issues, but knowing two languages will enable you to understand what is just syntax of a specific language, and what is real programming issue.

And Python books are not mile thick. :-) Wiki in my sig has links to free online books.

And Python compiles code for you without any effort - it is invisible, as it should be. :-)

@OP If you have no real reason to use Java, and are just starting out the above advice is seconded by me. No reason to make things tough on yourself.

---

### Post by kevykev on 2008-01-05
If you're looking for a development kit for java, eclipse is an excellent choice: [http://www.eclipse.org]("http://www.eclipse.org"). Netbeans is another good one: [http://www.netbeans.org/]("http://www.netbeans.org/"). Both can be installed from the ubuntu repositories. I.e.

```

sudo apt-get install eclipse

```

If you want to compile java code from the command line, you can do the following: Assuming you have a java file Test.java (using the default package: i.e. no package) you can compile it to byte code using the following command:

```

$ javac Test.java

```

This will produce a file Test.class. If the class contains a main method, you can run the resulting class file with the following command

```

$ java Test

```

Hope this helps,
Kevin

---

### Post by popch on 2008-01-05
Somewhere within the miles of of your java books you find instructions on how to download the jdk (java developer's toolkit which contains java compiler) and how to use it to compile and run your programs. The most straightforward way is probably just looking up [www.sun.com](www.sun.com) or perhaps [www.java.com](www.java.com).

If it is still called 'jdk'. They have a way of changing product names every decade or two.

HOWEVER: if you have no compelling reason to use Java, I would suggest to follow the excellent advice already given by two members, i.e. to start with Python.

---

### Post by kevykev on 2008-01-05
> **popch said:**
> Somewhere within the miles of of your java books you find instructions on how to download the jdk (java developer's toolkit which contains java compiler) and how to use it to compile and run your programs. The most straightforward way is probably just looking up [www.sun.com](www.sun.com) or perhaps [www.java.com](www.java.com).

Actually, I'd advise installing java from the ubuntu repositories using
```

$ sudo apt-get install sun-java6-jdk

```

That will setup all your path variables and such for you, and will allow updates to java to be auto-installed by your Update Manager

---

### Post by popch on 2008-01-05
> **kevykev said:**
> Actually, I'd advise installing java from the ubuntu repositories using
```

$ sudo apt-get install sun-java6-jdk

```

Much better advice than mine; thank you.

---

### Post by themusicwave on 2008-01-05
I also would advise you to install the jdk using apt.  Once you have that if you really want to compile from the command line it is easy.

I prefer eclipse personally, but it's always good to know how it works in the command line too.  Once you have the JDK installed try this to confirm it.

Here is a little tutorial for you:

Open a terminal/shell

$gedit Workin.java

paste in the following program:

public class Workin{

	public static void main(String args[]){

		System.out.println("Hey I Work!");
	}

}

Save the program as Workin.java(the capital W is important).

No in the shell run

$javac Workin.java

This will compile the program for you.  If there are errors they will be listed out.  There shouldn't be any, there weren't when I compiled it.

Now if you run an ls command you will see 2 files.  They are Workin.java which is the source code.  Also, there is Workin.Class, this is the compiled bytecode that the Java Virtual Machine runs.  

Now run your program on the shell enter

$java Workin

You should see the message Hey I work

Congratualtions you've compiled and run a Java program!  If you have any problems let me know.  I have a decent knowledge of Java, certainly not a master yet, but I am getting there :)

As for python Vs Java, I am currently learning python.  It is simpler, but I still prefer Java.  This is probably because Java uses C syntax and requires data types.  I miss my datatypes in python(I now they are there underneath).  Java was also my first love in programming, the first language I got really got good at so I am biased too.  

Hope it works out well for you,

Jon

---

### Post by LaRoza on 2008-01-05
My first post outlined the installation of the JDK and how to use it.

---

### Post by theparticle010 on 2008-01-06
Thanks Everybody, Yes I've tried Python, but the thing is I'm looking for more of GUI tools and I can't seem to find any in python so thats why I've stuck with Java, I've tried Perl, C, C++, And others, but they just seam to be unfiendley, I cant find many tools and python requires many things for building GUIs so I'm sticking to Java.

I'll Try everything here, except the Python ^_^

       :popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by LaRoza on 2008-01-06
> **theparticle010 said:**
> Thanks Everybody, Yes I've tried Python, but the thing is I'm looking for more of GUI tools and I can't seem to find any in python so thats why I've stuck with Java, I've tried Perl, C, C++, And others, but they just seam to be unfiendley, I cant find many tools and python requires many things for building GUIs so I'm sticking to Java.

I'll Try everything here, except the Python ^_^


Python comes with Tkinter for GUI's and wxWidgets and GTK are easily installed.

---

### Post by theparticle010 on 2008-01-06
Java and python similar (not in sintax) but not the same, python is interpreted, and that means that programs **will** run slower, While Java is compiled into byte-code which is also interpreted, but byte-code **is** faster. While c++ is compiled for each system type.

What I'm getting at is that What I plan on making is meant to run at a good pace, and I want it to be available on all Operating Systems that support the JRE.
'
By the way, does anyone know how to make a jar file that JRE can run directly, I know there is a tool that will do that for me, but I can't rember what It was called. I think its jar c or something.

---

### Post by jespdj on 2008-01-07
> **theparticle010 said:**
> Java and python similar (not in sintax) but not the same, python is interpreted, and that means that programs **will** run slower, While Java is compiled into byte-code which is also interpreted, but byte-code **is** faster. While c++ is compiled for each system type.
Reality is more complicated than that. Sun's JVM includes a JIT (Just In Time) compiler, which translates Java byte code at runtime to native machine code. This makes Java run quite fast. I don't know much about Python but AFAIK it can also be compiled to a kind of byte code.

Sun has a great set of tutorials for Java: [The Java Tutorials](http://java.sun.com/docs/books/tutorial/)

---

### Post by The Cog on 2008-01-07
It's even more complicated than that. java starts off interpreted and runs quite slowly. Then after a while (maybe a couple of seconds) it switches to a compiled version that has been optimised by profiling the interpreted version, at which point it suddenly runs very much faster.

The only fully cross-platform GUI for java that I know of is the AWT/SWING kit that comes with Sun's runtime. In my experience, this is somewhat slower than most other more platform-limited toolkits like GTK, WX etc. Also in my opinion, the AWT/SWING fonts are horrible decades old throwbacks.

Python is surprisingly fast at some things because it makes calls into precompiled library code. So it can produce quite fast and reasonably good-looking GUIs. 

In general, I'd say python is better for smaller projects, and java is better for large projects. But for GUIs, I really don't think much of java/swing. I think this is laregly why java has remained a server-side technology.

---

### Post by theparticle010 on 2008-01-07
I really don't care what the fonts look like, I know a couple of tricks that can allow you to produce you own "font," athough It will be limited to the program in question, thats all I need to make what I want.

---

### Post by pmasiar on 2008-01-08
It is even more complicated than that :-)

If you develop web-based app, about 80% od response time is spent between browser, web server, and database server. So even if you run remaining code in no time, you shave only 20% of total runtime. That's why it makes sense to use the more productive language for server-side development (Python), and almost ignore the speed issue (think about algorithm and overall design, not about optimizing loops and calls).

And Python's precompiled library code is often written in C - which is faster than average Java library.

BTW Python has also run-time optimizing compiler which inspects code in terms which types are used (at runtime), and optimizes code runtime - just not enough people care to use it.

And good thing is that with Python, even big project stay small, because AFAICT it takes 1/3 of the code to accomplish same thing :-)

IMHO, YMMV. Test and measure, then decide.

---

### Post by theparticle010 on 2008-01-08
I know that python is a good laungauge for most people, and I know that Java really is not the best langauge to use for building apps, but I do know that I like Java and that is what I will use, someday when I get everything done with my website, and when I am done building what I want and need I will most likely pick up a book on python.

---

### Post by LaRoza on 2008-01-08
> **theparticle010 said:**
> I know that python is a good laungauge for most people, and I know that Java really is not the best langauge to use for building apps, but I do know that I like Java and that is what I will use, someday when I get everything done with my website, and when I am done building what I want and need I will most likely pick up a book on python.
Use what you want :)

If you want to peruse good learning material on other languages, or on Java, see my wiki.

---

### Post by xlinuks on 2008-01-08
> **theparticle010 said:**
> Java and python similar (not in sintax) but not the same, python is interpreted, and that means that programs **will** run slower, While Java is compiled into byte-code which is also interpreted, but byte-code **is** faster. While c++ is compiled for each system type.

What I'm getting at is that What I plan on making is meant to run at a good pace, and I want it to be available on all Operating Systems that support the JRE.
'
By the way, does anyone know how to make a jar file that JRE can run directly, I know there is a tool that will do that for me, but I can't rember what It was called. I think its jar c or something.
To create an executable JAR file:
1) Create a java file (since the package is called "xx" it must be in a subfolder called "xx", thus in ${HOME}/xx):
```

package xx;

public class Test {
	public static void main( String[] args ) {
		javax.swing.JOptionPane.showMessageDialog( null, "Hello", "title", 1 );
	}
}

```
2) Compile it. From ${HOME} run "javac xx/*.java".
3) Create a "manifest" file that tells java what your .jar file should look like, in our case we need to tell java what will be our "main" class that will run when double-clicking the .jar file, thus, create a file in ${HOME} called "manifest.mf" with only one single line of plain text "Main-Class: Test", and - IMPORTANT - at the end of the line hit ENTER. (The file must end with the new line character)
4) Finally create the .jar file. From the ${HOME} folder run:
```

jar cmf manifest.mf Test.jar xx/Test.class

```
You will get the executable .jar file called "Test.jar".
You should play with it, then after you get into basic compiling/packaging routines, you might wanna start using NetBeans/Eclipse to speed up the process, or, create shell scripts to automate the process of development.
Regards

---

### Post by CptPicard on 2008-01-08
I would just like to point out that Java isn't bad. I use it all the time, and even in intense number-crunching work you can pretty much achieve the performance of non-optimized gcc output (without an -O3 flag for example). I just tried compiling my latest, greatest achievement (a complete analysis of a highly combinatorial domain, spends hours crunching) with gcj, and the end result was slower than just running it through "java".

The gotcha with Java is often a coding style that spams garbage objects all over the place and thus triggers lots of gc, not to mention all the other memory referencing overhead you get by having an object graph that changes a lot all the time. But the old adage applies: Don't Be Stupid.

Also the language takes more hate than it deserves. The only real issue with it is verbosity, but Use The Right Tools, such as Netbeans or Eclipse, and the pain is taken away. I actually am quite dependent on having a proper code-completing, auto-suggesting IDE.

On one point I do agree wholeheartedly... Java's web development is a horrible mess. It's unneccessarily Byzantine, and the learning curve is just horribly steep before you can achieve anything.

---

### Post by theparticle010 on 2008-01-08
Thaney have JRE installed ) or in some cases just right clickks [xlinuks]("http://ubuntuforums.org/member.php?u=235329") I really wanted to know how to do that, my main thing was to have a program that you could just click on and have it work ( If they have JRE installed ) or in some cases just right click on it, I downloaded the Java version of Frozen Bubble to play on my windows computer and It works fine, thats when I got the Idea of building a jar file for my program, and if the programs get to big I can always just make a jar installer with some if, else statements that will determine the system type and install the correct files.

And I don't know about the rest of you but I see no reason not to use Java in web design.. I know how slow It can be, but sometimes it's worth the wait, the only thing I don't like about Java and using it in the navigation of a website, is that it takes a million years to load and it's useless, I mean use something different, my site uses an iFrame and a mac like dock made out of css and ajax.

---

### Post by CptPicard on 2008-01-08
> **theparticle010 said:**
> 
And I don't know about the rest of you but I see no reason not to use Java in web design.. I know how slow It can be, but sometimes it's worth the wait, the only thing I don't like about Java and using it in the navigation of a website, is that it takes a million years to load and it's useless

You are talking about applets, and I was talking about server-side Java, which is an atrociously complex set of libraries, not to mention the development methodology is very cumbersome. Try setting up ant scripts for deployment of your test site, for example.

Applets have their place, but like Flash, should be used sparingly.

---

### Post by theparticle010 on 2008-01-09
[LEFT]I aggree that applets should be used only once and a while for a game or something, but for server-side scripting I'd use something like Perl and some providers now will even offer python, however I'd rather use Perl, I don't know why but the commands for Perl *seem* to be pointed at web servers.
[/LEFT]

---

### Post by xlinuks on 2008-01-09
Partly you prolly mean (rightfully) that the JVM start up time is slow (especially the so called "cold start" - when the JVM starts for the first time after you started the computer).
_IF_ we are lucky enough we will have soon (within a year or so) a Java platform based on a single "kernel" (in this regard Sun pays too much attention to windows, hopefully we'll get it on Linux as well, within same timeframe). It means you will no longer have to wait that long for a Java program/applet to start, roughly saying it will start as fast as an average little flash app you see all over the internet (that is in almost no time). The concept of a new Java kernel means that all Java applications will execute within a single instance of the Java Virtual Machine (JVM).., so no more waiting long seconds till an applet starts and no more resources spent (in vain) on every instance of a (JVM). It probably sounds too well, but who knows.. If you wanna read more go to Sun's Java site or google for "Java update N". But even though it won't be ideal, from different points of view, for instance for a web developer on the client side might be the lack of any built in video support nor cam or alike.. It's all just about (even) better memory management and speed (for instance IMHO over flash).

---

### Post by theparticle010 on 2008-01-09
OK I picked up my book and looked at different scripts, and which I should start with, I knew how to do most of the more simple things that involved just text and input and output, so I tried building something harder, a doodle program that uses a canvas and mouse events to draw lines and stuff on the screen, I compiled the canvas and that ( as far as I know ) it works, it's just the program it's self,  the compiler wont let me import the canvas...

this is what I typed in the terminal:

[email]particle010@theparticle010:~/Desktop/.Java[/email]-Programs/Java$ java Doodle.java
Doodle.java:1: '.' expected
import DoodleCanvas;
                   ^
1 error
[email]particle010@theparticle010:~/Desktop/.Java[/email]-Programs/Java$

I get this every time, and it doesn't matter if I change the canvas name to "dude" I still get the same error!!!

---

### Post by xlinuks on 2008-01-09
"java Doodle.java" - javac should be used to compile. Anyway it's hard to help when we can't see the (complete) source code and the file hierarchy they lie in (and the way you're trying to compile), it all matters..

---

### Post by LaRoza on 2008-01-09
> **xlinuks said:**
> "java Doodle.java" - javac should be used to compile. Anyway it's hard to help when we can't see the (complete) source code and the file hierarchy they lie in (and the way you're trying to compile), it all matters..

No, "javac Doodle.java", java to run.

---

### Post by theparticle010 on 2008-01-09
Ooops I pasted the code in wrong, but I still got the same message, and here is the source code:


```
import DoodleCanvas;

import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

public class Doodle extends Applet implements ActionListener
{

  private int APPLET_WIDTH = 300;
  private int APPLET_HEIGHT = 250;
  
  
  private Label titleLabel;
  private DoodleCanvas canvas;
  private Button clearButton;


 public void init ()
{

  titleLabel = new Label ("Doodle using the mouse.");
  titleLabel.setBackground (Color.cyan);
  add (titleLabel);

  canvas = new DoodleCanvas();
  add (canvas);

  clearButton = new Button("clear");
  clearButton.addActionListener (this);
  add (clearButton);

  setBackground (Color.cyan);
  setSize (APPLET_WIDTH, APPLET_HEIGHT);

}

  public void actionPerformed (actionEvent event)
{

  canvas.clear();
}

}
```

---

### Post by Deakon on 2008-01-09
it interests me how everyone is criticizing the difficulty of java, when a couple years ago, everyone was saying it was too easy and would be telling you to just go C... ;)

---

### Post by pmasiar on 2008-01-09
Couple years ago, Java was great new language with OOP for mere mortals, and garbage collected memory, much simpler than C++.

These days, plenty of new languages (Python, Ruby, D) do GC and OOP, and with dynamic typing and other cool features leave Java in the dust. And evan Java is realizing the shackles of static typing, why I would do generics if I can have cleaner dynamic typing in Jython?

---

### Post by xlinuks on 2008-01-10
> **LaRoza said:**
> No, "javac Doodle.java", java to run.

That's exactly what I mean, you misunderstood me. I quoted the guy for using "java Doodle.java" and told him that javac should be used instead.

---

### Post by xlinuks on 2008-01-10
> **theparticle010 said:**
> Ooops I pasted the code in wrong, but I still got the same message, and here is the source code:


import DoodleCanvas;

import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

public class Doodle extends Applet implements ActionListener
{

  private int APPLET_WIDTH = 300;
  private int APPLET_HEIGHT = 250;
  
  
  private Label titleLabel;
  private DoodleCanvas canvas;
  private Button clearButton;


 public void init ()
{

  titleLabel = new Label ("Doodle using the mouse.");
  titleLabel.setBackground (Color.cyan);
  add (titleLabel);

  canvas = new DoodleCanvas();
  add (canvas);

  clearButton = new Button("clear");
  clearButton.addActionListener (this);
  add (clearButton);

  setBackground (Color.cyan);
  setSize (APPLET_WIDTH, APPLET_HEIGHT);

}

  public void actionPerformed (actionEvent event)
{

  canvas.clear();
}

}

This is a bit a subtle issue.
1) In the early days of Java development you were not forced to use a package to compile a program. Thus there were no issues doing imports by specifying just  the class (without mentioning a package, thus "import DoodleCanvas;" worked fine ). In later versions (since version 1.3 I guess) you are practically forced to use a package, this is believed (by SUN) to be the way to do programming in Java.
2) If it doesn't help consider posting the second class you prolly forgotten to post (DoodleCanvas.java)
3) To help us helping you, you should use the corresponding tags for code formatting (put the between [ code ] .. [ / code ] tags, without spaces ). It will (greatly) improve the code readability.

---

### Post by kevykev on 2008-01-10
Please stop bashing java people. It's a great language, it's mature, fast, flexible and has good industry acceptance. Also static typing can be beneficial, esp for catching errors at compile time.

Don't get me wrong, python is excellent too. C++ is great when I need high performance (for image processing algorithms, for instance) and C is perfect for systems programming. Point is that I use the tool I feel is most appropriate, or the one I am most comfortable with, for a given job.

---

### Post by theparticle010 on 2008-01-10
Oops! I swear that I'm brain-dead sometimes... 
   ^_^ ^_^ ^_^ ^_^ ^_^ ^_^ ^_^ ^_^ 
here is the source code for DoodleCanvas  Oh just to let you all know, this one already compiled

```
import java.awt.*;
import java.awt.event.*;

class DoodleCanvas extends Canvas implements MouseListener,
                                             MouseMotionListener
{

  private final int CANVAS_WIDTH = 200;
  private final int CANVAS_HEIGHT = 200;

  private int lastX, lastY;

  public DoodleCanvas ()
  {

    addMouseListener (this);
    addMouseMotionListener (this);


    setBackground (java.awt.Color.white);
    setSize(CANVAS_WIDTH, CANVAS_HEIGHT);

  }


  public void mousePressed (MouseEvent event)
  {

    Point first = event.getPoint();
    lastX = first.x;
    lastY = first.y;
  }

  public void mouseDragged (MouseEvent event)
  {

    Point current = event.getPoint();

    Graphics page = getGraphics();
    page.drawLine (lastX, lastY, current.x, current.y);

    lastX = current.x;
    lastY = current.y;

  }

  public void clear ()
  {

    Graphics page = getGraphics();
    page.drawRect (0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
    repaint();

  }



  public void mouseReleased (MouseEvent event) {}
  public void mouseClicked (MouseEvent event) {}
  public void mouseEntered (MouseEvent event) {}
  public void mouseExited (MouseEvent event) {}
  public void mouseMoved (MouseEvent event) {}

}
```

---

### Post by slavik on 2008-01-10
> **pmasiar said:**
> I don't want to start flamewars, but if Java is not hard requirement, IMNSHO Python is much simpler language to start learning programming. You can easily switch to Java after you learn and understand programming basics, which are language-independent: variables, loops, functions, scope (local/global/module), debugging, data structure design. Of course you will have to learn Java's way of handling same issues, but knowing two languages will enable you to understand what is just syntax of a specific language, and what is real programming issue.

And Python books are not mile thick. :-) Wiki in my sig has links to free online books.

And Python compiles code for you without any effort - it is invisible, as it should be. :-)
How does compiling Java relate to Python? Please let people learn what they want to learn.

---

### Post by Unterseeboot_234 on 2008-01-11
I was struggling with Jython. I love Python. I hate the GUI choices for Python. The Python GUIs have absolutely dismal docs and books available. So, I thought I'd try Jython. Java6 can mimic Vista even. With Jython, you are forced to construe pathnames for a) the javac; b) python.home; c) jython.jar. Code actually compiles. It really does! But, then try to run the heap and the pathnames to reconnect the MyApplet.class become a nightmare. Trying to pack everything in a .jar or .war makes things even worse, one will have to edit the manifest file in the .jar because the Sun jdk has it's own ideas about pathnames and records what it wants to do in cachedir. I think we have to wait for Jython 3.0. Jythonc -- equivalent of javac -- is on it's way out.

As it stands now, I have learned to uninstall the Ubuntu repository versions of Sun JDK, and the Ubuntu Jython 2.1 with all its embedded sym-links and keep my own installs of those two development kits in the home directory. Otherwise, you can just forget about using a database without invoking Root privileges.

---

### Post by xlinuks on 2008-01-11
> **theparticle010 said:**
> Oops! I swear that I'm brain-dead sometimes... 
   ^_^ ^_^ ^_^ ^_^ ^_^ ^_^ ^_^ ^_^ 
here is the source code for DoodleCanvas  Oh just to let you all know, this one already compiled

```
import java.awt.*;
import java.awt.event.*;

class DoodleCanvas extends Canvas implements MouseListener,
                                             MouseMotionListener
{

  private final int CANVAS_WIDTH = 200;
  private final int CANVAS_HEIGHT = 200;

  private int lastX, lastY;

  public DoodleCanvas ()
  {

    addMouseListener (this);
    addMouseMotionListener (this);


    setBackground (java.awt.Color.white);
    setSize(CANVAS_WIDTH, CANVAS_HEIGHT);

  }


  public void mousePressed (MouseEvent event)
  {

    Point first = event.getPoint();
    lastX = first.x;
    lastY = first.y;
  }

  public void mouseDragged (MouseEvent event)
  {

    Point current = event.getPoint();

    Graphics page = getGraphics();
    page.drawLine (lastX, lastY, current.x, current.y);

    lastX = current.x;
    lastY = current.y;

  }

  public void clear ()
  {

    Graphics page = getGraphics();
    page.drawRect (0, 0, CANVAS_WIDTH, CANVAS_HEIGHT);
    repaint();

  }



  public void mouseReleased (MouseEvent event) {}
  public void mouseClicked (MouseEvent event) {}
  public void mouseEntered (MouseEvent event) {}
  public void mouseExited (MouseEvent event) {}
  public void mouseMoved (MouseEvent event) {}

}
```

1) As I mentioned somewhere above, there should be used packages.
2) I would use JApplet instead of Applet (the Applet class is deprecated ..)
The screenshot of it working
[http://xlinuks.googlepages.com/doodle.jpg](http://xlinuks.googlepages.com/doodle.jpg)
3) The java classes, Doodle.java (there was the typo "actionEvent"):
```

package xx;

//sometimes (at least in NetBeans AFAIK) you don't have import
//the classes that are in some packages
//but depending on settings it might not work
//thus better always import files even if
//they are in same package

import xx.DoodleCanvas;//or just xx.*;

import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

public class Doodle extends Applet implements ActionListener {

	private int APPLET_WIDTH = 300;
	private int APPLET_HEIGHT = 250;
	
	
	private Label titleLabel;
	private DoodleCanvas canvas;
	private Button clearButton;
	
	
	public void init () {
		titleLabel = new Label( "Doodle using the mouse." );
		titleLabel.setBackground( Color.cyan );
		add( titleLabel );
		
		canvas = new DoodleCanvas();
		add( canvas );
		
		clearButton = new Button( "clear" );
		clearButton.addActionListener( this );
		add( clearButton );
		
		setBackground( Color.cyan );
		setSize( APPLET_WIDTH, APPLET_HEIGHT );
	}
	
	public void actionPerformed( ActionEvent event ) {
		canvas.clear();
	}
}

```

DoodleCanvas.java:
```

package xx;

import java.awt.*;
import java.awt.event.*;

//thus de facto the class name turns to xx.DoodleCanvas

class DoodleCanvas extends Canvas implements MouseListener, MouseMotionListener {

	private final int CANVAS_WIDTH = 200;
	private final int CANVAS_HEIGHT = 200;

	private int lastX, lastY;

	public DoodleCanvas () {
		
		addMouseListener( this );
		addMouseMotionListener( this );
		
		setBackground( Color.white );
		setSize( CANVAS_WIDTH, CANVAS_HEIGHT );
	}


	public void mousePressed( MouseEvent event ) {
		
		Point first = event.getPoint();
		lastX = first.x;
		lastY = first.y;
	}
	
	public void mouseDragged( MouseEvent event ) {
		
		Point current = event.getPoint();
		Graphics page = getGraphics();
		page.drawLine( lastX, lastY, current.x, current.y );
		
		lastX = current.x;
		lastY = current.y;
	}
	
	public void clear () {
		
		Graphics page = getGraphics();
		page.drawRect( 0, 0, CANVAS_WIDTH, CANVAS_HEIGHT );
		repaint();
	}
	
	public void mouseReleased (MouseEvent event) {}
	public void mouseClicked (MouseEvent event) {}
	public void mouseEntered (MouseEvent event) {}
	public void mouseExited (MouseEvent event) {}
	public void mouseMoved (MouseEvent event) {}
}

```
To successfully compile, say your code is in {HOME}/xx, from {$HOME} run "javac xx/*.java"
Later, after you get used to it, consider packaging all your classes and resources inside a jar file, that would increase the download speed (partially because the browser has to send only one query to the server to download a single .jar file instead of querrying for every single file).

---

### Post by Unterseeboot_234 on 2008-01-11
Most of the problems with java on the Ubuntu box have to deal with the path names. I completely recoded a project I was doing to see what I was doing wrong. And, I went back to my NetBeans IDE install which includes the Ubuntu repositories for Java6 and Jython 2.1. I got it to work  :)  I can now have a Swing GUI with python doing the numbers crunching and logic. And, I edit the python, not the java to improve the logic.

I can't say enough about the NetBeans IDE. NetBeans allows textbook examples for code -- something Eclipse nor JBuilder will let you do very easily. Setting up anything with more than one class is a breeze with NetBeans because the IDE slam-dunks the pathnames for each Run and configures all the packages correctly. Thus, you get software that is cross-platform that have a java  JVM.

---

### Post by theparticle010 on 2008-01-11
Thanks that will really help a lot, I have an older book, and I know some of the commands will be useless... and the book was written in 2000 so I can imagine that after 8 years... But hey! thanks! Now I know how to import all of the classes that I need! ^_^

---

### Post by theparticle010 on 2008-01-11
AHHHH Firefox glitch sorry about the repeated post

---

### Post by xlinuks on 2008-01-11
Hey you should really consider dropping that book, there are a few good ones that are free and you can download in the internet (google for "Thinking in Java") or I can send you a few commercial ones if you PM your email. I had a similar story, I started learning Java when there was already Java2, so much I learned was useless at the time.. I wouldn't like you to do the same mistake..
ps: I was learning the old version of Java cause I didn't know at the time that there was  a new one..

---

### Post by pmasiar on 2008-01-11
> **slavik said:**
> How does compiling Java relate to Python? Please let people learn what they want to learn.

I am not sure what OP's original goal is, my ESP crystal ball is clouded. Yours work better I hope? :-)

If OP's goal is to learn programming in general (and ultimate goal to learn multiple languages, each good fit in particular area), starting with simpler language (like Python) is better, IMHO. BTW, this is also opinion of many CompSci experts, I am not alone.

OTOH if OP's goal is to become single-language (Java) code monkey with no clue or interest in other languages, of course learning other languages will be a grave mistake. :-)

FYI, my current project in work is in Java, so I do have a clue (and frustrations) about differences.

---

### Post by slavik on 2008-01-11
> **pmasiar said:**
> I am not sure what OP's original goal is, my ESP crystal ball is clouded. Yours work better I hope? :-)

If OP's goal is to learn programming in general (and ultimate goal to learn multiple languages, each good fit in particular area), starting with simpler language (like Python) is better, IMHO. BTW, this is also opinion of many CompSci experts, I am not alone.

OTOH if OP's goal is to become single-language (Java) code monkey with no clue or interest in other languages, of course learning other languages will be a grave mistake. :-)

FYI, my current project in work is in Java, so I do have a clue (and frustrations) about differences.
OP's goal was to compile Java code, nothing in there about learning how to program. If the OP wanted info on languages, we have stickies.

---

### Post by jespdj on 2008-01-11
> **pmasiar said:**
> I am not sure what OP's original goal is, my ESP crystal ball is clouded. Yours work better I hope? :-)

If OP's goal is to learn programming in general (and ultimate goal to learn multiple languages, each good fit in particular area), ...
Well, the OP did mention Java in his first post so it's safe to assume that he wants to know about Java. You are assuming that he wants to learn programming in general - despite the OP specifically mentioning Java. Don't use your crystal ball if it's clouded... ](*,) and carefully read the OP's post.

Note that the title of the post is "Help with **Java**!"

Everybody knows you love Python, you're pushing it everywhere you can. But if someone asks a question that's not about Python, then please stay on topic.

---

### Post by Wybiral on 2008-01-11
> **jespdj said:**
> Well, the OP did mention Java in his first post so it's safe to assume that he wants to know about Java. You are assuming that he wants to learn programming in general - despite the OP specifically mentioning Java. Don't use your crystal ball if it's clouded... ](*,) and carefully read the OP's post.

Note that the title of the post is "Help with **Java**!"

Everybody knows you love Python, you're pushing it everywhere you can. But if someone asks a question that's not about Python, then please stay on topic.

IMO this reply is off topic by discussing reply-validity and not discussing "**Help** with Java!" :)

(this could get recursive)

---

### Post by pmasiar on 2008-01-11
[quote=OP]I have this mile thick book on the topic of Java so I thought I'd read it, so I did, and now I can't make any Programs[/quote]

My crystal ball said me OP is not 100% happy with what he has, and has hard time to start programming. 

I qualified my advice by "if Java is not hard requirement" and waited for OP to respond. You decided for OP to limit her learning to Java only. I don't, at this is IMHO all difference. Have a nice day.

---

