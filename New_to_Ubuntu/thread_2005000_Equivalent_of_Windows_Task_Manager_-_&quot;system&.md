---
title: "Equivalent of Windows Task Manager - &quot;system&quot;?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by pshute on 2012-06-16
I've just installed Ubuntu 12.04 and I haven't used Linux before. I was trying to find the equivalent of Windows Task Manager, and came across this page:
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
which says:
"Ubuntu's *System Monitor* is the closest equivalent to the Task Manager in Windows.  It's available through *System > Administration > System Monitor*."

That sounds perfect, but what's this "System" thing? How do I get to that?

I can run the System Monitor from the search box that comes up when I click that round icon on the top left, the one with a circle and three dots on it, whatever it's called. I just want to know how to run it via the GUI.

---

### Post by afixane on 2012-06-16
Just click your dash (the big ubuntu logo) and type "system monitor" :D

---

### Post by jmfal on 2012-06-16
If you are using the gnome desktop, along the top toolbar should be >apps > places (file management) and > system
You may need to hover your mouse over the left side of the toolbar and they should appear.

If you are using unity (2D) click on the ubuntu  trademark (top of tool bar above folder icon) click on the three bars at bottom of that screen and select installed apps 

IF it is not there open a terminal
```
 sudo apt-get install system monitor
```

it should be installed

---

### Post by pshute on 2012-06-16
> **afixane said:**
> Just click your dash (the big ubuntu logo) and type "system monitor" :D
That would be the circle thing I mentioned. At least I know what it's called now.

---

### Post by forrestcupp on 2012-06-16
> **pshute said:**
> That would be the circle thing I mentioned. At least I know what it's called now.

You can click that and start typing whatever you want that is installed, and it will bring it up so you can click to open.

---

### Post by David Andersson on 2012-06-16
> **jmfal said:**
> 
IF it is not there open a terminal
```
 sudo apt-get install system monitor
```

it should be installed

Ignore that for the time being. System Monitor is installed by default in every version of Ubuntu I know of. (Besides, its package name is gnome-system-monitor).

In Unity the easiest way to find it appears to be to type "system" or "monitor" or both, in dash.

In Ubuntu Classic mode you find it in Applications>System>System Monitor.

---

### Post by Shadius on 2012-06-16
> **pshute said:**
> That would be the circle thing I mentioned. At least I know what it's called now.

That "circle thing" is called the Dash. You'll be using it a lot so it's good to know the name. It still confuses me with all the names given to it. :lolflag:

---

### Post by pshute on 2012-06-16
> **David Andersson said:**
> Ignore that for the time being. System Monitor is installed by default in every version of Ubuntu I know of. (Besides, its package name is gnome-system-monitor).
Yes, it's definitely installed, and I can run it by typing it's name in the search box.
> In Unity the easiest way to find it appears to be to type "system" or "monitor" or both, in dash.

In Ubuntu Classic mode you find it in Applications>System>System Monitor.
How do I tell which desktop/mode I'm running? I suspect the instructions I referred to are for one that I'm not running. It's nice to have  choice, but it does make instructions that work for me hard to find.

---

### Post by Shadius on 2012-06-16
> **pshute said:**
> Yes, it's definitely installed, and I can run it by typing it's name in the search box.

How do I tell which desktop/mode I'm running? I suspect the instructions I referred to are for one that I'm not running. It's nice to have  choice, but it does make instructions that work for me hard to find.

To find out what Desktop Environment you're in, run the following in Terminal:
```
echo $DESKTOP_SESSION
```

---

### Post by codingman on 2012-06-16
System Monitor should do the trick for you, I have a desktop shortcut for it for quick access. If this has been solved for you, please set this thread as solved ;).

---

### Post by pshute on 2012-06-17
> **codingman said:**
> System Monitor should do the trick for you, I have a desktop shortcut for it for quick access. If this has been solved for you, please set this thread as solved ;).
Not quite solved. I'd like to know on what sort of system those instructions work ("Ubuntu's *System Monitor* is the closest equivalent to the Task Manager in Windows.  It's available through *System > Administration > System Monitor*.")

The result of the echo $DESKTOP_SESSION[FONT=monospace] COMMAND were "ubuntu-2d". What does that tell me, and do the above instructions apply to me?
[/FONT]

---

