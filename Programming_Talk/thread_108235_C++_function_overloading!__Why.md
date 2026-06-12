---
title: "C++ function overloading!  Why?"
date: 2005-12-25
forum: Programming Talk
---

### Post by nami on 2005-12-25
Hi

I'm a Linux noobi and a C++ noobi too!!!

I'm currently learning about "function overloading".  The reason why I'm posting here is because I don't understand the purpose of "function overloading".  The book I am learning from has provided the following example of "function overloading"

[C++ Code using function overloading]
[PHP]#include <iomanip>
#include <iostream>
using namespace std;

void FtoC(int temp);
void FtoC(float temp);
void FtoC(double temp);

int main()
{
	int itemp, level;
	float ftemp;
	double dtemp;
	
	cout << "CONVERTING FAHRENHEIT TO CELSIUS\n";
	cout << "Select required level of precision\n";
	cout << "Integer (1) - Float (2) - Double (3)\n";
	cin >> level;
	cout << "Enter Fahrenheit temperature: ";
	
	switch (level)
	{
		case 1 : cin >> itemp; FtoC(itemp); break;
		case 2 : cin >> ftemp; FtoC(ftemp); break;
		case 3 : cin >> dtemp; FtoC(dtemp); break;
		default : cout << "Invalid selection\n";
	}

	return 0;
}

void FtoC(int itemp)
{
	int temp = (itemp - 32) * 5 / 9;
	cout << "Integer precision: ";
	cout << itemp << "F is " << temp << "C\n";
}

void FtoC(float ftemp)
{
	float temp = (ftemp - 32) * 5. / 9.;
	cout << setprecision(8) << "Float precision: ";
	cout << ftemp << "F is " << temp << "C\n";
}

void FtoC(double dtemp)
{
	double temp = (dtemp - 32) * 5. / 9.;
	cout << setprecision(12) << "Double precision: ";
	cout << dtemp << "F is " << temp << "C\n";
}[/PHP]
[/C++ Code]

The code below does exactly the same thing as the code above, but is not using "function overloading"

[C++ Code without function overloading]
[PHP]#include <iomanip>
#include <iostream>
using namespace std;

void FtoCint(int temp);
void FtoCfloat(float temp);
void FtoCdouble(double temp);

int main()
{
	int itemp, level;
	float ftemp;
	double dtemp;
	
	cout << "CONVERTING FAHRENHEIT TO CELSIUS\n";
	cout << "Select required level of precision\n";
	cout << "Integer (1) - Float (2) - Double (3)\n";
	cin >> level;
	cout << "Enter Fahrenheit temperature: ";
	
	switch (level)
	{
		case 1 : cin >> itemp; FtoCint(itemp); break;
		case 2 : cin >> ftemp; FtoCfloat(ftemp); break;
		case 3 : cin >> dtemp; FtoCdouble(dtemp); break;
		default : cout << "Invalid selection\n";
	}

	return 0;
}

void FtoCint(int itemp)
{
	int temp = (itemp - 32) * 5 / 9;
	cout << "Integer precision: ";
	cout << itemp << "F is " << temp << "C\n";
}

void FtoCfloat(float ftemp)
{
	float temp = (ftemp - 32) * 5. / 9.;
	cout << setprecision(8) << "Float precision: ";
	cout << ftemp << "F is " << temp << "C\n";
}

void FtoCdouble(double dtemp)
{
	double temp = (dtemp - 32) * 5. / 9.;
	cout << setprecision(12) << "Double precision: ";
	cout << dtemp << "F is " << temp << "C\n";
}[/PHP]
[/C++ Code]

So, what's the purpose of "function overloading"?

Appreciate any answers.

nami.

---

### Post by Mike Buksas on 2005-12-25
Hi nami,

Function overloading is basically syntactic sugar. It tastes kinda good, as long as you don't over do it! As you've discovered, you can't do anything with it that you cannot do with non-overloaded functions, as in your example. 

One of it's goals it to reduce the memory load on programmers. The three functions in your example all do the same thing. By using an overloaded function, the programmer does not need to remember three versions of the function. Instead, you remember one and let the compiler figure out the tedius detail of which one to call, as determined by the type of the argument.  This also lets the programmer work at a higher level of abstraction. You can worry more about the big picture, and less about the details.

