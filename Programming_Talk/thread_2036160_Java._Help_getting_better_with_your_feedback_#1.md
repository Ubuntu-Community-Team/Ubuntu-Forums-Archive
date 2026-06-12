---
title: "Java. Help getting better with your feedback #1"
date: 2012-08-01
forum: Programming Talk
---

### Post by Drenriza on 2012-08-01
Hi guys.

So i'am currently trying to learn Java, where i favor quality over quantity. Yes when i start a new project to get better / learn, i tend to start of by writing what could be considered sloppy code, and when the method is working as i want i go back and make it pretty / more efficient.

But i have hit my current limit to what i can improve in my current methods. So now i'am kindly asking if you would look it over and give your feedback on what i could / should improve.

Coding style, changes, creating a new class and split code? Increase efficient of the current code and anything else where you can say "hey you can improve this".

**The main goal here is to get better to Java by learning from you guys on what i could do better when i have hit my own limit. But i don't want to just "achieve the goal". I want to do it right, and if takes a little while longer than thats how it is.**

Please consider that i'am no pro AT ALL, and it's a ongoing process.
Also if i'am missing critical information first time around to a method, please just state it, and i will be **_more_** than happy to provide the necessary code.

But to start it off, i go and post my first method.

The method is to check for specific servers on it's local lan from where the program is run, based on hostnames. The hostnames are always the same their so they are static added to **a.input** which is a **String ArrayList**. **Localhost** is used later in another method but is always present, thus i also static add this to another **String ArrayList**. The difference on **a.input** and **a.input3** is that **a.input is cleared** at the beginning of the next method. And the content of **a.input3 is not**.

WTFC is in this case ALWAYS false.
```

public boolean checkCombiValues(boolean WTFC) throws UnknownHostException, IOException
    {
        boolean WTF = false;
        boolean written = false;
        
        System.out.println("Starting \"check combi values\" method.");
        
        a.input.add("vod");
        a.input.add("audio");
        a.input.add("vnc");
        
        a.input3.add("localhost");
        
        byte count = 0;
        byte countTwo = 0;
        
        BufferedWriter bw = new BufferedWriter(new FileWriter(new File("/home/nice/mail.txt"), true));
        
        for(String string : a.input)
        {
            System.out.println("\tChecking " + string);
            try
            {
                if(InetAddress.getByName(string).isReachable(200))
                {
                    String ip = InetAddress.getByName(string).getHostAddress();
                    if(ip.equals("192.168.20.1"))
                    {
                        if(!written && !WTFC)
                        {
                            bw.write("System information \n");
                            written = true;
                        }
                        bw.write(a.input.get(count) + " is combi \n");
                        
                        System.out.println("\tFound " + a.input.get(count) + " to be combi.");
                        
                        count++;
                        
                        WTF = true;
                    }
                    else
                    {
                        a.input3.add(a.input.get(countTwo));
                    }
                }
                countTwo++;
            }
            catch(UnknownHostException ex)
            {
                System.out.println("\t\t" + string + " wasn't found");
            }
        }
        bw.close();
        
        System.out.println("Ending \"check combi values\" method. \n");
        
        return WTF;
    }

```

The a class looks as follows, if anyone is wondering how i storage the String ArrayLists.
```

/**
 *
 * @author crisitanambk
 * ArrayList Logic Class.
 */
public class ALL 
{
    private static ALL lInstance;
    
    public static ALL getInstance()
    {
        if (lInstance == null)
        {
                lInstance = new ALL();
        }

        return lInstance;
    }
    
    ArrayList<String> input = new ArrayList<String>();
    
    ArrayList<String> input2 = new ArrayList<String>();
    
    ArrayList<String> input3 = new ArrayList<String>();
    
    ArrayList<String> output = new ArrayList<String>();
}

```

Hope you will give your opinions and your knowledge.
Thanks on advance.
Kind regards.

---

### Post by veroslav on 2012-08-01
Hi,

I just skimmed through the checkCombiValues() and here are my two improvement suggestions:

1. I would enclose of the BufferedWriter methods inside a try-block, and have a matching finally block. Within finally block, I would close the BufferedWriter. This is in order to always close the writer, whether an exception occurs or not. Currently, if there is an exception during reading, for instance IOException, close() will never execute.

2. You are catching UnknownHostException and doing some output when it occurs. However, you should re-throw it again from within catch, as it will be never thrown and you will not know whether it was thrown at all or not. Currently your method signature declares that it does so make sure that it does.

Happy coding!

Kind Regards,
Veroslav

---

