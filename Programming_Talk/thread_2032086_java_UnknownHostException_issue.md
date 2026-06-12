---
title: "java UnknownHostException issue"
date: 2012-07-23
forum: Programming Talk
---

### Post by Drenriza on 2012-07-23
Hey guys.

I'am running a line of code as follows
```
if(InetAddress.getByName(string).isReachable(200))
```

In a case i have the hostname does not exist on the system, and can their for not be resolved to an ip address. This generates a UnknownHostException and crash my program.

How can i avoid that the exception crash my program but just checks the next host? If one cant be resolved.

Thanks on advance.
Kind regards.

---

### Post by Bachstelze on 2012-07-23
Use a try...catch?

---

### Post by Drenriza on 2012-07-23
> **Bachstelze said:**
> Use a try...catch?

I have a try catch

```
while(end != true)
        {
            try 
            {
                System.out.println("Program startet");
                boolean created = l.createMailDOTtxt();
                if(created == false)
                {
                    System.out.println("Program exited, necessary files was not created.");
                    System.exit(1);
                }
                ArrayList<String> systemsAlive = l.checkCombiValues(WTF);
            } 
           [B] catch(UnknownHostException ex)
            {
                System.out.println(ex);
            }[/B]
            catch(IOException ex)
            {
                System.out.println(ex);
            }
            catch(InterruptedException ex)
            {
                System.out.println(ex);
            }
            end = true;
        }
```

but still the program crash when the "unknownhostexception occures"....... i don't get it.

---

### Post by mickeelm on 2012-07-23
```
if(InetAddress.getByName(string).isReachable(200))
```

I can't find that code in your latest reply?

Please provide the stacktrace (error log) and I'll try to see what the problem is.

---

### Post by Drenriza on 2012-07-23
> **mickeelm said:**
> ```
if(InetAddress.getByName(string).isReachable(200))
```

I can't find that code in your latest reply?

Please provide the stacktrace (error log) and I'll try to see what the problem is.

In my main class i have the following.
```

public static void main(String[] args) 
    {
        Logic l = Logic.getInstance();
        //boolean mailSend = false;
        
        boolean end = false;
        boolean WTF = false;
        
        while(end != true)
        {
            try 
            {
                System.out.println("Program startet");
                boolean created = l.createMailDOTtxt();
                if(created == false)
                {
                    System.out.println("Program exited, necessary files was not created.");
                    System.exit(1);
                }
                ArrayList<String> systemsAlive = l.checkCombiValues(WTF);
            } 
            catch(UnknownHostException ex)
            {
                System.out.println(ex);
            }
            catch(IOException ex)
            {
                System.out.println(ex);
            }
            catch(InterruptedException ex)
            {
                System.out.println(ex);
            }
            end = true;
        }
    }

```

I then have a logic class where i have the methode
```

public ArrayList checkCombiValues(boolean WTFC) throws UnknownHostException, IOException
    {
        ArrayList<String> check = new ArrayList<String>();
        ArrayList<String> checked = new ArrayList<String>();
        check.add("vod");
        check.add("audio");
        check.add("vnc");
        byte count = 0;
        byte countTwo = 0;
        
        checked.add("localhost");//STATIC VALUE. Always need to be their.
        
        BufferedWriter bw = new BufferedWriter(new FileWriter(new File("/home/nice/mail.txt"), true));
        
        for(String string : check)
        {
            **if(InetAddress.getByName(string).isReachable(200))**
            {
                String ip = InetAddress.getByName(string).getHostAddress();
                if(ip.equals("192.168.20.1"))
                {
                    if(count == 0 && WTFC == true)
                    {
                        bw.write("\nSystem information \n");
                    }
                    else if(count == 0 && WTFC == false)
                    {
                        bw.write("System information \n");
                    }
                    bw.write(check.get(count) + " is combi \n");
                    count++;
                }
                else
                {
                    checked.add(check.get(countTwo));
                }
            }
            countTwo++;
        }
        bw.close();
        return checked;   
    }

```
The methode is a bit messy at the moment because, i'am still working with it.
But from what i can tell the error occurs in the bold part. The inet function tries and resolve a hostname (that does not exist) to an ip address. When it cant do that it throws an UnknownHostException. The issue is. When it throws this exception the program crash. Even tho the exception is catched in the main class in a while loop.

---

