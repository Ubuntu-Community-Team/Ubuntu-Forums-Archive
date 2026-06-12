---
title: "etc/network/interfaces file editing"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by Cthulu2156 on 2013-01-12
Hello,

  Basic question, but hoping someone can help me out.  I have edited a file in /etc/network, which is interfaces.  When I pull up the file using gedit or nano the changes are shown in the file that is displayed.  However when I look at the file in unity, there are no changes showing, also when I try to change the file in unity, it says I do not have permissions (I already changed permissions to make changes).  Are there two files in /etc/network that unity only shows one?  Also, if changes are not permanent, why has the file changed in the past (before I made changes and it permanently affected my connection)?  (there was a similar question to this but didn't answer my question).

---

### Post by Bucky Ball on 2013-01-12
Right click the network icon and 'Edit Connections'. Does Network Manager reflect the changes?

Importantly, did you make a backup copy of /etc/network/interfaces before tweaking it?

```
sudo cp /etc/network/interfaces /etc/network/interfaces.BAK

```... or whatever else you want to call the copy. I sometimes append the date.

---

### Post by squakie on 2013-01-12
did you change the permissions on the /etc/network/interfaces file itself?  What did you change them to?  I believe that file needs to be owned by root.  If you couldn't edit it so you changed permissions, change them back, then the next time you need to edit open a terminal window and use sudo gedit /etc/network/interfaces.

---

### Post by Impavidus on 2013-01-13
Gedit has no problem editing a file for which you don't have write permission, but it won't be able to save the file (at least, not in the same location). Therefore, when you open it later you won't see the changes. And don't use "sudo gedit", use "gksudo gedit" instead. Sudo gedit may sometimes break your account by causing a few files in your home directory to be owned by root. GUI programs (programs opening a window of their own instead of living in the terminal) are best called with root privileges using gksudo.

Whenever you don't have permissions to edit a file there's usually a good reason for it. Don't change the permission of system files for easier editing, but momentarily give yourself extra rights by using (gk)sudo.

---

### Post by Cheesehead on 2013-01-13
Impavidus and squakie are right. /etc/network/interfaces is owned by root and not-user-editable for good reason.

Changing that file can break how Network Manager connects your system to the world. Once that link is broken, it's more difficult to ask for help!

Don't change a system file's permissions - that is a great way to break your system. Instead, use 'sudo' or 'gksudo' appropriately to edit as root.
*Always* make a backup of the file before you edit it!
And know how to restore from the backup when your edit fails.

What are you trying to accomplish?
There may be a simpler or safer way to do it.

---

### Post by squakie on 2013-01-13
Personally, I've never had a problem using gedit only.  I remember a couple of years ago this discussion going around, and everyone could only come up with 1 example, and it wasn't changes in owndership, etc..  Instead, the root owned file being edited got gibberish.  However, since this is still hanging around, go ahead and substitue gksudo in place of the sudo in my prior post.    If you didn't already know, which I made the assumption you did, [Impavidus]("http://ubuntuforums.org/member.php?u=1417721") is correct in that you can open a file to read, edit it all you want, but you can't save it to it's original path unless you have permissions.  Also - we have no answer to my question on permissions, etc., yet.

Dave ;)

---

### Post by Cthulu2156 on 2013-01-14
OK, that answers a lot, as far as being able to save changes made.  I'll make a note not to change files as far as permissions and using sudo vs gksudo.  I think I originally deleted the file contents accidentally, and just put what was deleted back in.  I think the permissions are the same too.  So thanks.

---

