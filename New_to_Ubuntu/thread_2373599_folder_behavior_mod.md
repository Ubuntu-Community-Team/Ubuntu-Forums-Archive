---
title: "folder behavior mod"
date: 2017-10-07
forum: New to Ubuntu
---

### Post by poisonfor3 on 2017-10-07
A bit hard to explain but I will try to make it short.

Back in the day, when it was new, I was using XP. It had many good things and as most people HEAR know Microsoft has been working hard to drive people away from their OS ever since. ):P One of the things I loved and lost with Vista and have never been able to find since is a behavior with folder link/shortcuts. I have tried every folder style/type/brand I can find on Linux and can not find it. A bit tricky to even explain I have had to show some people in person to get them to understand what I am even talking about. Let me explain what "IT" is:

You have your folder window. On most you have (or can have) a "Back" button AND AN UP BUTTON both. If I click on a shortcut/link it takes me to the "link target" like is should. If I click on the "BACK" button it takes me back where I was, Like is should BUT if I click on a link and go to that folder then CLICK THE UP BUTTON it does not take me to the next 'higher" folder like it should it takes me BACK to where I was. Why do I have to buttons there that do the same thing when in a proper world they should act different. WHY WOULD ANYONE WANT THAT since you have to buttons there why not have different behaviors???? But looks like the world does want it because I lost it in XP and never got it back nor have I been able to find a folder manager in Linux that does this or gives me the option to do that. Well . . . I think I know why, people get lost with all them buttons and have no idea what they are doing . . . maybe the world is not ready for the OLD XP style where people are expected to know that they clicked on a symbolic link. 

This wacky behavior makes me do extra clicks to get to where I want to be in my folders. If I can find a way to change this in Xubuntu  that would be nice, I do like a light footprint. Anyone have an idea how I can get the "up button" on folder window to go to the next higher folder in the folder "tree" rather than just taking me back to the last folder I was on?

Thanks for any help

---

### Post by again? on 2017-10-07
> **poisonfor3 said:**
> ......If I click on a shortcut/link it takes me to the "link target" like is should.......
Symbolic links aren't shortcuts in the way you believe, and don't take you to the location of the link in your file browser.
Symlinks reference abstract filenames/directories and NOT physical locations. They are given their own inode.

My **/home/glen/conky** folder is a symlink to **/media/Data/glen/conky** and when the symlink is clicked on the path shown is **/home/glen/conky** not **/media/Data/glen/conky**
[ATTACH=CONFIG]277022[/ATTACH]

The behaviour you see is not wacky to me and is what I expect from a symbolic link.
Does your directory need to be symlinked or would a shortcut/bookmark suit you?

I use the nemo file browser which allows you to "Follow link to original file".
[ATTACH=CONFIG]277023[/ATTACH]

---

### Post by poisonfor3 on 2017-10-10
I know it is not wacky to most humans if it was someone would have fixed it by now. Maybe I should be asking how do I NOT have symlink's tbe given their own inode. I am glad that most people are happy with the way it is but it bugs the heck out of me. Could I hire someone to write a program to change the action to the way I explained? Make a simple program to HAVE REAL shortcuts that WOULD take me to the file in the tree rather than their own inode. I mean this is open source there should be a way, Windows did it back in 2001 so it sould be able to be done in Linux too. Right?

---

### Post by again? on 2017-10-10
I don't fully understand the use of symlinks but I'm guessing there is a good reason they behave this way.
If you want a shortcut to a location, make a .desktop file to open your file browser at that location or add a bookmark to your file browser.

---

### Post by poisonfor3 on 2017-10-14
Not solved but thanks for trying.

---

