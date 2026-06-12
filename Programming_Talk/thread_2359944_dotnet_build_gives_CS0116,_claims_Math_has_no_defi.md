---
title: "dotnet build gives CS0116, claims Math has no definition for DivRem"
date: 2017-04-29
forum: Programming Talk
---

### Post by jamesjones01 on 2017-04-29
I'm grinding through the exercism.io C# exercises, and in one I'm working on now, I have occasion to use Math.DivRem (C#'s equivalent of the C div() function or Haskell's divMod). Looking at MS's page on the method, [https://msdn.microsoft.com/en-us/library/yda5c8dx.aspx](https://msdn.microsoft.com/en-us/library/yda5c8dx.aspx), it's in the System namespace, so "using System;" should suffice to make it available... but despite having that directive, when I try to compile I get the error message

[FONT=monospace][COLOR=#FF5454]PythagoreanTriplet.cs(62,22): error CS0117: 'Math' does not contain a definitio[/COLOR]n for 'DivRem' [/home/jejones/exercism/csharp/pythagorean-triplet/PythagoreanTriplet.csproj]

I've used methods in Math in earlier exercises with no problem; what is different about DivRem?

I'm using Ubuntu 17.04. Relevant packages:

[/FONT][FONT=monospace][COLOR=#ff5454]dotnet-dev-1.0.1, version 1.0.1-1
dotnet-host, version 1.1.0-preview1-001100-00-1
dotnet-hostfxr-1.1.0, version 1.1.0-1
dotnet-sharedframework-microsoft.netcore.app-1.1.1, version 1.1.1-1[/COLOR][/FONT]

---

### Post by MikeCyber on 2017-05-02
Maybe like me you need to install stuff:
[http://www.mono-project.com/docs/getting-started/install/linux/#debian-ubuntu-and-derivatives](http://www.mono-project.com/docs/getting-started/install/linux/#debian-ubuntu-and-derivatives)
then install as described in the usage section.

---

