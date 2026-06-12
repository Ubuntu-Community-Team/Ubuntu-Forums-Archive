---
title: "how to drag and drop applications on task bar"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by FuturePerfect on 2008-05-17
In Ubuntu,
How to change location of minimized applications on the task bar 

WHAT IS THIS FEATURE?

You can drag and drop applications in the task bar so they are located anywhere in the task bar you want.  (In XP, this feature is part of add-on programs ButtonBoogie 2 or Taskbar Shuffle).

WHY DID I DO THIS WRITE-UP ABOUT THIS FEATURE?

Although this feature how-to may seem obvious after reading this, it wasn't obvious to nontechnical me when I was going crazy using trial and error trying to make it work (I heard of this on the Internet but couldn't find a how-to)--I couldn't figure out which keys to click, and mouse buttons to press, in what order, and in what circumstances so it always worked (i.e. solve the maddening puzzle of why it sometimes worked and sometimes didn't).  

So in the hopes that this will save tiem for other nontechnical people, I've included this long (hopefully complete) explanation:  

WHY DO YOU WANT TO LEARN THIS FEATURE?

This nice feature of the last two Ubuntu (really Gnome) releases is the ability to drag applications to any place you like on the taskbar.  This is particularly good if you have a lot of applications open and want a related few next to each other for easy access (e.g. explanatory browser window next to a photo editor window next to a Nautilus window to see your files).

DISCLAIMER

I tested this thoroughly running Ubuntu 8.04 in VMware player (an old release 1) running under the latest Windows XP patch level.  I think this works anywhere but I tested only this.  Also I may have used Windows rather than Gnome nomenclature due to my bad.

HOW TO MAKE THIS FEATURE WORK

I.E. How to drag and drop minimized applications on the taskbar in 4 easy steps:

1) Depress and hold the Shift key down

2) Left Click the mouse AND HOLD THAT CLICK KEY DOWN on a minimized application on the taskbar that you want to relocate to another position on the taskbar (THEN release the Shift key, or, if you prefer, you can continue to hold it down).  

3) Drag a little window that appears to the position of another application on the taskbar where you want to reposition it.

4) BEING CAREFUL THAT THE TOP OF THE LITTLE WINDOW ENDS UP NOT EXCEEDING THE TASKBAR HEIGHT, drop the application by releasing the Left Click (if you're still holding the Shift key, you can release the Shift key before or after you release the Left Clock)

NOTE:  I say make sure the little window ENDS UP not exceeding the task bar height, because, as long as you're HOLDING DOWN the Left Click button, you won't end the drag and drop by dragging the little window anywhere on the screen to see it--just make sure when you're ready to drop it on the application on the taskbar where you want to reposition it, that the little window does not exceed the task bar height.  In fact, you may WANT to occasionally drag the little window up into full view because it shows the icon of the program you're dragging to reposition, so, in case you forget what program this is, the icon can remind you.

NOTE:  I say depress Shift key first because if you tentatively Left Click first you may unwantedly maximize the application (if you do things right, you can Left Click first if you prefer).

NOTE:  for those of you new to this kind of drag and drop, when you drop the application it doesn't swap place with the other application, it MOVES OVER all the applications.  An example-- minimized applications A B C D E; horizontal task bar at top:

-current applications in order left to right:  A B C D E
drag & drop right D to left B, order is now:   A D B C E
Thus:  when you drag an application from right to left,
       it takes the position of the application you dropped it on
        and moves over to the right that application 
        and all other applications remaining on the right

-current applications in order left to right:  A B C D E
drag & drop left B to right D, order is now:   A C D B E
Thus:  when you drag an application from left to right, 
       it takes the position of the application you dropped it on
       and moves over to the left that application 
       and all other applications remaining on the left.

       (This interface is not the same as a drag and drop of a tab in Firefox, where the actual INTERSECTION of two adjacent tabs is highlighted when you drag a tab there so you can see exactly where between adjacent tabs your dragged tab will go.)

NOTE:  the Alt key appears to work too, but ONLY if you FIRST Left Click BEFORE you depress the Alt key (whereas if you use the Shift key you may depress it BEFORE OR AFTER the Left Click).
[Although there would seem to be no reason to use the Caps Lock key because it changes case, Caps Lock key also works for dragging and dropping both before or after the Left Click].

NOTE:  when you drag the minimized application across the taskbar to the new desired location, make sure that a little window it shows doesn't exceeds the taskbar height:
       EXPLANATION:  when you drag a minimized application, you are dragging a little window that will be visible if you move the cursor so that it is around the middle of the height of the taskbar (measured from where the taskbar is anchored).  If you move the cursor so that this little window height EXCEEDS the height of the taskbar, THE DRAG WILL NOT WORK (you will see the little window fizzle back to its original taskbar location)

                     (One ADVANTAGE of this approach is that if you grab the wrong window <or get lost where you are dragging> and want the original minimized application to stay where it is on the taskbar, you can just drag the little window so it exceeds the taskbar height, and the app will automatically fizzle back to its original taskbar location <without you having to refind that and painstakingly drag the little window back to that origin>.)

NOTE:  another way you'll know that this drag will work is when you drag the little window to the minimized app, the app WILL HAVE ITS BORDER HIGHLIGHTED (if the little window height exceeds taskbar height, this border highlighting will turn off).

NOTE:  still another way you will knows that this drag will work is when you drag the little window to the minimized app, the little window WILL SHOW A LITTLE OUTLINE ARROW IN ITS UPPER LEFT-HAND CORNER (if the little window height exceeds taskbar height, this little outline arrow will disappear).

---

