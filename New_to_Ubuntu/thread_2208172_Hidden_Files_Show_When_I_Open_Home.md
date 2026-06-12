---
title: "Hidden Files Show When I Open Home"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-02-26
Hello All...
I did something wrong.  Now, when I open my Home Folder, all my hidden files are displayed.  To get the view back to normal, I simply hit Ctrl + H to hide them again.  
How do I get it back to normal so the hidden files remain hidden when I open Home?
Thanks

---

### Post by rburkartjo on 2014-02-26
try opening the home folder and then click view on the top and uncheck show hidden.

---

### Post by ibjsb4 on 2014-02-26
That option (and more) can be controlled using "dconf-editor".

[ATTACH=CONFIG]250707[/ATTACH]

You may need to install it.
```

sudo apt-get install dconf-tools
```

---

### Post by deadflowr on 2014-02-26
If you're using 13.10, the setting in dconf (org.gnome.nautilus.preferences show-hidden-files)was deprecated.
The new place to change it is in org.gtk.settings.file-chooser show hidden.

---

### Post by ibjsb4 on 2014-02-26
Thanks deadflowr :)

[ATTACH=CONFIG]250708[/ATTACH]

---

### Post by GUZZLR on 2014-02-26
Umm...I think I did it another way.  I opened home, and next to the little gear thingy up in the top right, there is a little drop down arrow.  From there, I simply unchecked the "Show Hidden Files",  I never knew all that stuff was there!  I keep learning about this program.  And yes, I am on 13.10.
Thanks for the help
PS...I just found out how to change the folder icon to a picture in the properties when right clicking on the folder which I wish to change.  It's getting closer to Windows functionality all the time... Now, just to get Netflixs to work on it would really be nice!

---

### Post by ibjsb4 on 2014-02-27
Start a new thread on Netflix.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by GUZZLR on 2014-02-28
Actually, that did not fix the problem. It still shows all hidden files when I start the computer.  I have to uncheck the "Show Hidden Files" every time I restart and open homes...

---

### Post by deadflowr on 2014-02-28
Did you try the dconf method?

---

### Post by GUZZLR on 2014-02-28
```
The new place to change it is in org.gtk.settings.file-chooser show hidden.
```
Hello Deadflowr
I'm sorry, but I'm not following how to get to org.gtk.settings.file?
where is that?
Thanks

---

### Post by deadflowr on 2014-02-28
In dconf editor.
org > gtk > settings > file-chooser (show-hidden will be listed in main window, unmark it)

But you can also use gsettings as well.
```
gsettings get org.gtk.Settings.FileChooser show-hidden
```
which should show as true
```
gsettings set org.gtk.Settings.FileChooser show-hidden false
```

---

### Post by GUZZLR on 2014-02-28
```
In dconf editor.
```

Thanks for the help...how do I get to dconf editor?
Thanks

---

### Post by deadflowr on 2014-02-28
You can install it.

It is one of those oddball ones though.
The package is actually called dconf-tools.

But if you install through the software center, just look for dconf editor.

Like I stated, oddball.

command line would simply be
```
sudo apt-get install dconf-tools
```
When installed, just look for dconf editor.

That make sense?

---

### Post by GUZZLR on 2014-02-28
Wow...this is nice! I never knew this existed, Thanks!

---

