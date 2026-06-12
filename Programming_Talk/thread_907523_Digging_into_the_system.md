---
title: "Digging into the system"
date: 2008-09-01
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-09-01
so i want to make a program that senses weather in the appearance menu my effects setting in my appearance menu and switch it either to maximum or off...so i can quickly turn compiz off when i want to play games...i thought this would be a good learning experience...how would i go about this

---

### Post by rogeriopvl on 2008-09-01
It's a nice idea. I think that Vista does that. When you play games it turns Aero off.

That seems to be a simple script.

---

### Post by loganwm on 2008-09-01
> **jimi_hendrix said:**
> so i want to make a program that senses weather in the appearance menu my effects setting in my appearance menu and switch it either to maximum or off...so i can quickly turn compiz off when i want to play games...i thought this would be a good learning experience...how would i go about this

Your phrasing of the question is a bit entangled.

But if I follow correctly, you could create a sort of launcher program/script that acts as a rudimentary layer between the game and Ubuntu and does the following:

The game is launched through a minimal program or script that turns of compiz for the length of the child process of the program (the game) and when the child process ends (the game) then compiz is restarted.

With C it could possibly be done with a few easy system calls in the right order.

although I don't know if this method could interfere with some games.

If you need me to elaborate further or even help, I suppose I could.

---

### Post by jimi_hendrix on 2008-09-01
i want to make a program that switches the desktop effects from high to none and back

---

### Post by loganwm on 2008-09-01
> **jimi_hendrix said:**
> i want to make a program that switches the desktop effects from high to none and back

I read this and revised my post to include my thoughts.

---

### Post by jimi_hendrix on 2008-09-01
> **loganwm said:**
> Your phrasing of the question is a bit entangled.

But if I follow correctly, you could create a sort of launcher program/script that acts as a rudimentary layer between the game and Ubuntu and does the following:

The game is launched through a minimal program or script that turns of compiz for the length of the child process of the program (the game) and when the child process ends (the game) then compiz is restarted.

With C it could possibly be done with a few easy system calls in the right order.

although I don't know if this method could interfere with some games.

If you need me to elaborate further or even help, I suppose I could.

closest i know to C is C++...forgot to mention that

---

### Post by loganwm on 2008-09-01
> **jimi_hendrix said:**
> closest i know to C is C++...forgot to mention that

If you can give me some commands to suspend or disable the graphics (and re-enable) then I can write up a sample for you.

---

### Post by jimi_hendrix on 2008-09-01
wouldnt know that :)

---

### Post by loganwm on 2008-09-01
> **jimi_hendrix said:**
> wouldnt know that :)

Well if you decide to look into it, then it'll be a nice fist step towards your solution :)

---

### Post by rogeriopvl on 2008-09-01
Well, it seems that someone has done it already.

[http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on](http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on)

And there is also fusion-icon in the repositories, that does the same thing.

---

### Post by jimi_hendrix on 2008-09-01
i thought fusion just let u access compiz

---

### Post by loganwm on 2008-09-01
> **rogeriopvl said:**
> Well, it seems that someone has done it already.

[http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on](http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on)

And there is also fusion-icon in the repositories, that does the same thing.

Good find.

Personally, I don't use any of the advanced graphical desktop features, I'm very critical of overly fancy graphical eye candy hogging system resources. Although I'm not going to lie, I do like the sight of desktop transparency, I wish my graphics card wasn't so completely out of date.

---

### Post by mssever on 2008-09-01
I wrote the following script a while back to toggle between Compiz and Metacity: ```
#!/bin/bash

return_val=

function current_window_manager {
  local status=
  local current_wm=
  p compiz "$USER" > /dev/null 2>&1
  status=$?
  if [ $status -eq 0 ]; then
    current_wm=compiz
  else
    p metacity "$USER" > /dev/null 2>&1
    status=$?
    if [ $status -eq 0 ]; then
      current_wm=metacity
    fi
  fi
  if [ -z $current_wm ]; then
    echo "Unknown current window manager." >&2
  fi
  return_val="$current_wm"
}

function toggle_window_manager {
  local current_wm=
  current_window_manager
  current_wm="$return_val"
  case $current_wm in
    compiz)
      metacity --replace
      killall gtk-window-decorator
      exec killall compiz
      ;;
    metacity)
      exec compiz --replace
      ;;
    *)
      local tmp=`zenity --entry --title="New Window Manager" --window-icon=question --text="Enter the command for the window manager you want to run.
