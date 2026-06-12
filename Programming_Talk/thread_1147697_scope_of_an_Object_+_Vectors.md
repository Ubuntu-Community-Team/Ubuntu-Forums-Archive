---
title: "scope of an Object + Vectors"
date: 2009-05-03
forum: Programming Talk
---

### Post by mikemcleanuk on 2009-05-03
Hey have created a simple example of some object and vector code using 1 superclass and 1 sub-class.

The problem i have is the scope in which an object i assign has. When i replace the comment marks the code works fine but i get the compile error when i try to do the object calls outside of the IF statement. 

For this example it wouldnt matter but i need a way to be able to use the objects methods from anywhere within the code after i have done the "instance of" assignements.

Thanks in Advance
Mike

```
import java.util.*;
import javax.swing.*;

public class Vectors
{
	public static void main(String[] args) 
    {
		Vector <Appliance> myAppliances = new Vector <Appliance>();
		
		myAppliances.add(new Television(true, 1,1));
	
		if (myAppliances.elementAt(0) instanceof Television) 
		{
			Television tv1 = (Television)myAppliances.elementAt(0);
			/*
			System.out.println(tv1);
			tv1.setPower(false);
			System.out.println(tv1);
			tv1.setPower(true);
			System.out.println(tv1);
			tv1.setChannel(2);
			System.out.println(tv1);
			tv1.setVolume(2);
			System.out.println(tv1);
			*/
		}
		
		System.out.println(tv1);
		tv1.setPower(false);
		System.out.println(tv1);
		tv1.setPower(true);
		System.out.println(tv1);
		tv1.setChannel(2);
		System.out.println(tv1);
		tv1.setVolume(2);
		System.out.println(tv1);
	}
}
```


```
C:\JPR\ICA3\ICA3\Java\Demos>javac Vectors.java
Vectors.java:28: cannot find symbol
symbol  : variable tv1
location: class Vectors
                System.out.println(tv1);
                                   ^
Vectors.java:29: cannot find symbol
symbol  : variable tv1
location: class Vectors
                tv1.setPower(false);
                ^
Vectors.java:30: cannot find symbol
symbol  : variable tv1
location: class Vectors
                System.out.println(tv1);
                                   ^
Vectors.java:31: cannot find symbol
symbol  : variable tv1
location: class Vectors
                tv1.setPower(true);
                ^
Vectors.java:32: cannot find symbol
symbol  : variable tv1
location: class Vectors
                System.out.println(tv1);
                                   ^
Vectors.java:33: cannot find symbol
symbol  : variable tv1
location: class Vectors
                tv1.setChannel(2);
                ^
Vectors.java:34: cannot find symbol
symbol  : variable tv1
location: class Vectors
                System.out.println(tv1);
                                   ^
Vectors.java:35: cannot find symbol
symbol  : variable tv1
location: class Vectors
                tv1.setVolume(2);
                ^
Vectors.java:36: cannot find symbol
symbol  : variable tv1
location: class Vectors
                System.out.println(tv1);
                                   ^
9 errors
```

superclass:

```
import javax.swing.*;

public abstract class Appliance
{
	public boolean power;
	public ImageIcon picture;
	
	public Appliance(ImageIcon ii)
	{
		picture = ii;
	}
	
	boolean getPower()
	{
		return power;
	}
	
	void setPower(boolean p)
	{
		power = p;
	}
	
	public abstract ImageIcon getPicture();
	
	public String toString()
	{
		return "Appliance " + power;
	}
}
```

sub-class:

```
import javax.swing.*;

public class Television extends Appliance
{
	private int channel;
	private int volume;

	public Television()
	{
		super(new ImageIcon("../images/television.jpg"));
		power = false;
		channel = 1;
		volume = 5;
	}
	
	public Television(boolean p, int c, int v)
	{
		super(new ImageIcon("../images/television.jpg"));
		power = p;
		channel = c;
		volume = v;
	}
	
	public void setChannel(int C)
	{
		channel = C;
	}
	
	public int getChannel()
	{
		return channel;
	}
	
	public void setVolume(int V)
	{
		volume = V;
	}
	
	public int getVolume()
	{
		return volume;
	}
	
	public ImageIcon getPicture()
	{
		return picture;
	}
	
	public String toString()
	{
		return "Television " + power + " " + picture + " " + channel + " " + volume + "\n";
	}
}
```

---

### Post by dwhitney67 on 2009-05-03
The bottom line is that the variable tv1 is not accessible out of the if-block.  It's lifetime expires as soon as the if-block concludes.

You can define an Appliance handle outside the if-block, then recast as needed within the if-block.  Once the if-block is finished, use the Appliance handle for your set/get method calls.

Wrt printing a Television (or Applicance) object, you probably want to call the toString() method.

---

