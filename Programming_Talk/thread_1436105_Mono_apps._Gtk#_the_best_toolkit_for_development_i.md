---
title: "Mono apps. Gtk# the best toolkit for development in Gnome."
date: 2010-03-22
forum: Programming Talk
---

### Post by michaelmartin007 on 2010-03-22
OK
Nowaday is necessary to establish a rapid application development for apps in Gnome. Everyone knows that C is very expensive to maintain. It is expensive to create applications in C and develop features. The developers of KDE make it easy with Qt. They can implement many new features easyly. Python is very slow. Vala and Genie, today, are not up to it.
Vala and Genie would be the best, but developers need very good documentation and many tutorials. They need much promotion and support and time. But, maybe, is the future.
As a developer of apps in mono said "if someone makes an application better than someone made in mono, then, this one can replace de mono app one. The important thing is that Gnome can have the best applications."
That's right. For example, if Banshee is the best music player, it is good to replace Rhythmbox. Why not?
With the war agains mono the losers are going to be users of GNOME.
KDE has a magnificent Qt4 toolkit and framework. Whether we like it or not Gnome has a Gtk#. 
So says someone who had long been against mono.

---

### Post by SledgeHammer_999 on 2010-03-22
Or the Gtk/Gnome guys could switch to C++ instead of Vala or C# :P (I use gtkmm but I am not quite happy with it).

One recent example for "mono replacement" is Gnote instead of Tomboy.

Also many users would say that Amarok is the best music player out there for linux(I personally prefer exaile). But just keep in mind that if you use Gnome you don't have to use only Gtk+ apps. You can use Qt apps too(k3b anyone?). And vice versa.

---

### Post by zekopeko on 2010-03-22
> **SledgeHammer_999 said:**
> Or the Gtk/Gnome guys could switch to C++ instead of Vala or C# :P (I use gtkmm but I am not quite happy with it).

One recent example for "mono replacement" is Gnote instead of Tomboy.

There is only one problem with Gnote. Its always two steps behind Tomboy. You still can't sync with Ubuntu One/Snowy with Gnote and Gnote doesn't promise interoperability with Tomboy notes (there are no guarantees that importing Gnote created notes into Tomboy will work as intended).

> Also many users would say that Amarok is the best music player out there for linux(I personally prefer exaile). But just keep in mind that if you use Gnome you don't have to use only Gtk+ apps. You can use Qt apps too(k3b anyone?). And vice versa.

Amarok may be the best music player on KDE but take into consideration that even if KDE apps emulate GTK+ looks there are still huge differences in application design guidelines. A KDE app isn't going to fit into a Gnome environment since the design philosophies are different. KDE devs think that there should be a million option and a GUI for each one (this has gotten a lot saner/better in KDE4 but it is still present). Gnome devs are proponents of "less is more".

---

### Post by SledgeHammer_999 on 2010-03-22
I was just trying to say that:

Qt4 != KDE apps
Gtk+ != Gnome apps.

If a Gtk/Qt app doens't use Gnome/KDE facilities then it shouldn't be considered a Gnome/KDE app respectively. Just don't confuse the toolkits with the DE philosophy. I could make a Gtk app that had millions of options and make a GUI for them :P

---

### Post by michaelmartin007 on 2010-03-22
Yes, amarok is to much dependent on kde, it fit good for kde desktop but no with Gnome.
It is true too that gnote is behind Tomboy and has no features that Tomboy has. Mono, pygtk, vala, gtk+... We need mono apps and we need mono devs. You can think, for example, in evolution. It is writing in C and it has a large code base. It is hard to maintain. If evolution should be code with mono should be easier to maintain and code cleaner. By no means I say to code evolution with mono. Not at all. Only that maybe, nowaday, devs could have choosen gtk#.
We must consider only "the best app". We can consider features, integration with Gnome... and this independent of the programming language. For example, Banshee, integrate better with Gnome, has many features. Amarok doesn't integrate with the HIG of Gnome, install half kde (more o less)and, really, I don't think Amarok is better than Banshee. Anyway, in in future, we have a vala music player better or equal to Banshee we can replace it.

---

### Post by soltanis on 2010-03-22
Problem with Mono is that Microsoft has been holding a threat of suing over infringement of patents/copyrights (not sure which one, probably both), even though they ironically hold it up as an example of .NET interoperability.

Personally, I'm not a fan of having to install another framework on my system just to run some apps although it sure is easy with package managers. This kind of relates to a rant I posted in another thread about why there is no good open source rich media plugin for browsers (and hence we're stuck using Flash or equally worse, Silverlight).

Making "yet another framework" for everything means that we'll just have more frameworks, more fragmentation and no real agreement on anything. I'm not saying what we have is good, but I think you inordinately disparaged Python there -- first of all, it isn't that slow, second, speed is usually not even that important, and third, there are ways to make it faster.

---

### Post by zekopeko on 2010-03-22
> **soltanis said:**
> Problem with Mono is that Microsoft has been holding a threat of suing over infringement of patents/copyrights (not sure which one, probably both), even though they ironically hold it up as an example of .NET interoperability.

Not true. They have been doing quite the opposite.

> Personally, I'm not a fan of having to install another framework on my system just to run some apps although it sure is easy with package managers. This kind of relates to a rant I posted in another thread about why there is no good open source rich media plugin for browsers (and hence we're stuck using Flash or equally worse, Silverlight).

