---
title: "Mono &amp; VB.NET"
date: 2009-01-09
forum: Programming Talk
---

### Post by elziko on 2009-01-09
I am invesigating the possibilities of running .NET Framework applications on operating systems other than Windows. I'm new to Linux and have chosen Ubuntu v8.1 for my initial testing as I understand it come with Mono installed as standard.

I'm trying to run VB.NET applications written on VS2008 on Windows.

I have got as far as running a "Hello World" console application and then after doing:

sudo apt-get install mono-winforms*

I was able to get a "Hello World" C# WinForms applciation working. However I am unable to get a VB.NET WinForms application running - I get:

Could not load file or assembly 'Microsoft.VisualBasic

So, I understand that Ubuntu doesn;t contain the Microsoft.VisualBasic package that Mono needs.

I then Googled and found a packagfe for this here:

[http://fr2.rpmfind.net//linux/RPM/opensuse/10.3/noarch/mono-basic-1.2.5-15.noarch.html](http://fr2.rpmfind.net//linux/RPM/opensuse/10.3/noarch/mono-basic-1.2.5-15.noarch.html)

I installed 'alien', generated a .deb file from the .rpm file before doing a:

sudo dpkg -i mono-basic_1.2.5-16_all.deb

The terminal then reports:

Setting up mono-basic (1.2.5-16) ...

...and then goes back to the normal prompt. At this point I assume that the Microsoft.VisualBasic runtimes are installed but I still get the same "Could not load file or assembly 'Microsoft.VisualBasic" error.

Can any one help me - what am I doing wrong?

Thanks!

---

### Post by directhex on 2009-01-09
> **elziko said:**
> I am invesigating the possibilities of running .NET Framework applications on operating systems other than Windows. I'm new to Linux and have chosen Ubuntu v8.1 for my initial testing as I understand it come with Mono installed as standard.

I'm trying to run VB.NET applications written on VS2008 on Windows.

I have got as far as running a "Hello World" console application and then after doing:

sudo apt-get install mono-winforms*

I was able to get a "Hello World" C# WinForms applciation working. However I am unable to get a VB.NET WinForms application running - I get:

Could not load file or assembly 'Microsoft.VisualBasic

So, I understand that Ubuntu doesn;t contain the Microsoft.VisualBasic package that Mono needs.

I then Googled and found a packagfe for this here:

[http://fr2.rpmfind.net//linux/RPM/opensuse/10.3/noarch/mono-basic-1.2.5-15.noarch.html](http://fr2.rpmfind.net//linux/RPM/opensuse/10.3/noarch/mono-basic-1.2.5-15.noarch.html)

I installed 'alien', generated a .deb file from the .rpm file before doing a:

sudo dpkg -i mono-basic_1.2.5-16_all.deb

The terminal then reports:

Setting up mono-basic (1.2.5-16) ...

...and then goes back to the normal prompt. At this point I assume that the Microsoft.VisualBasic runtimes are installed but I still get the same "Could not load file or assembly 'Microsoft.VisualBasic" error.

Can any one help me - what am I doing wrong?

Thanks!

Never use Alien. It rarely works - and certainly not with Mono packages.

Remove what you installed, and install [http://directhex.mfgames.com/pool/main/m/mono-basic/libmono-microsoft-visualbasic8.0-cil_2.0+dfsg-1~dhx1_all.deb](http://directhex.mfgames.com/pool/main/m/mono-basic/libmono-microsoft-visualbasic8.0-cil_2.0+dfsg-1~dhx1_all.deb)

---

### Post by elziko on 2009-01-09
> **directhex said:**
> Never use Alien. It rarely works - and certainly not with Mono packages.

Remove what you installed, and install [http://directhex.mfgames.com/pool/main/m/mono-basic/libmono-microsoft-visualbasic8.0-cil_2.0+dfsg-1~dhx1_all.deb](http://directhex.mfgames.com/pool/main/m/mono-basic/libmono-microsoft-visualbasic8.0-cil_2.0+dfsg-1~dhx1_all.deb)

Thanks very much, it's all working now!

---

