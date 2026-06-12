---
title: "Java6: Adding primitive member vars. to TreeSet&lt;Generics&gt;"
date: 2009-01-31
forum: Programming Talk
---

### Post by andrew222 on 2009-01-31
I have a question to ask about Java 6.  Today I tried to declare a TreeSet with a Generic type as Double as seen below..I was putting primitive double values which are member fields of a class I designed into the TreeSet.

```
TreeSet<Double> ts = new TreeSet<Double>();
```

Then after doing so, Eclipse told me that I can't do such an operation in Java 6 and had to change the compliance to work with Java 5.0.  

What I can't figure out is why? I made a prototype that puts straight primitive double values into a TreeSet with no error.  Now my deductive reasoning tells me that it has a problem using a primitive field of my class.

Does anyoneone know what specific changes were made to the API to make this happen?


Here is the whole program below...


```
import java.util.*;

class SP
{
	  String name;
	double percentageChange;
	
	SP()
	{this.name=null;this.percentageChange=0.0;}
	
	
	SP (String i_name, double i_percentageChange)
	{
		this.name = i_name;
		this.percentageChange = i_percentageChange;		
	}	
}


public class TreeSetDemo 
{
	

	public static void main(String [] args)
	{
		System.out.println("S&P's Best and Worst Performing Stocks of 2008");
		System.out.println("http://seekingalpha.com/article/112981-s-p-s-best-and-worst-of-2008\n\n");
		
		SP lb = new SP("Lehman Brothers", -99.96);
		SP wm = new SP("Washington Mutual", -99.84);
		SP wr = new SP("Wrigley", 36.58);
		SP fd = new SP("Family Dollar", 35.57);
		SP fm = new SP("Fannie Mae", -98.10);
		SP frm = new SP("Freddie Mac", -97.86);
		SP aig = new SP("AIG", -97.31);
		SP cc = new SP("Circuit City", -96.90);
		SP ab= new SP("Anheuser-Busch", 31.03);
		SP ust = new SP("UST", 26.61);
		SP am = new SP("Amgen", 24.35);
		SP bph = new SP("Barr Pharma", 23.92);
		SP ggp = new SP("General Growth Properties", -96.87);
		SP ew = new SP("EW Scripps", -95.09);
		SP abk = new SP("Ambac Financial", -94.96);
		SP bs = new SP("Bear Stearns", -89.43);
		SP nc = new SP("National City", -89.00);
		SP gf = new SP("Genworth Financial", -88.88);
		SP dd = new SP("Developers Diversified",-87.26);
		
		SP [] spArr = {lb, wm, wr, fd,fm,frm, aig,cc,ab,ust,am,bph,ggp,ew,abk,bs,nc,gf,dd};
		
		/*I have Java 6 installed and had to change worspace compliance to Java 5.0 in order to
		 make the declaration below work*/
		TreeSet<Double> ts = new TreeSet<Double>();
		
		
		
		System.out.println("Name" + ": " + "Percentage Change" );
		System.out.println("-------------------------");
		for(int i =0; i < spArr.length; i++)
		{	
			ts.add(spArr[i].percentageChange);
			System.out.println(spArr[i].name + ": " + spArr[i].percentageChange + '\n');
			
		}
		System.out.println("\nS&P 2008 stocks percentage change values above sorted from least to greatest ");
		System.out.println("There are "+ts.size() + " elements in this TreSet");
		System.out.println("The TreeSet dectects the lowest element as: " + ts.first());
		System.out.println(ts + "\n\n");
		System.out.println("Between the range: 20.0--30.0");
		System.out.println(ts.subSet(20.00,30.00));
		System.out.println("\nBetween the range: 30.0--40.0");
		System.out.println(ts.subSet(30.00,40.00));
		System.out.println("\nBetween the range: -100.0--(-90.0)");
		System.out.println(ts.subSet(-100.00,-90.00));
		System.out.println("\nBetween the range: -90.0--(-80.0)");
		System.out.println(ts.subSet(-90.00,-80.00));
		
		
	
	}

}

```


Ok, here is the prototype I talked about

```
import java.util.*;


public class demo {

public static void main(String [] args)
	{
	double [] d = {11.11,22.22,33.33};
	TreeSet<Double> ts = new TreeSet<Double>();
	
		ts.add(d[0]);
			
	}
}

```

---

### Post by CptPicard on 2009-01-31
Could you give the exact error you're getting? Can you isolate the problem into a more concise demonstrative case?

You should be really cautious about putting floating-point numbers into a set like that, by the way -- their equality is tricky, and especially after arithmetic operations two of them are rarely equal in practice although mathematically they would be.

---

### Post by Reiger on 2009-01-31
You need to box it first, like so:
(modified your prototype)
```

import java.util.*;


public class demo {

public static void main(String [] args)
	{
	double [] d = {11.11,22.22,33.33};
	TreeSet<Double> ts = new TreeSet<Double>();
	
		ts.add(**[COLOR="#ff0000"]new Double([/COLOR]**d[0][COLOR="Red"]**)**[/COLOR]);
			
	}
}
```

---

### Post by muntasir_120 on 2009-01-31
The (shorter) code compiles without any errors or warnings on compiling in jdk1.6 with javac. The problem must be with eclipse.

---

### Post by andrew222 on 2009-01-31
CtpPicard:  I received the error message as a "red box error" from Eclipse which plainly told me as an itelli-sense option "change workspace compliance to Java 5.0 in order to make the declaration work".  I searched the API to find any changes and then came here to see if anyone else has experienced this.

Actually, I started a new project and pasted the exact code into a new class to reproduce the error from Eclipse and did not get one.  We all know how Eclipse complains about things like uninitialized variables etc. when typing in code  Anyways, I feel bad that I can't reproduce the actual error for you.

I do agree that it is bad practice to compare floating point values (can strictfp help this?) but this is just a prototype that I am doing for training in Consultancy.



Reiger:  I agree that the new "Double" in the add statement is needed as well.

Thank you and have a pleasant weekend,

Andrew

---

### Post by CptPicard on 2009-01-31
You might want to try a clean/rebuild in the old project, or something... it sounds weird.

As regards the floating point... BigDecimal probably would be the way to go in this case.

---

