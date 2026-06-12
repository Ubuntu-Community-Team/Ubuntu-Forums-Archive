---
title: "Mono 2.4 on Jaunty"
date: 2009-07-21
forum: Programming Talk
---

### Post by hardskinone on 2009-07-21
Hi,
 there is a way to apt-get mono-2.4 in Jaunty? The mono-testing PPA seems broke in xsp2 package. I would like to avoid to get crazy with sources.

Thanks.

---

### Post by hardskinone on 2009-07-21
[https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)

---

### Post by directhex on 2009-07-21
That reminds me, I still haven't uploaded mod-mono have I

---

### Post by hardskinone on 2009-07-21
In monoxide where can I get System.Web >= 3.0 ?

---

### Post by directhex on 2009-07-21
> **hardskinone said:**
> In monoxide where can I get System.Web >= 3.0 ?

Hm? What's the EXACT assembly reference you're trying to fulfill? AFAIK There's no such thing - System.Web is part of the 2.0 library set. Remember that Microsoft.NET 3.0 and 3.5 are just add-ons for 2.0

---

### Post by hardskinone on 2009-07-21
> **directhex said:**
> Hm? What's the EXACT assembly reference you're trying to fulfill? AFAIK There's no such thing - System.Web is part of the 2.0 library set. Remember that Microsoft.NET 3.0 and 3.5 are just add-ons for 2.0

I have a piece of code that requires HttpResponse.Header field which is available, as stated on MSDN[0] only on .NET 3.5. In 2.0 there is no Header field.

I suppose there is a 3.0 version for that assembly.

[0] [http://msdn.microsoft.com/it-it/library/system.web.httpresponse_members%28VS.80%29.aspx](http://msdn.microsoft.com/it-it/library/system.web.httpresponse_members%28VS.80%29.aspx)

---

### Post by directhex on 2009-07-21
> **hardskinone said:**
> I have a piece of code that requires HttpResponse.Header field which is available, as stated on MSDN[0] only on .NET 3.5. In 2.0 there is no Header field.

I suppose there is a 3.0 version for that assembly.

[0] [http://msdn.microsoft.com/it-it/library/system.web.httpresponse_members%28VS.80%29.aspx](http://msdn.microsoft.com/it-it/library/system.web.httpresponse_members%28VS.80%29.aspx)

If you've got an assembly, can you give me "monodis --assemblyref myassembly.dll" on it?

---

### Post by directhex on 2009-07-21
"This property supports the ASP.NET infrastructure and is not intended to be used directly from your code. "

i.e. if your app uses Headers, that's a bug. Headers is only visible because Microsoft are thick and don't know how to follow the spec properly

---

### Post by hardskinone on 2009-07-22
> **directhex said:**
> If you've got an assembly, can you give me "monodis --assemblyref myassembly.dll" on it?

```
AssemblyRef Table
1: Version=2.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=2.0.0.0
	Name=System.Configuration
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 
3: Version=0.4.0.0
	Name=Wok.Core
	Flags=0x00000000
	Zero sized public key
4: Version=2.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
5: Version=2.0.0.0
	Name=System.Web
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 
6: Version=0.3.0.0
	Name=Roar
	Flags=0x00000000
	Zero sized public key

```

---

### Post by directhex on 2009-07-22
> **hardskinone said:**
> ```

5: Version=2.0.0.0
	Name=System.Web
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 

```

Yeah, see, they're mandating System.Web 2.0

Headers should be internal, not public. Using it is convenient - but a violation of the spec.

---