Be sure to pass in the --replace or -replace option." --entry-text="metacity --replace"`
      if [ -n "$tmp" ]; then
        exec $tmp
      else
        #exec zenity --error --text="I don't know how to handle the current window manager, nor do I know to which window manager you want to switch."
        :
      fi
      ;;
  esac
}

function main {
  zenity --question --text="Do you want to switch window managers?" && toggle_window_manager
}

main "$@"
```I tried backing up my Compiz settings to enable configuration changes, but Compiz seems buggy in that respect. Changing the gconf settings probably won't work, because you'd still be using Compiz.

EDIT: p is a shortcut script for listing processes matching a particular expression. It's available in the p-shortcut package in [my repository]("http://repository.scottseverance.us/falcon/dists/main/scripts/").

---

### Post by jimi_hendrix on 2008-09-01
> **rogeriopvl said:**
> Well, it seems that someone has done it already.

[http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on](http://forlong.blogage.de/entries/2008/1/6/Compiz-Switch---an-easy-way-to-switch-Compiz-off-and-on)

And there is also fusion-icon in the repositories, that does the same thing.

well i want to do it anyway to learn...someone has already written a hello world program for every language...but do people download that or do they write they're own to learn

---

### Post by rogeriopvl on 2008-09-01
> **loganwm said:**
> Good find.

Personally, I don't use any of the advanced graphical desktop features, I'm very critical of overly fancy graphical eye candy hogging system resources. Although I'm not going to lie, I do like the sight of desktop transparency, I wish my graphics card wasn't so completely out of date.

I have the same problem. I like transparency, but although I have a "minimum requirements" graphic card (intel GMA 3100 onboard), I prefer to save it for something else, so I turn off the compiz.

---

### Post by rogeriopvl on 2008-09-01
> **jimi_hendrix said:**
> well i want to do it anyway to learn...someone has already written a hello world program for every language...but do people download that or do they write they're own to learn

I agree with you, but you can also learn from what others did :) And make it better.

---

### Post by loganwm on 2008-09-01
> **rogeriopvl said:**
> I have the same problem. I like transparency, but although I have a "minimum requirements" graphic card (intel GMA 3100 onboard), I prefer to save it for something else, so I turn off the compiz.

I figure, with the way tech works there will be some of the higher-end computers of the last couple of years available at a reasonable price when I'm ready to upgrade.

Hopefully I could nab it without paying yet another Windows OS fee.

I'm not hardcore against Windows, I just disdain being OBLIGATED to reboot my system just to Sync my Zune and Pocket PC.

---

### Post by jimi_hendrix on 2008-09-01
> **loganwm said:**
> Hopefully I could nab it without paying yet another Windows OS fee.

i just got a new computer...i think it costs extra to not have windows because they get money for the addware

---

### Post by loganwm on 2008-09-01
> **jimi_hendrix said:**
> i just got a new computer...i think it costs extra to not have windows because they get money for the addware

I detest all of the extra trial software that is loaded onto a new computer.

I'd love nothing more than a blank slate to start from and design my way up from that, and thanks to Linux, now I can.

---

### Post by mssever on 2008-09-01
> **loganwm said:**
> I detest all of the extra trial software that is loaded onto a new computer.
I bought a new ThinkPad a couple of months ago. It came with XP (!) and the only trial software was MS Office. Of course, I quickly put Ubuntu on it.

---

### Post by anotherdisciple on 2008-09-01
I made this one a while back to run games without all the desktop effects. They were making my games twitchy!

```
GAME=$(zenity --entry --title "Game Runner" --text "What game would you like to play?")
metacity --replace &
sleep 2
$GAME
compiz --replace &
sleep 2
exit 1
```

---

### Post by slavik on 2008-09-01
> **mssever said:**
> I wrote the following script a while back to toggle between Compiz and Metacity: ```
#!/bin/bash

