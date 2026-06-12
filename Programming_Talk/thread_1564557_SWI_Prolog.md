---
title: "SWI Prolog"
date: 2010-08-30
forum: Programming Talk
---

### Post by Extol11 on 2010-08-30
So I need this programming language for one of my classes. I've never done anything in this programming language and I'm wondering two things... The first one is if I can use this in Ubuntu without any difference to Windows. I don't want to keep my programs in windows to a minimum since I always end up slowing the computer and I'd rather just keep it running my games and have Ubuntu for all my programming needs. :D And Second, is there a GUI for it or is it always just a terminal running words? I know it's not a compiler but a hybrid between a compiler and something else. But there should be something to let me know if I made any mistakes before it runs. 

Oh and is there a Notepad++ for Ubuntu too? He recommended it. Thanks in advance.

PS: I normally look for this myself but I was clueless as to where to start searching for it.

---

### Post by worksofcraft on 2010-08-30
A long time ago a company called Borland had a whole range of languages, their object oriented Turbo Pascal was streaks ahead of the competition... amongst them was a fully fledged Prolog compiler which I think still continues as full visual tool maintained by "Prolog Development Center" aka PDC.

Sadly I don't think it was ported to Linux, but another solution would be to run your development tools in a Virtual machine under Linux, so it won't clutter your games platform.

Regarding Notepad++ I really don't see it as much better than gedit... Notepad++ is only impressive when compared to  Microsoft products ;)

---

### Post by spjackson on 2010-08-30
> **Extol11 said:**
> So I need this programming language for one of my classes. I've never done anything in this programming language and I'm wondering two things... The first one is if I can use this in Ubuntu without any difference to Windows. I don't want to keep my programs in windows to a minimum since I always end up slowing the computer and I'd rather just keep it running my games and have Ubuntu for all my programming needs. :D And Second, is there a GUI for it or is it always just a terminal running words? I know it's not a compiler but a hybrid between a compiler and something else. But there should be something to let me know if I made any mistakes before it runs. 

Oh and is there a Notepad++ for Ubuntu too? He recommended it. Thanks in advance.

PS: I normally look for this myself but I was clueless as to where to start searching for it.
swi-prolog is a package in the repositories. You can install it from Synaptic, or via any of the other package installers.

For example, click on System->Administration->Synaptic Package Manager, type prolog in the search box and select the package(s) you want.

---

### Post by rjbl on 2010-08-30
> **Extol11 said:**
> So I need this programming language for one of my classes. I've never done anything in this programming language and I'm wondering two things... The first one is if I can use this in Ubuntu without any difference to Windows. I don't want to keep my programs in windows to a minimum since I always end up slowing the computer and I'd rather just keep it running my games and have Ubuntu for all my programming needs. :D And Second, is there a GUI for it or is it always just a terminal running words? I know it's not a compiler but a hybrid between a compiler and something else. But there should be something to let me know if I made any mistakes before it runs. 

Oh and is there a Notepad++ for Ubuntu too? He recommended it. Thanks in advance.

PS: I normally look for this myself but I was clueless as to where to start searching for it.

Get it from the Ubuntu Software Centre - which has a whole bunch of standard PROLOG compilers / interpreters which run well in GNU/Linux. All your really need to support your college work is likely to be a simple editor - PROLOG is done in words, not pictures. I guess you could use Geany or KDevelop as an IDE if you really wanted to. Or use prolog-el (from Ubuntu Software Centre) - a version of Emacs configured for PROLOG code editing.

Hope this helps
rjbl

---

### Post by dv3500ea on 2010-08-30
You can just install the package: [swi-prolog]("apt:swi-prolog").
There is a GUI library for it: [swi-prolog-xpce]("apt:swi-prolog-xpce").

---

### Post by worseisworser on 2010-08-30
> **Extol11 said:**
> So I need this programming language for one of my classes. I've never done anything in this programming language and I'm wondering two things... The first one is if I can use this in Ubuntu without any difference to Windows. I don't want to keep my programs in windows to a minimum since I always end up slowing the computer and I'd rather just keep it running my games and have Ubuntu for all my programming needs. :D And Second, is there a GUI for it or is it always just a terminal running words? I know it's not a compiler but a hybrid between a compiler and something else. But there should be something to let me know if I made any mistakes before it runs. 

Oh and is there a Notepad++ for Ubuntu too? He recommended it. Thanks in advance.

PS: I normally look for this myself but I was clueless as to where to start searching for it.

SWI-Prolog is available in the standard Ubuntu repositories:

  [http://www.psychocats.net/ubuntu/installingsoftware#softwarecenter](http://www.psychocats.net/ubuntu/installingsoftware#softwarecenter)


Just search for 'prolog' in the Software Center then hit `Install' and go.

edit: errr .. looks like 3-4 people already answered .. heh :)

---

### Post by fct on 2010-08-31
notepad++ is windows-only AFAIK. BUT I think it works fine on linux using wine. Might want to try that.

---

### Post by Extol11 on 2010-08-31
Thanks for the info, guys. It's greatly appreciated. I'll get to that in the afternoon.

---

### Post by Metal Fan on 2010-09-04
Hi!

Prolog Development Tools (ProDT) is a Prolog Integrated Development Environment (IDE) aiming to be as rich in functionality as the Eclipse's java IDE, giving the developer a single environment where it can control the development of a Prolog project from code edition, test execution, etc...

This project stands on top of Eclipse's projects to take advantage of its already existent features and its extensibility and works on any environment Eclipse works including windows, linux and mac OSX.

It support as underlying interpreters: SWI-prolog, XSB prolog, B-prolog

The site has more information about the project including installation and features list: [http://prodevtools.sourceforge.net/](http://prodevtools.sourceforge.net/)

Hope you can find it useful!!! :)

---

