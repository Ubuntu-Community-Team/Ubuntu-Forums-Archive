---
title: "[SOLVED] where to find download"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by lyni on 2008-08-31
I downloaded a game thru Synaptic but when I went to Applications>Games it is not there. could someone please tell me where to look for it please?
thanks

---

### Post by jemate18 on 2008-08-31
> **lyni said:**
> I downloaded a game thru Synaptic but when I went to Applications>Games it is not there. could someone please tell me where to look for it please?
thanks

What game in particular did you downloaded? Where there errors encountered in the download? Try restarting your computer


Mark this thread SOLVED if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button

Hope this helps.

jemate18

---

### Post by lyni on 2008-08-31
there were no problems during the download.
the game was 'scribble.'
I downloaded it yesterday so the computer has been turned off then on.
in Synaptic the box is green showing that it has been installed.

---

### Post by eggdeng on 2008-08-31
Run
```
sudo updatedb
```
then
```
locate scribble
```
It's probably in /usr/games/scribble or similar.

---

### Post by Too Late on 2008-08-31
I haven't try that specific game, but in general, you can launch an application by going to terminal, and simply type its name (in this case, scribble). If that doesn't work, you can try to check if it has a manual page (type: man scribble) which tells the commands. If that didn't work, right-click the package in Synaptic, go to Properties and look at Installed Files tab.

When you've found the correct command (almost certainly scribble), you can add it to the Games menu by going to System -> Prefecences -> Main Menu. Not all programs add themselves into menus by default. Unfortunately, then they won't probably have any icons neither.

---

### Post by jemate18 on 2008-08-31
> **lyni said:**
> there were no problems during the download.
the game was 'scribble.'
I downloaded it yesterday so the computer has been turned off then on.
in Synaptic the box is green showing that it has been installed.

Was it scribble-1.10.2?

to verify it 
1. Applications -> Accessories -> Terminal

2. type
```
which scribble
```

3. to launch it, type
```
scribble
```

It is a console/shell -based game and not GUI based. Thats why it is not available under Applications -> Games

If you want to include it in Applications -> games
Do this
1. right click on Applications
2. select "Edit menu"
3. Click Games
4. Click new item in the right most button
5. A create launcher dialog box will appear
6. On the type combobox, select Application in terminal
7. On the name, type SCRIBBLE
8. On the command, type /usr/games/scribble
9. Click the icon on the left-most part so you could change it.
10. Its DONE

Mark this thread SOLVED if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button

Hope this helps.

jemate18

---

### Post by lyni on 2008-08-31
thank you everyone

---

