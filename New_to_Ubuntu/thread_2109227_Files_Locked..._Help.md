---
title: "Files Locked... Help"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by SoccerRef on 2013-01-26
Here's my situation...  Three or Four years ago I had need of some more storage space for photos.  I had an old PC case sitting in my garage and enough money to buy a 500 Gig HD (Huge at the time...), but not enough to buy a new system or an OS.  I downloaded Ubuntu at the suggestion of a friend and created a shared folder which I accessed via the home network.

Fast forward to today.  I just built a new PC with Win7 Ultimate.  The old PC died, but the data on the HD is fine, except I can't seem to copy or use any of it.  I put the HD in an external HD case and tried to copy the files to my new PC (with 6 TB of HD space).  I can see all of my folders, but I can't access all of them.  Some of them I have opened and copied the contents with no issues, but some of them (of course the most important ones to me!) give me an error that I am not authorized.

Needless to say, I am thoroughly confused.  In the properties window, some of the folders are shown as "Read Only", but there is no consistency between that being an indicator of whether or not I can read it...

Any help will be greatly appreciated...
:confused:

---

### Post by elgordodude on 2013-01-26
```
sudo chown -R yourdrivenamehere

```

---

### Post by SoccerRef on 2013-01-26
While I appreciate the quick response... I have no idea what this means...

---

### Post by SoccerRef on 2013-01-26
> **elgordodude said:**
> ```
sudo chown -R yourdrivenamehere

```

While I appreciate the very quick response I have no idea what this means... How do I use this piece of information you've given me?

---

### Post by lisati on 2013-01-26
> **SoccerRef said:**
> While I appreciate the very quick response I have no idea what this means... How do I use this piece of information you've given me?

It's a *command* you type in from the terminal.

---

### Post by elgordodude on 2013-01-26
Fair enough, I'll break it down for you

It's a terminal command, a terminal is kind of like dos, but more powerful, flexible, and well just better.

Open a terminal with Ctrl+Alt+T or terminal in your applications menu

sudo gives you temporary administrator rights, you'll need to enter your password, but it's how you tell linux, yes I am the boss

chown is the change ownership command, it will transfer ownership to your current account, over whoever has it now, likely your old ubuntu account.

-R is for recursive in chown, it will transfer ownership of subdirectories and files below the directory you're currently in

yourdrivenamehere depends on the directory you're changing, the easy way is to drag and drop, type sudo chown -R then drag the directory window into the terminal and something like "/media/110add42bb/My\ Documents/My\ Pictures/" will appear at the end of the line, your results will vary.

Then press enter and you should be able to copy all the photos you'd like :)

edit: And a belated welcome to the forums, enjoy your ubuntu

---

