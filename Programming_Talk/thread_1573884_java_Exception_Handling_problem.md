---
title: "java Exception Handling problem"
date: 2010-09-13
forum: Programming Talk
---

### Post by Eremis on 2010-09-13
Hi,

I have a problem with exception handling in java. I was wondering if I could get some help...

Here's my code:

```

import java.net.InetAddress;

public class DaytimeTcp{
    
    private String hostName;
    private int portNumber;

    public DaytimeTcp(String hostName, int portNumber){
        this.hostName = hostName;
        this.portNumber = portNumber;
    }

    public String getHostName(){
        return this.hostName;
    }

    public int getPortNumber(){
        return this.portNumber;
    }

    public static void main(String[]args){
        
        try{      
            String hostName = args[0];
            int portNumber = Integer.parseInt(args[1]);
        }
        catch(ArrayIndexOutOfBoundsException e){
            System.err.println("-- Usage: java DaytimeTcp <host name> <port number>");
        }
        
        DaytimeTcp time = new DaytimeTcp(hostName, portNumber);
        System.out.println(time.getHostName());
        System.out.println(time.getPortNumber());
    }
}


```

The problem is when I do not have any command line arguments the exception does not work, and it gives me a normal exception, like I never caught it...

---

### Post by r-senior on 2010-09-13
Doesn't compile for me ...

```

$ javac DaytimeTcp.java 
DaytimeTcp.java:31: non-static variable hostName cannot be referenced from a static context
        DaytimeTcp time = new DaytimeTcp(hostName, portNumber);
                                         ^
DaytimeTcp.java:31: non-static variable portNumber cannot be referenced from a static context
        DaytimeTcp time = new DaytimeTcp(hostName, portNumber);
                                                   ^
2 errors

```

---

### Post by simeon87 on 2010-09-13
What do you mean by normal exception? Can you show us the exception and the stack trace that it gives?

---

### Post by spjackson on 2010-09-13
Your class does not compile because of the scope of hostName and portNumber on line
```

DaytimeTcp time = new DaytimeTcp(hostName, portNumber);

```However, when I fix this, the catch works correctly in the absence of command line arguments. Which java are you using? (Sun 1.6.0_20-b02 here).

---

### Post by Eremis on 2010-09-13
java version "1.6.0_18"

so how excactly did u fix this problem?

---

### Post by r-senior on 2010-09-13
Your declarations of hostName and portNumber inside the try block are only active in that block. That's essentially the problem.

---

### Post by Eremis on 2010-09-13
Oh... wow I did not see that...

Thx for the help

---

### Post by r-senior on 2010-09-13
I know you've marked the problem as solved (and it's a work in progress), but a couple of suggestions:

a. I don't write many command line tools in Java but if I do I tend to use a driver class that contains only the main() method. It would have highlighted your problem in this case (because it wouldn't have had sneaky access to those private instance variables) but I think it's good style to have your hopefully reusable object in one file and your main method for this usage in another.

b. It's generally best to reserve exceptions for "exceptional" error conditions rather than things you can achieve with simple programming logic:

```

    if (args.length < 2) {
        System.out.println(...);
    }

```

Exceptions are an expensive way of dealing with simple program logic but really come into their own when you want to propagate them up the chain of classes and method calls with flexibility to ignore or deal with errors at different levels, wrap them in other exceptions, etc.

---