That said, function overloading can be bad for you if not used properly. For example, your FtoC functions *should* all do the same thing. What if one of them doesn't. It would be bizarre indeed if you got very different behavior from two functions with the same name, but function overloading lets you do exactly that. Also too much function overloading can make understanding code harder. The rules that the C++ compiler must follow to figure out exactly which overloaded version of a function to call are quite complicated in some situations. It can be hard for a person reading the code to figure out which function get's called.

In short, it's a way to make your code cleaner, and easier to understand, but can cause more problems than it solves if overused or misused.

Hope this helps,
Mike

---

### Post by nami on 2005-12-25
Thanks Mike Buksas,

That cleared things up nicely!

Just 1 question.  You said that the compiler decides which function to use.  Does this mean that function overloading will use more processing power and memory than the an identical program with no function overloading?

But thanks for the detailed explaination.  I had to post the question because I hate moving on when I don't understand something! :)

nami

---

### Post by Mike Buksas on 2005-12-25
The compiler has to do a little more work when compiling the code, but the resulting code will be just as efficient as code without function overloading.

It might help to have a little background into what the compiler does with overloaded functions. Internally, it combines the name of the function with the types of the arguments (e.g. double, float and int in your example) to create a unique name for each function. Once the compiler determines which version of a function is being called, it binds the function call to one of the unique internal versions of the function when it creates your program. Hence, it doesn't need to figure out which function to call when the program is being run.

The process of making unique names for functions is called "name mangling" because the resulting names are not designed to be read by people. Check the man page for command 'nm' if you want to get a look at what the internal names are like.

Glad I could help,
Mike

---

### Post by LordHunter317 on 2005-12-25
[QUOTE=Mike Buksas]As you've discovered, you can't do anything with it that you cannot do with non-overloaded functions, as in your example. [/quote]That's not quite true, in general terms.  Templates are a fancier form of function overloading (among other things) and they allow you to do something non-overloaded functions do not: use the same source regardless of type.

> Also too much function overloading can make understanding code harder.I don't see how that is.

>  The rules that the C++ compiler must follow to figure out exactly which overloaded version of a function to call are quite complicated in some situations.Not especially so.  At any rate, you have to be aware of the rules all the time *anyway* so this isn't a valid reason to avoid them.

---

### Post by Mike Buksas on 2005-12-25
[QUOTE=LordHunter317]That's not quite true, in general terms.  Templates are a fancier form of function overloading (among other things) and they allow you to do something non-overloaded functions do not: use the same source regardless of type.[/QUOTE]

I think that's confusing the issue. Function templates and overloading are two different, but complimentary, things. The original question did not involve templates, so I didn't go there.

[QUOTE=LordHunter317]I don't see how that is.[/QUOTE]

I must have seen more poorly written C++ code than you have. Using an overloaded function instead of unique names removes information that could help somebody understand the code. It can also obscure significant differences in the behavior of functions that operate on different types. If somebody reads the code, they're going to think that since the functions have the same name, they're going to do the same thing, even if they don't.

That said, judicious use of overloading can reduce the verbosity of function names and aid in understanding the code. It's all in how you use them.

[QUOTE=LordHunter317]Not especially so.  At any rate, you have to be aware of the rules all the time *anyway* so this isn't a valid reason to avoid them.[/QUOTE]

In a few situations, I think avoiding overloading is warranted, but not generally.  For example, the "overload resolution happens before protection resolution" rule is a killer. This is where one version of an overloaded function is a private class member and another is public. Someone attempting to use the public version can get a compiler error if the private version is a better match according to the rules of overload resoltion. Since a user may not even have access to the private parts of the class (e.g. the source code) this can be a real show stopper. In this case there is nothing to be gained by the overloading, and a lot of potential confusion to be created.

So yea, it can be useful, but overdoing it is a recipie for heartache.

Mike

---

### Post by LordHunter317 on 2005-12-25
[QUOTE=Mike Buksas]I think that's confusing the issue. Function templates and overloading are two different, but complimentary, things. The original question did not involve templates, so I didn't go there.[/quote]Which is why I noted it in general terms.

> I must have seen more poorly written C++ code than you have. Using an overloaded function instead of unique names removes information that could help somebody understand the code.If the only difference in user semantics is type, then it does not.  If you provide an overloaded functions with different semantics, that's a design error.  That's not a reason to lambast a language feature, seeing as it doesn't especially encourage it in anyway.

>  It can also obscure significant differences in the behavior of functions that operate on different types.So can implict-type conversion, and templates.  Should I just go back to writing C now?  You can't use that justification without starting on a slippery slope: the whole point of abstractions is to obscure things.  

