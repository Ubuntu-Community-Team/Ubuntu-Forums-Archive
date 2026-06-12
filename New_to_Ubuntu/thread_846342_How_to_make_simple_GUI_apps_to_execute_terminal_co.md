---
title: "How to make simple GUI apps to execute terminal commands?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by monsterstack on 2008-07-01
Hello! I'll just get straight into my problem. Any suggestions welcome.

I've no problem using the terminal and most of the time I prefer using it than click-clicking. My girlfriend is not so inclined. I'd quite like to start making scripts for various things (control ffmpeg, or to remove spaces from file names, to control iptables etc etc) to make life easier for her and that's been largely successful so far but that isn't the problem.

I'd really like to be able to call these scripts from a window with actual buttons and text and whatever pasted all over it so as to make it completely foolproof to an extremely h4x0rz-phobic user.

I had a look for programs to help me out, I found a couple that look like they might do: Gazpacho and Glade, but I can't find any decent documentation. I found stuff about controlling the buttons etc in Ruby or Perl or Python, but I'm very crappy with Python and I know little to nothing of the other two.

Can someone point me in the right direction here?

Regards.

---

### Post by drs305 on 2008-07-01
For any shortcut you make, either on desktop or on a panel (by right clicking), there is an option for a custom shortcut to either run an app/script normally or in terminal. In either case, you can select the icon you wish to use. You can make your own icons (bonus points for asking her what she would like to use as an icon). You would write small BASH scripts and put the path/address/command.sh in the 'Command' line and select 'Run in Terminal'.

---

### Post by sdennie on 2008-07-01
You could have a look at zenity.  It's a program that allows you to popup gtk dialogs from shell scripts.  Check the man page.

---

### Post by monsterstack on 2008-07-01
Thanks for the input, chaps.

Icons on the desktop or in the taskbar isn't what I'm after. Menus, dialogs, boxes and buttons is the name of the game for me. Basically a proper application like any other, except it executes bash scripts and/or commands.

Zenity is pretty neat. But its fuctionality is limited to simple dialogs and notification windows with only a few buttons. Unless I'm missing something, that's my understanding of it.

---

