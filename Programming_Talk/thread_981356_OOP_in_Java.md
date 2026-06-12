---
title: "OOP in Java"
date: 2008-11-13
forum: Programming Talk
---

### Post by luke77 on 2008-11-13
Hi guys,

I am beginning Java, which will be my second language after Python, which I have only been using for 2 or 3 months. I have a question regarding basic program layout/design, and I have written a small program that illustrates my confusion. All it does is input up to 10 numbers (until 0 is entered), sort them, and display the numbers in sorted order. Here it is:

```
import java.util.Arrays;

public class ReadNumbers{
  static int [] numarray ;
  static int count;
  static int currentnum;
  static int i;
  
  public ReadNumbers(){
    
    count = 0;
    numarray = new int[10];
    currentnum=1;
  }
  
  public static void buildArray(){
    while (currentnum!=0){
      currentnum=TextIO.getlnInt();
      if (currentnum!=0){
      numarray[count]=currentnum;
      count++;
      }
    }
  }
  
  public static void sortArray(){
    Arrays.sort(numarray);
  }
  
  public static void printAnswer(){
    for (i=0;i<numarray.length;i++){
      if (numarray[i]!=0){
      TextIO.put(numarray[i]);
    }
    }
  }
  
    
  
  public static void main (String [] args){
    
    ReadNumbers app=new ReadNumbers();
    app.buildArray();
    app.sortArray();
    app.printAnswer();
    
  }
  }
```
    
    



My question is, what is the best method to design classes in Java, because I don't think this is "correct" or the best way to design, even though it get the job done. Here's another way of doin the same thing. In this program, instead of creating the array in each instance of "ReadNumbers2" (in the constructor), I create the array in main(), and then pass the array to each method as an argument. Here it is:

```
import java.util.Arrays;

public class ReadNumbers2{
  
  static int count;
  static int currentnum;
 
  
  public ReadNumbers2(){
    
    count = 0;
    currentnum=1;
  }
  
  public static int []  buildArray(int numarray[]){
    while (currentnum!=0){
      currentnum=TextIO.getlnInt();
      if (currentnum!=0){
      numarray[count]=currentnum;
      count++;
      }
    }
    return numarray;
  }
  
  public static void sortArray(int [] numarray){
    Arrays.sort(numarray);
  }
  
  public static void printAnswer(int numarray[]){
    for (int i=0;i<numarray.length;i++){
      if (numarray[i]!=0){
      TextIO.put(numarray[i]);
    }
    }
  }
  
    
  
  public static void main (String [] args){
    
    int [] numarray = new int[10];
    ReadNumbers2 app=new ReadNumbers2();
    numarray=buildArray(numarray);
    sortArray(numarray);
    printAnswer(numarray);
    
  }
  }
```
    





I could have also defined each variable within the methods themselves, such as defining currentnum in buildArray rather than the constructor. Also, I'm not sure when to use "this", as it seems that in some tutorials I've read it is used, and some it is not. For example:
```

    this.count = 0;
    this.numarray = new int[10];
    this.currentnum=1;
```

versus the way that I did it. In python we would say "self.count", etc. for each variable, but I've seem "this" used in some cases and not used in others. 

Finally, it seems like I could have written the same thing without making a "ReadNumbers" instance at all, like this:

```

import java.util.Arrays;

public class ReadNumbers3{
  

  
  public static int []  buildArray(int numarray[]){
    
    int currentnum;
    int count;
    currentnum=1;
    count = 0;
    
    
    
    while (currentnum!=0){
      currentnum=TextIO.getlnInt();
      if (currentnum!=0){
      numarray[count]=currentnum;
      count++;
      }
    }
    return numarray;
  }
  
  public static void sortArray(int [] numarray){
    Arrays.sort(numarray);
  }
  
  public static void printAnswer(int numarray[]){
    for (int i=0;i<numarray.length;i++){
      if (numarray[i]!=0){
      TextIO.put(numarray[i]);
    }
    }
  }
  
    
  
  public static void main (String [] args){
    
    int [] numarray = new int[10];
    

    numarray=buildArray(numarray);
    sortArray(numarray);
    printAnswer(numarray);
    
  }
  }

```


