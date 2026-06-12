---
title: "Using speech synthesis software with C sharp and Linux."
date: 2011-09-11
forum: Programming Talk
---

### Post by cyb3r_sn4k3 on 2011-09-11
I am doing this project in C Sharp (C#) were I have to make the computer  speak out a few sentences so I am using Festival Speech Synthesis in  Linux. But how do I use the output of the C # console program in  festival. Right now I am doing it like this.

```

using System;
using System.Diagnostics;
namespace speak
{
   class MainClass
   {
      public static void Main (string[] args)
      {
         string s = Console.ReadLine();
         Process.Start("/bin/echo " + '"' + s + '"' + " | festival --tts");
      }
   }
}


```But I get a error :(

```

Error showing url: Error stating file '/bin/echo hello | festival --tts': No such file or directory

```Please help.

---

### Post by ziekfiguur on 2011-09-11
i'm not familiar with C# but i think process.start doesn't create a subshell, but executes the file directly. So shell syntax like | to pipe cannot be used, you just have to give it one filename and use another way to create a pipe.

---

### Post by cyb3r_sn4k3 on 2011-09-11
I tried doing it another way by writing the text to a file then making Festival read that file but even then I get somewhat the same error.

---

### Post by ziekfiguur on 2011-09-11
I think you have to use separate arguments for command-line parameters you want to pass to the command. the first one should just be the filename of the program, nothing more.

Edit, a quick google found this:
```
ProcessStartInfo startInfo = new ProcessStartInfo();
startInfo.FileName = "WINWORD.EXE";
startInfo.Arguments = f;
Process.Start(startInfo);

```

---

### Post by PaulM1985 on 2011-09-11
See the post by MadCow108 in this thread:
[http://ubuntuforums.org/showthread.php?t=1804818](http://ubuntuforums.org/showthread.php?t=1804818)

Paul

---

