---
title: "Problem with Mono. Pls help."
date: 2008-06-04
forum: Programming Talk
---

### Post by x88a on 2008-06-04
i am trying to run a file called "Program.cs" using Mono.

Here is the Program.cs content:-

&#65279;using System;

using System.Collections.Generic;

using System.Windows.Forms;



namespace ECamTools {

static class Program {

/// <summary>

/// Der Haupteinstiegspunkt für die Anwendung.

/// </summary>

[STAThread]

static void Main(string[] args) {

Application.EnableVisualStyles();

Application.SetCompatibleTextRenderingDefault(fals e);

Application.Run(new ECamViewer(args));

}

}

}



after typing "mcs Program.cs", i get this error:-

Program.cs(2,7): error CS0234: The type or namespace name `Generic' does not exist in the namespace `System.Collections'. Are you missing an assembly reference?
Program.cs(2,1): error CS0246: The type or namespace name `Collections.Generic' could not be found. Are you missing a using directive or an assembly reference?
Program.cs(3,7): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 4 error(s), 0 warnings


From my intepretation, the errors are all based on the libraries.
What is wrong?

Pls help.

TQ

---

### Post by Zugzwang on 2008-06-04
A solution could easily be found using the search function: [http://ubuntuforums.org/showthread.php?t=722869]("http://ubuntuforums.org/showthread.php?t=722869")

---

### Post by kragen on 2008-06-04
It looks like a combination of using the wrong version of .Net (Generics are only in .Net 2.0 and above) and not referencing System.Windows when building.

Looking at the documentation for mcs you need to:

[LIST=1]
[*]use the flag "-v2" to enable .Net 2.0
[*]reference the system.windows.dll and system.windows.drawing.dll assembly using "-r:System.Windows.Forms.dll -r:System.Drawing.dll"
[/LIST]

So my guess would be use:

```

mcs Program.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll -v2
```

and hope for the best!

(Note that I've never used mono, so those parameters could well be wrong, but your problem is that you need to reference those two assemblies and use .Net 2.0 not .Net 1.1)

---

### Post by Peyton on 2008-06-04
Yes, Mono defaults to .NET 1.1.

---

### Post by x88a on 2008-06-05
i have started a new thread
[http://ubuntuforums.org/showthread.php?t=819095](http://ubuntuforums.org/showthread.php?t=819095)

some tiny changes made

pls help

tq

---

### Post by LaRoza on 2008-06-05
```

~$apt-cache search windows.forms
libmono-winforms1.0-cil - Mono System.Windows.Forms library
libmono-winforms2.0-cil - Mono System.Windows.Forms library
~$

```

Looks like you should install it first (it doesn't come by default).

---

### Post by x88a on 2008-06-05
root@laptop:~/Desktop/ECamTools/ECamViewer# apt-cache search windows.forms
libmono-winforms1.0-cil - Mono System.Windows.Forms library
libmono-winforms2.0-cil - Mono System.Windows.Forms library
root@wlx01234:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs
Program.cs(3,14): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings


still doesnt work :(

---

### Post by LaRoza on 2008-06-05
> **x88a said:**
> root@wlx01234:~/Desktop/ECamTools/ECamViewer# apt-cache search windows.forms
libmono-winforms1.0-cil - Mono System.Windows.Forms library
libmono-winforms2.0-cil - Mono System.Windows.Forms library
root@wlx01234:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs
Program.cs(3,14): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings

still doesnt work :(

Install the library needed. That command just searches the repos.

---

### Post by x88a on 2008-06-05
```
Install the library needed. That command just searches the repos.
```

ic, could you pls tell me how to install the library?
i m very new to these

---

### Post by LaRoza on 2008-06-05
> **x88a said:**
> 
ic, could you pls tell me how to install the library?
i m very new to these

You could just search in synaptic. I use the command line, but synaptic can be used.

The command for installing is:

```

sudo aptitude install <packagename>

