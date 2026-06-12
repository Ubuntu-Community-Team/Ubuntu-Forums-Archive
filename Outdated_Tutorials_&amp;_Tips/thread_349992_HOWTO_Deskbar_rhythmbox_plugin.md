---
title: "HOWTO: Deskbar rhythmbox plugin"
date: 2007-01-31
forum: Outdated Tutorials &amp; Tips
---

### Post by zigford on 2007-01-31
**[SIZE="5"]Credit goes to Ryan Rousseau for creating this plugin[/SIZE]**

Deskbar can be extended very easily with plugins (known as handlers) written in python.
Ryan Rousseau has written a nice one that reads the rhythmbox xml file and can play and control Rhythmbox directly from deskbar.

To install the rhythmbox plugin for the current user.  Download the attached file and copy it to:

```
~/.gnome2/deskbar-applet/handlers
```

To intall the rhythmbox plugin system wide.  Download the attached file and copy it to:

```
/usr/lib/deskbar-applet/handlers
```

Then enable the plugin.  Right click deskbar and click properties scroll down and tick the two checkboxes for rhythmbox.

Now deskbar already knows where your rhythmbox xml database is and you can already search and play your songs.  *Note, at this point I think you can only search on song name.

If someone else knows python, they could modify this script to enable searching via other database tags.

Ryan has given permission for others to modify this deskbar handler.

---

### Post by everdred on 2007-03-28
This is seriously good. Thanks, Ryan!

---

### Post by vnkatesh on 2007-05-21
Great Plugin!

---

### Post by Kobalt on 2007-05-21
One more interesting function of the Deskbar. Neat !

---

### Post by rmjb on 2007-06-01
I just tried this. My music is on a gnome-vfs ssh share and when I typed the name of a song I got a crash.
I think it's related to the fact I'm on a ssh share because I get this coming up:
```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/deskbar/DeskbarApplet.py", line 177, in on_start_query_real
    matches = modctx.module.query(qstring)
  File "/home/richard/.gnome2/deskbar-applet/handlers/rhythmbox.py", line 180, in query
    path = gnomevfs.get_local_path_from_uri(path)
RuntimeError: unknown error
```

Something to take a look at I guess.

- rmjb

---

### Post by bamboo.7 on 2007-07-16
Thats pretty neat thank you!

---

### Post by vnkatesh on 2007-07-17
i too had a similar problem, maybe because i load it in the 'Failsafe GNOME' mode, the error pops up

---

### Post by dkbg on 2007-08-04
The song search worked but controlling Rhythmbox didn't. I fixed this by changing "rhythmbox" to "rhythmbox-client" on line 44 of the script:

```
argv = ['rhythmbox', self.rb_arg]
```
to
```
argv = ['rhythmbox-client', self.rb_arg]
```

---

### Post by mabrowning on 2007-09-05
I really liked this applet, but I upgraded to Gutsy Gibbon, and it broke, because they switched to a new Deskbar-applet API, so I updated this plugin and gave the ability to search Song Title, Artist, and Album.

Place this in 
```
~/.gnome2/deskbar-applet/modules-2.20-compatible
```

for just your user, or
```
/usr/lib/deskbar-applet/modules-2.20-compatible/
```
for a system wide installation.

Massive props to Ryan Rousseau for writing the original.

---

### Post by everdred on 2007-11-09
> **mabrowning said:**
> I really liked this applet, but I upgraded to Gutsy Gibbon, and it broke, because they switched to a new Deskbar-applet API, so I updated this plugin and gave the ability to search Song Title, Artist, and Album.

Just noticed your comment... thank you for updating this!

---

### Post by eliosh on 2009-04-29
I'm sorry, but with Jaunty it doesn't activate at all, without giving me any error...
I'm not a python programmer, so i can't locate the error :-(

Probably the error is in the fact that new rythmbox uses a sqllite storage and not a xml file

---

### Post by eliosh on 2009-05-05
> **eliosh said:**
> I'm sorry, but with Jaunty it doesn't activate at all, without giving me any error...
I'm not a python programmer, so i can't locate the error :-(


Solved: copied rhythmbox.py in ```
~/.local/share/deskbar-applet/modules-2.20-compatible
```

> **eliosh said:**
> 
Probably the error is in the fact that new rythmbox uses a sqllite storage and not a xml file

This is absolutely wrong, sorry for my mistake :-D

---

### Post by Xytovl on 2009-05-20
This plugin is quite useful :)
But it didn't behave exactly like I wanted it to, I have done some changes : if you type several words separated by whitespaces it now searches songs that match all words (in any field : artist + title for example). I also fixed what appeared to be a parsing bug : some strings were cut in the middle, unfortunately this seems to slow it down. Last detail : it has now a "Music" category.

---

### Post by Xytovl on 2009-05-20
Sorry, the previous version had a very bad behaviour with some songs (if the filename had a &), here is a d-bus version. It seems to work better, enjoy.

---

### Post by MahBumble on 2009-05-21
I'm having trouble finding where to copy the code in Jaunty...

Terminal output:
[FONT=Courier New]
mb@ubuntu:~/Desktop$ cp rhythmbox.py ~/.local/share/deskbar-applet/modules-2.20-compatible
cp: cannot create regular file `/home/mb/.local/share/deskbar-applet/modules-2.20-compatible': No such file or directory[/FONT]

---

### Post by Xytovl on 2009-05-21
you probably don't have the deskbar directory, you can either create it (mkdir -p [FONT=Courier New]~/.local/share/deskbar-applet/modules-2.20-compatible ) or simply drag and drop the file in the preference window, unfortunately this option doesn't work with the link on the forum, you have to download it first.
[/FONT]

---

