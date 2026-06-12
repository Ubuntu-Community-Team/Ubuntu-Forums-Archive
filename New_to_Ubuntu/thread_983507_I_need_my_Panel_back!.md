---
title: "I need my Panel back!"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by MoreCowBell on 2008-11-15
My computer is running Ubuntu 8.04 LTS and I have The GNOME Panel 2.22.2, whatever that is. Yesterday, I accidentally moved or deleted part of the uppermost panel on my desktop.  Now, what is missing are the links to Applications, Places and System.  Can someone tell me how I can get them back?  Also, I would like to upgrade to the newest version of Ubuntu, 8.10 Desktop.  Would that upgrade fix things for me?

---

### Post by perlluver on 2008-11-15
> **MoreCowBell said:**
> My computer is running Ubuntu 8.04 LTS and I have The GNOME Panel 2.22.2, whatever that is. Yesterday, I accidentally moved or deleted part of the uppermost panel on my desktop.  Now, what is missing are the links to Applications, Places and System.  Can someone tell me how I can get them back?  Also, I would like to upgrade to the newest version of Ubuntu, 8.10 Desktop.  Would that upgrade fix things for me?

If you right click on the panel, go to add to panel, and add back window list, and main menu.  And for firefox just drag it to the panel.

---

### Post by cdtech on 2008-11-15
Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
```
```
gconftool-2 --recursive-unset /apps/panel
```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```

---

### Post by eternalnewbee on 2008-11-15
>  Also, I would like to upgrade to the newest version of Ubuntu, 8.10 Desktop. Would that upgrade fix things for me?
I'd advise you to be patient for like another month or two, as you are new.

---

### Post by MoreCowBell on 2008-11-15
> **cdtech said:**
> Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
```
```
gconftool-2 --recursive-unset /apps/panel
```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```

Thank you so much, cdtech!  I did exactly as you told me to do and it worked perfectly!  About halfway through the fix, I began to worry because all of my panels disappeared, but, in the end, all was restored like new.  How do you do it?  You must be a programmer or something.  I am amazed!  Thanks again, cdtech.  You know your stuff.

---

### Post by chronographer on 2008-11-15
> **MoreCowBell said:**
> You must be a programmer or something.

Not necessarily. he just knows which applications do what. The steps given to you did the following:
[LIST=1]
[*]install gconf2 ( a configuration tool for gnome)
[*]use this installed tool to set all your preferences back to default for the application 'panel'
[*]rm -rf (is dangerous it means "remove everything below this without prompting") and then your settings folder for the panel
[*]then pkill is probably process kill. This means the application gnome-panel will be closed (and restarted presumably) No programming required, just some prior knowledge!
[/LIST]

I am sure that after a year of use you will give some advice to another fellow, who may think you must be a programmer too!

---

### Post by cdtech on 2008-11-15
> **MoreCowBell said:**
> Thank you so much, cdtech!  I did exactly as you told me to do and it worked perfectly!  About halfway through the fix, I began to worry because all of my panels disappeared, but, in the end, all was restored like new.  How do you do it?  You must be a programmer or something.  I am amazed!  Thanks again, cdtech.  You know your stuff.

Your welcome, I've just been around.

Good Luck....

---

### Post by MoreCowBell on 2008-11-16
> **cdtech said:**
> Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
```
```
gconftool-2 --recursive-unset /apps/panel
```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```

Now I need to say that this issue has been solved.  There must be a link to do that properly or a process somehow.  I'm not sure how to say that the problem has been solved so I am saying it right here.  Thanks for your help everyone.

---

### Post by commonplace on 2008-11-21
> **MoreCowBell said:**
> Now I need to say that this issue has been solved.  There must be a link to do that properly or a process somehow.  I'm not sure how to say that the problem has been solved so I am saying it right here.  Thanks for your help everyone.

At the top of the thread, you should see a menu that says 'Thread Tools'. Click on that and a menu will drop down. One of the choices should be 'Mark this thread as solved'. That's it. And welcome to the forums and Ubuntu!

/Kevin

---

### Post by juanbretti on 2008-11-23
> **cdtech said:**
> Press ALT+F2 and in the run dialog box, type "gnome-terminal" then click on Run.

When the Terminal window opens, enter the command:
```
sudo apt-get install gconf2
```
```
gconftool-2 --recursive-unset /apps/panel
```
Then enter:
```
rm -rf ~/.gconf/apps/panel
```
And enter one more command:
```
pkill gnome-panel
```


Hey, I didn't need the ```
sudo apt-get install gconf2
``` with **Intrepid**.

Btw, **cdtech**. Thanks!

---

### Post by XProflmfao on 2009-11-10
thank you, thank you, cdtech!!! My stupid brother messed up the entire panel on my guest account (decided to delete it after he couldn't find the volume control) and then I had to find a way to get it back. Like most people, I started getting scared in the middle of the procedure because all of the panels disappeared. Also, I heard that in the announcements from the Ubuntu Forum staff that anybody giving you advice to type in anything with "rm" was like trying to mess up your computer or whatever... But now I fixed it!!! And nothing happened!! Thanks so much again!!!!

---

### Post by fenririx on 2010-03-20
oops wrong thread

---

