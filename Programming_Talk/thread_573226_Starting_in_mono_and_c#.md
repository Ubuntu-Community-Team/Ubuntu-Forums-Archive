---
title: "Starting in mono and c#"
date: 2007-10-11
forum: Programming Talk
---

### Post by mgazb on 2007-10-11
I'm just starting learning c# and mono. I've written a command line hello world but am having trouble with a GUI version.

If I add 
```

using System.Windows.Forms;

```

then mcs fails to compile it. It can't find dotnet if I add it to the command line.
```

dwhs1@gloin:~/mono$ mcs /pkg:dotnet blah.cs 
Package dotnet was not found in the pkg-config search path.
Perhaps you should add the directory containing `dotnet.pc'
to the PKG_CONFIG_PATH environment variable
No package 'dotnet' found

```
 
Where can I get the dotnet package?

If I explicitly include the forms library 
```

mcs -r:/usr/lib/mono/gac/System.Windows.Forms/2.0.0.0__b77a5c561934e089/System.Windows.Forms.dll blah.cs

```

I get a different lot of errors.

Is there a way of including winforms in a mono build?

---

### Post by TheOz on 2007-10-13
you'll need to compile your code in this way
```

mcs blah.cs -r:System.Windows.Forms.dll -r:System.Drawing.dll

```

---

### Post by mgazb on 2007-10-15
Thanks for the reply, it has got me the next step forward.
I had to add 

```
 
dwhs1@gloin:~/mono$ export MONO_PATH=/usr/lib/mono/2.0

```

to get it to find forms and drawing. I suspect that this demonstrates that I don't have everything set up correctly.

```

dwhs1@gloin:~/mono$ mcs -r:System.Windows.Forms.dll -r:System.Windows.Drawing.dll -r:System.Diagnostocs.dll blah.cs

** (/usr/lib/mono/1.0/mcs.exe:29923): WARNING **: Missing method System.Diagnostics.Process::get_StandardOutput() in assembly /usr/lib/mono/gac/System/1.0.5000.0__b77a5c561934e089/System.dll, referenced in assembly /usr/lib/mono/1.0/mcs.exe

Unhandled Exception: System.MissingMethodException: Method not found: 'System.Diagnostics.Process.get_StandardOutput'.
  at <0x00000> <unknown method>
  at Mono.CSharp.Driver.MainDriver (System.String[] args) [0x00000] 
  at Mono.CSharp.Driver.Main (System.String[] args) [0x00000] 

```

where can I find System.Diagnostics? I have grepped the /user/lib tree and still can't find it.

thanks

---

### Post by mgazb on 2007-10-15
If I use gmcs, then everything seems to work and I don't even need to reference System.Windows.Drawing and don't need to change MONO_PATH.

---

