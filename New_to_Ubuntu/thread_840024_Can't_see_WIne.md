---
title: "Can't see WIne"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Papenco on 2008-06-25
Ok, I've installed Wine but it doesn't appear in my app list.
Thanks for help.

---

### Post by Kronie on 2008-06-25
well then u probaqbly didnt install it right..

---

### Post by Papenco on 2008-06-25
Ok, but I've removed it and reinstalled it twice.
ANy Help?

---

### Post by Methuselah on 2008-06-25
Did you install the wine directly from Wine's repositories?
I've noticed that the ubuntu wine gives you the desktop integration but the wine wine (lol) doesn't. 
What I ended up doing was installing ubuntus' wine 0.9.59 then upgraded to wine 1.0 from wine's repository after I enabled it.

Anyway, It's possible you do have wine just without the gnome menus.

Type 

```

wine --version

```

in a terminal and see what comes out.

---

### Post by Papenco on 2008-06-25
leandro@Gopulgafre:~$ wine --version
preloader: Warning: failed to reserve range 00000000-60000000
wine-0.9.59

But I could see it before. I uninstalled and reinstalled but now I can't see it anymore. I've already done:

[PHP]sudo apt-get purge wine[/PHP]

and reinstalled

and also removed the .wine folder and reinstalled.

---

### Post by rockerphil on 2008-06-25
i've never seen the purpose for having an entry in the menus for Wine seeing as it's primarily a command line app. so just open up a terminal and type:

wine <filename.exe>

remember to replace <filename.exe> with the Windows executable you're wanting to run through Wine

---

### Post by Papenco on 2008-06-25
No, when it was in the Menu, I could access to all the programs I had installed with it.

---

### Post by Methuselah on 2008-06-25
There might be problems with wine too:
You might want to upgrade wine.

Your error message seems similar to what was observed in the thread below:

[http://ubuntuforums.org/showthread.php?t=801770](http://ubuntuforums.org/showthread.php?t=801770)

I'm honestly not sure how to enable the menu though.

---

### Post by Papenco on 2008-06-25
No, that's not my problem.
And though it was, Why can't I see it now?

---

### Post by Papenco on 2008-06-25
Anyone?

---

### Post by cpetercarter on 2008-06-25
Before looking for complicated answers, try :

Right click on the menu bar > Edit Menus

Is wine in the list of possible menu items, and is it checked?

---

### Post by Papenco on 2008-06-25
No, it's not.
What could be happening?

---

### Post by cpetercarter on 2008-06-25
I don't know why Wine isn't there, but if you have installed Wine correctly, you can create a Wine menu like this.

Right click on menu bar > Edit Menus > New Menu > name your new menu "Wine" and add a comment (eg "Run Windows programmes") if you want > OK

The new Wine menu item should now appear on the list. Check the "show" box. Highlight the new Wine menu > New Item

In the box which appears, insert name of one of your Wine applications, and in "command" box insert "wine name_of_windows_programme.exe" > OK

Click on Applications > Wine > the Windows app which you have placed there, and see that it works. If it doesn't, the problem will be either that the app isn't in Wine's "drive_c" folder, or that you have not entered the correct command to run it. 

If all ok, go back and insert new items for your other Wine apps.

---

### Post by Fedz on 2008-06-25
If you've downloaded the latest version it doesn't show in the menu, the folder is in /home/name/.wine (hidden)

If you download a .exe and put it on desktop it works as normal by running double click.

If you want to goto program files or c drive goto /home/name/ view show hidden files/folders and open **.**wine ...

---

### Post by Papenco on 2008-06-25
How do I view hidden files?

---

### Post by Canis familiaris on 2008-06-25
In nautilus:
Press Ctrl + H
Press Ctrl + H again to hide those files again

In terminal you can view hiiden files by
```
ls -a
```

---

### Post by Pepperoni on 2008-06-25
Also, check other places other than Apps.  Maybe it threw the icon under "Other" or something else.

---

