---
title: "simple java seems breaking head"
date: 2010-07-24
forum: Programming Talk
---

### Post by navaneethan on 2010-07-24
```
import java.util.Scanner;



class Calculation{

	

	private int noRange;



	

	public void getData(int no)

	{

		noRange=no;

	}

	public int calculateSeries()

	{

		int data=1;

		while(data<=noRange)

		{

			if(data%2==0)

				return -data;

			else

				{

					return data;

				}

			data++;

		}

	}

}

public class Series{

	public static void main(String args[])

	{

		Calculation calc = new Calculation();

		Scanner r = new Scanner(System.in);

		System.out.println("Enter the Integer No:");

		calc.getData(r.nextInt());

		

		System.out.println("The series are:"+calc.calculateSeries());

	}

				

}
```

Here I have programmed for the output

Enter the Integer no:6
1-2+3-4+5-6

likewise according to input..

but i get error what is the problem dude

---

### Post by dwhitney67 on 2010-07-24
Fix this code:
```

			if(data%2==0)

				return -data;

			else

				{

					return data;

				}

			data++;

```
Then maybe the issue with your code will be corrected.

Btw, above, the value of 'data' is _never_ incremented.  Your function _always_ returns 1, if the value of noRange is 1 or greater.  Otherwise your function doesn't return anything... oops!

P.S.  Typically one calls their set-accessor methods with the prefix "set", not "get".  Consider renaming your function getData to setData.

---

### Post by shadylookin on 2010-07-24
while(data<=noRange)

the condition is not guaranteed to run once so there's no guarantee that it will ever return. You need to add a return statement after the while loop.

data++;

is unreachable because of your return statements

---

### Post by trent.josephsen on 2010-07-24
Holy whitespace, Batman!

---

### Post by navaneethan on 2010-07-28
How it will return 1 always?

---

### Post by hyperAura on 2010-07-28
you only return a value once.. what you can do is to have a while loop where you will call the method calculateSeries, but each time u will feed to it the value returned from the previous run.. Don't know if this does makes sense to you but it is an easy solution if u want to return a value every time..

---

