---
title: "[SOLVED] Intellisense in Monodevelop is abscent"
date: 2008-09-14
forum: Programming Talk
---

### Post by lakersforce on 2008-09-14
The Intellisense thing (aka. autocompletion and on-the-fly documentation) does not work. If it should work as in VS2008, intellisense should come with loads of suggestions as soon as you start typing. But in Monodevelop, nothing comes up when I start typing. What gives, do I have to enable it somewhere?

---

### Post by reverseblade on 2008-09-14
I've been using monodevelop for at least 2 years and intellisense was always working. There should be something wrong with your environment

---

### Post by lakersforce on 2008-09-14
I found out of the ctrl+space combination at start of a new line.

---

### Post by cszikszoy on 2008-09-14
That feature does work, just not exactly the same as it does in VisualStudio.

To make sure that it's enabled, go to Edit > Preferences.

Then under Text > General make sure "Enable Code Completion" is checked.

Also, under Preferences > Key Bindings > Text Editor you can find the key binding for code completion.  The item name is "Show Completion Window".

MonoDevelop doesn't show the completion window right as you start typing like in Visual Studio.  If you type a known keyword, then a '.', it will show the completion window though.

For example, typing "Console." as soon as you type the . the completion window will show.

If you want to show it when you type the first keyword just press ctrl + space (the default key binding).

---

### Post by caymahallesi on 2009-01-16
Hi

I downloaded version 1 from aptget 

intellisense (code completion) doesn't work. 
I check the preferences , text, code completion check box but it was enabled already. however in edit menu code completion is disabled. 

when I run the monodevelop from command prompt, I get below error;
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

thanks in advance.

---

### Post by danieru on 2009-03-13
I can't find exactly what is causing this, but it seems that when you pick a project template (e.g. 'console project' or 'gtk project') the intellisense features work, but if you start with an empty project then they don't.  I tried connecting this to particular assemblies that the templates load but it doesn't seem to be tied to that. Oh well, so I guess you can just make sure you start a new project with one of the templates and then strip out everything you don't need.:D

---

### Post by caymahallesi on 2009-03-13
Thanks for the info , I will try.

---