This completely bypasses the issue of creating a new class instance. So, which one is "correct"? Many thanks for any help.

---

### Post by tinny on 2008-11-13
Personally I think you're doing just fine. I cant see any obvious "structure" that could be applied that you haven't already.

One tip on "this"

[PHP]
public class MyClass {

    private int var;

    public MyClass(int var) {
        this.var = var;
    }
    public void doSomething(int var) {
        this.var = var;
    }

}
[/PHP]

In the above example "this" is used to distinguish between the two scopes in which a variable named "var" exists.

[PHP]
this.var //field variable named var

var //constructor or method parameter (local scope) 
[/PHP]

---

### Post by Cinnander on 2008-11-13
For non-Objecty programs like this (it's essentially a procedural program wrapped in an object) it doesn't particularly matter if you do everything in main() or in your constructor - however if you do it in the constructor your main() method must at the very least do a "new ReadNumbers()" for anything to happen - main is a static method and thus when it is called you don't have any 'this' or any other instance of a ReadNumbers instantiated. Thus to reach non-static methods and fields you must create one.
The advantages of either approach only become relevant if you'd want to separate the instantiation of the object and the running of the program - with just one 'object' it's really up to you. A classic example would be a simple GUI app - you might have a 'main' window (JFrame) with all its functionality in a class MainWindow, and the class for this could also contain the main method, which just fires up the GUI when the program is run - saves having another class just to launch the app.
```

public class MainWindow extends javax.swing.JFrame {
  public static void main(String[] args) {
    // Maybe process some command line arguments to get window dimensions.
    final int w = ...;
    final int h = ...;
    new MainWindow(w, h).setVisible(true);
    // and we're off!
  }
  
  public MainWindow(int width, int height) {
   // build  this window
   this.setTitle("Hello, World");
   this.add(new javax.swing.JButton("Click Me"));
   // ...
  }
}
```

For 'real' OO where you'd have several different classes calling methods on one another, you'd only have one main method for the entire program, and you can just situate it in a convenient class as above. The constructors in each class are then responsible only for setting up that one instance of the class which has resulted in them being called.

I include this merely as an exercise in syntax, but it worth knowing that you can also do something like this which, while it will compile and run, will generate warnings if you run "java ThisClass" as you don't have a main method. It can be useful if you need something akin to a main method in other classes though - the warnings only occur if you're actually running java "on" this class. Generally you'd do it if you have a public, static data-structure of some kind intended for other classes to use, and which needs to have values added to it instead of starting empty. It could be a list of properties or something:
```
public class ThisClass {
  // This instances the map but we have no way to add anything to it
  public static Map<String, String> THE_LIST = new Map<String, String>();
  // Oh wait, yes we do:
  // This code is run as soon as the class is first referenced.
  // (It can access any static methods and fields).
  static {
   THE_LIST.put("Age", "21 years");
   THE_LIST.put("Hobbies", "Tweaking Ubuntu");
  }
}
```
(that might not actually compile but the theory is valid.)
We now have a class containing a list which is accessible from anywhere (the list is public) and it's all set up without requiring any method calls to set it up. Neat!

---

### Post by dribeas on 2008-11-14
> **luke77 said:**
> 
```
import java.util.Arrays;

public class ReadNumbers{
  [COLOR="Red"]static[/COLOR] int [] numarray ;
  [COLOR="Red"]static[/COLOR] int count;
  [COLOR="Red"]static[/COLOR] int currentnum;
  [COLOR="Red"]static[/COLOR] int i;
  
  public ReadNumbers(){
    count = 0;
    numarray = new int[10];
    currentnum=1;
  }
  
  public [COLOR="Red"]static[/COLOR] void buildArray(){
    while (currentnum!=0){
      currentnum=TextIO.getlnInt();
      if (currentnum!=0){
      numarray[count]=currentnum;
      count++;
      }
    }
  }
  
  public [COLOR="Red"]static[/COLOR] void sortArray(){
    Arrays.sort(numarray);
  }
  
  public [COLOR="Red"]static[/COLOR] void printAnswer(){
    for (i=0;i<numarray.length;i++){
      if (numarray[i]!=0){
      TextIO.put(numarray[i]);
    }
    }
  }
  
    
  
  public static void main (String [] args){
    
    ReadNumbers app=new ReadNumbers();
    app.buildArray();
    app.sortArray();
    app.printAnswer();
    
  }
  }
```
[...]So, which one is "correct"? Many thanks for any help.


There is no such thing a 'the correct'. There are things that are clearly wrong, and depending on how you expect to use the class there are better alternatives than others.

The code above is not too OO-alike. You are using a class but just to encapsulate global (or class wide) data. In general, static should seldomly be used. static attributes are class-wide, and not instance wide. If you decided to instantiate a second ReadNumbers object, you would loose all the data you already worked on as a side effect. By just removing the statics marked in red you will get the advantage of being able to work on different objects. In your case, I would consider those statics as errors (there is no reason to justify those members being shared). 

You asked when this should/could be used. As @tiny said, it serves to differentiate variables from different scopes. In particular method parameters versus member variables. You can only use this in non-static methods, as static methods work on a class level and there is no such thing as 'this instance'.

Another detail is that you are using an array to hold data and the array has a fixed size of 10, but your reading method does not control how many numbers are inputted into the system. It stops when you read a 0 (if I did not misunderstood it). This means that if your user enters more than 10 numbers you will be in trouble. Your reading loop should control the number of elements if you are to use an array, or you could use a Vector that can be made to grow.

Now it comes to the question of design. The difference between the first and second code snippets comes from the fact that in the first case the int array is an internal data structure while in the second case it is part of the interface. You should use the former whenever it is a detail of your class. That is, when designing you should consider the objective of your class. 

What are you implementing? What do users (other code) expect/want/require from your class? If the use of your class is just retrieving data and outputting to the screen, the first solution would be better, users of your class don't need to know how you store the data or even whether it is stored. They just care about the result and any other knowledge is coupling. Consider that if you changed the int[] for a Vector in a latter implementation, it is an internal detail of the first class and thus users won't notice.

If on the other hand, your class is a tool to obtain a sorted array of numbers for further processing in another class, then the first class will not fit the suit. Users of your class expect a result and they won't get it in the first case so the second will be better. The same goes with member attributes versus function variables.

Variables should be as local as possible. That goes with the member attribute/function variable discussion. If you have a datum that is only to be used locally inside a member method, then there is no need to make it a member attribute, and doing so will fill the class with useless attributes that will confuse you later on, will make your object heavier (member attributes are kept there for the whole lifetime of the object, function variables only during the function call) and make your code confusing.

You should try to design your methods considering the requirements from your users and your member attributes considering what your methods require.

Consider a user that requires you to implement a system that reads numbers, outputs the read numbers, sorts them and then outputs the sorted numbers. But that the user will never want to get the read numbers. The signatures in your first code are close to what you need:

```

class Numbers
{
   public Numbers() {}
   public read() {}
   public print() {}
   public sort() {}
};
int main()
{
   Numbers n = new Numbers();
   n.read();
   n.print();
   n.sort();
   n.print();
}

```

With the interface clear, you can go into details. You need your read numbers to be available to other methods, so it must be an instance variable (chosen to use a Vector):
```

class Numbers {
   private java.util.Vector<int> data;

   public Numbers() {
      data = new Vector<int>();
   }

   public read() {
      // code similar as your example, reads into the vector
   }

   public print() {
      // prints elements in data
   }

   public sort() {
      // can use data vector, and sort it
   }
}

```

Your read method requires an integer variable in which to read from the user before adding it to the vector, but that variable is not required by any other of your methods, so it makes sense to keep it as internal to the function.

Now, you can consider the case where a user want to hint you with the number of elements that you can expect. Then you would receive that number in the constructor, but it is to be used not only during construction of the vector, but also while reading (you don't want to read more than those elements). That 'size' data is part of your class now. You no longer have a Number class to hold integers, you have a Number class to hold 'size' elements, read 'size' elements, ...

In another case, if you decided to use an array of size 1000 elements but you have read only 100, then the number of read elements is part of your state. Not only of the reading method, but the whole class: you don't want to print 1000 elements, only the 100 that were read. So the number of read elements would be part of your object state and thus a member attribute.

This are just a couple of hints, but you will get most from your own experiences. Just try one and another solutions, see what your user code can get from you, what cannot be achieved, recode to give more functionality, reread your code and determine what data that you are publishing does not really help the user and can thus be hidden inside your class... have fun.

---

### Post by achelis on 2008-11-14
Your example is a little small to consider OO-design principles, but there is a few things I think is not best practice in your code.

1)
Counters in your loop should be local to the method.

They have no global uses, and only local responsibility and therefore there is no reason to expose them.
The same thing goes for your currentnum variable - it is only used locally in the method (which is good) - so make it a local variable.

2)
It is really overkill for such a small application, but if the purpose is to learn OO principles you might consider the following:
Classes should have focused areas of responsibility. In your example if I had to divide the responsibility, I would probably start by saying we have the bootstrapping of the application and the application itself - i.e. move the main method to a class whose only responsibility is to startup your program correctly. The reason I suggest this is also that it'll force you to consider the ReadNumbers class from a slightly different perspective.

