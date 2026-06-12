---
title: "How can I use Grub??"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by antalves on 2008-06-30
[FONT="Georgia"]I just installed Ubuntu 8.04, together with an Win XP already installed. I want to change order of boot, being **Win** by default, because of my son and wife[/FONT]
When I try to edit and save Grub a message tells me I have no permission...
I simply do not know what to do! (How can I give permission to myself?)
When editing, I see:

##default num

Should I replace **num** by a number?

If somebody help now...

---

### Post by billgoldberg on 2008-06-30
> **antalves said:**
> [FONT="Georgia"]I just installed Ubuntu 8.04, together with an Win XP already installed. I want to change order of boot, being **Win** by default, because of my son and wife[/FONT]
When I try to edit and save Grub a message tells me I have no permission...
I simply do not know what to do! (How can I give permission to myself?)
When editing, I see:

##default num

Should I replace **num** by a number?

If somebody help now...

So you want the grub to boot into windows by default instead of Ubuntu?

->

[http://ubuntuforums.org/showthread.php?t=192659](http://ubuntuforums.org/showthread.php?t=192659)

Should take you around 10 seconds to do.

---

### Post by unutbu on 2008-06-30
```
gksudo gedit /boot/grub/menu.lst
```
gksudo gives you root permissions (administrator powers). Edit the line that says

```
default		0
```

by changing 0 to the number of the Windows entry as seen in the GRUB menu at boot time. On most installations the correct entry will be 3 (because Windows is the 4th entry).

---

### Post by billgoldberg on 2008-06-30
Oh, you can edit the file by using this command in a terminal:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by bumanie on 2008-06-30
You can go to terminal > sudo apt-get install startupmanagerThen under Sytem --> Administration --> Startup Manager, use the gui to get windows to be first on the grub list.

---

### Post by billgoldberg on 2008-06-30
> **bumanie said:**
> You can go to terminal Then under Sytem --> Administration --> Startup Manager, use the gui to get windows to be first on the grub list.

If you're keen on GUI's, you should go to "system -> administration -> synaptic package manager". Then press the "search" button and type in "startup manager" and then press ok.

Click it, then press apply.

Then search for the program in one of the menu's.

---

### Post by pmlxuser on 2008-06-30
> **antalves said:**
> [FONT="Georgia"]
When I try to edit and save Grub a message tells me I have no permission...
I simply do not know what to do! (How can I give permission to myself?)

If somebody help now...

please do 
$sudo gedit /boot/grub/menu.lst

you will have full access to edit that file (don't forget to back up the menu.lst first)
simple command will be sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck



of course the default will be the one kernel you assign as default...

---

### Post by kansasnoob on 2008-06-30
> **bumanie said:**
> You can go to terminal Then under Sytem --> Administration --> Startup Manager, use the gui to get windows to be first on the grub list.

That's the safest way to go:D

---

### Post by antalves on 2008-06-30
gksudo gedit /boot/grub/menu.lst
That's was the command I gave: it's all ok now. Thanks:lolflag::lolflag:

---

### Post by katzpiketailes on 2008-06-30
hi.. ok i really need help..

i typed in: gksudo gedit /boot/grub/menu.1st 
in the terminal..
an editor opened up with a tab that's called menu.1st..
but the problem was, nothing was written in it.. so i can't edit anything..
is this normal? what do i do??

i want windows to be the default instead of ubuntu

im using ubuntu 8.04 by the way..

pls help me ASAP. thank you/

---

### Post by unutbu on 2008-06-30
"/boot/grub/menu.1st" should be 
"/boot/grub/menu.lst". 

(The "one" should be an "ell").

---

