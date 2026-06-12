---
title: "Java experts, show me your favorite tricks"
date: 2008-08-18
forum: Programming Talk
---

### Post by pmasiar on 2008-08-18
I wrestle with Java daily (for web apps, Struts1 and now Struts2 if you must know, and JSTL), reading some books etc. 

I can manage OK now (most of my data structures are ArrayLists of HashMaps, exactly like in Python :-) ) 

But I am obviously missing some cool tricks, like (thanks, hod139 and tinny):
[php]
import java.text.MessageFormat;  
 MessageFormat format = new MessageFormat(
    "Hello from {1} I am {0} old");        
 Object[] testArgs = {new Integer(age+4), name};
 System.out.println(format.format(testArgs));
// or whole thing as one expression
  return MessageFormat.format("Hello from {0} and I am {1} old",
        new Object[]{name, age + 4});   [/php]

I used to do (and hated how clunky it was, for real-world cases):
[php]println("hello " + name + " I am " + age.toString() + " old");[/php]

What cool trick/utilities I am missing? What is good book/website to read about such timesaving trick for a programmer who is way beyond beginner, and bored by beginner's books?

Before you ask: no, I don't know what I am missing, if I knew I would JFGI. What is not obvious, little hidden, and saves loads of time?

And please keep noise at minimum, this one thread I am going to bookmark.

---

### Post by ghostdog74 on 2008-08-18
have you posted this to other Java forums, like the SUN one?
If not, i suggest you do. You can get more suggestions pertaining to your problem.

---

### Post by CptPicard on 2008-08-18
I am so spoiled by languages that have closures that I can't help but always code in terms of the "ad hoc callback plus final wrapper indirection" pattern...

