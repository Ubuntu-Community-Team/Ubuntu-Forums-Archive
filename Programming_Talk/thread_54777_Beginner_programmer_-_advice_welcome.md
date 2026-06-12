---
title: "Beginner programmer - advice welcome"
date: 2005-08-06
forum: Programming Talk
---

### Post by npaladin2000 on 2005-08-06
Ok, here's the deal: I've learned a fair amount of Java, and previously learned Pascal/Delphi (haven't used it recently though).  I've actually coded GUI elements in java (in Windows anyway) but I prefer a visual tool like Glade or the Borland tools for laying out GUIs.

I've got several application ideas that have been kicking around in my head and I want to see if I can finally do them.  No, I don't want to learn C or C++...been there, tried that, have the Excedrin headache to prove it. I've heard Python is a bit similar to Java and easier to learn.  

Now, i've got Glade (GNOME2 version) installed, but I don't see an option for Java in the settings.  Eclipse looks just like Netbeans, so not terribly interested.   Anyway, advice on the following is welcome:

-Getting glade working properly to generate Java code
-How good is the GCC java compiler?
-Am I better off with Python?
-Where's some REALLY good Python documentation?  Besides the stuff on [www.python.org](www.python.org) anyway ;)
-Other than Glade, what good programming tools are out there for Python?  And I don't wanna hear Vim/Emacs...I know about them.  ](*,)  They're especially nice for Java

Oh..does anyone know about SDL programming?

---

### Post by amohanty on 2005-08-06
> -Am I better off with Python?
-Where's some REALLY good Python documentation? Besides the stuff on [www.python.org](www.python.org) anyway
-Other than Glade, what good programming tools are out there for Python? And I don't wanna hear Vim/Emacs...I know about them. They're especially nice for Java


thats depends on what your are trying to do. I have used C++, C, java, python and they are all for different things. Python is a nice general purpose language and easy too, so it might work for you.

For Gui programming in python look at wxPython and Boa Constructor on sf.net. Another IDE (sorta) is pythonwin. Also I think dive-into-python comes installed with Ubuntu. hunt for it.

HTH
AM

---

### Post by LordHunter317 on 2005-08-06
[QUOTE=npaladin2000]Now, i've got Glade (GNOME2 version) installed, but I don't see an option for Java in the settings.[/quote]Did you install libglade-java?

If you want to make GUI applications in Java, use JFC/Swing or SWT.  SWT will give you native feel.  Both are crap, but GTK+ isn't really words better, at least as GUI toolkits go.

> Eclipse looks just like Netbeans, so not terribly interested.Not really and it is junk, but any IDE with IntelliSense-like features is a must for Java, really.

> -How good is the GCC java compiler?Questionable, just use Sun's, BEA's, or IBM's (not Jikes).

---

### Post by npaladin2000 on 2005-08-06
[QUOTE=LordHunter317]Did you install libglade-java?[/QUOTE]

It's libglade2-java and yes it's installed.

---

### Post by npaladin2000 on 2005-08-06
[QUOTE=amohanty]thats depends on what your are trying to do. I have used C++, C, java, python and they are all for different things. Python is a nice general purpose language and easy too, so it might work for you.

For Gui programming in python look at wxPython and Boa Constructor on sf.net. Another IDE (sorta) is pythonwin. Also I think dive-into-python comes installed with Ubuntu. hunt for it.

HTH
AM[/QUOTE]


Found dive-into-python...looks like a good read.

I'm decent enough with Java, but my problem with it is that it's SUCH a bear sometimes...kinda OVERstructured, so much that you spend half the time typing a ton of constructors and public/private yadda yadda.  And I never liked the way it handles vectors or arrays to begin with.

I miss my nice Pascal multitype multidimensional arrays..field 1 an int, field 2 a string, field 3 a boolean....I haven't found a way to do that in Java yet.     I'm looking to make desktop apps to start with, and since they'll be for Ubuntu I figured I'd stick with GTK/GNOME rather than fooling with wx.

*EDIT:*  I just found "Jython."   Sounds just about right for a guy who knows Java, wants to learn Python, and will eventually decide to mix and match because he knows how to do something in one and not the other, right? ;)

