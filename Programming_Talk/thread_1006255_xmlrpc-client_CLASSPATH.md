---
title: "xmlrpc-client CLASSPATH"
date: 2008-12-09
forum: Programming Talk
---

### Post by quintok on 2008-12-09
I downloaded libxmlrpc3-client-java and openjdk-6-jdk from my repository and I was having trouble accessing org.apache.xmlrpc.XmlRpcClient.  I downloaded netbeans to see if I was just unable to set my CLASSPATH correctly but it seems that even if I go to Tools->Libraries and set the classpath to include /usr/share/java/ (where xmlrpc-client-3.1.jar seems to be located) still did not solve my problem.

I moved the .jar to my development directory (~/NetBeansProjects/Hospitality/src/hospitality/) and viewed it in netbeans and it did indeed include org.apache.xmlrpc.XmlRpcClient in netbeans project tree.  It did not however find org.apache.xmlrpc.XmlRpcClient

Here's the code:
```
import org.apache.xmlrpc.XmlRpcClient;
import java.util.Vector;

package hospitality;

public class Main 
{
    public static void main(String[] args)
    {
        XmlRpcClient client = new XmlRpcClient( "http://localhost/hospitality/rpc/" );
        Vector params = new Vector();
        params.addElement(( new Integer(33) ));
        params.addElement(new Integer(5));
    }
}
```

I realise I'm doing something stupid and I'm grateful for any thoughts you might have.

---

### Post by theDaveTheRave on 2008-12-09
Quintok

I had a similar issue with a DBase connector for java.

Even though I seemed to have the classpath and everything in correctly

confirmed by getting the report of 

```

echo $classpath

```

it didn't want to work.

In the end I put the .jar file directly into the JRE directory located here

/user/lib/jvm/java-1.5.0.sun.1.5.0.08/jre/lib/ext/

your version of the jvm / jre may be different, hence the values of -1.5.0.sun.... will need to be changed accordingly.

I would be interested to know if your classpath is being echoed back as containing the path to the missing extension, before and after you add this file to the new location (just to see if it is the same as on my system). Note also that to copy the file into the jre/lib/ext/ folder you will need root permision.

If you are using the system as a web server, apparently you can add the file into the path of the webserver (somehow), but I haven't looked at this as currently I am working on standalone applications.

---

### Post by quintok on 2008-12-09
theDaveTheRave,

echo $CLASSPATH didn't do anything, but I have tried export CLASSPATH=/usr/share/java/ and javac -classpath /usr/share/java/ as well, export did make it show up in echo, but obviously only for that session.  I do have CLASSPATH in my /etc/environment but I haven't restarted which is why I assume it hasn't taken affect on a global scale.

I tried putting it in /usr/lib/jvm/java-6-openjdk/jre/lib/ext but javac failed again.  Which I found by going:
[LIST=1]
[*]which javac -> /usr/bin/javac
[*]cd /usr/bin && ls -l javac -> /etc/alternatives/javac
[*]cd /etc/alternatives && ls -l javac -> /usr/lib/jvm/java-6-openjdk/bin/javac
[/LIST]

The location is ultimately the same for 'which java' as 'which javac',  I did run update-java-alternatives when I installed the open6-jdk

The jar's chmod is is 644, if that's of any use, but I did try it once at 777, in case that was it.

---