return_val=

function current_window_manager {
  local status=
  local current_wm=
  p compiz "$USER" > /dev/null 2>&1
  status=$?
  if [ $status -eq 0 ]; then
    current_wm=compiz
  else
    p metacity "$USER" > /dev/null 2>&1
    status=$?
    if [ $status -eq 0 ]; then
      current_wm=metacity
    fi
  fi
  if [ -z $current_wm ]; then
    echo "Unknown current window manager." >&2
  fi
  return_val="$current_wm"
}

function toggle_window_manager {
  local current_wm=
  current_window_manager
  current_wm="$return_val"
  case $current_wm in
    compiz)
      metacity --replace
      killall gtk-window-decorator
      exec killall compiz
      ;;
    metacity)
      exec compiz --replace
      ;;
    *)
      local tmp=`zenity --entry --title="New Window Manager" --window-icon=question --text="Enter the command for the window manager you want to run.
Be sure to pass in the --replace or -replace option." --entry-text="metacity --replace"`
      if [ -n "$tmp" ]; then
        exec $tmp
      else
        #exec zenity --error --text="I don't know how to handle the current window manager, nor do I know to which window manager you want to switch."
        :
      fi
      ;;
  esac
}

function main {
  zenity --question --text="Do you want to switch window managers?" && toggle_window_manager
}

main "$@"
```I tried backing up my Compiz settings to enable configuration changes, but Compiz seems buggy in that respect. Changing the gconf settings probably won't work, because you'd still be using Compiz.

EDIT: p is a shortcut script for listing processes matching a particular expression. It's available in the p-shortcut package in [my repository]("http://repository.scottseverance.us/falcon/dists/main/scripts/").
ps ax | grep "expression" :)

---

### Post by mssever on 2008-09-02
> **slavik said:**
> ps ax | grep "expression" :)
It isn't that simple.

[LIST]
[*]The grep command sometimes appears in the process list (it appears to be a race condition). That breaks the case where you're using the exit status to determine whether the process you're testing for is running. So it's necessary to filter out the grep command.
[*]p allows filtering by multiple parameters (which is how it's used in the script I posted). Implementing this as a pipeline requires even more filtering in order to work reliably, making for quite a hairy pipeline. My original bash implementation required three grep commands in the pipeline just to handle the necessary filtering (not counting the grep commands necessary for filtering by the expressions given on the command line). I later rewrote p in Ruby and was able to simplify things by exploiting Ruby features not conveniently available in bash. Writing such a pipeline in every script that needs to check processes is silly and bug-prone.
[*]When I wrote p, I was frequently running ps -ef | grep something | grep somethingelse interactively. Typing all that over and over quickly became tiresome.
[/LIST]
If I had cared about portability when I wrote the script I posted here, I might have bothered with a foolproof pipeline. But, I might not have, since external dependencies are common in Linux.

---

### Post by unutbu on 2008-09-02
Here is a trick for avoiding the race condition:
```

% ps -ef | grep emacs
unutbu    6110  6052  0 07:13 ?        00:00:03 emacs-snapshot-gtk
unutbu    6464  6161  0 07:46 pts/0    00:00:00 grep emacs
% ps -ef | grep [e]macs
unutbu    6110  6052  0 07:13 ?        00:00:03 emacs-snapshot-gtk
```

---

### Post by jimi_hendrix on 2008-09-02
so all of your examples seem to be bash...i would like to learn how to do it in C++ but if i cant i will just use your examples

---

### Post by rogeriopvl on 2008-09-02
> **jimi_hendrix said:**
> so all of your examples seem to be bash...i would like to learn how to do it in C++ but if i cant i will just use your examples

That's because in this particular case, bash or other scripting language like python and perl, is the better way to go.

But if you really really prefer C++, you should also try to do it in Assembly. That's even more challenging.:twisted:

---

### Post by jimi_hendrix on 2008-09-02
> **rogeriopvl said:**
> guage like python and perl, is the better way to go.That's because in this particular case, bash or other scripting lan

the only scripting lan i know is python

> you should also try to do it in Assembly. That's even more challenging.:twisted:

```
mov trash, idea
```

---

