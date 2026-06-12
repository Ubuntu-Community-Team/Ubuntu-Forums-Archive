---
title: "Why can't I delete some files from Trash?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by d.kusummmanth@gmail.com on 2008-05-25
Why can't I delete some files from Trash?

---

### Post by sayakb on 2008-05-25
```
sudo rm -rf ~/.local/share/Trash/files
```

---

### Post by bwhite82 on 2008-05-25
More than likely, because you do not have the permissions to delete them. You can open nautilus with root privileges and navigate to your /home/username/.Trash folder and delete them that way.

---

### Post by forestpixie on 2008-05-25
If your username is a real e-mail address I would get it changed.

Edit - normally it's not allowed but in e-mail as username cases they will I think - post a thread on the forum feedback/help 

[http://ubuntuforums.org/forumdisplay.php?f=48](http://ubuntuforums.org/forumdisplay.php?f=48)

---

### Post by bwhite82 on 2008-05-25
> **forestpixie said:**
> If your username is a real e-mail address I would get it changed.

+1

---

### Post by sayakb on 2008-05-25
But I don't think that the display name could be changed. The OP should rather create a new account.

---

### Post by Joeb454 on 2008-05-25
We're getting way off topic here. More than 1 account is prohibited. Changing the username however, can be done in certain circumstances when the user has an email address as the username. Though I guess some people may want an email as a username, most wouldn't.

So if the OP posted a thread requesting his username to be changed in Forum Feedback and Help, it may well be changed due to the nature.

Now...back on topic?

---

### Post by crf on 2008-05-25
I had this happen too, and I filed a bug partly about the problem.

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/230125](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/230125)

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **Soldierboy said:**
> More than likely, because you do not have the permissions to delete them. You can open nautilus with root privileges and navigate to your /home/username/.Trash folder and delete them that way.

[COLOR="Blue"]You can open nautilus with root privileges [/COLOR]!!!!! How?

My problem is still not solved & I'm not able to understand how to solve this problem using Terminal.

---

### Post by bwhite82 on 2008-05-26
> **d.kusummmanth@gmail.com said:**
> [COLOR="Blue"]You can open nautilus with root privileges [/COLOR]!!!!! How?

My problem is still not solved & I'm not able to understand how to solve this problem using Terminal.

Hit ALT+F2 type in: gksu nautilus
Navigate to your home directory (/home/yourusername) Then in Nautilus: View>Show hidden items. Go into .Trash folder and delete the files.

---

### Post by J@n on 2008-05-27
> **LinuxIsInnovation said:**
> ```
sudo rm -rf ~/.local/share/Trash/files
```

Mind you.... if you have deleted files on additional disks (USB, Remote disks and so on) those remain in your Trash. It happened on my box also. It might help to check those disks as well for "Trash-folders" Start a console and type *sudo nautilus* assuming Gnome. Browse to the additional disks and remove the .Trash folders.

HTH

Greetz

J@n

---

### Post by sayakb on 2008-05-27
Yes, but while Unmounting, Natilus does ask us to Empty the trash, doesn't it? But aren't the trash file of removable media located on the media itself?

---

### Post by J@n on 2008-05-27
In my situation Nautilus does not ask to empty Trash. I just checked preferenaces and it does not seem to be a user configurable option. Not that it really matters. If the OP can't delete files Nautilus obviously does not ask for it.

The fact of the matter is that if you can't delete certain files, browsing to the individual disks might do the trick :-k

Greetz,

J@n

---

### Post by sayakb on 2008-05-27
Yes, maybe. It does create a .Trash folder into every removable media's parent directory when we delete something. Or if, due to some reasons, it can't, it simply asks you to delete the file (bypassing trash).

---

