---
title: "How do execute a bash script with C# .NET"
date: 2011-07-15
forum: Programming Talk
---

### Post by Drenriza on 2011-07-15
Hi all.

I hope someone can help me. On a Linux debian server i got, i have installed mono, with the purpose of being able to make a C# .NET program, that can execute a bash script, and somehow import the output of the bash script into C# for processing. 

But how do you do this?

Also, how can you from C# send a argument or value to a bash script?

Hope someone can help me, or lead me in the right direction.

Thanks on advance.
Kind regards.

---

### Post by PaulM1985 on 2011-07-15
What script are you trying to run?

Have you checked that libraries don't already exist for what you are after?

Paul

---

### Post by Drenriza on 2011-07-15
Lets say i want to run a script containing ls commands.
Just so i can get an example of this process.

---

### Post by MadCow108 on 2011-07-15
see:
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)
[http://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.standardoutput.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.standardoutput.aspx)

example:
```
/*$ cat /tmp/bash.sh 
 * #!/bin/bash
 * echo "bla $1"
 */
using System;
using System.Diagnostics;

class Runshell
{
  static void Main()
  {
    ProcessStartInfo psi = new ProcessStartInfo();
    psi.FileName = "/tmp/bash.sh";
    psi.UseShellExecute = false;
    psi.RedirectStandardOutput = true;

    psi.Arguments = "test";
    Process p = Process.Start(psi);
    string strOutput = p.StandardOutput.ReadToEnd();
    p.WaitForExit();
    Console.WriteLine(strOutput);
  }
}

```

---

### Post by Drenriza on 2011-07-15
> **MadCow108 said:**
> see:
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)
[http://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.standardoutput.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.standardoutput.aspx)

example:
```
/*$ cat /tmp/bash.sh 
 * #!/bin/bash
 * echo "bla $1"
 */
using System;
using System.Diagnostics;

class Runshell
{
  static void Main()
  {
    ProcessStartInfo psi = new ProcessStartInfo();
    psi.FileName = "/tmp/bash.sh";
    psi.UseShellExecute = false;
    psi.RedirectStandardOutput = true;

    psi.Arguments = "test";
    Process p = Process.Start(psi);
    string strOutput = p.StandardOutput.ReadToEnd();
    p.WaitForExit();
    Console.WriteLine(strOutput);
  }
}

```

Thanks, this gives me a lot of information i can look through and make searches from. Thumps up. If anyone has more to give :p i wont say **_NO!_**

---

### Post by PaulM1985 on 2011-07-15
> **Drenriza said:**
> Lets say i want to run a script containing ls commands.

This is exactly the reason I didn't post the solution in my original post.  What do you really want to do?  Finding information about files and folders is something you should be doing with the .NET API, not something you should be running bash scripts on.

You should try to avoid running scripts from C# unless you have no other alternative.

Paul

---

### Post by Drenriza on 2011-07-15
> **PaulM1985 said:**
> This is exactly the reason I didn't post the solution in my original post.  What do you really want to do?  Finding information about files and folders is something you should be doing with the .NET API, not something you should be running bash scripts on.

You should try to avoid running scripts from C# unless you have no other alternative.

Paul

I work in a medium size corporation, where i from time to time write scripts to do a specific task. Over R&D department has at sometime written a command in the C language or bash scripting (i don't know what it is 100% or how to check it, asking is like puting a sign on ur back saying "i'm THAT dumb"). But it can be executed from a bash script. And what i want to do it run that command (right now) and take its output. But it wodent make sense (i think) to tell about a custom command you don't know. So just to get an example to work from. I said **_ls_**. Since thats what comes the closest in function, and what has most similarities in its output form.

I'm interested in learning the foundation in getting C# working on Linux.
Taking output from bash, C and C++ and being able to work with it in C#. But i need to start somewhere, to try and get this understanding.

> Finding information about files and folders is something you should be doing with the .NET API, not something you should be running bash scripts on.
Your right, but i dont know how.

---

### Post by PaulM1985 on 2011-07-15
Ok, so you have a function in C that you want to call.  Have you seen anything like this:

[http://msdn.microsoft.com/en-us/library/aa288468%28v=vs.71%29.aspx](http://msdn.microsoft.com/en-us/library/aa288468%28v=vs.71%29.aspx)

Say you have a function in C which looks like:
int GetNumPlusOne(int num)
in a lib called "Test.dll"

You can do:
[DllImport("Test.dll")]
public static extern int GetNumPlusOne(int num);

And now you can use GetNumPlusOne in your C# code.  Saves you having to use scripts :-)

Paul

---

### Post by PaulM1985 on 2011-07-15
File and directory info can be found using the file and directory info classes:

[http://msdn.microsoft.com/en-us/library/system.io.fileinfo.aspx](http://msdn.microsoft.com/en-us/library/system.io.fileinfo.aspx)
[http://msdn.microsoft.com/en-us/library/system.io.directoryinfo.aspx](http://msdn.microsoft.com/en-us/library/system.io.directoryinfo.aspx)

Paul

---

### Post by Drenriza on 2011-07-15
> **PaulM1985 said:**
> Ok, so you have a function in C that you want to call.  Have you seen anything like this:

[http://msdn.microsoft.com/en-us/library/aa288468%28v=vs.71%29.aspx](http://msdn.microsoft.com/en-us/library/aa288468%28v=vs.71%29.aspx)

Say you have a function in C which looks like:
int GetNumPlusOne(int num)
in a lib called "Test.dll"

You can do:
[DllImport("Test.dll")]
public static extern int GetNumPlusOne(int num);

And now you can use GetNumPlusOne in your C# code.  Saves you having to use scripts :-)

Paul

As i understand it a DLL is a dynamic link library. Lets say this custom C program lies in /path/bin/commandName

How can i decompile this, and search for this function, that you describe.
Or have i misunderstood something?

---

### Post by PaulM1985 on 2011-07-15
I think that you would be able to use a path to an .exe instead of a .dll in the import, but I am not certain.

I assumed you had the source code for the command you wanted to run, so you would know what it does and what functions are involved etc.

Do you do code reviews at your company?  Would it not be best to suggest your solution to your reviewer before you implement and ask what they think?  That's how I learned stuff.

Paul

---

### Post by Drenriza on 2011-07-15
> **PaulM1985 said:**
> 
Do you do code reviews at your company?  Would it not be best to suggest your solution to your reviewer before you implement and ask what they think?  That's how I learned stuff.
Paul

Hi Paul.
At the company i'm currently in, i work as a 3'rd level technician on a Linux system (Debian).
And unfurtiantly over R&D does not have time, to review what code i make, or make tools for us. So i make what tools i need myself. Also the program i'm currently trying to make is to run on a local test system. Where it has 0 consequences.

But me and my other co workers in my department (support) has before made tools to over system, and tried to get it passed by over R&D department. But it just get dropped on the floor. So if we need to get something "cleared" for a live system, we send it to over testing department. And if they clear it, well then thats that :p or else they review it and say what is not good enough and then i need to change it if i want it approved, but they don't give suggestions or anything like that.

But your way is definitely the best.

---

### Post by Drenriza on 2011-07-18
> **PaulM1985 said:**
> Ok, so you have a function in C that you want to call.  Have you seen anything like this:

[http://msdn.microsoft.com/en-us/library/aa288468%28v=vs.71%29.aspx](http://msdn.microsoft.com/en-us/library/aa288468%28v=vs.71%29.aspx)

Say you have a function in C which looks like:
int GetNumPlusOne(int num)
in a lib called "Test.dll"

You can do:
[DllImport("Test.dll")]
public static extern int GetNumPlusOne(int num);

And now you can use GetNumPlusOne in your C# code.  Saves you having to use scripts :-)

Paul

But how do i find out, what functions a C program has? Since it's compiled to machine code to i need to decompile it to find out or?

---

### Post by PaulM1985 on 2011-07-18
> **Drenriza said:**
> But how do i find out, what functions a C program has? Since it's compiled to machine code to i need to decompile it to find out or?

I was assuming since your company wrote it you may be able to look at the source code...

To be honest, if it is really difficult to get hold of that sort of stuff, maybe running the process like you are doing now is going to be your simplest solution.  Additionally, thinking about it some more, the chance that someone has exported a function in an executable is probably not that likely, so even if you got the function name, you might not be able to PInvoke it.

You were probably right first time, stick with using C#'s Process and parse the output.

Paul

---

### Post by Drenriza on 2011-07-18
> **MadCow108 said:**
> see:
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)
[http://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)
[http://msdn.microsoft.com/en-us/library/system.diagnostics.process.standardoutput.aspx](http://msdn.microsoft.com/en-us/library/system.diagnostics.process.standardoutput.aspx)

example:
```
/*$ cat /tmp/bash.sh 
 * #!/bin/bash
 * echo "bla $1"
 */
using System;
using System.Diagnostics;

class Runshell
{
  static void Main()
  {
    ProcessStartInfo psi = new ProcessStartInfo();
    psi.FileName = "/tmp/bash.sh";
    psi.UseShellExecute = false;
    psi.RedirectStandardOutput = true;

    psi.Arguments = "test";
    Process p = Process.Start(psi);
    string strOutput = p.StandardOutput.ReadToEnd();
    p.WaitForExit();
    Console.WriteLine(strOutput);
  }
}

```

Cool.

Tried this code out myself and it works. Sure its a simple ls -lah but gives a sort of feeling that i am going in the right direction :p need to read more about this.

EDIT:
Is their a way to start a C# program without typing mono infront of the program name.exe?

---

### Post by Drenriza on 2011-07-18
> **PaulM1985 said:**
> I was assuming since your company wrote it you may be able to look at the source code...
Paul

You would believe so.
I kinda want to smile and :( at the same time.

---

### Post by directhex on 2011-07-18
> **Drenriza said:**
> EDIT:
Is their a way to start a C# program without typing mono infront of the program name.exe?

Install the binfmt-support package.

---

### Post by directhex on 2011-07-18
> **Drenriza said:**
> But how do i find out, what functions a C program has? Since it's compiled to machine code to i need to decompile it to find out or?

objdump -T

---

### Post by venomenus on 2011-07-23
> **Drenriza said:**
> Cool.

Is their a way to start a C# program without typing mono infront of the program name.exe?

Another way of starting this program without typing mono first would be to write a shell script to call mono with the application exe.

```

#!/bin/bash
mono "name.exe" &

```
then you can just execute this instead.

---

