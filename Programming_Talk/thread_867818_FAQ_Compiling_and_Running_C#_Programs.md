---
title: "FAQ: Compiling and Running C# Programs"
date: 2008-07-23
forum: Programming Talk
---

### Post by LaRoza on 2008-07-23
**Working on the rest, post suggestions as well. I am not skilled or experienced in C#**

So you're willing to write your own C# programs, or simply compile someone else's code? This guide will get you started...

This FAQ assumes you're trying to compile *error-free* code. To actually learn the C# languages, see the [How to start programming](http://ubuntuforums.org/showthread.php?t=333867) thread.

Also remember that although C# is now an ECMA standard, and mono and gmcs follow it (at this point, up to 2.0 fully), many popular libraries used by C# in Windows are not part of the standard.

[SIZE="5"]**0.a. Make sure the [COLOR="Blue"]third party repositories[/COLOR] are enabled**[/SIZE]

The easiest way to do this is open Applications->Add/Remove and select "All Available Applications".

[SIZE="5"]**0.b. Make sure the [COLOR="Blue"]mono-gmcs[/COLOR] package is installed**[/SIZE]

This package installs the essential tools needed to write and run C# programs.

```
sudo aptitude install mono-gmcs

```

[SIZE="5"]**1. Compiling your [COLOR="Blue"]first C# program[/COLOR]**[/SIZE]

Copy & paste this code into a new file. Save the file as **Main.cs**
[php]
//First C# Program
using System;

namespace Main
{
   class Welcome
   {
      public static void Main( string[] args )
      {
          Console.Write("Hello world\n");
      }
   }
}//Matching brace. Some people can't be pleased...
[/php]
Open a terminal, go to the directory where you saved **Main.cs**, and type:
```
gmcs Main.cs
```If all went fine, nothing is printed and you get back to the shell. Now, run it:
```
mono Main.exe
```"Hello World!" gets printed in the terminal.

**Explanations:**[list][*] **[COLOR="Navy"]gmcs[/COLOR]** is the C# compiler
[*] obviously, **[COLOR="Navy"]Main[/COLOR]** means that the compiler must compile this file.
[*] **[COLOR="Navy"]mono Main.exe[/COLOR]** runs the newly compiled executable.[/list]


[SIZE="5"]**2. [COLOR="Blue"]Paranoid programming[/COLOR] is good for your health!**[/SIZE]

Many beginners want to avoid compiler errors and warnings at *any* cost, which often leads them to ignore the "cryptic" messages the compiler outputs and to tinker anxiously with the relevant line until the error goes away.
**Don't fall in that trap!** The compiler is your friend, the messages it outputs are *kind advices* rather than *punishments*. You should really take the time to try and understand those messages, this is a very good way to improve your code's quality.

As a matter of fact, most seasoned programmers set the compiler's warning level as high as possible, so that it catches the little errors they make when they aren't paying much attention.

**Help needed** Post in thread to recommend content or deletion of this section.


[SIZE="5"]**3. [COLOR="Blue"]Useful tips[/COLOR]**[/SIZE]

**Help needed** Post in thread to recommend content or deletion of this section.

[SIZE="5"]**4. [COLOR="Blue"]Read the manual![/COLOR]**[/SIZE]

Plain old manpage:
```
man gmcs
man mono
```

Naturally, the Documentation and Tutorial on the Mono project site [http://www.mono-project.com/](http://www.mono-project.com/) are good to visit.

You can use any editor, but [MonoDevelop]("http://www.monodevelop.com/Main_Page") seems to be the IDE of choice for many C# programmers.


Thanks to so many people @UF for their very useful help, this FAQ wouldn't be the same without them. In particular, this thread is based on aks44's thread on C and C++ (see link in sticky). Not only is this thread based on it, it is blatently copying it, I hope he doesn't mind...

---

### Post by Kadrus on 2008-07-23
Good Thread,this will help a lot of windows c# programmers(new comers) and Linux users that want to learn c# and are  facing problems compiling,setting up an environment,etc.
Well Done.

---

### Post by LaRoza on 2008-07-23
> **Kadrus said:**
> Good Thread,this will help a lot of windows c# programmers(new comers) and Linux users that want to learn c# and are  facing problems compiling,setting up an environment,etc.
Well Done.

Thanks. You'll notice it is a rip off of the Java FAQ, which was a rip off of the C++ FAQ (which I didn't write).

