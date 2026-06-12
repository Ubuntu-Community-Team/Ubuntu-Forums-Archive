---
title: "Linux, C++ &amp; GUIs"
date: 2009-04-04
forum: Programming Talk
---

### Post by oldchris on 2009-04-04
<flameretardent on>

Not a troll, but what combination do application developers really use for GUI devel in Linux using C++?  

I've used GTK and Glade/2 a bit and while this seems to be a potentially very powerful and flexible approach, it reminds me of coding the first half of a COBOL program - lots of typing for not much action.  

I'd like something that allows me to hack together simple applications quickly - if things work out they can be "tuned" by me or others later.  

Borland C++Builder was about my speed as a development environment - is there an "equivalent"? 

I realize there are alternatives to using C++, but I've tried to reduce the number of languages I use over the years, and now being down to C/C++ I'd like to keep it that way. 

TIA,
Chris

<flameretardent default>

---

### Post by slavik on 2009-04-04
glade3+glademm or QT. :)

---

### Post by OutOfReach on 2009-04-04
Ahh I think the Qt toolkit is right for you.

---

### Post by pacofvf on 2009-04-04
mmm.. gnuc-gtk+  is very powerful, but if you want an object oriented approach, then I'm sorry about I'm going to tell you, but the answer is python-gtk(pygtk). gtkmm can solve some problems but you won't get much support if you are in trouble....another reason of using gnuc-gtk is the multiplataform capability...but if you're just trying new things, you can also can try qt, is c++ native....

---

### Post by slavik on 2009-04-04
in that case ... Vala :D

---

### Post by Can+~ on 2009-04-04
> **oldchris said:**
> it reminds me of coding the first half of a COBOL program - lots of typing for not much action.

Well, it's GUI programming after all. There's a lot of widgets to configure, many things that need to be connected, and specially the language choice can make it rather confusing.

The key of GUI programming, is that you can make it completely from code, but it will be painful. GUI tools move a lot of code to a graphical input which eases the job. 

For example, even though I dislike C#, I've gotta admit that Visual Studio does some things right, developing things there is plain drag n' drop with minimal code.

It all depends on the tools you have.

---

### Post by tanderson on 2009-04-07
check out qt creator. I think it is a good fit for c++ developers raised on visual studio.

---

### Post by mdurham on 2009-04-07
> **tanderson said:**
> check out qt creator. I think it is a good fit for c++ developers raised on visual studio.
It's more than 'good' it's great!

---

### Post by Yacoby on 2009-04-07
I used wxFormBuilder.

---

