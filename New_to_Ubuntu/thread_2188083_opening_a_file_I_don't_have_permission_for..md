---
title: "opening a file I don't have permission for."
date: 2013-11-15
forum: New to Ubuntu
---

### Post by s1wood on 2013-11-15
As a result of a failed attempt to run two users on my system (which ended up with a re-install) I have a few odd files that seem to be still owned by the deleted account so I can't open or remove them.

I had this problem once before and found this tip: 
*>Create a [launcher]("https://help.ubuntu.com/community/HowToAddaLauncher") with the following command: *
*gksudo "gnome-open %u"*[I]When  you drag and drop any file on this  launcher (it's useful to put it on  the desktop or on a panel), it will  be opened as Root with its own  associated application. This is helpful  especially when you're editing  config files owned by Root, since they  will be opened as read only by  default with gedit, etc.<

[/I]Which worked that time but though I've created the launcher dragging and dropping the file on it doesn't work .  Any suggestions? Using xubuntu desktop at present[I].

[/I]Susan

---

### Post by Impavidus on 2013-11-15
That launcher thingy sounds a bit more complicated than it needs to be. But I've never been a drag-and-drop person.

Run **gksu thunar** to start your file manager as root, then change ownership or delete the files. Or open the files to edit, but I don't see why. Then close thunar, as it's really easy to screw things up if you forget in which directory you are and delete the wrong file.

---

### Post by s1wood on 2013-11-15
Thank you, that is a lot simpler - wonder why no-one told me about it last time I asked!
Only one question, how would I change ownership? I have deleted these files because they were unimportant but I might find I have the problem with others.

---

### Post by th.sigit on 2013-11-15
_Ch_ange _own_ership: chown

Just type > chown --help and it will display some text to help you.

For an example here, if I want to change the ownership of "/home/someuser/somedirectory" to "myusername" then I would type

> sudo chown -hR myusername /home/someuser/somedirectory 

---

### Post by deadflowr on 2013-11-15
> **s1wood said:**
> Thank you, that is a lot simpler - wonder why no-one told me about it last time I asked!
Only one question, how would I change ownership? I have deleted these files because they were unimportant but I might find I have the problem with others.

The simplest way to change ownership is through the command line.
```
sudo chown currentusename:currentusername path-to-filename
```
change currentusername to thename of the user who you want to have ownership.
The first name is the owner and the second is the group the file belongs to. Usually, the group is the users default group.
If the file is to be shared, somehow, with others who belong to a made-up group then you'd make that group the name for the group in the command.

The command works easiest because it doesn't discriminate against whichever desktop environment you might happened to be running.

---

