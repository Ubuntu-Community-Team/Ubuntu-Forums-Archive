---
title: "What does # do in DecimalFormat in Java?"
date: 2009-10-17
forum: Programming Talk
---

### Post by s3a on 2009-10-17
In the following code:
```
import java.text.DecimalFormat;

import java.util.Scanner;

public class decform_checker
{
	public static void main (String [] args)
	{
		Scanner kb = new Scanner(System.in);
		
		double number = kb.nextDouble();
		
		DecimalFormat formatter = new **DecimalFormat("#0000.000");**
		System.out.println(formatter.format(number));
	}
}
```

What does the **#** do in the line in bold?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by kavon89 on 2009-10-18
Try the Java API, once you learn to read/browse it you'll know how everything in the Java library works. ;D

[http://java.sun.com/javase/6/docs/api/java/text/DecimalFormat.html](http://java.sun.com/javase/6/docs/api/java/text/DecimalFormat.html)

---

### Post by SSTwinrova on 2009-10-18
[http://java.sun.com/javase/6/docs/api/java/text/DecimalFormat.html](http://java.sun.com/javase/6/docs/api/java/text/DecimalFormat.html)

Scroll down to Special Format Characters, it has what all the various possibilities mean.

---

### Post by s3a on 2009-10-19
All it says is

"#  	Number 	Yes 	Digit, zero shows as absent ."

That is not enough information for me to understand :(.

---

### Post by myrtle1908 on 2009-10-20
Both '#' and '0' mean digit.  If you use '#' but you do not supply a digit then it (the result) is left empty (blank).  If you use '0' but do not supply a digit in said position then zero is inserted instead.

Take this example format: "####.000"

This pattern means four places before the decimal point, which are empty if not filled, and three places after the decimal point, which are 0 if not filled.

So if you supplied '12.65' to this pattern then the result would be '12.650'.

---

### Post by s3a on 2009-10-20
Thanks!

---