### Post by mickeelm on 2012-07-23
If you want the program to check the next host if one fails (e.g. causes an UnknownHostException), you should have a try/catch in your for-loop, not in your main class. For the for loop to continue, you must catch the exception before the end of the current iteration.

So remove the UnknownHostException-catch from your main class (you don't have to if you dont want, but it will be redundant).

I haven't really examined your logic in whole but putting your catch inside the for loop in the checkCombiValues-method will give you the behavior you are looking for.

But, if you just want the loop to go on like nothing happened, change from:

```
catch(UnknownHostException ex)
            {
                System.out.println(ex);
            }
```

to

```
catch(UnknownHostException ex)
            {
                continue;
            }
```

or something like that. Maybe you want to log the error or whatever. 

Sorry, I'm in a bit of a hurry so if this doesn't help - please reply and I'll dig into your code more when I get back tonight and solve your problem :)

---

### Post by Drenriza on 2012-07-23
If i have my try catch in my main methode, the program crash when the exception hits. If i put the try catch around the for loop inside the methode, the program catch the exception and continue. But does not check the last two values inside the String ArrayList........

How can i solve this pesky issue? :)

---

### Post by mickeelm on 2012-07-23
Ok, so we're half way there. I think I'll need your code again then :)

Anyways, to sum the try-catch thing up (if you didn't get it already) is that if you would have kept your try/catch in your main method, the catch would occur AFTER the checkCombiValues-method is "gone"/left by the program. Now, your catch occurs DURING the checkCombiValues-method.This is needed to get the behavior you are looking for.

It sounds strange that the other hosts aren't checked. How does that behavior show itself? Nothing is printed in your desired files or something else?

I'll need your code to go further. And also how you determine that the program isn't behaving as you prefer.

---

### Post by dwhitney67 on 2012-07-23
> **Drenriza said:**
> ... the program crash when the exception hits.

Twice (if not more) you have used the term "crash".  What do you mean by this?  If Java throws an unhandled exception, surely you would have some output that indicates the problem.  But you have yet to provide this critical piece of information (as was requested earlier).

Please, rather than toy with the notion that everyone must have a crystal ball, please post all of your code and any errors that are generated when you run your application.  Also, post what you think the code should do... it's _your_ application built using _your_ requirements.

---

### Post by Drenriza on 2012-07-24
If i'am missing something please tell me. Im still fairly new to this.

```

public class ContentServerMonitorLocal 
{

    public static void main(String[] args) 
    {
        Logic l = Logic.getInstance();
        
        boolean end = false;
        boolean WTF = false;
        
        while(end != true)
        {
            try 
            {
                System.out.println("Program startet");
                boolean created = l.createMailDOTtxt();
                if(created == false)
                {
                    System.out.println("Program exited, necessary files was not created.");
                    System.exit(1);
                }
                ArrayList<String> systemsAlive = l.checkCombiValues(WTF);
            } 
            catch(UnknownHostException ex)
            {
                System.out.println(ex);
            }
            catch(IOException ex)
            {
                System.out.println(ex);
            }
            catch(InterruptedException ex)
            {
                System.out.println(ex);
            }
            end = true;
        }
    }
}

```

The checkCombiValues() method.
```

public ArrayList checkCombiValues(boolean WTFC) throws UnknownHostException, IOException
    {
        ArrayList<String> check = new ArrayList<String>();
        ArrayList<String> checked = new ArrayList<String>();
        check.add("vod");
        check.add("audio");
        check.add("vnc");
        byte count = 0;
        byte countTwo = 0;
        
        checked.add("localhost");//STATIC VALUE. Always need to be their.
        
        BufferedWriter bw = new BufferedWriter(new FileWriter(new File("/home/nice/mail.txt"), true));
        //try
        //{
        for(String string : check)
        {
            if(InetAddress.getByName(string).isReachable(200))
            {
                String ip = InetAddress.getByName(string).getHostAddress();
                if(ip.equals("192.168.20.1"))
                {
                    if(count == 0 && WTFC == true)
                    {
                        bw.write("\nSystem information \n");
                    }
                    else if(count == 0 && WTFC == false)
                    {
                        bw.write("System information \n");
                    }
                    bw.write(check.get(count) + " is combi \n");
                    count++;
                }
                else
                {
                    checked.add(check.get(countTwo));
                }
            }
            countTwo++;
        }
        /*}catch(UnknownHostException ex)
        {}*/
        bw.close();
        return checked;   
    }

```

In my public static void main() method i have my l.methodes inside a while loop with a try catch. What i want is when a exception is thrown, it is catched in the main method. But the program should continue.

In my checkCombiValues() method (from what i can tell) the problem lies in the following line
```
**if(InetAddress.getByName(string).isReachable(200))**
```
Since it cannot resolve the hostname it throws an unknownhostexception.

**The try catch**
If i use my try catch in my main methode to catch the exception, it is printed to the screen just fine. But the program also Crash / Stops / End, however you want to put it.

Also in my code example above. If i keep the try catch around the for loop and comment out the one in the public static void main() methode. The program does NOT Crash / Stops / End when the exception is thrown. The exception is catched and printed to the screen, afterwards the checkCombiValues() skipt the two last entries in the ```
**ArrayList<String> check = new ArrayList<String>();**
```, which is "audio" and "vnc" 
```
[B]check.add("audio"); 
check.add("vnc");[/B]
```

**What i would like the program to do**
Is throw and catch the unknownhostexception when it occures, but the program should continue and check the remaining values in the ```
**ArrayList<String> check = new ArrayList<String>();**
``` until all values have been checked. And then continue with the rest of the program.

---

### Post by spjackson on 2012-07-24
> **Drenriza said:**
> If i'am missing something please tell me. Im still fairly new to this.

What you are missing is the need to put the catch **inside** your for loop, not around it, as mickeelm pointed out in post #6. i.e. like this:

```

public ArrayList checkCombiValues(boolean WTFC) throws UnknownHostException, IOException
    {
        ArrayList<String> check = new ArrayList<String>();
        ArrayList<String> checked = new ArrayList<String>();
        check.add("vod");
        check.add("audio");
        check.add("vnc");
        byte count = 0;
        byte countTwo = 0;
        
        checked.add("localhost");//STATIC VALUE. Always need to be their.
        
        BufferedWriter bw = new BufferedWriter(new FileWriter(new File("/home/nice/mail.txt"), true));
        for(String string : check)
        {
            try
            {
                if(InetAddress.getByName(string).isReachable(200))
                {
                    String ip = InetAddress.getByName(string).getHostAddress();
                    if(ip.equals("192.168.20.1"))
                    {
                        if(count == 0 && WTFC == true)
                        {
                            bw.write("\nSystem information \n");
                        }
                        else if(count == 0 && WTFC == false)
                        {
                            bw.write("System information \n");
                        }
                        bw.write(check.get(count) + " is combi \n");
                        count++;
                    }
                    else
                    {
                        checked.add(check.get(countTwo));
                    }
                }
                countTwo++;
            }
            catch(UnknownHostException ex)
            {
                continue;
            }
        }
        bw.close();
        return checked;   
    }

```

---

### Post by Drenriza on 2012-07-24
Thanks ,)

