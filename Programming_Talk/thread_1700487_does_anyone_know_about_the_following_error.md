---
title: "does anyone know about the following error"
date: 2011-03-05
forum: Programming Talk
---

### Post by ajay.eeralla on 2011-03-05
package sqrtbigint;
import java.math.BigInteger;
import java.util.Scanner;
/**
 *
 * @author ajay
 */
public class Sqrtbigint {

    /**
     * @param args the command line arguments
     */
 
 public static void main(String[] args)

 {
        // TODO code application logic here
    System.out.println("Enter a big integer");
 Scanner input=new Scanner(System.in);
 BigInteger n=new BigInteger(input.toString());

 BigInteger a = BigInteger.ONE;
  BigInteger b = new BigInteger(n.shiftRight(5).add(new BigInteger("8")).toString());
  while(b.compareTo(a) >= 0) {
    BigInteger mid = new BigInteger(a.add(b).shiftRight(1).toString());
    if(mid.multiply(mid).compareTo(n) > 0) b = mid.subtract(BigInteger.ONE);
    else a = mid.add(BigInteger.ONE);
  }
 System.out.println("sqrt of n= "+a.subtract(BigInteger.ONE).toString());
    


    }
    }


Exception in thread "main" java.lang.NumberFormatException: Illegal embedded sign character
        at java.math.BigInteger.<init>(BigInteger.java:308)
        at java.math.BigInteger.<init>(BigInteger.java:470)
        at sqrtbigint.Sqrtbigint.main(Sqrtbigint.java:25)
Java Result: 1

---

### Post by lykeion on 2011-03-05
You don't use Scanner.toString() to read from input, it's Scanner.next() or in your case Scanner.nextBigInteger() so line 25 should be:
```
BigInteger n=input.nextBigInteger();
```

Read about using the Scanner class here: [http://forums.hotjoe.com/posts/list/128.page](http://forums.hotjoe.com/posts/list/128.page)

---

### Post by ajay.eeralla on 2011-03-07
Thank you very much...

---

### Post by ajay.eeralla on 2011-03-07
how to write e^sqrt(lognloglog(n)) ,where n is biginteger
i wrote   Double a;
a=Math.pow(e,Math.sqrt(Math.log(num.longValue())*M  ath.log(Math.log(num.longValue())))));
but iam getting error

---

### Post by Arndt on 2011-03-07
> **ajay.eeralla said:**
> how to write e^sqrt(lognloglog(n)) ,where n is biginteger
i wrote   Double a;
a=Math.pow(e,Math.sqrt(Math.log(num.longValue())*M  ath.log(Math.log(num.longValue())))));
but iam getting error

What error?

---

### Post by ajay.eeralla on 2011-03-08
n is biginteger, type mismatch coming...

---

### Post by ajay.eeralla on 2011-03-08
i have a big integer n,
now i want find construct factor base, ie. i have sieve {3,5,7,11...} are in integer array.
now i have to construct factorbase by checking legendre symbol,
i.e, to check wether n is quadratic residue modue 3 or 5 or 7....
A number n is said to be quadratic residue modulo p, if there exist x belongs to zp suchthat x^2 =n(modp) ,
iam unable to divide n by 3 or 5or 7...
because n is biginteger and array is int.

---

### Post by ajay.eeralla on 2011-03-08
my intention is to find log values to very Bigintegers is it possible to find

---

### Post by PaulM1985 on 2011-03-08
Why not create an array of BigIntegers instead of the array of integers using the static BigInteger.valueOf(long) function?

Then you can use the remainder(BigInteger) function to find the %.

Paul

---

### Post by PaulM1985 on 2011-03-08
Have you considered implementing your own version of the log function for big integers?

