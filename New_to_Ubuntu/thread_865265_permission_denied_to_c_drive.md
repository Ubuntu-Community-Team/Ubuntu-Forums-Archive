---
title: "permission denied to c drive"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Falc7 on 2008-07-20
When i try to put some windows applications in wine's c drive, and make shortcuts in the applications-> wine menu, i quite often get the messsage 'permission denied' when i try to use these shortcuts, but if i navigate to the c drive and start them with a double click they work fine, how can i fix this?


Also, another problem is that i added a shortcut to a program under wine's list, so it goes
system tools
wine
(shortcut)

How can i get rid of that shortcut there?

---

### Post by madjr on 2008-07-20
> **Falc7 said:**
> When i try to put some windows applications in wine's c drive, and make shortcuts in the applications-> wine menu, i quite often get the messsage 'permission denied' when i try to use these shortcuts, but if i navigate to the c drive and start them with a double click they work fine, how can i fix this?

the **wine C drive** is a *virtual* C drive, is not a real partition

i think the virtual C drive is inside **.Wine** folder (which is invisible) in your user folder.

---

### Post by Falc7 on 2008-07-20
> **madjr said:**
> the **wine C drive** is a *virtual* C drive, is not a real partition

i think the virtual C drive is inside **.Wine** folder (which is invisible) in your user folder.


yeah i know where wine's c drive is, just don't know how to get past this shortcut permissions problem :confused:

---

### Post by Falc7 on 2008-07-22
Anyone?
This is the message i get:
Could not launch menu item
Failed to execute child process "/home/wer/.wine/drive_c/Program Files/Heroes of Might and Magic III Complete/Heroes3.exe" (Permission denied)

---

### Post by RuleMaker on 2008-07-22
Try this:
```
sudo chmod a+x ~/.wine/drive_c
```

---

### Post by Potatoj316 on 2008-07-22
try this
```
sudo chmod a+x PATHTOFILE
```

EDIT: sure rulemaker, beat me why dont you

---

### Post by Falc7 on 2008-07-22
Thanks for the reply guys

I still get the same message however

---

### Post by Falc7 on 2008-07-24
any thing else i can try?

---

### Post by Falc7 on 2008-07-30
anything?
it is quite strange, if i drag to make a link on the top bar, it works fine, i only seem to have a problem when i try to manually make a link the applications-> wine menu.

---

### Post by darksoul7 on 2008-07-30
Do you get the same thing if you create a launcher on the desktop?

I'd double check and make sure that your user account has the correct permissions to access the .wine directory.

---

### Post by estyles on 2008-07-30
When you say "manually make a link", I assume that means you're typing in the path?  If so, it might help if you post what you're typing in.  I believe it should be something like "wine ~/path/to/file.exe"

---

### Post by darksoul7 on 2008-07-30
> **estyles said:**
> When you say "manually make a link", I assume that means you're typing in the path?  If so, it might help if you post what you're typing in.  I believe it should be something like "wine ~/path/to/file.exe"

Hmm, I think you may have nailed the monkey on the head there, estyles. 

Falc7 - Are you using the wine command when you make the link? If not, that may be what is causing the issue. I'll mess around with it when I get home (no Ubuntu here :()

---

### Post by Falc7 on 2008-07-31
making a link to desktop works fine.

To manually make a link, i went system-> preferences-> main menu
Then new item, command-> browse to the file, and name it, then 'ok'

---

### Post by estyles on 2008-08-02
> **Falc7 said:**
> making a link to desktop works fine.

To manually make a link, i went system-> preferences-> main menu
Then new item, command-> browse to the file, and name it, then 'ok'

Which is incorrect.  You don't want a link to the .exe.  Linux can't run that.  You want a link to "wine /path/to/file.exe".  From what you did, just put wine in front of the command you already put in the link.  Should work like that.

---

### Post by darksoul7 on 2008-08-05
Played around with this after I posted my last reply and it seems correct. I just got busy and forgot about this thread. Did that work for you Falc7?

---

### Post by Falc7 on 2008-08-05
Yes it seems to work, the only thing is that using this method i get the message: files from game are missing please reinstall, whereas if i go to the .exe file in the c drive it starts fine.

However, at least i don't get the permissions error

---

### Post by estyles on 2008-08-05
Okay, that problem has something to do with the working directory.  If you want to make a launcher for it, you'll need to make a shell script.  Open a terminal.

```
gedit ~/.wine/heroes3.sh
```

In the text editor that pops up, add this:
```
#! /bin/bash
cd ~/.wine/drive_c/Program\ Files/Heroes\ of\ Might\ and\ Magic\ III\ Complete/
wine Heroes3.exe
```
Then save and exit.  In the terminal type:
```
chmod u+x ~/.wine/heroes3.sh
```

Then, in the launcher command line, put ```
/home/wer/.wine/heroes3.sh
```

I believe that should work for you.

---

### Post by Falc7 on 2008-08-05
Thanks i will try this once i am back on my desktop.

Could you explain the problem conceptually as well, i am interested in how ubuntu works

---

### Post by estyles on 2008-08-05
Well, I can try to explain the problem conceptually.  There's a chance that I'm incorrect.  I'm still somewhat new to linux.  Some of this I know to be true and some of it I am kind of guessing on, or I don't know the correct term.

The reason you have to put "wine" in front of the path name is that an .exe file is a Windows/DOS binary file.  Windows and DOS know how to interpret an .exe file, and the format is geared towards them.  Wine provides an emulation layer (technically wine isn't an emulator, but I don't know the exact correct term for what it does - it's close enough to what an emulator does that many people blur the distinction) that can interpret .exe files and provide the correct libraries for running that binary under linux.  Wine associates itself with the .exe extension so when you double-click a .exe file, it opens with wine.  When you make a launcher, you need to tell it to use wine, otherwise it tries to run using a Gnu/Linux interpretation of a binary, which doesn't work at all.

As for the working directory, some .exe's know to get the directory where the .exe file is located and use that as the program's working directory, and some will use the current directory that you run it from.  Frex, if Heroes is looking for saved games, it might look in the "Saved Games" folder.  If you run heroes3.exe from its own home directory, it knows that "Saved Games" is a subdirectory of that folder.  But let's say you are at a terminal and run... ```
~ $ wine /wine/drive_c/Program\ Files/Heroes\ of\ Might\ and\ Magic\ III\ Complete/heroes3.exe
```

In that case, it's not always clear whether your working directory should be your home directory or the directory where heroes.exe is located (or a third choice, which would be the directory where the wine binary is located).  Frex, when you run "ls", the "ls" binary is located in /bin, but "ls" knows that its working directory should be your current directory - it wouldn't be much use if ls always gave you a listing of /bin.  Some programs will know that their working directory should be the location of the .exe, and some will not.  If they don't, you have to make a little shell script (like a batch file in windows/DOS) to change directories and *then* run the program from there.

---

### Post by Falc7 on 2008-08-06
That worked perfectly thank you very much, in the future, with other games, if i change the location and 'heroes3' parts, if i do the same thing, will it work?

---

### Post by estyles on 2008-08-06
> **Falc7 said:**
> That worked perfectly thank you very much, in the future, with other games, if i change the location and 'heroes3' parts, if i do the same thing, will it work?

When using wine, nothing's guaranteed to work.  It's always a little sketchy, but yes, that should do the trick.

---

