---
title: "Sigh.  Help with root permissions, please..."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-30
...I'm sorry for even asking this, as I'm sure it is around somewhere, but I've tried several searches and I don't see the specific thing I'm asking for.

Is there a way to delete things in system folders (say usr/share/doc/dosbox, for example) through the GUI?  Is there some kind of master command that has to be run?  (For example, I know how to run gksudo gedit to open an editor with root saving privileges.)  Is there a a list of all the apps, or can I just run gksudo File Browser?

Thanks for answering this question.  I appreciate it.

Eric

---

### Post by iaculallad on 2008-07-01
> **Eric Qel-Droma said:**
> ...I'm sorry for even asking this, as I'm sure it is around somewhere, but I've tried several searches and I don't see the specific thing I'm asking for.

Is there a way to delete things in system folders (say usr/share/doc/dosbox, for example) through the GUI?  Is there some kind of master command that has to be run?  (For example, I know how to run gksudo gedit to open an editor with root saving privileges.)  Is there a a list of all the apps, or can I just run gksudo File Browser?

Thanks for answering this question.  I appreciate it.

Eric

Use:

```
gksudo nautilus
```

---

### Post by Eric Qel-Droma on 2008-07-01
Is there a list of commands like that somewhere that would be useful to a beginner like me?  Something that says "Open file editor with root permissions:  gksudo nautilus"?

Thanks for the help, BTW.

---

### Post by rockerphil on 2008-07-01
the command "gksudo nautilus" opens your file browser aka Nautilus in "root" mode, which gives you unrestricted access to all files

----------------
Now playing: [Aerosmith - Dream On](http://www.foxytunes.com/artist/aerosmith/track/dream+on)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by dfreer on 2008-07-01
> **Eric Qel-Droma said:**
> Is there a list of commands like that somewhere that would be useful to a beginner like me?  Something that says "Open file editor with root permissions:  gksudo nautilus"?

Thanks for the help, BTW.

Ubuntu guide maybe?
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

### Post by rockerphil on 2008-07-01
this site has saved my butt too many times to count, i consider it the n00b's life jacket 


[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by iaculallad on 2008-07-01
> **Eric Qel-Droma said:**
> Is there a list of commands like that somewhere that would be useful to a beginner like me?  Something that says "Open file editor with root permissions:  gksudo nautilus"?

Thanks for the help, BTW.

I can't give you any site for commands such as those, only pointers:

Use **gksu** or **gksudo** to open GUI-application base such as gedit, nautilus, or /usr/sbin/gdmsetup and other apps that needs authentication when opened or accessed.

Use the sudo when trying to open terminal-base commands that needs authentication.

gksu & gksudo is the GTK frontend for su and sudo.

---

### Post by bab1 on 2008-07-01
Read any basic book on Linux for the commands.  Then use the term "man yourcommand" in a command terminal specific for the use on your system.  Be very carefull with root commands.

---

### Post by harjp on 2008-07-01
> **Eric Qel-Droma said:**
> Is there a list of commands like that somewhere that would be useful to a beginner like me?  Something that says "Open file editor with root permissions:  gksudo nautilus"?

I thought this list of commands in post #2 in the "New to Ubuntu" sticky was useful:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by Tod Merley on 2008-07-01
Hi Eric,

The others have helped you well with "gksudo nautilus".

In terms of finding the applications I use three tricks - 

1. If you drag a launcher from the Applications,(NOT-Places - copies place!!), or System menus or subs it will copy the laucher for you onto the desktop.  There you can use it to see how it is launched and modify it for your purposes.  For example I copied my Adobe Reader launcher to my desktop, did a right-click on my mouse and chose "Properties" which resulted in a tabbed dialog box.  The far right tab is labeled "Launcher".  In that tab I can both see and edit the command.  In this case I wanted Acrobat Reader to open into several study PDFs I have - I find this a great way to study!!  So I simply added the full path to the document I wanted to study to the existing command, edited the Description and Comments, changed the Icon (unnecessary but fun) and then made several more for the rest of the documents I regularly study.

You inspired me to make a new one to launch nautilus with root privileges. I did a right-click on an empty place on my desktop and chose "Create Launcher".  I made the "Command" "gksudo mautilus", chose a name and comment and selected an icon I liked (click on the icon provided). I tried it and it works very well.  It is now on my action bar. (note: use root with extreme caution!!!).

2. You can do Help > About from the menu bar to see which program is runniing.

3. For finding linux commands I find the Google search "linux command list" very useful.

Have a lot of fun!!

Tod

---

