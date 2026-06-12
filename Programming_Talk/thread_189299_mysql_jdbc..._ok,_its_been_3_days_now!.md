---
title: "mysql jdbc... ok, its been 3 days now!"
date: 2006-06-05
forum: Programming Talk
---

### Post by guitarded on 2006-06-05
please help before i go nuts!!!

for the past 3 days, i have  been trying to solve my mysql jdbc problem.

here is my classpath (copied from my bashrc file). with the location of my connector jar file..

CLASSPATH=$CLASSPATH:/usr/share/mysql/mysql-connector-java-3.1.12-bin.jar
export CLASSPATH

i am using netbeans and here is my code snippet...

try {
Class.forName("com.mysql.jdbc.Driver").newInstance();
        } catch (Exception ex) {
            System.out.println("Couldn't find the driver!");
            System.out.println("Lets' print out a stack trace");
            ex.printStackTrace();
            System.exit(1);
        }
        
        System.out.println("Registered the driver ok, so lets' make a connection");


of course, the app exits during the catch statement with the following errors...

Couldn't find the driver!
Lets' print out a stack trace
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at jammer.MainFrame.testMySQLConnection(MainFrame.java:55)
        at jammer.MainFrame.<init>(MainFrame.java:48)
        at jammer.Main$1.run(Main.java:32)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:461)
        at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:110)

---

### Post by guitarded on 2006-06-07
bump

---

### Post by adamkane on 2006-06-07
Not too many jdbc users on the forums. Please share any information or solutions you may find.

---

### Post by Csabo on 2006-06-07
1) Are you sure the class file is actually inside your jar?

2) Did you try putting the jar into the lib/ext directory of your Java runtime?

---

### Post by guitarded on 2006-06-07
there are several class files in the jar.  is there any specific file that i am looking for?

---

### Post by yaaarrrgg on 2006-06-07
is your program a web application?  For example, are you running JBoss/Tomcat/? 

Or are you building a standalone java app?

This basically looks like some sort of classpath problem... The problem is that you have the jar on your machine, but the java runtime has no privileged knowledge where it is, and can't find it.  Or maybe your permissions on the file are hiding it?

Although possibly this could be a NetBeans problem too (maybe not reading/passing the information to java).  Can you test this without NetBeans?  For example, for a stand alone app, you can pass a classpath to Java with:

```

java -cp "/path/to/file.jar"  YourMainClassName

```

Also, most web application servers have a lib folder where you can drop the connector.

I'd avoid using the IDE when debugging... it will only add another level of complexity to the problem.

---

### Post by Csabo on 2006-06-07
In your case it would be **com/mysql/jdbc/Driver.class**.

Also try an alternate to Class.forName: [http://www.darrenhobbs.com/archives/2002/09/classforname_is.html](http://www.darrenhobbs.com/archives/2002/09/classforname_is.html)

---

### Post by guitarded on 2006-06-07
first let me thank you folks for the help...

1.  this is a stand alone java application (not a web-based app).
2.  yes, Driver.java is in the jar
3.  i tried to compile and run outside of the netbeans environment and i get the same errors.
4.  i haven't tried putting the jar in the lib/ext directory of my Java runtime (i am searching for the dir - new to linux - any hints?).
5.  tried using the snippet on darren hobbs site and i still get a classnotfoundexception.

i have run this code on my window machine with no problem so i am sure it is some configuration error i am doing in linux.  i can, at least, eliminate that it is a netbeans config problem since i get the same errors when running outside of the ide.

i am pulling my hair out on this one.  if i can solve my (probably self-induced) problem, i can be well on my way.  i have been programming for a long time, but not on linux.  i have my mysql up and running and have created my tables and stored procedures.  just need to make this darn connection.

---

### Post by Csabo on 2006-06-07
4. Couldn't you just search for ext?

---

### Post by guitarded on 2006-06-07
the only one i find related to java is in the jdk directories.  howver, putting the jar in there does not help.

---

### Post by yaaarrrgg on 2006-06-08
could this be a permissions problem?  what happens if you run this as sudo?

for example:

```

sudo -i
cd  /to/your/project/
java   -cp  ".:/path/to/driver.jar"   YourMainClassName

```


I'm using the sun jdk 1.5 by the way.  Do you have any problems running other java programs/applets?  Perhaps something is corrupted in your installation (or perhaps the connector jar is bad?)

---

### Post by jvictor on 2006-06-08
1) I've used netbeans quite long back, and u were supposed to mount the jars, bcoz netbeans uses its own classpath. But I read somewhere that now u neednt mount jars .. if not there will be a equalent process to do so.