### Post by quintok on 2008-12-09
I've now since restarted and I also added the .jar's specifically in netbeans library settings and it seems to have found them.  it does not compile from the command line (without referencing the specific jar's) however.  I shouldn't need to select them as individual jar's should I?

---

### Post by theDaveTheRave on 2008-12-10
quintok.

I was reading my book last night and came across more info onthe classpath.

I got the impression that you can import it in some like fashion not too dissimilar to the <import> command that you do for getting the various packages. However it seemed you would need to do this with a fully qualified name for it to be found properly.

I'm surprised that having it in the /lib/ext didn't work for you, I was hoping that it would.

Is it possible that you have more than one JVM?? and needs to have this in both??

sorry once again I'm not being much help. I'll have another look at the book tonight, and bring it in to work with me tomorrow... if I haven't got too much other stuff to carry! and I'll quote what it says for you.

I find it highly depressing though when the advice in the text produced by the guys who work for the people that make java seems not to work!

something I did read however..when you export the classpath it is only in the correct place for that session, and potentially only for that particular open terminal. Once you log off / reboot the stuff is lost if it isn't in the /etc/environment settings.

I wish someone could explain to us why changing this doesn't seem to have any effect on the JVM being able to find the extensions?

also why is the connectorJ in the repositories not set to get itself working in the right fashion from the start? especially as you need sudo to install it it would seem a small matter for it to be made to work correctly.

Well I hope you soon find a solution to your problem, for now though enough from me and my "having a gripe at the java" people.

David

---

### Post by bobrocks on 2008-12-10
Hello, 

About the classpath, the classpath can only refer to folders that contain code not folders that contain jars.  

In essence if you add a jar explicity to the classpath the classpath reads inside that jar as if it was an actual folder.  This means if you want to add a jar to your classpath you need to reference the jar explicitly not the folder that contains the jar.  Java will then take this jar and treat it as a folder that contains your code.


Taking to putting jar files into jre/lib/ext/ is bad practice, this adds these jars to the classpath of all java applications that run on your jvm.  It can cause wierd and wonderful problems with versioning of libs unexpected name clashes and just plain problems.

As for your code, I haven't used apache XmlRpc before but a quick look at the javadoc shows that the class XmlRpcClient is in the package org.apache.xmlrpc.client and doesn't contain a constructor that takes a string.  The wrong package thing in itself is enough for the compiler to through a cannot find symbol that might look like a broken classpath.

---

### Post by theDaveTheRave on 2008-12-10
Bobrocks.

it seems you may have spread some light on this. it is obviously implied to add the JAR extension to the classpath, but never actually written as such, or I suspect that quintok and I would have been able to get the link to function!

I'm going to try it tonight.

David

ps I was adding a connectorJ to my /lib/ext/ and as I am likely to need it a lot, I figure it doesn't matter too much!

but now that I know how to do this correcty (providing that things work out that is) I'll add other stuff in a local folder somewhere.

---

### Post by bobrocks on 2008-12-10
Hi,

Yeah the classpath is a strange and scary thing at first, but you can learn to tame it quite easily.  You don't have to take my word for it, it is written in the tool docs for suns jdk.  Now finding the tool docs is remarkable hard as I have just found out.  It doesn't seem to be linked from the main site anymore but I did find the classpath documentation through google.

[http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/classpath.html](http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/classpath.html)

It's just good practice not to get into the habit. 

For a couple of jars just create a script that calls javac with the classpath entries required to compile your project.
For more than that maybe look into ant, it's a scary thing at first, but it's a great tool to learn.

---

### Post by quintok on 2008-12-11
Thank you very much bobrocks.  obviously that was my mistake =)  netbeans seemed to handle linking them specifically (the jar's) in my project and it makes sense now thanks to your description and the link you gave us.

---

### Post by theDaveTheRave on 2008-12-11
I can confirm how hard it is to find ther required documentation for setting the classpath.

the crazy thing is I've just read my "old version" of the Java book (it is for version 5), and it says that you need to reference the filename.jar in the classpath....

I guess it is just one of those things where you search for something on the net and because you can't find it there (and you are essentially reading the same stuff!), you decide that your out of date book won't have the required info in it!

Ah well, we all learn!

David

---

### Post by theDaveTheRave on 2009-01-22
Hi all,

I hate to resurect this forum, but a very strange thing just happened to me!

I do a fair amount of programing (although maybe prentending to program would be a better description!). So I was working on something on my works pc, and running the file off of the external HDD. Everything was working just how I wanted it too... in fact maybee even better than I had expected - scary stuff really :eek:

So I took home my external HDD and did a bit of home time tidying up the docs and re-factoring some of the code. I compiled and everthing went just fine.

Then when I attemted to run the proggy from inside netbeans (its still in development for now), I got an old error message I had inserted telling me "I can't find the mysql.connectorJ class!

Very strange thought I?  ](*,)

So I copied the file to my local HDD and tried again. Everything went perfectly..... in fact it was better than perfect. I'm almost ready to turn this into a bean and then add it to a GUI program login thing, and then forever onwards and upwards....

So my question... if I've followed the corrected advice and been able to successfuly add the connectorJ.jar to the classpath, why is it it only works when running stuff from my local pc?

Thoughts are very much appreciated, in advance.

David

---

