---
title: "Beginning C Programming class...using Linux"
date: 2007-07-25
forum: Programming Talk
---

### Post by VChief on 2007-07-25
I'm taking Beginning C Programming this semester.I only have one quick question. Will I be able to write programs in Linux, run them, then be able to turn in that exact code and have it work on Windows for the instructor ok? Thank you.

---

### Post by mgoblue on 2007-07-25
If you just turn in the source code I'd imagine it'd be fine.  If you have to turn in a compiled program then absolutely not.

---

### Post by VChief on 2007-07-25
Sweet. I imagine I'll just have to turn the source code in so the professor can read it. That's how it was with my Java class. I just wasn't sure if there were differences for code between different OSes. Thanks.

---

### Post by Geekkit on 2007-07-25
> **leeward said:**
> I'm taking Beginning C Programming this semester.I only have one quick question. Will I be able to write programs in Linux, run them, then be able to turn in that exact code and have it work on Windows for the instructor ok? Thank you.

You need to ask your prof/instructor - not a bunch of people in the forum. If he/she isn't running Linux and you tie into some Linux specific call, you'll be taking a hit.

---

### Post by slavik on 2007-07-26
you'll be fine. it's an intro class, so no worries about platforms. :)

---

### Post by LaRoza on 2007-07-26
As long as you are using standard headers in your class, which you most likely will, I have had no trouble moving C code between Linux and Windows.

---

### Post by Wybiral on 2007-07-26
> **Geekkit said:**
> You need to ask your prof/instructor - not a bunch of people in the forum. If he/she isn't running Linux and you tie into some Linux specific call, you'll be taking a hit.

I've been using C for a while now and haven't ran into any portability problems. Just don't use functions like "system" or any platform specific headers.

But you'll probably be writing console apps the entire time, so it won't matter.

---

### Post by Soybean on 2007-07-26
Hmm... ideally, you'd probably want to test things in a Windows environment before handing them in, unless you talk with the prof first (a lot of CS profs are pretty supportive of Linux use). It's just that if they're expecting you to be using MSVC, you may run into trouble in some areas where MS.... uh... "interprets the standard differently" from GCC. I haven't used a recent version of MSVC, but there always used to be a few pitfalls like this, even in fairly simple code.

For example, in GCC, it's ok to define a variable anywhere in a function, as in
```

void foo()
{
	int a=3;
	printf("%d\n", a);
	[color=red]int b=7;[/color]
	printf("%d\n", b);
}

```

This is fairly innocuous, and it would compile without warning in GCC, but it would fail to compile in the last version of MSVC I used. It didn't even have a sensible error message.

---

### Post by LaRoza on 2007-07-26
You can run Dev-C++ in Wine and compile and run Windows programs in Linux.

Dev-C++ comes in an installation version, and a portable version, I use the portable version on my flash drive, and often run it in Linux.

The resulting program runs in Windows perfectly.

---

### Post by AnRa on 2007-07-26
You may cross-compile your code using [mingw32](http://packages.ubuntu.com/feisty/devel/mingw32). ;)

---

### Post by mgoblue on 2007-07-26
What I'd do is create your source in linux, and compile and test it on your computer.  Then go to a computer with a windows compiler and compile it there.

---

### Post by LaRoza on 2007-07-26
Dev-C++ will run in Linux under Wine, so you won't need to use Windows at all.

---

### Post by Wybiral on 2007-07-26
> **LaRoza said:**
> Dev-C++ will run in Linux under Wine, so you won't need to use Windows at all.

Dev-C++ uses GCC though... I think the thing they're worried about is MS-VC++ compatibility.

---

### Post by LaRoza on 2007-07-26
If it is Ansi C, it shouldn't matter, although I don't trust MS VS, so I can't say for sure.

Oh, the code that was posted above did compile in Dev-C++, so maybe it isn't the best for testing compatibility for incompatable MS programs. If you compile in Dev-C++, the .exe will run fine in Windows, so maybe it won't matter.

---

### Post by mgoblue on 2007-07-26
Best advice?  Ask your professor:)

---

### Post by VChief on 2007-07-27
Thanks for all the help. I did finally find out who the professor was and look up his page. My hopes got pretty high when I saw it. I like this guy. He also teaches all the Linux and Unix classes. His site was full of Linux and UNIX links and info. E-mailed him and got a reply back 30 minutes later. So, all is good. I'm thinking of taking his Advanced UNIX admin class too.

---

### Post by LaRoza on 2007-07-27
Cool, maybe you will get extra points for using Linux :D.

---

### Post by slavik on 2007-07-28
> **Soybean said:**
> Hmm... ideally, you'd probably want to test things in a Windows environment before handing them in, unless you talk with the prof first (a lot of CS profs are pretty supportive of Linux use). It's just that if they're expecting you to be using MSVC, you may run into trouble in some areas where MS.... uh... "interprets the standard differently" from GCC. I haven't used a recent version of MSVC, but there always used to be a few pitfalls like this, even in fairly simple code.

For example, in GCC, it's ok to define a variable anywhere in a function, as in
```

void foo()
{
	int a=3;
	printf("%d\n", a);
	[color=red]int b=7;[/color]
	printf("%d\n", b);
}

```

This is fairly innocuous, and it would compile without warning in GCC, but it would fail to compile in the last version of MSVC I used. It didn't even have a sensible error message.
that is C++ code, not C ... C allows declaration of variables only at the beginning of the block. You are allocating b dynamically.

---

### Post by zerobinary on 2007-07-28
err ask to tell pro u don't like linux u go to beep 
just kidding it will kill u 
prof will kill u trsut me lol 
so best to ask him nicely 
is ur prof male or female

---