### Post by Drenriza on 2012-08-01
> I would enclose of the BufferedWriter methods inside a try-block, and have a matching finally block. Within finally block, I would close the BufferedWriter.

So in my example i would create a new try from the bufferedWriter and all the way down to where i close it and then put the close method inside a finally block?

Something like

```

try
{
BufferedWriter bw = new BufferedWriter(new FileWriter(new File("/home/nice/mail.txt"), true));
        
        for(String string : a.input)
        {
            System.out.println("\tChecking " + string);
            try
            {
                if(InetAddress.getByName(string).isReachable(200))
                {
                    String ip = InetAddress.getByName(string).getHostAddress();
                    if(ip.equals("192.168.20.1"))
                    {
                        if(!written && !WTFC)
                        {
                            bw.write("System information \n");
                            written = true;
                        }
                        bw.write(a.input.get(count) + " is combi \n");
                        
                        System.out.println("\tFound " + a.input.get(count) + " to be combi.");
                        
                        count++;
                        
                        WTF = true;
                    }
                    else
                    {
                        a.input3.add(a.input.get(countTwo));
                    }
                }
                countTwo++;
            }
            catch(UnknownHostException ex)
            {
                System.out.println("\t\t" + string + " wasn't found");
            }
        }
}
catch(IOException){handleException}
finally{bw.close();}

```
?? :)

---

### Post by muteXe on 2012-08-01
Just a small comment I guess:

Call variables sensible names. Class "a" for example, and things like "WTF" and "WTFC".

---

### Post by Drenriza on 2012-08-01
> **muteXe said:**
> Just a small comment I guess:

Call variables sensible names. Class "a" for example, and things like "WTF" and "WTFC".

The names WTF and WTFC had a greater meaning, even tho i cant remember them right here and i didn't write them down so i change this eventually to something i know what stand for. But do you have a suggestion for the "a"? I myself didn't have the great ideas. Also if you have a better name for the entire arraylist class feel free to give your opinion.

I also have a Logic class (where the checkcombivalues() method resides) where i call the methods with **l.methodName();** I don't know what Java devs in the real world call these things so please any input is appreciated.

---

### Post by muteXe on 2012-08-01
> **Drenriza said:**
>  even tho i cant remember them right here and i didn't write them down

It is *exactly* for this reason you should give them sensible names from the outset. Like you, my first stab at writing code looks pretty 'sloppy', but I do make an effort on variable names and stuff like that, even on the my first pass.

Write a tiny description of exactly what that class is trying to do. And (ideally) it should be one and no more than one piece of functionality that it does, or else your class is too big or not needed.  From that description you should be able to pluck out a sensible name.

---

### Post by muteXe on 2012-08-01
> 
The a class looks as follows, if anyone is wondering how i storage the String ArrayLists


So StringStorageClass might be an okay name for it? Not brilliant I guess, but better.

---

### Post by veroslav on 2012-08-01
@Drenriza: yes, that is exactly what I had in mind.

Regards,
Veroslav

---

### Post by trent.josephsen on 2012-08-01
I'm a little confused by your ALL, or let's call it StringStorageClass since that was suggested already. Classes are blueprints for objects. What kind of object is this a blueprint for? If you can't describe its role except as "a bunch of lists" or the equivalent, then maybe you should rethink your design. "ArrayList Logic Class" is no kind of description.

Which leads in to my other criticism: comments. Don't just comment your classes. Comment every method, every class variable, and every instance variable. Use /** .. */ notation so it will show up in the javadoc.

I've written before that there's a difference between comments on code and other kinds of comments. When you comment on code within a method, explain *why it's doing what it's doing*; the reader can usually figure out *what* code does line-by-line, but it won't be immediately obvious why you want to do it that way. Comments on methods and classes should describe *what it is* but not *how it works*; as your customer I shouldn't have to care about the logic internal to your checkCombiValues() method, as long as I know (1) what parameters it takes, (2) what value it returns, (3) what side effects it has, and (4) what exceptions it can throw. Documentation is at least as important as coding the thing in the first place; you can often take documentation and code to it much more easily than the other way around.