```

Where <packagename> is what you want to install.

---

### Post by x88a on 2008-06-05
root@laptop:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs
Program.cs(3,14): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings
root@laptop:~/Desktop/ECamTools/ECamViewer#

---

### Post by Zugzwang on 2008-06-05
> **x88a said:**
> root@laptop:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs
Program.cs(3,14): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
Program.cs(3,1): error CS0246: The type or namespace name `Windows.Forms' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings
root@laptop:~/Desktop/ECamTools/ECamViewer#
Did you try kragen's solution of referencing the assemblies?

---

### Post by x88a on 2008-06-05
> **Zugzwang said:**
> Did you try kragen's solution of referencing the assemblies?

i tried with both mcs and gmcs. Here are the results:-

root@laptop:~/Desktop/ECamTools/ECamViewer# mcs Program.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll -v2
The compiler option -2 is obsolete. Please use /langversion instead
Program.cs(2,7): error CS0234: The type or namespace name `Generic' does not exist in the namespace `System.Collections'. Are you missing an assembly reference?
Program.cs(2,1): error CS0246: The type or namespace name `Collections.Generic' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 2 error(s), 0 warnings


Compilation failed: 2 error(s), 0 warnings
root@laptop:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll -v2
The compiler option -2 is obsolete. Please use /langversion instead
Program.cs(14,33): error CS0246: The type or namespace name `ECamViewer' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 1 error(s), 0 warnings


