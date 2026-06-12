---
title: "learning GTK#"
date: 2006-12-10
forum: Programming Talk
---

### Post by jordilin on 2006-12-10
Is there a good documentation or book on how to program User Interfaces with GTK# and C sharp in Mono Linux?. Programming for Windows with Windows Forms is extremely easy but I find it quite difficult in GTK#. There are tons of books and documentation for Microsoft Windows but nothing for GTK# Linux. 
Any suggestions?

---

### Post by Lord_Freelancer on 2006-12-10
i would also like to find documentation on this topic

---

### Post by jordilin on 2006-12-10
> **Lord_Freelancer said:**
> i would also like to find documentation on this topic

Yes, documentation on this topic is crucial as c sharp Mono is going to be the leading choice for developing apps in Linux. Novell, or whoever is behind Mono and GTK# should write a good book or tutorials on how to develop apps for Linux using this new and exciting technology.

---

### Post by MadMan2k on 2006-12-10
writing gtk is all the same across the languages - so if you understand pygtk, you should have no problems with gtk#:
[http://pygtk.org/pygtk2tutorial/index.html](http://pygtk.org/pygtk2tutorial/index.html)

especially if you use Glade for the interface:
[http://glade.gnome.org/](http://glade.gnome.org/)
[http://pygtk.org/docs/pygtk/class-gladexml.html](http://pygtk.org/docs/pygtk/class-gladexml.html)

the gtk# api docs are here:
[http://www.go-mono.com/docs/](http://www.go-mono.com/docs/)

but I'd discourage the use of mono, since it is highly controversial on the background of the latest actions by Novell.

---

### Post by loell on 2006-12-10
c gtk documentation is already mature, once you have familirize it , i think it will be easier to adapt whenever gtk# doc will be available.

---

### Post by jordilin on 2006-12-10
> **MadMan2k said:**
> writing gtk is all the same across the languages - so if you understand pygtk, you should have no problems with gtk#:
[http://pygtk.org/pygtk2tutorial/index.html](http://pygtk.org/pygtk2tutorial/index.html)

especially if you use Glade for the interface:
[http://glade.gnome.org/](http://glade.gnome.org/)
[http://pygtk.org/docs/pygtk/class-gladexml.html](http://pygtk.org/docs/pygtk/class-gladexml.html)

the gtk# api docs are here:
[http://www.go-mono.com/docs/](http://www.go-mono.com/docs/)

but I'd discourage the use of mono, since it is highly controversial on the background of the latest actions by Novell.

Yes, it seems that developing apps with python and PyGTK in Linux is much easier. Mono has been a hot topic since its inception in Linux and has been as you say very controversial within the Linux community.

---

### Post by duff on 2006-12-10
there's edd dumbill's book 
[http://www.amazon.com/Mono-Developers-Notebook-Edd-Dumbill/dp/0596007922/sr=1-1/qid=1165755694/ref=pd_bbs_sr_1/105-9604093-2537247?ie=UTF8&s=books](http://www.amazon.com/Mono-Developers-Notebook-Edd-Dumbill/dp/0596007922/sr=1-1/qid=1165755694/ref=pd_bbs_sr_1/105-9604093-2537247?ie=UTF8&s=books)

---

### Post by pmasiar on 2006-12-10
> **jordilin said:**
> c sharp Mono is going to be the leading choice for developing apps in Linux. Novell, or whoever is behind Mono and GTK# should write a good book or tutorials on how to develop apps for Linux using this new and exciting technology.

Mono as leading choice? LOL!!! The fate of Mono and C# on Linux was questionable even before recent Novel "pact with the devil" :-) MS. After that, Mono is IMHO dead in the water: why would *anyone* spend effort, time and money helping Novel and Mono? MS was very open: you can use Mono only as "hobbist" and you cannot make money from it. If you want to make money outside of Novel's protection, MS lawyers will rush in and get you - that's the deal Novel wanted.

And for Novel it does not make sense to invest in Mono tools either: they realize that anything they spend money to create, they are forced by GPL to share with all (including competitors like redhat) for free. Novel tried to corner market for *tools for fools*: people who cannot make their mind, cannot decide between .NET and open-source platforms.

Novel need to recall the lesson we all learned in kindergatden: play nicely and share toys, and we are friends. Join with a bully, and we will pick our toys and go to other corner. 

If you really have to share between platforms, consider python for .NET: IronPython. 

You don't have to switch to every new and exciting technology fad. *Be especially careful* if company promoting any "newest and bettest" technology has millions of dollars for generating hype. Best technology is the one successful *despite* total lack of marketing money: word-of-mouth of software gurus at least for me is more important that blabbering of a marketoid. IMHO, YMMV of course. :-)

---

### Post by emperon on 2007-01-03
install edgy from fresh , open your console, type "mono". Do you think it is still questionable ?
Try it for java also, what do you see ? sun's java or crappy gcj ? ohh both are crappy anyway

---

### Post by zgornel on 2007-01-06
You people are offtopic. Try searching on the emule network for GTK# docs.

---

