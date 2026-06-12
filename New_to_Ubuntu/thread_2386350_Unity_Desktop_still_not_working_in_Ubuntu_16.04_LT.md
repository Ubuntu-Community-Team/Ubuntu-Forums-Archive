---
title: "Unity Desktop still not working in Ubuntu 16.04 LTS after upgrade"
date: 2018-03-04
forum: New to Ubuntu
---

### Post by Nigel Hewlett on 2018-03-04
I lost the Unity Desktop on Ubuntu 16.04 LTS after the January upgrade, the result it seems of a known bug.  Only the Desktop is displayed, no icons. I tried various strategies before discovering about the bug and I may have messed things up with one of these.  I have upgraded again and all my software is up to date.  I am using an Asus Desktop computer (Cyber Station 1151) purchased last year, with Intel core i36100.   With a right-key press I can open a command line from the menu.  By typing DISPLAY=0: ccsm &
I obtained a graphic window for installing Unity and I managed to go through the steps with that and close the window but it didn't succeed.  Now I can't even call up that graphic.  I am wondering now if my best bet might be to try installing the Lubuntu desktop.  I'd be grateful for any advice.

---

### Post by cruzer001 on 2018-03-04
This known bug is unknown to me :) link please.

An i3 processor is good enough to handle the full Ubuntu desktop.

---

### Post by Nigel Hewlett on 2018-03-05
Link is here:  [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1741447](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1741447).  It is reported to have been fixed.

---

### Post by Nigel Hewlett on 2018-03-05
Further information.  This is the response I get on the command line when I enter DISPLAY=0: ccsm &

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 94, in <module>
    import ccm
  File "/usr/lib/python2.7/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.7/dist-packages/ccm/Conflicts.py", line 26, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.7/dist-packages/ccm/Constants.py", line 30, in <module>
    CurrentScreenNum = gtk.gdk.display_get_default().get_default_screen().get_number()
AttributeError: 'NoneType' object has no attribute 'get_default_screen'

[2]+  Exit 1                  DISPLAY=0: ccsm

---

### Post by cruzer001 on 2018-03-05
Suppose to be fixed in xenial-proposed, but the ticket is still open.

You could switch over to "Flashback" (with Metacity WM) until the fix is release.

```
sudo apt install gnome-session-flashback
```

And choose at login.

---

### Post by blade4 on 2018-03-05
Seems like the same issue I had a couple of weeks ago. Cruzer001's suggestion of using a gnome flashback session is good but before you do, try logging into the guest session and see if the issue persists there. If it doesn't, the problem could be with your user account. 

In my case, my guest account was normal so I just created a new user, logged into it, copied over files from the old user account and deleted said old user account.

---

### Post by monkeybrain20122 on 2018-03-05
Did you try the solution in the last post of the bug report page you linked?

```
sudo apt-add-repository ppa:paulo-miguel-dias/pkppa
sudo apt update && sudo apt upgrade
```

The problem is basically due to a bad mesa upgrade but the ppa pushes mesa to a higher version than Ubuntu updates so it bypasses the bad version. It should work if you haven't messed up other things in your attempt to fix it. (note that I removed "-y" from sudo apt upgrade from the post in the link. IMO it is always a stupid idea to do "-y" which means don't prompt me go ahead and upgrade or install, sometimes the output may indicate an upgrade will remove a bunch of things and you shouldn't go ahead)

---

### Post by Nigel Hewlett on 2018-03-06
Many thanks for all these pieces of advice.  Blade4:  I have just tried to log in with a guest session and it worked!  It just never occurred to me to try that. So I will set about creating a new user account and copying into it as you did.    cruzer001:  Thanks for this suggestion.  I might actually try this anyway as a temporary measure.  monkeybrain20122:  Yes I did try the paulo-miguel fix but it didn't work so I uninstalled it.  
Thanks again to all.

---

