---
title: "Java nub in need of help"
date: 2010-02-11
forum: Programming Talk
---

### Post by bartre on 2010-02-11
alright, first off, yes, this is for school.
but, i've got a problem, and i'm fairly sure it's just me being stupid.
so, for this program, we have to write our own queue class in java.
yes, java has it's own, but we have to write one for ourselves.
i've got the logic down on the queue class, but my question is, how do i keep it in the same file as the rest of the program and implement it in the main program?

---

### Post by kamaji792 on 2010-02-11
I probably have got the wrong end of the stick but can't you just add a **static void main()** method in your Queue class to run it.

Here is my quick little example:
```
class SingleFile
{
   private String message;

   public static void main( String[] argv )
   {
      SingleFile sc = new SingleFile( "Hello world!" );

      System.out.println( sc.get_message() );
   }

   SingleFile( String message )
   {
      this.message = message;
   }

   String get_message()
   {
      return this.message;
   }
}
```

I hope that helps

---

### Post by doas777 on 2010-02-11
> **bartre said:**
> alright, first off, yes, this is for school.
but, i've got a problem, and i'm fairly sure it's just me being stupid.
so, for this program, we have to write our own queue class in java.
yes, java has it's own, but we have to write one for ourselves.
i've got the logic down on the queue class, but my question is, how do i keep it in the same file as the rest of the program and implement it in the main program?

most of the java compilers I've worked with, require each class to be in it's own file, named after the class. personally I wouldn't put them in the same file. multifile compilation is an important thing to work through, so give it a try. just make sure they are in the same folder and compile your class before you try to compile the main program.

---

### Post by kamaji792 on 2010-02-11
OK, having seen doas777 reply.

You can put 2 classes in one file with my re-worked example.

```
class SingleFile
{
   private String message;

   public static void main( String[] argv )
   {
      SecondClass sc = new SecondClass( "Hello world!" );

      System.out.println( sc.get_message() );
   }
}

class SecondClass
{
   private String message;

   SecondClass( String message )
   {
      this.message = message;
   }

   String get_message()
   {
      return this.message;
   }
}
```

atb

[edit] I agree with doas777 that putting the classes in separate files is better.  I use the Sun JDK and I am sure if all the files you need are in the same directory you just need to:

```
javac *.java
```
[/edit]

---

### Post by doas777 on 2010-02-11
post back if you are still having troubles, and i'll work up a demo.

---

### Post by HotCupOfJava on 2010-02-11
Keep in mind that while you may have multiple classes in the same ".java" file, the class with the "main" method must have the same name as the ".java" file itself. The compiler will produce multiple ".class" files once you compile the ".java" file.

---

