---
title: "[SOLVED] .dbus folder in /home/username"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-20
I find a folder, locked and owned by root in my /home/mark (mark is the username)

the folder is:

.dbus

Gnome FM does not say how many items in it.

1 - Does this folder belong in /home at all?

2 - If it does not belong there, where should it go? How do I determine if there are links/dependencies to it and move them all to the correct place simultaneously?

3 - If .dbus doesn't belong in /home/mark what caused it to go there? I have never moved a hidden file or folder.

---

### Post by tuxxy on 2008-10-20
> **Mark_in_Hollywood said:**
> I find a folder, locked and owned by root in my /home/mark (mark is the username)

the folder is:

.dbus

Gnome FM does not say how many items in it.

1 - Does this folder belong in /home at all?

2 - If it does not belong there, where should it go? How do I determine if there are links/dependencies to it and move them all to the correct place simultaneously?

3 - If .dbus doesn't belong in /home/mark what caused it to go there? I have never moved a hidden file or folder.

It shouldnt have many files its for the session bus, I beleive it does belong in your /home

Also you could check the contents with this command if needed

```
sudo nautilus /home/mark/.dbus
```

---

### Post by Mark_in_Hollywood on 2008-10-20
I want to copy the entirety of /home to an external usb drive. Then I'm going to udgrade to Ibex.

When I tried this before, the copy command halted at .dbus and asked what to do: ignore, skip, something ...

How can I simply do a command line to copy the /home over without changing permissions?

---

### Post by tuxxy on 2008-10-20
This post maybe useful

[http://ubuntuforums.org/showthread.php?t=652584](http://ubuntuforums.org/showthread.php?t=652584)

---

### Post by Mark_in_Hollywood on 2008-10-20
Thanks, I'm going to give that a try. But before I do

How can I make the last line's device permsssion look exactly like the 2 lines above it?

drwx------  4 mark root  4096 1969-12-31 16:00 PRESTON
drwx------  2 mark root 16384 1969-12-31 16:00 UDISK 28X
drwxrwxr-x  2 mark mark  4096 2008-10-20 17:06 usb

PRESTON and UDISK 28X are memory sticks. usb is an 80 gig ext. usb drive.

---

### Post by tuxxy on 2008-10-20
```
chmod 700 <drive location>
```

---

### Post by Mark_in_Hollywood on 2008-10-20
Thank you and I'm going for it. Marking this solved.

---

