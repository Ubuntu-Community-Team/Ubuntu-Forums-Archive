---
title: "Java: Trim trailing zeros"
date: 2009-09-13
forum: Programming Talk
---

### Post by falconindy on 2009-09-13
So I've got a for loop that makes interest calculations based on the iterator. The iterator is increased by .125 each loop, and its printed at the beginning of each line with System.out.printf() along with the the other involved calculations. For now, I'm using the substitution %.3f to make sure it gets all 3 significant digits to the right of decimal, but I'd rather that the whole numbers be printed without trailing zeros. I suppose this might make more sense in code:

```
for (int i = 5; i <= 8; i += .125) {
    System.out.printf("%.3f", i);
}
```And this results in ```
5.000
5.125
5.250
5.375
5.500
5.625
...
7.750
7.875
8.000
```My preferred output would be:
```

5
5.125
5.250
5.375
5.5
5.625
```etc etc etc. Can I accomplish this? It seems like C's version of printf can accomplish this with %g, but it doesn't appear to function the same in Java.

---

### Post by Volt9000 on 2009-09-13
I don't think this will help, but I will point out that your loop variable i should be of type float and not int. This program shouldn't even work properly.

---

### Post by myrtle1908 on 2009-09-13
The java.math.BigDecimal class has a stripTrailingZeros method.  Perhaps you could use that.  Also there is a DecimalFormat class somewhere in the Java tree ... can't remember where off the top of my head.

---

### Post by Can+~ on 2009-09-13
+1 to the above.

Also, here is the format for Java's printf:
[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Formatter.html#syntax](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Formatter.html#syntax)

---

### Post by falconindy on 2009-09-13
> **Volt9000 said:**
> I don't think this will help, but I will point out that your loop variable i should be of type float and not int. This program shouldn't even work properly.
Mmm, right.. was rewriting it from memory. The actual class is written properly with a double, not an int and compiles/runs properly. This is just some mindless nitpicking of the formatting.

The formatter class is obviously what I'm using with printf, but it doesn't have the conversion I'm looking for. Not going to bother with a building a custom format. Oh well.

---

### Post by Mister.Vash on 2009-09-14
Try this out with the DecimalFormat

[PHP]
//First Java Program
import java.text.*;

public class Main {
  public static void main(String[] argv) throws Exception {

	for (double i = 5; i <= 16; i += .125) {
		DecimalFormat df = new DecimalFormat("#.###");
		//System.out.printf("%.3f\n",i);  //original format
		//System.out.printf("Decimal Format: " + df.format(i) +"\n"); //new format
		System.out.printf("Original Format: %.3f Decimal Format: " + df.format(i)+"\n",i); //combined
	}

  }
}
[/PHP]


This results in:
```

Original Format: 5.000 Decimal Format: 5
Original Format: 5.125 Decimal Format: 5.125
Original Format: 5.250 Decimal Format: 5.25
Original Format: 5.375 Decimal Format: 5.375
Original Format: 5.500 Decimal Format: 5.5
Original Format: 5.625 Decimal Format: 5.625
Original Format: 5.750 Decimal Format: 5.75
Original Format: 5.875 Decimal Format: 5.875
Original Format: 6.000 Decimal Format: 6
Original Format: 6.125 Decimal Format: 6.125
...
Original Format: 15.000 Decimal Format: 15
Original Format: 15.125 Decimal Format: 15.125
Original Format: 15.250 Decimal Format: 15.25
Original Format: 15.375 Decimal Format: 15.375
Original Format: 15.500 Decimal Format: 15.5
Original Format: 15.625 Decimal Format: 15.625
Original Format: 15.750 Decimal Format: 15.75
Original Format: 15.875 Decimal Format: 15.875
Original Format: 16.000 Decimal Format: 16

```

---

### Post by falconindy on 2009-09-14
> **Mister.Vash said:**
> Try this out with the DecimalFormat

[php]
//First Java Program
import java.text.*;

public class Main {
  public static void main(String[] argv) throws Exception {

    for (double i = 5; i <= 16; i += .125) {
        DecimalFormat df = new DecimalFormat("#.###");
        //System.out.printf("%.3f\n",i);  //original format
        //System.out.printf("Decimal Format: " + df.format(i) +"\n"); //new format
        System.out.printf("Original Format: %.3f Decimal Format: " + df.format(i)+"\n",i); //combined
    }

  }
}
[/php]

That'll do nicely! Thanks!!

---