Back to StringStorageClass, if you persist in using the singleton pattern, don't forget to write a (private) default constructor so that you can't accidentally create more than one instance, and I would initialize the instance variables (input, input2, input3, output) inside the constructor. (As an aside, those are also bad variable names -- what's the conceptual difference between input2 and input3?)

Final criticism: your method is just on the edge of too long, IMHO. I'd try to break it down, probably by creating a private method to check one string at a time and calling it from within the for loop in checkCombiValues. That would make your code more concise and easier to read.

---

### Post by spjackson on 2012-08-01
I would not call myself a Java programmer, and I don't have much to say that hasn't been said. However, there are a couple of mistakes that we all make when starting out with a language, and it is well worth grasping the importance of these principles as soon as you possibly can.

There's nothing more important than meaningful names. In ["Clean Code" ]("http://www.objectmentor.com/resources/books.html"), the first chapter after the introduction is about naming.

In the same book, in the chapter on Functions, [Uncle Bob]("http://www.objectmentor.com/omTeam/martin_r.html") says:
> 
The first rule of functions is that they should be small. The second rule of functions is that *they should be smaller than that.*

...Functions should hardly ever be 20 lines long.


---

### Post by muteXe on 2012-08-02
one other thing: I think singletons are massively over-used and a bit 'cheaty'. If i can think of another design that due not utilise singletons then i'd probably go with that.

---

### Post by Drenriza on 2012-08-02
> if you persist in using the singleton pattern, don't forget to write a (private) default constructor so that you can't accidentally create more than one instance, and I would initialize the instance variables (input, input2, input3, output) inside the constructor

Can you give an example of this?

> I think singletons are massively over-used and a bit 'cheaty'. If i can think of another design that due not utilise singletons then i'd probably go with that.

Can you give an example of another design pattern that accomplishes the same thing?

---

### Post by muteXe on 2012-08-02
Not a pattern no. The main thing about design patterns is knowing when to use when and when not to.

I think it's better to new up object and pass it around into other objects, rather than having a global variable, which essentially how you're using that class at the moment.

---

### Post by GeneralZod on 2012-08-02
> **muteXe said:**
> 
I think it's better to new up object and pass it around into other objects, rather than having a global variable, which essentially how you're using that class at the moment.

Yep - and this is especially useful if you're into unit testing in isolation (using injected test doubles in place of production classes), where singletons or any form of global data are increasingly frowned upon.

Also, n'thing the recommendation for Clean Code - it's one of the few books that profoundly changed the way I write code.  I'd also recommend [Agile Software Development, Principles, Patterns, and Practices](http://www.amazon.com/Software-Development-Principles-Patterns-Practices/dp/0135974445) by the same author which will expose you to a nice range of OOD design techniques (don't let the "agile" in the title put you off - it seems to have been placed there by the Marketing department ;))

---

### Post by Drenriza on 2012-08-02
Thanks Mute and General.

Well i have tried and take some of the suggestions into consideration and tried changing some of the code accordingly.

