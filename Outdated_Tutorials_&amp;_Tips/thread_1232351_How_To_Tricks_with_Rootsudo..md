---
title: "How To: Tricks with Root/sudo."
date: 2009-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by BslBryan on 2009-08-05
Hello, everyone. :-)

[SIZE="3"]**Before I begin, I issue a warning.**[/SIZE]  
```
[COLOR="Red"][B]The root account and the sudo command are not intended to be messed with.  
Of course, you're allowed to mess with them, but 
you can severely damage your system, or have an 
unfixable problem if you're not terribly careful.  

Please, just keep in mind that I'm posting these 
tricks here for purely academic purposes, and while 
they can be used for convenience, it isn't worth 
compromising your install if performed incorrectly.
Nothing here is recommended.[/B][/COLOR]
```
[B]
Now that that's over with, let's learn some tricks![/B]
**1.** How to gain root access without logging in (forgotten password).
**2.** How to use the sudo command without being prompted for a password.
**3.** How to add sudoers (users who are able to use the sudo command).
**4.** How to login as root for a graphical GNOME session.

[SIZE="3"][CENTER]**How to gain root access without logging in (forgotten password).**[/CENTER][/SIZE]
This tutorial assumes that you do not have a GRUB password.  There are ways to do this if you have one, but this tutorial will not go into them, considering you probably haven't set a GRUB password if you can't remember your own password. ;-)
1.  Reboot your computer.
```
sudo reboot now
```
2.  As GRUB is loading, press Esc to enter the menu (if your menu isn't set to display by default.)
3.  Select your version and correct kernel of Ubuntu (recovery mode)
4.  Press Enter to boot.
5.  Select "drop to a root terminal"
6.  Enjoy a passwordless root session! 

[SIZE="3"][CENTER]**How to use the sudo command without being prompted for a password.**[/CENTER][/SIZE]
Wow, how secure this isn't!  But maybe you just NEED to use sudo a hundred times a day, and all of those pesky password prompts keep bothering you.
1.  Open up /etc/sudoers like this:```
EDITOR=gedit sudo visudo
```
2.  Find the line that looks like this:```
system_username	ALL=(ALL) ALL
```
3.  Make it look like this: ```
system_username	ALL=(ALL) NOPASSWD: ALL

```
4.  ```
sudo reboot now
```
5.  Never be bothered by silly root passwords again!

[CENTER]**[SIZE="3"]How to add sudoers (users who are able to use the sudo command).[/SIZE]**[/CENTER]
The simplest way to do this is to add a user to the "admin" group.

You can do it the GUI way or the command-line way.  Both are pretty easy.  

**The GUI Way**
1.  Navigate to System --> Administration --> Users and Groups.
2.  Click "Unlock" and enter your password when prompted.
3.  Select the user that you'd like to edit, and click properties.
4.  Select the User Privileges tab and select all that apply.

**The Hacker Way**
1.  Open up a terminal emulator and type in ```
EDITOR=gedit sudo visudo

``` 
2.  Add this line to the end of the file, obviously replacing "username" with the username that you'd like to add to the admin group. ```
sudo adduser a_username admin

```
3.  Enjoy sudo access!

[CENTER]**[SIZE="3"]How to login as root for a graphical GNOME session.[/SIZE]**[/CENTER]
I know a lot of people that migrate to Ubuntu or have to use it for work that hate the fact that you can't enjoy a graphical session as root, to make the work get done a lot faster, as you can in many other distros.  The simple answer: make it work.  It's probably a lot easier than you think.

1.  Navigate to System --> Administration --> Login Window --> Preferences.

2.  Click on the Security tab, and find "Allow local system administrator login".

3.  All you have to do is check that box, and you're good to go!


**I hope that you have enjoyed this tutorial.  I'd like to think that maybe somebody learned something.  But, please, take my warnings into account before attempting any of this.  Even though graphically logging in as root is easy, it is still highly dangerous.**

---

