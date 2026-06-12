---
title: "C# mono: Type or namespace name `freenect' could not be found"
date: 2012-03-11
forum: Programming Talk
---

### Post by Matt Pellegrini on 2012-03-11
I'm keen to get programming using Kinect. So I wrote I basic program to  change the LED color based on buttons pressed in a GUI to see if I could  get things rolling... 

I wrote the file in c# and compiled 

                gmcs -pkg:gtk-sharp-2.0 helloworldkinect.cs 

I get the following error... 

                Error CS0246: The type or namespace name `freenect'  could not be found. Are you missing a using directive or an assembly  reference? 

 ...and don't know how to sort it out, I'm sure it's simple enough but  there simply isn't somewhere to ask these questions nor any really basic  examples out there.

libfreenect.so exists in /usr/lib/ and -pkg:libfreenect didn't work.

I don't actually understand what the .so file is, only that all the demo application work, and I can get the depth and RGB videos to display with a Kinect plugged in (so it works).

Thanks in advance for any help/ info.

Matt

---

### Post by uRock on 2012-03-11
Moved to *Programming Talk*

---

### Post by directhex on 2012-03-11
> **Matt Pellegrini said:**
> I'm keen to get programming using Kinect. So I wrote I basic program to  change the LED color based on buttons pressed in a GUI to see if I could  get things rolling... 

I wrote the file in c# and compiled 

                gmcs -pkg:gtk-sharp-2.0 helloworldkinect.cs 

I get the following error... 

                Error CS0246: The type or namespace name `freenect'  could not be found. Are you missing a using directive or an assembly  reference? 

 ...and don't know how to sort it out, I'm sure it's simple enough but  there simply isn't somewhere to ask these questions nor any really basic  examples out there.

libfreenect.so exists in /usr/lib/ and -pkg:libfreenect didn't work.

I don't actually understand what the .so file is, only that all the demo application work, and I can get the depth and RGB videos to display with a Kinect plugged in (so it works).

Thanks in advance for any help/ info.

Matt

A "using" directive relates to a namespace in a referenced assembly, e.g. "using System" works when you reference mscorlib

The -pkg:foo flag to Mono serves as a shorthand way to run "pkg-config --libs foo" on the assumption that foo is a .NET library and the pkg-config file for it includes lines like "-r:foo.dll"

Neither of these are remotely useful for you if you're trying to call into C libraries from C# (which is the case when trying to use a .so file). What you want to do is P/Invoke the .so file. See [http://www.mono-project.com/Interop_with_Native_Libraries](http://www.mono-project.com/Interop_with_Native_Libraries)

---

### Post by Matt Pellegrini on 2012-03-12
The link you provided suggests using [DllImport ("libfreenect.so")] and also says that the search for such a parameter eventually looks in /usr/lib (where libfreenect.so is stored).

However this still doesn't work.

The example code ([http://openkinect.org/wiki/CSharp_Wrapper](http://openkinect.org/wiki/CSharp_Wrapper))
Uses a "using freenect;" statement at the top. I'm thinking now that this csharp wrapper needs to be installed properly but the instructions on the page are not very helpful. I get as far as copying the libfreenect.so to some directory then it just says to build it...

This is so frustrating, I just want to get access to the libraries but know very little about how everything is connected together here.

---

### Post by directhex on 2012-03-12
> **Matt Pellegrini said:**
> I get as far as copying the libfreenect.so to some directory then it just says to build it...

"Building C# wrapper and demo application" heading covers building the wrapper.

A .so on its own is not a C# wrapper.

---