I putted the try catch inside the for loop and it worked.

But is it not possible to have all try catches in the main method and still get the functionality i want?

---

### Post by Zugzwang on 2012-07-24
> **Drenriza said:**
> Thanks ,)

I putted the try catch inside the for loop and it worked.

But is it not possible to have all try catches in the main method and still get the functionality i want?

No. The idea of Java's exception handling is that you catch the exception at the level at which you want to deal with it. Since you want to deal with it when iterating your list (by skipping some entry), you have to put your exception handling code there.

There is a good reason why it is implemented this way: if you could handle your exceptions from outside a function (and then jump back), the function called couldn't be sure of the state after the exception handling occured. This would be a real mess for people writing library functions!

---

### Post by mickeelm on 2012-07-24
Dreniza, glad it seems to work but the important part for you here is to understand what's going on. E.g. why did you have to put your try/catch in your for loop as I stated and spjackson provided examples for. Do you understand Zugswangs explanation?

Coding java is easy - if you get it :) No, but it is important to really understand what is going on.

I'll try to explain the difference between having the try/catch in the main method vs. in the for loop with another example. Let's say you're an apple farmer and want to check every apple in a batch. Rumours are going that a toxic substance have spread in the area that are dangerous to humans. The substance turns an apple blue. If a single blue apple is discovered, the whole batch has to be thrown away for safety reasons. Apart from that, you check that the apples are not rotten or have wormholes. An apple that is rotten or has wormholes is thrown away, but that's just that single apple and the rest of the batch is unaffected.

The "main"/top-level code:

```

List<Apple> batch = getTheAppleBatchInSomeWay();

try {
   controlBatch(batch);
} catch (ToxicSubstanceEncounteredException e) { 
   logger.log("A dangerous substance has been found! Throw the batch away!");
   discardAppleBatchAndAlertAuthorities();
}

```

