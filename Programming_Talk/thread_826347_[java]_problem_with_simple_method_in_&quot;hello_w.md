---
title: "[java] problem with simple method in &quot;hello world&quot;ish program"
date: 2008-06-11
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-06-11
Hey All

I'm just starting to learn java, and I'm having some trouble with this code in a "hello world"ish program:
```

package newPackage;

public abstract class NewClass 
{

	
	public static void main(String[] args) 
	{
		
		int calculateSum(int first, int second)
		{
			return first + second;
		}
		calcluateSum(5,3);
	}
	

}


```

Can anyone tell me where I'm going wrong?
Thanks.

---

### Post by tamoneya on 2008-06-11
can you tell us what the error is.  How is it responding? Are you having compiler errors? Are you getting no output?

---

### Post by bruce89 on 2008-06-11
[LIST]
[*]You can't define a method inside another method. Here [FONT="Monospace"]calculateSum[/FONT] is defined inside [FONT="Monospace"]main[/FONT].
[*]Why is this class marked as abstract?
[*][FONT="Monospace"]calculateSum[/FONT] has to be static as NewClass hasn't been instantiated.
[*]You're not printing the result.
[/LIST]

Here's my example:

```

public class NewClass 
{
	public static int calculateSum(int first, int second)
	{
		return first + second;
	}

	public static void main(String[] args) 
	{
		System.out.println(calculateSum(5, 3));
	}
}

```

---

### Post by Yuki_Nagato on 2008-06-11
Is it possible to run your starting "public static void main" inside of an abstract class?

Yes, previous poster is correct in saying that methods cannot be declared inside of one another.  Method "calculate" also needs a public or private label.

---

### Post by the_real_fourthdimension on 2008-06-11
Thanks for the responsese.
...You'd think I've been around these forums long enough to remember to include compiler errors! :p  
```

NewClass.java:10: ';' expected
		int calculateSum(int first, int second)
		                ^
NewClass.java:10: <identifier> expected
		int calculateSum(int first, int second)
		                           ^
NewClass.java:10: not a statement
		int calculateSum(int first, int second)
		                                ^
NewClass.java:10: ';' expected
		int calculateSum(int first, int second)
		                                      ^
4 errors
                                     ^
4 errors

```

So java is not like C++ where you can have other functions/methods within the main function/method?
BTW, I fixed the typo.
As for why I labeled it abstract, I guess it's because I'm still getting used to eclipse/java and wanted to allow myself room to create subclasses if I wanted to.  I changed it to final (and left it blank), but it didn't change the errors.
Thanks for the help.

---

### Post by bruce89 on 2008-06-11
> **the_real_fourthdimension said:**
> 
So java is not like C++ where you can have other functions/methods within the main function/method?
BTW, I fixed the typo.
As for why I labeled it abstract, I guess it's because I'm still getting used to eclipse and wanted to allow myself room to create subclasses if I wanted to.
Thanks for the help.

Abstract just means that the class cannot be instantiated. You'd not use it to "facilitate subclasses". For instance:

```

public class SuperClass
{
}

public class SubClass extends SuperClass
{
}

```

Nested methods can't been done in Java. Nested classes, but not methods.

Java's quite different to C++, it's much nicer.

---

### Post by slimjim8094 on 2008-06-11
```
package newPackage; //namespace newPackage {

public class NewClass 
{

	
	public static void main(String[] args) //equivalent to void main(int *argc, char[] *argv)
	{
		System.out.println(calcluateSum(5,3)); //cout << calculateSum(5,3)
	}

	public static int calculateSum(int first, int second)
	{
		return first + second;
	}
	

}
```

There's no such thing as a classless Java program. There is a one to one correspondence between .java files and classes (well, there are inner classes but that's different)

So you correctly created a class... The main method is static, so you don't need an object to run it (if you were running this from another class, it'd be NewClass.main(new String[]{}) )

However - static methods (like main) can only call other static methods. This is very similar to C++.

No, you can't embed a method (not a function, this is Java) inside another method.

Oh, and yes - 'abstract' is not the same as 'virtual'. You can extend ANY class, but it defines the terms (protected, private, and public work the same way). Hell, you could extend the built-in String class if you wanted to.
Abstract means that a class can not be instantiated. It's a class that contains a (in C++ language) a pure virtual function. Similarly, it can't be instantiated... children of that class MUST define that method or be abstract themselves.

