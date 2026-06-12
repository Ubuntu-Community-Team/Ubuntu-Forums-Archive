---
title: "No permission to change Xorg.conf"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Sprollest on 2008-07-07
Hey all, I'm having some trouble with my display driver. I'm currently running in safe graphics mode (due to install problems), and have tried on numerous occasions to download the Nvidia driver. It installs, and on restart either freezes up, or displays the log on screen sound but displays nothing except the cursor. 

I have heard a fix for this, by editing the Xorg.conf file and adding the line: Option "UseDisplayDevice" "DFP". I've tried the method of using the Alt+Shift+F2 screen (sorry I'm noob to this! :P) and using the commands:

[I]sudo dpkg-reconfigure xserver-xorg -phigh
sudo nvidia-xconfig
nano /etc/X11/xorg.conf[/I]

and then adding the line Option *"UseDisplayDevice" "DFP"* in the "Screen" section.

Essentially I do this, but upon trying to exit (where it asks me to save) it says I do not have permission (meaning I can't make the changes). I have also tried editing the actual file in the GUI in the word editor, but that again says I don't have permission. Anyone know a solution to this? I want to try and see if this fix works - sorry if this is long winded explanation, just wanted to explain everything!

---

### Post by billgoldberg on 2008-07-07
do this instead

sudo dpkg-reconfigure xserver-xorg -phigh
sudo nvidia-xconfig
gksudo gedit /etc/X11/xorg.conf

---

### Post by bodhi.zazen on 2008-07-07
Just use nvidia settings :)

```
gksu nvidia-settings
```

---

### Post by Sprollest on 2008-07-08
Well, if I try

```
gksu nvidia-settings
```

It just says Gtk-WARNING **: cannot open display

I just need to know how to get permission to edit the Xorg.conf really.

A few noob questions, how do I copy and paste bits of code into the Alt+Shift+F2 screen? I'm manually tabbing between the screen modes and typing atm, and its a bit annoying.

And another thing, as I said, I am currently running Ubuntu in safe graphics mode - as the Vessa drivers seem to cause problems too. What is the command to enable / disable this? As whenever I try to activate the Nvidia drivers, on restart it will not display the screen at all - and I dont know how to fix it back to safe graphics mode so I can try something else. As atm I just do an ENTIRE resinstall if the graphics go wrong.

---

### Post by eriqjaffe on 2008-07-08
> **Sprollest said:**
> I just need to know how to get permission to edit the Xorg.conf really.You have to be sudo to edit that..

```
sudo nano /etc/X11/xorg.conf
```

...should do the trick.  If you're in one of the virtual terminals (CTRL-ALT-F2, etc), that's why you get those errors trying to run nvidia-settings - it's a GUI program which can't run without X.

BTW, it's a good idea to back up xorg.conf (or any system file, really) first before editing it:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by ChameleonDave on 2008-07-08
> **Sprollest said:**
> Well, if I try

```
gksu nvidia-settings
```

It just says Gtk-WARNING **: cannot open display

gksu and nvidia-settings are graphical applications.  They work when you are logged onto your desktop, not from the TTY terminal.

> **Sprollest said:**
> 
I just need to know how to get permission to edit the Xorg.conf really.

You were just missing a "sudo" to give you superuser permissions.

> **Sprollest said:**
> 
A few noob questions, how do I copy and paste bits of code into the Alt+Shift+F2 screen? I'm manually tabbing between the screen modes and typing atm, and its a bit annoying.

You can't.

---

### Post by bodhi.zazen on 2008-07-08
Is your user in the admin group ?

If so, edit /etc/sudoers with :

```
sudo visudo
```

Add this to the end of the "Defaults" line

> env_keep+=DISPLAY

The list is comma delineated.

---

### Post by ChameleonDave on 2008-07-08
> **bodhi.zazen said:**
> Is your user in the admin group ?

If so, edit /etc/sudoers with :

```
sudo visudo
```

Yes, if you look at his post, you'll see that he successfully used sudo twice.  He then forgot to use sudo when he open up nano.

Moreoever, I'm not sure it's wise to get a newbie to open vi.  It is a counter-intuitive editor.

---

