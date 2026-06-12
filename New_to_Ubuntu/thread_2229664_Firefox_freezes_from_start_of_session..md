---
title: "Firefox freezes from start of session."
date: 2014-06-14
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-14
I wonder if someone can assist me with this problem please.

I installed Ubuntu 14.04 about 4 weeks ago, dual booting with Windows 7. I have been trying to install, using WINE, a program designed for Windows. At present the program does not run as it should. In the last few days I had a logging in problem but, with the help of this Forum, this has been solved. All this is background to another problem which arose about the same time as the logging in problem.

I am finding that Firefox freezes at the start of every Ubuntu session, so for the present I have removed Firefox. I kept getting a message saying 'This window is not responding'. The Ubuntu browser does seem to work however. Nevertheless, what is more worrying is that the hard drive runs very fast,and continuously, while I am in Ubuntu. I don't know much about the working of computers but I guess something is going on that shouldn't be.

I used Terminal to get into the command 'top' which shows active processes. This showed something named 'dconf-servi+' using 57.7% of the CPU. Something else named 'compiz' was using 32.5% of the CPU. I have no idea if these figures mean very much I'm afraid. 

Can any one tell me what I should be doing to pin point the reason, and preventing the freezing of Firefox and the fast running of the hard drive please?

---

### Post by ajgreeny on 2014-06-14
Reinstall FF and then try two things.

First, rename the hidden** .mozilla** folder in your home as **.mozilla-old**, then try FF again to see if everything works OK.  Now close FF and rename the .mozilla-old  back to .mozilla.
then
Second, start FF in safe mode with command** firefox -safe-mode** and see if the freezing is now gone.

The first test with a new profile will show you if the problem is something in your own old profile.
If it is OK running in safe mode, it is almost certainly one of the add-ons or extensions of FF that is your problem that is the problem, so disable them all while running in safe mode and the restart in normal mode to see if all is still OK.  You can then enable them one by one to see which one causes the problem.

I think, however, you have greater problems than that with the top output you mention.  Compiz is a requirement of unity, but should not need such a high CPU usage, so I wonder if you have other graphic problems; what is your graphic card and other hardware, please?
I'm not sure about the dconf-servi+ process, but again I do know it should not need 57% cpu, so something is wrong there as well.

---

### Post by gordon99 on 2014-06-14
I think you are correct aj. I now find I cannot even download FF. My computer is HP Presario Compaq CQ56 Notebook.
The graphics card is AMD M880G with ATI Mobility Radeon HD4250. Windows 7 is working ok. I guess I have messed up somehow and will probably have to uninstall and reinstall Ubuntu once I find out what's involved in doing this. I will try again to download FF, or anything else that should download, and if I have success I will come back for more help.

---

### Post by gordon99 on 2014-06-19
Have recently had to re-install Ubuntu to get me out of my misery.

---

