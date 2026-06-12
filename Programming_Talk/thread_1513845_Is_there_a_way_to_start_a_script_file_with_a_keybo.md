---
title: "Is there a way to start a script file with a keyboard shortcut in Ubuntu?"
date: 2010-06-20
forum: Programming Talk
---

### Post by Jammanuser on 2010-06-20
Hello.
I need to start a script file with a keyboard shortcut in Ubuntu.
I had this problem today in Ubuntu 8.10 (and I've had it before several times) where I could not eject a disk from the cdrom drive. I right-clicked on the icon on the desktop, and clicked "Eject" but a dialog popped up saying the disk was in use by another program.
That is one thing it does...
Other times, it may lose the mount of the cdrom drive for some reason, and the cd icon will disappear from the desktop and from Computer, and so I wont be able to either eject the disk or remount the cd drive. I would have to restart to fix such problem.
Today, though, when I had this problem, I started Googling for solutions.

Found [this link]("http://ubuntulinuxhelp.com/quick-tip-when-linux-wont-give-your-cd-back/") which suggests running this in the Terminal:

```

sudo umount /media/cdrom0/ -l

```
So I did, only using "cdrom" instead of "cdrom0" since that was the device that my cdrom drive appeared to be located at. At first glance it didn't appear to do anything, but read further to see that maybe it did...
So I then continued searching, and found [this link]("http://www.cyberciti.biz/faq/linux-cd-dvd-locked-drive-not-opening/") which suggests using the following commands:

```

df
sudo fuser -km /media/cdrom0

```
So I went ahead and ran those. The first command gave me as the device name for the /dev/scd0 which was the cdrom drive as: /media/*name_of_disk_inserted*

But I ignored it and ran this instead:

```
sudo fuser -km /media/cdrom
```

I know...dumb move, right. Anyway, what happened then was the whole OS froze up and I did Ctrl + Alt + Del to restart so I was able to finally eject the stupid disk. I'm thinking that the maybe the reason for this was that I possibly unmounted the cd with the first command I did, then when I tried to use "fuser" to do whatever it is that the command does, it couldn't do it since the cdrom drive was already unmounted, and so it decided to freeze up my entire system. So the moral of this story is...I need to write a script file which contains a command for forcefully ejecting a disk from the cdrom drive when Ubuntu chooses to do its best to keep me from doing this with more traditional (preffered) means. :lolflag:
Basically, I want to have a keyboard shortcut to start up the script file containing a command for unlocking the cdrom and ejecting the disk, so if such a thing happens again, I can just (hopefully) eject the disk by using the shortcut.

Thanks in advance.

-Jam Man

:guitar:

EDIT: Oh, and another good thing to mention here is, I've been having all sorts of weird problems related to my cd drive in Ubuntu. For example, many times when I first start up Ubuntu, a dialog pops up saying a blank disk was inserted in the cdrom drive *when there is no disk in the cd drive*, and I have to push Cancel to close it. This is an annoyance more than a real problem really, but I'd still like to get this fixed as well.

---

### Post by simeon87 on 2010-06-20
System > Preferences > Keyboard Shortcuts > Add and fill in the location of the script under Command.

---

### Post by Jammanuser on 2010-06-20
> **simeon87 said:**
> System > Preferences > Keyboard Shortcuts > Add and fill in the location of the script under Command.
See the attachment. I don't see any "Command" field, or anything looking like you can add in a keyboard shortcut to a script file.

---

### Post by simeon87 on 2010-06-20
Ow, then Adding custom commands must be a feature that was added in a later version than yours. In that case I wouldn't know how to run a script by a keyboard shortcut. How about upgrading to a newer version of Ubuntu.. perhaps it also solves the other problems you're having with your CD drive?

---

### Post by stylishpants on 2010-06-21
> **simeon87 said:**
> Ow, then Adding custom commands must be a feature that was added in a later version than yours. In that case I wouldn't know how to run a script by a keyboard shortcut. How about upgrading to a newer version of Ubuntu.. perhaps it also solves the other problems you're having with your CD drive?


The user interface for new custom keyboard shortcuts was only added in Ubuntu 9.10, but you can still do it the old way, by messing with the gnome-configuration-editor.  It's not hard.


(instructions copied from this post: [http://ubuntuforums.org/archive/index.php/t-785231.html](http://ubuntuforums.org/archive/index.php/t-785231.html) )
```
2.How to create a custom hotkey to launch whatever application you want in GNOME:

Open "gconf-editor" as the user as you're logged in in GNOME (typing gconf-editor in the terminal or "Run Application").
Go to apps > metacity > keybinding_commands
Here we have a list of twelve slots for commands. Double click on e.g. "command_1" 
In Key Value Type in the name of the application you want to launch.
Go to apps > metacity > global_keybindings 
Double click on e.g. "run_command_1" 
Change the key value to whatever key combination you like.Press "Ok".

```

---

### Post by Jammanuser on 2010-06-21
> **stylishpants said:**
> The user interface for new custom keyboard shortcuts was only added in Ubuntu 9.10, but you can still do it the old way, by messing with the gnome-configuration-editor.  It's not hard.


(instructions copied from this post: [http://ubuntuforums.org/archive/index.php/t-785231.html](http://ubuntuforums.org/archive/index.php/t-785231.html) )
```
2.How to create a custom hotkey to launch whatever application you want in GNOME:

Open "gconf-editor" as the user as you're logged in in GNOME (typing gconf-editor in the terminal or "Run Application").
Go to apps > metacity > keybinding_commands
Here we have a list of twelve slots for commands. Double click on e.g. "command_1" 
In Key Value Type in the name of the application you want to launch.
Go to apps > metacity > global_keybindings 
Double click on e.g. "run_command_1" 
Change the key value to whatever key combination you like.Press "Ok".

```
Thanks.

-Jam Man

:guitar:

---

### Post by Can+~ on 2010-06-21
Compiz also provides a keyboard shortcut interface, by default ("Commands").

---

### Post by McRat on 2010-06-21
On the "EDIT" - 

First make sure your CD drive is healthy.  That's probably the most fragile device on a computer, and I've seen a lot of them fail.  They often don't die all at once, they get "crippled" first.

---

### Post by Jammanuser on 2010-06-21
> **McRat said:**
> On the "EDIT" - 

First make sure your CD drive is healthy.  That's probably the most fragile device on a computer, and I've seen a lot of them fail.  They often don't die all at once, they get "crippled" first.
I'm fairly certain my physical CD drive is healthy. It *was* broken a while back though (because my little brother stuck something into it), but I ordered a new one from Dell for my laptop and had a fairly knowledgeable about computers friend replace it with the new one.
The actual CD drive has been working flawlessly in other OSes (though admittedly, I haven't used it in another OSes, such as Windows, in a while) ever since.
The problem outlined in my "EDIT" of the first post seems to be more software related than hardware related.

Thanks for the replies though, all of you.

-Jam Man

:guitar:

---

