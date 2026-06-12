---
title: "Help with touchpad!"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by Roody4U on 2012-02-16
Hello all. I've played around with Ubuntu in the past, but would still be called a newbie. I just downloaded Ubuntu 11.10 and installed via wubi. My touchpad however is useless. It it recognized in some form, but when you touch it (no matter how you touch it) the cursor just jump to the top right corn of the screen and can do nothing else. Can turn it on and off via fn-f7 but that's not the problem. It just does nothing but jump and move to the corner. I don't has a usb mouse, this is my only tool for a mouse. I'm using an Acer One. Intel atom netbook. PLEASE HELP! Never had this issue in previous ubuntu's

---

### Post by Scott Baker on 2012-02-16
Howdy, hope this helps. Open the software center. In the search box,  enter the term "pointing devices". This will pull up a program called "pointing devices" ( real surprise, right?) Download that to your machine. Log out, then log back in. You'll now find that program installed and ready for use. It works quite well and should solve your headaches. Good luck.  ](*,)

---

### Post by Roody4U on 2012-02-16
Where is software center? Last Ubuntu I had was 10. 11.10 is not as cut and dry.

---

### Post by anewguy on 2012-02-16
11.10, by default, uses the Unity desktop.  As such, you won't see the familiar things on the top bar.  Instead, Unity has a "dash board" that by default is on the left of the screen (if it's not showing, hold your mouse as far to the left as possible - since your touchpad isn't working, temporarily just use a mouse - and it should pop in).  Part way down that column of larger icons you will see what looks like a box at a party, for lack of better terms.  That is the software center (it will say so if you hold your mouse over it).  Just single-click and it will bring up the software center.

If you don't have a mouse to use, try borrowing one.  It will only take you 10 minutes to find out if this all works for you.  Whatever the result, you can return the mouse right away.

Let us know if you are having problems, as there are other things to try.

dave ;)

---

### Post by Scott Baker on 2012-02-16
Back again, and I've got a couple of things for you here. First, the software center is the icon that looks like the shopping bag, on the launcher ( the bar on the very left side of your screen ). Next, if Unity ( the current desktop ) is not your bag of cookies, you can install a version of the "classic" desktop for use. It's not exactly the same as the earlier versions, but it's pretty close. To do this, follow along. Dash home > more apps > installed. Click "see more" on this. Go down to the "terminal" program, and open that. You'll get a small screen that looks like an early computer screen, with your user info on it. next to that info, type the following; [FONT=Verdana][COLOR=Blue]sudo apt-get install gnome-panel [/COLOR][/FONT][COLOR=Black]then hit enter. You'll be asked for your user ID. Enter that number, then hit enter again. In a few moments [/COLOR]you'll see some codes flash across that screen. When it gets back to the information you first saw ( your user info ), your done. Close that terminal, log out ( if you choose ) then log back in. At the log-in screen, click the gear, and you'll find the new classic option available for use. Good luck, hope this all helps.

---

### Post by anewguy on 2012-02-16
And his biggest trick is that he's going to need a mouse before he can do any suggestions.  Can't use touchpad - aren't going to scroll over the unity menu and make a selection.

hence my suggestion on using a mouse.

Also, gsynaptics can be installed straight from the command line -

- ctrl/alt and push F2
- login using your normal userid and password
- at the prompt type:

sudo apt-get install gsynaptics <press enter>

It will prompt for a password - this is your normal password, and nothing shows on the screen as you type it.

- reboot

- try touchpad again.

If not the synaptic brand/type, there are other touchpad drivers to load as well.

dave ;)

---

### Post by Roody4U on 2012-02-17
I'd like to thank all that posted advice. Ironicall, I ended up needing none of it. Perhaps it's just a glitch (and also I may not have permanantly fixed the problem, but for now it does the trick. As expected I could not get to the dash without a mouse, so I ended up repeatedly hitting the fn-f7. After a while I noticed that if I held down fn and wiggled my finger on the touchpad it seemed to calibrate itself and works fine. After a few restarts the problem arose once more and the same trick worked again. Again, I see no rhyme or reason to why this would work, but for me it did. I wrote down all of the info you people have posted just in case this stops working for me. And thanks to the suggestion about getting the "classic" desktop. For now I kinda like the unity setup, but if I ever want that to change, it's good to know. Also, in my old Ubuntu (Jaunty I believe) I found some programs and scripts that help change the appearance to look like a Mac desktop. Is that still possible under the Unity setup? If anyone knows let me know. Thanks again for all the help!! 

Christian

---

### Post by wolfen69 on 2012-02-17
> **Roody4U said:**
> 
As expected I could not get to the dash without a mouse


Hitting the windows(super) key will bring it up.

---