Splitting some of the code, to be able to give more documentation with the /** method. And changing some of the variable names.

the set_gsValues() method is used in two other methods also. Besides setCheckCombiValues()
Where i have created a get/set class.

Changes in bold.

```

**public void set_gsValues()**
    {
        gsValues.set_WTF(false);
        gsValues.set_written(false);
        
        gsValues.count1 = 0;
        gsValues.count2 = 0;
    }
    
    **public void setCheckCombiValues()**
    {
        set_gsValues();
        
        arraylistLogicClass.shortTermStorage.add("vod");
        arraylistLogicClass.shortTermStorage.add("audio");
        arraylistLogicClass.shortTermStorage.add("vnc");
        
        arraylistLogicClass.longTermStorage.add("localhost");
    }
    
    public boolean checkCombiValues(boolean WTFC) throws UnknownHostException, IOException
    {
        System.out.println("Starting \"check combi values\" method.");
        
        **setCheckCombiValues();**
        
        BufferedWriter bw = new BufferedWriter(new FileWriter(new File("/home/nice/mail.txt"), true));
        
       [B]try
        {[/B]
            for(String string : **arraylistLogicClass.shortTermStorage**)
            {
                System.out.println("\tChecking " + string);
                try
                {
                    if(InetAddress.getByName(string).isReachable(200))
                    {
                        String ip = InetAddress.getByName(string).getHostAddress();
                        if(ip.equals("192.168.20.1"))
                        {
                            if(!gsValues.get_written() && !WTFC)
                            {
                                bw.write("System information \n");
                                **gsValues.set_written(true);**
                            }
                            bw.write(**arraylistLogicClass.shortTermStorage.get(gsValues.count1)** + " is combi \n");

                            System.out.println("\tFound " + **arraylistLogicClass.shortTermStorage.get(gsValues.count1)** + " to be combi.");

                            [B]gsValues.count1++;

                            gsValues.set_WTF(true);[/B]
                        }
                        else
                        {
                            **arraylistLogicClass.longTermStorage.add(arraylistLogicClass.shortTermStorage.get(gsValues.count2));**
                        }
                    }
                    **gsValues.count2++;**
                }
                catch(UnknownHostException ex)
                {
                    System.out.println("\t\t" + string + " wasn't found");
                }
            }
        }
        [B]catch(IOException io)
        {
            System.out.println(io);
        }
        finally
        {
            bw.close();
        }[/B]
        
        System.out.println("Ending \"check combi values\" method. \n");
        
        return gsValues.get_WTF();
    }

```

> The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that.

...Functions should hardly ever be 20 lines long.

a function isint that something that start as follows

```

public/static/private type name
{code}

```
where a method is
```

public/static/private type name()
{code}

```

But if anyone has any ideas to split up my method that now contains 62 lines (if it makes any sense to do so) then please give your feedback and examples.

---

### Post by muteXe on 2012-08-02
'method' and 'function' mean the same thing really, it's that some people use the word 'function' for procedural coding and 'method' for OO coding.

---

### Post by trent.josephsen on 2012-08-02
> **Drenriza said:**
> Can you give an example of this?
Here's how I'd write that singleton:
```
public class StringStorage {
    private static StringStorage global = null;

    private ArrayList<String> input, input2, input3, output;
    
    /* Private default constructor prevents unauthorized code from creating
     * a new instance */
    private StringStorage() {
        input = new ArrayList<String>();
        input2 = new ArrayList<String>();
        input3 = new ArrayList<String>();
        output = new ArrayList<String>();
    }

    /** Returns the singleton object. */
    public static StringStorage getInstance() {
        if (global == null) {
            global = new StringStorage();
        }
        return global;
    }
}
```

But I'm also in agreement with muteXe in that if you don't have a good reason to use a singleton then don't.

I think at this point you're trying to patch up an underlying bad design. No offense, we all make bad designs (some of us pretty frequently ;) ), but one thing you absolutely must learn is how to recognize what part of your design is bad and how to refactor it.

Toward that end, I think it would be good for you to describe the structure of your code. You don't have to post the entire project, especially if it's more than a few .java files, but take some time to tell us what classes there are, what kinds of data they store, and what their methods do. If you have or can easily create a UML class diagram, that would probably be helpful too, but don't spend hours on it. The goal is to get a overall view of your design, not to get tied up in details.

The reason I'm asking is because I can think of a few different ways that would make this code subjectively "better", but without greater context I'm not sure how it would affect the dataflow, and I don't want to be giving poor advice.

---

### Post by trent.josephsen on 2012-08-02
One other note:
> **Drenriza said:**
> 
```
String ip = InetAddress.getByName(string).getHostAddress();
if(ip.equals("192.168.20.1"))

```

I don't think I'd use the String equals() method to compare IP addresses. I can't think of an instance where it would break, but it seems to me more sensible to convert the string "192.168.20.1" to an InetAddress and compare them directly.

```
InetAddress ip = InetAddress.getByName(string);
if(ip.equals(InetAddress.getByName("192.168.20.1")) { ... }
```

---

### Post by ofnuts on 2012-08-03
> **spjackson said:**
> In ["Clean Code" ]("http://www.objectmentor.com/resources/books.html"), the first chapter after the introduction is about naming.

Indeed. Totally required reading. Once you have read it you'll find that this thread has little purpose, since it will have answered all your questions, and some more you didn't even ask :)

---

### Post by Drenriza on 2012-08-03
> **ofnuts said:**
> Indeed. Totally required reading. Once you have read it you'll find that this thread has little purpose, since it will have answered all your questions, and some more you didn't even ask :)

Thats a little harsh. Sure clean code is something i'am trying to get a hand on at the moment. But clean code and efficient code isn't necessarily the same thing. Or am i wrong?

But i will take a look at the book.

> Indeed. Totally required reading. Once you have read it you'll find that this thread has little purpose

But if i didn't start the thread, i would not have heard of this book. So at the end the thread wasn't without purpose :)

---

### Post by ofnuts on 2012-08-05
> **Drenriza said:**
> Thats a little harsh. Sure clean code is something i'am trying to get a hand on at the moment. But clean code and efficient code isn't necessarily the same thing. Or am i wrong?
Necessarily, no, but in practice they are usually seen together. Clean code is more easily understood so its inefficiencies are easier to spot, and easier to fix.


> **Drenriza said:**
> But i will take a look at the book.

But if i didn't start the thread, i would not have heard of this book. So at the end the thread wasn't without purpose :)
Unlike reading the book, requesting our thoughts about code you wrote will only make you aware of the problems with code you have already written but not with code you'll write later. :)

---

