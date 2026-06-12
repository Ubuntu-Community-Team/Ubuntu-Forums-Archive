---
title: "Terminator"
date: 2013-10-30
forum: Programming Talk
---

### Post by crushed26 on 2013-10-30
Please forgive me if I am posting in the wrong place.

I am having an issue with Terminator that I credit as being an issue with the programing. I have contacted terminator and had a brief conversation with, who I believe, is one of the developers. However, due to the fact that the Terminator team is spread thin, the issue was never resolved and was kind of left hanging up in the air. 

I am running the latest version, 97, which I downloaded from the ppa:gnome-terminator repository. I created a layout to where, when I launch terminator with the layout option, it opens the terminal pane, which is split into 4 panes and each pane runs a separate command. Everything worked just fine, the panes were split as they should be and all four commands were running. I got excited because I knew my boss would be happy, as I could now save a tremendous amount of time. I decided to kill one of the commands running in one of the panes so I could start another command; therefore, I clicked inside the pane bringing it into focus and I hit control-c to kill the currently running command...nothing happened. I quickly realized that although the commands were running, I was unable to send control-c and I was unable to send any type of keyboard input to stop the commands. The only way i was able to get the commands to stop was by closing the terminator session. Just as a test, I edited my newly created to only run three commands leaving the fourth pane without a custom command set. I reran terminator with the layout option and the results were the same as before, however I was able to send keyboard input into the pane that was not running a command. I could execute a command and terminate it with control-c with no problem. The other 3 panes running the custom commands were still unresponsive to any type of keyboard input. 

I have been through the config file and I have tried every combination of settings within Terminators right-click preference menu and nothing seems to correct this issue. I have tried setting with many different commands, which makes no difference. I have also tried downloading the current trunk from bzr trunk lp:terminator and the problem still exist there also. 

Can someone please try and recreate this issue and help me solve it or at least point me in the right direction. Terminator is written in python and I am no expert at it, but I am no stranger to python either.

I have attached a screen shot(SS) of the terminator pane. The SS shows the pane split into four panes and running three commands, the fourth pane is free to accept keyboard input.  

Thank you in advance.

---

### Post by ofnuts on 2013-10-30
I don't know terminator but I would be surprised if it didn't provide some way to send the SIGINT signal to the running programs (which is what Ctrl-C does). Look in the menus, or check the doc. Unless your VMWare gets in the way and Terminator doesn't even receive the Ctrl-C in some cases.

You can also use the standard "kill" command in one of the windows to interrupt processes running in other windows.

If you describe your setup in more detail there may be other explanations (operating system where you run terminator, operating systems running the sessions in terminator, etc...)

---

### Post by crushed26 on 2013-10-30
Thank you for your reply. I am running Win 7 with Ubuntus current version installed in VM. SIGINT does work with terminator, but not when using custom layout commands. No, I cannot use the kill command seeing how the panes with the running layout custom commands do not accept any type of key board input.

---

### Post by Habitual on 2013-10-30
Post your ```
~/.config/terminator/config
```

---

### Post by crushed26 on 2013-10-30
thanks, but ~/.config/terminator/config is not the solution. The config file is just copy of what is set in the richt click/preference menu. 

I figured out the issue I am having. When a custom command is used in a layout, the command is executed outside of the parent bash process. By issuing the "bash" command after the opening layout command, you will be returned to the parent bash process and may send control-c or any other command you choose. For example, if you set the layout custom command of "free; bash", you will be able to send control-c.

---

### Post by Habitual on 2013-10-31
yeah, I read this am on that "other forum".

---

### Post by crushed26 on 2013-10-31
haha

---

