---
title: "java methods......."
date: 2009-08-22
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-22
can i have same method names in java?
i tried but there was errors, so i passes differnt datatypes, then it worked fine......
```
import java.util.Random;

public class samemehod {
	void prt(String s) {
		System.out.println(s);
		
	}
	
	int ret(int i) {
		Random ran=new Random();
		return i+ran.nextInt()%10;
	}
	
	double ret(double d) {
		Random ran =new Random ();
		return ran.nextDouble()%10+d;
	}
public static void main(String[] args) {
	samemehod s=new samemehod();
	s.prt("int s="+s.ret(10));
	s.prt("doube d="+s.ret(10.5));
}
}

``` 

as u see there is function ```
void prt(String s) {
		System.out.println(s);
		
	}
```
for this function if i pass like 
```
 s.prt(+10); or s.prt(10)
``` it wont work
but it works if i write,
```
s.prt("int d="+10);
```

can i convert int to string before display or above method is correct?
how to keep same method name in above case, without passing any parameters?

---

### Post by slavik on 2009-08-22
for automatic conversion
```

s.prt(""+10);

```

or the proper OO approach

```

s.prt(new String(10));

```

---

### Post by abhilashm86 on 2009-08-22
> **slavik said:**
> for automatic conversion
or the proper OO approach

```

s.prt(new String(10));

```

using this gives an error, compiler says ```
the constructor String(int) is undefined
```, why is this error?

---

### Post by shadylookin on 2009-08-22
> **abhilashm86 said:**
> can i have same method names in java?
i tried but there was errors, so i passes differnt datatypes, then it worked fine......


yes it's called method overloading. The name can be the same, but the parameters have to be different.

> 
as u see there is function ```
void prt(String s) {
		System.out.println(s);
		
	}
```
for this function if i pass like 
```
 s.prt(+10); or s.prt(10)
``` it wont work
but it works if i write,
```
s.prt("int d="+10);
```

can i convert int to string before display or above method is correct?
how to keep same method name in above case, without passing any parameters?

prt requires a string. 10 is not a string and +10 is not a string. To make it a string you have to have quotes like slavik has posted.

---

### Post by Drone022 on 2009-08-22
> 
Quote:
Originally Posted by slavik View Post
for automatic conversion
or the proper OO approach

Code:

s.prt(new String(10));

using this gives an error, compiler says
Code:

the constructor String(int) is undefined

, why is this error? 

String(int) isn't a valid constructor so you would have to do 
```
s.prt(new String("10"));
```

or maybe use a 'toString()' method

```
Integer int1 = new Integer(10);
s.prt(int1.toString());
```

Pretty sure an Integer is different from an int by the way.

---

### Post by dribeas on 2009-08-23
There is another way of implementing the conversion to String without the cost of concatenation ( ""+value, this implies creating an empty String object, and then creating a second String object with the number concatenated ) or creating an Integer you do not need ( new Integer(value).toString ):

```

int value = 10;
String str = Integer.toString( value );

```

---

