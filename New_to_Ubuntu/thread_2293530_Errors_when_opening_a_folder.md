---
title: "Errors when opening a folder"
date: 2015-09-05
forum: New to Ubuntu
---

### Post by c10h15n2 on 2015-09-05
Hi. I just started using Ubuntu 15.04 a few days ago (dual boot with Windows 10) and I see these warnings when I open a folder from the terminal:

```
(nautilus:4300): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:4300): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:4300): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


```

I tried to change the icons with an app called 'Unity Tweak tool' (some people said to try that) and it didn't work.

After I run "***nautilus folder_name***" the folder still opens though, but those warnings are always there... Should I do something, or I can just ignore them ? 

thank you.

---

### Post by Bucky Ball on 2015-09-05
Welcome. No, I wouldn't ignore them. Annoying and they are error messages so there is an issue.

First, make sure your machine is up to date by running these commands in a terminal:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post any and all error messages.

---

### Post by c10h15n2 on 2015-09-05
> **Bucky Ball said:**
> Welcome. No, I wouldn't ignore them. Annoying and they are error messages so there is an issue.  First, make sure your machine is up to date by running these commands in a terminal:  ```
sudo apt-get autoremove sudo apt-get update sudo apt-get upgrade sudo apt-get dist-upgrade
```  Post any and all error messages.  There were no error messages.

---

### Post by Bucky Ball on 2015-09-05
Did you 'Enable desktop icons' with Ubuntu Tweak? That is the workaround, only that. Try reading down from [this]("http://askubuntu.com/questions/287571/desktop-shows-a-white-or-black-background-instead-of-wallpapers/286532#286532").

---

### Post by c10h15n2 on 2015-09-05
> **Bucky Ball said:**
> Did you 'Enable desktop icons' with Ubuntu Tweak? That is the workaround, only that. Try reading down from [this]("http://askubuntu.com/questions/287571/desktop-shows-a-white-or-black-background-instead-of-wallpapers/286532#286532").  That option was already enabled. I disabled it to see what happens but nothing changed.  I read that page, but I don't think it's related to my problem... 

          **edit**: I've just installed a file manager called 'Nemo' and it doesn't show any errors when I use it. To avoid any further complications, I'm gonna remove nautilus and use this instead...   sorry for wasting your time Bucky Ball. I will try to search more thoroughly for a solution before posting a new thread.

---

### Post by Bucky Ball on 2015-09-05
Good plan. There are other for file managers. Removing Nautilus might cause weird things to happen so let us know how you go. 

If it doesn't, see the first link in my signature and good luck. :)

PS: You shouldn't be getting the issues in Nautilus, the default file manager. If you leave the thread unsolved for a few days you may get a solution. As it is the default file manager it is worth filing a bug report or seeing if there is one already.

---

### Post by Geoffrey_Arndt on 2015-09-06
Be careful, Nautilus is more than a file manager.   Removing it may seriously screw up Unity/Gnome.    It's often better just to add another file manager that is not a fork of Nautilus (Nemo & Caja are forks).

Many people here at UF don't like KDE, but it's default file manager (Dolphin) is the "cream of the crop" re features and customization.

For what it's worth, I've always felt that new users should avoid changing any of the default gui programs or config settings until they get to know more (after bout 6 months of running ubuntu "daily" . . . )

---

