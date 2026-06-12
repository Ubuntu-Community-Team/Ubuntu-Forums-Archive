---
title: "(Java) Round() method"
date: 2010-01-05
forum: Programming Talk
---

### Post by s3a on 2010-01-05
I found the following with a google search on rounding numbers in java:

"Here is the code of program:
public class RoundTwoDecimalPlaces{
  public static void main(String[] args) {
    float num = 2.954165f;
    float round = Round(num,2);
    System.out.println("Rounded data: " + round);
  }

  public static float Round(float Rval, int Rpl) {
  float p = (float)Math.pow(10,Rpl);
  Rval = Rval * p;
  float tmp = Math.round(Rval);
  return (float)tmp/p;
    }
}"

From: [http://www.roseindia.net/java/beginners/RoundTwoDecimalPlaces.shtml](http://www.roseindia.net/java/beginners/RoundTwoDecimalPlaces.shtml)

I then tried to do it for myself and had trouble. Here is what I did:
```
public class rounding
{
    public static void main (String[] args)
    {
        double number = 10.768458039485;
        double round = Round(number, 2); // I am trying to round 10.768458039485 off to two decimal places
        System.out.println(number);
        //double a = Math.round(number);
        //System.out.println(rounded_number);
    }
}
```

I think that if I got this to work I would enjoy rounding numbers in such a way but if others have a different (but not too difficult) way of doing this, I'd be happy to see it :)

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2010-01-05
There are different ways to round numbers; one way is to do something like:
```

import java.math.*;

public class Round
{
   public static void main(String[] args)
   {
      BigDecimal  bd = new BigDecimal(10.768458039485);
      MathContext mc = new MathContext(4, RoundingMode.CEILING);

      System.out.println("Original: " + bd);
      System.out.println("Rounded : " + bd.round(mc));
   }
}

```

Refer to other "formatters", perhaps the DecimalFormat object.

In lieu of using Google as your first choice in performing research on Java, consider using the following [site]("http://java.sun.com/javase/6/docs/api/"):
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

---

### Post by PaulM1985 on 2010-01-05
The way that you have described seems to be the best way to be, but if you were looking for alternatives, some sort of converting to a string, manipulating it by removing characters and then converting it back to a float could be an option.  This can get quite complicated, so I would stick with that method.

I have just found that there is a decimal format class which you would look for on the API:
[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

The class is DecimalFormat and should do what you are after.

Paul

---

### Post by PaulM1985 on 2010-01-05
Doh, you beat me to it.

Paul

---

### Post by s3a on 2010-01-06
Actually, I already learned how to do these! I just did not practice them enough which is why I forgot how to do them. Thanks dwhitney67 and PaulM1985 for reminding about DecimalFormat. I also recalled the use of System.out.printf(); which I seem to prefer.

The following is my implementation of both for future readers:
```
import java.text.DecimalFormat;
public class rounding
{
	public static void main (String[] args)
	{
		double number = 10.768458039485;
		System.out.printf("%.2f ", number);
		DecimalFormat obj = new DecimalFormat("0.000");
		System.out.println(obj.format(number));
		
		//double round = Round(number, 2); // I am trying to round 10.768458039485 off to two decimal places
		//System.out.println(number);
		//double a = Math.round(number);
		//System.out.println(rounded_number);
	}
}
```

However given that it isn't so difficult, I would like to understand the bold parts in the following:
```
import java.text.DecimalFormat;
import java.math.*;
public class rounding
{
	public static void main (String[] args)
	{
		double number = 10.768458039485;
		System.out.printf("%.2f ", number);
		DecimalFormat obj = new DecimalFormat("0.000");
		System.out.println(obj.format(number));
		
		//double round = Round(number, 2); // I am trying to round 10.768458039485 off to two decimal places
		//System.out.println(number);
		//double a = Math.round(number);
		//System.out.println(rounded_number);
		
[B]		BigDecimal  bd = new BigDecimal(10.768458039485);
		MathContext mc = new MathContext(4, RoundingMode.CEILING);[/B]

		System.out.println("Original: " + bd);
		System.out.println("Rounded : " + bd.round(mc));

	}
}
```

What confuses me about the bold stuff is why CEILING is in capitals since I learned that Math.floor and Math.ceil (not even the full word ceiling) are not in capital letters. I'm guessing it's a completely different thing. I see that bd and mc are just regular and changeable variables. I also see that the number 4 determines how many numbers there are (including the numbers before the decimal point). Another thing I am questioning is if the rest has to be the way it is. I tried to change the words BigDecimal and MathContext as well as RoundingMode. I also tried making CEILING into small letters. Each of these transformations caused at least one syntax error. Is this something I have to memorize at this point or is there a way to break it down into simpler terms and make it more logical to make it easier to understand? (for a beginner like myself)

---

### Post by myrtle1908 on 2010-01-06
> **s3a said:**
> What confuses me about the bold stuff is why CEILING is in capitals

CEILING is an enumerated constant (read final) field of the RoundingMode Enumeration.  Constants are normally capitalised and words separated by an underscore.

[http://www.symatech.net/java-constant](http://www.symatech.net/java-constant)

[http://java.sun.com/j2se/1.5.0/docs/api/java/math/RoundingMode.html#CEILING](http://java.sun.com/j2se/1.5.0/docs/api/java/math/RoundingMode.html#CEILING)

---

### Post by dwhitney67 on 2010-01-06
> **s3a said:**
> ... Is this something I have to memorize at this point or is there a way to break it down into simpler terms and make it more logical to make it easier to understand? (for a beginner like myself)
You will (hopefully) learn that it is impossible to memorize everything; that is why we have books, reference manuals, and on occasion, hand-written personal notes.

Earlier I supplied you with a URL to the Java 6 API.  Bookmark this URL so that you do not have memorize things.  Of course, it is helpful (and this applies to any subject), that you have domain knowledge of the subject you are tackling so that you can recall whether something is feasible or not.  The details are in the books/manuals; thus no need to memorize them... unless you have the spare capacity in the 'noggin'.

Here's the Java SE 6 API URL again:
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)


P.S.  I was unaware of the System.out.println() feature you presented; that seems like the easiest to use.  I will keep that in mind for the future.

---

