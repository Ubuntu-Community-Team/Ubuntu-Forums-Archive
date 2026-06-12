---
title: "opinions on c# &amp; mono"
date: 2011-03-17
forum: Programming Talk
---

### Post by might and power on 2011-03-17
hi all, 

i am thinking about doing some linux/ubuntu programming. nothing major just some utility programs and some format converters.
 
  i was just wondering what ubuntu users and developers think of c# and the mono platform? i have read a few blogs where some people say they flat out wont use mono. is this common? 

i ask because c# is the language im most comfortable in. naturally i could us java but it's much inferior to c# imo. I can program in c++ too but id rather not.

---

### Post by Thund3rstruck on 2011-03-17
> **might and power said:**
> hi all, i am thinking about doing some linux/ubuntu programming. nothing major just some utility programs and some format converters.
 
  i was just wondering what ubuntu users and developers think of c# and the mono platform? i have read a few blogs where some people say they flat out wont use mooo. is this common? 

i ask because c# is the language im most comfortable in. naturally i could us java but its much inferior to c# imo.I can program in c++ if too be but id rather not.

I'm a professional C# (ASP.NET & Win32) programmer and I have been down this road several times without success. I have personally had a horrible experience with Mono (Eclipse IDE). The editor consistently crashed every 15 minutes and it was absolutely unusable. 

Of course I'm used to Visual Studio and MSDN and after 40 hours or so I decided to stick with Windows for enterprise development and use bash scripting for Linux automation. 

Its been a few years since the last time I tried Mono so things may have improved in this time but my experience was so poor the last time that I pretty much gave up on the idea of cross plat development with .NET. 

Just my $.02

---

### Post by directhex on 2011-03-17
> **Thund3rstruck said:**
> I'm a professional C# (ASP.NET & Win32) programmer and I have been down this road several times without success. I have personally had a horrible experience with Mono (Eclipse IDE). The editor consistently crashed every 15 minutes and it was absolutely unusable.

Um, that's Eclipse. Which is a showcase app for Java. Nobody in their right mind uses Eclipse for C#.[/QUOTE]

---

### Post by directhex on 2011-03-17
> **might and power said:**
> hi all, i am thinking about doing some linux/ubuntu programming. nothing major just some utility programs and some format converters.
 
  i was just wondering what ubuntu users and developers think of c# and the mono platform? i have read a few blogs where some people say they flat out wont use mooo. is this common? 

i ask because c# is the language im most comfortable in. naturally i could us java but its much inferior to c# imo.I can program in c++ if too be but id rather not.

Click Applications, Accessories. See Tomboy Notes? That's a Mono app in C#.

Click Applications, Games, Logic. See gbrainy? That's a Mono app in C#.

Click Applications, Sound & Video. See Banshee Media Player? That's a Mono app in C#.

So is it a reasonable choice? Yes. Are there people using it? Yes. Are there some who refuse to use it? Yes.

Use what you want, tbh.

---

### Post by might and power on 2011-03-17
> **Thund3rstruck said:**
> I'm a professional C# (ASP.NET & Win32) programmer and I have been down this road several times without success. I have personally had a horrible experience with Mono (Eclipse IDE). The editor consistently crashed every 15 minutes and it was absolutely unusable. 

Of course I'm used to Visual Studio and MSDN and after 40 hours or so I decided to stick with Windows for enterprise development and use bash scripting for Linux automation. 

Its been a few years since the last time I tried Mono so things may have improved in this time but my experience was so poor the last time that I pretty much gave up on the idea of cross plat development with .NET. 

Just my $.02


thanks. 

yeah i hadn't even begun to think about tooling, but that is a very relevant issue. i have used eclipse on windows for java and c++ development and never found it very good. 

if its just a matter of tooling you could presumably write programs in visual studio on windows targeting .net 2.0 (or whatever is the latest runtime supported by ubuntu) and simply deploy it on linux? is .net code portable to that extent?

---

