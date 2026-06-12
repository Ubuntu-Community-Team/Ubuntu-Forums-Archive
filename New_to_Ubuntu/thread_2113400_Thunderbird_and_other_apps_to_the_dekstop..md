---
title: "Thunderbird and other apps to the dekstop."
date: 2013-02-07
forum: New to Ubuntu
---

### Post by erikja on 2013-02-07
Hi.
I'm running Ubuntu 12.04.1 LTS.

I want to have shortcuts on the desktop for for instance Thunderbird.

Have tested with opening Applications->Internet->Thunderbird, and then right click for make a shortcut on the desktop.

But what only happens is, that Thunderbird opens.

What can I do?.

My desktop looks like this one:

---

### Post by PowerBarry43 on 2013-02-07
Hi

Launchers for all installed applications are stored in /usr/share/applications so all we need to do is copy the thunderbird one to the desktop and make sure it can be executed. Just fire up a terminal and run:

```
cp /usr/share/applications/thunderbird.desktop ~/Desktop
chmod 755 ~/Desktop/thunderbird.desktop
```

And that's it!

Hope this helps!

Barry

---

### Post by TheFu on 2013-02-07
Change to a non-Unity GUI or setup accel keys that launch whatever app you like without any mouse use.  Something like <super>-T for Thunderbird, <super>-F for firefox .... The underlying Window manager almost certainly supports this if you can't find a GUI interface to make it so.  I'm fairly certain that Unity does this too, but I dropped that GUI back in 2011 and remove it from every install these days. It doesn't work well with my hardware.

Here is an example: [http://blog.jdpfu.com/2011/05/11/get-natty-shortcuts-with-lucid-stability](http://blog.jdpfu.com/2011/05/11/get-natty-shortcuts-with-lucid-stability)

---

### Post by PowerBarry43 on 2013-02-07
> Change to a non-Unity GUI or setup accel keys that launch whatever app you like without any mouse use

That's definitely an option although it's not actually answering the question that was asked. Also if you take a look at the screenshot provided you'll see that erikja is using gnome classic, otherwise known as gnome-session-fallback ;) of course if you prefer to have keyboard shortcuts as I personally do, here's an alternative way of doing it.

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

hope this helps!

Barry

---

### Post by erikja on 2013-02-07
> **TheFu said:**
> Change to a non-Unity GUI or setup accel keys that launch whatever app you like without any mouse use.  Something like <super>-T for Thunderbird, <super>-F for firefox .... The underlying Window manager almost certainly supports this if you can't find a GUI interface to make it so.  I'm fairly certain that Unity does this too, but I dropped that GUI back in 2011 and remove it from every install these days. It doesn't work well with my hardware.

Here is an example: [http://blog.jdpfu.com/2011/05/11/get-natty-shortcuts-with-lucid-stability](http://blog.jdpfu.com/2011/05/11/get-natty-shortcuts-with-lucid-stability)

Thank you for the suggestions. I'm not sure what my GUI is called, can you tell me it ?. What is accel keys ?.

---

### Post by erikja on 2013-02-07
> **PowerBarry43 said:**
> Hi

Launchers for all installed applications are stored in /usr/share/applications so all we need to do is copy the thunderbird one to the desktop and make sure it can be executed. Just fire up a terminal and run:

```
cp /usr/share/applications/thunderbird.desktop ~/Desktop
chmod 755 ~/Desktop/thunderbird.desktop
```

And that's it!

Hope this helps!

Barry

Hi Barry. This worked, many thanks ):P

Erik

---

### Post by erikja on 2013-02-07
> **PowerBarry43 said:**
> That's definitely an option although it's not actually answering the question that was asked. Also if you take a look at the screenshot provided you'll see that erikja is using gnome classic, otherwise known as gnome-session-fallback ;) of course if you prefer to have keyboard shortcuts as I personally do, here's an alternative way of doing it.

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

hope this helps!

Barry

Barry, ALT F2 doesn't work on my system. Can you tell me whay ?

Erik

---

### Post by PowerBarry43 on 2013-02-07
Hi

Based on a quick google I think that's a quirk of gnome-classic (which is the name of your GUI) you can easily set the run command shortcut to alt-F2 like this 


"In Applications -> System Tools -> System Settings -> Shortcuts -> System set Show the Run Command Prompt to Alt+F2"

taken from

[http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/](http://www.flynsarmy.com/2011/11/how-to-make-ubuntu-11-10-more-usable/)

I know the URL says ubuntu 11-10 but this should still work :)

Hope this helps!

Barry

---

### Post by erikja on 2013-02-07
Barry.

I think this is a shortcut to an app..

What I would want is to have ALT F2 to open a field, where to input the name of the app to be opened. For instance Gedit

---

### Post by erikja on 2013-02-07
Barry.

Just checked ALT F2, and it opens as wanted.
Sorry for the mistake :-(

And thanks to all here, that replied to my different quieries

Erik

---

### Post by PowerBarry43 on 2013-02-07
Ok so in the keyboard settings tool under the 'Shortcuts' tab you'll see 'System' category from there, in the right pane one of the entries will say 'Show the run command prompt' right click on that and press ALT+F2 then close the window and that should have set the shortcut to open :) 

[http://stackoverflow.com/questions/8781758/enable-run-command-prompt-shortcut-in-ubuntu](http://stackoverflow.com/questions/8781758/enable-run-command-prompt-shortcut-in-ubuntu)

an alternative way is to just use terminal (CTRL+ALT+T) and run commands in there. The result is the same but you do get a lingering terminal windows which is a bit ugly.

Hope this helps!

Barry

---

### Post by PowerBarry43 on 2013-02-07
> Just checked ALT F2, and it opens as wanted.
Sorry for the mistake 

And thanks to all here, that replied to my different quieries

that's ok! happy to help!

---

### Post by Clopper Almon on 2013-02-09
In my experience with Ubuntu 12.04, the desktop shortcuts for many programs, including Thunderbird, can be simply dragged from the Dash to the desktop, and they bring with them their nice icons. But that technique fails for programs in the Libre-Office suite, probably some of the icons you are most likely to want.  The reason seems to be that the files for creating them are not in /usr/share/applications but in /usr/lib/libreoffice/share/xdg . So to get them on your desktop you need to open a terminal session and do 
```
	cd /usr/lib/libreoffice/share/xdg

	cp draw.desktop        /home/<user>/Desktop 
	cp writer.desktop      /home/<user>/Desktop 
	cp impress.desktop     /home/<user>/Desktop 
	cp calc.desktop        /home/<user>/Desktop

```
where <user> is your user name. (I have added some spaces for clarity). At this point, they are not executable, so you must do:

```
	cd  /home/<user>/Desktop
	chmod a+x draw.desktop
	chmod a+x writer.desktop
	chmod a+x impress.desktop
	chmod a+x calc.desktop

```
Now look at your desktop, and you should find them all. On my desktop, they were scattered about, but a little dragging lined them up together. 

All of this can be done without the use of the terminal, but the terminal is quicker and easier. 

Presumably, nobody gave any thought to this problem in preparing 12.04, and we may hope that it will be fixed in future releases so these steps are not necessary.

---

