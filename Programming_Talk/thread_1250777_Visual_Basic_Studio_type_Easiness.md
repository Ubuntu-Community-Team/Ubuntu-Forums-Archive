---
title: "Visual Basic Studio type Easiness"
date: 2009-08-26
forum: Programming Talk
---

### Post by Elep.Repu on 2009-08-26
I wasn't sure how to title this. 
I'm taking a VB Studio class, and apparently the program can write C#, C++ and similar, so I was curious if I could use it to write programs that can be compiled and run from linux, 
or a similar program that supplies a relative easiness that is similar?


I mean, I'm seriously dragging boxes and resizing them in designer view. 
I wonder if I can export this somehow, or something?

---

### Post by Mirge on 2009-08-26
[MonoDevelop]("http://monodevelop.com/")

---

### Post by Mateo on 2009-08-26
No, of course not.  Visual Studio is for building windows applications.  MonoDevelop uses .NET but if you expect it to be even 10% as easy you are in for a rude wakening.  My questions are:

1) Why would you write Visual Basic?  C# follows the same patterns, only in a C-like syntax.  I don't understand why they are still developing VB when you have C# as a better, but just as easy to learn, alternative.
2) Why are you writing desktop applications?  The *desktop is dead*.  I've been programming c# for 2 years and I've never written a desktop app for anything more than testing.

---

### Post by Mirge on 2009-08-26
> **Mateo said:**
> No, of course not.  Visual Studio is for building windows applications.  MonoDevelop uses .NET but if you expect it to be even 10% as easy you are in for a rude wakening.  My questions are:

1) Why would you write Visual Basic?  C# follows the same patterns, only in a C-like syntax.  I don't understand why they are still developing VB when you have C# as a better, but just as easy to learn, alternative.
2) Why are you writing desktop applications?  The *desktop is dead*.  I've been programming c# for 2 years and I've never written a desktop app for anything more than testing.

Desktop is dead? Damn, I better stop using dreamweaver, thunderbird, eclipse, filezilla...etc.

---

### Post by Elep.Repu on 2009-08-26
> **Mateo said:**
> No, of course not.  Visual Studio is for building windows applications.  MonoDevelop uses .NET but if you expect it to be even 10% as easy you are in for a rude wakening.  My questions are:

1) Why would you write Visual Basic?  C# follows the same patterns, only in a C-like syntax.  I don't understand why they are still developing VB when you have C# as a better, but just as easy to learn, alternative.
2) Why are you writing desktop applications?  The *desktop is dead*.  I've been programming c# for 2 years and I've never written a desktop app for anything more than testing.

Excuse me?
Why bother asking, if I'm prodded into a cage of questions myself.
Jeez, Desktop is dead, 

How about: "I don't care, answer my question or not" but don't whine about *why* I'm asking.
I hope *some* people are nice on here.

---

### Post by Fallen_Demon on 2009-08-27
I'd recommend NetBeans (get the one from NetBeans.org). It's a very nice IDE and automates everything in Java, C/C++, PHP, Python, Ruby... The list goes on :D There are loads of plugins as well

---

### Post by Elep.Repu on 2009-08-27
I just found
[http://en.wikipedia.org/wiki/Integrated_development_environment](http://en.wikipedia.org/wiki/Integrated_development_environment)

It references Anjuta. I've never heard of this type of program (IDE), I'm glad I know now!

> **Fallen_Demon said:**
> I'd recommend NetBeans (get the one from NetBeans.org). It's a very nice IDE and automates everything in Java, C/C++, PHP, Python, Ruby... The list goes on :D There are loads of plugins as well

Oh Cool! This looks pretty awesome. :)

---

### Post by Fallen_Demon on 2009-08-27
I suppose that's what comes from Windows development :P Don't worry, you'll be excited by *NIX development. One thing I'll say about NetBeans though is that OpenJDK isn't overly pretty with it. Get the Sun JDK instead

---

### Post by ganeshmallyap on 2009-08-27
I found even Lazarus is awsome RAD tool.

---

### Post by Elep.Repu on 2009-08-27
> **ganeshmallyap said:**
> I found even Lazarus is awsome RAD tool.

I really like how Lazarus looks!
Thanks for the other term: **RAD**
That'll help a lot! :D

---

### Post by Tony Flury on 2009-08-27
Visual Studio of course is itself an IDE (intergrated development environment). You can in theory edit all the VB forms and code outside Visual Studio (and it does work -  i had to do it once to get round a VS bug).

It is just that Visual Basic gives you an IDE out of a box.

On Unix you get the compilers as standard (effectively), and IDES are optional extras - some good ones are : 

Netbeans
Anjuta
IDLE (for Python)
ERIC (again for Python)
and several others - apoligies if i have not listed your favourite.

One of the limitations of the VS method of form building is that everything has a fixed position - making resizing stuff a pain - you have to reposition everything when the window resizes - or prevent the user from resizing.

I think that most Unix desktop windows systems (i known Gnone/GTK does this i assume KDE and QT are the same), use a relative positioning system form components on a window - so if the user resizes the window - the contents get moved (and maybe scaled) automatically.

---

### Post by Mirge on 2009-08-27
> **Tony Flury said:**
> Visual Studio of course is itself an IDE (intergrated development environment). You can in theory edit all the VB forms and code outside Visual Studio (and it does work -  i had to do it once to get round a VS bug).

It is just that Visual Basic gives you an IDE out of a box.

On Unix you get the compilers as standard (effectively), and IDES are optional extras - some good ones are : 

Netbeans
Anjuta
IDLE (for Python)
ERIC (again for Python)
and several others - apoligies if i have not listed your favourite.

One of the limitations of the VS method of form building is that everything has a fixed position - making resizing stuff a pain - you have to reposition everything when the window resizes - or prevent the user from resizing.

I think that most Unix desktop windows systems (i known Gnone/GTK does this i assume KDE and QT are the same), use a relative positioning system form components on a window - so if the user resizes the window - the contents get moved (and maybe scaled) automatically.

In C# in visual studio, using WinForms, you can dock elements to various edges, make them auto-grow/shrink, etc as the window changes size. I'm not sure about WPF, but I would assume it has something similar/better.

---

### Post by Elep.Repu on 2009-08-27
Working with Visual Basic, one of the first things the teacher showed us was the resize capability.
He anchored the form to the left and right side so as to enable resize capability.

Also, by default that is the *template*. "Resizable"

---