### Post by might and power on 2011-03-17
> **directhex said:**
> Click Applications, Accessories. See Tomboy Notes? That's a Mono app in C#.

Click Applications, Games, Logic. See gbrainy? That's a Mono app in C#.

Click Applications, Sound & Video. See Banshee Media Player? That's a Mono app in C#.

So is it a reasonable choice? Yes. Are there people using it? Yes. Are there some who refuse to use it? Yes.

Use what you want, tbh.

im running windows 7 so i cant do any of those things heh. but it's cool i get that your point is rhetorical. ;)

---

### Post by Simian Man on 2011-03-17
> **might and power said:**
> yeah i hadn't even begun to think about tooling, but that is a very relevant issue. i have used eclipse on windows for java and c++ development and never found it very good. 

if its just a matter of tooling you could presumably write programs in visual studio on windows targeting .net 2.0 (or whatever is the latest runtime supported by ubuntu) and simply deploy it on linux? is .net code portable to that extent?

.NET code is portable to that extent, but the libraries you use may not be.  For developing on Linux, there is MonoDevelop, which is quite a good IDE, though it doesn't have all the features of Visual Studio.

I recommend C# and Mono on Linux, especially if you are already confortable with the language.

---

### Post by forrestcupp on 2011-03-17
> **directhex said:**
> Um, that's Eclipse. Which is a showcase app for Java. Nobody in their right mind uses Eclipse for C#.+1
It's too bad your experience was tainted by using the wrong IDE.

> **might and power said:**
> i have used eclipse on windows for java and c++ development and never found it very good.

Eclipse is a pain in the rear to set up properly, but in my opinion, once it's set up it's a lot better than Netbeans for Java.

Like Simian Man said, you'll have to be mindful of your libraries. I've never messed with Mono, always straight .Net. But if I remember correctly, they had to implement their own version of Windows.Forms, and I'm not sure if the code lines up perfectly or not.

---

### Post by directhex on 2011-03-17
> **forrestcupp said:**
> Like Simian Man said, you'll have to be mindful of your libraries. I've never messed with Mono, always straight .Net. But if I remember correctly, they had to implement their own version of Windows.Forms, and I'm not sure if the code lines up perfectly or not.

Forms looks like ***. It's a badly designed, pixel-layout toolkit. Don't use it.

---

### Post by Thund3rstruck on 2011-03-17
> **forrestcupp said:**
> +1
It's too bad your experience was tainted by using the wrong IDE.

I'm more than willing to give it another go. I used Eclipse (with the .NET plugins) because that's what the Novell engineers demonstrated to my team the week they came in to instruct a seminar on how we could engineer our .NET solutions for Suse clients. 

Please suggest an appropriate IDE and I will investigate.

---

### Post by ve4cib on 2011-03-17
> **Thund3rstruck said:**
> Please suggest an appropriate IDE and I will investigate.

MonoDevelop is probably the best Mono IDE out there.  It's not as good as VS, but it certainly gets the job done.

Conveniently you can also install it on Windows, and it comes with GTK#, so you can develop GUIs for Linux while working under Windows and vice versa.

---

### Post by fuduntu on 2011-03-17
> **might and power said:**
> hi all, 

i am thinking about doing some linux/ubuntu programming. nothing major just some utility programs and some format converters.
 
  i was just wondering what ubuntu users and developers think of c# and the mono platform? i have read a few blogs where some people say they flat out wont use mono. is this common? 

i ask because c# is the language im most comfortable in. naturally i could us java but it's much inferior to c# imo. I can program in c++ too but id rather not.


I'm a fan.  I write utilities in C#, some for Linux some for Windows (though nothing there in recent years).  I would say use the language you are comfortable with, and ignore the naysayers.

---

### Post by fuduntu on 2011-03-17
> **directhex said:**
> Forms looks like ***. It's a badly designed, pixel-layout toolkit. Don't use it.

using Gtk;
using Gdk;

:p

---

