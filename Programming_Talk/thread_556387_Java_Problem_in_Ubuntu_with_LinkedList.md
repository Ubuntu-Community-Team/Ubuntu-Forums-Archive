---
title: "Java Problem in Ubuntu with LinkedList"
date: 2007-09-21
forum: Programming Talk
---

### Post by Black Mage on 2007-09-21
I recently installed Ubuntu 7.04 on my IBM, and with the Add/Remove, downloaded Eclipse and JRE 5 &6. When I transfered my java code that I was working on before to the Eclipse in Ubuntu, errors started coming up saying

```

LinkedList<String> ID;
ID =new LinkedList<String>
//The error here in Eclipse is it says cannot have parameters
String string="string";

ID.add(string);
//Error here is cannot add datatype string

ID.contains(string);
//Error is is containg(Object) is not applicable for type String.

```

And this code works fine when I compile and run under in Eclipse in Mac or Windows enviroments. Is there a fix?

---

### Post by WakkiTabakki on 2007-09-21
The problem is most likely that you've named your variable 'string' which the compiler doesn't like. It should've given you the same error under Mac (maybe you've used different JDK versions or something).
Also there was a missing ();

> **Black Mage said:**
> 
```

LinkedList<String> ID;
ID =new LinkedList<String>(); **<- missing semi-colon and parentheses (typo?)**
String **str**="string";

ID.add(**str**);

ID.contains(**str**);

```


/N

---

### Post by Black Mage on 2007-09-21
That wasn't the exact actual code, I just typed that up real quick as an example. Ok, here's the real code:

```

LinkedList<String> brandList, modelList;
LinkedList<Integer> IDList;
brandList=new LinkedList<String>();
modelList=new LinkedList<String>();
IDList=new LinkedList<Integer>();

 int j=result.getInt(1);
 IDList.add(j);

int i=r.nextInt(10000);
	if(IDList.contains(i)==true)
	randomInt();

```

Alll these lines are from the actual code and each one is wrong and only in Eclipse in Ubuntu, Windows and Mac there is no error and it compiles and runs fine.

The error message by the compiler is

```

Exception in thread "AWT-EventQueue-1" java.lang.Error: Unresolved compilation problems: 
	The type LinkedList is not generic; it cannot be parameterized with arguments <String>
	Syntax error, parameterized types are only available if source level is 5.0
	The type LinkedList is not generic; it cannot be parameterized with arguments <Integer>
	Syntax error, parameterized types are only available if source level is 5.0
	brandList cannot be resolved
	The type LinkedList is not generic; it cannot be parameterized with arguments <String>
	Syntax error, parameterized types are only available if source level is 5.0
	The type LinkedList is not generic; it cannot be parameterized with arguments <String>
	Syntax error, parameterized types are only available if source level is 5.0
	IDList cannot be resolved
	The type LinkedList is not generic; it cannot be parameterized with arguments <Integer>
	Syntax error, parameterized types are only available if source level is 5.0
	brandList cannot be resolved
	IDList cannot be resolved
	Type mismatch: cannot convert from Object to String
	IDList cannot be resolved


```

And it doesn't explain why add() and contains() doesn't work either.

---

### Post by hod139 on 2007-09-21
My guess is that you do not have java configured correctly, and eclipse is using gnu's implementation.  See my howto for setting up java: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by Ramses de Norre on 2007-09-21
Are you sure you are actually using java 5 or 6? It seems to me you're not... The error that LinkedList is not generic is probably due to you not having a class LinkedList<T> in your classpath. I think you are using gcj which might not have support for those generic types.

Try **sudo update-java-alternatives -s *java-version***, you can find out which java versions you can enter there by executing the same command with the **-l** switch.
If that's not the problem, try setting the JAVA_HOME variable, I've got this line in my ~/.bashrc : ```
export JAVA_HOME="/opt/java/jre/"
``` but you'll have to change it to point to the place where ubuntu installs java (somewhere under /usr/lib I think).
Do also make sure your settings in eclipse under java > JRE are correct.

---

### Post by sikakraa on 2007-09-21
It seems that you are using (or trying to use) JRE 1.4 or older for compilation. 

You should check your Eclipse and/or project settings so that your compiler compliance level is 5.0 or better. It's found under Window->Preferences and Java -> Compiler: Compiler compliance level.

You should also check under Java->Installed JREs that Eclipse is really using right JRE.

Btw. If you installed Eclipse from Ubuntu repository, I'd suggest you remove it and download and use the version from Eclipse.org. The ubuntu/debian version is apparently compiled with some other Java compiler (probably GNU) than the Eclipse.orgs version and is runs much slower than the original.

---

### Post by Black Mage on 2007-09-21
I got it,t hnx. The problem was Java 6 was the library in Eclipse but it was compiling in Java 4, so I had to change some of the system properties around.

---

### Post by nishaka_k on 2007-09-22
How to make JAVA Progamme?

---

### Post by the_unforgiven on 2007-09-22
Simple and obvious answer to the OP's question:
You're using Java Generics which are supported only since Java 1.5 (aka J2SE 5.0).
[http://en.wikipedia.org/wiki/Java_generics](http://en.wikipedia.org/wiki/Java_generics)

---

