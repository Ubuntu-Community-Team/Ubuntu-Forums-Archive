---
title: "exception handling in multiple languages c++, java, c#"
date: 2009-08-06
forum: Programming Talk
---

### Post by leblancmeneses on 2009-08-06
I am working with another developer on some code and received an email that concerns exception handling in multiple languages.

   >  

  > But I don't think we should introduce another exception for this, as 
  > it will make the signatures more bloated than they already are (in the 
  > Java version there are already two kinds of exceptions that must be 
  [FONT=&quot]> propagated up, parsing exceptions and IO exceptions), [/FONT]

his concern is across:

    public abstract boolean isMatch() throws IOException, ParsingFatalTerminalException;

    protected boolean Predicate() 
    throws IOException, ParsingFatalTerminalException 

and many more methods that look similar in both java and c++ as signatures define exceptions handled in those languages.



here is my reply:



> 
    
  To do's with exception:
  raise specific exceptions to what the problem is.
  DivideByZeroException .. there are reasons why the base class ArithmeticException  is not thrown.
  This has to do with making use of catch blocks and including more specific information about the exception.
  A user should never parse an exception string to access exception data. (big no no)   By using the correct type you have easy access to extra information you need from the exception.
   
   
  However I do believe that our exceptions should inherit from the same base type: ModelException This way if the caller can expect base class ModelException and apply a catch block that will catch all child classes.
   
  try
  {
     Boolean test = parser.IsMatch();
  }
  catch(ModelException e) {
    //will catch parent and all childs that inherited form ModelException 

 } 

//any others will be unhandled
   


   
  Now if we expected other exceptions from occurring in c# and wanted to provide the caller a type to expect then the following could be done:


 new SpecificExceptionName("exception message", innerException);
  But this requires the caller to unravel the exception tree to access the cause of the real problem.
   
   
   
  Also in the c++ version at least (i haven't looked at the java because I'm not really a java programmer) I notice you add signatures of what exceptions are thrown... 
  I believe these can be reduced as public api should contain this information not non public methods which should clean up signatures.
   
  




so what are your thoughts about my reply?
Because by looking at our current class it looks redundant with signatures including exception information.

---

### Post by Reiger on 2009-08-06
In Java you would typically define your own exception containing all fields and necessary methods to generate UI error messages and logs etc.: you can pretty much do in the object what you want.
```

public class InternalException extends Exception {
 public InternalException(/*params*/) {
   super(/*params*);
   /* init object*/
 }

 public String getUIMessage() {
   /* should probably be an actual localized message ;) */
   return "Ouch, this hurt code flow.";
 } 

 public void logToFile(/*params*/) { // do stuff
 }

 public static void showErrorMessage(InternalException e) {
  String msg = e.getUIMessage();
  // do stuff with it
 }
}

```

However you should in general try to avoid raising an exception for every possible thing you can raise one for. Say you had an object that must be read from serialized data: if that fails you might as well return null instead of throwing an exception. It fits the type system and a simple error check on calling code avoids overhead (which can be significant), plus it is very clear what a null object (does not) mean(s).

I Am Not A C Plus Plus Coder but from what I read: in C++ Exceptions are a Sure Path to Memory Leak.

---

### Post by JohnnySage50307 on 2009-08-06
> **Reiger said:**
> I Am Not A C Plus Plus Coder but from what I read: in C++ Exceptions are a Sure Path to Memory Leak.
 
It is true, poorly coded exceptions in C++ tend to cause severe memory leaks.  Secondly, as a general rule of thumb, only code an exception for things you expect the user to recover from.  Typically exception coding is for the benefit of other ppl who will use the libraries you are developing, not for someone designing an application.  If you code for absolutely EVERYTHING, you'll never finish the product and it'll be more bloated than ever.

---

### Post by Can+~ on 2009-08-06
> **JohnnySage50307 said:**
> It is true, poorly coded exceptions in C++ tend to cause severe memory leaks.

Yup, weird to have Exception Handling without Garbage Collector, I made a simple snippet that can cause it:

[PHP]#include <iostream>

int main(int argc, char **argv)
{
	char *x;
		
	try
	{
		// Example allocation
		x = new char[100]; 
		throw 10;
		
		delete[] x;
	}catch(int y)
	{
		std::cout << "Catched:" << y << std::endl;
	}
	
	return 0;
}[/PHP]

Running it with valgrind

```
==8783== 
Catched:10
==8783== 
==8783== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==8783== malloc/free: in use at exit: 100 bytes in 1 blocks.
==8783== malloc/free: 2 allocs, 1 frees, 184 bytes allocated.
==8783== For counts of detected errors, rerun with: -v
==8783== searching for pointers to 1 not-freed blocks.
==8783== checked 93,100 bytes.
==8783== 
==8783== 100 bytes in 1 blocks are definitely lost in loss record 1 of 1
==8783==    at 0x402630E: operator new[](unsigned int) (vg_replace_malloc.c:268)
==8783==    by 0x804895E: main (in /home/canxp/Desktop/leaktest)
==8783== 
==8783== LEAK SUMMARY:
==8783==    definitely lost: 100 bytes in 1 blocks.
==8783==      possibly lost: 0 bytes in 0 blocks.
==8783==    still reachable: 0 bytes in 0 blocks.
==8783==         suppressed: 0 bytes in 0 blocks.
```

---

### Post by leblancmeneses on 2009-08-07
reason why std::auto_ptr is important.


so back to exceptions in java/c++ 

> 
Also in the c++ version at least  I notice you add signatures of what exceptions are thrown... 

    public abstract boolean isMatch() throws IOException, ParsingFatalTerminalException;

    protected boolean Predicate() 
    throws IOException, ParsingFatalTerminalException 


I believe these can be reduced as public api should contain this information not non public methods which should clean up signatures.



this means 
1) leave isMatch as is.
2) remove/clean syntax of throw in protected/private signatures.

do you all agree?

---

### Post by slavik on 2009-08-07
you also want to throw fatal exceptions if it causes your app to die (most common example I see: java.lang.OutOfMemory, followed by various forms of not being able to get to the DB).

---

