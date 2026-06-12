---
title: "Alt+F2 sometime fails to search"
date: 2018-01-02
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-01-02
I typed Alt+f2  and then typed xkill.
Sometime it shows xkill and sometime it does not. Is Alt+f2 searching inside wrong container?

Is there a way to specify the container?


Thanks

---

### Post by deadflowr on 2018-01-03
That looks like the dash instead of the run dialog.
Obvious sign is that the run dialog has no dash scopes.

Also the run dialog will simply add whatever you enter as if it means something.
It never shows anything about something not found.


Anyway the dash does not list commands like the run dialog does.

Are you sure you're hitting alt+ F2 and not clipping the super key instead?

---

### Post by vasa1 on 2018-01-03
Does that happen only with *xkill* or with other commands as well?

As a side-note, it's a bit worrisome that you need to use *xkill* at all.

---

### Post by wrongusername2 on 2018-01-03
> **deadflowr said:**
> 
Are you sure you're hitting alt+ F2 and not clipping the super key instead?

As far as my memory goes I was using Alt + F2. I will verify again when I go home. 

Before trying I read about Alt+f2 and I was expecting something like "start->run" of Windows. I will check again and get back.

---

### Post by deadflowr on 2018-01-03
Which Ubuntu version is it by the way? (14.04 16.04 17.04, 17.10, or 18.04?)

In a perfect world there should be 3 different instances where the overlay window opens

The first is the dash, super key, which will show gui (graphical) programs, files and searchable content, if on-line search is enabled.

The second is the run dialog , alt + f2 keys ,which will show, if not disabled to show, the history of any commands started from it.

And the third is the hud, ,alt key,  which will show a bar like the run command, but is integrated in program menus to allow you to simply type a program's command function and run that function;
stuff like "save as" as an example can be opened by simply typing all or part of "save as" and selecting it from a list of options that will appear, it makes it easy to keep going without having to pause to remember some apps specific keybinding to do something, if that makes sense.

All 3 have the same basic underlying design and look, so it can be easy to mistake one for another.

---

### Post by wrongusername2 on 2018-01-03
> **vasa1 said:**
> Does that happen only with *xkill* or with other commands as well?

As a side-note, it's a bit worrisome that you need to use *xkill* at all.

Yes. I understand what you are saying. Recently two applications stopped responding. I one case NUM Lock stopped responding. Then I had to power off the system. That is when I started researching this. I thought of using KILL but in some cases I may not know the process name. Also the name shown in title-window may not translate to process name. So xkill is great. Click on window and it will kill the process. 

I had selected 10 DNG files for copying but by accident I pressed ENTER key. That triggered several instances of Rawtherapee.  Then NUM lock stopped responding.. I ended up powering off the machine.

---

### Post by wrongusername2 on 2018-01-03
> **deadflowr said:**
> Which Ubuntu version is it by the way? (14.04 16.04 17.04, 17.10, or 18.04?) 
It is 16.04.


> **deadflowr said:**
> 
In a perfect world there should be 3 different instances where the overlay window opens

The first is the dash, super key, which will show gui (graphical) programs, files and searchable content, if on-line search is enabled.

The second is the run dialog , alt + f2 keys ,which will show, if not disabled to show, the history of any commands started from it.

And the third is the hud, ,alt key,  which will show a bar like the run command, but is integrated in program menus to allow you to simply type a program's command function and run that function;
stuff like "save as" as an example can be opened by simply typing all or part of "save as" and selecting it from a list of options that will appear, it makes it easy to keep going without having to pause to remember some apps specific keybinding to do something, if that makes sense.

All 3 have the same basic underlying design and look, so it can be easy to mistake one for another.

This is lot of useful info, let me read up about these first.

---

### Post by deadflowr on 2018-01-03
Press and holding the super key down should reveal a quick tips overlay page on the screen.
It should show the default keybindings for the dash and the hud, as well as a few nifty keybindings for basic functions.
Not sure it shows anything for the run dialog, but the run dialog is basically the same across desktop environments.

---

### Post by wrongusername2 on 2018-01-03
I tested now; when I typed Alt+F2, i got only Run-window. This is not same window that I attached in first port. I could not reproduce that any more. Anyhow I know few more things about Ubuntu. I will close this issue. Thanks everyone.

---

