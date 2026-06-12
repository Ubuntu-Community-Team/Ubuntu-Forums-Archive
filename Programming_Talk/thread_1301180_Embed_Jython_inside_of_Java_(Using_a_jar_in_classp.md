---
title: "Embed Jython inside of Java (Using a jar in classpath)"
date: 2009-10-25
forum: Programming Talk
---

### Post by patrickaupperle on 2009-10-25
Using java and jython you are able to embed python code inside of your java code. The two ways to embed example code from the Jython site are:
```
import javax.script.ScriptEngine;
import javax.script.ScriptEngineManager;
import javax.script.ScriptException;
public class jythonEx
{
	public static void main (String args[]) throws ScriptException
	{
		ScriptEngine engine = new ScriptEngineManager().getEngineByName("python");
        	engine.eval("import sys");
        	engine.put("a", 42);
        	engine.eval("print a");
        	engine.eval("x = 2 + 2");
        	Object x = engine.get("x");
        	System.out.println("x: " + x);
	}
}

```
and
```
import org.python.core.PyException;
import org.python.core.PyInteger;
import org.python.core.PyObject;
import org.python.util.PythonInterpreter;

public class pjythonEx {

    public static void main(String[] args) throws PyException {
        PythonInterpreter interp = new PythonInterpreter();
        interp.exec("import sys");
        interp.exec("print sys");
        interp.set("a", new PyInteger(42));
        interp.exec("print a");
        interp.exec("x = 2+2");
        PyObject x = interp.get("x");
        System.out.println("x: " + x);
    }
}

```
(I did modify the code to suit the file name I chose.)
To do this, I have to use jython.jar. If I add it to my project in eclipse, everything works fine. If I unzip the jar, everything works fine. But, if I try to specify -cp jython.jar, it does not work. I get:
```
[patrick@arch class]$ java -cp jython.jar jythonEx 
Exception in thread "main" java.lang.NoClassDefFoundError: jythonEx
Caused by: java.lang.ClassNotFoundException: jythonEx
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: jythonEx.  Program will exit.
[patrick@arch class]$ java jythonEx -cp jython.jar
Exception in thread "main" java.lang.NullPointerException
	at jythonEx.main(jythonEx.java:9)
[patrick@arch class]$ java pjythonEx -cp jython.jar 
Exception in thread "main" java.lang.NoClassDefFoundError: org/python/core/PyObject
Caused by: java.lang.ClassNotFoundException: org.python.core.PyObject
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: pjythonEx.  Program will exit.
[patrick@arch class]$ java -cp jython.jar pjythonEx
Exception in thread "main" java.lang.NoClassDefFoundError: pjythonEx
Caused by: java.lang.ClassNotFoundException: pjythonEx
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: pjythonEx.  Program will exit.
[patrick@arch class]$ 

```
Can someone give me the proper command to launch these programs?

---

### Post by Reiger on 2009-10-25
Look closely:
> 
java -cp jython.jar <myclass>


What this tells the Java environment is to search for <myclass> in jython.jar; and as it dutifully reports:
> 
Exception in thread "main" java.lang.NoClassDefFoundError: <myclass>
Caused by: java.lang.ClassNotFoundException: <myclass>


Obviously, <myclass> is not in jython.jar; and -less obviously- jython.jar is the only entry in the classpath.

Try:
```

java -cp ./:jython.jar <myclass>

```
Note the additional entry **./** which is the current working directory; and the URL-seperator **:** (colon) to signal that jython.jar and ./ are two different entries in the classpath.

On a Windows machine, the URL-seperator is IIRC a semi-colon.

EDIT: Or as the [SUN tutorial]("http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/classpath.html") mentions as an aside:
> The default class path is the current directory. Setting the CLASSPATH variable or using the -classpath command-line option overrides that default, so if you want to include the current directory in the search path, you must include "." in the new settings.

---

### Post by patrickaupperle on 2009-10-25
> **Reiger said:**
> Look closely:


What this tells the Java environment is to search for <myclass> in jython.jar; and as it dutifully reports:


Obviously, <myclass> is not in jython.jar; and -less obviously- jython.jar is the only entry in the classpath.

Try:
```

java -cp ./:jython.jar <myclass>

```
Note the additional entry **./** which is the current working directory; and the URL-seperator **:** (colon) to signal that jython.jar and ./ are two different entries in the classpath.

On a Windows machine, the URL-seperator is IIRC a semi-colon.
Thank you. That is exactly what I needed. :)

---

