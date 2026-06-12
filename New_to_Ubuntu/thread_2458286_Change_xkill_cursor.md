---
title: "Change xkill cursor"
date: 2021-02-20
forum: New to Ubuntu
---

### Post by james461 on 2021-02-20
I changed the cursor for the xkill command to the skull. But I have decided I want to change it back to the original cross.
I changed it using the command (which I got from [this post]("https://ubuntuforums.org/showthread.php?t=809010")): ```
s[COLOR=#000000][FONT=&amp]udo chmod -r /usr/share/icons/DMZ-White/cursors/pirate[/FONT][/COLOR]
``` I tried: ```
sudo chmod -r /usr/share/icons/DMZ-White/cursors/diamond_cross
``` As that is the icon I want the cursor to be. But that did not do anything.

I couldn't find anything about this online.
Any help would be appreciated.
Thanks in advance!

---

### Post by TheFu on 2021-02-20
Why would removing read access for everyone be helpful?  That's what those commands do.
You need to learn what chmod does.  Use explainshell.com or at least look up what the command does: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) or using manpages.
Throwing random commands WITH SUDO at a system is a good way to break it.

To modify resources for X/Windows programs, it is normal to use the ~/.Xresources file. What to put in that file is a multi-step process. We can't just guess.

---

### Post by Holger_Gehrke on 2021-02-21
The cursor to use in xkill is more or less hardcoded (in the source for xkill it creates a cursor using XC_pirate; this is defined as 88 in cursorfont.h; seems like an index into some kind of list or array of available cursors to me ...). It should take a cursor file named 'pirate' in the directory of your selected cursor theme. So to set xkill to use something else you should go to the directory where your cursor theme is stored (/usr/share/icons/NAME_OF_THEME/cursors), rename 'pirate' to something else that's unlikely to be used by some unlucky program (rename so you can go back to it later; if you never want to see that cursor again you could also delete it) and create a symbolic link named 'pirate' to the cursor you want to use.

Assuming you're using the default "DMZ White" theme, the commands to do this should look like this:
```

sudo mv /usr/share/icons/DMZ-White/cursors/pirate /usr/share/icons/DMZ-White/cursors/old-skull-and-bones-cursor
sudo ln -s /usr/share/icons/DMZ-White/cursors/X_cursor /usr/share/icons/DMZ-White/cursors/pirate

```
If you're using another cursor theme, you'll need to change the 'DMZ-White' in the commands above to whatever you're using.

Holger

Edit: ... or you could simply change the cursor theme to one which doesn't have the skull-and-crossbones (most don't ...).

---

### Post by james461 on 2021-02-21
[COLOR=#000000]> Why would removing read access for everyone be helpful? That's what those commands do.[/COLOR]
[COLOR=#000000]You need to learn what chmod does. Use explainshell.com or at least look up what the command does: [/COLOR][http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)[COLOR=#000000] or using manpages.[/COLOR]
[COLOR=#000000]Throwing random commands WITH SUDO at a system is a good way to break it.[/COLOR]

[COLOR=#000000]To modify resources for X/Windows programs, it is normal to use the ~/.Xresources file. What to put in that file is a multi-step process. We can't just guess.[/COLOR]


Ok, I'll try to read up about some more commands. But what I do know is that it worked from the post linked in my question. Thanks for the suggestion for learning commands!

---

### Post by james461 on 2021-02-21
> **Holger_Gehrke said:**
> or you could simply change the cursor theme to one which doesn't have the skull-and-crossbones (most don't ...).

Thanks, I changed the theme and it went back to a cross.

---

### Post by ActionParsnip on 2021-02-22
Another way of looking at this is, why do you care what it looks like? Are you using xkill regularly enough to want to change its appearance? If so, you should probably sort that instead

---

### Post by TheFu on 2021-02-22
> **ActionParsnip said:**
> Another way of looking at this is, why do you care what it looks like? Are you using xkill regularly enough to want to change its appearance? If so, you should probably sort that instead

Yep. I use xkill about 2 times a year, if that.  With some of the new Wayland client apps controlling their window decorations, I expect I'll need it much more, if/when I'm forced to move to Wayland.

---

### Post by ajgreeny on 2021-02-22
> **TheFu said:**
> Yep. I use xkill about 2 times a year, if that.  With some of the new Wayland client apps controlling their window decorations, I expect I'll need it much more, if/when I'm forced to move to Wayland.
I don't think xkill works when using a wayland session , only in xorg sessions; perhaps there will have to be another version for you to use; wkill?

I had never even considered this xorg/wayland difference but this thread caused me to search a bit leading to the above discovery.
At present I use xkill very seldom, probably even less than TheFu, but it is useful to have it available as a keyboard shortcut (Winkey+Del) to kill some process or other that has frozen solid, and remains frozen even after waiting a long time.

---

### Post by #&amp;thj^% on 2021-02-22
ajgreeny is right:
> Power users are familiar with a large range of X11-related utilities, like xkill, xrandr, xdotool, xsel. These tools won&#8217;t work under Wayland session, or will only work with **XWayland applications **but not Wayland applications. Some tools might have a replacement which allows to perform similar tasks.
For the time being, you may want to stick with the [pkil]("https://linux.die.net/man/1/pkill")l or kill in terminal

---

### Post by james461 on 2021-02-23
> **1fallen said:**
> ajgreeny is right:

For the time being, you may want to stick with the [pkil]("https://linux.die.net/man/1/pkill")l or kill in terminal


Ok thanks, I have quite an old laptop so when it freezes I use xkill. 
What's the difference between xkill, pkill, and kill?

---

### Post by #&amp;thj^% on 2021-02-24
> **james461 said:**
> Ok thanks, I have quite an old laptop so when it freezes I use xkill. 
What's the difference between xkill, pkill, and kill?

Xkill will only work under an X11 Session where as "pkill, and kill" will just work on any (Linux) session.

---