---

### Post by LordHunter317 on 2005-08-06
[QUOTE=npaladin2000]I'm decent enough with Java, but my problem with it is that it's SUCH a bear sometimes...kinda OVERstructured, so much that you spend half the time typing a ton of constructors and public/private yadda yadda.[/quote]That's hardly overstructed.  All Simula-derived OOP languages require you to declare access scope and what not.  There are some tedium issues invovled, but it could be worse.

> And I never liked the way it handles vectors or arrays to begin with.While I can list a ton of flaws, I'd like to hear what you think is wrong.

[quote[I miss my nice Pascal multitype multidimensional arrays..field 1 an int, field 2 a string, field 3 a boolean....I haven't found a way to do that in Java yet.[/quote]Unless I'm misunderstanding what you're talking about (an array of records?), why not create your own object and store that?

Heterogenous arrays are rarely a good thing.

 > I'm looking to make desktop apps to start with, and since they'll be for Ubuntu I figured I'd stick with GTK/GNOME rather than fooling with wx.If you want to do them, don't do them in Java.

*EDIT:*  I just found "Jython."   Sounds just about right for a guy who knows Java, wants to learn Python, and will eventually decide to mix and match because he knows how to do something in one and not the other, right? ;)[/QUOTE]Not really.  The languages differences will make the knowledge transfer somewhat low, and the Java standard API is nothing really to write home about.

---

### Post by npaladin2000 on 2005-08-07
Trust me, heterogenious arrays can be incredibly handy.  Basically, it's a built-in database object.  And since one of the things I want to create eventually is a complete media management applications (Sort of mediaman for GNOME with a few added items) then that sort of variable is perfect for storing ID3 tag data in its native form.

Anyway, I got through the first few pages of dive-into=python and it definitely looks worthwhile.  I just have to figure out how to use Glade with it, and I think I found a tutorial somewhere.

---

### Post by LordHunter317 on 2005-08-07
> **npaladin2000]Trust me, heterogenious arrays can be incredibly handy.[/quote]No, they're not.

Heterogenous arrays in all langauges I know mean you give up your type-safety.  Under Java 5, you can't have a heterogenous array and use generics:```

// This is impossible.
ArrayList<any> myList
```Besides, that's not what you want to do anyway.  It violates the whole idea of data encapsulation.  What you want to do is create a class to hold all your interrelated data of different types, and store that data in an array.  Perhaps an example is in order:```
public class MyData {
    private int recordNumber said:**
>  Basically, it's a built-in database object.Yes, but it's about the worse one you can have.  There are far better ways of storing your data in memory.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=LordHunter317]```
public class MyData {
    private int recordNumber;
    private string recordName;
    private string title;

    public MyData(recordNumber, recordName, title) {
        // Left as exercise to reader
   }
}
```Then, elsewhere:```
// IIRC, this is the correct syntax, but it's been a while since I've played with generics.
ArrayList<MyData> dataList = new ArrayList<MyData>();
```Then, as you iterate through the list, you still have your data.
[/QUOTE]

Know how you do that in pascal?

```
type mydata = record
     recnum = int;
     recname = string;
     title = string;

var myarray = array of mydata;
```

And it can even be in the same source file...Java will MAKE you put that statement in a different file, no matter how short the program is or how silly it would be. I don't like that. It may be good for organization of large programs, but it's silly for a 50 line program to need a seperate text file for an object. 

And I know you're gonna disagree.  Apparently, you like Java more than I do.  I like SOME of it's variable handling...declaring them anywhere is great, and it can do some good work with strings.  But there are things I do NOT like about the language, and I think it tries too hard to protect the programmer from himself, and forces one to jump through otherwise-unnecessary hoops. 

But I'm stuck with either that, or Python/Jython (which is looking more and more interesting) or brushing up on my Delphi/Kylix/ObjectPascal...which might not be beyond the realm of possibility.

---

### Post by LordHunter317 on 2005-08-07
[QUOTE=npaladin2000]Know how you do that in pascal?[/quote]Guess what... that's not a multitype, multidimensional array.  That's an array of a single type: your custom record type.

