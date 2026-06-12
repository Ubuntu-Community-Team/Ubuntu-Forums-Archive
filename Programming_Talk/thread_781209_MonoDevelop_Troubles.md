---
title: "MonoDevelop Troubles"
date: 2008-05-04
forum: Programming Talk
---

### Post by darkoz on 2008-05-04
Hi Ubuntu people,

I have been using Ubuntu exclusively at home for a few months now and while I am a ASP.NET web developer by profession have only recently installed Mono and MonoDevelop and gave ASP.NET development on Ubuntu a go.

Obviously I wouldn't be starting a thread had I not have encountered some problems (and searched for solutions on [www.justfuckingoogleit.com](www.justfuckingoogleit.com)) so here goes:

1) Syntax highlighting for aspx and config files doesn't work. As in all the text is the default black colour. I don't even know where to start with this, but I would have thought that MonoDevelop would have an easy way of adding schemes.

2) I am unsure how the code completion is supposed to work. It works fine on a "." character bringing up the expected stuff, however nothing when i start a new line (works if forced with Ctrl-Space). Does anyone know if this is intended functionality? If not any pointers on how to fix it?

3) Code completion doesnt work at all in aspx or config files. Again is this intended or is my install broken? Any tips would be welcome.

Any help would be muchly appreciated.

Darko

---

### Post by LaRoza on 2008-05-04
> **darkoz said:**
> ...

"ASP" and ".NET" are very closely tied to Windows. I do recommend using Windows and Windows tools for such development.

---

### Post by darkoz on 2008-05-04
Thank you for responding LaRoza, I am aware that the best tools are currently on Windows since this is what I do as a day job. However as I have a choice of what tools to use at home, I would rather stick to trying to make MonoDevelop work for me.

---

### Post by LaRoza on 2008-05-04
> **darkoz said:**
> Thank you for responding LaRoza, I am aware that the best tools are currently on Windows since this is what I do as a day job. However as I have a choice of what tools to use at home, I would rather stick to trying to make MonoDevelop work for me.

If this is for personaly use, you might want to look at more native Linux solutions.

I hope it works out, I don't know how MonoDevelop works, so I can't help with that much.

---

### Post by sakabato on 2008-05-05
> **LaRoza said:**
> "ASP" and ".NET" are very closely tied to Windows. I do recommend using Windows and Windows tools for such development.


This is completely incorrect for ASP.NET. Current status of ASP.NET on linux is very complete and promising. Practically everything works including ajax except WebParts as of Mono 1.9.1+. Secondly ASP!=ASP.NET. They are very different. For windows forms, you can definitely develop applications with windows forms on linux. However, windows forms is a bit immature for my taste. Here's some sophisticated windows forms applications that runs (or partially runs on linux) : NUnit-GUI, NCLass, Pain.NET, Reflector

I had developed a medium scaled application on asp.net using following technologies: ASP.NET Ajax, Ajax Control Toolkit, NUnit, Rhino Mocks, Log4net, Postgresql, NHibernate , CastleWindsor  on MonoDevelop and successfully ported to windows without a glitch (minor corrections was necessary).

---

### Post by LaRoza on 2008-05-05
> **sakabato said:**
> This is completely incorrect for ASP.NET. Current status of ASP.NET on linux is very complete and promising. Practically everything works including ajax except WebParts as of Mono 1.9.1+. Secondly ASP!=ASP.NET. They are very different. For windows forms, you can definitely develop applications with windows forms on linux. However, windows forms is a bit immature for my taste. Here's some sophisticated windows forms applications that runs (or partially runs on linux) : NUnit-GUI, NCLass, Pain.NET, Reflector

I had developed a medium scaled application on asp.net using following technologies: ASP.NET Ajax, Ajax Control Toolkit, NUnit, Rhino Mocks, Log4net, Postgresql, NHibernate , CastleWindsor  on MonoDevelop and successfully ported to windows without a glitch (minor corrections was necessary).

No, it is correct. Active Server Pages and .NET were designed for Windows and that is where they are almost always used. I know ASP != ASP.NET. I didn't say otherwise.

I never said it was impossible, or even hard.

I have ported PHP scripts to Windows with no modification or minor corrections.

---

