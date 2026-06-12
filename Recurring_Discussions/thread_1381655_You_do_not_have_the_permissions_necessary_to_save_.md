---
title: "You do not have the permissions necessary to save the file."
date: 2010-01-15
forum: Recurring Discussions
---

### Post by expozen on 2010-01-15
I am soooooooooo tired of making changes to some file in gedit, pressing the save button, and having the thing refuse to save it because I don't have permission. How difficult is to ask for my password instead of just downright denying me. It's like, "Sorry you made those changes without doing a full investigation of who can do what, when, where, why and how, before opening that file you need to modify. Now you get to jump through five hoops to get back to even."

---

### Post by nitstorm on 2010-01-15
try "man chmod" in the terminal, see what permissions u want to give ur file and then do so by the terminal 

chmod (whatever permission )   location of the file


but highly advisable to not edit the system files if you dont know what u are doing 100%

hope that was useful, cheers!

---

### Post by konqueror7 on 2010-01-15
what file is that your editing?

use 'sudo' to open the editor,```
sudo gedit myfile.txt
```

---

### Post by expozen on 2010-01-15
> **nitstorm said:**
> try "man chmod" in the terminal, see what permissions u want to give ur file and then do so by the terminal 


Yeah, I'm thinking about maybe, "chmod -R 777 /"

---

### Post by FuturePilot on 2010-01-15
> **konqueror7 said:**
> what file is that your editing?

use 'sudo' to open the editor,```
sudo gedit myfile.txt
```

It's better to use "gksudo" for graphical applications [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

I would advise against changing permissions of system files. If you need to edit a system file use gksudo for a GUI editor or sudo if you're using a command line editor. Changing the permissions can break things and leave your system vulnerable.

---

### Post by expozen on 2010-01-15
> **FuturePilot said:**
> If you need to edit a system file use gksudo for a GUI editor or sudo if you're using a command line editor.

sudo and gksudo have a major flaw: You need to know, ahead of time, that you're going to need sudo or gksudo before you do whatever it is that you're going to do.

---

### Post by FuturePilot on 2010-01-15
> **expozen said:**
> sudo and gksudo have a major flaw: You need to know, ahead of time, that you're going to need sudo or gksudo before you do whatever it is that you're going to do.

Just about any time you edit a file that is not in /home/$USER you're going to need to use gksudo/sudo.

---

### Post by expozen on 2010-01-15
> **FuturePilot said:**
> Just about any time you edit a file that is not in /home/$USER you're going to need to use gksudo/sudo.

I shouldn't have to worry about things like that. If gedit knows I don't have the permissions to save the file, why can't gedit ask me for my password, then supply the given password to sudo to save the file itself. Why do I have to hold the things hand to make sure it doesn't trip over it's own feet?

---

### Post by FuturePilot on 2010-01-15
> **expozen said:**
> I shouldn't have to worry about things like that. If gedit knows I don't have the permissions to save the file, why can't gedit ask me for my password, then supply the given password to sudo to save the file itself. Why do I have to hold the things hand to make sure it doesn't trip over it's own feet?

