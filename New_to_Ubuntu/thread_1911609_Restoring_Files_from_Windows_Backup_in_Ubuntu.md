---
title: "Restoring Files from Windows Backup in Ubuntu"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by davotronomatic on 2012-01-19
Hey Ubuntu-ers!

Is there an easy way to restore compressed files that were made using Windows Backup onto Ubuntu? My portable hard drive has 300ish .rar files that I don't want to unpack one-by-one. Before I decided to use Ubuntu exclusively I tried restoring them onto my Vista partition but I received and error message and the files stayed on the HD.

I hope somebody can help with this; it would save me a lot of time.

Thanks

---

### Post by Double.J on 2012-01-19
Hi there! Welcome to the forums!

First to get into the live CD, click "try not "install" when it boots.

RAR archiving isn't included by default in Ubuntu at it isn't "opensource" - so a bit like mp3 support, we have to add it in.

open a terminal by pressing CTRL+ALT+T on your keyboard.  you should see a new window with something like the following
```

ubuntu@ubuntu:~#
```
type in the following (or copy and paste) to install rar support
```

sudo apt-get update && sudo apt-get install unrar

```
Hit return - this will then fetch the latest list of programs from the mirror and install unrar for you.

While this is running, open the icon on the left that looks like a folder - a window manager should open. in the column on the left, you should see your back-up drive (it may be liested as a filesystem of a certain size. make sure you "open" it by clicking on it, this should mount it. Switch back to the terminal and make sure it's finished and the blinkin curser is back

You should now be able to use the tool archive manager to unrar the files without going back to the terminal - highlight them and right click.

If you have troubles you could try the terminal way (bit more complicated):
Back in the terminal navigate to your drive.
```

cd /media
ls

```
the cd /media moves you to /media and ls shows you whats there - use these commands to navigate through your drive to where the Rar files are (you won't need to put a / in front of the names now.

The command to unrar is, um, unrar :) an example is
```

unrar e file.rar

```
 This will decompress the file "file.rar" in the current directory. Other options inlude the letter L (but lower case) instead of e - this will list the contents of the rar, and x - unrar to a specific directory (not the one you're in)

If you use x be careful, as the command "-xfile.rar" instead of "x file.rar" would exclude a file from the list :)

I suspect you want yo unrar them all, in the place where they are. to do this try
```

unrar e *.rar

```

Hope it helps - while you're unpacking them however you choose to, have a play with Ubuntu, you just might like it :)

All the best!

---

### Post by davotronomatic on 2012-01-19
Hey GNU, thanks for the reply.

I've already committed to Ubuntu and I have Archive Manager. Highlighting them all and selecting Archive Manager opens 300ish windows simultaneously, and this floods the screen! I suppose what I'm after is a way to unpack them all at once without opening 300 windows.

Do you have any other ideas?

---

### Post by Mark Phelps on 2012-01-20
I once had to do something similar and I did it using the unzip command -- as follows:

for FILE in `/bin/ls _*.ZIP`; do unzip -o $FILE; done

The ` marks are not quote marks, they are "graves" -- on my keyboard, they are the lowercase on the tilde (~) key.

Basically, what the command does is list each _nnn.ZIP file (in a single directory) and hand that off to unzip -- which then unzips it.

You may be able to do the same with "unrar" -- pointing it to all the *.rar files in a directory.

---

### Post by davotronomatic on 2012-01-20
I ended up biting the bullet and doing them one by one. It took a few hours but it's sorted now. Thanks for the replies!

---