And the way you do it in Pascal is *suprise* no different from Java.

The pascal you posted is using a homogenous array, believe it or not.

> And it can even be in the same source file...Java will MAKE you put that statement in a different file, no matter how short the program is or how silly it would be.That's just not true.  Only public outer classes have to be declared in their own file.  Anything else doesn't have to be defined in it's own file.


> But I'm stuck with either that,Why?  I don't undersatnd what you have to use Java for this.  It really is a terrible idea for making GNOME applications.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=LordHunter317]That's just not true.  Only public outer classes have to be declared in their own file.  Anything else doesn't have to be defined in it's own file.
[/QUOTE]

Well, in the class I took, the instructor told us any seperate outer class had to be in it's own file.  

[QUOTE=LordHunter317]Why?  I don't undersatnd what you have to use Java for this.  It really is a terrible idea for making GNOME applications.[/QUOTE]

Then let's get away from the Java talk! :)  It's one of the programming languages I KNOW...that's why it has to be an option.  Basically, there's one I know well (Java), one I know from way back (ObjectPascal) and one that looks interesting but I can't do anything with yet (Python).

---

### Post by thumper on 2005-08-07
[QUOTE=npaladin2000]Well, in the class I took, the instructor told us any seperate outer class had to be in it's own file. [/QUOTE]
That is why LordHunter317 said to use an **inner** class.

```

public class outer
{
   public class inner
   {
      public String field1;
      public int field2;
   }

   // use the inner class in the definition of outer.
   // since it is a public inner class, it has visibility
   // for all other classes using outer.
}

```

---

### Post by npaladin2000 on 2005-08-07
The guy never even covered inner classes....and last time I tried to rig up something like it javac spit it right back out at me.

"So, is your class an innie or an outie?"   :grin: 

But Java sucks for GNOME development anyway, so likely I'll only use it as a crutch for a while.

---

### Post by LordHunter317 on 2005-08-07
[QUOTE=npaladin2000]Well, in the class I took, the instructor told us any seperate outer class had to be in it's own file.[/quote]Even that's wrong.  It's perfectly legal to declare multiple classes without public access in the same file.  It's also somewhat common in some circles. 

Classes can have more scope than public.

---

### Post by jerome bettis on 2005-08-07
^ exactly

this is (surprisingly) ok in java to just have a class with no scope modifier.

```
class Y  {
    private int x;
	
    public Y(int x)  {
        this.x = x;
    }

    public String toString()  {
        return "" + x;  // another reason why i don't like java.  nooo overloading operators for you, but this is ok though
    }
}

public class X  {
    public static void main(String[] args)  {
        Y y = new Y(5);
        System.out.println(y.toString());
    }
}
```

```
// IIRC, this is the correct syntax, but it's been a while since I've played with generics.
ArrayList<MyData> dataList = new ArrayList<MyData>();
```

i haven't done that for awhile either but i think that's ok

---

### Post by LordHunter317 on 2005-08-07
[QUOTE=jerome bettis]this is (surprisingly) ok in java to just have a class with no scope modifier.[/quote]Well, that's because it takes the default scope: package.  Classes with no explict access declaration can be accessed by classes in the same package only.

To be fair though, the valid uses of package are rather small, realistically, due to limitations usually hoisted on you by Java.

---

### Post by jwenting on 2005-08-09
[QUOTE=LordHunter317]Guess what... that's not a multitype, multidimensional array.  That's an array of a single type: your custom record type.

And the way you do it in Pascal is *suprise* no different from Java.

The pascal you posted is using a homogenous array, believe it or not.

That's just not true.  Only public outer classes have to be declared in their own file.  Anything else doesn't have to be defined in it's own file.


Why?  I don't undersatnd what you have to use Java for this.  It really is a terrible idea for making GNOME applications.[/QUOTE]
 > That's just not true. Only public outer classes have to be declared in their own file. Anything else doesn't have to be defined in it's own file.
Though it's generally a good idea to place every class in its own file (except inner and nested classes of course).
Easier to find the class you want on disk, easier for finegrained version control, etc.

> Guess what... that's not a multitype, multidimensional array. That's an array of a single type: your custom record type.

