---
title: "Super basic System.out.printf(); Question"
date: 2009-09-24
forum: Programming Talk
---

### Post by s3a on 2009-09-24
```
public class pf
{
public static void main (String [] args)
{
System.out.printf("%.2f", 123456);

}
}
```

It compiles successfully but why does it output gibberish?

It outputs:
Exception in thread "main" java.util.IllegalFormatConversionException: f != java.lang.Integer
	at java.util.Formatter$FormatSpecifier.failConversion(Formatter.java:4011)
	at java.util.Formatter$FormatSpecifier.printFloat(Formatter.java:2738)
	at java.util.Formatter$FormatSpecifier.print(Formatter.java:2683)
	at java.util.Formatter.format(Formatter.java:2449)
	at java.io.PrintStream.format(PrintStream.java:937)
	at java.io.PrintStream.printf(PrintStream.java:838)
	at pf.main(pf.java:18)

But I expect it to print out the first two digits of the number.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by s3a on 2009-09-24
I just realized that adding .0 after 123456 and making it %.-2f would do what I want but is there not a way to not require the extra .0 at the end?

Edit: Actually, that didn't work.

---

### Post by Finalfantasykid on 2009-09-24
```
System.out.printf("%.2f", 123456f);
```I've never used the printf(); in Java, so I'm not sure what the .2f represents, but for the moment, I'll assume that is correct.

But notice I added an f to the end of 123456f.  That says that that number in a floating point number, and not an int.  (I think lower case works.  If not try an upper case F)

Also why don't you just use println()?

---

### Post by credobyte on 2009-09-24
Just for the future knowledge - there's a section called [**Programming Talk**]("http://ubuntuforums.org/forumdisplay.php?f=39") ;)

---

### Post by myrtle1908 on 2009-09-24
> **s3a said:**
> ```
public class pf
{
public static void main (String [] args)
{
System.out.printf("%.2f", 123456);

}
}
```

It compiles successfully but why does it output gibberish?

It outputs:
Exception in thread "main" java.util.IllegalFormatConversionException: f != java.lang.Integer
	at java.util.Formatter$FormatSpecifier.failConversion(Formatter.java:4011)
	at java.util.Formatter$FormatSpecifier.printFloat(Formatter.java:2738)
	at java.util.Formatter$FormatSpecifier.print(Formatter.java:2683)
	at java.util.Formatter.format(Formatter.java:2449)
	at java.io.PrintStream.format(PrintStream.java:937)
	at java.io.PrintStream.printf(PrintStream.java:838)
	at pf.main(pf.java:18)

But I expect it to print out the first two digits of the number.

Any help would be greatly appreciated!
Thanks in advance!

The output is not "gibberish".  It is useful.  It is telling you that you are doing something wrong!  Learn from it.  As *Finalfantasykid* posted earlier, you are attempting to format an int as a float.  This is evident from this line in the stack trace: "Exception in thread "main" java.util.IllegalFormatConversionException: **f != java.lang.Integer**".

There are a number of ways to deal with this.

```
public class pf {
	public static void main(String[] args) {
		int iNum = 123456;
		Float fNum = new Float(123456);
		System.out.printf("%.2f\n", (float)iNum); // cast your int to a float
		System.out.printf("%.2f\n", fNum); // already a float
		System.out.printf("%.2f\n", 123456.5555); // prints 123456.56
	}
}
```

---

### Post by myrtle1908 on 2009-09-24
> **s3a said:**
> But I expect it to print out the **first two** digits of the number.

Are you sure about this?  That's not what "%.2f" will help with.  If you want the first two digits then why bother with a float at all?  Why not just use a string?

---

### Post by zinouch on 2009-09-25
> ```
public class pf {
    public static void main(String[] args) {
        int iNum = 123456;
        Float fNum = new Float(123456);
        System.out.printf("%.2f\n", (float)iNum); // cast your int to a float
        System.out.printf("%.2f\n", fNum); // already a float
        System.out.printf("%.2f\n", 123456.5555); // prints 123456.56
    }
}
```

the %.2F is used to around a float or a loonng float for just 2 number after point X.YY !!

---

