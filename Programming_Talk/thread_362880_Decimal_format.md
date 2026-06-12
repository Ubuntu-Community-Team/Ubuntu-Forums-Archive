---
title: "Decimal format"
date: 2007-02-16
forum: Programming Talk
---

### Post by Essa on 2007-02-16
Hii guys...I made this code but the problem is I want to get in the output the currency format for example if entered 1000 i need to get it 1,000..but my code seems not to function like this  
I could really use some help here thanks.

Heres the code 
```

import java.text.*;
import java.util.Scanner;
public class BD
{
	public static void main(String [] args)
		
	{
		
		DecimalFormat myformat= new DecimalFormat("BD ###.000");
			Scanner MyScanner = new Scanner (System.in);
			Double BD;
			System.out.println("type the amount of Bahraini Dinars ");
			BD = MyScanner.nextDouble();
			System.out.println("BD");
			
		
	}
}
```

---

### Post by supirman on 2007-02-16
I don't do java, but this looks like what you may need:
[http://72.5.124.55/j2se/1.4.2/docs/api/java/text/DecimalFormat.html](http://72.5.124.55/j2se/1.4.2/docs/api/java/text/DecimalFormat.html)

Looks like you  need to tell it how to group characters, so
```

DecimalFormat myformat= new DecimalFormat("BD #,###.000");

```

---