[http://en.wikipedia.org/wiki/Logarithm#Taylor_series](http://en.wikipedia.org/wiki/Logarithm#Taylor_series)

Paul

---

### Post by MadCow108 on 2011-03-08
as you assign it to a double I assume you do not need infinite precision.
maybe it is enough to just transform the BigInteger to a double (.doubleValue())

---

### Post by Zugzwang on 2011-03-08
> **ajay.eeralla said:**
> n is biginteger, type mismatch coming...

Please copy & paste *precise* error messages. Also state which language you are using. While the main command looks like Python, the line beforehand "Double a;" doesn't look like python, C++ nor Java.

---

### Post by trent.josephsen on 2011-03-08
It's valid Java (Double is a wrapper class for the built-in type).

The "error" sounds more like a "warning" (if in fact it's verbatim; what you said sounds a little weird as compiler output).  That said, none of us really know what you're trying to achieve or why on Earth you think BigInteger is necessary -- sounds like you don't need it if you can call .longValue() on it without checking bounds.  Or maybe you just don't understand the problem and you're throwing code at it hoping something will stick.  Either way, we need more information to help you.  Give some background.

---

### Post by Zugzwang on 2011-03-09
> **trent.josephsen said:**
> It's valid Java (Double is a wrapper class for the built-in type).

Ah, ok, I didn't expect that to work without using the constructor for the Double class explicitly.

---

### Post by trent.josephsen on 2011-03-09
> **Zugzwang said:**
> Ah, ok, I didn't expect that to work without using the constructor for the Double class explicitly.
Automatic wrapping and unwrapping was added only recently (1.6 I think), so your confusion is not without justification.

---

### Post by StephenF on 2011-03-09
> lognloglog(n)
This is ambiguous; note the inconsistent use of brackets. It could be one of.[INDENT]
log_n log log n

or 

log n log log n[/INDENT]

---

### Post by ajay.eeralla on 2011-03-11
package pollardp1;
import java.math.BigInteger;
import java.security.SecureRandom;
import java.util.*;
import java.io.*;
/**
 *
 * @author ajay
 */
public class Pollardp1 {
private final static BigInteger ZERO = new BigInteger("0");
    private final static BigInteger ONE  = new BigInteger("1");
    private final static BigInteger TWO = new BigInteger("2");
 //private final static SecureRandom random = new SecureRandom();



    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here

     System.out.println("Enter a number to be factor");
       Scanner input=new Scanner(System.in);
       BigInteger n=input.nextBigInteger();
       Random rand = new Random();

       BigInteger b=lnr(BigInteger.valueOf(rand.nextInt()),n);
        //BigInteger b  = 
        BigInteger r2;
int i=2;
    BigInteger r=b.mod(n);
    BigInteger gcd=r.subtract(ONE).gcd(n);
    while(true){
     while(gcd.equals(ONE))
     {
      
        
            for(int j=1;j<i;j++)
         {
             r = r.multiply(r).mod(n);
        gcd=(r.subtract(ONE)).gcd(n);
    }
     i++;
     }
    if(gcd.equals(n))
    {
        System.out.println(ONE + "," + gcd);
        break;
        }
        else

    {
        System.out.println(gcd + "," + n.divide(gcd));
        break;
        }
        }
    }}


Enter a number to be factor
632887
Exception in thread "main" java.lang.RuntimeException: Uncompilable source code
        at pollardp1.Pollardp1.main(Pollardp1.java:34)
Java Result: 1
BUILD SUCCESSFUL (total time: 12 seconds)

---

### Post by Arndt on 2011-03-11
> **ajay.eeralla said:**
> package pollardp1;
import java.math.BigInteger;
import java.security.SecureRandom;
import java.util.*;
import java.io.*;
/**
 *
 * @author ajay
 */
public class Pollardp1 {
private final static BigInteger ZERO = new BigInteger("0");
    private final static BigInteger ONE  = new BigInteger("1");
    private final static BigInteger TWO = new BigInteger("2");
 //private final static SecureRandom random = new SecureRandom();



    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here

     System.out.println("Enter a number to be factor");
       Scanner input=new Scanner(System.in);
       BigInteger n=input.nextBigInteger();
       Random rand = new Random();

       BigInteger b=lnr(BigInteger.valueOf(rand.nextInt()),n);
        //BigInteger b  = 
        BigInteger r2;
int i=2;
    BigInteger r=b.mod(n);
    BigInteger gcd=r.subtract(ONE).gcd(n);
    while(true){
     while(gcd.equals(ONE))
     {
      
        
            for(int j=1;j<i;j++)
         {
             r = r.multiply(r).mod(n);
        gcd=(r.subtract(ONE)).gcd(n);
    }
     i++;
     }
    if(gcd.equals(n))
    {
        System.out.println(ONE + "," + gcd);
        break;
        }
        else

    {
        System.out.println(gcd + "," + n.divide(gcd));
        break;
        }
        }
    }}


Enter a number to be factor
632887
Exception in thread "main" java.lang.RuntimeException: Uncompilable source code
        at pollardp1.Pollardp1.main(Pollardp1.java:34)
Java Result: 1
BUILD SUCCESSFUL (total time: 12 seconds)

Do use code tags when inserting code in a message.

I don't know the answer, but did you google for the interesting part of the error message? Googling for "java.lang.RuntimeException: Uncompilable source code" brings up some pages which seem relevant.

---

### Post by Some Penguin on 2011-03-11
I fail to see why people should attempt to solve errors when posters refuse to make the slightest effort themselves, such as -- oh, I don't know, reading 'compilation error' with a specific line number; figuring out what that line is and reading it; and failing to realize an obvious mistake, compiling it to see what the error actually is.

---

### Post by ajay.eeralla on 2011-03-11
package funfun;
import java.math.BigInteger;
/**
 *
 * @author ajay
 */
public class Fun{
   private  final static  BigInteger ONE=new BigInteger("1");
    private  final static  BigInteger ZERO=new BigInteger("0");
     private  final static  BigInteger TWO=new BigInteger("2");
public static BigInteger sqrt(BigInteger n) {
        BigInteger a = BigInteger.ONE;
        BigInteger b = new BigInteger(n.shiftRight(5).add(new BigInteger("8")).toString());
        while (b.compareTo(a) >= 0) {
            BigInteger mid = new BigInteger(a.add(b).shiftRight(1).toString());
            if (mid.multiply(mid).compareTo(n) > 0) {
                b = mid.subtract(ONE);
            } else {
                a = mid.add(ONE);
            }
        }
        return a.subtract(ONE);
    }//end of sqrt of n

