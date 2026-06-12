---
title: "Allow WiFi to start before you log in"
date: 2009-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by DizzyTech on 2009-07-16
I often find myself, despite having a lightning-fast boot with Ubuntu, waiting at my desktop for something to start.  I started looking at what I do with my computer, investigating my bottlenecks.  One of them was my wireless network.  Even though I have a perfectly functional wireless card and I work within mere feet of my router, I often find myself waiting for the wireless to start before opening my web browser.

**Background:  **I recently had a brief stint with Arch Linux due to, well, curiosity.  I discovered a very helpful and useful tip when configuring NetworkManager in my Gnome installation.  This tutorial is mostly duplication of that, and you may find the Wiki article [here](http://wiki.archlinux.org/index.php/NetworkManager).

Most modern Linux distributions include NetworkManager, a very powerful network management daemon.  The practical upshot of having NetworkManager in Ubuntu is that you can easily swap between multiple wireless networks, and even between WiFi and ethernet without editing configuration files or using the terminal.

NetworkManager can support automatically unlocking itself and signing in to networks immediately upon the daemon starting.  The daemon itself usually starts up even before X and GDM/KDM, so it's running long before you log in.  You can use this time to your advantage!

**Steps**:  Still with me?
[LIST=1]
[*]Make sure you are logged in to the account on your Ubuntu computer that manages wireless networks.
[*]If you don't use encrypted networks or don't have a password on your Gnome keyring, skip ahead to step 5.
[*]Hit Alt+F2.  A dialog named "Run Application" will pop up.  Enter the following in the dialog, press Enter, and enter your password when asked.
```
gksudo gedit /etc/pam.d/passwd
```
[*]A text editor window should open.  Skip to the end of the file, and copy and paste the following into a new line at the end of the document.  Save and quit.
```
password        optional        pam_gnome_keyring.so
```
[*]Hit Alt+F2.  When the dialog "Run Application" pops up, copy and paste the following command into the input box and press enter.  If it asks for your password, enter it and hit okay.  Nothing else will appear.
```
gksudo polkit-auth --grant org.freedesktop.network-manager-settings.system.modify --user $USER
```
[*]Right-click the network icon (if you're on wireless, it should be cellphone-like bars) and hit "Edit Connections...".  
[img]http://imgur.com/kr0WQ.png[/img]
[*]A "Network Connections" window will pop up.  Navigate to the wireless tab.
[img]http://imgur.com/roTK1.png[/img]
[*]Select a network that you wish to have connect automatically, and hit "Edit".
[img]http://imgur.com/rqtVF.png[/img]
[*]Towards the bottom of the property sheet that comes up, check "Available to all users."  Hit Apply.  If you are currently connected to this network, the network will disconnect and reconnect.
[img]http://imgur.com/x1vnO.png[/img]
[*]Repeat steps 8 and 9 for each network you wish to be able to connect to during boot.
[*]You are done!
[/LIST]

From now on, WiFi will immediately start when the NetworkManager daemon does.  This is particularly useful if you use the login screen; however, you should also benefit if you automatically login.

**Consequences**:  If your computer is ultra-mobile, or often doesn't stay in the same location, this obviously won't work unless you've been there before.  This also opens up WiFi to all users on your computer, but that really shouldn't be an issue.

**Undo!**:  If you wish to undo this hack, substitute the command in step 5 for the following command.  As well, redo the steps while *un*checking "Available to all users" in step 9.
```
sudo polkit-auth --block org.freedesktop.network-manager-settings.system.modify --user $USER
```

---

### Post by jpeddicord on 2009-07-19
Approved; thanks for your Tutorials & Tips contribution.

---

### Post by MontanaMax on 2009-07-20
This looks very cool - is there a similar set of steps anyone is aware of that will work with Kubuntu?

Thanks,
- Jon

---

### Post by DizzyTech on 2009-07-20
I believe KDE (or at least Kubuntu) uses both PolicyKit and NetworkManager.  

Steps 3 and 4 are not needed for Kubuntu systems, as this is just a hack to make sure Gnome authenticates your user for wireless keys immediately/ASAP.  KDE uses a different method, which may or may not unlock automatically.

As an alternative to step 5, open KDE's terminal and run the following:
```
sudo polkit-auth --grant org.freedesktop.network-manager-settings.system.modify --user $USER
```

Enter your password when asked; press enter when done.  Note that your password will not show up when typing it in within the terminal.

Attempt to follow steps 6-9 in the same fashion; KDE's NetworkManager should follow a similar set of steps.  I don't use it often, so I couldn't answer.  If the method mentioned here (Right-click > Edit Connections) doesn't work, attempt to use KDE's normal network management application.

---

### Post by adempewolff on 2009-07-21
I do not log out very often but often suspend (to RAM) and resume and always find myself waiting ~20s for network manager to detect a network and connect.  I was hoping this method might speed up that wait a little but it does not appear to.  Have I done something wrong or does this method just not apply to resuming from suspend?  Thanks!

---

### Post by dawnlove on 2009-07-21
Is there a way to get this to work in xubuntu? many thanx

---

### Post by dawnlove on 2009-07-21
> **dawnlove said:**
> Is there a way to get this to work in xubuntu? many thanx
I got it to work in xubuntu with    sudo apt-get install gedit

---

### Post by DizzyTech on 2009-07-21
Unfortunately, the waiting for ~20s and up on resume from suspend is from your wireless card.  Some cards like to dump all connection information between suspend/resume.  Not much can be done, but I'm hopeful for the future.  In addition, if you leave your computer long on enough before unlocking your user account, you probably will be connected again.  :D    It's just the nature of Wi-Fi and, more accurately, Wi-Fi in Linux.

Yes, this works properly on Xubuntu with an installation of gedit.  I intended to make this as user friendly as possible.  However, I don't think XFCE uses the Gnome Keyring so the gedit commands are not generally needed.  But your mileage may vary.

---

### Post by magh-87 on 2009-07-21
Awesome :) Thanks a lot. This is definitely going to speed up my day-to-day routine

---

### Post by adempewolff on 2009-07-21
yeah I figured as much, thanks for the quick reply!  The dump is probably for the better--I can just imagine all sorts of bugs and crashes from suspending then moving to another signal and resuming with it trying to talk with the old network.  Ok, maybe that wouldn't be too hard to work around but I am determined to see the silver-lining in this cloud!

---

### Post by yuli_capone on 2009-07-22
Thank's,nery nice!
It's something like this to do with gmail notifier?
When i start my laptop, i am asked for the password...

---

### Post by davidfernando on 2009-07-22
Thanks for sharing such a nice useful tutorial. Its so easy to understand and it really worked

---

### Post by DizzyTech on 2009-07-22
> **yuli_capone said:**
> Thank's,nery nice!
It's something like this to do with gmail notifier?
When i start my laptop, i am asked for the password...

Do you use autologin?  Unfortunately, this is a larger issue with Gnome as a whole... it's keyring (what it stores your passwords in) unlocks automatically if you log in via the login screen, but not if you log in automatically.

There are two workarounds.

First is changing your keyring to have no password:
[LIST=1]
[*]Open Applications > Accessories > Passwords and Encryption Keys
[*]Click on the Passwords tab.
[*]Right-click "default" and hit "Change password..."
[*]Enter your current password and hit change (leaving new password blank) and confirming any warnings.
[/LIST]

The second is disabling the auto-login (Gnome/XFCE only), giving your wireless network more time to autologin while you wait at the login screen thanks to my tutorial ( :P ):
[LIST=1]
[*]Open System > Admistration > Login Window; enter your password if prompted.
[*]Click to the "Security" tab.
[*]Untick the "Automatic Login" checkbox, and hit "Close."
[/LIST]
**I leave Timed Login on, but I don't know if it'll still leave the keyring locked. Your mileage may vary.**

---

### Post by bfckarlos on 2010-04-02
OP

Thanks for that, have been trying to sort this out for a while now.
Great!!;)

---

### Post by trusktr on 2010-07-29
It's been about a year since the original post, but i believe the following still applies.

I believe steps 3, 4, and/or possibly 5 are NOT necessary.

I'm on Arch Linux and all I had to do was add my user to the "networkmanager" group (after creating it) and then step 9 (checking "available to all users") and that's it.

After adding you user to the "networkmanager" group, Gnome authenticates your user for wireless keys immediately/ASAP... This is much easier than modifying PAM files and using polkit commands. This feature is built into networkmanager. ;)

---