And all classes are polymorphic by default. So you don't need to remember to make at least one function virtual.

Hope this helps, and hope this cleared some things up. Java's a great language

---

### Post by bruce89 on 2008-06-11
There's no need to complicate things with packages for single file projects such as this.

---

### Post by descendency on 2008-06-11
> **the_real_fourthdimension said:**
> So java is not like C++ where you can have other functions/methods within the main function/method?

C++ can have functions inside of one another? news to me.

If you mean you can call functions inside of the main function, then yes, you can do that in Java too.

In C++:

[PHP]
#include <iostream>

using namespace std;

void CalcSum(int num1, int num2)
{
  return num1 + num2;
}

int main(void)
{
  cout << CalcSum(5,3) << endl;
  return 0;
}
[/PHP] 

Notice, the definition of the function isn't located in the main function. Java only differs (at least at this point) in the fact that you have to have a class encompass the methods/functions and you use a few other keywords. 

I'm not going to bother typing code as slimjim8094 has provided an excellent example. (although, I would ignore packaging at the moment, as it isn't terribly important for smaller projects/learning the language).

---

### Post by the_real_fourthdimension on 2008-06-11
> **slimjim8094 said:**
> ```
package newPackage; //namespace newPackage {

public class NewClass 
{

	
	public static void main(String[] args) //equivalent to void main(int *argc, char[] *argv)
	{
		System.out.println(calcluateSum(5,3)); //cout << calculateSum(5,3)
	}

	public static int calculateSum(int first, int second)
	{
		return first + second;
	}
	

}
```

There's no such thing as a classless Java program. There is a one to one correspondence between .java files and classes (well, there are inner classes but that's different)

So you correctly created a class... The main method is static, so you don't need an object to run it (if you were running this from another class, it'd be NewClass.main(new String[]{}) )

However - static methods (like main) can only call other static methods. This is very similar to C++.

No, you can't embed a method (not a function, this is Java) inside another method.

Oh, and yes - 'abstract' is not the same as 'virtual'. You can extend ANY class, but it defines the terms (protected, private, and public work the same way). Hell, you could extend the built-in String class if you wanted to.
Abstract means that a class can not be instantiated. It's a class that contains a (in C++ language) a pure virtual function. Similarly, it can't be instantiated... children of that class MUST define that method or be abstract themselves.

And all classes are polymorphic by default. So you don't need to remember to make at least one function virtual.

Hope this helps, and hope this cleared some things up. Java's a great language

Thanks a lot!  That really helps.  Yeah, I didn't have a classless program, just a class that wasn't declared as abstract or final.  I see what I was doing wrong now (besides the typo)...  I didn't call the method static.

As a matter of convention, is it preferable to write the method body before you execute or call the method (forgive my lack of proper terminology) as is required in C++, or is it better to write it after the main method/function in which it is used?

Thanks for all your help!

---

### Post by the_real_fourthdimension on 2008-06-11
> **descendency said:**
> C++ can have functions inside of one another? news to me.

If you mean you can call functions inside of the main function, then yes, you can do that in Java too.

Yes, that's what I meant.  Thanks for clarifying.:KS

---

### Post by jamesstansell on 2008-06-12
> **the_real_fourthdimension said:**
> 
As a matter of convention, is it preferable to write the method body before you execute or call the method (forgive my lack of proper terminology) as is required in C++, or is it better to write it after the main method/function in which it is used?

Most of the code I've looked at has tended to have the main() method at the end of the class.  But apparently not for any particular reason.  For the other methods, the ones that are called first would generally appear earlier in the class.

Tools like Eclipse and NetBeans make it relatively easy to navigate among your methods, so their order becomes less important than other things.

You may find the coding conventions documentation to be of interest:

[http://java.sun.com/docs/codeconv/](http://java.sun.com/docs/codeconv/)

---

### Post by NormR2 on 2008-06-12
>  There is a one to one correspondence between .java files and classes   You can have more than one class defined in a .java file by having them not be public.

>  you could extend the built-in String class if you wanted to.  You can NOT extend final classes!

---

