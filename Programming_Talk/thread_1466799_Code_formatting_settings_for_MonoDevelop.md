---
title: "Code formatting settings for MonoDevelop"
date: 2010-04-30
forum: Programming Talk
---

### Post by marshall.robert on 2010-04-30
Hi all.

I've recently picked up the C# language and have been using it on Windows exclusively (due to no Linux install 'til yesterday). I decided to install MonoDevelop and give that a go. All is good except that it automatically formats code (as seen in Visual Studio).

The problem here is; I can't seem to find settings to change the way it formats the code. This is annoying because there is too much white space, and opening braces don't deserve their own line!

Thanks
Rob

---

### Post by phrostbyte on 2010-04-30
I find that a little funny since the Mono style guidelines talk about just that: [http://www.mono-project.com/Coding_Guidelines](http://www.mono-project.com/Coding_Guidelines)

I'll let you know if I figure out a way to fix this myself.

---

### Post by marshall.robert on 2010-04-30
Ok, I found a work around, albeit a bit inconvenient, using a thing called *astyle*.

Found an article [here]("http://dustinbreese.blogspot.com/2008/09/auto-formatting-code-in-monodevelop-10.html"), that is written for MonoDevelop 1 but works on 2, that tells you how to set it up.
[URL="http://astyle.sourceforge.net/"]
Here is the website for Astyle.[/URL] It tells you how to set up the formatting and stuff.

On a more of a ranting note; there is soo much wrong with that article, no article should ever tell someone how to lay out their code in terms of "good" and "bad", nor should it be enforced in the IDE. No IDE will tell me how to format my code!

---

### Post by soltanis on 2010-04-30
> No IDE will tell me how to format my code!

I take it you don't like Java.

---

### Post by Queue29 on 2010-04-30
> **soltanis said:**
> I take it you don't like Java.

Java will let you format your code however you like. You can make your entire project on one line if you want to.

Something like Python or Go on the other hand actually enforces coding style.

---

