---
title: "Some Java help"
date: 2005-12-09
forum: Programming Talk
---

### Post by raublekick on 2005-12-09
Hey guys. I'm pretty new to Java but I'm pretty experienced with C++ (in terms of a college student).

I'm working on the "Dining Philosophers" problem, but I'm having trouble at the very start with compiling. All I want to do right now is create five "philosophers" and then have them print out their pertinent info.

However, when I compile I get this for each one: 
```
dining.java:3: cannot find symbol
symbol  : class Dude
location: class diningDudes
    Dude d1 = new Dude(HUNGRY, "Jerry Garcia", 1);
    ^

```

It doesn't give me problems about the other public functions, just the constructor. Any tips on how to get past this?

I've got my dining.java file wich contains:
```
class diningDudes {
  public static void main(String[] args) {
    int HUNGRY = 1;
    int EATING = 2;
    int THINKING = 3;
    
    Dude d1 = new Dude(HUNGRY, "Jerry Garcia", 1);
    Dude d2 = new Dude(HUNGRY, "Rick Wakeman", 2);
    Dude d3 = new Dude(HUNGRY, "Jeff Lynne", 3);
    Dude d4 = new Dude(HUNGRY, "Keith Richards", 4);
    Dude d5 = new Dude(HUNGRY, "Keith Emerson", 5);
	
    d1.start();
    d2.start();
    d3.start();
    d4.start();
    d5.start();
  }
}
```

and I also have my philosophers class (but I'm using dudes instead):
```
public class Dude extends Thread {
    private int status;
    private string name;
	private int id;
	
	public static int HUNGRY = 1;
	public static int EATING = 2;
	public static int THINKING = 3;
	

    public Dude(int stat, string nam, int ident) {
        status = stat;
        name = nam;
    }
    public string getName(){return name;}
    public int getStatus(){return status;}
    public int getID(){return id;}
    
    public void run() {
		/*for(int i=0;i<meals;i++)
			{
				try{
				m.getForks(this.getmyId());
				System.out.println("Philosopher "+this.getmyId()+ " is eating!");
				m.release(this.getmyId());
				}catch(Exception e){}
			}*/
		System.out.println(this.getName()+" is " + this.getStatus() + " and " + this.getID() + "!");	  
	}
}

```

---

### Post by Adrian on 2005-12-09
Ok. First of all, there are three occurances of "string" in the Dude.java file. Changing them to "String" will eliminate a couple of errors.

Also, method called getName() already exists in java.lang.Thread, so you have to choose a different name for your method since it's final.

---

### Post by raublekick on 2005-12-09
Hmm... I actually wasn't getting any trouble from the string/String or getName() issues you mentioned. I changed them like you said and still get the same 10 errors (1 for each instance of Dude).

---

### Post by Adrian on 2005-12-09
[QUOTE=raublekick]Hmm... I actually wasn't getting any trouble from the string/String or getName() issues you mentioned. I changed them like you said and still get the same 10 errors (1 for each instance of Dude).[/QUOTE]

Hm.... Strange. I just tried compiling it, and i got no errors at all (after the modifications suggested above).

---

### Post by raublekick on 2005-12-09
Really? 

I guess I should mention that I'm using javac to compile, just to make sure we're both on the same page. Did you run it? Does it print out correctly?


Thanks for taking the tiem to check this out.

---

### Post by Adrian on 2005-12-09
[QUOTE=raublekick]Really? 

I guess I should mention that I'm using javac to compile, just to make sure we're both on the same page. Did you run it? Does it print out correctly?


Thanks for taking the tiem to check this out.[/QUOTE]

I'm using javac supplied with jdk1.5.0_06.

Here is the result:

```
> javac diningDudes.java

> java diningDudes
Jerry Garcia is 1 and 0!
Rick Wakeman is 1 and 0!
Jeff Lynne is 1 and 0!
Keith Richards is 1 and 0!
Keith Emerson is 1 and 0!
```

I guess it works (since you have commented out their ability to eat :) ).

---

### Post by raublekick on 2005-12-09
All those zeros should be different though. Apart from that, that's all I really wanted for right now. Like I said, I'm pretty new with Java so I'm taking this one step at a time.

