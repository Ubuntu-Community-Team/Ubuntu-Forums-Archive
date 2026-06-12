---
title: "Conky disappears when I click on desktop when compiz is enabled"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by ShawnHeim on 2013-03-28
Problem:
When I have Compiz enabled Conky disappears when I click anywhere on the desktop.

Distro:
Linux Voyager (xubuntu xfce 12.10)

I have tried to search Google for a solution. I added some exceptions in compiz settings manager for window rules, I tried to put conky into compiz's widget layer and I have tried to change lines in ~/.conkyrc but nothing ever changes. I'm not even sure that conky reads the .conkyrc file as I don't see any changes (after logging out and logging in again, or restarting conky from terminal). It keeps disappearing when I click on the desktop no matter what I do. On application auto-start conky also seems to have a short delay on it, which doesn't seem to solve the problem either. 

Now I am clueless on what to try next, thus I registered here to post a thread and ask about the matter. 

My .conkyrc at the moment looks like this:
```

own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override

```

Sorry if this is the wrong place, but I didn't find any sub-forums under absolute beginners.

---

### Post by wojox on 2013-03-28
Try these values:
```

own_window_type normal
own_window_transparent no
own_window_hints undecorated
```

---

### Post by ShawnHeim on 2013-03-28
> **wojox said:**
> Try these values:
```

own_window_type normal
own_window_transparent no
own_window_hints undecorated
```
Thanks for suggestion, 
the problem persists though.

edit:
okay, it appears that conky wasn't reading the ~./conkyrc file at all, or it was overridden by a file in ~./conky/conky/conky16/TimeFull, which seems to be a conky settings file for that particular conky item that I have been trying to display. 

now I'm using the following configuration:
```

own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated, skip_taskbar

```

and it displays pretty much the way I want it to and now it does not seem to disappear when I click on desktop, but now for some reason, it only appears in one workspace. How can I make it display on every workspace?

edit2:
solved it by adding sticky in own_window_hints

ended up using this configuration:
```

own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated, below, skip_taskbar, skip_pager, sticky

```

So, to sum things up the problem was that I was editing the wrong file. Apparently it doesn't matter what you put in ~/.conkyrc when the item specific values override it under ~/.conky/.

---

