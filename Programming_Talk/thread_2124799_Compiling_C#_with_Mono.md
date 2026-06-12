---
title: "Compiling C# with Mono"
date: 2013-03-12
forum: Programming Talk
---

### Post by qwikrazor87 on 2013-03-12
Hi.
I am trying to compile C# code with Mono under Xubuntu and I am having some trouble figuring it out.
I ran gmcs on the file and here are some errors that came up:
```
Program.cs(3,14): error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?

FormMain.cs(4,14): error CS0234: The type or namespace name `Data' does not exist in the namespace `System'. Are you missing an assembly reference?

FormMain.cs(5,14): error CS0234: The type or namespace name `Drawing' does not exist in the namespace `System'. Are you missing an assembly reference?

FileDirBrowser.cs(17,17): error CS0246: The type or namespace name `Color' could not be found. Are you missing a using directive or an assembly reference?

FileDirBrowser.cs(421,55): error CS0246: The type or namespace name `DragEventArgs' could not be found. Are you missing a using directive or an assembly reference?
```
I tried Googling it but I'm still at a loss of how to get it resolved.
I have installed mono-complete with apt-get.
I would appreciate some help.
Thanks.

---

### Post by slickymaster on 2013-03-12
Are you sure you compiled all your C# code?
Replace your_file.cs with *.cs to compile all your C# code, else just write the list of files to compile.

---

### Post by qwikrazor87 on 2013-03-12
> **slickymaster said:**
> Are you sure you compiled all your C# code?
Replace your_file.cs with *.cs to compile all your C# code, else just write the list of files to compile.
I tried compiling with *.cs as you have stated but the errors still pop up.
The code is open source and originally programmed on Windows.

---

### Post by slickymaster on 2013-03-12
Are you using the latest version of Mono? If not, this might work:
```
gmcs -pkg:dotnet *.cs
```
AFAIK the latest version of mono uses **mcs** instead of **gmcs**.

---

### Post by qwikrazor87 on 2013-03-12
You're awesome man!
9 warnings, but the compilation was successful. :D
I wanted to change some of the code that outputs files with the Windows "\", because that's not what linux uses.
Thank you very much! :D

---

