---
title: "C#"
date: 2008-06-09
forum: Programming Talk
---

### Post by sdmike on 2008-06-09
So I've been used to programming C# with Visual Studio 2008.

Is there something better than that, that I can use on Ubuntu? 

Also is anyone working on any C# projects that they need help on because I need the practice? :)

~Curious Mike

---

### Post by regomodo on 2008-06-09
> **sdmike said:**
> 

Also is anyone working on any C# projects that they need help on because I need the practice? :)

~Curious Mike

Read back through this subforum. There are apparently a lot.
Visualstudio replacement? Trolltech's Qt perhaps. That's c++ best with c++ i believe.

---

### Post by LaRoza on 2008-06-09
> **sdmike said:**
> So I've been used to programming C# with Visual Studio 2008.

Is there something better than that, that I can use on Ubuntu? 



C# can be used on Linux, but it isn't that big. 

There are a lot of "better" things, see my site and the stickies.

---

### Post by jespdj on 2008-06-09
Try [MonoDevelop]("http://www.monodevelop.com/Main_Page") if you're looking for a good IDE for C# on Ubuntu.

---

### Post by Lau_of_DK on 2008-06-09
> **sdmike said:**
> So I've been used to programming C# with Visual Studio 2008.

Is there something better than that, that I can use on Ubuntu? 

Also is anyone working on any C# projects that they need help on because I need the practice? :)

~Curious Mike

Coming from a similar background I would recommend you to read through this site: [clojure.org]("http://www.clojure.org") and perhaps watch a few of these videos: [SICP]("http://www.google.dk/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fswiss.csail.mit.edu%2Fclasses%2F6.001%2Fabelson-sussman-lectures%2F&ei=I5dNSPcdkKDWBvmKhb4E&usg=AFQjCNFfNpYTmn-iEKExE6oDckzNY1L_NA&sig2=a4HdZg_NT5P1fWlMdCGa4Q")

If you really get into this, its hard to let go of :)

/Lau

---

### Post by xlinuks on 2008-06-09
I tried MonoDevelop just of curiosity, perhaps it's the best one on Linux for C# code (not for other languages though), but it's pathetic in features and their quality, it managed to freeze the first time I started it, IMHO it's an editor rather than IDE. It's several years behind Eclipse, not to mention Visual Studio :)
So please don't judge Linux by the MonoDevelop "IDE", not everything in Linux is of "such quality" :)

---

### Post by kragen on 2008-06-09
Your not going to find an IDE on par with Visual Studio I'm afraid, if you really cant live without it then it runs very well with VirtualBox as long as you can spare it about 1GB of ram.

For C# development on Linux you need to look at Mono.

---

### Post by descendency on 2008-06-09
No. For C# development, there is nothing on par with VS. It's an amazing IDE. Intellisense alone is a reason to use it. 

For other languages, however, there are good alternatives to VS.

> **kragen said:**
> For C# development on Linux you need to look at Mono.

Mono is decent, but it still is lacking.

---

### Post by LaRoza on 2008-06-10
> **descendency said:**
> 
Mono is decent, but it still is lacking.

If a language is judged by the tools it has available, it shows something is wrong with the language.

---

### Post by sowelie on 2008-06-10
How is Visual Studio an amazing IDE?  Sure, it has good "intellisense" but it's slow, clunky, and still pretty buggy!  I haven't tried 2008 yet, but 2005 is pretty poor I think.

I would recommend using Eclipse to work with mono / C#.  Here's an article describing how to do so:

[http://www.gotmono.com/docs/ide/eclipse.html]("http://www.gotmono.com/docs/ide/eclipse.html")

EDIT:

I found an even better plugin for eclipse, works with nant / mono.

Check it out here:

[http://emonic.sourceforge.net/]("http://emonic.sourceforge.net/")

I have installed it and it works great.  Make sure to install nant (sudo aptitude install nant).

---

