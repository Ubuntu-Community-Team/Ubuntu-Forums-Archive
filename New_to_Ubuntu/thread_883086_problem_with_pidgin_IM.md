---
title: "problem with pidgin IM"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by c-man01 on 2008-08-07
I have a problem with pidgin.  everytime I go to open it, it starts to open and load up but then it just closes.  I don't get any error messages or anything like that, it just won't open.  Any Suggestions?

---

### Post by kane77 on 2008-08-07
> **c-man01 said:**
> I have a problem with pidgin.  everytime I go to open it, it starts to open and load up but then it just closes.  I don't get any error messages or anything like that, it just won't open.  Any Suggestions?

you could try running it in the terminal and see what error message does it give you..

---

### Post by nkri on 2008-08-07
Do you mean your buddy list doesn't pop up, or the entire program just stops?  The buddy list doesn't open automatically by default (I think you can set this in preferences); when you open it, there should be an icon with a green circle somewhere in the top panel.  Right-click on this and click "Show Buddy List."

Good luck!
-nkri

---

### Post by c-man01 on 2008-08-07
The entire program stops.

---

### Post by perlluver on 2008-08-07
Could you please run it from the terminal, Applications>Accessories>Terminal, type pidgin, press enter, and give us the results.

---

### Post by LowSky on 2008-08-07
go to /home folder hit Ctrl+h and delete the .pidgin folder. now restart pidgin, what happens?

---

### Post by ConMan318 on 2008-08-07
Mine does that if Pidgin is already open.  Did you do File -> Exit to close it or Crtl + Q?  If you didn't, it is still running.  I don't know why opening it when it's already open does not just show the window, but mine just says it's opening and then nothing happens.  I've been befuddled by this before without realizing it was running.  Is there a Pidgin icon in your taskbar by the clock?

---

### Post by steveneddy on 2008-08-07
One of the first things you could try is a concept that actually seems to work in Linux as opposed to Windows.

Open Synaptic Package Manager, click all that has to do with Pidgen, and simply reinstall.

Then try it again.

I would also take advise and delete the .pidgen folder from your /home before reinstalling.

Firefox acts weird on me sometimes and every once in a while I'll just reinstall.

---

### Post by Rplus9 on 2008-10-19
I'm having the same problem, there is no .pidgin folder in my home, when I use the icon it pretends to load then nothing

from terminal it says there is no such program

I've also tried the reinstall package.

any other ideas?

---

### Post by m_duck on 2008-10-19
Pidgin stores its stuff in .purple in your home directory, rather than .pidgin.

---

### Post by Rplus9 on 2008-10-21
well deleting that folder gets me a menu but soon as I add a login it poofs away, no icon no window.

any ideas why it's so shy?

---

### Post by RamR on 2008-10-27
I have this problem too and when I open it in Terminal I get "Segmentation fault".

---

### Post by RamR on 2008-11-05
I am still having this problem with 8.10 and it is really bugging me.

---

### Post by Rplus9 on 2008-11-05
I renamed the .purple folder, then opened pidgen, reset the proxy to direct connect and it worked for me.  then I could copy the old .purple folder contents into the new .purple folder to get all my accounts and stuff back.

---

