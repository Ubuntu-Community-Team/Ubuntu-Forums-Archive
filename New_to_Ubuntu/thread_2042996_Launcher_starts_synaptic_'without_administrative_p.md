---
title: "Launcher starts synaptic 'without administrative privileges'"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by mlnease on 2012-08-15
Hello,  I've added a Synaptic shortcut to the Unity launcher but when it launches Synaptic, it does so with the error message,   "Starting without administrative privileges -  You will not be able to apply any changes. But you can still export the marked changes or create a download script for them."  

From a terminal I can start Synaptic with ```
synaptic
```, ```
synaptic-pkexec
```, or ```
gksu synaptic
```, and get a window asking for my password as usual.  I've tried changing the permissions of synaptic-pkexec in /user/bin and created a new launcher, but it still doesn't work properly.

Any ideas?

Thanks in advance.

---

### Post by ubudog on 2012-08-15
Try installing alacarte and editing the launcher that way.

```
sudo apt-get install alacarte
```

Add 'gksu' to the front of the "Command:" field.

Best,
ubudog

---

### Post by mlnease on 2012-08-15
> **ubudog said:**
> Try installing alacarte and editing the launcher that way.

```
sudo apt-get install alacarte
```Add 'gksu' to the front of the "Command:" field.

Best,
ubudog
Thanks for the quick response, ubudog.  I've installed Alacarte but it seems to be a menu editor?  Can it also edit shortcuts?  I don't see the option.  Sorry if I'm being dim.

---

### Post by wojox on 2012-08-15
> **mlnease said:**
> Hello,  I've added a Synaptic shortcut to the Unity launcher but when it launches Synaptic,

What's the script look like?

---

### Post by ubudog on 2012-08-15
> **mlnease said:**
> Thanks for the quick response, ubudog.  I've installed Alacarte but it seems to be a menu editor?  Can it also edit shortcuts?  I don't see the option.  Sorry if I'm being dim.

Oops - sorry, I misread your post.

Have you tried making a new launcher with 'gksu' in front of the Command field?

Try this:
```
gedit ~/Desktop/synaptic.desktop
```

In gedit, paste the following:
```

[Desktop Entry]
Encoding=UTF-8
Name=Synaptic
Comment=Synaptic Package Manager
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
NoDisplay=true
Name[en_US]=Synaptic
Comment[en_US.UTF-8]=Synaptic Package Manager
GenericName[en_US.UTF-8]=Synaptic
Exec=gksu synaptic

```

Then, make it executable:
```
chmod +x ~/Desktop/synaptic.launcher
```

And drag it on to the Unity bar.  

Does this work?

Best,
ubudog

---

### Post by u2nTu on 2012-10-25
Just to finish off this thread, ubudog's solution worked (thank you), but **the fix was even easier**:

[LIST]
[*]After installing Synaptic, type "syn" into the Dash and drag the Synaptic shortcut onto the desktop.
[*]Open a gedit window and drop the shortcut into it, then change the Exec line from "synaptic-pkexec" to "gksu  synaptic", save and exit.
[*]Get rid of any previously placed Synaptic shortcut in the launcher, then drag the new, edited one from the desktop and position in the launcher as desired.
[*]Check that clicking it brings up the authentication dialog, as it should. Back to normal.
[/LIST]
[B]
EDIT:[/B]
There's a drawback to the above method; the desktop shortcut must remain. Delete it and the launcher shortcut evaporates.

So the better way is to:

[LIST]
[*]First open the editor with *gksu gedit*,
[*]Drop the shortcut from the Dash directly into the gedit window,
[*]Make the Exec line change noted in the second bullet above and save,
[*]Get rid of any existing Synaptic shortcuts in the launcher,
[*]Type "syn" into the Dash and drag the Synaptic shortcut to the launcher.
[/LIST]
Since the shortcut in /usr/share/applications has been changed, any inserted from the Dash will now work right.
</EDIT>

Could this annoyance be an attempt to steer users toward the default package manager, U. Software Center? Hmm, not working for me.  :smile:

---

### Post by mlnease on 2012-10-25
> **u2nTu said:**
> Just to finish off this thread, ubudog's solution worked (thank you), but **the fix was even easier**:

[LIST]
[*]After installing Synaptic, type "syn" into the Dash and drag the Synaptic shortcut onto the desktop.
[*]Open a gedit window and drop the shortcut into it, then change the Exec line from "synaptic-pkexec" to "gksu  synaptic", save and exit.
[*]Get rid of any previously placed Synaptic shortcut in the launcher, then drag the new, edited one from the desktop and position in the launcher as desired.
[*]Check that clicking it brings up the authentication dialog, as it should. Back to normal.
[/LIST]
Alternatively, to fix the shortcut in /usr/share/applications (useful for example if a multi-user environment), open the editor with *gksu gedit*, drop the shortcut from the Dash directly in the gedit window and make the Exec line change.

Could this annoyance be an attempt to steer users toward the default package manager, U. Software Center? Hmm, not working for me.  :smile:
Me either--***thanks!***

---