Ah, now I see. That would be a nice feature. I would imagine it could be implemented with PolicyKit. No one has do so though :(

---

### Post by Sarmacid on 2010-01-15
I'm guessing this hasn't been done because allowing an program to escalate privileges would introduce a lot of vulnerabilities. However gedit allows for plugins, so maybe there's one for that task or if not you could write your own.

---

### Post by oldos2er on 2010-01-15
> **expozen said:**
> I shouldn't have to worry about things like that. If gedit knows I don't have the permissions to save the file, why can't gedit ask me for my password, then supply the given password to sudo to save the file itself. Why do I have to hold the things hand to make sure it doesn't trip over it's own feet?

Nautilus can do this if you install the package nautilus-gksu. It will give you the option in your right-click menu to open a file as administrator.

---

### Post by Eisenwinter on 2010-01-15
> **expozen said:**
> Yeah, I'm thinking about maybe, "chmod -R 777 /"
Sure, so everyone can have all access to your root filesystem, great idea there!

---

### Post by aysiu on 2010-01-15
I can't really find where this is now, but I remember filing a bug report suggesting that Nautilus automatically prompt you for a password if you are a sudoer and you drag a file to a system folder, and the devs totally rejected the idea.

There seems to be a lopsided approach to usability and security. So the keyring passwords are visible without a password prompt because you supposedly already logged into your account with a password so should be privy to all of those passwords, but if you are a sudoer who can *gksudo* or *sudo* to modify any system file, Nautilus shouldn't prompt you for a password to modify system files automatically... no, **that** would be sloppy security.

I don't buy it. Unfortunately, I have yet to meet a dev (Ubuntu or upstream Gnome) who sees it my way. One advantage Mac OS X users have over us, I guess.

---

### Post by aysiu on 2010-01-15
> **Eisenwinter said:**
> Sure, so everyone can have all access to your root filesystem, great idea there!
Chmoding the entire filesystem will actually render it unusable.

---

### Post by hoppipolla on 2010-01-15
> **expozen said:**
> i am soooooooooo tired of making changes to some file in gedit, pressing the save button, and having the thing refuse to save it because i don't have permission. How difficult is to ask for my password instead of just downright denying me. It's like, "sorry you made those changes without doing a full investigation of who can do what, when, where, why and how, before opening that file you need to modify. Now you get to jump through five hoops to get back to even."

[size="7"]**+1!!**[/size]

---

### Post by aysiu on 2010-01-15
By the way, as a workaround, if you do open a system file without *sudo* or *gksudo*, you can save it to your desktop for the time being and then use ```
gksudo nautilus
``` to replace the original file with your new modified one (I'd rename the old file just in case).

---

### Post by juancarlospaco on 2010-01-15
It seems a[ Layer 8 ]("http://en.wikipedia.org/wiki/Osi_model")problem

---

### Post by Mornedhel on 2010-01-15
And here I can flaunt Emacs' features again.

You can open a file as a sudoer from within an Emacs you started without sudo. Instead of just typing the filename, you prefix it with /sudo:: and ta dah, there you go.

Also works with /ssh:user@host:filename, ftp, even smb (Samba) and imap (saves files as encrypted messages), and many others.

I have no idea how the privilege escalation bit works, though, but clearly it's doable.

---

### Post by Marvin666 on 2010-01-15
One time in an attempt to make a back-up, I rendered a vista install un-usable, and had to reinstall. It wouldn't let me even copy a system file, so I took ownership of the whole C: drive, subfolders and all. When I was running, and more so after a reboot, vista went completely insane. System restore doesn't save file persmisions and owners, so I had to reinstall vista.

---

### Post by djchandler on 2010-01-15
> **expozen said:**
> I shouldn't have to worry about things like that. If gedit knows I don't have the permissions to save the file, why can't gedit ask me for my password, then supply the given password to sudo to save the file itself. Why do I have to hold the things hand to make sure it doesn't trip over it's own feet?

When you find yourself in this predicament, save the resulting file in your /home/user folder, then enter  **Alt-F2**, then enter **gksu nautilus** in the command dialog. You are now using nautilus with root privileges. Move the file where it belongs. Make sure you rename the previous version (you may need it) before copying the recently edited file where you want it. 

Using chmod indiscriminately sounds like a bad idea to me. Gedit will restrict you this way to keep you from inadvertently rendering your system unbootable. If you are changing system-wide configurations, you must be root, and if you don't know ahead of time that you should be root or su, then you probably stand a good chance of messing up your system.

---

### Post by djchandler on 2010-01-15
> **hoppipolla said:**
> [size=7]**+1!!**[/size]

[size=7]**-10!!**[/size]

---

### Post by hoppipolla on 2010-01-15
> **djchandler said:**
> [size=7]**-10!!**[/size]

it's an important point though man, it SHOULD do this, it would streamline use of the system quite a lot and make it easier for newer and less technical users.


EDIT -- btw I'm not just talking about one program! I mean all the apps not being run as root :)

---

### Post by NFblaze on 2010-01-15
If people really want, they can always add 'gksudo gedit' as the default application to Open it with. Of course this would make you have to enter your password everytime you start gedit to edit and application. 

It's probrably easier to just use nano.

---