### Post by zombifier25 on 2012-06-17
That means you are using Unity 2D. Click the top left button, search for "system monitor" and done. The instructions stated (System > Administration > System Monitor) are for GNOME Classic (Ubuntu 10.10 and downward's default desktop environment, which still has the Windows-like start menus))

What confuses me is that you stated that you're using Unity, you knew how to start the System Monitor via Unity, but you're still asking the question.

---

### Post by Shadius on 2012-06-17
You might want to take the Ubuntu [tour]("http://www.ubuntu.com/ubuntu/take-the-tour") as well. 

Some helpful links:
[Ubuntu Help]("https://help.ubuntu.com/12.04/ubuntu-help/index.html")

This manual is for 11.10, but it's worth reading. Not that different from 12.04. 
[Ubuntu Manual]("http://ubuntu-manual.org/")

---

### Post by forrestcupp on 2012-06-17
> **pshute said:**
> 
How do I tell which desktop/mode I'm running? I suspect the instructions I referred to are for one that I'm not running. It's nice to have  choice, but it does make instructions that work for me hard to find.
The instructions you saw were probably old instructions from back in the Gnome 2 days. Gnome 2 had the Applications menu in the upper panel by default. Ever since Ubuntu 11.04, we've been using Unity, which now uses Gnome 3 as a base, but Unity is the user interface. Before Ubuntu 11.04, we used the Gnome 2 interface, which is what your instructions are describing. If you have the Dash button in the upper left, you know you're running Unity.

If you want to check out the old way, you can try out Gnome Classic, which makes Gnome 3 look like the old Gnome 2 UI. If you want to install that to try it out, open a terminal and type:
```
sudo apt-get install gnome-session-fallback
```Then log out and at the login screen, change the icon next to your user name to Gnome Classic.

---

### Post by pshute on 2012-06-17
> **zombifier25 said:**
> That means you are using Unity 2D. Click the top left button, search for "system monitor" and done. The instructions stated (System > Administration > System Monitor) are for GNOME Classic (Ubuntu 10.10 and downward's default desktop environment, which still has the Windows-like start menus))

What confuses me is that you stated that you're using Unity, you knew how to start the System Monitor via Unity, but you're still asking the question.
Thanks for clarifying that. I didn't know how to do it, found those instructions and used them as a clue for how to start the right program manually, but wanted to know if:
a) there was a way to do it via the GUI
b) there was a reason why the instructions made no sense.

It's disconcerting for a brand new user when official instructions make no sense. I assume I'll be running into a lot of that.

Are there plans to update those instructions, or is there some kind of war going on between the people who write them and the people who decide what the default desktop is?

---

### Post by pshute on 2012-06-17
Should I be considering changing to the Gnome desktop if there's better documentation for it?

---

### Post by Shadius on 2012-06-17
> **pshute said:**
> Should I be considering changing to the Gnome desktop if there's better documentation for it?

What instructions are you looking at exactly? Those instructions seemed to have confused you, so I can try to help you if you show me exactly what you're relying on.

---

### Post by meathdeath on 2012-06-17
**_one word! _**: Terminal!

---

### Post by forrestcupp on 2012-06-17
> **pshute said:**
> Should I be considering changing to the Gnome desktop if there's better documentation for it?

No, you just need to make note of when the instructions were written. The old Gnome 2 desktop is obsolete and not being developed or supported anymore. Unity has been around for over a year and will continue being supported. You'll start seeing a lot more instructions for that. 

If you scour the net, you could probably find a lot of instructions for Windows 98. That doesn't make that a good choice for Windows users. Your only problem was that you were unaware of the different desktop environments, and now you'll be aware in the future when you're looking for help. There is plenty of help out there for Unity, especially on these forums and Ask Ubuntu.

---

### Post by pshute on 2012-06-17
> **Shadius said:**
> What instructions are you looking at exactly? Those instructions seemed to have confused you, so I can try to help you if you show me exactly what you're relying on.
Here: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

It says "last edited 2011-07-18".

---

### Post by pshute on 2012-06-17
> **meathdeath said:**
> **_one word! _**: Terminal!
Does that mean I just get a command line? Apart from the obvious "disadvantage" that I'll have to type every command, what are the advantages? Will it use less RAM and CPU? Will programs like Gimp and Audacity still work, and if so, will they work better? This is an old computer with only 500MB RAM, so if it'll help it then I'll do it.

---

