---
title: "Help with porting windows .net project to Mono"
date: 2005-06-24
forum: Programming Talk
---

### Post by fuzzy on 2005-06-24
I have a GUI (windows.forms) project that runs in Windows fine.  I've recently installed Ubuntu (sweet stuff) and discovered the backports project.  So I now have Mono 1.1.7 and monodevelop 0.7 installed.  I found several references to adding the following line to /etc/mono/config: 

```
<dllmap dll="libX11" target="/usr/X11R6/lib/libX11.so.6.2"/>
```

And now when I run my project I get:

```
Unhandled Exception: System.TypeInitializationException: 
An exception was thrown by the type initializer for System.Windows.Forms.XplatUI 
---> System.Reflection.TargetInvocationException: Exception has been thrown by 
the target of an invocation. ---> System.NotSupportedException: Either image 
format is unknown or you don't have the required libraries for this format.
``` 

I seem to be stuck.  I can't think my GUI is doing anything special (a couple edit boxes, a few buttons, a listbox,  a combobox), at least nothing special enough to kick out such an off exception.  I know the latest version of mono is 1.1.8, but it's not in backports as of yet.  I'd prefer not to have to compile from source, and wanted to evaluate the portability of this project to linux for future considerations.

I have the detailed trace if that would help anyone.  Any help or thoughts appreciated.  Thanks.
- fuzzy

---

### Post by Zingam on 2005-06-25
[QUOTE=fuzzy]I have a GUI (windows.forms) project that runs in Windows fine.  I've recently installed Ubuntu (sweet stuff) and discovered the backports project.  So I now have Mono 1.1.7 and monodevelop 0.7 installed.  I found several references to adding the following line to /etc/mono/config: 

```
<dllmap dll="libX11" target="/usr/X11R6/lib/libX11.so.6.2"/>
```

And now when I run my project I get:

```
Unhandled Exception: System.TypeInitializationException: 
An exception was thrown by the type initializer for System.Windows.Forms.XplatUI 
---> System.Reflection.TargetInvocationException: Exception has been thrown by 
the target of an invocation. ---> System.NotSupportedException: Either image 
format is unknown or you don't have the required libraries for this format.
``` 

I seem to be stuck.  I can't think my GUI is doing anything special (a couple edit boxes, a few buttons, a listbox,  a combobox), at least nothing special enough to kick out such an off exception.  I know the latest version of mono is 1.1.8, but it's not in backports as of yet.  I'd prefer not to have to compile from source, and wanted to evaluate the portability of this project to linux for future considerations.

I have the detailed trace if that would help anyone.  Any help or thoughts appreciated.  Thanks.
- fuzzy[/QUOTE]
 I'm not sure if Windows.Forms work on Mono at all yet. Wait for 1.2 release of Mono. They promise it will fully support Windows.Forms.
I never had a success even opening a window.

---

### Post by fuzzy on 2005-06-26
I just went to the Mono roadmap and saw an estimate of Q3 of this year for 1.2.  I guess I was hoping someone had a magic config update or command-line tweak that made everything work happy with the current version available, or someone could point out my obvious oversight.  *sigh*  Patience is a virtue, especially when others are doing all the work  :razz:

---

### Post by Ozitraveller on 2005-06-27
Try this article, I found it a while back, it might be useful.


Introduction to Mono - Your first Mono app
By Brian Delahunty 


[http://www.codeproject.com/cpnet/introtomono1.asp](http://www.codeproject.com/cpnet/introtomono1.asp)


The author has done a couple of articles on the Mono topic.

---

