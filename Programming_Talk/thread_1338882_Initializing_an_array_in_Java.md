---
title: "Initializing an array in Java"
date: 2009-11-26
forum: Programming Talk
---

### Post by swappo1 on 2009-11-26
Is it good programming practice to initialize an array in the constructor of a class?  I always initialize my variables in the constructor and am wondering if I should do the same with an array.  Here is my example of what I have done with initializing my array.  Is this correct?
```
class Temperature
{
	private double[][] temperature;
	
	public Temperature()
	{
		temperature = new double[12][2];
		
		for(int i = 0; i < temperature.length; i++)
			for(int j = 0; j < temperature[0].length; j++)
				temperature[i][j] = 0;
	}
}
```

---

### Post by NovaAesa on 2009-11-27
Yes, if you are programming in an OOP way (which Java basically forces), initialization of instance variables should occur in the constructor (unless you have a good reason not to initialize them there). This would be the temp = new double[x][y] part. However, you don't need to loop through them setting them to 0, as they are alredy zero. Also, when using 2D arrays in Java, they are actually arrays of array. You need to loop through the outer array initializing the inner arrays. It might be a bit different because you specified the size of the second dimension, I can't remember (I'm not on a machine with javac at the moment).

---

### Post by pbrockway2 on 2009-11-27
> **NovaAesa said:**
> It might be a bit different because you specified the size of the second dimension, I can't remember (I'm not on a machine with javac at the moment).

It is different - the following compiles and runs OK:

```

public class ArrayInitEg
{
    private double[][] data;

    public ArrayInitEg()
    {
        data = new double[12][2];
            // this one compiles but gives NPE at runtime
        //data = new double[12][];
    }

    public static void main(String[] args)
    {
        ArrayInitEg test = new ArrayInitEg();
        System.out.println("test.data[2][1]=" + test.data[2][1]);
    }
}

```

---

### Post by myrtle1908 on 2009-11-27
> **swappo1 said:**
> Is it good programming practice to initialize an array in the constructor of a class?  I always initialize my variables in the constructor and am wondering if I should do the same with an array.  Here is my example of what I have done with initializing my array.  Is this correct?

If you intend to use said arrays throughout the lifecycle of the class then yes, you should initialize at creation.  This (at least) is the rule I apply.

---

### Post by darthmob on 2009-11-27
Just a small thing but I think it would be more correct that way:

```
for(int i = 0; i < temperature.length; i++)
			for(int j = 0; j < temperature[i].length; j++)
				temperature[i][j] = 0;

```

In theory you could have differently sized arrays in each temperature[i] though I've never seen anyone making use of it. ;)

---

