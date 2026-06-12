---
title: "Java backend/servlets"
date: 2012-01-24
forum: Packaging and Compiling Programs
---

### Post by JCoster on 2012-01-24
Hi,
I want to run a Java application as a backend, and want some of the functions to respond to get/post methods.  I'm not convinced I that I couldn't just make-do with RMI, but ideally i'd like everything over an HTTP port.
I've installed Tomcat and Axis2, but I'm having trouble understanding the absence of main methods in Axis2.  When the server starts, I want it to launch my application and to call a main method, for example:

```

int counter = 0; 

public Main()
{
    while (true)
    {
        counter++;
        Thread.sleep(10000);
    }
}

```

I'd like the application to continue running this loop within the main method, whether any user calls the application via the web or not.

I then want a user to come along and be able to access:

```

public int getCounter()
{
   return counter;
}

```

..through an HTTP request, no matter where the application is within the main method.

Am I on the right track, or do I have completely the wrong idea of what servlets are?  Would I be better writing a standard Java application and implementing RMI?  

Thanks for your help in advance.
Cheers,
JCoster

---

