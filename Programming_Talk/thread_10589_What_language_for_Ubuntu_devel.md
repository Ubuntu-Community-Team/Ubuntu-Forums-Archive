---
title: "What language for Ubuntu devel?"
date: 2005-01-09
forum: Programming Talk
---

### Post by Alessio on 2005-01-09
I'm learning a language, i like python and pygtk. Is it the best language to learn for ubuntu devel? For make ubuntu's appz? Or ubuntu's scripts?

---

### Post by poster_nutbag on 2005-01-09
In a nutshell, I'd say Python+GTK is the preferred language for Ubuntu desktop applications. You may wish to try Pygame for games programming though.

---

### Post by jdodson on 2005-01-10
[QUOTE=poster_nutbag]In a nutshell, I'd say Python+GTK is the preferred language for Ubuntu desktop applications. You may wish to try Pygame for games programming though.[/QUOTE]

pygtk is an awesome development platform.

---

### Post by lordan on 2005-01-21
I agree. Start off with Python. After a while, (ca 5-10 minutes), Python may start to annoy the hell out of you. In that case you can move on to Ruby. It won't annoy you.

---

### Post by Quest-Master on 2005-01-21
Ruby annoyed me after a few minutes. Python still sticks to me. :)

---

### Post by wtd on 2005-01-22
As much as I hate Microsoft, I have to say that Mono and GTK# is pretty spiffy.

```
using System;
using Gtk;

public class HelloWorld
{
   public class MyWindow : Window
   {
      public MyWindow() : base("Hello...")
      {
         Add(new Label("World!"));
         ShowAll();
      }

      protected override bool OnDeleteEvent(Gdk.Event e)
      {
         Application.Quit();
         return true;
      }
   }

   public static void Main()
   {
      Application.Init();
      MyWindow win = new MyWindow();
      Application.Run();
   }
}
```

---

### Post by Viro on 2005-01-22
What's wrong with good old C++? It's portable, it's an open standard and it suites you from writing small applications right up to large scale ones. The compilers are free and the supporting apps (debugger, profiler, lint, etc) have been developed for years.

If you're after portable GUI apps, C++ with a framework like wxWidgets (unstable has good GNOME integration) is pretty much unstoppable. Surprised no one has mentioned this option yet.

---

### Post by Lovechild on 2005-01-22
I second that vote for C#

---

### Post by poster_nutbag on 2005-01-24
[QUOTE=Viro]What's wrong with good old C++? It's portable, it's an open standard and it suites you from writing small applications right up to large scale ones.[/QUOTE]
Nothing is wrong with C++, it's just that other things are *better*. Lets face it, it doesn't really matter wether you write a gtk+ application in C++ or Python, as 99% of the code loop will be inside the gtk libs. So you may as well use the easier language.

If you *are* concerned about real-time performance, then one could well say why use gtk anyway, since the overhead for this is obviously out of your control: if you have some specific need for speedy code in one particular area, use your own C lib.

I used C/C++ for 15 years as my main language of choice: back when I started, it was the only choice, apart from machine code (you could say I upgraded from Zilog Z80) - and I loved it. Nowadays, I prefer to get the task done quickly, and not spend so much time in the debugger. Pretty much every script language (except shell scripts) lets me do just that.

---

### Post by dataw0lf on 2005-01-24
> If you're after portable GUI apps, C++ with a framework like wxWidgets (unstable has good GNOME integration) is pretty much unstoppable. Surprised no one has mentioned this option yet. 
Sure, but wxPython is another, equally, valid option.  You don't have to use C++ for wxWidgets.
dataw0lf

---

### Post by Ozitraveller on 2005-01-25
[QUOTE=wtd]As much as I hate Microsoft, I have to say that Mono and GTK# is pretty spiffy.

```
using System;
using Gtk;

public class HelloWorld
{
   public class MyWindow : Window
   {
      public MyWindow() : base("Hello...")
      {
         Add(new Label("World!"));
         ShowAll();
      }

      protected override bool OnDeleteEvent(Gdk.Event e)
      {
         Application.Quit();
         return true;
      }
   }

   public static void Main()
   {
      Application.Init();
      MyWindow win = new MyWindow();
      Application.Run();
   }
}
```[/QUOTE]

C# for me too! But I'll give python a go!

---

### Post by JeffS on 2005-01-27
Different languages are good for different things. 

 If you want to develop a small scale app and develop it quickly, and program speed is not important, go for Python or Ruby or Perl.  

If you want something larger scale but speed and overhead still don't matter too much, and you want rapid application development, go for Mono/C#. 

If you want to make anything from very small scale to very large scale, and program speed and low overhead do matter, and you don't mind the extra work of memory management, go for C or C++.  

Also consider the perspective of the end user, or your own experience with using various apps developed with various languages.  Personally, I've had good luck with apps written using a scripting language, such as Python or Perl, so long as the app isn't too large scale. 

 Gnome System Tools have a Perl front end with a C backend.  Notice when you launch Gnome System Tools (like the network connection configuration utility in Ubuntu), it takes a bit to load intitially.  Red Hat's Anaconda installer is a good medium sized app that uses Python.  Mandrake's installer is written in Perl.  These two apps perform decently (they are not speed demons) and are very easy and useful.  

I've never experienced any apps written using Mono, so I can't really judge.  However, it runs in a virtual machine (like Java) and virtual machines add huge overhead (big memory footprint and lot's of extra cpu cycles).   I have tried some .Net stuff on Windows (Visual Studio .Net).  It performed decently on fast modern hardware, and it had a big memory footprint - I dared not run much else on the system.

And speaking of Java, I've never used a desktop app written Java that wasn't  dead-dog slow.  Eclipse, for instance, is completely unusable unless you are using very modern hardware, with at least a 1.6GHz cpu and at least 512 megs memory.  I've tried Eclipse on lesser hardware, and it either takes at least 10 minutes to load, or it completely locks up the system.  JBuilder is another hog, but not quite as bad. However Java has been a huge success on the server side with J2EE.

Then there are apps written in good 'ol C and C++.  Still the majority of the major apps in Gnome are written in plain old C with the GTK libs.  And the majority of KDE apps are written in C++, with QT.  Personally, I've always had the best user experience when using an app written in C or C++.  They are always faster, more responsive, have quicker loading times, and have much smaller memory footprints.  I tend to be impatient when using apps, and I much prefer using an app written in C or C++ for these reasons.  Yes, writing software with C or C++ is much harder than any interpreted/virtual machine language, but the end result is often much better for the end user.  

And if you go down the C or C++ road, you will become a better programmer.  C and C++ really force you to know what you are doing, and understand how a computer works, and they force you to be very disciplined.  It's a journey well worth taking.

But then again, if you only interested in  small apps developed rapidly, then by all means use Python.  Python is a very easy, intuitive, clean, elegant language.

---

