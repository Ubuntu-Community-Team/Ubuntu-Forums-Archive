---
title: "cant find wine in software center"
date: 2016-08-21
forum: New to Ubuntu
---

### Post by fistthumper on 2016-08-21
I am trying to install wine so I can utilize windows applications and I have searched online and everywhere I go says to install it from the software center that comes with ubuntu. Ok only one problem, when I search for Wine it does not appear.

I see the following apps

Tellico
Configure Wine
Winefish LaTeX Editor
Winetricks
GemRB
and Notepad which is installed

I click search software button and also search for Wine and it shows me

Configure Wine, Uninstall wine software and winetricks.

Now I think I am being an idiot because supposing those 3 are there in the list you could assume that wine should be installed. But where is it? Shouldn't it show up in my apps list ?

Why does it not show up on the software store?

I even did a manual add for the ppa in the software and update center. No luck.

Any help or advice on what I'm doing wrong would be appreciated.

---

### Post by Frogs Hair on 2016-08-21
I get the same result, but do find the wine meta package in synaptic which is my primary package manager. 

```
sudo apt-get install synaptic
``````
sudo apt-get install apt-xapian-index
``````
sudo update-apt-xapian-index -vf
```

---

### Post by grahammechanical on 2016-08-21
> Configure Wine, Uninstall wine software and winetricks.

If you see icons for those three packages then it is most likely that a version of Wine has been installed. You are expecting to see an icon with the label  "Wine." You will not see that. You will not believe what I am now going to say.

Click on Uninstall Wine Software. That will open a Windows style Add/Remove Programs dialog box. Then you can browse to the Windows exe file (install.exe or setup.exe) in the usual Windows way. Then click the button with the label "Install." And the Windows program will install in the usual Windows way. There should be an icon for it in the Dash that will load the program.

That is right. To use Wine to install a Windows program we load "Uninstall Wine Software." I did say that you would not believe me.

Regards

---

### Post by Mark Phelps on 2016-08-21
Before you go to a lot of trouble to install and configure Wine, visit this site and do searches on the Windows apps you want to install:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

If the app & version you want to use is not listed, or if it IS listed but the rating is lower than Gold -- you are wasting your time with Wine because the app is then not going to work properly for you.

---