From my bread-and-butter analysis toolkit (it's full of this):

```


	
	private void forAllWinClasses(VakioRecord r, final Closure2<VakioRecord, Integer> c) {
		final Wrapper<Integer> index = new Wrapper<Integer>(0);
		while (index.get() < winClasses()) {
			findNWrong(r, index.get(), new Closure<VakioRecord>() {
				public void call(VakioRecord param) {
					c.call(param, index.get());
				}
			});
			index.set(index.get()+1);
		}	
	}

// later on somewhere...

		forAllWinClasses(r, new Closure2<VakioRecord, Integer>() {
			public void call(VakioRecord rec, Integer i) {
				winclass_cache.get().get(i).add(rec);
			}
		});

	

```


> **pmasiar said:**
> I wrestle with Java daily (for web apps, Struts1 and **now Struts2** if you must know, and JSTL), reading some books etc. 

Gah, the idiots didn't take up Spring?? :(

---

### Post by dribeas on 2008-08-19
Browse through the newsletter in [Java Specialists]("http://www.javaspecialists.co.za/"). Most of the items are not really tricks, but they give you insights into the language that I found interesting.

---

### Post by jespdj on 2008-08-19
There are a lot of short code snippets in Java at [http://www.exampledepot.com/egs/](http://www.exampledepot.com/egs/)

---

### Post by tinny on 2008-08-19
> **CptPicard said:**
> I am so spoiled by languages that have closures that I can't help but always code in terms of the "ad hoc callback plus final wrapper indirection" pattern...

From my bread-and-butter analysis toolkit (it's full of this):



Look out for [Java 7]("http://gafter.blogspot.com/2006/08/closures-for-java.html") (closures in Java)

Where would we be without anonymous inner classes in Java? (not saying its pretty) The other option is the observer design pattern (Listeners).

> 
Gah, the idiots didn't take up Spring?? :(

Oh dear :(

Right now im really into [Maven]("http://maven.apache.org/"). [Maven Archetypes]("http://maven.apache.org/guides/introduction/introduction-to-archetypes.html") are really handy! We all know and love the Java dynamic web app XML config (even worse if your using a framework like struts or Spring), it just takes time to get setup. But when using Maven archetypes all this setup is done for you, leaving you to just get into it! Dependency management in Maven is a godsend! Components of a wider system are deployed as artifacts to a local maven repository (on your LAN), this is a great way to distribute things like wrapped web service clients to various teams across an enterprise.

You can kind of think of a Maven repository in the same way as a Linux repository. There are also public Maven repositories available that you can retrieve useful components from. E.g. [http://mvnrepository.com/](http://mvnrepository.com/)

Also two useful API's that spring to mind.

[Pattern]("http://java.sun.com/j2se/1.5.0/docs/api/java/util/regex/Pattern.html") (regular expressions)
[String.split]("http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html#split(java.lang.String)") (used instead of StringTokenizer)

---

### Post by CptPicard on 2008-08-19
> **tinny said:**
> Look out for [Java 7]("http://gafter.blogspot.com/2006/08/closures-for-java.html") (closures in Java)

Interesting... not sure how well that sits in with the rest of the language. But at least there is already a Lisp (Clojure) for the JVM if I get really needy...

> 
Where would we be without anonymous inner classes in Java? (not saying its pretty)

IDEs make it all too easy to just provide an ad hoc implementation of something :) I really don't know how I could write something like that in a plain editor though... I probably couldn't, or I'd go mad...

> 
 The other option is the observer design pattern (Listeners).


The benefit of this approach is that you still keep yourself nicely inside the class where you're creating your anon class, despite the requirement for final.

> We all know and love the Java dynamic web app XML config (even worse if your using a framework like struts or Spring)

Yes... we... love... it :neutral:

> But when using Maven archetypes all this setup is done for you, leaving you to just get into it! 

I'll have to look into this next time I fire up a new web project.

---

### Post by tinny on 2008-08-19
> 
The benefit of this approach is that you still keep yourself nicely inside the class where you're creating your anon class, despite the requirement for final.


Yes. Why create another file when the code you are writing (the call back) is already coupled to your class.

---

### Post by CptPicard on 2008-08-19
... and of course the requirement for final is not *that* gruesome because you can still call *methods* in your enclosing class.

I also really like the way IDE refactorings also let you just automagically crack out one of those anon classes to either a nested or top-level class if they start getting so big you feel like they should stand on their own. It gives a little bit of fluidity to Java development which would otherwise be a bit lacking...

---

### Post by Wybiral on 2008-08-19
/me pokes his head in, gasps in horror, then goes back to Python and Lisp

---

### Post by tinny on 2008-08-19
@pmasiar ([http://ubuntuforums.org/showthread.php?t=892101&page=7](http://ubuntuforums.org/showthread.php?t=892101&page=7) post #64)

Array copying. A completely non-practical example. (no imports required, just standard java.lang stuff)

[PHP]
public class Hello {

    public static void main(String[] args) {
        String partOne = "Hello";
        String partTwo = " World";
        char[] partOneArray = partOne.toCharArray();
        char[] partTwoArray = partTwo.toCharArray();
        char[] resultArray = new char[partOneArray.length + partTwoArray.length];
       
        System.arraycopy(partOneArray, 0, resultArray, 0, partOneArray.length);
        System.arraycopy(partTwoArray, 0, resultArray, partOneArray.length, partTwoArray.length);
        System.out.println(new String(resultArray));
    }
}
[/PHP]

The output is "Hello World"

---

### Post by mssever on 2008-08-20
> **tinny said:**
> Array copying. A completely non-practical example. (no imports required, just standard java.lang stuff)
Is copying arrays in Java necessarily that complicated? I've always hated Java's arrays, but I've generally chalked that up to the fact that I barely know the language.
```
~:$ irb # Ruby shell
>> a = 'hello'
=> "hello"
>> b = 'world'
=> "world"
>> array = [a,b]
=> ["hello", "world"]
>> puts array.join(' ')
hello world
=> nil
>> copy_of_array = array.dup
=> ["hello", "world"]
>> array == copy_of_array
=> true
>> array.object_id == copy_of_array.object_id
=> false
>> array + copy_of_array
=> ["hello", "world", "hello", "world"]
>> 
```

---

### Post by CptPicard on 2008-08-20
> **mssever said:**
> Is copying arrays in Java necessarily that complicated?

IMO the minimum relevant part is not all that different from other C-like languages is it?

---

### Post by tinny on 2008-08-20
> **mssever said:**
> Is copying arrays in Java necessarily that complicated? I've always hated Java's arrays, but I've generally chalked that up to the fact that I barely know the language.


I dont know Ruby. That Ruby example looked complicated to me. But thats because I dont know Ruby.

The important part of the example that I posted was just one line of code.

Copy one array into another....
```

System.arraycopy(src, srcPos, dest, destPos, length);

```

I dont think thats intimidating...?

---

### Post by CptPicard on 2008-08-20
The important part in the Ruby appears to be

```

copy_of_array = array.dup

```

which is, uh, I suppose, equivalent to using SomeArrayList.clone() :) (I don't think Java arrays are cloneable...?)

(ArrayLists should in general be preferred to raw arrays anyway)

---

### Post by mssever on 2008-08-20
> **tinny said:**
> The important part of the example that I posted was just one line of code.
OK. I understand now what's the key point. The ruby equivalent (assuming you're copying entire arrays, not slices): ```
array1 + array2
```

(I get the feeling that I'm only making a fool of myself in this thread....)

---

### Post by mike_g on 2008-08-20
my expert trick is the increadible bubble sort, but I'm keeping it secret!

---

### Post by tinny on 2008-08-20
> **CptPicard said:**
> The important part in the Ruby appears to be

```

copy_of_array = array.dup

```

which is, uh, I suppose, equivalent to using SomeArrayList.clone() :) (I don't think Java arrays are cloneable...?)

(ArrayLists should in general be preferred to raw arrays anyway)

I believe that they are cloneable.

But yeah ArrayLists....

---

### Post by dribeas on 2008-08-20
> **mssever said:**
> OK. I understand now what's the key point. The ruby equivalent (assuming you're copying entire arrays, not slices): ```
array1 + array2
```

(I get the feeling that I'm only making a fool of myself in this thread....)

The point here is that even if Java's version seems more complicated it is just because it covers not only array copies but also copies of sections of arrays (thats where the three parameters srcPos, destPos, length come from). That is besides the fact that destination array (I believe) must be large enough to hold the copied elements (size >= destPos+length).

---

### Post by dribeas on 2008-08-20
My useless Java trick would be having the following code print 'Bye!!' with some magical implementation of (not shown here) class Magic.

```

class Test
{
   public static void main( String args[] )
   {
      Magic.doIt();
      System.out.println( "Hello" );
   }
};

```

So Strings are inmutable... or are they not?

---

### Post by tinny on 2008-08-20
> **dribeas said:**
> My useless Java trick would be having the following code print 'Bye!!' with some magical implementation of (not shown here) class Magic.

```

class Test
{
   public static void main( String args[] )
   {
      Magic.doIt();
      System.out.println( "Hello" );
   }
};

```

So Strings are inmutable... or are they not?

Yes they are "immutable". Im struggling to see the point of your post?

---

### Post by dribeas on 2008-08-20
> **tinny said:**
> Yes they are "immutable". Im struggling to see the point of your post?

Uhm... I have just tried it with Java 1.5 and it does not work anymore (now value internal field is final, which was not before). But used to with Java 1.3 (when I tried it). Anyway, the explanation:

Strings are meant to be immutable, and some optimizations are performed based on that fact.

At least up to Java 1.3 (when I tried it, have not tested with 1.4) you can use reflection to get to the insides of the String (which is a char[]). This by itself is just a violation of access levels (you are reading into a private member). You could use the access to the array to change the contents of a String, which were thus not really immutable. [With Java 1.5, String value field is final and you cannot change its contents]

What makes Strings different from any other class is that the VM uses the fact that Strings are immutable to perform optimizations. If two classes (or one class in different positions) define the same string literal, only one copy of them is kept in memory and all the variables are just references to the shared copy. [*]

Now comes the Magic (class), that creates a variable with the same string literal, which is a reference to the only literal kept in memory. Magic uses reflection to access the char[], and then modifies the contents of each of the positions. As there is only one shared string literal instance, what really seems as a constant non-changeable text in Test main method turns out to be changed by some external class code!!!

And thus you get what is (was) my favorite and completely useless Java trick. Try it on your friends if you find an old VM.

You can read an article about this in [Java Specialists]("http://www.javaspecialists.eu/archive/Issue014.html").

[*] This optimization is the reason why:
```

   System.out.println( "Hello" == "Hello" ); // true
   StringBuffer sb = new StringBuffer();
   sb.append( "Hel" ).append( "lo" );
   String hello = sb.toString();
   System.out.println( "Hello" == hello ); // false
      // the string was dinamically created, the VM does not
      // know that it is in fact "Hello", unless we tell it:
   System.out.println( "Hello" == hello.intern() ); // true 
      // intern() forces the VM to find another String with the 
      // same contents and point the reference to that shared
      // copy.
   // in all cases "Hello".equals( hello ) is true

```

---

### Post by tinny on 2008-08-20
> **dribeas said:**
> Uhm... I have just tried it with Java 1.5 and it does not work anymore (now value internal field is final, which was not before). But used to with Java 1.3 (when I tried it). Anyway, the explanation:

Strings are meant to be immutable, and some optimizations are performed based on that fact.

At least up to Java 1.3 (when I tried it, have not tested with 1.4) you can use reflection to get to the insides of the String (which is a char[]). This by itself is just a violation of access levels (you are reading into a private member). You could use the access to the array to change the contents of a String, which were thus not really immutable. [With Java 1.5, String value field is final and you cannot change its contents]

What makes Strings different from any other class is that the VM uses the fact that Strings are immutable to perform optimizations. If two classes (or one class in different positions) define the same string literal, only one copy of them is kept in memory and all the variables are just references to the shared copy. [*]

Now comes the Magic (class), that creates a variable with the same string literal, which is a reference to the only literal kept in memory. Magic uses reflection to access the char[], and then modifies the contents of each of the positions. As there is only one shared string literal instance, what really seems as a constant non-changeable text in Test main method turns out to be changed by some external class code!!!

And thus you get what is (was) my favorite and completely useless Java trick. Try it on your friends if you find an old VM.

You can read an article about this in [Java Specialists]("http://www.javaspecialists.eu/archive/Issue014.html").

[*] This optimization is the reason why:
```

   System.out.println( "Hello" == "Hello" ); // true
   StringBuffer sb = new StringBuffer();
   sb.append( "Hel" ).append( "lo" );
   String hello = sb.toString();
   System.out.println( "Hello" == hello ); // false
      // the string was dinamically created, the VM does not
      // know that it is in fact "Hello", unless we tell it:
   System.out.println( "Hello" == hello.intern() ); // true 
      // intern() forces the VM to find another String with the 
      // same contents and point the reference to that shared
      // copy.
   // in all cases "Hello".equals( hello ) is true

```

Oh umm... yeah. I now see the useless trick :)

---

### Post by generalguy on 2008-08-20
> **pmasiar said:**
> I wrestle with Java daily (for web apps, Struts1 and now Struts2 if you must know, and JSTL), reading some books etc. 

I can manage OK now (most of my data structures are ArrayLists of HashMaps, exactly like in Python :-) ) 

But I am obviously missing some cool tricks, like (thanks, hod139 and tinny):
[php]
import java.text.MessageFormat;  
 MessageFormat format = new MessageFormat(
    "Hello from {1} I am {0} old");        
 Object[] testArgs = {new Integer(age+4), name};
 System.out.println(format.format(testArgs));
// or whole thing as one expression
  return MessageFormat.format("Hello from {0} and I am {1} old",
        new Object[]{name, age + 4});   [/php]

I used to do (and hated how clunky it was, for real-world cases):
[php]println("hello " + name + " I am " + age.toString() + " old");[/php]

What cool trick/utilities I am missing? What is good book/website to read about such timesaving trick for a programmer who is way beyond beginner, and bored by beginner's books?

Before you ask: no, I don't know what I am missing, if I knew I would JFGI. What is not obvious, little hidden, and saves loads of time?

And please keep noise at minimum, this one thread I am going to bookmark.

PrintStreams (System.out etc.) have printf now. Also, MessageFormat.format supports varargs, so on 1.5+ you don't need to create the Object[] manually.

[PHP]
mport java.text.MessageFormat;  
 MessageFormat format = new MessageFormat(
    "Hello from {1} I am {0} old");
System.out.printf("Hello from %s and I am %d years old", name.toString(),age);
// or whole thing as one expression
  return MessageFormat.format("Hello from {0} and I am {1} old",name, age + 4);  
[/PHP]

---

### Post by tinny on 2008-08-21
Some useful Java generics info....

Wildcards are worth knowing.

[PHP]
		List<?> strs = new ArrayList<String>();
		//TODO add some objects
		for(Object obj : strs){
			//TODO
		}
		
		List<? extends JComponent> comp = new ArrayList<JPanel>();
		//TODO add any JPanel object
		
		List<? super JPanel> comp2 = new ArrayList<JComponent>();
		//TODO add any JComponent object
[/PHP]

Wildcards are useful when you want to take advantage of polymorphism in generic collections

[PHP]
	public void method(List<? extends JComponent> list) {
		//deal with a collection of JComponents
	}
[/PHP]

The above method is only concerned with dealing with JComponents and doesn't care about the specific type.

---

### Post by tinny on 2008-08-21
Ref: [http://ubuntuforums.org/showthread.php?t=892101&page=2](http://ubuntuforums.org/showthread.php?t=892101&page=2) #20

Useful, probably not, interesting YES!

I can fully complete your challenge in Java!

[PHP]
import java.io.FileReader;
import javax.script.ScriptEngine;
import com.sun.script.jython.JythonScriptEngine;

public class Test {
    public static void main(String[] args) {
        try {
            ScriptEngine jsengine = new JythonScriptEngine();
            // #1 #2 #3 #4 #5 #6 #7 #8
            jsengine.eval(new FileReader("hello.py"));
        } catch (Exception se) {
            se.printStackTrace();
        } 
    }
}
[/PHP]

Requirements:

jython.jar
jython-engine.jar
hello.py

:lolflag: Yes I am cheating :)

---

