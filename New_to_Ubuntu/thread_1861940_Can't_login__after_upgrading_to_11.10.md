---
title: "Can't login  after upgrading to 11.10"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by new123 on 2011-10-16
[LEFT]I just upgraded from 11.04 to 11.10 and I can only login with Guest. If I try with my username (root) it just return me to login screen again. I tried logging in with Gnome classic, Gnome classic (no effects), Ubuntu, and all other in the list, same problem.
[/LEFT]

---

### Post by onex on 2011-10-16
I'm glad it's not just me then!

I followed advice re the following bug:

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

That appeared to get me past command line, but now I'm unable to log in with my username with the same behavior. It appears to kill the X session, which then prompts it to restart and give me a log in screen again.

I've tried all the desktops, including Recovery and it's not playing.

Still trying to debug, so if I find anything, I'll post it here.

---

### Post by onex on 2011-10-16
Well, this worked for me:

1. At log in screen, press Ctrl+Alt+F1
2. Login with your username/password
3. ls -Shla | grep "Xauthority"
4. sudo mv .Xauthority Xauthority.old
5. sudo shutdown -r now

I was then able to log in without issue.

Hope this helps!

---

### Post by edgardol on 2011-10-16
Ctrl-Alt-F1 or F2 or ... F6 take me to a blank screen. No prompt at all. I also tried pressing the SHIFT key during boot and I also get a blank screen.
Is there another way to boot in text mode ?

I can login as one user, but trying to login to another user takes me back to the login screen. I tried removing the .Xauthority file of the "problem" user from the "good" user and then rebooting, and it didn't make any difference.
Any other suggestion would be very welcome !

---

### Post by powersurge360 on 2011-10-17
Reboot your computer and make sure you do those steps *before* trying to log in. I had exactly this same problem minutes ago and was able to resolve it by deleting my .Xauthority from the command line.

So do this:

* Reboot
* Do *not* try to log in through the GUI
* Press ctrl+alt+f1
* Enter credentials
* Run rm .Xauthority
* Reboot (sudo reboot now).

If this still doesn't work, I'm afraid I'm tapped :<

---

### Post by cives on 2011-10-17
> **powersurge360 said:**
> Reboot your computer and make sure you do those steps *before* trying to log in. I had exactly this same problem minutes ago and was able to resolve it by deleting my .Xauthority from the command line.

So do this:

* Reboot
* Do *not* try to log in through the GUI
* Press ctrl+alt+f1
* Enter credentials
* Run rm .Xauthority
* Reboot (sudo reboot now).

If this still doesn't work, I'm afraid I'm tapped :<

Powersurge360: I tried what you suggest without success, unfortunately. 
I also have this login problem, as explained in this other thread: [http://ubuntuforums.org/showthread.php?p=11359040&posted=1#post11359040](http://ubuntuforums.org/showthread.php?p=11359040&posted=1#post11359040)
Any help? Thanks in advance.

---

### Post by powersurge360 on 2011-10-17
Hmmm... Are you getting exactly that problem with the permissions?

At worst, you could potentially create a new user and put them in all the same groups that you are in and go from there.

sudo adduser <account_name>

groups
^ take note of what groups show up here

sudo adduser <account_name> <group_name>

and then use that account going forward. It sucks, but it beats reinstalling :<

---

### Post by cives on 2011-10-18
powersurge360, thank you very much for your help.
effenberg0x0 solved my problem with the instructions offered in this post:
[http://ubuntuforums.org/showpost.php?p=11359168&postcount=11](http://ubuntuforums.org/showpost.php?p=11359168&postcount=11)

---

### Post by new123 on 2011-10-18
> **powersurge360 said:**
> Reboot your computer and make sure you do those steps *before* trying to log in. I had exactly this same problem minutes ago and was able to resolve it by deleting my .Xauthority from the command line.

So do this:

* Reboot
* Do *not* try to log in through the GUI
* Press ctrl+alt+f1
* Enter credentials
* Run rm .Xauthority
* Reboot (sudo reboot now).

If this still doesn't work, I'm afraid I'm tapped :<

1st thing I tried is this and the problem is gone, thanks =))

---

### Post by new123 on 2011-10-18
It's solved thank you all for help :)
Just deleted .Xauthority, that's all.
^^

---

### Post by Historian1776 on 2011-10-18
> **powersurge360 said:**
> Reboot your computer and make sure you do those steps *before* trying to log in. I had exactly this same problem minutes ago and was able to resolve it by deleting my .Xauthority from the command line.

So do this:

* Reboot
* Do *not* try to log in through the GUI
* Press ctrl+alt+f1
* Enter credentials
* Run rm .Xauthority
* Reboot (sudo reboot now).

If this still doesn't work, I'm afraid I'm tapped :<

This worked perfect for me. It got me right in. Thanks a million.

---

### Post by artoonie on 2011-10-18
> **onex said:**
> Well, this worked for me:

1. At log in screen, press Ctrl+Alt+F1
2. Login with your username/password
3. ls -Shla | grep "Xauthority"
4. sudo mv .Xauthority Xauthority.old
5. sudo shutdown -r now

I was then able to log in without issue.

Hope this helps!

> **powersurge360 said:**
> Reboot your computer and make sure you do those steps *before* trying to log in. I had exactly this same problem minutes ago and was able to resolve it by deleting my .Xauthority from the command line.

So do this:

* Reboot
* Do *not* try to log in through the GUI
* Press ctrl+alt+f1
* Enter credentials
* Run rm .Xauthority
* Reboot (sudo reboot now).

If this still doesn't work, I'm afraid I'm tapped :<
Thanks folks, this worked!

---

### Post by micdhack on 2011-10-21
> **powersurge360 said:**
> Reboot your computer and make sure you do those steps *before* trying to log in. I had exactly this same problem minutes ago and was able to resolve it by deleting my .Xauthority from the command line.

So do this:

* Reboot
* Do *not* try to log in through the GUI
* Press ctrl+alt+f1
* Enter credentials
* Run rm .Xauthority
* Reboot (sudo reboot now).

If this still doesn't work, I'm afraid I'm tapped :<

Worked for me as well (^_^)

---

### Post by flitbee on 2011-11-22
Am I the ONLY user who doesn't have an .Xauthority file in his home folder and yet can't still login?
And how in the WORLD did the Ubuntu guys manage to release code that is a MAJOR showstopper? I ahd converted half a dozen friends and family to Ubuntu and they've abandoned it for Windows when they encountered the same error :(. This is way beyond them.

---