Sure there is. Moonlight is fully FOSS.

> Making "yet another framework" for everything means that we'll just have more frameworks, more fragmentation and no real agreement on anything. I'm not saying what we have is good, but I think you inordinately disparaged Python there -- first of all, it isn't that slow, second, speed is usually not even that important, and third, there are ways to make it faster.

Google tried to speedup python but I don't think they succeeded in reaching their goal of 5x speed improvement.

---

### Post by soltanis on 2010-03-22
[http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.E2.80.99s_patents](http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.E2.80.99s_patents)

I not so naive to say that the FSF has no underlying motive (or Stallman, I should say) for disliking Mono, but then again threatening not to sue Novell isn't exactly a very great promise. Unless you're using SuSE, this doesn't even apply to you, and even if you were, it hasn't been made very clear where Microsoft is drawing the line. They will of course keep it that way since it's in their interest to reserve the right to squash Mono if and when they choose.

Moonlight is like Mono in that it's liable to get quashed by Microsoft for patent infringement.

Besides optimizing the python interpreter there are other ways to attain speedups, which is writing math intensive code in C and gluing it to Python, or by using psyco or similar tools. My point is also that in my experience Python has been faster than say, Javascript, and yet how many people do you see creating web applications that revolve around that? Lot's of people criticize languages for being slow, and torture themselves with compiled languages as a result, for no real reason -- unless you're doing something like cryptography or encoding (which Python has libraries written in C for) then you seriously do not need that speed.

---

### Post by michaelmartin007 on 2010-03-22
> **soltanis said:**
> Problem with Mono is that Microsoft has been holding a threat of suing over infringement of patents/copyrights (not sure which one, probably both), even though they ironically hold it up as an example of .NET interoperability.


Making "yet another framework" for everything means that we'll just have more frameworks, more fragmentation and no real agreement on anything. I'm not saying what we have is good, but I think you inordinately disparaged Python there -- first of all, it isn't that slow, second, speed is usually not even that important, and third, there are ways to make it faster.

We are spending years with this matter. I think if someone know a library of mono that has a patent or copyright problem say it. Devs can make with this library what openjdk devs has make with libraries with copyright or patents. They can change that library or code a new one for replace.
We need to convince all users that we need a programming language of high level. Mono make coding far easier and code is cleaner, easier to maintain, easier to add new features.


What you say is true and very sad. Gnome is very fragmented and I think too that so it is difficult finding an agreement on anything. In Gnome we see as an advantage so many bindings but
sometimes I envy KDE. Think in it. KDE devs have all apps Qt4 c++. So, any dev can help in any of the apps of Kde. They know the code of any apps. Devs of KDE can help each other better
because all of them speak the same language (Qt4). They have a toolkit capable of anything.
Meanwhile we have gtk+ that it is needed to replace and devs know it. Yes, Google tried to speed up python and I am thinking if, maybe, they develop Go language programming language because they don't succede with other languages.
Genie should be a good language. Gnome devs like python and Genie
is closed in syntax but compiled and perform as good as C.
But apart of this, in the desktop apps we have mono in apps as Tomboy, F-spot, Banshee... all of them a very good apps and really gnome apps. Thanks to mono devs we have first class apps and they are gnome apps as pygtk or gtk+.

---

### Post by SledgeHammer_999 on 2010-03-22
Well I disagree. Language doesn't have to do much about the understanding of how a toolkit works. I have personally helped quite a few users here with issues with Gtk development. Most of them developed in python or C. I am using C++ and gtkmm but I was able to help them because I know how the toolkit works(in terms of concepts) regardless of a spedific language(and I don't know python). So to my humble opinion every potential developer should develop in whatever language he feels comfortable with. The two(or three) most important parts for Gtk to be even more accepted are these:
1. Better bindings
2. A hell of a lot better documentation with LOTS of code examples and concept examples for noob users.
3. Maybe a centralised point where knowledge is gathered(think wiki) and a centralised point about questions/problem solving(think official forum).

---

### Post by zekopeko on 2010-03-22
> **soltanis said:**
> [http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.E2.80.99s_patents](http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.E2.80.99s_patents)

I not so naive to say that the FSF has no underlying motive (or Stallman, I should say) for disliking Mono, but then again threatening not to sue Novell isn't exactly a very great promise. Unless you're using SuSE, this doesn't even apply to you, and even if you were, it hasn't been made very clear where Microsoft is drawing the line. They will of course keep it that way since it's in their interest to reserve the right to squash Mono if and when they choose.

Moonlight is like Mono in that it's liable to get quashed by Microsoft for patent infringement.

Not true. You have CP and OSP from MS which are legally binding. Its ironic but Mono has more legal protection around it against patent lawsuits then most major FOSS projects.

> Besides optimizing the python interpreter there are other ways to attain speedups, which is writing math intensive code in C and gluing it to Python, or by using psyco or similar tools. My point is also that in my experience Python has been faster than say, Javascript, and yet how many people do you see creating web applications that revolve around that? Lot's of people criticize languages for being slow, and torture themselves with compiled languages as a result, for no real reason -- unless you're doing something like cryptography or encoding (which Python has libraries written in C for) then you seriously do not need that speed.

I think Mono is filling an important part of the framework landscape. You aren't going to write the kernel in it (at least in the foreseeable future) but writing something like Evolution in it makes more sense.

---

