---
title: "kb.next() instead of kb.nextLine how do I catch each individual input?"
date: 2009-09-18
forum: Programming Talk
---

### Post by s3a on 2009-09-18
I did not learn try and catch statements yet so please don't try to introduce me to new things I haven't learnt in class (I will do that in my Christmas break). All I want to know now is how can I tell kb.next() to take the second input of the user instead of the first.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by s3a on 2009-09-18
Changing

                                        ```
if(! kb.hasNextInt())

					{

					String junk = kb.next();

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					}					



					int year = kb.nextInt();

					
int month = kb.nextInt();

					int day = kb.nextInt();
```

to:

```
if(! kb.hasNextInt())

					{

					String junk = kb.next();

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					}					



					int year = kb.nextInt();

					

					if(! kb.hasNextInt())

					{

					String junk = kb.next();

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					}

					int month = kb.nextInt();

					

					if(! kb.hasNextInt())

					{

					String junk = kb.next();

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					}

					int day = kb.nextInt();
```

worked! (My friend told me)

---

### Post by dwhitney67 on 2009-09-18
This may seem harsh, but you should consider distancing yourself from the use of the Scanner class and doing keyboard input manually using, say, Reader, BufferedInputStream, and whatever else is needed.

Scanner is a utility, but just as a Swiss-Army knife, it is not "perfect" for all situations.  I know... MacGyver would probably disagree.

---

### Post by fiddler616 on 2009-09-18
> **dwhitney67 said:**
> This may seem harsh, but you should consider distancing yourself from the use of the Scanner class and doing keyboard input manually using, say, Reader, BufferedInputStream, and whatever else is needed.

Scanner is a utility, but just as a Swiss-Army knife, it is not "perfect" for all situations.  I know... MacGyver would probably disagree.
Do you have an example, or something? Scanner is preached very heavily in my Java class (with the exception of using...something else...(System.in.read()??) for chars). And I've never had too many problems with it, as long as I catch InputMismatchExceptions, and perform black magic with garbage collecting.

And OP: I didn't have the time to thoroughly analyze the working code you got, but you could always use kb.nextLine(), and then use string methods (find, substring) to pick out the string between the first and second space.

---

### Post by dwhitney67 on 2009-09-18
> **fiddler616 said:**
> Do you have an example, or something? Scanner is preached very heavily in my Java class (with the exception of using...something else...(System.in.read()??) for chars). And I've never had too many problems with it, as long as I catch InputMismatchExceptions, and perform black magic with garbage collecting.
...


My usage of the word "distancing" in my previous post was poorly chosen.  What I meant to imply is that the OP should learn to use other means to capture/interpret "variable" user data.

I come from a C/C++ background, and unfortunately no "Scanner" utility is available off the shelf.  Thus a developer must code the nuts-n-bolts themselves to appreciate the complexity of interpreting user input.

Your teachers may be correct, but I counter that they are wrong.  Java is not used everywhere.

-- Comment Edited --

---

### Post by falconindy on 2009-09-18
The language that you learn in a programming class rarely has much to do with the languages you'll use after you leave the class. The purpose has always been to teach you how to create clean and well structured code, while getting a feel for what programming is all about. Java might not be used everywhere, but it's a great example of how you should learn to program -- it encourages you to write small bits of useful code and reuse them, as you should in any OOP language.

Bottom line: there's a big difference between learning how to write code, and learning a specific language. Scanner's fine for what it is.

---

### Post by fiddler616 on 2009-09-19
> **dwhitney67 said:**
> My usage of the word "distancing" in my previous post was poorly chosen.  What I meant to imply is that the OP should learn to use other means to capture/interpret "variable" user data.

I come from a C/C++ background, and unfortunately no "Scanner" utility is available off the shelf.  Thus a developer must code the nuts-n-bolts themselves to appreciate the complexity of interpreting user input.

Your teachers may be correct, but I counter that they are wrong.  Java is not used everywhere.

P.S.  Before some Python dipstick weighs in, I know, C/C++ is not used everywhere as well.

Well then I stand behind my use of Scanner because it's the best tool for the job in the language I'm writing in. I refuse to stunt my Java code because I want to make sure I'm practicing my C* coding style.

Speaking about Python dipsticks (of which I am one), I'd much rather have:
[PHP]
raw_input() #String
int(raw_input()) # int
whatever_number_type(raw_input("Ooh, we can put a string here!"))[/PHP]
than poke around with lower level tools. raw_input() is very Pythonic, and I'd argue that Scanner is very Javaesque.

tl;dr - Celebrate diversity.

---