2) Check if its a corrupted jar by any chance, try making a copy of this jar and unzip it

3) Try copying the jar to the same pkg as ur class (JUST_TO_TEST) if we can get it working.

---

### Post by guitarded on 2006-06-08
thanks for persevering along with me...

yaaarrrgg, 

i tried to run it as root (sudo -i) and, of course, out of the netbeans environment, using the command line to compile/run as per your command line snippets.  i still get the same error.

as for jdk5, i am creating a stand-alone java app (no applets) and, with the exception with this jdbc problem (albeit, probably self-induced), it compiles and runs fine.

jvictor,

yeah, there is a setting in netbeans to "manage classpath".  i set the path there, but again, same error messages.  i think netbeans internally uses this because it does not actually edit the system's classpath.  in netbeans 5 there is also a feature where you can view and sort of manage the database.  you need to set the path for the jar and it tests the connection and connects to the database.  that part works, but of course, that is part of the netbeans environment.

ok, so get this... i installed and used eclipse.  i ported my code over and, of course, i got the errors, but... i found a feature to set the classpath in eclipse so i pointed to my jar and, wham bam, no errors.  again, like netbeans, it does not actually edit the system's classpath, it is used only in the eclipse project.  so this verifies that the jar file is not corrupt.

even tho i can get it to work with eclipse, i really want to be able to configure my machine so that i can use any environment (ide) or gedit, for that matter, and compile/run my app.  so i am still desperate for suggestions.

---

### Post by jvictor on 2006-06-09
Which file have u set the CLASSPATH ? I do it in ~/.bashrc.

In general if you are into serious development u stick to one environment / ide , so i guess since eclipse works fine for you , u must stick to it. ;) its jsut a humble suggestion. I too agree that it must be as flexible as possible , so till we find a work-around for this I suggest yu stick with eclipse. 

Im trying to reproduce your problem on my machine now and see where we stand.

---

### Post by jvictor on 2006-06-09
yes u r right, this is the code i wrote

import java.sql.*;

public class Test{
        private void testDB(){
                try{
                        Class.forName("com.mysql.jdbc.Driver");
                        System.out.println("LOADED");
                }
                catch(Exception e){
                        e.printStackTrace();
                }
        }//testDB ends
        public static void main(String args[]){
                Test testObj = new Test();
                testObj.testDB();
        }//main ends
}//Test ends


and look at the o/p

juby@fiero:~$ java -cp $CLASSPATH Test
LOADED

java Test
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at Test.testDB(Test.java:9)
        at Test.main(Test.java:21)


So we need to look into by installing a standalone JDK (from the bin file ) and use it rather than the one provided in Ubuntu

Further investigation is needed..


EDIT
-----
You need to set the CLASSPATH in ~/.bashrc **and export it too**; 

Earlier I dint set it in ~/.bashrc , i just set it in the shell on the fly, which didnt work, setting it in the ~/.bashrc solved the problem

juby@fiero:~$ java Test
LOADED

---

### Post by guitarded on 2006-06-09
aloha jvictor...

my classpath was set using .bashrc and export  here is the classpath line....

CLASSPATH=$CLASSPATH:/home/kepa/mysql/mysql-connector-java-3.1.12-bin.jar
export CLASSPATH

i verifiy my classpath using echo $CLASSPATH so i know its properly set.

the jdk was intalled using the bin file.