    //legendre symbol
    public BigInteger legende(BigInteger n, int s) {

        BigInteger mone = new BigInteger("-1");
        BigInteger p = new BigInteger("" + s);
        BigInteger d = p.subtract(ONE).divide(TWO);
        BigInteger c = n.modPow(d, p);
        if (c.compareTo(ONE) == 0) {
            return ONE;
        } else {
            return ZERO;
        }
    }
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {

        int fcount=8; 
int [] factorbase={2,3,11,17,19,23,43,47};
int k=0;
 BigInteger n= new BigInteger("1042387");
BigInteger Sqrt=sqrt(n);
BigInteger t=Sqrt.add(ONE);
 int sscount=0;
BigInteger [] s=new BigInteger[500];
BigInteger f;
BigInteger m;
while(t.compareTo(Sqrt.add(BigInteger.valueOf(418)))!=0)
        {
        f=t.multiply(t).subtract(n).mod(n);
        for(int i=0;i<fcount;i++)
        {

        BigInteger z= BigInteger.valueOf(factorbase[i]);
            m=f.mod(z);
if(m.compareTo(ZERO)==0)
{
    s[k]=f;
     k++;
     sscount++;
            }
        }

}
for(int q=0;q<sscount;q++)

{
    System.out.println(""+s[q]);
}
//    if(jTextField2.getText().isEmpty())
//            jTextField2.setText(jTextField2.getText()+s[q]);
//    else
//        jTextField2.setText(jTextField2.getText()+","+s[q]);

}

              
        }


run:
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 500
        at funfun.Fun.main(Fun.java:68)
Java Result: 1
BUILD SUCCESSFUL (total time: 0 seconds)

---

### Post by Arndt on 2011-03-11
> **ajay.eeralla said:**
> package funfun;
import java.math.BigInteger;
/**
 *
 * @author ajay
 */
public class Fun{
   private  final static  BigInteger ONE=new BigInteger("1");
    private  final static  BigInteger ZERO=new BigInteger("0");
     private  final static  BigInteger TWO=new BigInteger("2");
public static BigInteger sqrt(BigInteger n) {
        BigInteger a = BigInteger.ONE;
        BigInteger b = new BigInteger(n.shiftRight(5).add(new BigInteger("8")).toString());
        while (b.compareTo(a) >= 0) {
            BigInteger mid = new BigInteger(a.add(b).shiftRight(1).toString());
            if (mid.multiply(mid).compareTo(n) > 0) {
                b = mid.subtract(ONE);
            } else {
                a = mid.add(ONE);
            }
        }
        return a.subtract(ONE);
    }//end of sqrt of n

    //legendre symbol
    public BigInteger legende(BigInteger n, int s) {

        BigInteger mone = new BigInteger("-1");
        BigInteger p = new BigInteger("" + s);
        BigInteger d = p.subtract(ONE).divide(TWO);
        BigInteger c = n.modPow(d, p);
        if (c.compareTo(ONE) == 0) {
            return ONE;
        } else {
            return ZERO;
        }
    }
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {

        int fcount=8; 
int [] factorbase={2,3,11,17,19,23,43,47};
int k=0;
 BigInteger n= new BigInteger("1042387");
BigInteger Sqrt=sqrt(n);
BigInteger t=Sqrt.add(ONE);
 int sscount=0;
BigInteger [] s=new BigInteger[500];
BigInteger f;
BigInteger m;
while(t.compareTo(Sqrt.add(BigInteger.valueOf(418)))!=0)
        {
        f=t.multiply(t).subtract(n).mod(n);
        for(int i=0;i<fcount;i++)
        {

        BigInteger z= BigInteger.valueOf(factorbase[i]);
            m=f.mod(z);
if(m.compareTo(ZERO)==0)
{
    s[k]=f;
     k++;
     sscount++;
            }
        }

}
for(int q=0;q<sscount;q++)

{
    System.out.println(""+s[q]);
}
//    if(jTextField2.getText().isEmpty())
//            jTextField2.setText(jTextField2.getText()+s[q]);
//    else
//        jTextField2.setText(jTextField2.getText()+","+s[q]);

}

              
        }


run:
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 500
        at funfun.Fun.main(Fun.java:68)
Java Result: 1
BUILD SUCCESSFUL (total time: 0 seconds)

Use code tags. Turn off smileys.

---

### Post by GregBrannon on 2011-03-11
Arndt++.

Your array s[] is only allowed 500 members, s[0] through s[499].  I suspect your loop near the end is getting to s[500].

Hints: Use better variable names that describe what they are.  Add a comment or two to explain what's going on.

---

### Post by Some Penguin on 2011-03-11
And don't repost questions in entirely new threads without putting any effort into them.

---

### Post by uRock on 2011-03-11
5 matching threads merged.

---

