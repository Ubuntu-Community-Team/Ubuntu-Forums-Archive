---
title: "Advice on short cutting an app that runs in Terminal"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by bdemers on 2008-07-15
I have an app that is located in /usr/local/share/asem-51/1.3/.  The chances of my remembering that path is about nil.  What I'd like to do is have a desktop icon, or a listing in the Applications tab which would launch an instance of terminal and set the path for me.  I do not want to launch the app, as it requires some additional command line info which varies.  Maybe there is another direction that I am not aware of.  Certainly open to suggestions.

Thanks

---

### Post by Inxsible on 2008-07-15
> **bdemers said:**
> I have an app that is located in /usr/local/share/asem-51/1.3/.  The chances of my remembering that path is about nil.  What I'd like to do is have a desktop icon, or a listing in the Applications tab which would launch an instance of terminal and set the path for me.  I do not want to launch the app, as it requires some additional command line info which varies.  Maybe there is another direction that I am not aware of.  Certainly open to suggestions.

ThanksDepending on the terminal application that you are using, you need to set the working directory for it.

urxvt  - use the "-cd" flag
mrxvt - use the "-wd" flag
xfce4-terminal - use the "--working-directory" flag. Look at the man pages for your terminal app.

---

### Post by Amstell on 2008-07-15
I would edit your .bashrc to include a command to cd into that directory.

For example.

# vi ~/.bashrc

Scroll down to the bottom and you will see

alias home='cd /home/woody/'

now create an alias like this

alias asemdir='cd /usr/local/share/asem-51/1.3/'

save the file and then restart your terminal

now whenever you enter a terminal and type asemdir it will cd into it.

Hope this helps

cheers

---

### Post by Pro-reason on 2008-07-15
Make a launcher for "gnome-terminal --working-directory /usr/local/share/asem-51/1.3/".

Or "konsole --workdir /usr/local/share/asem-51/1.3/" for Kubuntu.

---

### Post by Inxsible on 2008-07-15
> **Pro-reason said:**
> Make a launcher for "gnome-terminal --working-directory /usr/local/share/asem-51/1.3/".Aah !

So the xfce4-terminal and gnome-terminal both use the same flag !!

---

