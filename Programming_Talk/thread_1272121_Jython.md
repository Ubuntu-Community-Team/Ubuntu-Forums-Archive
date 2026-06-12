---
title: "Jython"
date: 2009-09-21
forum: Programming Talk
---

### Post by kodalisrikanth on 2009-09-21
Hi,


I am trying to access the java variables and methods from python script. Using Jython library i am successfully able to execute some java commands.Now, i am trying to execute java functions and variables from python script. Here is my code
```

import org.python.util.PythonInterpreter;
import org.python.core.PyObject;
import org.python.core.PyException;
import org.python.core.PyArray;
public class Mypython {
	public static void main(String args[]){
		PythonInterpreter pyin = new PythonInterpreter();
		String variable = "This is variable one";
		pyin.exec("from java import awt");
		pyin.exec("import java");
		pyin.exec("java.lang.System.out.println('H');");
		pyin.exec("print 'hello'");

	}
	void inMethod(){
		
		System.out.println("I am in method");
	}
}

```

How to call the function inMethod() from the python script?
How to access the string variable from python script?



Thanks,
Srikanth Kodali.

---

### Post by kodalisrikanth on 2009-09-21
Is it possible to pass the variables from python function to java and vice versa ..?



Thanks,
Srikanth Kodali.

---

### Post by Can+~ on 2009-09-21
[http://www.javalobby.org/articles/jython/](http://www.javalobby.org/articles/jython/)

Never used Jython, but for some reason, I thought that it looked more like Java on Python, than Python on Java.

---

### Post by Reiger on 2009-09-21
Basically put you must register your object with the interpreter so it has a &#8216;name&#8217; in the interpreter. This is easy with JSR 223 script engines (putting an object in a Map...) but I dunno if Jython is compatible at the moment...

---

