---
title: "[SOLVED] Reseting Firefox to Default Settings"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by inearlygaveup on 2008-10-17
Hi can any one help please
I am trying to reset Firefox back to the default settings – have found the instructions at 
[http://support.mozilla.com/en-US/kb/Resetting+preferences](http://support.mozilla.com/en-US/kb/Resetting+preferences)

The instructions are 
If you want to reset your Firefox preferences, this article provides instructions on how to reset them through Safe Mode. 
To reset preferences: 
1.Close down Firefox completely: At the top of the Firefox window, click the File menu, and select the Exit menu item.Close down Firefox completely: On the menu bar, click the Firefox menu, and select the Quit Firefox menu item.Close down Firefox completely: At the top of the Firefox window, click the File menu, and select the Quit menu item. 
Go to your Terminal and run:
/path/to/firefox/firefox -safe-mode
My problem is I get no response – am I typing something in incorrectly 
Results are
martin@martin-laptop:~$ /path/to/firefox/firefox -safe-mode

bash: /path/to/firefox/firefox: No such file or directory

martin@martin-laptop:~$ 

Martin

---

### Post by philinux on 2008-10-17
Just type

firefox -safe-mode

In the terminal

---

### Post by greg@localhost on 2008-10-17
Are you entering '/path/to/firefox/firefox' as the path to firefox?

I don't mean to sound patronising, but you are meant to replace that with the actual path to firfox ;)

Greg

---

### Post by TCSnyder on 2008-10-17
you should be able to delete you firefox settings by deleteing the ~/.mozilla/firefox  folder. The forst time a program is run it creates its own folder in your home directory. and deleting it makes it run like it was the first time.

What exactly is your problem that you have to reset it?

---

### Post by inearlygaveup on 2008-10-17
Thanks Phil that worked fine.

Thanks Greg &#8211; But I don't have a clue where the path to Firefox is &#8211; I am very new to Open Source so everything is new &#8211; its a good job you have the forum I still have much to learn and loads of questions

Thanks again to both of you.

Martin

---

### Post by inearlygaveup on 2008-10-17
Thanks for your reply - I had changed loads of font & colours and wanted to go back to the beginning again.

Martin

---

### Post by inearlygaveup on 2008-10-17
> **greg@localhost said:**
> Are you entering '/path/to/firefox/firefox' as the path to firefox?

I don't mean to sound patronising, but you are meant to replace that with the actual path to firfox ;)

Greg
Greg - just a quick question how do I find the path to an application like Firefox

Martin

---

### Post by philinux on 2008-10-17
From the terminal 

which firefox
spits out
/usr/bin/firefox

Or 
Have a look in synaptic for the app in question. Click it to highlight it. Click the installed files tab.

---

### Post by inearlygaveup on 2008-10-17
Thanks Phil - another bit of the jigsaw solved, still a long way to go yet.

Regards
Martin

---

### Post by Sentoguy on 2009-01-27
> **TCSnyder said:**
> you should be able to delete you firefox settings by deleteing the ~/.mozilla/firefox  folder. The forst time a program is run it creates its own folder in your home directory. and deleting it makes it run like it was the first time.

What exactly is your problem that you have to reset it?

Where is this folder? My buddy who set up my comp directed me to where it was once before, but it's been so long I don't remember where to find it.

---

### Post by Sentoguy on 2009-01-27
bump

---

### Post by mrgeorges on 2012-12-18
> **philinux said:**
> Just type

firefox -safe-mode

In the terminal
woow..it works like magic...thanks :D

---

### Post by howefield on 2012-12-18
Old thread back to sleep.

---

