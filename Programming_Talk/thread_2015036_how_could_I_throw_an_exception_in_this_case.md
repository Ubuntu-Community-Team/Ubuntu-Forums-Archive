---
title: "how could I throw an exception in this case"
date: 2012-07-02
forum: Programming Talk
---

### Post by Mia_tech on 2012-07-02
guys, I'm reading a formula from file like: 2 + 2 - ( 3 - 1 ) * 3 $, but I want to be able to throw an exception if there are two operands together like: 2 + 2 3 * 4 $ or if there are two operators together like: 2 + + 3 $.

here's what I have so far, the operator part the program detects it, but I'm having problem with two operands together. I would like to throw the exception where "Bad Formula!..." is

```
while(in.hasNext())
        {
            String next = in.next();
            do
            {
                if (optor.isOperator(next)) 
                {
                    processOptor(next);
                    oprandCount = 0;
                } 
                else 
                {
                    if(oprandCount == 0)
                    {
                        oprand.push(Integer.parseInt(next));
                        strOut += next+" ";
                        oprandCount++;                        
                    }
                    else
                    {
                        System.out.println("Bad formula!...");
                        System.exit(0);
                    }
                }                                   
                next = in.next();
 
                if(next.equals("$"))
                    processOptor(next);
 
            }while(!next.equals("$"));
```

---

### Post by dwhitney67 on 2012-07-02
If you want to throw an exception, then try throwing an Exception object.  For example:
```

throw new Exception("Bad formula");

```

If you want to do something a wee bit better, define your own exception class; for example:
```

public class BadFormula extends Exception
{
    public BadFormula(String what)
    {
        super(what);
    }
}

```
Then you could throw that:
```

throw new BadFormula("Illegal formula entered.");

```

P.S.  You will need to declare your method to indicate that it throws an exception; something like:
```

public void getFormula(...) throws BadFormula
{
   blah, blah, blah...

   if (badFormula)
   {
       throw new BadFormula(...);
   }
}

```

---

