---
title: "making java applets"
date: 2008-12-01
forum: Programming Talk
---

### Post by rtoot3 on 2008-12-01
how can i start making java applets for the web?
first of all, what code do i use to install java
second, does anyone know a good tutorial?

---

### Post by rtoot3 on 2008-12-01
comon, theres gotta be somone who knows java! also i have another question, can you use my sql with java?

---

### Post by CptPicard on 2008-12-01
> **rtoot3 said:**
> how can i start making java applets for the web?

I guess Netbeans would be good, I like the GUI editor...

> 
first of all, what code do i use to install java

Read stickies

> 
second, does anyone know a good tutorial?

Google Is Your Friend!

> **rtoot3 said:**
> also i have another question, can you use my sql with java?

Yes, JDBC works with a lot of database, MySQL included.

---

### Post by drubin on 2008-12-01
> **rtoot3 said:**
> comon, theres gotta be somone who knows java! also i have another question, can you use my sql with java?

Firstly please wait at least 24hours before bumping your threads I was busy answering one of your other posts. Things take time.

Take a look at my sig for installing Java and as for learning java  [http://java.sun.com](http://java.sun.com) has some great tutorials. 

But you need to be more specific as to what you would like to do. Also Applets have odd permissions issues. I suggest starting with a simple application at first to try out your new Java Skills

---

### Post by drubin on 2008-12-01
> **CptPicard said:**
> Yes, JDBC works with a lot of database, MySQL included.

I prefer the native drivers. [http://dev.mysql.com/usingmysql/java/](http://dev.mysql.com/usingmysql/java/)

Never done comparisons as to which is better/faster yet.

---

### Post by rtoot3 on 2008-12-01
> **drubin said:**
> Firstly please wait at least 24hours before bumping your threads I was busy answering one of your other posts. Things take time.


oops, sorry, ill do that next time, also thanks.

---

### Post by rtoot3 on 2008-12-01
do you need to compile an applet, or do you just save it as .class and then you can load it in a webpage. i got pretty good at one time with both normal java applications and java applets. but its been a while and i need some refreshing, thanx.

EDIT:
nevermind, found out.

---

### Post by Mr.Macdonald on 2008-12-01
this is where I learnt to first program, with applets. May it do you well

[http://javaboutique.internet.com/tutorials/Java_Game_Programming/]("http://javaboutique.internet.com/tutorials/Java_Game_Programming/")

and not to make you turn from Java, for I once would only program in Java, but if it ever seems boring, move to Python and then C++/C. Those are far funner, and if your up for a challenge (I mean it, don't post questions for help) try Prolog, Awk or Lisp

---

### Post by jespdj on 2008-12-02
> **drubin said:**
> I prefer the native drivers. [http://dev.mysql.com/usingmysql/java/](http://dev.mysql.com/usingmysql/java/)

Never done comparisons as to which is better/faster yet.
What do you mean with "I prefer the native drivers"? You make it sound like JDBC and "native driver" are two different things, but they aren't.

JDBC is the standard API to talk with databases from Java, and you use a JDBC driver to talk with a database. Your link points to the page for the JDBC driver for MySQL.

There's no question of "which is better/faster".

---

### Post by Geekkit on 2008-12-02
> **jespdj said:**
> What do you mean with "I prefer the native drivers"? You make it sound like JDBC and "native driver" are two different things, but they aren't.

JDBC is the standard API to talk with databases from Java, and you use a JDBC driver to talk with a database. Your link points to the page for the JDBC driver for MySQL.

There's no question of "which is better/faster".

[http://java.sun.com/javase/6/docs/technotes/guides/jdbc/getstart/intro.html#1019423](http://java.sun.com/javase/6/docs/technotes/guides/jdbc/getstart/intro.html#1019423)

---

### Post by jespdj on 2008-12-02
> **Geekkit said:**
> [http://java.sun.com/javase/6/docs/technotes/guides/jdbc/getstart/intro.html#1019423](http://java.sun.com/javase/6/docs/technotes/guides/jdbc/getstart/intro.html#1019423)
So? Yes, there are different JDBC driver types. But they all work with the JDBC API. There is no "JDBC vs. native driver" question. The native driver *is* a JDBC driver.

---

### Post by drubin on 2008-12-02
> **jespdj said:**
> What do you mean with "I prefer the native drivers"? You make it sound like JDBC and "native driver" are two different things, but they aren't.

JDBC is the standard API to talk with databases from Java, and you use a JDBC driver to talk with a database. Your link points to the page for the JDBC driver for MySQL.

There's no question of "which is better/faster".

/me hangs his head in shame! 

I thought it was a question of odbc... vs jdbc. 

ps.
I need to stop posting so late at night I seem to always make these mistakes. We definitely need something like [this ]("http://gmailblog.blogspot.com/2008/10/new-in-labs-stop-sending-mail-you-later.html")

---

### Post by Reiger on 2008-12-02
Class files are compiled versions of the Java source files; so no: "just saving as .class" won't cut it.

You'll need to install a JDK. Quite a few people prefer to use Sun's own; which you can get by typing:  sudo aptitude install sun-java6-jdk in a terminal. You will be prompted to accept Sun's license agreement.

As you are apparently new to Java I'd recommend you start out with installing an IDE next. Both Netbeans and Eclipse are popular choices. I know some people say "learn it the hard, basic, down-to-raw-source way", but personally I found it very relieving not having to worry about handling the finer details of compiling: that's one thing the IDE will automatically do for you. The other is sourcecode highlighting, and giving you a shell of orts to run/monitor your code in. (Of course an IDE can do much, much more but it requires some 'learing how the IDE works' to get your IDE to do that.)

---

### Post by rtoot3 on 2008-12-02
> **Mr.Macdonald said:**
> this is where I learnt to first program, with applets. May it do you well

[http://javaboutique.internet.com/tutorials/Java_Game_Programming/]("http://javaboutique.internet.com/tutorials/Java_Game_Programming/")

and not to make you turn from Java, for I once would only program in Java, but if it ever seems boring, move to Python and then C++/C. Those are far funner, and if your up for a challenge (I mean it, don't post questions for help) try Prolog, Awk or Lisp

i have programmed with c++ and python before, and they are a lot more fun to me than java.  but the reason i want to program in java is because you can use them in browsers.

---

### Post by rtoot3 on 2008-12-02
i wrote this code from a simple tutorial that makes a ball move across the screen

```

import java.applet.*;
import java.awt.*;

public class ball extends Applet implements
Runnable
{
    //integers
    int x_pos = 10;
	int y_pos = 100;
	int radius = 20;

    public void init(){}
    
    public void start()
    {
        //define new thread variable
        Thread th = new Thread(this);
        //make it happen
        th.start();
    }
    
    public void stop(){}
    
    public void destroy(){}
    
    public void run()
    {
        //low priority
        Thread.currentThread().setPriority(Thread.MIN_PRIORITY);
        
        //always
        while(true)
        {
            x_pos += 1;
            //repaint
            repaint();
        
            try
            {
                //wake me up in 20 milliseconds
                Thread.sleep(20);
            }
            catch (InterruptedException ex)
            {
                //nothins goin on here
            }
            
            // set ThreadPriority to maximum value
            Thread.currentThread().setPriority(Thread.MAX_PRIORITY);
        }
    }
    
    public void paint (Graphics g)
    {
        //set color
        g.setColor(Color.red);
        
        //paint a filled colored circle
        g.fillOval(x_pos - radius, y_pos - radius, 2 * radius, 2* radius);
    }
    
}

```

i was messing around with the code in order to understand it more. and for some reason what ever i changed, even very big changes, i never noticed any difference in the browser. im compiling it and everything. and im begining to think maybe when i compile it, instead of compiling the last saved version, it is compiling the little autosaved version ubuntu makes. by the auto saved version i mean the files that end with a ~. how could i fix this? theres definitely something wrong, because if you look in the while loop where it says "x_pos += 1", i tried changing it to "x_pos += 300! then i saved it and compiled it and it still did the exact same thing!

---

### Post by jespdj on 2008-12-02
> **rtoot3 said:**
> i was messing around with the code in order to understand it more. and for some reason what ever i changed, even very big changes, i never noticed any difference in the browser.
First, when you change the source code, you have to recompile it (are you doing that?) and second, browsers have a cache and if you don't refresh the page in the browser properly (with Ctrl + F5) you might be looking at an old version that the browser got out of its cache, instead of your newer version.

How are you compiling your source code? It's very unlikely that you're actually compiling the backed up version (with the ~ at the end).

---

### Post by rtoot3 on 2008-12-02
> **jespdj said:**
> First, when you change the source code, you have to recompile it (are you doing that?) and second, browsers have a cache and if you don't refresh the page in the browser properly (with Ctrl + F5) you might be looking at an old version that the browser got out of its cache, instead of your newer version.

How are you compiling your source code? It's very unlikely that you're actually compiling the backed up version (with the ~ at the end).

i am recompiling it, and as for reloading it i first tried using the reload button at the top of the browser, then i tried re entering the location, then i did the ctrl + F5 thing and it still displayed the same thing. and if anyone is about to ask, yes, i save it before i recompile it.

---

### Post by jamesstansell on 2008-12-02
> **rtoot3 said:**
> i have programmed with c++ and python before, and they are a lot more fun to me than java.  but the reason i want to program in java is because you can use them in browsers.

Starting with the java 6u10 browser plugin it's said to be possible to program your applet using jython, jruby, groovy, etc.  Sun will probably formalize this more with the javafx script release later this week.

[http://javafx.com/](http://javafx.com/)

Regards,

-james.

---

### Post by rtoot3 on 2008-12-03
> **jamesstansell said:**
> Starting with the java 6u10 browser plugin it's said to be possible to program your applet using jython, jruby, groovy, etc.  Sun will probably formalize this more with the javafx script release later this week.

[http://javafx.com/](http://javafx.com/)

Regards,

-james.

are you saying i could make java applets using python and ruby and all that? that would be great! then i wouldnt have to start learning java!

---

### Post by jamesstansell on 2008-12-03
> **rtoot3 said:**
> are you saying i could make java applets using python and ruby and all that? that would be great! then i wouldnt have to start learning java!

Well, it appears that's the way Sun is leaning.  That is, eventually, most of your applet might be written with those syntaxes.

But, you probably need to be something of an expert to even begin doing it now.  In the future, when documentation and live examples are available, you will still need to have a firm understanding of the java virtual machine, applet lifecycle, etc.

So I guess what I'm saying is go through the java tutorial right now.  Learn what's currently available, but anticipate some sweet new ways to do things.

There's a java tutorial at java.sun.com and one of the "trails" should focus on applets.  Also netbeans.org should have some tutorials, but I'm not sure how well organized those are.

Regards,

-james.

---

### Post by rtoot3 on 2008-12-03
ok, thanks!

---

### Post by rtoot3 on 2008-12-03
how would i download java so i could write programs on a mac (i use ubuntu, but i have a webdesign class and all the comps are macs) but i went to the java.sun.com and there was a ton of downloads, java ee, java me, java se, and i dont know what to download.

---

### Post by jamesstansell on 2008-12-03
> **rtoot3 said:**
> how would i download java so i could write programs on a mac (i use ubuntu, but i have a webdesign class and all the comps are macs) but i went to the java.sun.com and there was a ton of downloads, java ee, java me, java se, and i dont know what to download.

If you have a recent mac (10.4 or 10.5) you should already have the JDK installed.  Otherwise there is a download page from the apple developer connection.

Or you could try [http://www.apple.com/support/downloads/](http://www.apple.com/support/downloads/) and search for "java SE" or some other java variation.

---

### Post by rtoot3 on 2008-12-03
its an i-mac, would that have it pre installed?
also how would i get to the terminal in a mac?
and would i use the same code for compiling

---

### Post by jamesstansell on 2008-12-04
> **rtoot3 said:**
> its an i-mac, would that have it pre installed?
also how would i get to the terminal in a mac?
and would i use the same code for compiling

1) apparently some imacs have java pre-installed

[http://www.simongbrown.com/blog/2006/05/29/intel_imac_the_best_java_development_box_in_the_world.html](http://www.simongbrown.com/blog/2006/05/29/intel_imac_the_best_java_development_box_in_the_world.html)

2) I have my at the office set to auto-start and I don't remember how I got to it originally.  I'm sure it's under the Applications menu though.

3) MacOS X is based on the same unix foundation as Linux so shell commands are going to be very similar.  In addition Java was designed cross-platform.  Also Ant, Maven and other build tools even make compiling nearly the same across platforms.  For getting started 
you shouldn't notice much difference between ms/windows, macos and ubuntu.

---

### Post by rtoot3 on 2008-12-04
thanks, ill see if it works when i get to school

---

### Post by rtoot3 on 2008-12-04
> **rtoot3 said:**
> i wrote this code from a simple tutorial that makes a ball move across the screen

```

import java.applet.*;
import java.awt.*;

public class ball extends Applet implements
Runnable
{
    //integers
    int x_pos = 10;
	int y_pos = 100;
	int radius = 20;

    public void init(){}
    
    public void start()
    {
        //define new thread variable
        Thread th = new Thread(this);
        //make it happen
        th.start();
    }
    
    public void stop(){}
    
    public void destroy(){}
    
    public void run()
    {
        //low priority
        Thread.currentThread().setPriority(Thread.MIN_PRIORITY);
        
        //always
        while(true)
        {
            x_pos += 1;
            //repaint
            repaint();
        
            try
            {
                //wake me up in 20 milliseconds
                Thread.sleep(20);
            }
            catch (InterruptedException ex)
            {
                //nothins goin on here
            }
            
            // set ThreadPriority to maximum value
            Thread.currentThread().setPriority(Thread.MAX_PRIORITY);
        }
    }
    
    public void paint (Graphics g)
    {
        //set color
        g.setColor(Color.red);
        
        //paint a filled colored circle
        g.fillOval(x_pos - radius, y_pos - radius, 2 * radius, 2* radius);
    }
    
}

```

i was messing around with the code in order to understand it more. and for some reason what ever i changed, even very big changes, i never noticed any difference in the browser. im compiling it and everything. and im begining to think maybe when i compile it, instead of compiling the last saved version, it is compiling the little autosaved version ubuntu makes. by the auto saved version i mean the files that end with a ~. how could i fix this? theres definitely something wrong, because if you look in the while loop where it says "x_pos += 1", i tried changing it to "x_pos += 300! then i saved it and compiled it and it still did the exact same thing!

anyone got any news on this though?

---

### Post by rtoot3 on 2008-12-04
> **jamesstansell said:**
> If you have a recent mac (10.4 or 10.5) you should already have the JDK installed.  Otherwise there is a download page from the apple developer connection.

Or you could try [http://www.apple.com/support/downloads/](http://www.apple.com/support/downloads/) and search for "java SE" or some other java variation.

it does have java pre-installed i just found out, but i dont have permission to use the terminal. it has dream weaver though, and you can write in java with dreamweaver. but then how can i compile it?

---

### Post by rtoot3 on 2008-12-04
is there maybe an online compiler anybody knows about?

---

### Post by Reiger on 2008-12-04
(a) You could try and install an IDE which should handle any & all interaction with the Java Compiler.
(b) Do you actually have the SDK as well and not only the JRE installed?
(c) There's no online compiling service that I know of.

---

### Post by jamesstansell on 2008-12-04
> **Reiger said:**
> 
(c) There's no online compiling service that I know of.

Curiously I recently came across one, but it was from 1997, using a very old java version so I wasn't interested.

---

### Post by jamesstansell on 2008-12-04
> **rtoot3 said:**
> it does have java pre-installed i just found out, but i dont have permission to use the terminal. it has dream weaver though, and you can write in java with dreamweaver. but then how can i compile it?

I'm not familiar with dreamweaver but there is a chance that it can compile.

No access to the terminal?  That's harsh!

Is there a lab assistant who might "show off" how you can use the lab to do what you want?

---

### Post by rtoot3 on 2008-12-05
> **jamesstansell said:**
>  1) I'm not familiar with dreamweaver but there is a chance that it can compile.

2) No access to the terminal?  That's harsh!

3)Is there a lab assistant who might "show off" how you can use the lab to do what you want?

1) i checked all over today, turns out you cant

2) yeah, but i talked to the teacher today about it and he gave my account the terminal, yay!

3) sadly, Im the best person with computers in my class. its just high school, and its not really a technology school, its just an elective im taking. the teacher even told me he can't really do most of the stuff i do, and i dont think what i do is very advanced.

also, still waiting to see if anyone knows whats happening here:
> **rtoot3 said:**
> i wrote this code from a simple tutorial that makes a ball move across the screen

```

import java.applet.*;
import java.awt.*;

public class ball extends Applet implements
Runnable
{
    //integers
    int x_pos = 10;
	int y_pos = 100;
	int radius = 20;

    public void init(){}
    
    public void start()
    {
        //define new thread variable
        Thread th = new Thread(this);
        //make it happen
        th.start();
    }
    
    public void stop(){}
    
    public void destroy(){}
    
    public void run()
    {
        //low priority
        Thread.currentThread().setPriority(Thread.MIN_PRIORITY);
        
        //always
        while(true)
        {
            x_pos += 1;
            //repaint
            repaint();
        
            try
            {
                //wake me up in 20 milliseconds
                Thread.sleep(20);
            }
            catch (InterruptedException ex)
            {
                //nothins goin on here
            }
            
            // set ThreadPriority to maximum value
            Thread.currentThread().setPriority(Thread.MAX_PRIORITY);
        }
    }
    
    public void paint (Graphics g)
    {
        //set color
        g.setColor(Color.red);
        
        //paint a filled colored circle
        g.fillOval(x_pos - radius, y_pos - radius, 2 * radius, 2* radius);
    }
    
}

```

i was messing around with the code in order to understand it more. and for some reason what ever i changed, even very big changes, i never noticed any difference in the browser. im compiling it and everything. and im begining to think maybe when i compile it, instead of compiling the last saved version, it is compiling the little autosaved version ubuntu makes. by the auto saved version i mean the files that end with a ~. how could i fix this? theres definitely something wrong, because if you look in the while loop where it says "x_pos += 1", i tried changing it to "x_pos += 300! then i saved it and compiled it and it still did the exact same thing!

---

### Post by rtoot3 on 2008-12-06
the way i learn is by taking tutorials. then when ive got the full code i mess around with it alot. over and over, which means alot of refreshing. so heres the problem, when i refresh a page alot with a java applet it eventually crashes firefox. how do i prevent this?

---

### Post by rtoot3 on 2008-12-07
does anyone know anywhere that explains with detail how to use collisions with a java applet?

---

### Post by jamesstansell on 2008-12-07
> **rtoot3 said:**
> the way i learn is by taking tutorials. then when ive got the full code i mess around with it alot. over and over, which means alot of refreshing. so heres the problem, when i refresh a page alot with a java applet it eventually crashes firefox. how do i prevent this?

Can you characterize how to reproduce the crash?  If you can explain it so that someone else can verify it then I'd say it's worth filing a bug report for.

---

### Post by rtoot3 on 2008-12-08
well id doesnt crash anymore when i reload it. i think my computer was just being slow. also i solved this problem...
> **rtoot3 said:**
> i wrote this code from a simple tutorial that makes a ball move across the screen

```

import java.applet.*;
import java.awt.*;

public class ball extends Applet implements
Runnable
{
    //integers
    int x_pos = 10;
	int y_pos = 100;
	int radius = 20;

    public void init(){}
    
    public void start()
    {
        //define new thread variable
        Thread th = new Thread(this);
        //make it happen
        th.start();
    }
    
    public void stop(){}
    
    public void destroy(){}
    
    public void run()
    {
        //low priority
        Thread.currentThread().setPriority(Thread.MIN_PRIORITY);
        
        //always
        while(true)
        {
            x_pos += 1;
            //repaint
            repaint();
        
            try
            {
                //wake me up in 20 milliseconds
                Thread.sleep(20);
            }
            catch (InterruptedException ex)
            {
                //nothins goin on here
            }
            
            // set ThreadPriority to maximum value
            Thread.currentThread().setPriority(Thread.MAX_PRIORITY);
        }
    }
    
    public void paint (Graphics g)
    {
        //set color
        g.setColor(Color.red);
        
        //paint a filled colored circle
        g.fillOval(x_pos - radius, y_pos - radius, 2 * radius, 2* radius);
    }
    
}

```

i was messing around with the code in order to understand it more. and for some reason what ever i changed, even very big changes, i never noticed any difference in the browser. im compiling it and everything. and im begining to think maybe when i compile it, instead of compiling the last saved version, it is compiling the little autosaved version ubuntu makes. by the auto saved version i mean the files that end with a ~. how could i fix this? theres definitely something wrong, because if you look in the while loop where it says "x_pos += 1", i tried changing it to "x_pos += 300! then i saved it and compiled it and it still did the exact same thing!
i found out if i just close the browser, open it up again and go to the page it changes.

---

