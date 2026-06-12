---
title: "Help with a Java program"
date: 2006-12-05
forum: Programming Talk
---

### Post by the.dark.lord on 2006-12-05
I got stuck in a Java program (I just begining to program)... someb ody please please correct it.

Thanks in Advance.

import java.io.*;
public class sweetsurvey
{
	public static void main(String[] args) throws IOException
	{
		BufferedReader keyin = new BufferedReader(new InputStreamReader(System.in));
		String instr;
    	{
		char c,n,p,o;
		int ctr,cctr,nctr,pctr,octr;
		for(ctr=0;ctr<1000;ctr++)
		System.out.println("Enter yes or no as y or n only");
		
		System.out.println("Do you like cadbury's");
		c=keyin.readLine();
		
		System.out.println("Do you like nestle");
		n=keyin.readLine();
		
		System.out.println("Do you like parle");
		p=keyin.readLine();
		
		System.out.println("Do you like other choclates");
		o=keyin.readLine();

       
      
		if(c==y)
		{
			cctr=cctr++;
	    }
	    else
	    {
	     cctr=cctr; 	
	    }
	    if(n==y)
		{
			nctr=nctr++;
	    }
	    else
	    {
	     nctr=nctr; 	
	    }
	    if(p==y)
		{
			pctr=pctr++;
	    }
	    else
	    {
	     pctr=pctr; 	
	    }
	    if(o==y)
		{
			octr=octr++;
	    }
	    else
	    {
	     octr=octr; 	
	    }
	    
	    if(cctr>nctr && cctr>pctr && cctr>octr)
	    {
	     System.out.println("Cadbury's is the most popular");	
	    }
	    
	    if(nctr>cctr && nctr>pctr && nctr>octr)
	    {
	     System.out.println("Nestle is the most popular");	
	    }
	    
	    if(pctr>cctr && pctr>nctr && pctr>octr)
	    {
	     System.out.println("Parle is the most popular");	
	    }
	    
	    if(octr>nctr && octr>pctr && octr>cctr)
	    {
	     System.out.println("Others are is the most popular");	
	    }
	    
	 }
 }
}	 

Thanks again.

---

### Post by Arndt on 2006-12-05
> **the.dark.lord said:**
> I got stuck in a Java program (I just begining to program)... someb ody please please correct it.

Thanks in Advance.



What happens when you run it?

Besides, use "wrap code" (the # symbol in the tool bar) for displaying code, otherwise all lines will be left-justified, making the code harder to read.

---

### Post by paulr on 2006-12-05
There's two groups of problems with it. 

Code : 

your keyIn.readLine() method returns Strings not chars. You have to store them in strings - or extract the first character.

your equality will not work. For characters it is (ch == 'y') and for strings it is str.equals("y") (you cannot write str == "y")

(Note:There are reasons to write "y".equals(str) but that will wait for later)

Conceptually :

Your code will work - just (I think). But it isn't a flexible way of doing it. Suppose you add in 3 more choices ? You will have to add more nested ifs, and your "most popular" will rapidly become unreadable. You can solve this using Arrays.

The input is unhelpful. Rather than asking do you want A ? do you want B ? The program would be better offering a list and then asking you to select one.

---

### Post by the.dark.lord on 2006-12-05
Modified Program:
	String c,n,p,o;
		int ctr,cctr,nctr,pctr,octr;
		for(ctr=0;ctr<1000;ctr++)
		
		System.out.println("Enter yes or no as y or n only");
		char y;
		System.out.println("Do you like cadbury's");
		c=keyin.readLine();
		
		System.out.println("Do you like nestle");
		n=keyin.readLine();
		
		System.out.println("Do you like parle");
		p=keyin.readLine();
		
		System.out.println("Do you like other choclates");
		o=keyin.readLine();
		
		y=1;

       
      
		if(c=Str.equals("y"))
		{
			cctr=cctr++;
	    }
	    else
	    {
	     cctr=cctr; 	
	    }
	    if(n=Str.equals(y))
		{
			nctr=nctr++;
	    }
	    else
	    {
	     nctr=nctr; 	
	    }
	    if(p=Str.equals(y))
		{
			pctr=pctr++;
	    }
	    else
	    {
	     pctr=pctr; 	
	    }
	    if(o=Str.equals(y))
		{
			octr=octr++;
	    }
	    else
	    {
	     octr=octr; 	
	    }
	    
	    if(cctr>nctr && cctr>pctr && cctr>octr)
	    {
	     System.out.println("Cadbury's is the most popular");	
	    }
	    
	    if(nctr>cctr && nctr>pctr && nctr>octr)
	    {
	     System.out.println("Nestle is the most popular");	
	    }
	    
	    if(pctr>cctr && pctr>nctr && pctr>octr)
	    {
	     System.out.println("Parle is the most popular");	
	    }
	    
	    if(octr>nctr && octr>pctr && octr>cctr)
	    {
	     System.out.println("Others are is the most popular");	
	    }
	    
	 }
 }
}	 

