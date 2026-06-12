---
title: "Is there a program that will pop up a message before it starts an application?"
date: 2010-04-05
forum: Programming Talk
---

### Post by cforput on 2010-04-05
I have always wanted a program that would have a couple of parameters. The first parameter would be the name of a program you want started. The second parameter would be a message box that pops up before the program starts and you have to click on a button to proceed. 

For example, suppose overnight, I download 500MB of clipart for OpenOffice. I let it run all night with the thought that next time I start OO, I need to install the clip art. It would be really cool if there was a program that would start up OO but before it actually started, it would let me put in a message to myself that says, "Hey, don't forget to install all that cool clip art you downloaded last night" Click OK to continue.

Does anyone know if something like this exists? It would also need to create a small file with the same name as the program you want to start and then take it's place so if I forgot that I needed to do something, I would just go to OO and start it up but since the real OO was replaced with this little app, I would get my reminder message to appear.

---

### Post by gnometorule on 2010-04-05
That is something easily done with VB & MS Office using simple event coding - well at least the basic question you ask (pop up at program start). I assume you're asking if you can code this, not if that particular program exists. 

I have never worked with OO, but it has its own Basic and operates under the 'pretty much like MS Office' premise, so I strongly assume it's possible here too (and equally as easy). I'd google 'event coding and Open Office basic' (and similar). Can't direct you further as said (also, last time I did MS event coding is also about 7 years ago). Gl.

---

### Post by km0r3 on 2010-04-05
Open up a terminal and type ```
man zenity
```
I bet you'll find something useful :)

Here's a quick compile...

```
wget http://coolOOclip_art.com && zenity --info --text="Hey, don't forget to install all that cool clip art you downloaded last night!"
```

---

### Post by cforput on 2010-04-06
Thanks for the suggestions. I think I will look into Zenity. I checked the man pages and it looks promising.

---

