---
title: "Shortcut from terminal"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by bob brazie on 2012-05-28
I just installed a nifty calculator tool that needs to run from a terminal. Tapecalc.

Is there a way to add either a short cut icon (or an icon in the dash application area) or a short cut key combination so I can run this without opening a terminal and then remembering what the app's name is and then entering tapecalc in the terminal window to start it.

Thanks in advance. Bob.

---

### Post by codingman on 2012-05-28
What DE?

---

### Post by Senior_Buckethead on 2012-05-28
go to terminal and type: whereis tapecalc

If you want to put a shortcut on your desktop go to your ~/Desktop directory in terminal and enter 
```

sudo ln -s /usr/bin/tapecalc 

```
(assuming its installed in your usr/bin directory.

Glenn.

---

### Post by bob brazie on 2012-05-28
What?

---

### Post by Senior_Buckethead on 2012-05-28
how did you install tapecalc? Did you use Ubuntu software center to do so? If so,, Tapecalc should have installed a shortcut in unity (the thing thats on the left hand side of your screen with the icons on it. Click on the windows button on your keyboard, when unity opens, in the search bar at the top, type in Tapecalc and press enter.

This is from memory since I got rid of unity and use gnome desktop.

The instructions I gave you before was how to put an icon on your desktop (think MS Windows).

---

### Post by bob brazie on 2012-05-28
A little new to this. How do I go to my ~/Desktop directory in terminal and enter?

---

### Post by bob brazie on 2012-05-28
Yes through the software center. It did not install an icon to the left and it does not show up in the unity area.

Tapecalc can only be run in a terminal it said in the software center.

---

### Post by Senior_Buckethead on 2012-05-28
ok, if you go to unity search ( remember the windows key on your keyboard) and type in 'terminal' into your search box it will bring up terminal.
once thats open, simply type in 
```

glenn@acer:~$ tapecalc

```
(disregard the glenn@acer, thats  my terminal prompt, yours will be different).
tapecalc should run.

If you get any errors doing that, post them here.

---

### Post by mc4man on 2012-05-28
> **bob brazie said:**
> I just installed a nifty calculator tool that needs to run from a terminal. Tapecalc.

Is there a way to add either a short cut icon (or an icon in the dash application area) or a short cut key combination so I can run this without opening a terminal and then remembering what the app's name is and then entering tapecalc in the terminal window to start it.

Thanks in advance. Bob.

You can do this in many ways though in unity there can only be 1 controlling launcher icon for gnome-terminal at a time (unless you set up a separate profile which is more than is needed here

So it only depends on what you want to do - 

I'd probably just add gnome-terminal to the unity launcher, then create a quicklist option to run tapecalc. Very easy to do & a bit 'cleaner'
see screen 1

Or you could create a separate tapecalc .desktop - then the icon could be added to the launcher or run from the Dash. Screens 2 & 3
In this case there are some scenarios that aren't great but if you wish this can be worked around to some extent
Don't really recommend

The 3rd option would be to just create a desktop launcher that you click on, that would work ok & not really interfere too much with another terminal running in a launcher icon 

So all of these are easily done - I'd go with the quicklist, if so post what release of Ubuntu you are using

---

### Post by bob brazie on 2012-05-28
What will that command do/create?

---

### Post by bob brazie on 2012-05-28
The new and improved 12.04 of course. <g>

---

### Post by Senior_Buckethead on 2012-05-28
send me a pm and ill give you my email. Sounds like you need a hand.

Glenn.

---

### Post by gnusci on 2012-05-28
Press "Alt+F2" and input this command

gnome-desktop-item-edit --create-new ~/.local/share/applications

add a name and in the command line add:

gnome-terminal -x mc  (EDIT: change mc for your command)

and a comment that it will show as a tooltip.

Then open Nautilus and from the menu "View" check "Show Hidden Files".

Then go to ~/.local/share/applications, in this directory you should see the created icon, just drag the icon with the mouse on the Launcher.

You can also put the icon in the Desktop.

---

### Post by bob brazie on 2012-05-29
gnome-terminal -x mc (EDIT: change mc for your command)

Would the mc be the word tapecalc?

---

### Post by bob brazie on 2012-05-29
I'd probably just add gnome-terminal to the unity launcher, then create a quicklist option to run tapecalc. Very easy to do & a bit 'cleaner'
see screen 1

How to create a quick list option?
My tapecalk does not show an icon when it runs.

---

### Post by bob brazie on 2012-05-30
"gnome-desktop-item-edit --create-new ~/.local/share/applications"

In 12.04 (which I am using) it is in file system/user/share/applications.

Is that what ~/. means?

What would the command look like for this and is MC the word tapecalk?

Thanks in advance. Bob.

---

### Post by bob brazie on 2012-05-31
Could you explain to me how to go the the desktop in terminal?

You wrote: 
If you want to put a shortcut on your desktop go to your ~/Desktop directory in terminal and enter

---

### Post by Derek Karpinski on 2012-05-31
> **bob brazie said:**
> Could you explain to me how to go the the desktop in terminal?

You wrote: 
If you want to put a shortcut on your desktop go to your ~/Desktop directory in terminal and enter

```
cd ~/Desktop
```

---

