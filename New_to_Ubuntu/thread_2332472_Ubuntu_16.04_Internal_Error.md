---
title: "Ubuntu 16.04 Internal Error"
date: 2016-08-01
forum: New to Ubuntu
---

### Post by barisius772 on 2016-08-01
Hi, I'm new to ubuntu and recently i just installed Ubuntu 16.04 LTS from usb. It works well on my thinkpad T460 for several days until the internal error occured today. I tried restarting my laptop, then log in. However, when i logged in, the launcher and the menu bar (File, Edit, View bar) are gone. I am not sure what the internal error details are since i didn't screenshot and remember them. 

Any help is appreciated, thank you.

*note: I have updated my Ubuntu 16.04 LTS to 16.04.01 from the command sudo apt-get upgrade and I've also sudo apt-get update. So the Ubuntu I'm using is already up-to-date.
         The terminal seems to be working but needed to be opened by ctrl-alt-T
         I'm typing this thread from firefox and i opened the firefox by typing firefox on the terminal.

---

### Post by mook765 on 2016-08-01
> 
**apt-get update** updates the list of available packages and their versions, but it does not install or upgrade any packages.


  **apt-get upgrade** actually installs newer versions of  the packages you have. After updating the lists, the package manager
  knows about available updates for the software you have installed. This  is why you first want to update.



So, if you sudo apt-get upgrade first and sudo apt-get update second, i don't know what will happen to the sytem.

As your Ubuntu is still fresh installed, maybe it is the easiest just to reinstall.
But you also may wait for some more replies, maybe one of the gurus here know how to solve this...

---

### Post by grahammechanical on 2016-08-01
> the menu bar (File, Edit, View bar)

That only appears in the top panel on the left when we have an application window open and mouse over the left end of the top panel. In System Settings>Appearance>Behaviour tab we can select to have those application menus always displayed or appear in the window's title bar instead of the top panel (menu bar).

Is the launcher "gone" or hidden? Auto-hide the launcher can also be turned off in the Appearance utility. Without more information about the system error we cannot give advice or even be sure if it is connected to the issues you tell us about. These kind of system errors usually appear every time we restart Ubuntu. Untick the box "Report the crash" and click on "Details" to find out what is causing the error.

The terminal is not in the Launcher by default. Can you open the Dash? Do you have app-indicators in the top panel on the right? If the Unity user interface is really not appearing then we can right click the desktop wallpaper and select Change Desktop Background from the menu. That will open System Settings at the Appearance utility. From there we can get to the main System Settings window and select Software & Updates>Additional Drivers tab and change video drivers. That might fix things. We need to be connected to the internet and to allow the utility time to do is job.

Right clicking the wallpaper is another way to open the terminal. The menu has the option Open Terminal.

Regards.

---

### Post by barisius772 on 2016-08-01
Hello mook765 and grahammechanical, thank you for your replies! However, due to my lack of patience to learn more about Ubuntu, I've reinstalled my Ubuntu yesterday...
Everything is working fine for now.

Anyway, should I continue this thread?

---

### Post by mook765 on 2016-08-02
Your problem is solved now, so it doesn't make sense to continue this thread.
When you have a new problem, you are always welcome to open a new thread.
Happy learning and good luck...:)

---

### Post by RobGoss on 2016-08-03
If you have solved your problem would you mind marking this thread as solved. You can do this by using the **Thread Tool**  at the top of this post

---

