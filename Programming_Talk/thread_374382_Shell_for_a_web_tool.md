---
title: "Shell for a web tool"
date: 2007-03-02
forum: Programming Talk
---

### Post by trivialpackets on 2007-03-02
This is a general web tool application.  Basically, our applications i located at a specific IP, i wanted to create a shell that works around the tool, interacting with the main window.  What is the best tool to look into doing something like this?  It has to be usable in a Windows environment, as it's a tool I'm building for work, so any help would be great.  I love the forum and always get the help I need, so bail me out here guys.  Gotta be some current/X windows developers here as well as web developers that would be able to help.  Thanks in advance and if anyone has any screenshots of what they feel I'm talking about, I'd be happy to see if that's the type of thing I'm thinking.  Thanks!

---

### Post by lnostdal on 2007-03-02
hm .. right, you've got a web-page that you want to interact with via the terminal?

i've used [http://weitz.de/drakma/](http://weitz.de/drakma/) for similar tasks on several occations .. i think it is portable to win32 using CLISP, but i haven't confirmed this (yet) as i've only used it under SBCL/linux

if you're really stuck i can confirm whether it currently is portable (edit: but if you have a linux-server at work you can maybe run it as a server-app on linux and have the win32-machines work as clients to that .. i don't know :)) or not and maybe help you get started with it

---

### Post by trivialpackets on 2007-03-02
Ok, a shell then is the wrong word.  Not shell as in bash, but shell as in like a frame, with functionality in the frame.  I know I could make it as a web page with different frames, however that is not what I was looking for.  Any ideas

---

### Post by lnostdal on 2007-03-02
oh, ok -- you can do something like this:

browser <--> server that generates "shell" web-page <--> server that has original web-page

..or if you for some reason don't want to use a browser as client you can do:

gtk+-client <--> server that adapts data (xml-rpc for instance) <--> server that has original web-page

..gtk+ lets you write user interfaces that are portable to many platforms; linux and win32 also.. edit: for screenshots just take a look at Ubuntu; most apps use gtk+

..should be an interesting task.. :)

edit2: you could of course handle the adaptation and interaction with the web-page directly at the client also (skipping the in-between server) .. but if the original web-page changes, all clients need to update their software to compensate (instead of only doing a single update at the in-between server) so that might not be suitable in all cases

edit3:
or maybe i misunderstood yet again .. do you mean interacting with an _application_ (the original source isn't a web-page) remotely?  in that case i am not sure; you'd have to provide more info about what toolkits etc. that application uses ..  what sort of application is it?

---

### Post by trivialpackets on 2007-03-02
Isn't it fun trying to draw a concept in a forum with text?  LOL.  

I'm not sure I got it, but I'll look into it a bit later today.  I've written a page that essentially does what I want, but I don't like the framework of using frames, that's where I'm at.

---

