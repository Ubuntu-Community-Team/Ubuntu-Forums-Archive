---
title: "Create a new right-click menu for scrollbar arrows?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by L a r r y on 2008-06-27
Hello,
I have found how to add items to the right-click menu by visiting
some earlier posts, and my new command appears whenever I right-click
on any icon on my desktop.  See this forum thread for instructions:

[http://ubuntuforums.org/showthread.php?t=264500](http://ubuntuforums.org/showthread.php?t=264500)

> **SavageBeginner said:**
> Check out the 'nautilus-actions' package. 

To install:
```
sudo apt-get install nautilus-actions
```
To configure:
```
nautilus-actions-config
```

I then was presented with an Add to Menu dialog, hit Add and filled
in the form to add this command to the menu.

I browsed for the "nautilus-actions-config" command and when done
filling the form, I closed the window.

I logged out and logged back in again before I saw the Add to Menu
option in the right-click menus for file icons, but not for folder
icons or for the Desktop.

I would like to create a new menu that appears when I right-click
on the down-arrows and up-arrows on the vertical scrollbar.  
I guess I could open some of the nautilus-actions-xxx commands 
and see what they offer.

I wanted to add my thanks to SavageBeginner, and maybe
I will get the chance when I complete a reply in the 
above-mentioned thread.

Googling this forum has really brought me a wealth of
related posts!

Has anyone any advice on how or if I can add a 
right-click menu to the scroll arrows?  I want to have 
the choice presented when scrolling down to scroll here 
or to go to the bottom of the page.  And when scrolling 
up to scroll here or go to the top of the page.

Thanks in advance!

---

### Post by L a r r y on 2008-07-06
I have an alternate solution to this problem of laying the heavy finger on the right-click button on my mouse.  I reassigned the right-click function to my top thumb button, and while I was at it I added double-click to my bottom thumb button.

See this tutorial for how it is done:
[http://ubuntuforums.org/showthread.php?t=787790]("http://ubuntuforums.org/showthread.php?t=787790")

Swapping my do-nothing thumb button with my right mouse button leaves me occasionally trying to right-click and remembering I have to thumb-click instead, but at least I avoid that top-of-page or end-of-page move when I am in the midst of reading something.  I notice also, that was added since 6.06, which I am running in the other room because that computer won't run 8.04.

I am wondering, if instead of finding a way to script a menu into Nautilus, if there is a config file that I can change to rid myself of that option.  I will call this case solved, now that I have found a work-around.

---

### Post by L a r r y on 2008-10-31
Hello,
I would like to re-open this thread and ask again if there is a way to edit the way Nautilus behaves  when I right-click the down-arrow button on the right-hand slide bar.

When the button is left-clicked, it advances the screen one line and when it is right-clicked it goes to the end of the document.

All well and fine if you have steady hands on the mouse.

I prefer a menu to appear on the right-click to give me the choice of scrolling one line or going to mthe end.  This way, my shaky hand doesn't send me to the end of the (swear at the computer) document *again.*

It is very frustrating.

I discovered that when I "solved" this problem, by reassigning my right mouse button to a thumb button on my mouse and assigning nothing to the right button, Firefox decided to send me back a page in history if the mouse pointer was on the web page.  That drew as many cuss words as the original complaint, whereas with the mouse right-click button assigned as normal, I came up with the context menu coming up, and a simple left clock would solve that issue.

Now, were there to be a menu come up on that up-arrow or down-arrow button on the slide bar, I could click that nuisance away and continue reading.

I want to vote for clean air if I can, if someone can please point me to the file I need to change and what I need to do with it.

I have made a considerable progress with  Ubuntu 8.04, and with Wine I have successfully made Windows programs work, including Cool Edit 96, a sound editor, IrfanView, a photo editor, Winamp, with limited success, Mailto Obfuscator, and EchoLink, an amateur radio software.

I have retooled gedit to let me edit my xhtml web site and done some photo editing with gimp.  I wrote a perl script to do the task of Mailto Obfuscator, and it works, the Windows program just has a little more convenience.  
There was what appeared to be a neat Web editor that ran in 6.06, called Screem, but it doesn't work as well in the current version, and I have looked at Bluefish.

Having said all of that, I would love to see a way to rid myself of this right-click issue, once and for all.  

Thanks.

---

