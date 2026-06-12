---
title: "nautilus-open-terminal"
date: 2011-06-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ayates on 2011-06-08
I installed it, but it doesn't show on a right click ? Bug ?

---

### Post by mc4man on 2011-06-08
None of the prior nautilus extensions will work atm

You can replace the open-terminal one, (& nautilus-gksu) with some nautilus-actions, but for the moment you'd need to rebuild NA for gtk3+ or wait for it to be done for you at some point.

(just set up a few on new install - screen

Edit: screen 2 shows how to get to show only on dir.'s

---

### Post by hatalar205 on 2011-06-08
Look here [http://ubuntu-tutorials.com/2007/05/13/nautilus-open-terminal-terminal-quick-launch/](http://ubuntu-tutorials.com/2007/05/13/nautilus-open-terminal-terminal-quick-launch/)

---

### Post by ronacc on 2011-06-08
> **mc4man said:**
> None of the prior nautilus extensions will work atm

You can replace the open-terminal one, (& nautilus-gksu) with some nautilus-actions, but for the moment you'd need to rebuild NA for gtk3+ or wait for it to be done for you at some point.

(just set up a few on new install - screen

Edit: screen 2 shows how to get to show only on dir.'s

nice but when I try to run nautilus-actions-config-tool this is what I get
```
 ron@ron-desktop2:~$ nautilus-actions-config-tool
Aborted
ron@ron-desktop2:~$ sudo nautilus-actions-config-tool
[sudo] password for ron: 
ron@ron-desktop2:~$ 
```

this is in gnome-shell , nautilus-actions was installed with synaptic . It isn't showing any output in the term to indicate why it is aborting .

---

### Post by mc4man on 2011-06-08
> **ronacc said:**
> nice but when I try to run nautilus-actions-config-tool this is what I get
```
 ron@ron-desktop2:~$ nautilus-actions-config-tool
Aborted
ron@ron-desktop2:~$ sudo nautilus-actions-config-tool
[sudo] password for ron: 
ron@ron-desktop2:~$ 
```

this is in gnome-shell , nautilus-actions was installed with synaptic . It isn't showing any output in the term to indicate why it is aborting .

You'll need to re-build NA to use gtk3 - I found it easier to use the current source, (config,make,checkinstall),  than than take O's source, adjust and re-package as ubuntu .deb. *though did both ways

There are some warnings when installing, (seem non critical) and an apparent small bug when opening text as root w. gedit - opens the file fine but also opens a new 'untitled file' (I just close it out, not going to file an upstream bug on quite yet

Heading out - if inclined to do can review some notes I made on either method if you run into any issues

---

### Post by ronacc on 2011-06-08
Thanks I'll give that a try and report back .

---

### Post by ronacc on 2011-06-08
built nautilus-actions 3.1.3 from source , installed ok and is working . Now I just have to figure out how to get the term to open in the active dir instead of /home .

---

### Post by mc4man on 2011-06-08
> **ronacc said:**
> built nautilus-actions 3.1.3 from source , installed ok and is working . Now I just have to figure out how to get the term to open in the active dir instead of /home .

Did you try setting up as is my screens/ (works fine here, U&GS logins

If trying to set the MimeType I find after entering the info as shown press enter on keyboard to set, not any mouse action
(if no go I'll export the action and attach

---

### Post by ronacc on 2011-06-08
thanks I had rather stupidly ignored the 2nd screen :(  working right now .

---

### Post by seeker5528 on 2011-06-08
> **ayates said:**
> I installed it, but it doesn't show on a right click ? Bug ?

What are you right clicking?

When I right click a directory 'Open In Terminal' is one of my options.

For the directory I am in right clicking doesn't work, but if I go to the 'Tools' menu it shows me.

```
Open Current Folder In Terminal     F4
Open Current Folder As Root
```

With the 'T' and the 'R' underlined so doing 'F4' or 'Alt'+'T' then 'T' work to open a terminal or 'Alt'+'T' then 'R' to switch user.

The switch user command isn't set for the 'R' though so the first time I had to fill in the command for it:

```
gksu %s
```

Or go to 'Edit --> Preferences --> Advanced' and set it before hand.

If you switch user, then open a terminal, you get a root terminal, but if you would prefer a root terminal instead of a root file manager for the switch user, use

```
gksu x-terminal-emulator %s
```

I have nautilus-gksu installed as well as nautilus-open-terminal.

Later, Seeker

---

### Post by Xgen on 2011-06-08
Both administrator rights and open terminal WFM normally by copying libnautilus-gksu.so and libnautilus-open-terminal.so from '/usr/lib/nautilus/extensions-2.0' to 'extensions-3.0'. No problems as yet...

---

### Post by ayates on 2011-06-08
Thanks mc4man. Your solution works. I tried Xgen's suggestion, and the drop down shows up but doesn't work. I'm not very good at building from source, but I muddled my way through it. Thanks again.

---

### Post by Xgen on 2011-06-08
"and the drop down shows up but doesn't work"

Requires a reboot, perhaps...

---

### Post by mc4man on 2011-06-11
> **mc4man said:**
>  an apparent small bug when opening text as root w. gedit - opens the file fine but also opens a new 'untitled file' 

Turns out to not an NA issue but with gedit itself.
Hadn't had occasion to use gksudo gedit before a moment ago - does then same

(there is another small bug in gedit that causes cursor run on - can be fixed by editing gedit.desktop and changing 
StartupNotify=true to false (or removing the line and space

---

