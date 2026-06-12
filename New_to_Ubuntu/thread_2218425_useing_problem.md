---
title: "useing problem"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by showmik on 2014-04-20
i am faceing a big problem.i have diseable ubuntu unty plugin from CompizConfig-setting.now i can't do anything.how can i eanble it?
please help me!!

---

### Post by Double.J on 2014-04-20
Hi there!

If you know which setting you changed, you can open ccsm by opening a terminal with ctrl+alt+t then typing
```
ccsm
```

if you cannot resolve unity, please see [this]("http://m.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html?m=1") article for 12.10 and later (i used option b)

If you need to log out you should be able to with ctrl+alt+del

---

### Post by showmik on 2014-04-20
i can't able any thing in my local account in my pc. but can't easily access into my gust account...

---

### Post by Double.J on 2014-04-20
Ctrl+alt+t not working? 

You ou can use ctrl+alt+F1 to get to the command line, though you won't be able to run graphical programs, but you mahouts be able o follow the reset guide through the terminal

Jj

---

### Post by showmik on 2014-04-20
Ctrl+alt+t and ctrl+alt+F1 it is not working...
i am useing ubuntu 14.04 LTS

---

### Post by grahammechanical on 2014-04-20
Here is something to try. I do not know if it will work as I have only done this in a terminal. 

1) At the Grub boot menu open the Advance Options for Ubuntu sub-menu and select Recovery mode. 
2) At the Recovery menu select Network. That will set up a connection to the internet and put the file system in read/write mode.
3) When back at the Recovery menu select Root and run
4) dconf reset -f /org/compiz/

That will reset Compiz. To exit from Root back to the recovery menu type exit and then select Resume. That will load to a desktop using the Ubuntu fallback video mode. So, you might want to reboot.

As you have found out if we disable the Unity plugin we lose the desktop unless we have first installed an alternative desktop. Same thing will happen if we uninstalled Unity.

Regards.

---

### Post by showmik on 2014-04-21
there is nothing i can't do...
can i install ubuntu? if i install 14.04 ubuntu LTS will my all data remove?

---

### Post by Double.J on 2014-04-21
There!

very sorry to hear that it's gotten to the point that not one of the options above work for you. It may well be best to reinstall and start over. To save your data, boot from the live dvd/usb and copy all your data from the ubuntu install (note do not just copy your home folder - that's going to have messed up settings in the hidden files, best to copy the actual files you want. When you open up your existing ubuntu file system in the live environment, click on the 'home' folder, then the folder with your user name, and that should be where your data is, unless you created extra folders somewhere else. Copy it to an external, then reinstall. Very sorry you've not been able to resolve this. I'm personally at a loss how none of the options listed have produced a terminal console for you, so it's likely that there are multiple issues in the OS, and a reinstall may be the quickest solution.

best of luck and keep us upto date! 

Jj

---

