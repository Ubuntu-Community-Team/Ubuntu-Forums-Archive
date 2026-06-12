---
title: "[SOLVED] XOR like function in C/C++"
date: 2008-02-14
forum: Programming Talk
---

### Post by WitchCraft on 2008-02-14
Question:

if i want to xor 2 values in C/C++, i can do this like this using:
( (p || q) && !(p && q) )
which is equivalent to p xor q.

How do i implement an xor function, that looks like p xor q?
Example:
```

int main()
{
     bool a,b;
     a=true; b=true;
     if (a xor b) 
          printf("true\n");
     else
          printf("false\n");
     return EXIT_SUCCESS ;
}

```

I can of course do a function like:
```

bool xor(bool p, bool q)
{
     return ( (p || q) && !(p && q) ) 
}

```

But then the function call looks like:
if( xor(a,b) )

and i want: if ( a xor b )

Can I do that at all in C/C++?

---

### Post by shaggy999 on 2008-02-14
I don't think you can do that in C++ itself. C++ does have operator overloading, but that's only for particular operators. You can't create any operator of your choosing. My suggestion would be to create some preprocessor syntax that gets parsed before getting handed off to the compiler. That way you can have your simple function, but it will convert to C++ code at compile time.

---

### Post by slavik on 2008-02-14
^ is the xor operator in C/C++

---

### Post by shaggy999 on 2008-02-14
Oh damn, it hurts. Hurts to the CORE. I was wrong. Damn.

---

### Post by WitchCraft on 2008-02-14
> **slavik said:**
> ^ is the xor operator in C/C++

Oh, i thought ^ is only bitwise. Obviously that also works non bitwise; funny ;-)

But it would still be interesting to know how to do a function that looks like:
argument1 OPERAND argument2

---

### Post by slavik on 2008-02-14
> **WitchCraft said:**
> Oh, i thought ^ is only bitwise. Obviously that also works non bitwise; funny ;-)

But it would still be interesting to know how to do a function that looks like:
argument1 OPERAND argument2
while in C you won't be able to do that (unless you change the language/compiler) in C++ you can overload the ^ operator to work on other things.

(un)fortunately you cannot define your own operators in C/C++ (whether this is good or not can be debated till infinity).

---

### Post by Zwack on 2008-02-14
Ummm, Depends on the types you are using...

in C a bitwise xor is just ^

thus a ^ b is a xor b

unfortunately you can't overload ^ with

bool operator^ (bool p, bool q)

As at least one of the data types needs to be user defined...

Z.

---

### Post by slavik on 2008-02-14
> **Zwack said:**
> Ummm, Depends on the types you are using...

in C a bitwise xor is just ^

thus a ^ b is a xor b

unfortunately you can't overload ^ with

bool operator^ (bool p, bool q)

As at least one of the data types needs to be user defined...

Z.
I am pretty sure operator^(bool,bool) is defined already :)

---

### Post by Zwack on 2008-02-14
I'd be surprised if  bool ^ bool isn't defined...  But my point is more that you can't really redefine it for built in types.  So if you want a function that sits in the middle like a binary operator then you have to be redefining a current operator for a user defined type.

If you decided you wanted a function to operate on two built-in types and you wanted it to look like a binary operator you can't... But then how would the compiler know what precedence to give it anyway?

a ^ b & c - d has a set precedence, it will always act in the same way...
but supposing I defined a new operator  "

what order would a ^ b " c - d be done in?  What should the expected result be?  While quote(a ^ b, c -d) is something that does have a recognised precedence.

Equally being able to overload operators for built-in types would be dangerous...  After all if you've redefined ^ to being something else then later you use it because you need to xor something how are you ever going to track down the cause of your odd results?

Z.

---

### Post by WitchCraft on 2008-02-14
> **Zwack said:**
> 
a ^ b & c - d has a set precedence, it will always act in the same way...
but supposing I defined a new operator  "


That would be simple if you could set the precedence for the operator.
But i see, that's something for (C++)++.

---

### Post by Zwack on 2008-02-14
Actually I found [This pdf]("http://www.informatik.uni-ulm.de/rs/mitarbeiter/ch/publ/Heinlein:Gi2:Gi:2004:459.pdf") on the subject while I was looking for more information earlier...

A suggestion for an extension to C++ that would allow you to define infix operators and set their precedence...

Z.

---

### Post by slavik on 2008-02-14
Honestly, I see this type of thing as something Larry Wall would put into Perl ...

---

### Post by WitchCraft on 2008-07-05
> **slavik said:**
> Honestly, I see this type of thing as something Larry Wall would put into Perl ...

:lolflag:

Nooooo, Python.

It's actually fun, you can write your own Python scrips that get executed before compilation, so you can add functions to C++ that are not supported by C++/preprocessor. *bricolage*

---

### Post by quino25 on 2012-04-12
Sorry about my bad english.

Hi I search in google for the XOR for boolean types, because i making one code and i need one, and i dosn't want use A·!B | !A·B and remember that is not correct use ^ for do an XOR is not correct, because it is for bitwise. I found the answer in other link, so pretty answer. I came again here to add the correct solution:

------

Boolean variables occupy 1 byte. 00000000 is false and other value is true.
If the implementation of the C/C++ dosn't use for true value alwais 00000001, use of ^ for XOR can cause unwanted or unpredictable results.

bool a = (0010) (true)
bool b = (0011) (true)
a^b = (0001) (true)

------

So what i must use?

Exist one operator in C/C++ that have the same true table that have XOR, is !=, to maque ABool XOR BBool you must do ABool != BBool.

---

### Post by Barrucadu on 2012-04-12
You've dredged up a four-year old thread&#8230;

You can do it with bitwise xor if you first normalise the values to 0 or 1, so you can do, eg: "(!!a) ^ (!!b)"

If a (b) is nonzero, it will be set to 1, if it is zero it will remain 0.

---

### Post by overdrank on 2012-04-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

