---
title: "Eclipse console"
date: 2011-10-28
forum: Programming Talk
---

### Post by S0m3guy on 2011-10-28
Hey guys,

I just installed Oneiric Ocelot on my laptop and wanted to start programming in Java with Eclipse IDE.

But there is a little problem I got.

```
public class aufgabe7 {

    public static void main(String[] args) {

        System.out.println("Please input a number: ");
        
        int zahl = Integer.parseInt(System.console().readLine());
        
    }

}
```

For example with this code. When I run this, I get a NullPointerException because it does not let me input anything, it just runs through and then of course readLine() returns null.

I read that since Eclipse 3.2 or 3.3 there is something different with the intern console.

When I run that program with the terminal and the java commands everything works fine.

---

### Post by 11jmb on 2011-10-28
add this to your code and see what happens

```

Console con = System.console();
    if (con == null) {
        System.err.println("Error:console is null");
        System.exit(1);
    }

```

---

### Post by S0m3guy on 2011-10-28
Gives me "Error: console is null"

---

### Post by 11jmb on 2011-10-28
Ok. I believe that this is because the JVM you are using does not have an associated console. I don't think it is a problem specific to eclipse. There is another way to read input from the command line. try this:

```

BufferedReader reader = new BufferedReader(new InputStreamReader(System.in);

System.out.println("Please input a number: ");
        
int zahl = Integer.parseInt(reader.readLine());

```

---

### Post by S0m3guy on 2011-10-28
I know but if possible I would like to avoid those "Readers" since we don't use those in our lectures.

And before it worked fine as well :/

Which means I'd rather fix that JVM problem. I didn't install/fix/repair anything java specific after I installied Oneiric so I'm quite unsure what I got here and what I need.

---

### Post by akoskm on 2011-10-28
For such input actions (like starting program with specific parameters) you should inspect Run Configurations [http://help.eclipse.org/galileo/index.jsp?topic=/org.eclipse.jdt.doc.user/tasks/tasks-java-local-configuration.htm](http://help.eclipse.org/galileo/index.jsp?topic=/org.eclipse.jdt.doc.user/tasks/tasks-java-local-configuration.htm) .

---

### Post by 11jmb on 2011-10-28
> **S0m3guy said:**
> I know but if possible I would like to avoid those "Readers" since we don't use those in our lectures.

And before it worked fine as well :/

Which means I'd rather fix that JVM problem. I didn't install/fix/repair anything java specific after I installied Oneiric so I'm quite unsure what I got here and what I need.

Actually, I should ask before blaming the JVM, does this work when run from the command line instead of eclipse?

---

### Post by S0m3guy on 2011-10-28
The original code from first post, yes.

---

### Post by akoskm on 2011-10-28
> **S0m3guy said:**
> The original code from first post, yes.

In this case you should definitely use run configurations...

---

### Post by 11jmb on 2011-10-28
Well a few minutes of research is telling me that eclipse does not allow for use of the Console class. Perhaps somebody else here can help with a solution

I think your best option for this assignment is to just run for the command line, but in the future, I recommend using the Reader classes anyway, because Console is a newer feature, and the Readers give you some backwards compatibility.

---

### Post by 11jmb on 2011-10-28
> **akoskm said:**
> In this case you should definitely use run configurations...

This is not going to get the Console class working. This is just a way to pass in runtime arguments, like you would do from the command line. The only way that I can find to run the code from post 1 is to run it from the command line

---

### Post by akoskm on 2011-10-28
> **11jmb said:**
> This is not going to get the Console class working. This is just a way to pass in runtime arguments, like you would do from the command line. The only way that I can find to run the code from post 1 is to run it from the command line

Yes, you are right, I misunderstood the problem. Sorry.

---

### Post by S0m3guy on 2011-10-28
But I dont understand why some time ago the same code worked fine within Eclipse and its console and now it just doesnt.

Maybe I should just switch to an older version of Eclipse -.-

Isnt there some way of getting Eclipse to start an external console when running a program?

---

### Post by 11jmb on 2011-10-28
I'm not sure what to say. From my research, it looks like the reason is that eclipse is called by a javaw command which excludes a console. I was unable to find a good plugin or workaround but there obviously must be some way. Was this the same exact system where it worked before? (computer and eclipse install) If so, did you change anything (i.e. install a plugin) before it stopped working?

---

### Post by ofnuts on 2011-10-28
For what it's worth: [https://bugs.eclipse.org/bugs/show_bug.cgi?id=122429](https://bugs.eclipse.org/bugs/show_bug.cgi?id=122429)

---

### Post by S0m3guy on 2011-10-29
> **11jmb said:**
> I'm not sure what to say. From my research, it looks like the reason is that eclipse is called by a javaw command which excludes a console. I was unable to find a good plugin or workaround but there obviously must be some way. Was this the same exact system where it worked before? (computer and eclipse install) If so, did you change anything (i.e. install a plugin) before it stopped working?

Pretty much the same system, only thing that changed is that I installed a SSD and I installed a Eclipse completely new, so I guess a quite newer version.

---

