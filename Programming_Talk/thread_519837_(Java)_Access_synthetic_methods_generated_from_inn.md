---
title: "(Java) Access synthetic methods generated from inner classes"
date: 2007-08-07
forum: Programming Talk
---

### Post by Ramses de Norre on 2007-08-07
I was wondering, is it possible to access these methods? For example, I've got this method in OwnFrame.java:
```

private WindowAdapter getWindowDestroyer()
{
    return new WindowAdapter()
    {
        @Override
        public void windowClosing(WindowEvent e)
        {
            System.out.println(button.toString());
            System.exit(0);
        }
    };
}

```
And this generates a synthetic method in OwnFrame.class to access the button variable which is private from the class OwnFrame$1.class, javap output for this method:
```
static javax.swing.JButton access$0(sandBox.OwnFrame);
  Code:             
   0:   aload_0     
   1:   getfield        #78; //Field button:Ljavax/swing/JButton;
   4:   areturn

```

Now can I access this method from another class in the same package? I tried the following: ```
System.out.println(OwnFrame.access$0(new OwnFrame()));
```
But that gives me this compiler error: ```
symbol  : method access$0(sandBox.OwnFrame)
location: class sandBox.OwnFrame
                System.out.println(OwnFrame.access$0(new OwnFrame()));
                                           ^
1 error

```

Does anyone know whether and how I can access the button field through this synthetic method?

---

### Post by pmasiar on 2007-08-07
I hate these unhelpful error messages. They know *exactly* what is wrong, but won't give you a hint.

maybe you need to assing new object to a reference, and use that? But access0 is static... But again, "new OwnFrame()" creates new instance, right? Too confusing.

---

### Post by Ramses de Norre on 2007-08-07
In the end I'm trying to accomplish something the java developers don't want to be possible... But I know it is possible in the present implementation of inner classes so I'm trying to find out how, just for curiosity :)

The access$0() method is indeed static, that's why I invoke it on OwnFrame (the class in which the method resides), the method takes an OwnFrame object as argument, so I guess it'll return the button object from the OwnFrame object it gets as argument.

So if I do
```

Ownframe frame=new OwnFrame();
JButton button=new JButton("test");
OwnFrame.setButton(button);
OwnFrame.access$0(frame).equals(button);

```
The last statement should be true in my understanding, but javac doesn't want to compile this, it gives the error I showed before. I thought javac uses the .class files in its classpath (which I explicitly specified) and thus it should be able to find this access$0() method and compile my statements, doesn't it?

---

### Post by Ramses de Norre on 2007-08-09
I found it, this is how I did it: (it's a pure proof of concept, the example has no use):

First I compiled these files:

Nullable.java:```
public interface Nullable{}
```

Anchestor.java:```

public class Anchestor
{
    private final String pstring="Result";

    public Object getObject()
    {
        return new Nullable()
        {
            public void print()
            {
                System.out.println(pstring);
            }
        };
    }

    static String access$000(Anchestor a)
    {
        return null;
    }
}

```

Because the String is final, the compiler treats it as a constant on the stack and no synthetic method is used, so I define **access$000()** myself. (Without the final modifier I get a compiler error for conflicting method names).

Then I compile this file:

AnchestorHack.java:```
public class AnchestorHack
{
    public static void main(String[] args)
    {
        System.out.println(Anchestor.access$000(new Anchestor()));
    }
}
```

And I change Anchestor.java to the following and recompile it (without changing AnchestorHack.class):

Anchestor.java:```
public class Anchestor
{
    private /*final*/ String pstring="Result";

    public Object getObject()
    {
        return new Nullable()
        {
            public void print()
            {
                System.out.println(pstring);
            }
        };
    }

    /*static String access$000(Anchestor a)
    {
        return null;
    }*/
}
```

Because the String isn't final anymore the compiler must generate a synthetic method **access$0000()** to make it accessible to the anonymous class, this method is also still present in the bytecode of AnchestorHack.class (although it was defined as the self-defined method when I compiled that), if I now run AnchestorHack.java the output is "result", so I accessed a private field through another class...

---

