---
title: "[SOLVED] getting programs to start automatically with Ubuntu"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-05-09
Hello Everybody,

Is there a way of getting a program to start automatically with Ubuntu when it boots? I would like my To Do List to boot with Ubuntu.

Many thanks,

Charlie

---

### Post by glennric on 2008-05-09
Go to System->Preferences->Sessions and add programs there.

---

### Post by NetworkGuy on 2008-05-09
Charlie,

If you click on system/preference/sessions - you should be able to enter the program you want to start automatically in the startup programs tab.

---

### Post by diablo75 on 2008-05-09
Click on System>Preferences>Sessions

All you have to do to get a program to start upon login is add it to the list of startup programs you'll find here.

The catch is:  What's the command for your to-do list?

One way you can find this out is to have it already running when you open this sessions menu, and then click on the "Current Session" tab to view a list of current processes that are running.  You can then extrapolate what command it is you're looking to add to your startup list.

Alternatively, you might try the third tab, "Session Options".  There's a "Automatically remember running applications when logging out" check box.

---

### Post by Charlie Chick on 2008-05-09
Thank you all for such a quick reply! 

As diabolo75 says, I can't find the command for the To Do List in the running programs. I'll try his/her last suggestion and tick the 'automatically remember' checkbox and see if that does the trick.

---

### Post by Charlie Chick on 2008-05-09
Sadly, I have to report that the last suggestion didn't work. How do I find the command for the To Do List to add it to the list of startup programs?

Thank you all,

Charlie

---

### Post by ByteJuggler on 2008-05-09
How do you start your to-do list?  What application is it?  You can inspect the launcher (shortcut) for the to-do list application to figure out what to add to the sessions list.

---

### Post by Charlie Chick on 2008-05-10
It's called the ToDo List. I found it in Add/Remove Programs and it lives in the Office section of Applications. Putting my mouse over it gives nothing more than a description of what it does. Don't programs normally reside in usr/bin? If so, then I can't see it in mine unless it's called something else.

Thanks,

Charlie

---

### Post by ByteJuggler on 2008-05-12
OK the command is "gtodo", simply put that in the "command" edit box in your "Sessions" list, and it will start next time you boot. 

By the way, the way I figured this out, so you can do the same next time, is as follows:

1) I right clicked the ToDo application entry in the menu, and then clicked "Add this launcher to Desktop".  This was simply so I could get easy access to the launcher's details.
2) Next I right clicked on the ToDo launcher (shortcut) on my desktop  and clicked "Properties"
3) On the "Laucnher" tab, it then lists the command associated with that launcher/shortcut in the "command" edit box, in this case it is "gtodo".

That's all.

As a check, I opened a terminal and entered:

```
whereis gtodo
```

And the system responded with:

```
gtodo: /usr/bin/gtodo /usr/share/gtodo
```

However, this is really irrelevant, as the "Sessions" box doesn't need the full path, you can simply enter "gtodo" as in the launcher and it works fine.  

Hope that helps. :-)

---

### Post by Charlie Chick on 2008-06-01
Just to say thanks to ByteJuggler - it works! And I've learnt something useful as well. 

Charlie

---

### Post by kungfutofu on 2008-06-01
In order to have a program like "Gnome-do" start automatically with Ubuntu, I added the command (/usr/bin/gnome-do) to the end of the .profile file. This would cause it to execute during startup.

I know you can go to System->Preferences->Sessions and add it that way, but I was curious about making the change via command line. 

The web link where I found the information is at:
[http://www.reviewsaurus.com/blogging-tips/statup-program-load-ubuntu-feisty-fawn/](http://www.reviewsaurus.com/blogging-tips/statup-program-load-ubuntu-feisty-fawn/)

---

