---
title: "what IDE are people using for C/C++ dev?"
date: 2009-01-21
forum: Programming Talk
---

### Post by hellz99 on 2009-01-21
I'm primarily a java person, so I use eclipse daily, but I'm taking on a JNI project so I'll have portions of C (and maybe C++).  any suggestions?

---

### Post by jimi_hendrix on 2009-01-21
vim

---

### Post by dexter on 2009-01-21
You can install eclipse-cdt, which enables eclipse compile c/c++ code.

---

### Post by hellz99 on 2009-01-21
yea I was kinda expecting the various replies of vim, pico, emacs, etc.  
But lets be serious.

---

### Post by Mr.Macdonald on 2009-01-21
If you take the time to learn emacs you will not be disappointed, very fast and powerful!

---

### Post by Wybiral on 2009-01-21
I'd go with the eclipse C/C++ plugin too, especially since you already use eclipse for Java.

---

### Post by Sorivenul on 2009-01-21
For your particular case, add another +1 for eclipse-cdt.

---

### Post by jmartrican on 2009-01-21
> **hellz99 said:**
> yea I was kinda expecting the various replies of vim, pico, emacs, etc.  
But lets be serious.

What are you alluding to?  Everyone I work with uses vim.  Only one guy, and he is a java guy, uses an IDE.  I do not know what they use in other parts of the company, but that's how it is in my group.

---

### Post by Joeb454 on 2009-01-21
Given that the OP asked for _IDE's_ and the fact that Vi(m) & Emacs et al are _not_ IDE's, I don't see why they would be suggested :)

Anyway...

I've never used Eclipse, though I have to use Netbeans for some Java work at university, and I've noticed that can do C/C++ as well, so it may be worth a look. It's also cross-platform :)

---

### Post by matthew.ball on 2009-01-21
The programming FAQ stickied mentions some IDEs for use with Ubuntu.

Personally, I think a Terminal with nano is all you need, but that's just my preference (keep it simple!).

One of the text-editors (IDEs?), recommended by the programming FAQ is Geany ([http://www.geany.org/](http://www.geany.org/)).

I have only briefly used it, but it seems quite powerful.

---

### Post by jmartrican on 2009-01-21
> **Joeb454 said:**
> Given that the OP asked for _IDE's_ and the fact that Vi(m) & Emacs et al are _not_ IDE's, I don't see why they would be suggested

Point taken.

Is there a link to this nano (IDE, editor?) that was mentioned.  I'd like to use an IDE but I am a terminal dude and I didn't know my options and was too lazy to yahoo it.

---

### Post by jmartrican on 2009-01-21
> **jmartrican said:**
> Is there a link to this nano (IDE, editor?) that was mentioned.

Nevermind, i found it.  Didnt realize it was already installed.

But I still would like any suggestions for a terminal based IDE for c++.

---

### Post by matthew.ball on 2009-01-21
I think there is some C++ IDE for KDE, kdevelop or something, maybe qtdevelop - I'm not sure.

There is the previously mentioned "Geany", which (much like Kate for KDE), supports an "in-built" shell, so you can easily run commands while editing your documents. (It's probably also possible to set-up Geany to use gcc, ghc etc. as a compiler, though I haven't done much searching regarding this).

If you want a very lightweight text-editor, there is also Scribe (or Scribes?).

There's more here: [http://ubuntuforums.org/showthread.php?t=1006662](http://ubuntuforums.org/showthread.php?t=1006662)

You could download glade and design your GUIs with that and then just link your programs to your designed GUI.

---

### Post by Sorivenul on 2009-01-21
If you want a console-based IDE for C/C++ there is "[motor]("http://konst.org.ua/motor/")". It isn't in the repositories, but you can just compile from source. You'll have to scroll down to find the package download links. [The source]("https://launchpad.net/ubuntu/+source/motor") is also available on Launchpad for Ubuntu.

---

### Post by DocForbin on 2009-01-21
You might try netbeans. Not sure how good the C/C++ support is, but it's there, and netbeans 6.5 is pretty friggin slick.

---

### Post by slavik on 2009-01-21
I use Geany for single file stuff, for bigger (actual projects) I use Anjuta.

---

### Post by AZzKikR on 2009-01-22
Eclipse CDT does the job very well for me. You're already used to Java, so Eclipse may be familiar to you.

---

### Post by monkeyking on 2009-01-22
I use emacs with speedbar and gud.
It't quite nice, I can code quite fast with this setup.

It looks like shiite though

---

### Post by jimi_hendrix on 2009-01-22
> **hellz99 said:**
> But lets be serious.

i am serious...

---

### Post by jimi_hendrix on 2009-01-22
> **Joeb454 said:**
> Given that the OP asked for _IDE's_ and the fact that Vi(m) & Emacs et al are _not_ IDE's, I don't see why they would be suggested :)


sorry for the double post but....

that depends on ones opinion...i have seen many features including intellisense like code completion in vim...

---

### Post by JMJ_coder on 2009-01-22
It depends on what you want to develop. For large GUI applications, I can see some benefits for using an IDE -- especially one that offers RAD features. 

But, for me, I do all of my C/C++ development at the console: (n)vi, pcc, gdb, cvs, etc.

---