here is exactly what happens when I compile
```
andrew@mario:~/phil$ javac dining.java
dining.java:7: cannot find symbol
symbol  : class Dude
location: class diningDudes
    Dude d1 = new Dude(HUNGRY, "Jerry Garcia", 1);
    ^
dining.java:7: cannot find symbol
symbol  : class Dude
location: class diningDudes
    Dude d1 = new Dude(HUNGRY, "Jerry Garcia", 1);
                  ^
dining.java:8: cannot find symbol
symbol  : class Dude
location: class diningDudes
    Dude d2 = new Dude(HUNGRY, "Rick Wakeman", 2);
    ^
dining.java:8: cannot find symbol
symbol  : class Dude
location: class diningDudes
    Dude d2 = new Dude(HUNGRY, "Rick Wakeman", 2);
                  ^
dining.java:9: cannot find symbol
symbol  : class Dude
location: class diningDudes
        Dude d3 = new Dude(HUNGRY, "Jeff Lynne", 3);
        ^
dining.java:9: cannot find symbol
symbol  : class Dude
location: class diningDudes
        Dude d3 = new Dude(HUNGRY, "Jeff Lynne", 3);
                      ^
dining.java:10: cannot find symbol
symbol  : class Dude
location: class diningDudes
        Dude d4 = new Dude(HUNGRY, "Keith Richards", 4);
        ^
dining.java:10: cannot find symbol
symbol  : class Dude
location: class diningDudes
        Dude d4 = new Dude(HUNGRY, "Keith Richards", 4);
                      ^
dining.java:11: cannot find symbol
symbol  : class Dude
location: class diningDudes
        Dude d5 = new Dude(HUNGRY, "Keith Emerson", 5);
        ^
dining.java:11: cannot find symbol
symbol  : class Dude
location: class diningDudes
        Dude d5 = new Dude(HUNGRY, "Keith Emerson", 5);
                      ^
10 errors

```

---

### Post by Adrian on 2005-12-09
[QUOTE=raublekick]All those zeros should be different though. Apart from that, that's all I really wanted for right now. Like I said, I'm pretty new with Java so I'm taking this one step at a time.
[/code][/QUOTE]

I bet a
```
id=ident;
```
in the constructor will solve your zeros problem ;)

---

### Post by Adrian on 2005-12-09
[QUOTE=raublekick]
here is exactly what happens when I compile
[/QUOTE]

Looks to me that it doesn't find the Dude class.

What happens if you put the two .java files you pasted in the first message in the same (new and fresh) directory, and then compile the diningDudes.java file?

EDIT: I see that your name of the diningDudes source file is not called diningDudes.java but dining.java. The file name should be the same as the class name. Make sure that the Dude .java file really is called Dude.java. If not, you'll get this error.

---

### Post by raublekick on 2005-12-09
[QUOTE=Adrian]Looks to me that it doesn't find the Dude class.

What happens if you put the two .java files you pasted in the first message in the same (new and fresh) directory, and then compile the diningDudes.java file?[/QUOTE]


Before reading this I took the code I pasted here, made a new directory, and made two new java files and pasted the code in. Got the same errors...

And the id=ident thing I fixed after I posted the code, but forgot to update hehe

---

### Post by raublekick on 2005-12-09
WOW! I just figured it out...

Files need to be EXACTLY the same as the class names...

dude.java + Dude class = frustration


thanks again.

---

### Post by Adrian on 2005-12-09
[QUOTE=raublekick]dude.java + Dude class = frustration[/QUOTE]

Well, everyone makes that mistake at least once. Glad that you sorted it out. Nothing compares to eliminating a frustrating bug :)

---

### Post by KLineD on 2005-12-09
That should do it. Also it's good practice to create a package for your classes. Just put at the first line of each class

```

package homework;

```

Then create a directory called homewok and put both your java files inside the homework directory. To compile, from outside your homework directory:

```

javac homework/*.java

```

And to run it:

```

java homework.diningDudes

```

Hope that helps.

---

### Post by raublekick on 2005-12-09
Sweet thanks KLineD. That looks like a nice useful method. 

Unfortunately I need to use a crummy subission program to submit this to my professor, and it's set up in a way that it can't be in different directories.

---