yes, for now i may have to continue using eclipse until i find the problem.  i have been using visual studio for about 8 years and have been coding c# since beta.  prior to that i have used C, C++ and VB (which i only do when forced by an employer or client).  i have dabbled with java using netbeans on windows (hence my desire to use it on linux).  prior to visual studio, i used textpad and command line.  all my machines (5) at home have been exclusively moved to linux except one xp machine that i use for windows development.  i must admit that visual studio is probably (my opinion only) the best ide, however, i enjoy my linux machines so i need to switch environments.

to all, thanks for the assistance.  i hope at some point we can find out where the problem lies.  while i agree it is good to stick with one tool, i just hate to be kept in the dark as to why something isn't working.

---

### Post by jvictor on 2006-06-10
The only thing I think different from you is that on my machine I have removed the gcj-compat thingy using

sudo apt-get remove --purge java-gcj-compat

To add on when I tried setting the CLASSPATH from the shell, it used to always show the CLASSPATH perfectly but never found the jar.

---

### Post by guitarded on 2006-06-10
Bingo... i got netbeans and jdbc to play nicely.

ok, netbeans does not have any respect for external references to the classpath.  you must set the classpath for each netbeans project.  so right-click on the on your project.  go to properties.  when the dialog box opens select "libraries" on the left panel.  then under the compile tab click the "Add Jar/Folder" button and navigate to your jar file.  that's it.  after i did that, everything worked great.

so i will go ahead and use netbeans since that is the java environmnet i was used to when i was a windows user.

i hope this helps anyone trying to setup jdbc with netbeans.

---

### Post by jvictor on 2006-06-10
> 1) I've used netbeans quite long back, and u were supposed to mount the jars, bcoz netbeans uses its own classpath. But I read somewhere that now u neednt mount jars .. if not there will be a equalent process to do so. 

I think we were not on the same page .. 

Cheers anyway ! Good Luck :)

---

### Post by andrecasteliano on 2006-07-02
I´m getting the same problem. Tried your tip without sucess.
Anybody else has a sugestion ?

My driver is in JAVA_HOME/jre/lib/ext and works great with "Database Explorer" feature of NetBeans, but when I type the following code, get a ClassNotFoundException:

Class.forName ("org.postgresql.Driver"); or
Class.forName ("com.mysql.jdbc.Driver"); // I have mysql driver too on the same place of postgres

I´m using sun-java5-jk (and related) packages from ubuntu repos.
God damn! Using the same jar file works under DataBase explorer but not in project code!

---

### Post by andrecasteliano on 2006-07-02
A little more info:

prompt: ~$ java -jar myapp.jar 
java.sql.SQLException: No suitable driver
        at java.sql.DriverManager.getConnection(DriverManager.java:545)
        at java.sql.DriverManager.getConnection(DriverManager.java:193)
        [ ... ]

prompt: ~$ java -Djdbc.drivers=org.postgresql.Driver -jar myapp.jar
prompt: ~$

If I specify jdbc.driver in command line my app runs fine! Jesus ... I´m getting crazy :)

---

### Post by guitarded on 2006-07-03
i had the same problem where i could get database explorer to work.  if command line is working that's great too.  however, as per my previous response, netbeans (and many other ide's for that matter) do not use your classpath settings.  unfortunately i can't offer any more than i outlined in my last post.  it is imperative, however, that you find a way to set the classpath via the netbeans libraries for your project as outlined in my post.  if you have done that with the steps i previously outlined it is supposed to work.  btw, i understand your frustration.

---

### Post by IntergalacticPlanetary on 2006-07-09
Hey, i had the same problem and got it working by adding the connector-j.jar to the build path of the ide i'm using (eclipse). for whatever reason, adding / appending it to $CLASSPATH had no affect. good luck.

---

### Post by Lars Skovbo on 2007-03-24
I had the same problem, and tried to solve it for like 2 days. This thread helped me a great deal! Now i can get some sleep :KS Cheers m8's

---

