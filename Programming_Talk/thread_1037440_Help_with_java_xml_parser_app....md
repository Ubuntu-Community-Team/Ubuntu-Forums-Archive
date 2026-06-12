---
title: "Help with java xml parser app..."
date: 2009-01-11
forum: Programming Talk
---

### Post by andrew222 on 2009-01-11
Hello,

I have a program that parses an xml file.  I got the program to compile, but i get a message in Eclipse telling me "<terminated>RateParserDemo" in the pane of the console window.  If I delete the class files I get a 'ClassNotFoundError'.  Can anyone point me in the direction to how I get get the code to compile.  i attached it to this thread in a .zip file....

---

### Post by myrtle1908 on 2009-01-11
Your program is terminating normally.

However you are not getting your desired results ...

In main(), your "rates" loop is not being entered as the length of rates is 0.  This is because your xpath expression in RateListParser ie. "count(/rates/rate)" will always return 0 as your XML does not contain these nodes.

---

### Post by andrew222 on 2009-01-11
Thank you for pointing that out. I changed the line to:   

"count(/rates_returns/rate_return)", doc));

And I now have a NumberRormatException (in which I'll have to make a try block for).  The error message is below,  


Exception in thread "main" java.lang.NumberFormatException: empty String
	at sun.misc.FloatingDecimal.readJavaFormatString(FloatingDecimal.java:994)
	at java.lang.Double.parseDouble(Double.java:510)
	at com.spaceage.XML.RateListParser.parse(RateListParser.java:47)
	at com.spaceage.XML.RateParserDemo.main(RateParserDemo.java:11)


Any ideas on how to fix this error??

---

### Post by kavon89 on 2009-01-11
```
      for (LineRate aRate : rates)
         System.out.println(aRate.format());
   }
```

What kind of for loop is that? I've only ever seen a semi-colon in use with the [?:]("http://en.wikipedia.org/wiki/%3F:") operator.

Might be why you see no output. It compiles and executes, just doesn't inform me that it did anything.

---

### Post by andrew222 on 2009-01-11
That is a 'for-each' loop that became part of the core java API as of java5.  They are specifically used with iterations of the Collections, more specifically lists, look up 'for-each' on google and you'll see what this strange for loop really is.

---

### Post by kavon89 on 2009-01-11
```
class EnhancedForDemo {
     public static void main(String[] args){
          int[] numbers = {1,2,3,4,5,6,7,8,9,10};
          for (int item : numbers) {
            System.out.println("Count is: " + item);
          }
     }
}

```

Hrm, an enhanced for eh. Could prove to be useful for me.

---

### Post by andrew222 on 2009-01-11
Can you click a thanks for me ;-)

---

### Post by myrtle1908 on 2009-01-11
> **andrew222 said:**
> Thank you for pointing that out. I changed the line to:   

"count(/rates_returns/rate_return)", doc));

And I now have a NumberRormatException (in which I'll have to make a try block for).  The error message is below,  


Exception in thread "main" java.lang.NumberFormatException: empty String
	at sun.misc.FloatingDecimal.readJavaFormatString(FloatingDecimal.java:994)
	at java.lang.Double.parseDouble(Double.java:510)
	at com.spaceage.XML.RateListParser.parse(RateListParser.java:47)
	at com.spaceage.XML.RateParserDemo.main(RateParserDemo.java:11)


Any ideas on how to fix this error??


It is because you are trying to create a Double from an empty String (which is not possible).

Have a look at the line where you are parsing 'last_closing'.  Note that 'last_closing' is a child of 'yeild_rate_pct' NOT of 'interest_rate'.

See fix below ...

[PHP]double lc = Double.parseDouble(path.evaluate("/rates_returns/rate_return[" + i + "]/interest_rate/yeild_rate_pct/last_closing", doc));[/PHP]

---

### Post by andrew222 on 2009-01-11
Hello myrtle1908,

I tried the fix and the NumberFormatException went away but I am back to getting an empty console with <terminated> on the pane of the console window...  

I am going to go to sleep shortly but any help is greatly appreciated.

Thank you, I do appreciate your help.

Rgds,

Andrew

---

### Post by andrew222 on 2009-01-11
Sorry, I forgot to attach the updated code, it is attached to this email:

---

### Post by myrtle1908 on 2009-01-11
RateListParser.parse() is returning an empty list because you are never adding the Rate to the rates ArrayList.

Add the following line to RateListParser.parse() after you create the Rate.

[PHP]rates.add(new LineRate(rt));[/PHP]


Output ...
```

Federal-Funds rate target                                   0.250.000.000.00-4.25
```

---

### Post by andrew222 on 2009-01-11
It works!

Thank you...you're really good

---