Well it's early morning so that's all for now.

@Cinnander: Remember to use Swing.invokeLater when using swing - it's not considered best practice to have swing-related objects running in the main thread.

PS: The this keyword in Java is implicit - that's why you only see it sometimes. However - as Tinny pointed out - local variables take precedence over instance variables and therefore you must use the this keyword explicitly in cases where names clash. If that confused you read Tinny's post again :)

---

### Post by ufis on 2008-11-14
Since dribeas has covered most of what my answer would be I'll just add a little bit of info regarding
```
private java.util.Vector<int> data;
```
which should be 
```
private java.util.Vector<Integer> data;
```
Please go read the following pages:
[http://java.sun.com/j2se/1.5.0/docs/guide/language/generics.html](http://java.sun.com/j2se/1.5.0/docs/guide/language/generics.html)
[http://java.sun.com/j2se/1.5.0/docs/guide/language/autoboxing.html](http://java.sun.com/j2se/1.5.0/docs/guide/language/autoboxing.html)
these two topics can be confusing for new java developers where more experienced developers sometimes take it for granted.
You can also read this [http://java.sun.com/docs/books/tutorial/collections/index.html](http://java.sun.com/docs/books/tutorial/collections/index.html) at some stage.
Although these 3 topics are beyond the scope of your question it will make for useful reading.

---

### Post by dribeas on 2008-11-14
> **ufis said:**
> ```
private java.util.Vector<Integer> data;
```
Please go read the following pages:
[http://java.sun.com/j2se/1.5.0/docs/guide/language/generics.html](http://java.sun.com/j2se/1.5.0/docs/guide/language/generics.html)
[http://java.sun.com/j2se/1.5.0/docs/guide/language/autoboxing.html](http://java.sun.com/j2se/1.5.0/docs/guide/language/autoboxing.html)
these two topics can be confusing for new java developers where more experienced developers sometimes take it for granted.
You can also read this [http://java.sun.com/docs/books/tutorial/collections/index.html](http://java.sun.com/docs/books/tutorial/collections/index.html) at some stage.
Although these 3 topics are beyond the scope of your question it will make for useful reading.

+1
Right... its been a while since I last programmed in Java.

---

### Post by pp. on 2008-11-14
Your difficulties in finding reasonable criteria for designing classes for that particular programming task stem from the fact that the task is too simple. 

No matter how you turn and twist the task, you would be left with one instance of one class with a life time identical to that of one execution of your whole application. 

Under these condition, any solution that works is practically just as good as any other solution which works.

---

