---
title: "How do I set a default HTML editor for when I right click and html file in Nautilus?"
date: 2007-05-24
forum: Programming Talk
---

### Post by tc101 on 2007-05-24
I am using Kompozer for html editing.  I get to it by going to Applications/Programming/Kompozer.  
When I am in Nautilus File Viewer and right click an html file there is an "Open With" option, but none of the programs listed is Kompozer.  At the top of the right click menu is "Open With Firefox Web Browser"  then right under that is "Open With".  If I select "Open With" it has several html editors that I tried and didn't like, but it doesn't have Kompozer.  How do I add Kompozer and remove the others from that list?

---

### Post by jfinkels on 2007-05-24
> **tc101 said:**
> I am using Kompozer for html editing.  I get to it by going to Applications/Programming/Kompozer.  
When I am in Nautilus File Viewer and right click an html file there is an "Open With" option, but none of the programs listed is Kompozer.  At the top of the right click menu is "Open With Firefox Web Browser"  then right under that is "Open With".  If I select "Open With" it has several html editors that I tried and didn't like, but it doesn't have Kompozer.  How do I add Kompozer and remove the others from that list?

Right click, go to Properties, go to the Open With tab, then choose the default opening application.

You may have to click "Add" to add it to the list yourself. If so, the binary file for this program (the file that you run when you open the program) is probably at "/usr/bin/kompozer".

---

### Post by tc101 on 2007-05-24
Thanks.  I got it to work, but I have a related question.  You said:

> You may have to click "Add" to add it to the list yourself. If so, the binary file for this program (the file that you run when you open the program) is probably at "/usr/bin/kompozer".

I didn't see it at  "/usr/bin/kompozer".   So I went to Applications/Programming/Kompozer and right clicked, thinking I would see a selection to open the  properties window and find it that way.  There was nothing to open properties window, just options to add the launcher to desktop or menu bar.  I added the launcher to the desktop and there I was able to open a properties window, but it still did not give me the location of the file.  Under the properties/launcher tab it just said "kompozer" for the launcher but gave no information on the location.  

I did what you told me to add kompozer to the list, but instead of entering the location I just entered "kompozer" and it worked.

However, I don't understand what is going on behind the scenes.  How does the system know where kompozer is located, and how do I get that info?  This is actually less intuitive and gives me less info than windows, although I am sure that is just because I don't understand it all yet.

---

### Post by jfinkels on 2007-05-24
> **tc101 said:**
> Thanks.  I got it to work, but I have a related question.  You said:



I didn't see it at  "/usr/bin/kompozer".   So I went to Applications/Programming/Kompozer and right clicked, thinking I would see a selection to open the  properties window and find it that way.  There was nothing to open properties window, just options to add the launcher to desktop or menu bar.  I added the launcher to the desktop and there I was able to open a properties window, but it still did not give me the location of the file.  Under the properties/launcher tab it just said "kompozer" for the launcher but gave no information on the location.  

One problem that we share is being annoyed at not being able to right click a menu launcher to view the command that it runs. :D You can view it by adding the launcher to the desktop and then right-clicking, or you can look at the menu item's entry in the 'alacarte' menu editor (Sytem > Preferences > Main Menu or System > Preferences > Menu Layout).
> 
I did what you told me to add kompozer to the list, but instead of entering the location I just entered "kompozer" and it worked.

However, I don't understand what is going on behind the scenes.  How does the system know where kompozer is located, and how do I get that info?  This is actually less intuitive and gives me less info than windows, although I am sure that is just because I don't understand it all yet.

You are very right that the system knows where kompozer is even if you just type "kompozer". Here's a brief explanation:

First, the 'shell' is the program with which you interact when you open a terminal (at Applications > Accessories > Terminal). In our case, it is called 'bash' (or Bourne Again SHell).

Open a terminal and type ```
env
``` to run the program called 'env'. These are your "environment variables", and they define the way the computer does certain things. One of the variables is your PATH variable, you can view it's contents alone by typing ```
echo $PATH
``` to run the 'echo' program, which will output the contents of a variable, among many other things. The '$' before the name of the variable tells the shell (the program with which you are interacting in your terminal) to replace the variable name with the actual contents of what the variable is storing. The PATH tells the computer where to look for executable files (or binary files...in Windows, .exe files). Mine looks something like this, yours will look similar:
```
/home/jeff/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
The idea is this: when I type "kompozer" in the terminal (which is actually what happens when you click the menu launcher shortcut in Application > etc.), the computer looks for /home/jeff/bin/kompozer, and if it doesn't find it, it looks for /usr/local/bin/kompozer, and so on until it finds the executable file.

It's important to keep in mind that every program is essentially being run from the shell, even if there's a fancy graphical user interface which doesn't show the output.

Tell me if you have any other questions! :D

---