Here we are saying, go ahead and check the apples. If a ToxicSubstanceEncounteredException would be thrown (**And not been caught at an earlier stage**, I'll get back to that), it is caught and we make sure that the entire batch is discarded and we do alerts and whatever...

The controlBatch(List<Apple> batch) method and submethods:

```

private void controlBatch(List<Apple> batch) {

   for (Apple apple : batch) {

     try{ 
        checkIfAppleIsBlue(apple);
        checkRottenAndWormholes(apple);        
     } catch (AppleIsBadException e) {
        logger.log("Bad apple encountered. Throwing it away...");
        throwAwayApple(apple);         
     }
   } 
}

private void checkRottenAndWormholes(Apple apple) {

  if(apple.isRotten() || apple.hasWormholes()) {
     throw new AppleIsBadException();
  }

}

private void checkIfAppleIsBlue(Apple apple) {

  if(apple.isBlue()) {
     throw new ToxicSubstanceEncounteredException();
  }
}

```

Now, I have left out some nullchecks (if batch is null, a NullpointerException would be thrown etc) and stuff but I just want to show the basic idea so I've left it out on purpose.

**The important part for you to understand here** is why a bad apple will cause the apple examination to continue, and a blue apple will cause it all to stop and discard the whole batch.

As you see, both the AppleIsBadException and the ToxicSubstanceEncounteredException are thrown at the "same level". The methods, where the exceptions are thrown, are called from inside the for loop.

**Now, here's the trick**: When an exception is thrown, it will continue through the stack until it is caught. If it is never caught, your program will crash (i. e. terminate). In our case, we choose to catch AppleIsBadException inside/during the for loop, at apple level, while we choose to catch ToxicSubstanceEncounteredException on a higher level, on batch level.

So to connect this to your case - if you would catch your UnknownHostException (i.e. bad apple) in your main method that would be like saying "I won't let the program run through if every host isn't perfect". Whereas putting it in the for loop like you have now is saying "If a bad host is encountered, let it be and go on checking the others".

Lets have another look at this part:

```

try{ 
        checkIfAppleIsBlue(apple);
        checkRottenAndWormholes(apple);     
     } catch (AppleIsBadException e) {
        logger.log("Bad apple encountered. Throwing it away...");
        throwAwayApple(apple);         
     }

```

We know that two kinds of exceptions can be thrown here, but we choose to deal with only one of them on this level. As I said before, an Exception will keep on wondering until it is caught (if it is caught). So in this case, an AppleIsBadException doesn't have to go long, it is caught right away and *the for-loop can continue with the next iteration*. But, an ToxicSubstanceEncounteredException will leave the whole controlBatch-method before it is caught. It means that the controlBatch is dead and gone and therefore the for-loop is history and forgotten by now.

Another thing that is to be noted here, is the order of the statements. If I would have put checkRottenAndWormholes(apple); first, the checkIfAppleIsBlue(apple); would never have been executed for that apple IF an AppleIsBadException would have been thrown. So a rotten apple that is blue would have been thrown away without alerting that it is toxic. Of course, I could have just had the try/catch surrounding the rotten-statement and left the toxic-statement out of it, like this:

```

checkIfAppleIsBlue(apple);

try{ 
        checkRottenAndWormholes(apple);     
} catch (AppleIsBadException e) {
        logger.log("Bad apple encountered. Throwing it away...");
        throwAwayApple(apple);       
}

```

I hope that made it a bit clearer. If you havent checked it already, I'd recommend Oracle's online tutorials, very good in my opinion. Take some time reading through the [section on exceptions]("http://docs.oracle.com/javase/tutorial/essential/exceptions/index.html") and this will be much clearer to you. Please ask if anything is unclear.

Good luck with your further coding!

---

### Post by Drenriza on 2012-07-24
Hi Mickeelm.

Thanks for taking the time to write me the apple story. It explains it very well.

A single apple vs a batch of apples, and makes good sense to me.

The only think that "struck" me was. How would you check multiple batches of apples.

Since a batch of apples (in the story) is thrown away if a blue is amongst them, and the method is "forgotten", how would you check multiple batches? Would you then run the statement inside a while / for loop or something.

I'am trying to get more into Java and to start it off i'am gonna try out this book
[http://www.amazon.co.uk/Java-Beginners-Guide-Herbert-Schildt/dp/0071606327/ref=sr_1_1?s=books&ie=UTF8&qid=1343056475&sr=1-1](http://www.amazon.co.uk/Java-Beginners-Guide-Herbert-Schildt/dp/0071606327/ref=sr_1_1?s=books&ie=UTF8&qid=1343056475&sr=1-1)

and hopefully i will learn :) and know where to go when i'am done with that.

Again, thumps up for the apple story. Loved it :)

