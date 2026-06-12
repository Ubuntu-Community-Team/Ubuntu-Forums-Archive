---
title: "friend gave me her desktop with ubuntu, can t get internet"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by lucalondon on 2011-12-14
hi

so this is going to sound very lame but i m useless with anything computer-related.
My friend gave me her old computer then left for holidays.
i opened it, and it uses ubuntu. I try to use it but it wont work with the wireless adaptor i bought today.
my friend says by text i just have to scroll down on first screen to find windows... but i can find it.

So what should i do ?

thanks ! i can explain better if anyone doesnt get what i mean :(

xoxo
Luca

---

### Post by DaveyG on 2011-12-14
Does the Windows installation show up from the main (grub) menu (when you switch the desktop on)?

---

### Post by pakopako on 2011-12-14
Two parts to my answer:

> **lucalondon said:**
> i opened it, and it uses ubuntu. I try to use it but it wont work with the wireless adaptor i bought today.
Would you happen to know what version of Ubuntu the computer is using?  (10.04, 11.04, 11.10... these will show up as the computer is starting  up.)
I have a basic install of 11.04, and after logging in, in the upper-right hand corner is this pizza slice-shaped icon next to the clock and envelope and audio buttons. That handles WiFi searching. When I left-click, a drop down menu will show me all the available networks nearby. If I plug in a 2nd WiFi card, the drop-down menu gets longer. (So I'll see "Network 1, Network 2, Network 3"... and then another set of "Network 1, Network 2, Network 3")

> **lucalondon said:**
> my friend says by text i just have to scroll down on first screen to find windows... but i can find it.
When a computer has two operating systems (in your case, Ubuntu and Windows), a user is given a menu for a few seconds to choose which one they want to enter. Depending on how your friend set it, the menu can stay on screen for 1 minute or just 1 second before disappearing.

If you have a desktop (or even laptop), pay attention to the screen as soon as you start the computer up.
After the computer brand-logo vanishes (or in some cases a memory check, or other things), start pressing the arrow keys. Any arrow keys. Just start pressing them. (My friend sets their OS menu choice to be 2 seconds... you see it flicker by really fast so if I wasn't expecting it, I would miss my chance.)

Why? When the menu pops up, if you press any key, the timer that causes the menu to vanish will stop and you will have all the time you need to choose another OS. So now you can use the arrow keys normally to move up and down to highlight Windows and press Enter to go start using it.

---

### Post by Mark Phelps on 2011-12-14
If the PC was set up using GRUB to select the OSs, and it was set to default to Ubuntu, you may not actually see a selection menu.

So, presuming this is a current version of Ubuntu, hold down a SHIFT key after you start the PC. That should eventually produce a text menu with Ubuntu kernels listed at the top.  Somewhere in the list, there should be an entry along the lines of "Windows (Loader) on XXX". That is the entry you want to select.

If you press the space bar as soon as the menu appears, that will stop the countdown time and you can then take as long as you want to make a selection.

---

### Post by lucalondon on 2011-12-14
yes !! you are right :) 
there was black screen for 2 seconds with ubuntu 8.4 then i used the arrow and scrolled down and found windows ! yay :) 

Thanks very much both of you for your answers.

So..... now that i m here ... whats Ubuntu ? why do people use it instead of windows ? 
x
x
x
Luca

---

### Post by pakopako on 2011-12-14
> **lucalondon said:**
> yes !! you are right :) 
there was black screen for 2 seconds with ubuntu 8.4 then i used the arrow and scrolled down and found windows ! yay :)
...

So..... now that i m here ... whats Ubuntu ? why do people use it instead of windows ? 

Glad to see you're up and running. Please select "Thread Tools" at the top of this thread and click on "SOLVED" so future users can see how to solve this issue. :D

As for what Ubuntu is, it is another [Operating System]("http://en.wikipedia.org/wiki/Operating_System"). Like Windows. Or Apple Snow Leopard. Or Android. Or even what keeps the PS3 running. It's an all-encompassing piece of software created to utilize hardware. Usually, specific hardware requires specific software (like the Playstation 3 example), but in the case of your friend's computer, sometimes a machine can use another OS

*Why* people use Ubuntu instead of Windows...? Well, that answer varies from user to user.

Personally, I like it because it is different from Windows. I have an older machine and it takes about 5 minutes from power-on to login under Windows XP, and then I have to wait for that hour-glass to change into my mouse cursor.  And the computer it's too old to install Windows 7.

I use Ubuntu 11.04 and it takes 30 seconds from power-on to logging in and starting my web-browser.:eek: I still keep Windows around for some of my more detailed art-programs (and of course fun and games), so I have a boot-choice at tpower-on, just like your friend's computer.

---

