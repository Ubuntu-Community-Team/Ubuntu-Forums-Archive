---
title: "Do I have to have Mac to program Objective-C ?"
date: 2012-01-15
forum: Programming Talk
---

### Post by hoboy on 2012-01-15
I was thinking of starting to play with Objective-C but I don't have Mac computer, is ther another way ?

---

### Post by nmaster on 2012-01-15
check out the package 'gobjc-4.4'.  the description from apt-cache is below:

```

Description-en: GNU Objective-C compiler
 This is the GNU Objective-C compiler, which compiles
 Objective-C on platforms supported by the gcc compiler. It uses the
 gcc backend to generate optimized code.

```

---

### Post by cgroza on 2012-01-15
There is a Objective-C compiler for it in the GCC, but to write software for a OSX or any of the iOS devices legally, you do need a Mac.

---

### Post by MadCow108 on 2012-01-15
you can also use llvm/clang to compile objective C, its available in most linux distributions.
I think thats also the compiler apple uses.

---

### Post by hoboy on 2012-01-15
Ok it seemed like the easier think to do is to get a Mac computer.

---

### Post by pbrane on 2012-01-15
> **cgroza said:**
> There is a Objective-C compiler for it in the GCC, but to write software for a OSX or any of the iOS devices legally, you do need a Mac.

Are you saying that I couldn't write a console app in obj-c (or any other language) on a GNU/Linux machine and run it on a mac legally? I can't seem to find that restriction anywhere on Apples TOS. I can understand not having access to the Cocoa dev libs on a linux machine legally (although I don't know that for sure), and I understand you need to have a Mac to do IOS dev, but it seems far reaching to say that you HAVE to have a mac to legally develop software to run on a mac. I really don't know the answer to this. Can you point us to where you find that?

---

### Post by cgroza on 2012-01-15
> **pbrane said:**
> Are you saying that I couldn't write a console app in obj-c (or any other language) on a GNU/Linux machine and run it on a mac legally? I can't seem to find that restriction anywhere on Apples TOS. I can understand not having access to the Cocoa dev libs on a linux machine legally (although I don't know that for sure), and I understand you need to have a Mac to do IOS dev, but it seems far reaching to say that you HAVE to have a mac to legally develop software to run on a mac. I really don't know the answer to this. Can you point us to where you find that?
I stand corrected.

---

### Post by pbrane on 2012-01-15
> **cgroza said:**
> I stand corrected.

I wasn't actually correcting you. I was really asking if it were true about developing apps for a Mac (as opposed to IOS devices). You may very well be correct. But this really doesn't help the OP, I just thought maybe you had come across something on Apples website.

---

### Post by r-senior on 2012-01-16
The basic answer to the quesion is no. You don't have to have a Mac to program in Objective-C.

There's no general legal requirement that you have to develop on a Mac to run the result on a Mac. Java applications for example.

But if you want to create complete Mac OS or iOS applications in Objective-C and submit them to the app stores, you need Xcode. Which means you need Mac OS to run it. Which means you need a Mac (it's against the EULA for Mac OS to run in a VM).

MadCow is correct that Apple use the LLVM/Clang compiler. Whether it is modified, I don't know. There used to be an issue that gcc would compile Objective-C 1.x but the versions available for Linux didn't incorporate the Objective-C 2.0 extensions that Apple added.

So you can play around with Objective-C on Linux but it might be quite different from the Objective-C used by Apple. Which is a shame because, although Objective-C is really weird when you first look at it, it is a powerful and flexible language. It grows on you.

---

### Post by nvteighen on 2012-01-16
You can use Objective-C 1.0.

What you won't have is Apple's NeXTStep API... you'll have to deal with GNUStep... And forget about Cocoa, of course.

---