Of course in Java you can achieve multidimensional arrays of different types by creating an array of arrays.
> 
int[][] arr = new int[5][]; 
 
actually creates an array of 5 int arrays.
Technically this is what you describe because those sub arrays can have different lengths (which makes them different types in Java), though effectively you still end up with an array that can hold only ints (as an int array can only hold ints.

---

### Post by jwenting on 2005-08-09
[QUOTE=LordHunter317]To be fair though, the valid uses of package are rather small, realistically, due to limitations usually hoisted on you by Java.[/QUOTE]

hmm, I can't agree with that.
Package scope classes have very valid uses if you want to restrict access to a class to a limited set of classes only.
Of course everyone could create a class using your package name, but that's actively discouraged by the official coding style guidelines.
It will also hide the class from javadoc (depending on the options passed to javadoc when generating), which cleans up your documentation if you don't want your class to be a public API.

Packages also make an excellent means to divide up a codebase into functional areas, something sorely lacking at a language specification level from most programming languages.

---

### Post by LordHunter317 on 2005-08-09
[QUOTE=jwenting]Of course in Java you can achieve multidimensional arrays of different types by creating an array of arrays.[/quote]Nope.  You could do it with a Vector of Vector of Objects or similiar, though.
 
> Technically this is what you describe because those sub arrays can have different lengths (which makes them different types in Java),No, it does not.  They're still arrays containing integers.  The fact one property is different (length) does not make them actually different types.

I can pass an integer array of length 10 anywhere I can pass one of length 20, without a cast.   Lenght of an array has no bearing on type, unless the language lets you artifically specify an array size in the arguments (which is only a partial type limitation, as if you remove the sizing specification, you can pass any size array, cast-free).

> Package scope classes have very valid uses if you want to restrict access to a class to a limited set of classes only.The number of cases where you can really say: "This class needs to be accessible to all classes of this package and no where else, are pretty small."  Usually composition or inhertience would be better choices for these things.

The only common useful case I can think of is if you had a bunch of static utility functions in use by multiple classes in a package.

> Packages also make an excellent means to divide up a codebase into functional areas, something sorely lacking at a language specification level from most programming languages.Nope.  Most languages have this.

---

### Post by doclivingston on 2005-08-09
[QUOTE=npaladin2000]Now, i've got Glade (GNOME2 version) installed, but I don't see an option for Java in the settings. [/QUOTE]

Those settings are for when you export the GUI design to code, rather than using the .glade files (with libglade).

You're much better to use libglade with .glade files, because a) you don't have to change your code every time you want to change anything in the gui, b) makes it easier for translators and c) exporting as code is deprecates in Glade 2, and is removed in Glade 3. There should be some tutorial floating around for most languages with gnome bindings for libglade.

---

### Post by npaladin2000 on 2005-08-09
[QUOTE=doclivingston]Those settings are for when you export the GUI design to code, rather than using the .glade files (with libglade).

You're much better to use libglade with .glade files, because a) you don't have to change your code every time you want to change anything in the gui, b) makes it easier for translators and c) exporting as code is deprecates in Glade 2, and is removed in Glade 3. There should be some tutorial floating around for most languages with gnome bindings for libglade.[/QUOTE]

Yeah, I found a Python tutorial for Glade...haven't found a Java one yet, but the consensus is that Java sucks for GTK/GNOME development, and I consider it a bit of a bear personally, even though it's the only language I know well so far.  

I also couldn't find anything decent for Object Pascal...I USED to know that one well.  But Lazarus/FreePascal is only GTK1, and I'm not too sure about Kylix....it's vintage 2003, so it might be GTK1 also.

---

### Post by jkndrkn on 2005-08-10
[QUOTE=npaladin2000]I miss my nice Pascal multitype multidimensional arrays..field 1 an int, field 2 a string, field 3 a boolean....I haven't found a way to do that in Java yet.[/QUOTE]

Just create an array (or better, an ArrayList) of objects with attributes as needed. If you *really* want to create a multitype array, I guess you could just create an Object array and set each element to Integer, String, Boolean object types as needed. I don't see the usefulness of this, however.

---

