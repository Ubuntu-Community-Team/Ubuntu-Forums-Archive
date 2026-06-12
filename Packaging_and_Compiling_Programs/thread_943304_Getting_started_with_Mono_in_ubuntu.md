---
title: "Getting started with Mono in ubuntu"
date: 2008-10-10
forum: Packaging and Compiling Programs
---

### Post by fballem on 2008-10-10
I see that Mono has released version 2.0. Since I am coming from a Microsoft world, I would be very interested in trying it out.

Could someone please tell me what I need to get started. I would like to get as close as possible to a Visual Studio experience, so I imagine that I will need a compiler, an IDE, and runtimes.

I am a relative newbie, so specific instructions would be very much appreciated.

Many thanks,

---

### Post by directhex on 2008-10-10
> **fballem said:**
> I see that Mono has released version 2.0. Since I am coming from a Microsoft world, I would be very interested in trying it out.

Could someone please tell me what I need to get started. I would like to get as close as possible to a Visual Studio experience, so I imagine that I will need a compiler, an IDE, and runtimes.

I am a relative newbie, so specific instructions would be very much appreciated.

Many thanks,

"monodevelop" is the IDE, including a visual designer (GTK#, which behaves differently to System.Windows.Forms, it's probably closer to designing HTML with a lot of <table> if that helps you visualise the use of VBox/HBox). The version in Ubuntu is unfortunately a little old.

"mono-gmcs" is the C# 2.0 compiler, as used by MonoDevelop. Install both.

If you need or want extra libs, all CLI libraries on Ubuntu have "cil" at the end of their names, so try "apt-cache search cil$"

---

### Post by fballem on 2008-10-11
> **directhex said:**
> "monodevelop" is the IDE, including a visual designer (GTK#, which behaves differently to System.Windows.Forms, it's probably closer to designing HTML with a lot of <table> if that helps you visualise the use of VBox/HBox). The version in Ubuntu is unfortunately a little old.

"mono-gmcs" is the C# 2.0 compiler, as used by MonoDevelop. Install both.

If you need or want extra libs, all CLI libraries on Ubuntu have "cil" at the end of their names, so try "apt-cache search cil$"

Thanks. Given how old the items in the repository are, do you know how to install mono and monodevelop from source? If you do, then could you please give me specific instructions?

Many thanks,

---

