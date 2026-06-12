---
title: "Trying to Compile a Program Using Glade."
date: 2010-10-09
forum: Packaging and Compiling Programs
---

### Post by Serentic on 2010-10-09
Hi everyone. <3 It's totally my first post on the forums.

I'm a fairly new user for Ubuntu; I switched around two months ago when Windows started freezing up constantly.

That being said, I'd like to start developing a few programs for Ubuntu to be used in the Software Center. I have something almost done, and I want to test it to see how it runs. The problem is that I can't for the life of me figure out how to compile it. I've been running around Google frantically, and I've come up with a few possible answers, but none of them seem to be working. I was told I was supposed to have a .xml and a .glade in the same folder, which I've done. I've downloaded most if not all of the packages involved in compiling programs, to no avail.

Someone help the noob? :D

---

### Post by Tony Flury on 2010-10-09
Glade is not a compiler - it is a tool to build GUI.

A GUI designed in glade wont actually do anything - you still have to write the application code in a language of your choice (python, C, C++ etc), The application sits behind the GUI and decides what to do when the user clicks a button or fills in a field.

What language is your application written in ?

---

### Post by Serentic on 2010-10-09
Sorry, I meant to clarify up there. xD I know Glade doesn't compile them; I was trying to do it myself. It's coded in Python.

---

### Post by Tony Flury on 2010-10-09
You don't compile python - you just run it : 

```

python <myfile>.py

```

If you application is correct then it should start up your GUI.

---

### Post by Serentic on 2010-10-09
Oh, thanks so much. (:

---

### Post by Tony Flury on 2010-10-09
What source of documentation are you using to learn python ? How to run python programs should be the first chapter.

---

