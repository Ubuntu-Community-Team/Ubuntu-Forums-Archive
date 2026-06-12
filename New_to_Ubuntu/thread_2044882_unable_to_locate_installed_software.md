---
title: "unable to locate installed software"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by tommytiptree on 2012-08-20
Hi, I am new to Ubuntu but am getting to grips with it. However I am puzzled that two apps I have downloaded through the software centre seem to have disappeared. They are showing as installed but I am unable to find them through the Dash or the Classic menu. I have searched Google and one recommendation was to install an app called application finder, but this did not show up the apps. Could someone tell me how to locate these apps.

Thanx

---

### Post by roger_1960 on 2012-08-20
Hi

If installed there would normally be a hidden folder called eg .firefox in your home folder.  Use Nautilus, view>showhiddenfiles and check there first.

I would expect them to show in the dash if they are installed. Did you install them as one user and now have logged on as a different user?

---

### Post by mlentink on 2012-08-20
Which packages did you install?

---

### Post by tommytiptree on 2012-08-20
Hi, thanx for the replies. The software I installed was 7zip and Sword, both found in software centre. I only have one user login and they do not show as hidden files. I have removed 7zip and re-installed but still unable to find it.

---

### Post by mcduck on 2012-08-20
> **tommytiptree said:**
> Hi, thanx for the replies. The software I installed was 7zip and Sword, both found in software centre. I only have one user login and they do not show as hidden files. I have removed 7zip and re-installed but still unable to find it.

7zip (on Linux) is not a standalone application so there is nothing tha could show in menus. Installing the package simply allows the Archieve Manager to handle 7zip packages. So not finding anything in your menus is perfectly normal, theres not supposed to be anything. :)

I have no idea about Sword, but the first thing to check would be to make sure it's not a command-line application (as those don't appear in menus either).

---

### Post by The Cog on 2012-08-20
In synaptic, you can find and right-click the package, and then have the option to list the installed files. You are probably looking for any files installed in /usr/bin or /usr/sbin as these will be the "launcher" part of the application.

---

### Post by Wim Sturkenboom on 2012-08-20
To locate a program and assuming you know the name, you can run the following command in a terminal (example for firefox)

```

wim@ubuntudesktop01:~$ **which firefox**
/usr/bin/firefox

```

---

### Post by mkstallings1 on 2012-08-20
As far as I know, Sword is a command line bible browsing and search tool.  There would be no menu item for this.  If you are looking for a bible program, xiphos may be more to your liking.  It will show up in a menu and has a graphical user interface rather than terminal interface.

---

### Post by tommytiptree on 2012-08-20
Hi guys, thanx for all your help. It all adds to my understanding of Ubuntu.

---

### Post by cmcanulty on 2012-08-20
I think that illustrates 2 very beginner unfriendly issues of Ubuntu. 1)often installed programs must be manually added to the menus, involving hunting through bin files to find the correct command 2)often the install says one name the and menu says another. For example you install gnome-tweak and the menu entry is advanced settings.

---

### Post by mcduck on 2012-08-20
> **cmcanulty said:**
> I think that illustrates 2 very beginner unfriendly issues of Ubuntu. 1)often installed programs must be manually added to the menus, involving hunting through bin files to find the correct command 2)often the install says one name the and menu says another. For example you install gnome-tweak and the menu entry is advanced settings.

Not really, at least not in case of these two aprticular packages, as actually having a menu entry for either one wouldn't make any sense.

Actually I've yet to run into any application from Ubuntu's official repositories that would not create a menu entry when having one would be appropriate. Sure, there might be some old or rarely used packages that don't do this, but most of the time it's a question of either installing a third-party package or a package that isn't actually a desktop application but something else instead.

---