It's worth saying obviously, that one shouldn't overload a function unless it will meet the same user-visible semantics.  That ought to go without saying anyway, and applies to many other places in C++: templates, inheritance, etc.  

It's not logical to reason that because people can provide different semantics, that overloading shouldn't be used.  And that's what you're suggesting.  All you can conclude from that it's the programmer's onus to enforce the semantics, not the compiler's.

> In a few situations, I think avoiding overloading is warranted, but not generally.They're plently warrented in all sorts of situations.  C++ classes wouldn't be nearly as expressive without operator overloading.  You couldn't emulated C# style properties without function overloads either, which  is far superior to me than setFoo(), getFoo().

> For example, the "overload resolution happens before protection resolution" rule is a killer. This is where one version of an overloaded function is a private class member and another is public. Someone attempting to use the public version can get a compiler error if the private version is a better match according to the rules of overload resoltion.This is done on purpose, to protect.  Someone who designs a class where the end-user can befall this has made a design error, plain and simple.  This is still not an argument against even judicious use of overloads in external interfaces.
It is an argument against overloads in implementations, since the class implementer has to be wary of this.

> In this case there is nothing to be gained by the overloading, and a lot of potential confusion to be created.Yes, but you've created a false dilemma.  The issue here isn't overloads created a problem, it's the class is simply designed wrong.

---

### Post by Mike Buksas on 2005-12-26
This discussion is getting pretty far away from the original purpose of the thread, which was a low level discussion on the uses and pitfalls of overloading to a new C++ developer.

Also, I think you may have misread one of my comments. I agree that overloading is acceptable in the majority of cases. I was pointing some particular cases in which it leads to confusion. The cases in question are indeed design flaws, (differing semantics and the protection resolution, specifically) but they are design flaws enabled by operator overloading. Hence, I maintain my position that overloading occasionally does more harm than good.

Since this is largely a question of style, I don't think we're going to make any progress debating it. Perhaps we could agree, for the benefit of the original poster, the overloading is a useful feature, but should be used with some caution?

Mike

---

### Post by LordHunter317 on 2005-12-26
[QUOTE=Mike Buksas]I was pointing some particular cases in which it leads to confusion.[/quote]But it's not user confusion.  You only have to be aware of it when designing classes, and it's far eaiser in those cases to say, "Don't overload in different access scopes" then say, "Overloading causes confusion and should be potentially avoided."  

> The cases in question are indeed design flaws, (differing semantics and the protection resolution, specifically) but they are design flaws enabled by operator overloading. Hence, I maintain my position that overloading occasionally does more harm than good.It's invalid to draw anything from that.  From that reasoning, nearly every language feature occasionally "does more harm than good."    That doesn't mean they necessarily should be avoided, or even used judiciously.  That's only true iff you always have to deal with the problems.  You don't with function overloading.

> the overloading is a useful feature, but should be used with some caution?Seeing the caution only has to be applied in one small case, no.

---

### Post by tbrownaw on 2005-12-27
[QUOTE=nami]I'm currently learning about "function overloading".  The reason why I'm posting here is because I don't understand the purpose of "function overloading".  The book I am learning from has provided the following example of "function overloading"

[snip]

So, what's the purpose of "function overloading"?[/QUOTE]
The purpose is that functions can be named after what they do, without worrying about what types of arguments they take. This makes them easier to remember, and also can make it easier to change the types of your variables.

A data type has a set of functions that you can call on it, possibly including member functions (if it's a class). If you have a different data type with the same functions available, with the same names for those functions, then you can switch which data type you're using for your variables very easily.

Say you have this code (not quite the same as your example):

```
#include <iomanip>
#include <iostream>
using namespace std;

void FtoC(int temp);
void FtoC(float temp);
void FtoC(double temp);

int main()
{
    int temp;
    
    cout << "CONVERTING FAHRENHEIT TO CELSIUS\n";
    cout << "Enter Fahrenheit temperature: ";
    
    cin >> temp;
    FtoC(temp);

    return 0;
} 
```

Now say someone decides that an int isn't precise enough... because FtoC and the >> operator are both overloaded, changing to a more precise data type is as simple as changing the "int temp;" line to "float temp;". (This is one problem with hungarian notation -- changing data types becomes much more annoying if you want to keep the names in sync with the actual types.)

Tim

---

