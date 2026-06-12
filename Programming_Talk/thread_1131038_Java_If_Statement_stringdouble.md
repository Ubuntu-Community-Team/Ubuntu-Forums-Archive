---
title: "Java If Statement string/double"
date: 2009-04-20
forum: Programming Talk
---

### Post by Texas Longhorn on 2009-04-20
Hello all,

I'm an absolute newbie to Java (and programming in general), so apologies in advance for any overly obvious questions...any help with the following would be greatly appreciated.

I have the following bit of code:
```

	public static double erchk(String s)
	{

		if(Double.parseDouble(s) == 123456789) return 1/0;
		else if(s.compareTo("NA") == 0) return 0;
		else return Double.parseDouble(s);

	}

```

In the data I feed into the program, certain elements contain the value 123456789.00.  When the above code encounters this value, I want to convert it into text (such as "NaN").  I've taken various stabs at this with no luck.  Any tips would be wonderful.

Thanks,
Bill

---

### Post by dwhitney67 on 2009-04-20
Try to see if you can return Double.NaN in lieu of attempting to perform the divide-by-zero operation.

P.S.  Some test code I threw together in a hurry; notice I had to reorganize the statements in erchk().  You may want to guard the code with a try/catch block; otherwise it would be "easy" to break the parseDouble() call.
```

class Parser
{
  public static double erchk(String s)
  {
    if (s == "NA") return 0;

    if (Double.parseDouble(s) == 123456789) return Double.NaN;

    return Double.parseDouble(s);
  }

  public static void main(String[] args)
  {
    double value1 = erchk("123456789");
    double value2 = erchk("NA");
    double value3 = erchk("1234");

    System.out.println("value1 = " + value1);
    System.out.println("value2 = " + value2);
    System.out.println("value3 = " + value3);
  }
}

```

---

### Post by Texas Longhorn on 2009-04-20
dwhitney67 - thank you for your quick reply.  Your solution worked perfectly...extremely helpful.

Thanks,
Bill

---

