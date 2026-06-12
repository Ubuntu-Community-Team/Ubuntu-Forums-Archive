---
title: "Developing in Mono"
date: 2007-05-07
forum: Programming Talk
---

### Post by foresth on 2007-05-07
Hi,

I am very delighted with Mono and I am seriously thinking about developing in Mono. I also like C# but my question is if it is worth.

Do you think that Mono has a future?

I also wasn't able to find much resources about it. Far less than eg. about developing GNOME applications in Python and the official webpage ([www.mono-project.com](www.mono-project.com)) seems to be quite dead this time of year.

But again, I like the Mono way and I **personally** prefer C# over Python or C++ etc. concerning desktop development.

I'd appreciate your experienced insights.

Thanks.

---

### Post by skeeterbug on 2007-05-07
> **foresth said:**
> Hi,

I am very delighted with Mono and I am seriously thinking about developing in Mono. I also like C# but my question is if it is worth.

Do you think that Mono has a future?

I also wasn't able to find much resources about it. Far less than eg. about developing GNOME applications in Python and the official webpage ([www.mono-project.com](www.mono-project.com)) seems to be quite dead this time of year.

But again, I like the Mono way and I **personally** prefer C# over Python or C++ etc. concerning desktop development.

I'd appreciate your experienced insights.

Thanks.

Of course Mono has a future. It has already been around for years. Now it is backed and supported by a large company (Novell). C# is a great language and .NET is a great platform for development. It is very exciting that the open source community has embraced it.

---

### Post by foresth on 2007-05-08
Are there any Mono developers in this forum?

---

### Post by skeeterbug on 2007-05-08
> **foresth said:**
> Are there any Mono developers in this forum?

Other than test some of its features, no. We were going to build a GTK# application using Mono. We had the shell of the GUI starting to be built, some of our third party libs compiled and tested under Mono, and we found support for GTK# in Mac wasn't up to par. We ended up using Microsoft's CLR and made the application Windows only.

---

### Post by angelmartinezn on 2007-05-09
I think Mono will change (if hasn't already done it) the entire world of .NET, guess in a few years many web developments in asp/aspx will be done under unix/linux with mono as a framework. Gui app's also will lead us to a new vision (like swing in java)... all of this will be very, very interesting (almost for Micro$osft) for the linux - people...

Good luck,

Àngel.

---

### Post by twistedtwig on 2007-05-09
Sorry if this is hijacking the post or slightly off topic but I thought I would ask.....

does mono work in exactly the same way as .net?  I mean can you write anything for windows .net environment and run it instantly on mono?

Thanks

---

### Post by samjh on 2007-05-09
> **twistedtwig said:**
> Sorry if this is hijacking the post or slightly off topic but I thought I would ask.....

does mono work in exactly the same way as .net?  I mean can you write anything for windows .net environment and run it instantly on mono?

Thanks

No.  Check out the Mono website ([www.mono-project.com](www.mono-project.com)) and you will see that there are some .NET features that are either not yet implemented.

[http://www.mono-project.com/Roadmap](http://www.mono-project.com/Roadmap)

Most small to medium-sized .NET projects from Windows will run in Mono, but not all of them.

---

### Post by emperon on 2007-05-10
Here we are building a very complex ERP type application with mono on linux. Also the page may look in active, but the project it self is very very active. take a look at [http://www.go-mono.com/monologue/](http://www.go-mono.com/monologue/)

---