I just changed a few names and commands, added a few sentences and it was done :-)

---

### Post by Kadrus on 2008-07-23
Well still useful :-),although I don't code with C# :-P.But do some coding with F#.

---

### Post by era86 on 2008-07-23
> **LaRoza said:**
> 
The compiler is your friend, the messages it outputs are *kind advices* rather than *punishments*. You should really take the time to try and understand those messages, this is a very good way to improve your code's quality.

Very well said.  You should link to this in a sticky or sig. :guitar:

---

### Post by LaRoza on 2008-07-23
> **era86 said:**
> Very well said.  You should link to this in a sticky or sig. :guitar:

I didn't actually write it: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by Can+~ on 2008-07-23
I'm not a C# expert, but:

[PHP]//First C# Program
using System;

namespace Main
{ // <------ Where's the matching brace?
   class Welcome
   {
      public static void Main( string[] args )
      {
          Console.Write("Hello world\n");
      }
   }  [/PHP]

---

### Post by LaRoza on 2008-07-23
> **Can+~ said:**
> I'm not a C# expert, but:

Think you are clever, huh?

Adding brace and counter snipe comment :-)

---

### Post by Can+~ on 2008-07-23
> **LaRoza said:**
> Think you are clever, huh?

Adding brace and counter snipe comment :-)

No, actually I know crap about C#. I even though that you left it open because it was part of the notation.

---

### Post by LaRoza on 2008-07-23
> **Can+~ said:**
> No, actually I know crap about C#. I even though that you left it open because it was part of the notation.