### Post by Shadius on 2012-06-17
> **pshute said:**
> Does that mean I just get a command line? Apart from the obvious "disadvantage" that I'll have to type every command, what are the advantages? Will it use less RAM and CPU? Will programs like Gimp and Audacity still work, and if so, will they work better? This is an old computer with only 500MB RAM, so if it'll help it then I'll do it.

Using the Terminal is just doing things via a command-line interface instead of using the GUI method. You'll have to type in the commands in the Terminal. RAM & CPU usage won't be affected if you use either the Terminal command-line interface or the GUI. It's just a different method of performing a task. You can take a look at how to use the Terminal from the [Community Help Wiki.]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by David Andersson on 2012-06-18
> **meathdeath said:**
> **_one word! _**: Terminal!

> **pshute said:**
> Does that mean I just get a command line? 

Ignore that for the time being. I don't know what question meathdeath is answering, but it is not an answer to your original question. (This highlights the more recent discussion in this thread: how do you know if a post on the internet is applicable to you?)

---

### Post by xedi on 2012-06-18
> **pshute said:**
> Thanks for clarifying that. I didn't know how to do it, found those instructions and used them as a clue for how to start the right program manually, but wanted to know if:
a) there was a way to do it via the GUI


By typing it in the dash, you did use the GUI version. If you mean how to do it without searching:

Click on the dash (the circle in the corner), click on the application lens (in the lower row, the second icon with the ruler and pen or something like it), click on installed and browse through the programs until you find the system monitor (it's alphabetically ordered).

As you see it, typing is probably faster and unity in general is more search/intention driven, which I find faster and more comfortable but if you are a fan of menus, you have to go the route I described.

> 
b) there was a reason why the instructions made no sense.

It's disconcerting for a brand new user when official instructions make no sense. I assume I'll be running into a lot of that.

Are there plans to update those instructions, or is there some kind of war going on between the people who write them and the people who decide what the default desktop is?

I looked at the link, it's not the official documentation but the userdocumentation, so WE are responsible for its content, so if anybody feels like updating it should go ahead and change it. 

However, you're right, it's outdated or it should at least state this only applies to GNOME 2 Shell.

---

### Post by xedi on 2012-06-18
I just updated the documentation. My first time editing it, so if I messed up, feel free to change it and virtually stone me :)

---

### Post by Shadius on 2012-06-18
> **xedi said:**
> I just updated the documentation. My first time editing it, so if I messed up, feel free to change it and virtually stone me :)

Hey xedi, what part did you edit? I'd like to take a look and help out with some editing too since some of these documentations seem to confuse a lot of people, especially beginners. :)

---

### Post by xedi on 2012-06-18
> **Shadius said:**
> Hey xedi, what part did you edit? 

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

originally said where to find the terminal and system monitor in the gnome 2 shell menus. I changed those two lines to say that you can type terminal/system monitor into the dash.

---

### Post by pshute on 2012-06-18
> **xedi said:**
> [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

originally said where to find the terminal and system monitor in the gnome 2 shell menus. I changed those two lines to say that you can type terminal/system monitor into the dash.
Thanks for fixing that, but haven't you now made the instructions inapplicable for gnome 2 users? Or should it be assumed that these instructions are for the current default desk top?

I also think that page should really do more to reassure new users coming from Windows that they're doing it the right way. My reaction on reading that would be to wonder if there was some shortcut key combination like control+shift+esc, or if I could right click somewhere and choose it from a menu. If it had said what it says now, and "There are no shortcut keys defined for this program" then this thread wouldn't exist. It should probably also mention the method of finding the app in the app list, but say that searching is generally faster.

I'd change it myself, but I'm not confident yet that I know what to write.

---

### Post by ubuntu27 on 2012-06-18
If that guide confuses you. I recommend you to read [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") (a.k.a Psychocats)

---

### Post by Shadius on 2012-06-18
I've edited the Task Manager section so it looks like this now:
> Task Manager

Ubuntu's System Monitor is the closest equivalent to the Task Manager in Windows.

In Unity:

You can launch the system monitor by typing "System Monitor" into the Dash.

In GNOME Classic/Fallback:

From the panel, click on Applications>System Tools>System Monitor

I was trying to make the "Applications>System Tools>System Monitor" part in italics, but it wasn't showing. Maybe someone else can solve that little detail. I hope this helps in clearing up the confusion. Also, I don't know of any keyboard shortcuts for System Monitor by default, but I believe you can create one. Hope that helps! It was my first time editing as well. :)

---