Errors:
C:\WINDOWS\Desktop\sweetsurvey.java:31: incompatible types
found   : java.lang.String
required: boolean
                if(c=Str.equals("y"))
                   ^
C:\WINDOWS\Desktop\sweetsurvey.java:31: cannot resolve symbol
symbol  : variable Str  
location: class sweetsurvey
                if(c=Str.equals("y"))
                     ^
C:\WINDOWS\Desktop\sweetsurvey.java:39: incompatible types
found   : java.lang.String
required: boolean
            if(n=Str.equals(y))
               ^
C:\WINDOWS\Desktop\sweetsurvey.java:39: cannot resolve symbol
symbol  : variable Str  
location: class sweetsurvey
            if(n=Str.equals(y))
                 ^
C:\WINDOWS\Desktop\sweetsurvey.java:47: incompatible types
found   : java.lang.String
required: boolean
            if(p=Str.equals(y))
               ^
C:\WINDOWS\Desktop\sweetsurvey.java:47: cannot resolve symbol
symbol  : variable Str  
location: class sweetsurvey
            if(p=Str.equals(y))
                 ^
C:\WINDOWS\Desktop\sweetsurvey.java:55: incompatible types
found   : java.lang.String
required: boolean
            if(o=Str.equals(y))
               ^
C:\WINDOWS\Desktop\sweetsurvey.java:55: cannot resolve symbol
symbol  : variable Str  
location: class sweetsurvey
            if(o=Str.equals(y))
                 ^
8 errors

Process completed.

---

### Post by Ramses de Norre on 2006-12-05
```
c=Str.equals("y")
```
Should be
```
c.equals("y")
```
Where did you got Str? I don't see it being declared, and you have to call the equals method from the string you want to compare.
And make sure that you've always got boolean expressions in if clauses.

PS: for such yes no questions you might be interested in the method equalsIgnoreCase instead of equals, the usage is the same.

---

### Post by Blacktalon on 2006-12-05
Yep like Ramses de Norre said that's your problem you are trying to use the = over the proper way .equals(), reason being you are getting these incompatible error is that when you did ( if(c=str.equals(...)) ) basically it is yelling cause you are trying to assign c to a Str.   And the second type of error you where getting with the symbol not resolved seem to be that if you look you where trying to use Str, but what is Str.  I might be missing it but I don't see it instaniated anywhere if you are meaning for it to be a string it needs to be made on by doing String Str;

I hope this help ya understand better on what went wrong
~BT

---

### Post by raul_ on 2006-12-05
the '=' operator is an attribution. 

```

a = 3

```

puts the value 3 in a

What u want is a comparison, the operator '=='
```

a==3

```
will return a boolean, and u can use it with if. I think that in c++ this would compile, but wouldn't work at all :P


EDIT/NOTE: just because it compiles, it doesn't mean it works...That code isn't very "pretty" but then again, u're getting started

NOTE #2: PLEASE wrap your code. use the [ code] (without the space) in the beginning and [ /code] (without the space) in the end

---

### Post by DeadEyes on 2006-12-05
Two pieces of advice if I may
1. Variable name should be **meaningful**. "c,n,p,o" are not very helpful when reading the code. Single letters like "i" can be used for loop indexes but thats about it.
2. You should never write the same code twice. If you see that your repeating the same code or code that is similar, stop and rethink what your doing.

[Coding Standards]("http://java.sun.com/docs/codeconv/") is well worth reading.

Finally welcome to a world of great frustration but also great satisfaction.

---

### Post by Ramses de Norre on 2006-12-05
> **raul_ said:**
> What u want is a comparison, the operator '=='
```

a==3

```
will return a boolean, and u can use it with if. I think that in c++ this would compile, but wouldn't work at all :P

"==" wont work for strings, when you use "==" you are actually comparing the value of the string's pointer and not the contents of the string (which is an object in java).
So you must use the equals() method to compare strings.

---

### Post by raul_ on 2006-12-06
Or the compareTo method :)
```

 if (string1.compareTo(string2) < 0)

```

I didn't even see that he was comparing strings. My bad

---

### Post by Ramses de Norre on 2006-12-06
> **raul_ said:**
> Or the compareTo method :)
```

 if (string1.compareTo(string2) < 0)

```
I think that has to be "==" instead of "<", no?

> **Returns:**
the value 0 if the argument is a string lexicographically equal to this string; a value less than 0 if the argument is a string lexicographically greater than this string; and a value greater than 0 if the argument is a string lexicographically less than this string.

---

### Post by raul_ on 2006-12-06
indeed

---

### Post by the.dark.lord on 2006-12-06
I *finally* *phew* got my program working. YAY. A big thanks to all of you. :)

---

### Post by pmasiar on 2006-12-07
> **the.dark.lord said:**
> I got stuck in a Java program (I just begining to program).

For a beginner, python is much easier to learn than java. So if you just want to learn programming, try python first. No type terrorist causing syntax errors (duck typing works just fine). Libraries with intuitive API. And you will learn properly indent your code! :-) 

You can switch to java whan you know what you are doing, but I doubt you will ever want to :-) unless you you has to like me :-(

---

