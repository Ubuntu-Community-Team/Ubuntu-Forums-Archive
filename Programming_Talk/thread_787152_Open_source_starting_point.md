---
title: "Open source starting point"
date: 2008-05-08
forum: Programming Talk
---

### Post by mikazo on 2008-05-08
I realize this question may have been asked before, but I've discerned no real answer after some extensive Google-searching. I am a budding computer science student wanting to get my feet wet with open source development, but have no idea where to start. I've just completed my first year of my computer science degree which covered Java (all the way up to GUIs, networking, and data structures) and C (all the way up to pointers and linked lists). I've also studied the basic calculus/algebra/discrete math that goes along with the computer science degree.

I have some Ubuntu experience, having used it to complete programming assignments at school, and having just set up a new Ubuntu box running dual monitors and TwinView. I've just set up Eclipse and am eager to start programming again. Open source contribution would also be an asset for a resume in the future.

I am open to any ideas you might have about which small projects to start on, or which new language to learn that is more valuable as far as open source programming, or anything else that might help me. Thank you in advance. Hopefully this doesn't turn into another "which language is better" debate.

---

### Post by imdano on 2008-05-08
I think the best way to get involved is to scratch an itch.  Think about how you would improve a program you already use regularly, and see if you can go about implementing it.  My first contributions to open source projects were fixing small bugs in apps I already used, and working on adding new features after I had a little bit of experience working with the codebase.

---

### Post by LaRoza on 2008-05-08
> **mikazo said:**
> 
I am open to any ideas you might have about which small projects to start on, or which new language to learn that is more valuable as far as open source programming, or anything else that might help me. Thank you in advance. Hopefully this doesn't turn into another "which language is better" debate.

The sticky has these questions mentioned already.

---

### Post by mikazo on 2008-05-08
I have read through the sticky, please ignore my question about which language to use or learn if it is inappropriate in this thread. The sticky still does not appear to answer my question about where to start with open source. Perhaps a better question to ask would be, what was your first experience with open source programming? I apologize if my question wasn't quite phrased how I meant it.

---

### Post by LaRoza on 2008-05-08
> **mikazo said:**
> Perhaps a better question to ask would be, what was your first experience with open source programming? I apologize if my question wasn't quite phrased how I meant it.

I just noticed the sticky didn't explicitly mention what I had in mind, although it is in there somewhere. Sorry.

For myself, I do mostly web based programming, but am working on a system restore program for Ubuntu. I have it done in a usable form now (although it isn't pretty) with a CLI and a GUI. 

I am not really sure how useful people will find it though. I haven't made it public yet.

To join a project, there are two sites that I know that host many projects: freshmeat.net and sourceforge. I suggst browing them. You may find something you want to help with.

---

### Post by pmasiar on 2008-05-08
Start at the place which is interesting to you. Only your own interest will be your guide and will be pushing you. And learn some dynamically typed language, to taste the freedom :-)

Programming games is fun. Join a project you like to play. Take look at pygame, or GameBaker in my sig.

---

### Post by sloggerkhan on 2008-05-08
I'm in a similar situation as the above guy. I'm a CS college student who knows pretty much Java only. If you want to get involved in project but don't know the languages they use, what do you recommend?

---

### Post by LaRoza on 2008-05-08
> **sloggerkhan said:**
> I'm in a similar situation as the above guy. I'm a CS college student who knows pretty much Java only. If you want to get involved in project but don't know the languages they use, what do you recommend?

It depends on you of course, but I would suggest trying to learn the language. With Java, you may find languages like Python (or another high level language that the project uses) very easy to learn.

As a CS student (hopefully, a graduate) you are probably not expected to know everything, but I hope you are expected to be able to teach yourself what you need to know.

---

### Post by imdano on 2008-05-08
> **sloggerkhan said:**
> I'm in a similar situation as the above guy. I'm a CS college student who knows pretty much Java only. If you want to get involved in project but don't know the languages they use, what do you recommend?I was in your position too.  When I noticed a bug in a python app I was using, I just took a look at the code and figured out how to fix it.  It's not as hard you might think to figure out what's going on and make small changes in new languages if you're already familiar with one.  Use the code that's already there as a guide or look at documentation if you're not sure of syntax on certain things.

---

### Post by pmasiar on 2008-05-09
If you are capable programmer, you could learn basic Python over a weekend - try "Dive Into Python" free ebook. You will be surprised how much simpler and intuitive (and fun!) programming can be if compiler does most of the boring type maintenance, and language has flexible data structures.

---

### Post by jespdj on 2008-05-09
[Dive Into Python](http://www.diveintopython.org/), thanks pmasiar.

If you're looking for a project, then have a look at the many thousands of Ubuntu programs, or have a look on [http://sourceforge.net/](http://sourceforge.net/) where thousands of open source projects are hosted.

---

### Post by Sinkingships7 on 2008-05-09
> **LaRoza said:**
> I just noticed the sticky didn't explicitly mention what I had in mind, although it is in there somewhere. Sorry.

For myself, I do mostly web based programming, but am working on a system restore program for Ubuntu. I have it done in a usable form now (although it isn't pretty) with a CLI and a GUI. 

I am not really sure how useful people will find it though. I haven't made it public yet.

To join a project, there are two sites that I know that host many projects: freshmeat.net and sourceforge. I suggst browing them. You may find something you want to help with.

I'd love you forever if you made and released a working system-restore program for Ubuntu... 

If I daresay, that would be a HUGE contribution to Ubuntu, and Linux in general.

Of course, that may just be my naivety speaking... there may already be such a program, though if there is, I know nothing of it.

---

### Post by LaRoza on 2008-05-09
> **Sinkingships7 said:**
> I'd love you forever if you made and released a working system-restore program for Ubuntu... 

If I daresay, that would be a HUGE contribution to Ubuntu, and Linux in general.

Of course, that may just be my naivety speaking... there may already be such a program, though if there is, I know nothing of it.

The thing about Windows system restore is that is a counter balance to a flaw in Windows. Windows uses a registry under the guise of making things more organized (less .ini files) but the real reason is that it make piracy harder.

Windows system restore is a registry restore program.

My program attempts to hide the fact that the settings are in plain text files, and allows users to undo changes that they made. Specifically, video (xorg), software sources, grub, and...something else. I forget the fourth one. It has the ability to be customized (by specificying other files to include in the backups) by the user. It has named restore points which have their date recorded and allows the user to select one. 

The problem with it is (besides it being not pretty, it uses Tkinter) it is not what I want users to use. It hides how things work, and that is dangerous IMO.

I have it, it works, but I am not sure what to do with it.

---

### Post by Sinkingships7 on 2008-05-09
> **LaRoza said:**
> I have it, it works, but I am not sure what to do with it.

If you have a working alpha version, then there's only one logical thing to do with it:

Make it open source! :)

---

### Post by LaRoza on 2008-05-09
> **Sinkingships7 said:**
> If you have a working alpha version, then there's only one logical thing to do with it:

Make it open source! :)

I will want to make a .deb for it. Or would a simple install script do? It is just a few python files.

---

### Post by mikazo on 2008-05-10
A system restore function like that would actually be really useful, since you can mess around with a lot more important settings in Linux than you can with Windows. (I'm in transition)

---

### Post by LaRoza on 2008-05-11
> **mikazo said:**
> A system restore function like that would actually be really useful, since you can mess around with a lot more important settings in Linux than you can with Windows. (I'm in transition)

Yes, but anyone messing around with such settings *should* know to back up the files they are changing.

---

