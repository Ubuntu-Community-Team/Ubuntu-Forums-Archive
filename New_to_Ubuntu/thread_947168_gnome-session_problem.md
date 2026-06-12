---
title: "gnome-session problem"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by geckoguykc on 2008-10-14
I recently was messing around with some permissions and added my user to a group. When I restarted I could no longer login to gnome without it saying that it couldn't start my session, automatically giving me the xterm window. My user permissions were gone as well, so I chrooted in through the liveCD and got my permissions back and reverted all the changes I had made, no luck, but now my failsafe gnome session works fine. I just can't login to the regular one. 

~/.xsession-errors reads as follows:

/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator

---

### Post by Liviu-Theodor on 2008-10-14
What you have in the [FONT="Courier New"]/etc/passwd[/FONT] file? Is there, at your user name, what it has to be? Maybe you can modify there, under the fail-safe gnome session?

For example, in my file, for my line is:
```
theodor:x:1000:1000:Liviu-Theodor Vizdoaga,,,:/home/theodor:/bin/bash
```

---

### Post by geckoguykc on 2008-10-14
mine says this:

```
casey:x:1000:4:casey,,,:/home/casey:/bin/bash
```

---

### Post by geckoguykc on 2008-10-14
I messed around some and tried to reinstall gnome-session, ubuntu-desktop, and gdm packages via apt, and that didn't do it either.

---

### Post by geckoguykc on 2008-10-14
Any ideas on what I should do to fix this? I've already had to completely reinstall once before, and now I have so much software installed I would hate to do it all over again? I know I can back up my home directory and reinstall, but how could I back up all the software I have installed? something along the lines of remastersys?

---

### Post by Liviu-Theodor on 2008-10-15
> **geckoguykc said:**
> ```
casey:x:1000:4:casey,,,:/home/casey:/bin/bash
```

Try to replace this with:
```
casey:x:1000:1000:casey,,,:/home/casey:/bin/bash
```

---

### Post by geckoguykc on 2008-10-15
That didn't change anything. When I go to the failsafe gnome session it says "logging you in without startup scripts." Is there a way I can just have it do that by default or just replace the startup scripts somehow? I installed some updates and it deleted all the entries in my GRUB menu.lst, so I had to boot via GRUB command line.

---

### Post by Liviu-Theodor on 2008-10-16
If you are using Hardy Heron (or newer), at [FONT="Courier New"]System->Administration->Users and groups[/FONT], click [FONT="Comic Sans MS"]Unlock[/FONT], at the dialog box you have [FONT="Comic Sans MS"]Details[/FONT], show them, click on the link next to [FONT="Comic Sans MS"]Action[/FONT], then enter your password to Authentificate. You will have now two open windows, *Authorizations* and *User settings*. Just try to play a little bit with what you have there, as the options related to users are quite intuitive. Of course, do nothing at the other options, especially these you don't know what they do.

---

### Post by geckoguykc on 2008-10-17
The unlock button is greyed out.

---

### Post by Liviu-Theodor on 2008-10-17
I verified, the command for this (to run in the command line) is ```
users-admin
```
If I run ```
gksudo users-admin
``` the button will be also grayed. All I can suggest is to have a new account and from it run what I have suggested, or in a terminal the command without gksudo. So what happens if you run that as another user?

---

### Post by geckoguykc on 2008-10-17
I've upgraded to intrepid and everything started working again. thanks for the help

---

