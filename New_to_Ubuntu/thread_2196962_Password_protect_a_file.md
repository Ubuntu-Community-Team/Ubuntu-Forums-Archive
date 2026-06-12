---
title: "Password protect a file?"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by nathankitsell on 2014-01-01
Ok, so... I'm new to linux. I mean really new. As in I only started using it a couple days ago.
So basically this is my situation - I'm used to windows, been using it all my life and have used linux/mac only intermittently and never owned a pc running the OS. I have actually worked as an IT administrator in the past, but still only worked on windows. So basically I know windows very well but I'm having a few hiccups transitioning to ubuntu....
I was given an old laptop (really really old.... 2003) by a friend, and decided to install lubuntu on it because XP was running slow- it only has a single core 1.5GHz processor and 512mb 333MHz RAM. It will support 2GB of RAM, but RAM that old is nearly £30 and I'm not paying that much haha. I'm only using it to display photos, and am considering one of those "convert an old laptop into a digital photo frame" projects.

So..... here's my issue:
I want to password protect a file. Just one file. I don't want to encrypt/archive it, as I will be using it fairly often, but I also don't want to have to use my password to log in every time I use the computer. I literally JUST want to have to enter a password each time I access this ONE file so that no one else but me can open it.
The file is a text document with some commands that I've set up as an executable file to launch an image viewer (feh) with some settings to play a slideshow of photos in a specific folder. I'm sure you can guess what kind of photos these are if I don't want anyone else to be able to view them.

So - is there a way to do this? So that I literally double click the file, type in a password, and it executes?

---

### Post by Dave_L on 2014-01-01
> The file is a text document with some commands that I've set up as an executable file to launch an image viewer...

Is the file a shell script? You could add a couple of commands to the script to ask for a "password", and it's not the right password, the script would exit.

But a knowedgeable person could bypass that by opening the script in a text editor, since the file is not encrypted.

Is that the kind of solution you want?

---

### Post by nathankitsell on 2014-01-01
I think so - I don't expect any knowledgeable people to be getting access to this laptop. My family struggles with computers.
I'm not 100% sure what a shell script is - the file just says "feh --recursive --fullscreen" etc etc and i ticked the executable box so I just double click and it runs

---

### Post by Dave_L on 2014-01-01
Here's a script that checks for a password. It might work for your case. If a graphical password prompt is needed, that could be done with gxmessage.

```
#!/bin/sh
read -p "Password:" PW
if [ "$PW" != "xyzzy" ]; then
	echo Not Authorized
	exit 1
fi
echo Simulated processing
```

---

### Post by nathankitsell on 2014-01-01
Thank you :D I'll test it out now
assuming to replace xyzzy with my chosen password?
and um... what's gxmessage?

---

### Post by Dave_L on 2014-01-01
gxmessage is a command that displays a dialog box that can have buttons and text boxes, so it could be used to prompt for a password.

[http://manpages.ubuntu.com/manpages/precise/en/man1/gxmessage.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/gxmessage.1.html)

zenity is another similar command.

[http://manpages.ubuntu.com/manpages/precise/en/man1/zenity.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/zenity.1.html)

---

### Post by nathankitsell on 2014-01-01
oh that looks really good... definitely going to have to look into that.

btw, I tried copy+pasting the code you wrote into the file, but it still just launched straight away without requesting a password :/ am I doing something wrong?

---

### Post by Dave_L on 2014-01-01
Maybe you need to replace the command line password prompt with zenity or gxmessage. Sorry that I don't have time to help with that now. But doing it yourself will be a good exercise for you in in shell scripting. :)

---

### Post by Jonathan Precise on 2014-01-01
You need to run it from a terminal if you do not use gxmessage or zenity.

---

### Post by nathankitsell on 2014-01-02
I'll try gxmessage :) thanks guys! If I run into any more trouble I'll be back on haha

---

