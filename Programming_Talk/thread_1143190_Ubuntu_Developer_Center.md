---
title: "Ubuntu Developer Center"
date: 2009-04-29
forum: Programming Talk
---

### Post by NoBugs! on 2009-04-29
I notice there is a Microsoft Developer Network site, there is an Apple developer center web site, I was curious, is there an official Ubuntu/Linux developer center on the web?

---

### Post by kostkon on 2009-04-29
Check [here]("https://wiki.ubuntu.com/UbuntuDevelopment").

---

### Post by soltanis on 2009-04-30
kernel.org ? gnu.org ? debian.org ? There is no one set of developers/maintainers for Linux-based systems. First of all, you have the deal with all the distributions. Even if you focus on a single distribution (say Ubuntu), the software is written by a huge conglomeration of different people (lots of independent coders, some affiliated with projects, some affiliated with academic/research institutions, some not affiliated at all) who don't necessarily get together in the interests of interoperability but somehow get by on the loose standards prevalent in the distro.

Unfortunately, more than once developers from different projects have criticized each other's programs, coding practices, licenses, or paradigms, so getting all of them together wouldn't be so easy.

---

### Post by samjh on 2009-04-30
> **NoBugs! said:**
> I notice there is a Microsoft Developer Network site, there is an Apple developer center web site, I was curious, is there an official Ubuntu/Linux developer center on the web?

Websites such as MSDN are promotional portals, rather than development resources.  Their development resources such as documentation, tutorials, or discussion forums, only exist as far as it aids promotion of Microsoft's products.

Because Linux or the open source community doesn't have one set of products to promote, there isn't a single, all-encompassing portal for developers.

Some significant development portals for Linux-related projects include:
Gnome Live: [http://live.gnome.org/](http://live.gnome.org/)
KDE Techbase: [http://techbase.kde.org/Welcome_to_KDE_TechBase](http://techbase.kde.org/Welcome_to_KDE_TechBase)
Freedesktop.org: [http://www.freedesktop.org/wiki/Software](http://www.freedesktop.org/wiki/Software)
Linux Standard Base: [http://www.linuxfoundation.org/collaborate/workgroups/lsb](http://www.linuxfoundation.org/collaborate/workgroups/lsb)
Linux Kernel: [http://www.kernel.org/](http://www.kernel.org/)
...among other websites by distributions for their specific needs.

---

### Post by JReagan1990 on 2009-05-20
I have actually put out a plan for an Ubuntu Developer Network (aka UDN).  You can see the Brainstorm idea here:

[http://brainstorm.ubuntu.com/idea/18100/](http://brainstorm.ubuntu.com/idea/18100/)

I have also written a plan, located here:

[http://docs.google.com/Doc?id=dfdw2zz6_155gdk646df](http://docs.google.com/Doc?id=dfdw2zz6_155gdk646df)

...and a Launchpad blueprint, located here:

[https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-developer-network](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-developer-network)

This has been something I have wanted to work on for some time.  If you've ever been through the wiki, it's a pain in the neck.  I wanted something where we can teach people to develop applications ON Ubuntu FOR Ubuntu.

Here's a simple mockup:

[IMG]http://jonreagan.files.wordpress.com/2009/02/udn3.jpg[/IMG]

---

### Post by trivialpackets on 2009-05-20
Not too shabby, I like the idea everyone, I'm now reading the plan.

---

### Post by trivialpackets on 2009-05-20
VB, for what it's worth was golden in it's original creation and intent.  It allowed people without formal training to create small apps for their PC's.  They could then begin to get familiar with the tools, and when they got "all grown up", they developed for Windows.  I think that making this a centralized resource is a terrific idea and I fully support it.

---

### Post by samjh on 2009-05-20
Why restrict it to Ubuntu?  If the aim is to create an MSDN-like service, it should serve Linux developers at large, not just Ubuntu.

---

### Post by JReagan1990 on 2009-05-21
As a matter of fact, UDN will be in the works soon, so hang on.  The purpose is to help with Ubuntu programming, not Linux in general.  I'm honestly not interested in the rest of Linux, because there is the LDN.  We need something to support Ubuntu, Linux will take care of itself.  However, an Ubuntu Developer Network might help create more Linux devs... either way it will be good for Ubuntu. :)

---

### Post by Simian Man on 2009-05-21
> **JReagan1990 said:**
> As a matter of fact, UDN will be in the works soon, so hang on.  The purpose is to help with Ubuntu programming, not Linux in general.  I'm honestly not interested in the rest of Linux, because there is the LDN.  We need something to support Ubuntu, Linux will take care of itself.  However, an Ubuntu Developer Network might help create more Linux devs... either way it will be good for Ubuntu. :)

But Ubuntu is just a type of Linux.  Honestly 99% of "Ubuntu programming" content will have *nothing* to do with your distribution of choice.  How does using Python or SDL or bash depend on your distribution?  The only thing I can think of is installing the tools, but that is such a ridiculously small portion of development that you could just have instructions for the top couple distros and let others figure it out on their own.

I know people here are so enamoured with Ubuntu that they try to steal mindshare away from Linux in general, but this is just ridiculous.

---

### Post by cl333r on 2009-05-21
> **samjh said:**
> 
Websites such as MSDN are promotional portals, rather than development resources. Their development resources such as documentation, tutorials, or discussion forums, only exist as far as it aids promotion of Microsoft's products.

Because Linux or the open source community doesn't have one set of products to promote, there isn't a single, all-encompassing portal for developers.

aha, and the sad thing is that many Linux users would defend such lack of unity as a virtue, backing this reason up with half truths, pure fantasies, using the 'fud' catchword and reasons like 'it's not windows' and in turn make the other hamsters hit the pedal, the psychology of the masses.

---

### Post by samjh on 2009-05-21
> **cl333r said:**
> aha, and the sad thing is that many Linux users would defend such lack of unity as a virtue, backing this reason up with half truths, pure fantasies, using the 'fud' catchword and reasons like 'it's not windows' and in turn make the other hamsters hit the pedal, the psychology of the masses.

I'm not sure that "lack of unity" is the thing some people might defend.  Rather, the unfortunate reality of developing for Linux is that the various frameworks and APIs are created mostly by many independent individuals or groups.  The logistics of collating authoritative, comprehensive, and up-to-date information about all the separately-developed APIs, frameworks, and tools, is huge.

Microsoft has an easy time, because Windows development is dominated by Microsoft's products: .NET Framework, Win32, Win64, Visual Studio, etc.  Who better to collate and present such information than Microsoft?  The same ability simply does not exist for Linux.  LDN is a worthy effort, but cannot be compared with breadth and depth of MSDN.

I'd personally love to see something for Linux to rival MSDN, but I can't see how it can be possible without a titanic attitude change in the entire Linux software ecosystem.

---

