---
title: "Call class methods written in python, called from c#?"
date: 2009-06-05
forum: Programming Talk
---

### Post by bramming on 2009-06-05
Hey :) I recently began to feel myself more experienced in programming (although im still at the novice level), so i decided to join a friends project. There is a problem though. He writes in c# visual express, from microsoft, while i do Python with IDLE. We're gonna have a graphical system, showing a grid with a lot of fields, with different background colors. He is supposed to do all the graphical stuff, but i have to calculate how the fields are supposed to be colored. 
- So basicly, he is supposed to construct a class i made, and then be able to call all its methods, and take the information my methods return, and then use it to display the colors.

But how can i call python code from c#? I have only been able to find one method on google. The method is: I convert my py files to an exe file using PyInstaller ([http://www.pyinstaller.org/](http://www.pyinstaller.org/)) then, he should open my exe, and run my methods by passing command line arguments.

But how does he pass me command line arguments? and can he even get the methods' return values?

By the way, english isnt my native language so hopefully spelling and grammatical errors are excused ;)

Thanks for taking the time to read this :) i have gotten a lot of good help from these forums, and i really appreciate it :)

---

### Post by Habbit on 2009-06-05
You can use [IronPython]("http://en.wikipedia.org/wiki/IronPython") so that both parts of the code use the same platform (the .NET Framework in this case). Code will be able to interoperate directly and you'll have a single executable, as opposed to the split solution of having a python-generated executable and the C# assembly.

---

### Post by bramming on 2009-06-05
> **Habbit said:**
> You can use [IronPython]("http://en.wikipedia.org/wiki/IronPython") so that both parts of the code use the same platform (the .NET Framework in this case). Code will be able to interoperate directly and you'll have a single executable, as opposed to the split solution of having a python-generated executable and the C# assembly.

thanks i'll look into it and post here if it worked or not :) Will take some time though since im at work :p

---

### Post by bramming on 2009-06-06
I just looked into it, and it seems like it doesn't do what i need :) as stated by the FAQ on their site: 

> IronPython does not support building DLLs for a C# style of linking and calling into Python code. You can define interfaces in C#, build those into a DLL, and then implement those interfaces in Python code as well as pass the python objects that implement the interfaces to C# code.

Too bad :( 
Me an my friend came up with a (bad) solution: He writes stuff to a file, i read it, and write stuff back. This way our code can communicate. However i think there is a better solution, i just cant figure out what :)

---

### Post by phrostbyte on 2009-06-06
Maybe use this
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

---

### Post by nvteighen on 2009-06-06
> **bramming said:**
> 
Me an my friend came up with a (bad) solution: He writes stuff to a file, i read it, and write stuff back. This way our code can communicate. However i think there is a better solution, i just cant figure out what :)

Why is that a bad solution? It's a very UNIX way to do stuff, using files to make different programs communicate each other.

---

### Post by bramming on 2009-06-06
Thanks Phrostbyte, i'll look into it :)

> Why is that a bad solution? It's a very UNIX way to do stuff, using files to make different programs communicate each other. 

At least i think so, because im afraid that the same file will be read and wrote in at the same time, causing errors? The program runs on windows, which AFAIK cant do that?

---

### Post by leblancmeneses on 2009-06-06
Expose your python code as a service.

use a bus.
which allows you to define an interface:
CORBA, WCF,  The nice thing is most often tools with the bus provide code generation.

SOAP is commonly used for data exchanges like these


I'm actually in the process of building my own custom bus.
That provides code generation capabilities.  It is based on:
[http://npeg.codeplex.com](http://npeg.codeplex.com)  I would need a python guy to help build the python parser. (I'm a c/c++/c# guy)



you can build your own by sitting down with your friend and discussing exactly what the inputs are and expected results are.  
Example:
public interface IGridService
{
    void Delete(Customer m);
    void Insert(Customer m);
    void Update(Customer m);
    Customer Select(Int32 id);
     List<Customer> SelectManyBy(String wildcardonname, Int32 offset, Int32 limit);
 }
in this example you have:
datacontracts:  Customer
operation contracts: Delete, Insert, Update, Select, SelectManyBy

This will be the contract aka interface both adhere to.


In c# you must implement this interface:
so that when he does this:
IGridService s = new PhythonGridService();
s.Insert(new Customer(){ FirstName="firstname" ....} );

the PhythonGridService actually has TcpClient code that converts the customer object into xml and sends it across the wire to your tcp server.

---

### Post by bramming on 2009-06-06
> **leblancmeneses said:**
> Expose your python code as a service.

use a bus.
which allows you to define an interface:
CORBA, WCF,  The nice thing is most often tools with the bus provide code generation.

SOAP is commonly used for data exchanges like these


I'm actually in the process of building my own custom bus.
That provides code generation capabilities.  It is based on:
[http://npeg.codeplex.com](http://npeg.codeplex.com)  I would need a python guy to help build the python parser. (I'm a c/c++/c# guy)



you can build your own by sitting down with your friend and discussing exactly what the inputs are and expected results are.  
Example:
public interface IGridService
{
    void Delete(Customer m);
    void Insert(Customer m);
    void Update(Customer m);
    Customer Select(Int32 id);
     List<Customer> SelectManyBy(String wildcardonname, Int32 offset, Int32 limit);
 }
in this example you have:
datacontracts:  Customer
operation contracts: Delete, Insert, Update, Select, SelectManyBy

This will be the contract aka interface both adhere to.


In c# you must implement this interface:
so that when he does this:
IGridService s = new PhythonGridService();
s.Insert(new Customer(){ FirstName="firstname" ....} );

the PhythonGridService actually has TcpClient code that converts the customer object into xml and sends it across the wire to your tcp server.

nice :D

Huge thanks to all that helped me, finally it works :)

@leblancmeneses i noticed u said u needed a pythonguy to help you. Even though i would like to try, i dont think i will be of any use since im still doing very basic stuff in python :)

---

### Post by Can+~ on 2009-06-06
> **bramming said:**
> At least i think so, because im afraid that the same file will be read and wrote in at the same time, causing errors? The program runs on windows, which AFAIK cant do that?

That's called Concurrency. That idea leaded to the creation of Databases to handle simultaneously accessed data, safely, optimized, etc. ([ACID]("http://en.wikipedia.org/wiki/Concurrency_control#Transaction_ACID_rules"))

Maybe your problem calls for a database? MySQL, Postgres, Oracle, MSSQL? Even SQLite could do.

---

