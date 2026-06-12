---
title: "Who parses out the parameters and places them in argv?"
date: 2009-06-25
forum: Programming Talk
---

### Post by deleyd on 2009-06-25
(I'm a complete novice at Linux, but this question is a bit involved. Originally worded as a Windows OS question. I want to learn how Linux handles command line parameters.)

If I launch a process from a command line, and I pass parameters to that process on the command line, e.g.

> MyCProgram.exe   one   two   three

In my C program I can access those parameters (one, two, three) using argv[] & argc. The parameters have already been parsed out into the argv[] array when control reaches my C program.

Who is responsible for parsing the command line parameters into argv[]? Is it the Operating System? Or does the C compiler throw in some code that does the parsing before control reaches my main routine?

Here's what I noticed which made me interested in this. If I have a simple C program that just echos the parameters:

>ShowParams.exe   "c:\test a\"   "c:\test b\"

I get:

param 1 = c:\test a" c:\test
param 2 = b"

Someone is parsing \" as meaning "a literal double quote." But if I instead run a .vbs script [does VBScript exist on Linux?]:

>ShowParams.vbs   "c:\test a\"     "c:\test b\"

I get different results:

param 1 = c:\test a\
param 2 = c:\test b\

Here \" is NOT interpreted as meaning "a literal double quote". So the rules aren't the same. Someone else is parsing the command line differently.

I tested again with a simple DOS batch file:

>ShowParams.bat   "c:\test a\"   "c:\test b\"

I get:

param 1 = "c:\test a\"
param 2 = "c:\test b\"

This time the double quotes are included as part of the parameter.

So I'm interested in what are the rules for passing special characters in parameters to C programs or scripts on Linux? Is there a standard? Or does it vary like it does on Windows?

Does Linux have a script language like VBScript, or batch files? (I think Linux has .sh shell files. It's been a long time since I toyed with a Unix machine. Things may have changed.)

---

### Post by deleyd on 2009-06-28
I found "Larry Osterman's WebLog: The Windows command line is just a string..."
[http://blogs.msdn.com/larryosterman/archive/2007/10/03/the-windows-command-line-is-just-a-string.aspx](http://blogs.msdn.com/larryosterman/archive/2007/10/03/the-windows-command-line-is-just-a-string.aspx)
who explains:

[INDENT]*nix and Windows handle command line arguments totally differently.  On *nix, you launch a program using the execve API(or  it's cousins execvp, execl, execlp, execle, and execvp).  Theinteresting thing about these APIs is that they allow the caller to specify each of the command line arguments - the signature for execve is:

[INDENT]**int execve(const char** **filename*, **char *const** *argv* [], **char *const** *envp*[]);[/INDENT] 

In *nix, the shell is responsible for turning the string provided by the user into the argv parameter to the program.
 
On Windows, the command line doesn't work that way.  Instead, you launch a new program using the [COLOR="Navy"]CreateProcess[/COLOR] API,which takes the command line as a string (the lpComandLine parameter to CreateProcess).  It's considered the responsibility of the newlystarted application to call the [COLOR="Navy"]GetCommandLine[/COLOR] API to retrieve that command line and parse it (possibly using the [COLOR="Navy"]CommandLineToArgvW[/COLOR] helper function).[/INDENT]

On Windows I disassembled my ShowParams.exe and found the code that calls [COLOR="Navy"]GetCommandLine[/COLOR] and parses the command line into *argv*[]. It was added by the compiler.

---

### Post by soltanis on 2009-06-28
To answer your second question, yes, Linux has .sh, scripts that utilize the standard shell. Also included in any standard UNIX environment is awk, which along with sh are the two guaranteed scripting environments.

Of course most machines also have Python resident, so you can script in that and get away with it, Perl is also pretty widely common. The standard (but not scripting) language available on any *nix worth using is C, of course, and usually this is the GNU C Compiler (but this is no requirement -- the cc might be completely different, or the computer might not even have one at all).

---

