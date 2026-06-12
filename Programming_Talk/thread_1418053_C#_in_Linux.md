---
title: "C# in Linux?"
date: 2010-02-28
forum: Programming Talk
---

### Post by Lyerae on 2010-02-28
I'm developing a custom parser, and one of the languages I've been considering is a C#.
The only problem with that is I need cross-compatiblity, without any kind of errors.

I was talking to a friend on MSN earlier, and he showed me something called MonoDevelop, which would allow me to create programs in C# for Linux, but I also need them to work on Windows and Mac platforms.

If I were to compile the code, would it compile it into an .exe which runs through Wine, or would it compile as a native program?

---

### Post by ja660k on 2010-02-28
you could always download virtualbox and install windows that way

---

### Post by DrMelon on 2010-02-28
> **ja660k said:**
> you could always download virtualbox and install windows that way

That's not what he was asking - he wanted to be able to compile C# on Linux.

I think you'd have to compile the code on those platforms - it'd probably work. IMO, you should give it a try! Make a simple little program, and compile it and see what you get.

---

### Post by Lyerae on 2010-02-28
Alright. I'll try that.

---

### Post by cprofitt on 2010-02-28
Just a small word of warning from a person who used to code in C#.

If you are looking to be cross-platform I would pick a language that is truly cross platform.

---

### Post by cb951303 on 2010-02-28
C# as a programming language is cross-platform and Mono applications are binary compatible with MS.NET. So you can compile an application on Linux and run it on Windows if you stick to the libraries that are available on both platforms. AFAIK most of the .NET libraries are supported by Mono.

---

### Post by cprofitt on 2010-02-28
Does C# code run on OS X or BSD?

I knew about Linux, but thought that was the extent -- maybe things have changed from a year ago though.

update:  It does indeed look as though Mono added support for OS X.

Perhaps my C# experience is valuable again.

-- edit 2 --
I just installed MonoDevelop and I have to say it is quite slick. I converted a statistics program I had... had to remake the main form as MonoDevelop does not appear to support Windows forms. The main statistics part of the class was all supported though.

---

### Post by wmcbrine on 2010-02-28
> **Lyerae said:**
> If I were to compile the code, would it compile it into an .exe which runs through Wine, or would it compile as a native program?Neither. C# compiles to byte code, which is interpreted at run time. It's like Java. The resulting ".NET assembly" gets named with ".exe" or ".dll", but it's not native code. Although apparently there's an option to generate native code, too.

[http://en.wikipedia.org/wiki/Common_Intermediate_Language](http://en.wikipedia.org/wiki/Common_Intermediate_Language)

I'm not a C# programmer myself, but this is my vague understanding.

cprofitt: [Mono](http://en.wikipedia.org/wiki/Mono_%28software%29) runs on pretty much everything, according to Wikipedia -- even Windows, if you want to be silly about it. :D

---

### Post by Lyerae on 2010-02-28
> C# compiles to byte code.

Yeah, my bad. I keep forgetting that. :D

Alright. Thanks guys. I think I figured out what I needed.

---

