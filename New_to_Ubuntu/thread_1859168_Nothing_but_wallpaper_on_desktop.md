---
title: "Nothing but wallpaper on desktop"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by oldstumpy on 2011-10-13
HI:I need help with ubuntu 11.04 natty classic please when i start ubuntu it boots ok but when i get to desktop i have no start menu no task bar nothing but my desktop wallpaper and  rainlendar my calendar on my desktop don't ask how i got here it is a long story i need to get my start menu and taskbar back can any one please help.Thanks oldstumpy:(

---

### Post by kolinab on 2011-10-13
Hi oldstumpy,

I know how you feel. Ubuntu has a new interface in version 11.04 called Unity. It is a little different but you can learn how to find the things you are looking for if you explore a little bit. In Unity, there is no bottom task bar, and the main menu is not quite where it used to be. The main functions of selecting applications can be found on the 'launcher' which is the vertical panel on the left side of the screen. If you can't see it, push the mouse cursor against the left side of the screen and it should pop up.

Next, you can click the small Ubuntu logo in the top left corner of the screen. This panel brings up a screen where you can search for the applications you need. If you start typing the name of the application you want it will show up in the search results. 

There are a number of guides for people new to Unity - I'm still getting used to it myself. 

Look here for an example of such a guide:

[http://omgubuntu.co.uk/natty/](http://omgubuntu.co.uk/natty/)

I found it by searching for 'introduction to ubuntu unity' in Google. 

If you have more problems, post back to the forums and we'll try to help you out!

Kolin

---

### Post by oldstumpy on 2011-10-13
Thanks Kolin but that is the problem i am running my desktop in classic mode and don't have those things on my desktop i have no way to navigate from my desk top other than i had to create a empty file to open and get to my home folder and then i go to help and click on online help to get here i really need some sort of solution to find my
start menus agian.Thanks for trying,Oldstumpy Anybody else out there have a solution.

---

### Post by kolinab on 2011-10-13
OK, sorry I misunderstood your problem! I'm sorry I can't think of what to tell you since I have never even tried classic mode. I'm sure someone out there will have some good ideas for you.

---

### Post by westie457 on 2011-10-13
> **oldstumpy said:**
> Thanks Kolin but that is the problem i am running my desktop in classic mode and don't have those things on my desktop i have no way to navigate from my desk top other than i had to create a empty file to open and get to my home folder and then i go to help and click on online help to get here i really need some sort of solution to find my
start menus agian.Thanks for trying,Oldstumpy Anybody else out there have a solution.

Try this in a terminal ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

If any errors post them back here please.

---

### Post by madjr on 2011-10-13
not sure what happened exactly with your classic interface..

but does unity work or has same issue?

also **11.10** was just released in case you want to test it from live-cd or usb.

other than that if trying to fix it fails, last resort would be reinstalling or upgrading...

---

### Post by oldstumpy on 2011-10-13
Hi:westie457,I have no way to bring up terminal i really have no way to navigate.

---

### Post by westie457 on 2011-10-13
> **oldstumpy said:**
> Hi:westie457,I have no way to bring up terminal i really have no way to navigate.

Sorry my fault. Press Ctrl+Alt+t at the same time. This will open a terminal for you.

---

### Post by PNY on 2011-10-13
Hi. just a thought. if you can find a way to log out (if you have set up to automatic login when the computer starts) or when you log in (if you are not set to automatic login) then at the log in screen it gives you the opportunity to chose what window manager you want to log in with. If you change window manager to a different one in the drop down menu then that may just do it.

just a thought... hope it helps.

A

---

### Post by oldstumpy on 2011-10-13
Thanks Westie457 ill try that and let you know in a view hope i can do this not to good with terminals i really neebe
to ubuntu lost my wendows xp so i went to ubuntu oldstumpy i will post reply in a few minutes

---

### Post by oldstumpy on 2011-10-13
Hi Westi457,tried that but got no process found do i need to type anything before that oldstumpy

---

### Post by westie457 on 2011-10-13
> **oldstumpy said:**
> Hi Westi457,tried that but got no process found do i need to type anything before that oldstumpy

Its okay was expecting something like that.
In the terminal type in ```
sudo apt-get install gnome-panel
``` not sure though if you will need to log out and back in or reboot to get things working.

---

### Post by oldstumpy on 2011-10-13
Hi:Westi457,Just wanted to say Thank You very very much problem solved that sudo apt-get install gnome-panel did the trick i did have to restart for it to take affect.Thanks Agian oldstumpy.

---

### Post by westie457 on 2011-10-14
You're welcome. Happy Ubuntuing.
Could you mark this 'SOLVED' please using [COLOR="Red"]Thread Tools[/COLOR] at the top of the page.

---

### Post by mörgæs on 2011-10-14
Changed the title to a more descriptive one.

---

