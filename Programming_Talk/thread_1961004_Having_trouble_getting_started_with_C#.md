---
title: "Having trouble getting started with C#"
date: 2012-04-18
forum: Programming Talk
---

### Post by ratcheer on 2012-04-18
I am a total newbie with C#, but I am an experienced programmer since the early 1970's. I am trying to learn C# in order to help my wife as she learns it at her job. But, I am having trouble with the tiniest programs from the tutorial I am trying to follow.

My IDE is MonoDevelop 2.6. The first tutorial example, Hello World, compiles and runs perfectly. However, the second program demonstrates a way to pause and accept input from the user. The program compiles and runs, but it skips right past the pause for input and completes, having accepted a null input value that I did not enter. Is the tutorial wrong, did I do something wrong, or is this a bug in MonoDevelop?

Here is the code in question, with the statement that is supposed to pause for input highlighted:

```
            string firstName = "John";
            string lastName = "Doe";

            Console.WriteLine("Name: " + firstName + " " + lastName);

           [COLOR=Blue] Console.WriteLine("Please enter a new first name:");[/COLOR]
           [COLOR=Blue] firstName = Console.ReadLine();[/COLOR]

            Console.WriteLine("New name: " + firstName + " " + lastName);

            Console.ReadLine();
```Tim

---

### Post by 11jmb on 2012-04-18
This certianly seems like a bug in Mono. Having never used Mono, I can't tell you for sure, but I've had no problem reading from command line using Console.ReadLine() in VS C# projects

---

### Post by ratcheer on 2012-04-18
Thanks, @11jmb. That is my thought, too. The program is just too simple for it to be a program error. And the tutorial so carefully explained about the ReadLine statement waiting for input, I don't see how that can be wrong, either.

So, my MonoDevelop version 2.6 is from the Ubuntu repos. But the current version is 2.8. I wonder if I could find that and upgrade?

Tim

---

### Post by ratcheer on 2012-04-18
Ok, I figured out how to compile at the command line. Everything I read says use gmcs, but the command with my version of C# is dmcs.

Anyway, when done this way, the program runs as expected, waiting for and accepting user input. Either something is wrong with MonoDevelop, or there is something I don't know about how to use it.

Tim

---

### Post by Newbie2910 on 2012-04-18
Tim, I cannot give you an answer to your specific question but I have used MonoDevelop for several years and like it a lot.

I also use VisualC# (the freebie version) and like it as well.

Nice thing is, MonoDevelop will build and run any VC# project unchanged.  Is there a reason you are starting with console apps?  I would start with windowed apps and event-driven programming, much easier and the environment makes it simple to tie GUI events into code.

If you create a Windows Forms app using VC# and copy the project to MonoDevelop, it will run unchanged.  

You will also find that you can run WPF apps on Linux unchanged using VirtualBox (which I do).  I *love* WPF.

---

### Post by venomenus on 2012-04-19
Hi,

Just to add to this, We heavily run C# applications at work in a cross platform environment, The best way I've found to keep everyone running the same mono version in Linux is by adding the badgerports repository located here [http://badgerports.org/](http://badgerports.org/)
monodevelop is also included in this.

Hope this helps!

---

### Post by ratcheer on 2012-04-19
Thanks for the tip, @venomenus. I will take a look.

Tim

---

### Post by ratcheer on 2012-04-19
I have added badgerports to my system and upgraded to Mono 2.10 and MonoDevelop 2.8. This is excellent, but it does not resolve my problem. I have a feeling that I am not using MonoDevelop properly.

Tim

---

### Post by mehaga on 2012-04-20
Just copy-pasted your code into a new Monodevelop project. Runs exactly as expected. I don't know if it makes any difference, but let me ask, did you create your project as "Console Application"?

---

### Post by ratcheer on 2012-04-20
Thanks, @vekaz. I will try it that way. I have just been opening a c-sharp source file and running it in the console window. Or even just pasting in code from the tutorial. I thought that running these simple programs would be easy enough that way, but maybe they have to be part of a project. I guess I could call the prohect "Tutorial Examples" or something.

Tim

---

### Post by directhex on 2012-04-20
MonoDevelop's terminal emulator, VTE#, does not support input.

You need to configure your project to execute on an external shell, not the built-in terminal.

---

### Post by ratcheer on 2012-04-20
> **directhex said:**
> MonoDevelop's terminal emulator, VTE#, does not support input.

You need to configure your project to execute on an external shell, not the built-in terminal.

Thank you very much. I wonder why they cannot just make that plain in the documentation? Good grief.

Tim

---

