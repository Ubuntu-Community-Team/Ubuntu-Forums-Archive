---
title: "Running .NET Applications"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by AlistairH on 2008-06-22
I have a number of .NET based Windows apps that I'd like to run under Linux. The will not load in wine, referring to missing .NET libraries.

I've heard of something called 'Mono' which allows Linux users to develop .NET applications. I'm not interested in developing apps, just running them under Linux.

Has any one successfully done this? If Mono is installed to run .NET, is Wine required as well?

Thanks in anticipation.

Alistair

---

### Post by fahadsadah on 2008-06-22
You should install the package mono-runtime to run .Net programs **compiled on Linux**! (no wine required)
If you only have a Windows version, you could decompile this with ILDASM, and reassemble it on Ubuntu with ILASM (program can't be copyrighted). This will require the full mono package.

---

### Post by WitchCraft on 2008-06-22
> **AlistairH said:**
> I have a number of .NET based Windows apps that I'd like to run under Linux. The will not load in wine, referring to missing .NET libraries.

I've heard of something called 'Mono' which allows Linux users to develop .NET applications. I'm not interested in developing apps, just running them under Linux.

Has any one successfully done this? If Mono is installed to run .NET, is Wine required as well?

Thanks in anticipation.

Alistair


[http://dn.codegear.com/article/32056](http://dn.codegear.com/article/32056)

---

### Post by AlistairH on 2008-06-22
> **fahadsadah said:**
> You should install the package mono-runtime to run .Net programs **compiled on Linux**! (no wine required)
If you only have a Windows version, you could decompile this with ILDASM, and reassemble it on Ubuntu with ILASM (program can't be copyrighted). This will require the full mono package.

It doesn't look like it's an option for me then as the applications I want to run are commercial, copyrighted programs and I certainly wouldn't want to get into decompiling/recompiling them for Linux (I wouldn't know where to start to be honest).

Thanks for getting back to me on that anyway.

As an afterthought, has there been any progress in getting .NET to install within a WINE environment does anyone know?

Alistair

---

