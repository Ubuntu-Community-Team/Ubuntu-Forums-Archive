---
title: "Java Path problem?"
date: 2006-09-01
forum: Programming Talk
---

### Post by IsKall on 2006-09-01
I am just trying to compile&execute a example file I made on java.

Just to see how it works in linux, but in Anjuta I get this error on build (compile works fine)

javac *.java

File *.java is missing.



What may that problem be? Is it the path?


```


class Test
{
   public static int main(String[] args)
   {
   		
    System.out.println(4*4);
		
	
    return 0;
   }
}

```

---

### Post by mortsahl on 2006-09-01
Don't know what Anjuta is ... if you're going to do Java development you might take a look at Eclipse.

A variety of things could be wrong -- but the most likely candidate from your the error you're getting is that you don't have a file named Test.java that contains your source.

Do you have java installed?  Do a "java -version" to see.  Have you defined a $JAVA_HOME?  Have you added $JAVA_HOME/bin to your path?

Good luck.

---

### Post by rko618 on 2006-09-02
javac is the java compiler.  So if that's not working than how do you know that it compiled correctly? (obviously it will because it is a simple program)

I also have yet to meet anyone who uses Anjuta for Java development so I don't expect their java support is up to snuff.

Try compiling the program from the command line yourself.  In terminal do this

```
cd <directory_of_java_program>
javac Test.java
java Test
```

change <directory_of_java_program> to the directory where Test.java is saved. Let us know if that does anything for you.

Option B: Is to try using Eclipse

---