---

### Post by mickeelm on 2012-07-24
Hi!

No problem, glad to help :)

And, good question! I'll try to explain two scenarios. In this case we will loop through n (where n is > 0) batches. We'll call that a harvest. Same rules apply with rotten apples/wormholes as before. 

1. If a single blue apple is discovered in ANY batch, ALL apples from the harvest will have to be thrown away.

2. If a single blue apple is discovered in a batch, THAT batch will be discarded, but we'll keep on checking the rest.

In both scenarios, there is no need to change our apple-check procedure. What we want to look at is *how we treat the ToxicSubstanceEncounteredException*.

Scenario 1 could be solved like this (To avoid lists containing lists, I've changed the object structure a bit):

```

List<Batch> harvest = getHarvestInSomeWay();

try {

   for(Batch batch : harvest) {

      List<Apple> batchAsAppleList = batch.getBatchAsAppleList();
      controlBatch(batchAsAppleList);
   }
} catch (ToxicSubstanceEncounteredException e) { 
      logger.log("A dangerous substance has been found! Throw the whole harvest away!");
      discardHarvestAndAlertAuthorities(harvest);
   }

```



Scenario 2 could be solved like this:

```

List<Batch> harvest = getHarvestInSomeWay();

for(Batch batch : harvest) {

   List<Apple> batchAsAppleList = batch.getBatchAsAppleList();

   try {
      controlBatch(batchAsAppleList);
   } catch (ToxicSubstanceEncounteredException e) { 
      logger.log("A dangerous substance has been found! Throw the batch away!");
      discardAppleBatchAndAlertAuthorities(batch);
   }
}

```

See the difference? 

In scenario 1, we want to make sure that the harvest is thrown away if ANY blue apple is found, so that's why whe wrap the try/catch around the *whole harvest* (i.e. the whole for-loop looping the whole harvest).
In scenario 2, we only want to throw away the batch containing the blue apple, so that's why we only wrap the *current batch* (i.e. the current iteration of the harvest).

On the litterature note: I haven't tried that particular book but most of them are fine, and it's nice to have a book to lean against.

---

### Post by Drenriza on 2012-07-25
Thanks for the explanation Mickeelm ,)

And books you would recommend for learning java / the OOP structure with objects, classes and so on and so forth.

---

### Post by mickeelm on 2012-07-25
I've used a couple of books during my university studies but I can't recall which they were at the moment, and I think some of them were in swedish. Most of the books out there are probably fine, but unfortunately I don't have any specific recommendations.

Otherwise I have used Oracle's (Which was Sun's before) tutorials, which I posted before so you already know about that. Generally I've been googling specific problems/questions and browsing forums.

When I got to a certain level, I felt the need to go for a certificate. For that I've been using [this book]("http://www.amazon.com/SCJP-Certified-Programmer-Java-310-065/dp/0071591060"). I would not recommend buying that straight away, I would recommend you to go with a normal book first. A lot of the "certificate stuff" is deep and it's not meant to be a book where you learn to code java, it's more like a book that digs into technical specifications of java.

Also, after you've been coding a while, a nice thing to do is to read books on how to be a good programmer and write nice code. There are two books that are good on the subject, Clean Code and The Clean Coder. I don't agree on all that is said, but it's refreshing to get out of the comfort zone once every now and then.

Since you seem to be interested in how to do things right, I saw one thing in your code that I though I should mention. You have:

```
while(end != true)
```

in your code. This works, but is not the general way how you write. If you want to test that a condition is false, you should have written:

```
while(!end)
```

and, if you wanted to test that the condition was true, you should have written:

```
while(end)
```

as simple as that :)

Now, I'm getting off topic here but as a little "assignment" you can check that very while-loop in your main class. Is it really needed? You can PM me your thoughts on that since it is not part of the thread really, and I'll get back to you.

Mark this thread as solved perhaps?

---

### Post by Drenriza on 2012-07-25
> Mark this thread as solved perhaps?

Snap ,)

---