doesnt work too :(

---

### Post by Zugzwang on 2008-06-05
> **x88a said:**
> root@laptop:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll -v2
The compiler option -2 is obsolete. Please use /langversion instead
Program.cs(14,33): error CS0246: The type or namespace name `ECamViewer' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 1 error(s), 0 warnings

doesnt work too :(

It does! Your program won't compile using Windows, too. This is because you are referencing to "ECamViewer" but this appears to be your own class which you didn't define.

---

### Post by x88a on 2008-06-05
> **Zugzwang said:**
> It does! Your program won't compile using Windows, too. This is because you are referencing to "ECamViewer" but this appears to be your own class which you didn't define.

what can i do to solve this problem?

Additional info: What i am doing now is trying to convert the source code for a E-Cam viewer from Windows to Linux. The source code consists of many many different files.

---

### Post by Zugzwang on 2008-06-05
> **x88a said:**
> 
Additional info: What i am doing now is trying to convert the source code for a E-Cam viewer from Windows to Linux. The source code consists of many many different files.

You should seriously look into some examples and tutorials about compiling programs using Mono. With regards to your problem: Have a look at [the man page of gmcs]("http://manpages.unixforum.co.uk/man-pages/linux/suse-linux-10.1/1/gmcs-man-page.html") and read the fourth paragraph of the description section. If you have a compiled version of your applications, you might also look at [this page]("http://http://www.mono-project.com/Guide:_Porting_Winforms_Applications").

---

### Post by x88a on 2008-06-05
```
C#  source  files  must  end with a ".cs" extension.  Compilation of C#
source code requires all the files that make up a  library,  module  or
executable to be provided on the command line.  There is no support for
partial compilation.  To achieve the benefits of  partial  compilation,
you should compile programs into their own assemblies, and later refer-
ence them with the "-r" flag.
```

From what i see, my codes are seperated into many different files. Is there a way to compile them using Mono?

It says there is a way for partial compilation, but that is not what i want

TQ

---

### Post by Zugzwang on 2008-06-05
Please read more carefully. It says:

> **x88a said:**
> Compilation of C# source code requires all the files 
that make up a  library,  module  or executable to be provided on the command line.

This means that you need to provide all files at once, i.e. something like, but not necessarily identical to:
```

gmcs Program.cs AnotherSourceFile.cs YetAnotherSourceFile.cs HeyIDontBelieveItEvenOneMoreFile.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll -v2

```

Btw: What's an E-Cam?

---

### Post by x88a on 2008-06-05
> Please read more carefully.
ic, so that is what it means.

> Btw: What's an E-Cam?
ethernet camera

---

### Post by x88a on 2008-06-05
root@laptop:~/Desktop/ECamTools/ECamViewer# gmcs Program.cs Camera.cs ConfigurationControl.cs ConfigurationControl.Designer.cs ConnectDialog.cs ConnectDialog.Designer.cs ECamViewer.cs ECamViewer.Designer.cs ImageControl.cs ImageControl.Designer.cs Paramter.cs RemoteProcedureCall.cs Settings.cs TcpClient1.cs TcpClient2.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll
TcpClient2.cs(16,10): error CS0101: The namespace `VideoStreamViewer' already contains a definition for `CameraStatus'
TcpClient1.cs(16,10): (Location of the symbol related to previous error)
TcpClient2.cs(22,17): error CS0101: The namespace `VideoStreamViewer' already contains a definition for `CameraProtocolType'
TcpClient1.cs(24,17): (Location of the symbol related to previous error)
TcpClient2.cs(28,11): error CS0101: The namespace `VideoStreamViewer' already contains a definition for `Camera'
TcpClient1.cs(30,11): (Location of the symbol related to previous error)
Compilation failed: 3 error(s), 0 warnings


still doesnt work :(

p/s - with -v2, i get more errors

---

### Post by Zugzwang on 2008-06-05
> **x88a said:**
> 
TcpClient2.cs(16,10): error CS0101: The namespace `VideoStreamViewer' already contains a definition for `CameraStatus'
TcpClient1.cs(16,10): (Location of the symbol related to previous error)
TcpClient2.cs(22,17): error CS0101: The namespace `VideoStreamViewer' already contains a definition for `CameraProtocolType'
TcpClient1.cs(24,17): (Location of the symbol related to previous error)
TcpClient2.cs(28,11): error CS0101: The namespace `VideoStreamViewer' already contains a definition for `Camera'
TcpClient1.cs(30,11): (Location of the symbol related to previous error)
Compilation failed: 3 error(s), 0 warnings


It doesn't look like it is supposed to have the two versions of the clients included at the same time. Try it with only one of them. 

> **x88a said:**
> 
p/s - with -v2, i get more errors
Let me guess - The one that says that this option shouldn't be used anymore?

---

### Post by x88a on 2008-06-05
> **Zugzwang said:**
> Let me guess - The one that says that this option shouldn't be used anymore?

what do u mean?

---

### Post by Zugzwang on 2008-06-05
> **x88a said:**
> what do u mean?

In your post 3 hours ago, you pasted the output of the compiler run:
```

...
The compiler option -2 is obsolete. Please use /langversion instead
...

```
But that's not an *error*. It just tells you that in the future you should use langversion. If you get this warning, why don't you fix it? It should be stated on the man page how that can be done.

Does it work now?

---

### Post by LaRoza on 2008-06-05
> **x88a said:**
> 
Additional info: What i am doing now is trying to convert the source code for a E-Cam viewer from Windows to Linux. The source code consists of many many different files.

Do you understand the code?

---

### Post by x88a on 2008-06-06
> **LaRoza said:**
> Do you understand the code?

no :(

---

### Post by LaRoza on 2008-06-06
> **x88a said:**
> no :(

Then this project will likely fail. It is using parts of C# that are not part of the ECMA standard (although, as you see, some of those non standard parts are implemented for mono), and is likely using Windows specific features.

---

### Post by x88a on 2008-06-06
how would you suggest me to get about with this problem?

---

### Post by LaRoza on 2008-06-06
> **x88a said:**
> how would you suggest me to get about with this problem?

With you having no programming knowledge in this area, I have no suggestions that are really useful.

The best thing to do is find a Linux alternative.

---

### Post by sandylaw on 2008-10-26
[SIZE="6"][COLOR="RoyalBlue"]How to set the monodevelop to compile default to .net 2.0?
Thank you![/COLOR][/SIZE]

---

### Post by pp. on 2008-10-26
Please start your own thread.
Please do not use annoying font colours and sizes.

---

### Post by sandylaw on 2008-10-26
UP
UP
How to set the monodevelop compile default to .net 2.0?
Thx.

---

### Post by directhex on 2008-10-27
Right click on the project in the solutions pane, click Options, go to Runtime Options, and set it to 2.0

Requires mono-gmcs installed.

And as someone else said, you should REALLY have started a new thread, not piggy-backed an irrelevant old one

---

