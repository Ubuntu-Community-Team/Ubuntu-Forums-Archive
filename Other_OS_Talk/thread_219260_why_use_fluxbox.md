---
title: "why use fluxbox?"
date: 2006-07-19
forum: Other OS Talk
---

### Post by gazj on 2006-07-19
Ok, I have been tinkering around with making fluxbox good for a couple of nights,  a long time for some eye candy, do you think it was worth my hard work? [IMG]http://homepages.tesco.net/beckygary/screenshot.jpg[/IMG]

---

### Post by nalmeth on 2006-07-19
That is beautiful man

I take a different approach with my fluxbox, but this is awesome, seriously.

I see you're not using the slit though? It's one of my more favorite features with fluxbox, the dockapps are really neat.

How did you get GKrellm to not show up in the taskbar? Is it on another desktop or something?

---

### Post by Kuraboy on 2006-07-19
Hi!

nice thing you did there... I still dont know what to use, gnome or fluxbox, gnome seems much easier and many things are where I can find them easy... but fluxbox still pull me in, by being lite on the system and seems more proffesional, even thought I have P4 2 GHz with 768 MB ram, I still like the idea that it takes only 60 MB when loaded XD

but it is so hard to costumize... can you help by telling me and others how you started and where did you learn things from?

I have a question, those icon on the top? are they icon on desktop? or a toolbar? I am confused... how do you make them?

thnx, and nice job :)

---

### Post by prash@linuxitarian on 2006-07-19
> **gazj said:**
> Ok, I have been tinkering around with making fluxbox good for a couple of nights,  a long time for some eye candy, do you think it was worth my hard work? [IMG]http://homepages.tesco.net/beckygary/screenshot.jpg[/IMG]

Excellent job dude! Nice work! Like the previous post, I think you could help us all out if you could give a "guide" on how you did this stuff! Thanks and great work!!

---

### Post by nalmeth on 2006-07-19
A lot of the stuff is covered in this wiki:
[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

For the icons, check out fbdesk:
[http://fluxbox-wiki.org/index.php/Howto_fbdesk](http://fluxbox-wiki.org/index.php/Howto_fbdesk)

---

### Post by hizaguchi on 2006-07-19
Sorry, never been able to get into those dark, dark themes.  But for a dark theme, it is pretty nice.  Especially the desktop search window.  I like green on grey.

---

### Post by gazj on 2006-07-20
ok, first of all i do use the slit in fluxbox, it is on the very right hand side if you scroll across you will see it, its because the screenshot is so big.  There you will see i have gkrellm there and a few other dockapps

By the way the reason gkrellm does not appear on the taskbar is because it is loaded into the slit, use the following to start gkrellm in the slit

```
gkrellm -w
```

The -w stands for withdrawn i believe (i.e in the slit)


The icons can be found (they are gentoo ones,  maybe thats cheating a little) can be found here [http://www.gentoo.org/dyn/icons.xml]("http://www.gentoo.org/dyn/icons.xml")
, to make them work you need to install idesk

```
sudo apt-get install idesk
```

then you must right a small text file for each icon which are stored in your home folder under .idesktop

all fluxbox settings are stored in .fluxbox in your home directory, within that directory is a text file called startup, where you can insert commands to programs that you want to start when fluxbox does,  you need idesk to be one of theese.

any other bits and pieces people want to know about you can MSN me,  if enough people want to know i will write a howto,  although two nights of work is going to take some explaining,  and i gotta try to remember how i did it all.

I'll do my best

---

### Post by christhemonkey on 2006-07-20
A howto would be very nice!

Always wanted to try flux/blackbox but was just a little daunting.

---

### Post by nalmeth on 2006-07-20
Thanks for the Gkrellm tip! So simple... 

And idesk huh? Never heard of it. What does it offer that fbdesk can't do?

EDIT:
@ christhemonkey

Check my previous post, I posted a fluxbox howto and a fbdesk howto.

---

### Post by K.Mandla on 2006-07-22
Wow. :shock: That's amazing. Nice job!

---

### Post by RavenOfOdin on 2006-07-22
Personally I like Fluxbox.
Next to KDE its my window manager of choice.

I don't use fbdesk though.

Have you checked out themes.freshmeat.net yet? They have a bunch of Fluxbox themes there which are pretty amazing.

---

### Post by egon spengler on 2006-07-23
Well since you asked, I think that the window decorations are hideous. I don't particularly like dark themes myself but beagle looks quite nice there. Gkrell also looks hideous but hey, it always does

---

### Post by jnev on 2006-07-24
awesome! what program are you using to diplay your cpu/ram/etc usage on the right of your desktop? when I tried fluxbox I really liked it but couldn't find the program to do that... (sorry for the stupid question)

---

### Post by orlfman on 2006-07-29
Conky or Gkrellm.... Not a Ubuntu user my self (Gentoo user :p), but was browing Google for Fluxbox themes and found this thread :p So thought id help ya lolz.

But hey! Should show off mine...

[http://img156.imageshack.us/img156/8780/7807jt3.png](http://img156.imageshack.us/img156/8780/7807jt3.png)

[http://img152.imageshack.us/img152/199/1022qf3.png](http://img152.imageshack.us/img152/199/1022qf3.png)

[http://img148.imageshack.us/img148/6317/5257cu3.png](http://img148.imageshack.us/img148/6317/5257cu3.png)

---

### Post by benplaut on 2006-07-30
idesk can do ANYTHING.

literally... anything.  take a look at their docs.

I'm one of those weirdos who finds fluxbox to be quite heavy.  I use openbox with pypanel, and conky for a sysmon.

Screenshot when i figure out what i'm doing my my icons and make it pretty again ;)

---

