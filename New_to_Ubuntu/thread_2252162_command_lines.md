---
title: "command lines"
date: 2014-11-09
forum: New to Ubuntu
---

### Post by Paul_Armstrong on 2014-11-09
hi guys i am obviously brand new to Linux so very sorry for the easy questions, So here is the question i would like to learn to open applications via a command line in terminal hopefully this will get me started with command lines, so for instance i am using thunder mail at the minute and i have to go to the side bar on the left and click on "search your computer and online sources", type in thunder and then click on the icon. I know that there is probably a short cut like alt ctrl and t for terminal but can you open it from terminal if so what would i type and would it be the same for all applications? also are most of the command lines similar to each other as in once you have learned a couple is it pretty easy to pick up the majority of them?

regards
Paul

---

### Post by coldcritter64 on 2014-11-09
For learning to use the command line here is an online source for you to look at, [[COLOR=#0000ff]--this link--[/COLOR]]("http://linuxcommand.org/lc3_learning_the_shell.php").

You can just type in the process name of the application, usually just its name, to start a program from the terminal; for example to open a text editor from the command line type in 
```
gedit
```and then press the return key (enter).

If you read that link contents list all the way through and follow along with the examples used, it may help you a bit, cheers.

---

### Post by CantankRus on 2014-11-09
You can find the start commands by looking at the .desktop files in **/usr/share/applications**
Drag and drop the file into gedit to view and find the **Exec=** line.

You could also list the applications in /usr/share/applications and the corresponding **Exec=** line with this command
which will place a start-commands.txt file in your home directory.
```
sed -nrs '/^(Name|Exec)=/p;${g;p}' /usr/share/applications/*.desktop > ~/start-commands.txt
```

The shell has auto completion so if you are unsure of the start command you type the first couple of letters and press tab.
eg if I enter **fi** and then press tab nothing happens because there is no unique command starting with **fi**.
Pressing tab again will display all commands starting with **fi**.
Then if I enter **fir** and press tab it will autocmplete firefox because it is the only command starting with **fir**.
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR]** fi**
fi              filefrag        find            findmnt         fixcvsdiff      fix-qdf         
fiascotopnm     file-roller     find2perl       firefox         fix_gpg_badsig  
file            filterdiff      findfs          fitstopnm       fixparts        
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **fir**
```
Also make use of the the relevant reference **man**ual for an application.
eg
```
**man** firefox
```

---

### Post by papibe on 2014-11-09
Hi Paul_Armstrong.

Before considering using the terminal, I would recommend a couple of alternatives to launch applications more quickly.

Using the search bar with the super (Windows) key:
```
Super  thunderbird  Enter
```
If you don't other applications with similar names sometimes it is as easy as:
```
Super th  Enter
```

Adding the Thunderbird icon to the Unity launcher. [Here]("http://www.youtube.com/watch?v=GpAG930cQ94")'s how to do it.

Once it is on the launcher, and it is within the first 10 icons (top to bottom), say 4th, you can press super+4 to quickly open it. Note that when you press and hold super, you can see the corresponding numbers over the applications' icons.

Finally, you could set your own personal shortcut for Thunderbird: Open 'Keyboard' and then switch to the 'Shortcuts' tab. Press the '+' button on the bottom of the left list. Then enter this in the new window:
```
Name: Thunderbird
Command: /usr/bin/thunderbird

```
Once you see it on the list, click on the 'New accelerator...'. and press your desired shortcut (for instance Ctrl+Alt+H).

Hope it helps. Let us know if that helps.
Regards.

P.S.: in case you want to do it using the terminal, simply run 'thunderbird' on any terminal.

---

### Post by buzzingrobot on 2014-11-09
Once any application has been launched, you can pin its icon to the Launcher via a right click.

---

