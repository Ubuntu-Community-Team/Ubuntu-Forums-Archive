---
title: "Commands in Bashrc"
date: 2013-12-01
forum: Programming Talk
---

### Post by ubu88 on 2013-12-01
Hi,

I've put two commands in bashrc but only one of them will execute.

How can we execute both?


- cd /home/user/Desktop
- sudo -i

---

### Post by steeldriver on 2013-12-01
What exactly are you trying to achieve? Putting sudo -i in your .bashrc file sounds like a TERRIBLE idea to me

FWIW it almost certainly IS executing both commands - however 'sudo -i' changes to root's home directory (/root) immediately negating the previous 'cd'

---

### Post by Lars Noodén on 2013-12-01
They probably are both executing but the -i in makes the new shell with the same settings as if it were a fresh login.  So that overrides the previous cd.  Try it without the -i, unless there is a specific reason you have it.

---

### Post by ubu88 on 2013-12-01
Thanks for the answers.

I'm trying to open terminal as root.

 Without -i it just spits out the options and with -s it freezes up.

---

### Post by Lars Noodén on 2013-12-01
Try using it to launch a shell instead.

```

cd /home/user/Desktop
sudo /bin/bash

```

Or are you talking about launching the graphical terminal?

```

gksudo "gnome-terminal --working-directory=/home/user/Desktop"

```

---

### Post by ubu88 on 2013-12-01
No, thanks, was talking about command line.

sudo /bin/bash asks for password but then it freezes up too.

---

### Post by ubu88 on 2013-12-01
It's working if I do a 'Ctrl-c' after it. Thanks!

---

### Post by JKyleOKC on 2013-12-01
Try your original commands, but swap their sequence so that you do the "sudo" first. That may not work, because of the switch to root being immediate and thus cutting off access to the rest of .bashrc, but if .bashrc is executing from RAM rather than from the disk, it might do what you want. In any case, were I doing this, I would make these the final two commands in the file. And as noted above, it's a really BAD idea since it puts you in root mode every time you log in!

---

### Post by Lars Noodén on 2013-12-01
Having it jump directly to root isn't the best idea.  What problem are you actually trying to solve?

---

### Post by drmrgd on 2013-12-01
> **Lars Noodén said:**
> Having it jump directly to root isn't the best idea.  What problem are you actually trying to solve?

This +1,000,000!  Why would you want to set it up so that each terminal session automatically opens up a root shell?  That's not very wise at all, and given the simplicity of switching to a root login whenever you need, there's really never a reason to do this.

---

### Post by ubu88 on 2013-12-01
> **JKyleOKC said:**
> Try your original commands, but swap their sequence so that you do the "sudo" first. That may not work, because of the switch to root being immediate and thus cutting off access to the rest of .bashrc, but if .bashrc is executing from RAM rather than from the disk, it might do what you want. In any case, were I doing this, I would make these the final two commands in the file. And as noted above, it's a really BAD idea since it puts you in root mode every time you log in!

I tried to switch already and it didnt change anything. Thanks though.

---

### Post by ubu88 on 2013-12-01
> **Lars Noodén said:**
> Having it jump directly to root isn't the best idea.  What problem are you actually trying to solve?

There isnt much that you can do with the terminal as a user. I never understood this paranoia with linux when you use it as a desktop computer and not a server.

---

### Post by ubu88 on 2013-12-01
> **drmrgd said:**
> This +1,000,000!  Why would you want to set it up so that each terminal session automatically opens up a root shell?  That's not very wise at all, and given the simplicity of switching to a root login whenever you need, there's really never a reason to do this.

Because its annoying to type sudo every time. Its just a desktop computer not a server so I dont need NSA level of security. :rolleyes:

---

### Post by Lars Noodén on 2013-12-01
Putting sudo into .bashrc means that you no longer have the option to use the terminal as a regular user.  What you might do instead is make a custom launcher that runs gnome-terminal for you using gksudo so you don't have to type it in.

---

### Post by ubu88 on 2013-12-02
Thanks Lars but 'make link' is greyed out on gnome-terminal.

---

### Post by Lars Noodén on 2013-12-02
Unity is very difficult to customize.  In 12.04, you can make a custom icon by creating the file /usr/share/applications/root-term.desktop and filling it with this:

```

[Desktop Entry]
Name=RootTerminal
Comment=Launches a terminal with a root shell
Exec=/usr/bin/gksudo "/usr/bin/gnome-terminal --working-directory=/home/user/Desktop/" 
Icon=/usr/share/icons/Humanity/apps/128/gksu-root-terminal.svg
Terminal=false
Type=Application
[s]Categories=Utility;Application;[/s]
Categories=Utility;TerminalEmulator;

```

I would guess it would be similar for later versions of Ubuntu.  Double check the icon and exec path to be sure.

Then once that file is in place, just go to the Dash and find "RootTerminal" or whatever you chose for "Name="

That saves you from messing with .bashrc which locks you out of your regular account.

---

### Post by ubu88 on 2013-12-02
That's perfect. Thank you Lars! :P

---