Think Java (if you don't know Java, think C++).

As for it being part of the notation, it is technically, but if you want it to compile you should close it.

---

### Post by matyasfalvi on 2008-07-24
Deleted ---

---

### Post by LaRoza on 2008-07-24
> **matyasfalvi said:**
> Hi!

I am new to ubuntu and I am new to K&R C as well, I know it is gonna be hard but I have to learn it for school. I installed mono-gmcs as u said nevertheless I cannot compile my C program which I created using mcedit:[CODE]

Could u please help me out!

Thanx a lot!

C# != C ;)

See the sticky for C..

---

### Post by LaRoza on 2008-07-24
> **matyasfalvi said:**
> Hi!

I am new to ubuntu and I am new to K&R C as well, I know it is gonna be hard but I have to learn it for school. I installed mono-gmcs as u said nevertheless I cannot compile my C program which I created using mcedit:[CODE]

Could u please help me out!

Thanx a lot!

C# != C ;)

See the sticky for C..  [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by true_friend on 2008-07-25
It should be STICKY so every one can read and find it before posting such basic problems.

---

### Post by LaRoza on 2008-07-25
> **true_friend said:**
> It should be STICKY so every one can read and find it before posting such basic problems.

The sticky links to it.

---

### Post by navneeth on 2009-06-17
Why is this happening? :confused:

```
The following NEW packages will be installed
  mono-gmcs
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 399kB of archives.
After this operation, 1167kB of additional disk space will be used.
Get: 1 http://in.archive.ubuntu.com jaunty/main mono-gmcs 2.0.1-4 [399kB]
Fetched 399kB in 3s (112kB/s)     
Selecting previously deselected package mono-gmcs.
(Reading database ... 121954 files and directories currently installed.)
Unpacking mono-gmcs (from .../mono-gmcs_2.0.1-4_all.deb) ...
Processing triggers for man-db ...
Setting up mono-gmcs (2.0.1-4) ...
navneeth@ubuntu:~$ gmcs Main.cs
The program 'gmcs' is currently not installed.  You can install it by typing:
sudo apt-get install mono-devel
bash: gmcs: command not found

```

---

### Post by Zugzwang on 2009-06-17
> **navneeth said:**
> Why is this happening? :confused:


Because "mono-gmcs" only installs the "gmcs2" compiler executable (for version 2 and 3 of the language), "gmcs" is in mono-devel, as the notice told you.

Such information can easily be looked up at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by navneeth on 2009-06-17
Thanks. I wonder if the first post should be edited to include this information?

---

### Post by directhex on 2009-06-17
> **navneeth said:**
> Thanks. I wonder if the first post should be edited to include this information?

It probably should. Try leaving a note for the moderators to ask them to do it?

---

### Post by blwizard on 2009-10-24
Holy **** I didn't know C# syntax is so similar to Java's. Is it derived from Java or?

---

### Post by directhex on 2009-10-24
> **blwizard said:**
> Holy **** I didn't know C# syntax is so similar to Java's. Is it derived from Java or?

Officially no. In reality, it's HEAVILY influenced by Java

---

### Post by bonefry on 2009-10-24
> **blwizard said:**
> Holy **** I didn't know C# syntax is so similar to Java's. Is it derived from Java or?

It is heavily derived from Java, with influences from Delphi, C++ (more than Java) and Haskell (Linq was inspired from Haskell's monads, not surprisingly since Simon Peyton Jones works there).

---

### Post by shababhsiddique on 2010-01-10
> **LaRoza said:**
> **Working on the rest, post suggestions as well. I am not skilled or experienced in C#**

So you're willing to write your own C# programs, or simply compile someone else's code? This guide will get you started...

This FAQ assumes you're trying to compile *error-free* code. To actually learn the C# languages, see the [How to start programming]("http://ubuntuforums.org/showthread.php?t=333867") thread.

Also remember that although C# is now an ECMA standard, and mono and gmcs follow it (at this point, up to 2.0 fully), many popular libraries used by C# in Windows are not part of the standard.

[SIZE=5]**0.a. Make sure the [COLOR=Blue]third party repositories[/COLOR] are enabled**[/SIZE]

The easiest way to do this is open Applications->Add/Remove and select "All Available Applications".

[SIZE=5]**0.b. Make sure the [COLOR=Blue]mono-gmcs[/COLOR] package is installed**[/SIZE]

This package installs the essential tools needed to write and run C# programs.

```
sudo aptitude install mono-gmcs

```[SIZE=5]**1. Compiling your [COLOR=Blue]first C# program[/COLOR]**[/SIZE]

Copy & paste this code into a new file. Save the file as **Main.cs**
[php]
//First C# Program
using System;

namespace Main
{
   class Welcome
   {
      public static void Main( string[] args )
      {
          Console.Write("Hello world\n");
      }
   }
}//Matching brace. Some people can't be pleased...
[/php]Open a terminal, go to the directory where you saved **Main.cs**, and type:
```
gmcs Main.cs
```If all went fine, nothing is printed and you get back to the shell. Now, run it:
```
mono Main.exe
```"Hello World!" gets printed in the terminal.

**Explanations:**
[LIST]
[*] **[COLOR=Navy]gmcs[/COLOR]** is the C# compiler
[*] obviously, **[COLOR=Navy]Main[/COLOR]** means that the compiler must compile this file.
[*] **[COLOR=Navy]mono Main.exe[/COLOR]** runs the newly compiled executable.
[/LIST]


[SIZE=5]**2. [COLOR=Blue]Paranoid programming[/COLOR] is good for your health!**[/SIZE]

Many beginners want to avoid compiler errors and warnings at *any* cost, which often leads them to ignore the "cryptic" messages the compiler outputs and to tinker anxiously with the relevant line until the error goes away.
**Don't fall in that trap!** The compiler is your friend, the messages it outputs are *kind advices* rather than *punishments*. You should really take the time to try and understand those messages, this is a very good way to improve your code's quality.

As a matter of fact, most seasoned programmers set the compiler's warning level as high as possible, so that it catches the little errors they make when they aren't paying much attention.

**Help needed** Post in thread to recommend content or deletion of this section.


[SIZE=5]**3. [COLOR=Blue]Useful tips[/COLOR]**[/SIZE]

**Help needed** Post in thread to recommend content or deletion of this section.

[SIZE=5]**4. [COLOR=Blue]Read the manual![/COLOR]**[/SIZE]

Plain old manpage:
```
man gmcs
man mono
```Naturally, the Documentation and Tutorial on the Mono project site [http://www.mono-project.com/](http://www.mono-project.com/) are good to visit.

You can use any editor, but [MonoDevelop]("http://www.monodevelop.com/Main_Page") seems to be the IDE of choice for many C# programmers.


Thanks to so many people @UF for their very useful help, this FAQ wouldn't be the same without them. In particular, this thread is based on aks44's thread on C and C++ (see link in sticky). Not only is this thread based on it, it is blatently copying it, I hope he doesn't mind...


Thats a very good tutorial.

---

### Post by piyush910 on 2012-09-19
well i am just a beginner to c# and the code that you have typed is giving me the following error...
error:Cannot open assembly 'a.cs': File does not contain a valid CIL image.

---

### Post by muteXe on 2012-09-19
I don't code in c# on linux, but he wrote this in 2008. Maybe things (in terms of the compiler/mono etc) have changed slightly since then?
You might want to google a more up to date c# mono tutorial.

---

### Post by directhex on 2012-09-19
> **piyush910 said:**
> well i am just a beginner to c# and the code that you have typed is giving me the following error...
error:Cannot open assembly 'a.cs': File does not contain a valid CIL image.

You're trying to execute source code. You need to compile source code, then execute the result.

---

### Post by Mohan1289 on 2012-09-25
Hello Guys

This is Mohana Krishna from India

I want to learn about Linux Shell Scripting and a Programming Language( I don't know which is Good for a Beginner and currently i am trying to learn JAVA and Scripting though i don't know them completely i am trying to solve the Logic by writing algorithms).. 

Could you suggest me a language that's best for beginner 

I will be very happy if you can Guide me with level by level tasks..

I saw the tasks LaRoza gave on Ubuntu Forums..

They Look Simple yet changeable...

I want to take challenges by step by step from Simple to complex i will be very happy if anyone can guide me through.

i tried to send a message to LaRoza since he gave the tasks but i think he refused to recieve Personal messages.

I tried to mail to his hotmail account. that too is refusing the mail.. I Don't know where to find him so i am posting here..

---

### Post by sisco311 on 2012-09-26
> **Mohan1289 said:**
> Hello Guys

This is Mohana Krishna from India

I want to learn about Linux Shell Scripting and a Programming Language( I don't know which is Good for a Beginner and currently i am trying to learn JAVA and Scripting though i don't know them completely i am trying to solve the Logic by writing algorithms).. 

Could you suggest me a language that's best for beginner 

I will be very happy if you can Guide me with level by level tasks..

I saw the tasks LaRoza gave on Ubuntu Forums..

They Look Simple yet changeable...

I want to take challenges by step by step from Simple to complex i will be very happy if anyone can guide me through.

i tried to send a message to LaRoza since he gave the tasks but i think he refused to recieve Personal messages.

I tried to mail to his hotmail account. that too is refusing the mail.. I Don't know where to find him so i am posting here..

The OP is no longer a member of the Ubuntu Forums.

> **muteXe said:**
> I don't code in c# on linux, but he wrote this in 2008. Maybe things (in terms of the compiler/mono etc) have changed slightly since then?
You might want to google a more up to date c# mono tutorial.

+1

Thread closed.

---

