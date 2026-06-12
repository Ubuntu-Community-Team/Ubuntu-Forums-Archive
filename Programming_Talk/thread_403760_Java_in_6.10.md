---
title: "Java in 6.10"
date: 2007-04-07
forum: Programming Talk
---

### Post by mcgooie on 2007-04-07
Im trying to get a java compliler (Eclipse or JEdit) setup so that i can do my java work on a laptop with just ubuntu on it. I have installed the sun java files and both of these IDE's but still having problems after various attempts.

Could someone give me some advice/guides on what to do from a freshly installed 6.10 version and also how to compile and run the java programs in either Eclipse or Jedit?

Thank you very much :D

---

### Post by cobray on 2007-04-07
I installed the sun-java5-* packages 
and installed eclipse from their web site (not thru synaptic)
everything works really good.
I had problems running eclipse after installing it from the repository

you may need to do
 sudo update-java-alternatives

---

### Post by mcgooie on 2007-04-07
can you post links to what you downloaded from the eclipse site as im not 100% sure what i need to get?

thx

---

### Post by cobray on 2007-04-07
goto [www.eclipse.org](www.eclipse.org)
click the Download button
download the Eclipse SDK 3.2.2

I downloaded the tar file, and expanded it in my home directory
Then I added a custom launcher to the top panel
/home/dkilcy/eclipse/eclipse -Xmx512m

I am using Edgy 6.10 on amd64

---

### Post by mcgooie on 2007-04-07
thanks mate im getting this now, can you tell me what the "Xmx512m" launch command does?

---

### Post by cobray on 2007-04-07
-Xmx512m tells the java program it can allocate up to 512 megs of memory.  The default is 64M.

---

### Post by cobray on 2007-04-07
I just updated to java 6 just now and it is working also with Eclipse SDK 3.2.2

---

### Post by mcgooie on 2007-04-09
just got a simple "Hello World" program to test out and when i compile in Eclipse and the terminal using javac + java i get the following message:

```
Exception in thread "main" java.lang.NoClassDefFoundError:
```

Any ideas?

---

### Post by phossal on 2007-04-09
Post your source, and the commands you're using.

---

### Post by mcgooie on 2007-04-09
test.java file

```

class test
{  
        public static void main(String args[])
        {
           System.out.println("Hello World!");
        }

}
```

compile this using javac test.java

then i use java test

This is now working for me in the terminal but i still get the same error message in Eclipse. Is there something i have to configure in Eclipse that i dont know about?

---

### Post by phossal on 2007-04-09
From the toolbar: Run -> Run -> Java Application -> "New Button" -> Run ...  and it fails? Have you searched for your main class? The only trouble I can imagine is that a) you haven't set the compiler options correctly b) you've packaged your class incorrectly, or might need public. 

Based on what you've posted, I can't tell you exactly what's wrong. There are little tweaks I make depending on how I've installed eclipse.

---

### Post by Ramses de Norre on 2007-04-09
Your class must be public.

---

### Post by phossal on 2007-04-09
Ramses, if you create project in eclipse, and name it "test", and then create a class within your project - even in the default package (against eclipse's recommendation) - you do not need to make the class public to execute it within eclipse. I tried.

---

### Post by aok on 2007-04-10
> **mcgooie said:**
> just got a simple "Hello World" program to test out and when i compile in Eclipse and the terminal using javac + java i get the following message:

```
Exception in thread "main" java.lang.NoClassDefFoundError:
```

Any ideas?

I think you forgot to set your JAVA_HOME environment variable so the CLASSPATH didn't get set.

Assuming you installed the sun-java5-* packages, try putting this in your .bashrc (and re-log in):

```
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/
```

---

### Post by mcgooie on 2007-04-11
thanks for that aok, can you tell me the path to the .bashrc file? i assume its a normal sudo gedit to open the file itself?

---

### Post by slavik on 2007-04-11
.bashrc is in your home directory, no need for sudo. :)

---

### Post by mcgooie on 2007-04-11
cheers, il try that after work today. Thanks for giving a noob all the help guys

---

