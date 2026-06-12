---
title: "Java clone() method help"
date: 2010-10-28
forum: Programming Talk
---

### Post by Sidneyaks on 2010-10-28
Ok, so I'm trying to use the [_[COLOR="Navy"]GregorianCalendar[/COLOR]_]("http://download.oracle.com/javase/1.5.0/docs/api/java/util/GregorianCalendar.html") class's clone() method, which as I understand it from the API overrides the clone() method from the object class.

However, the [_[COLOR="navy"]GregorianCalendar.clone()[/COLOR]_]("http://download.oracle.com/javase/1.5.0/docs/api/java/util/GregorianCalendar.html#clone()") returns an object type.

Do I need to explicitly downcast in my own code (and if so, how?), or is the clone() method just relatively useless? I've read most everywhere that down casting is a terrible idea in 99.9% of all cases, but this just seems a little strange to me.

By the way, I'm trying to use it like this

```
public class event
{
   **[COLOR="Blue"]private[/COLOR]** GregorianCalendar calStart; [COLOR="Lime"]//Declaration of calStart[/COLOR]
        [COLOR="Gray"]...some other woring code here...[/COLOR]
   **[COLOR="blue"]public[/COLOR]** setCalStart(GregorianCalendar a)
       {
        if(a == null)
            {
             System.out.println("Fatal error, reference to GregorianCalendar object in null");System.exit(0);
            } 
         calStart = a.clone()
        }

}
```


Thanks,
Sidney

P.S. I'll admit it right now, this is help with a homework assignment, but I'm not asking for help with the homework, just asking about java in general.

---

### Post by dwhitney67 on 2010-10-28
Please show an example where you are using clone().  copy() is not the same.

Here's a basic example:
```

import java.util.GregorianCalendar;

class Cal
{
   private GregorianCalendar calStart;

   public Cal()
   {
      calStart = new GregorianCalendar(2010, 10, 28);
   }

   public GregorianCalendar getNextDay()
   {
      GregorianCalendar nextDay = (GregorianCalendar) calStart.clone();
      nextDay.add(GregorianCalendar.DAY_OF_MONTH, 1);
      return nextDay;
   }

   public static void main(String[] args)
   {
      Cal c = new Cal();
      GregorianCalendar gc = c.getNextDay();
   }
}

```

---

### Post by Sidneyaks on 2010-10-28
Oh! Sorry, I meant to write a.clone() but wrote a.copy().

I edited my original post accordingly, sorry for that.

Also, thank you for the example on casting.

---

