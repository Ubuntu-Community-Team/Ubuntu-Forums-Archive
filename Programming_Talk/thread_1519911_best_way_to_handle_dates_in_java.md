---
title: "best way to handle dates in java"
date: 2010-06-28
forum: Programming Talk
---

### Post by badperson on 2010-06-28
Hi,
I'm writing an app that keeps track of projects and was wondering the best way to handle dates. I'm using gregorianCalendar and when I want to display, I usually output gc.getTime(). 

I don't see any methods to output in multiple formats, like 
June 28, 2010. Do I need to just write my own code for that? (not a big deal)

Is SimpleDateFormat something you use in conjunction with GregorianCalendar, or are they completely different? I didn't see that you could pass one to the other in the constructors...

thanks, 
bp

---

### Post by simeon87 on 2010-06-29
I'm not experienced with this but based on [the documentation of the parent class of SimpleDateFormat](http://java.sun.com/j2se/1.4.2/docs/api/java/text/DateFormat.html), you can do:

```
myString = DateFormat.getDateInstance().format(myDate);
```

where myDate is a Date object. I suggest reading also reading the documentation of [SimpleDateFormat](http://java.sun.com/j2se/1.4.2/docs/api/java/text/SimpleDateFormat.html) because it does appear to be the way to format dates in Java.

---

### Post by burton247 on 2010-06-29
You can yes use SimpleDateFormat with GregorianCalendar. I'll try and find you some code where I implemented

---

### Post by burton247 on 2010-06-29
This was the question:

"Formatting Dates using a Format class, (or otherwise if you prefer!)

There is a standard class called DateFormat which (among other things) lets you convert dates to various different output formats. It has a subclass SimpleDateFormat which you may also use).

Use it to write a method called convert which returns a String in the form dd-MMM-yyyy: when passed a GregorianCalendar with a specific date

   public String convert (Calendar gc) {
     ...
   }
For example, when myGC is a GregorianCalendar variable representing the 25th of December 2006,
   String s = convert(myGC);
should set s to the string "25-Dec-2006".
Enter your answer (just your convert method) below: "

My answer was:

public String convert (Calendar gc)
   {
       Date d = gc.getTime();
       SimpleDateFormat df = new SimpleDateFormat("dd-MMM-yyyy");
       String s = df.format(d);
       return s;
   }


EDIT: formatting went out but oh well

---

### Post by Some Penguin on 2010-06-29
One minor caution on SDF:  It is not threadsafe.

---

### Post by burton247 on 2010-06-29
I suppose I should put a warning when I try and help with programming, Ive only finished my first year at uni doing computer science so I don't know massive amounts

---

